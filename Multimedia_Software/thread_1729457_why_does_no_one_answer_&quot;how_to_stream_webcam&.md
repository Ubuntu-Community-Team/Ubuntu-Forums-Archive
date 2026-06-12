---
title: "why does no one answer &quot;how to stream webcam&quot;?"
date: 2011-04-14
forum: Multimedia Software
---

### Post by rebeltaz on 2011-04-14
I have asked this once before, and I have spent the past hour going through previous posts by other users on here (and yes, I searched Google) asking how to stream a webcam over their home network. No one has given an answer - much less a straight one.

I have a USB webcam that I want to attach to a computer. I want to be able to stream the output of that webcam so that I can view that video from any other computer on my home network. I have seen that this can be done using vlc, but I cannot get it to work.

Surely, there is SOMEone out there who can provide a step by step on doing this!!!

---

### Post by hsoulen on 2011-04-15
Try this with VLC:

```
# vlc v4l:/dev/video0:size=320×240 –sout “#transcode{vcodec=WMV1,vb=180,scale=1}:duplicate{dst=display, dst=std{access=mmsh,mux=asfh,dst=:12345}}” -v –noaudio
```

This will start the MMS server on port 12345 with 180 kbps and resolution of 320×240.

To view the stream in Your client machine, start Windows Media Player, choose File/Open URL… and type:

mms://your_server_address:12345

Hank

---

### Post by Enigmapond on 2011-04-15
> **rebeltaz said:**
> I have asked this once before, and I have spent the past hour going through previous posts by other users on here (and yes, I searched Google) asking how to stream a webcam over their home network. No one has given an answer - much less a straight one.  

No need to get hostile. We are all volunteers here and have lives other than "working" the forum. If you don't get the answer you need right away, be patient and if anyone does, they will  chime in. If you insist on an immediate response to your queries, might I suggest contacting Canonical and paying for support?

Good Luck.

---

### Post by hsoulen on 2011-04-15
> **Enigmapond said:**
> No need to get hostile. We are all volunteers here and have lives other than "working" the forum. If you don't get the answer you need right away, be patient and if anyone does, they will  chime in. If you insist on an immediate response to your queries, might I suggest contacting Canonical and paying for support?

Good Luck.

Well said :D

But I answered anyway because I am a nice guy.

---

### Post by saugatad on 2011-04-15
You can try cheese. Simple Application wide variety of support or guvcviews.

---

### Post by rebeltaz on 2011-04-15
> **Enigmapond said:**
> No need to get hostile. We are all volunteers here and have lives other than "working" the forum. If you don't get the answer you need right away, be patient and if anyone does, they will  chime in. If you insist on an immediate response to your queries, might I suggest contacting Canonical and paying for support?

Good Luck.

I wasn't being hostile... I'm sorry if it came across that way. And I wasn't expecting a "quick" answer. I posted my original request February 17, 2010. Over a year ago. I think I was VERY patient. And other threads that I looked at with no answers were from back in 2008! Again, if I sounded hostile, I apologize, but that wasn't my intention.

@hsoulen: Thank you for the response. I will try that tonight. If I have any trouble with it, I hope you won't mind if I come back and request a little more of your kindness... :)

---

### Post by hsoulen on 2011-04-15
> **rebeltaz said:**
> I wasn't being hostile... I'm sorry if it came across that way. And I wasn't expecting a "quick" answer. I posted my original request February 17, 2010. Over a year ago. I think I was VERY patient. And other threads that I looked at with no answers were from back in 2008! Again, if I sounded hostile, I apologize, but that wasn't my intention.

@hsoulen: Thank you for the response. I will try that tonight. If I have any trouble with it, I hope you won't mind if I come back and request a little more of your kindness... :)

No worries mate, frustration can sometimes look like hostility ;)

Remember that the codec, scaling, video size and port are all variables so don't give up if it does not work on the first try. Try a different codec or port and check the VLC documentation, it can be a bit daunting but you'll get the hang of it.

And yes by all means post your results and we'll continue to work to solve it for you.

Cheers,

