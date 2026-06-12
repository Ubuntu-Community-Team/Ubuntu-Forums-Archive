---
title: "avserver rotate stream temp files"
date: 2013-05-15
forum: Multimedia Software
---

### Post by chegancasb on 2013-05-15
Hi,

I've been playing around with avserver & avconv (ffserver & ffmpeg replacements in my Ubuntu version 12.04) to make a real live audio stream.

I've got that to work. I'm able to stream the audio and receive it on another house room with up to a few seconds delay (enough to hear when my 4 month old kid wakes up).

My question is: On the avserver configuration file (posted below) I need to set a file where the audio stream is  being written and set a maximum allowed file size. My system has very little disk space available and as I wanted to leave the working continuously and reliably during long periods of time I need to restrict this file size, without, if possible, not having to stop and restart the server to reset the file.

Is there a way to do one of the following?
        Not use a file at all - stream what is being captured at that instance and discard what has been captured before (I've tried to use /dev/null as destination file but didn't work);
     Re-use the same file after is has reached the maximum file size (start-over). 
     Set more than one file to use as tmp file (either explicitly or by some sort of wildcards) and rotate between them. 

There might be more possibilities to handle this that I haven't thought of... Suggestions are welcome.

Thanks.

# Server Configuration
Port 167761
MaxHTTPConnections 20
MaxClients 5
MaxBandwidth 50000
CustomLog -
NoDaemon

<Stream status.html>
  Format status
  FaviconURL [http://pond1.gladstonefamily.net:8080/favicon.ico](http://pond1.gladstonefamily.net:8080/favicon.ico)
</Stream>

# Redirect index.html to the appropriate site
<Redirect index.html>
  URL [http://www.libav.org/](http://www.libav.org/)
</Redirect>

<Feed FBedRoom.ffm>
  _**File /home/astream/AudioStream/FBedRoom.ffm**_
  _**FileMaxSize 200M**_
  Launch /usr/bin/avconv -f alsa -i plughw:1,0
</Feed>

# MP3 audio
<Stream FBedRoom.mp3>
  Feed FBedRoom.ffm
  Format mp2
  AudioCodec mp2
  AudioBitRate 32
  AudioChannels 1
  AudioSampleRate 22050
  NoVideo
  PreRoll 0
</Stream>

---

