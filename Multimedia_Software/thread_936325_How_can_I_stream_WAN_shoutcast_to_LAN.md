---
title: "How can I stream WAN shoutcast to LAN?"
date: 2008-10-02
forum: Multimedia Software
---

### Post by kwacka on 2008-10-02
I have a home network and listen to an internet 'radio' shoutcast that uses an .m3u playlist. At any one time there are likely to be more than one device connected to the station (which seems to be a waste of bandwidth)

Any suggestions as to how I can use the desktop to stream to a local network?

One unit is a handheld that does not recognise m3u lists - it does recognise mp3, ogg, FLAC but not m3u (adding another media player application is not an option) - I'd like to be able to use this too.

---

### Post by markbuntu on 2008-10-02
If you are wanting to stream audio over your local or home network you can use this guide here:

[http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio)

---

### Post by eye208 on 2008-10-03
> **kwacka said:**
> I have a home network and listen to an internet 'radio' shoutcast that uses an .m3u playlist. At any one time there are likely to be more than one device connected to the station (which seems to be a waste of bandwidth)

Any suggestions as to how I can use the desktop to stream to a local network?

One unit is a handheld that does not recognise m3u lists - it does recognise mp3, ogg, FLAC but not m3u (adding another media player application is not an option) - I'd like to be able to use this too.
To set up a stream you need a server such as Icecast or VLC. Here's how to do it with VLC:

In the "Open File" or "Open Network Stream" dialog, select the playlist file or enter the stream URL. Under "Advanced Options" enable "Stream/Save", then click "Settings". This will open the stream output configuration dialog.

Unter "Outputs" you can choose whether or not to play the stream locally as well. To configure a simple MP3 stream, enable "HTTP". The default port number will be "1234". If the input stream already is in MP3 format and you just want to pass it on, select "Raw" encapsulation and click "OK". If you want to transcode the stream to Ogg Vorbis on the fly, select "Ogg" encapsulation and enable "Audio Codec". Choose the "vorb" codec and a bitrate. Vorbis quality is very good even at 64kbps, but since there's plenty of bandwidth within your LAN you may choose a higher bitrate here if you prefer. Then click "OK".

Now your stream will be available at```
http://xx.xx.xx.xx:1234
```Replace "xx.xx.xx.xx" with your computer's LAN IP address. Other clients in the LAN should be able to connect to it. You can start and stop streaming at any time using VLC's play and stop buttons.

Some additional info:

The TTL value field at the bottom of the output stream configuration dialog determines whether or not the stream is visible beyond your LAN. If you increase the TTL value and forward port 1234 in your router, the stream will be accessible from the internet.

If your playlist is actually a list of items (e.g. locally stored audio files), VLC will reset the stream between items, causing all clients to reconnect. This may be useful sometimes, but usually it is not. You can change this behavior in "Settings --> Preferences --> Stream Output". Click "Advanced Options" in the lower right, then enable "Keep stream output open".

---

### Post by kwacka on 2008-10-03
That's great - many thanks.

'RAW' is what i was missing.

---