Hank

---

### Post by rebeltaz on 2011-04-16
Well, I got the server to run (I think) but I had to change v4l:/dev/video0 to v4l2:///dev/video0 and it asks like it's running, but I can't seem to pull it up with anything. I tried pulling it up with Totem Movie Player on the same machine and on Windows Media Player from another computer. WMP just says that it can't find the stream and Totem shuts itself down. 

Can you access the stream from the same computer just for test purposes? And I notice that there is no IP address in front of the :12345 port address in the command line that you provided. Do I need to give an IP address is does it assume the same address as the computer it's being run from? 

Thanks...

---

### Post by hsoulen on 2011-04-16
> **rebeltaz said:**
> Well, I got the server to run (I think) but I had to change v4l:/dev/video0 to v4l2:///dev/video0 and it asks like it's running, but I can't seem to pull it up with anything. I tried pulling it up with Totem Movie Player on the same machine and on Windows Media Player from another computer. WMP just says that it can't find the stream and Totem shuts itself down. 

Can you access the stream from the same computer just for test purposes? And I notice that there is no IP address in front of the :12345 port address in the command line that you provided. Do I need to give an IP address is does it assume the same address as the computer it's being run from? 

Thanks...

Well it sounds like you are making progress. To be perfectly frank I have only ever gotten the command line to work with VLC when I compile from source.

Couple of notes from my experience, I have NEVER gotten it to work with wmv/mms... UDP/HTTP work fine and you can use mp4 or mpeg2 for your video.

You might need another escape in your call to v41 "v4l:///dev/video0"

You can also try Video for linux 2 (v4l2) for streaming as it may work better.

Last thought, try using the GUI to setup streaming, just choose it from "Media" and if you decide to use HTTP leave the default port (8080) and leave the default path ("/") and it should work. I have found messing around with the GUI and then just copy/past the command line when you get it working.

And yes, you can test it using totem/mplayer (maplayer would be my choice) from the same machine using IP or "localhost".

Let me know how it goes.

Hank

---

### Post by rebeltaz on 2011-04-16
Making progress! 

Working first with my laptop I was able to deduce this command-line:

```
vlc v4l2:///dev/video0 --sout "#transcode{vcodec=h264,vb=800,scale=1}:std{access=http,mux=ts,dst=192.168.1.5:8080}" –noaudio
```

I can then point Totem to the IP address and I have streaming video. SO then I install vlc on the computer I want to set this up on and issue the same command (substituting v4l in place of v4l2) and I get this output:

```

[00000283] main private: creating httpd
status change: ( new input: v4l:///dev/video0 )
status change: ( audio volume: 256 )
status change: ( play state: 1 )
[00000288] v4l demuxer error: chroma selection failed
[00000288] v4l demuxer error: cannot open audio device (Device or resource busy)
[00000288] v4l demuxer error: cannot open device (No such file or directory)
[00000288] v4l demuxer error: cannot open audio device (No such file or directory)
[00000290] vcd access error: could not read TOCHDR
[00000290] vcd access error: no movie tracks found
[00000290] access_file access error: cannot open file /dev/video0 (Device or resource busy)
[00000275] main input error: no suitable access module for `v4l:///dev/video0'
status change: ( stop state: 0 )
[00000303] main private: creating httpd
status change: ( new input: –noaudio )
status change: ( audio volume: 256 )
status change: ( play state: 1 )
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat –noaudio
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000298] main input error: no suitable access module for `–noaudio'
[00000267] main playlist: nothing to play
status change: ( stop state: 0 )

```

By removing the '-noaudio' option, I can get the message down to: 

```

[00000283] main private: creating httpd
status change: ( new input: v4l:///dev/video0 )
status change: ( audio volume: 256 )
status change: ( play state: 1 )
[00000288] v4l demuxer error: chroma selection failed
[00000288] v4l demuxer error: cannot open audio device (Device or resource busy)
[00000288] v4l demuxer error: cannot open device (No such file or directory)
[00000288] v4l demuxer error: cannot open audio device (No such file or directory)
[00000290] vcd access error: could not read TOCHDR
[00000290] vcd access error: no movie tracks found
[00000290] access_file access error: cannot open file /dev/video0 (Device or resource busy)
[00000275] main input error: no suitable access module for `v4l:///dev/video0'
status change: ( stop state: 0 )
[00000267] main playlist: nothing to play

