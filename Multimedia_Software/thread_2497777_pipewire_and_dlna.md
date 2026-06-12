---
title: "pipewire and dlna"
date: 2024-05-16
forum: Multimedia Software
---

### Post by goodstuff9 on 2024-05-16
Ubuntu 22.04.4, Gnmome shell, Wayland, and pipewire.  Also have Rygel running.  

How do I "tell" my computer to send it's audio output out to a dlna client?  I can't see anywhere where I can make that selection.  I don't know what I'm missing or doing wrong.

---

### Post by TheFu on 2024-05-18
DLNA has 3 parts.
[LIST=1]
[*]Controller
[*]Renderer
[*]Server
[/LIST]

No such thing as a "DLNA client."

They can be on the same device or 3 different devices.

**The renderer** is the device that actually decodes the video and audio and subtitles/captions and displays/outputs the sound on them to a screen or speakers.

**The server** is where the media is stored.  It uses a file transfer.  It doesn't send video output nor audio output. Rather, it sends either the raw file or some DLNA media servers like Jellyfin, Plex, or Emby can transcode from the codes on the file they have into the type required for the "renderer".

**The controller** is the part that humans use to connect to a server and tell it where to send files for rendering.

So, if your PC is your DLNA server and you are trying to use a different renderer device, it is up to the server to know (or be told somehow) that the file type the server has will not work on the target rendering device.

In short, the server doesn't usually touch any audio directly, so telling it where to send it isn't a separate thing.  The video/audio file (say inside an mp4 or mkv container file) is transferred to the renderer when the controller tells the DLNA server to do so.  If there isn't any transcoding, the controller is done and the server simply transmits the file in the container to the render for playback.

Clear as mud?

I think Rygel is a minimal DLNA server, so it cannot transcode anything and it would be up to the DLNA Renderer to do whatever is needed to support video and/or audio playback for the provided file.

So ... what is the renderer device and which exact video and audio codecs does it support?  If you look inside the source file on the DLNA server (mediainfo is a tool for that), you can verify that the source file codecs are or are not supported by your player (DLNA renderer).

In general, all player devices can support h.264/aac codecs in either an MP4 or MKV container.  Not all players can support the newer h.265 (aka HEVC) video codec.  When it comes to audio formats, that can be extremely specific to the audio equipment you are using.  For example, DTS or DD+ may need to be converted to a different audio codec to be played.  Vorbis, AAC, mp3, are usually safe bets.   If you are sending the audio to a home audio receiver, then you'll need to see which audio formats they support over HDMI, TosLink, or another connector.  

And don't get me started about the different HDMI/HDCP standards.  In many situations, resolutions over 1080p won't work from Linux desktops because the HDMI/HDCP cartel thinks that all Linux users will pirate any 4K video, so they've rejected attempts to support the standards.  From March 2024 - [https://www.theregister.com/2024/03/02/hdmi_blocks_amd_foss/](https://www.theregister.com/2024/03/02/hdmi_blocks_amd_foss/)

---

### Post by goodstuff9 on 2024-05-19
Thanks very much for the explanation and clarification, that is helping me.  

After reading your explanation, here is what I tried to do - and so far it isn't working:  

On an Ubuntu 22.04.4 desktop computer (gnome shell, pipewire, and wayland - if any of that matters), I am running Rygel.  Also on this computer I have some mp3 music files, and I have VLC installed.  So that is the DLNA server.  In a different room connected to my stereo system is an old android device with its audio connected to the stereo, and it is running a DLNA renderer.  On the Ubuntu machine when I start VLC to play a song, and under VLC's menu options of playback >> renderers, it does not find the renderer on the old android device.  However, using a dlna controller on my main android device, I can find that mp3 music file on my Ubuntu computer and direct it to the renderer on the old android device no problem.  I can't figure out why VLC cannot find that dlna renderer on the old android device.  

Is this making sense?

---

### Post by gloster10 on 2024-05-24
Do you have installed minidlna and configured it correctly ? (You can check it with VLC (used as DLNA-Client) : Local Network -> Universal Plug + Play  -> YourPC:root will be indicated, 

also the respective directories of your minidlna Server (YourPC) -> Select the respective mp3-files)

If yes, take your TV remote control, choose source, you will get a list of server, e.g. your PC, the respective directories e.g.: music, videos.

Select the respective file you want (the server is passive, controlled by the TV).

If you have a Panasonic TV, you must enable the Server (TV : Network -> DLNA -> A list of devices in your home network will be indicated, select the respective MAC-Adress of your minidlna 

Server-PC and activate it on your TV).

---

### Post by goodstuff9 on 2024-05-26
> **gloster10 said:**
> Do you have installed minidlna and configured it correctly ? (You can check it with VLC (used as DLNA-Client) : Local Network -> Universal Plug + Play  -> YourPC:root will be indicated, 

also the respective directories of your minidlna Server (YourPC) -> Select the respective mp3-files)

If yes, take your TV remote control, choose source, you will get a list of server, e.g. your PC, the respective directories e.g.: music, videos.

Select the respective file you want (the server is passive, controlled by the TV).

If you have a Panasonic TV, you must enable the Server (TV : Network -> DLNA -> A list of devices in your home network will be indicated, select the respective MAC-Adress of your minidlna 

Server-PC and activate it on your TV).


Thank you.  

As I wrote originally, I have Rygel installed.  (I never installed minidlna.)  Just looking for clarification from you:  Are you telling me to give up on Rygel and switch to minidlna?

---

### Post by TheFu on 2024-05-27
I tried to use Rygel once a few years ago for temporary needs.  It didn't meet my needs. 

I'd used miniDLNA before and it has issues, but it works if you don't need transcoding and can manually refresh the list of media files when needed.  

I think miniDLNA has 1-2 config file settings needed - that's it - makes setup really easy.  Just set the location of the different types of media files to be available inside the miniDLNA conf file under /etc/.  Locations for Movies, TV, Music and perhaps Photos.  Is is only a DLNA-Server. Not a controller nor a renderer.  

I don't recall any interface at all, just make the location settings, start/restart the daemon, and tell it via a command line to re-read the media directories.  That's it.  Then go to your DLNA controller to wait for the media to show up.  Small collections happen in a minute. Huge collections might take a few hours for everything to be indexed.  Of course, the minidlna useraccount must have read-access to the media files.  That's normal for all media servers on any platform.

---

