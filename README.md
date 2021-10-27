# Discord (JDA) HTML Transcripts
[![Discord](https://img.shields.io/discord/555474311637499955?label=discord)](https://discord.gg/rf5qN7C)

Discord HTML Transcripts is a node.js module (recode on JDA) to generate nice looking HTML transcripts. Processes discord markdown like **bold**, *italics*, ~~strikethroughs~~, and more. Nicely formats attachments and embeds. Built in XSS protection, preventing users from inserting html tags. 

**This module is designed to work with [JDA](https://github.com/DV8FromTheWorld/JDA).**

HTML Template stolen from [DiscordChatExporter](https://github.com/Tyrrrz/DiscordChatExporter).

## Example Output
![output](https://img.derock.dev/5f5q0a.png)

## Usage
### Example usage using the built in message fetcher.
```java
TODAVIA NADA PE ME FALTA CREO LOS METOHD XD
const discordTranscripts = require('discord-html-transcripts');

const channel = message.channel; // or however you get your TextChannel

// Must be awaited
const attachment = await discordTranscripts.createTranscript(channel);

channel.send({
    files: [attachment]
});
```

### Or if you prefer, you can pass in your own messages.
```java
TODAVIA NADA PE ME FALTA CREO LOS METOHD XD
const discordTranscripts = require('discord-html-transcripts');

const messages = someWayToGetMessages(); // Must be Collection<string, Message> or Message[]
const channel  = someWayToGetChannel();  // Used for ticket name, guild icon, and guild name

// You do not need to await this
const attachment = discordTranscripts.generateFromMessages(messages, channel);

channel.send({
    files: [attachment]
});
```

## Configuration
Both methods of generating a transcript allow for an option object as the last parameter.

### Built in Message Fetcher
```java
const attachment = await createTranscript(channel, {
    limit: -1, // Max amount of messages to fetch.
    returnBuffer: false, // Return a buffer instead of a MessageAttachment 
    fileName: 'transcript.html' // Only valid with returnBuffer false. Name of attachment. 
});
```

### Providing your own messages
```java
const attachment = await generateFromMessages(messages, channel, {
    returnBuffer: false, // Return a buffer instead of a MessageAttachment 
    fileName: 'transcript.html' // Only valid with returnBuffer false. Name of attachment. 
});
```