```

I tried installing 'v4l-conf' and it's associated dependencies, but that didn't make a difference. Does it matter that the computer I want to run this command on does not have a GUI installed? It is simply a command-line server system. 

You have been a great help so far, so if you have any other ideas and am willing to try anything! :) Thanks...

---

### Post by hsoulen on 2011-04-18
Ok, well you said something very important here... Your streaming server has no GUI!!!

You will need the command line for VLC not the GUI version or it will not work.

Try the below using "cvlc" which is the command line only (replace the IP with your streaming server of course):

```
cvlc v4l2:///dev/video0:width=320:height=240:fps=12 --sout '#transcode{vcodec=h264,vb=800,scale=1}:duplicate{dst=std{access=http,mux=ts,dst=192.186.0.1:8080}}' --noaudio &
```

Edit: You will notice the "noaudio" option has two "-" not one "--" and the quotes around the transcode options should be single "'" not double.

Let me know!

Cheers,

Hank

---

### Post by GangusKhan on 2011-04-18
Try running vlc from windows on wine?

---

### Post by hsoulen on 2011-04-18
> **GangusKhan said:**
> Try running vlc from windows on wine?

Ugh...

Why complicate things? The command line options are just as complex with the windows version and as he stated he has no GUI on the streaming server so using wine in this case is just a pain, plus who uses windows software anyway :D

But hey, any suggestion is a good one and it's always good to see folks with suggestions.

Happy "chomputing"

Hank

---

### Post by rebeltaz on 2011-04-18
Like you said, why use a Windows program when there's a Linux version?

Anyway, I had tried cvlc before but I get 

```
-bash: cvlc: command not found
```

I tried doing a apt-cache search for cvlc, but it doesn't return any results. That command works fine on my laptop. Is cvlc not available on Gutsy 7.10?

Yes, I know it's old and out of date, but up until now it's worked flawlessly without any problems. And unlike the rest of the world, I don't believe that newest is always better.  ;-)  I'd rather not upgrade a working system if I can avoid it. I probably should have mentioned the version before, but I didn't think that that would matter.... Sorry.

---

### Post by hsoulen on 2011-04-19
> **rebeltaz said:**
> Like you said, why use a Windows program when there's a Linux version?

Anyway, I had tried cvlc before but I get 

```
-bash: cvlc: command not found
```

I tried doing a apt-cache search for cvlc, but it doesn't return any results. That command works fine on my laptop. Is cvlc not available on Gutsy 7.10?

Yes, I know it's old and out of date, but up until now it's worked flawlessly without any problems. And unlike the rest of the world, I don't believe that newest is always better.  ;-)  I'd rather not upgrade a working system if I can avoid it. I probably should have mentioned the version before, but I didn't think that that would matter.... Sorry.

Dude! You're killing me here :(

I think you may be out of luck running 7.10 with VLC unless you go the "compile yourself" route.

I am pretty sure any debs you find are going to be way out of date and not support a bunch of features you may be looking for (transcoding to certain formats etc.) so your options are a bit limited here.

My recommendation would be to upgrade to minimum of Hardy (8.04) and go from there, trying to compile the latest VLC from source on a distro that far back is going to lead you down a very slippery dependency and compiler slope which may not be worth it.

If you decide to try and compile, post your results and we'll see what we can do to assist and the same goes for any upgrade issues.

If your concern for upgrading is hardware spec no worries, you are running a cli server anyway and you can always "dissclude" (not an actual word) any software you don't need for your install.

Cheers,

Hank

---

### Post by rebeltaz on 2011-04-19
:lolflag:  Yeah... I thought as much. I may look into upgrading this weekend. Gotta back everything up and pray first!  Thanks for your help. I'll let you know how it goes...

---

