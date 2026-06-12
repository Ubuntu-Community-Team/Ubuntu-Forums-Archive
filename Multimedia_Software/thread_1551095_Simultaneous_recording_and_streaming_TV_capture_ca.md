---
title: "Simultaneous recording and streaming TV capture card data"
date: 2010-08-11
forum: Multimedia Software
---

### Post by Thallant on 2010-08-11
Greetings, I'm attempting to create TV capture solution for a website I'm working on. I have an Ubuntu box with a crappy Pinnacle TV capture card plugged in. After mucking with drivers and codecs I finally got the card to work in Ubuntu with MythTV and Mplayer so that I can watch cable TV through the capture card. I couldn't get FFmpeg to work because I couldn't figure out the command line option to set the tuner channel like you do in mplayer with -tv channel=4:norm=NTSC.
 
The problem I have now is both conceptual and technical. Basically, using the single TV capture input I need to be able to Record, and Stream LIVE (via flash or WebM). What is the best tool/methodology for accomplishing this task? MythTV? VLC? FFmpeg? Mplayer? In addition, the whole system needs to be, somewhat, command line driven (or at least database driven), so eventually I can control the action externally through a CMS.
 
My first attempt was using MythTV. The problem I ran into is I couldn't figure out a way to stream it online live in flash format.
 
My second attempt was using mencoder and then stream that file (while it is being generated) over the internet using Red5. Yet, while thinking about it, if I was to view the stream 5 minutes after it started would I start at the beginning of the file, or the current position in the file (afterall the purpose is for it to be a LIVE stream, not a start-of-file stream)?
 
My third idea was using something like VLC, which is what I've been mucking with while at work with a windows machine. The problem I have is that VLC has been crashing and behaving terribly. I set it up, click the stream button but nothing happens, no error message, no success message, it's like I didn't do anything. When I get home I plan on testing it on Ubuntu to see if it operates better there.
 
My 4th idea was using something like ffmpeg and ffserver. The dilemma I ran into is that usually you have to send the TV capture to a .ffm which is then transmitted by the ffserver... But once it's complete, say after a half hour TV show, how do I dump or recieve that flash file that was generated?
 
If anyone has any guidance it would be much appreciated. I'm beginning to think the best solution is just use Adobe's Flash Media Encoder for Windows, but that seems like a total cop out solution. I would *really* rather not do that, but if I can't figure out a way with Ubuntu, I may have to.

---

### Post by Jonie on 2010-08-15
Don't know whether it helps you, but you can always split the video stream (or rather "tee") into two or more processes:

cat /dev/video0 | tee >( command to encode to a live stream ) | command to encode to a file

both commands should use standard input as their source, like mplayer -

By piping into further tees it's possible to redirect the stream to as many processes as you like provided your computer is able to handle them all.

---

### Post by Jonie on 2010-08-15
or better, tee the encoded stream into your streaming server and into a file:

cat /dev/video0 | command to encode | tee >( live stream handler ) > file

---

