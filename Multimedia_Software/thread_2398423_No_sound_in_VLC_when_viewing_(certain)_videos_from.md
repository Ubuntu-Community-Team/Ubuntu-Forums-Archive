---
title: "No sound in VLC when viewing (certain) videos from NAS"
date: 2018-08-11
forum: Multimedia Software
---

### Post by cellsplitter on 2018-08-11
I decided to try out Ubuntu over the weekend to check it out and here is a issue I bumped into that I could not figure out.

When playing some video files with VLC that are located on my NAS (Qnap to be precise) there would simply be no audio.
However, other videos WOULD work so it's not even a 100% certainty which makes it even harder to troubleshoot.

Here's an image of the codecs running on a video when viewed from the NAS.

[IMG]https://i.imgur.com/3OFtLSr.png[/IMG]

And here is the same video but running off the desktop.

[IMG]https://i.imgur.com/bI6IR3E.png[/IMG]

All of a sudden it finds the audio track. It's the exact same video file but played locally instead.

I've looked around for possible solutions but none have worked for me.
I'd appreciate any help I can get.

---

### Post by mc4man on 2018-08-11
No idea about nas, don't have. 
Maybe while waiting for someone who does you could see if it's possibly that audio file or maybe  vlc is only gong to find stream 0 for some reason (or these don't matter..

To do so install ffmpeg (- sudo apt install ffmpeg

Then with the file in question visible in the file manager open a terminal (ctrl+alt+t

Paste  this in, hit the spacebar, then DnD the video on to the terminal. Click on terminal to return focus, hit spacebar again, then copy & paste 2nd command into terminal ,  press enter. If all works you'll find test1.mp4 in your home folder. Tranfer to nas, try vlc on it
(command makes audio stream 0, video stream 1
```
ffmpeg -i
```
```
-map 0:1 -map 0:0 -c copy test1.mp4
``` 

(- in case I'm being confusing above, example here, blue is result of the DnD, ect.
```
ffmpeg -i  [COLOR="#0000CD"]'/home/doug/Videos/Jessie J.mp4' [/COLOR] -map 0:1 -map 0:0 -c copy test1.mp4
```


Is this only happening when audio is .mp4a  vs .m4a or .aac?

---

### Post by cellsplitter on 2018-08-14
I'm starting to believe it has to do with SMB sharing and how it doesn't work 100% on streaming some videos.
Been trying to setup and mount a NFS share instead but it isn't easy.

---

