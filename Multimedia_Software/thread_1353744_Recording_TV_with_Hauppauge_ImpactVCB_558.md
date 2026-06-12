---
title: "Recording TV with Hauppauge ImpactVCB 558"
date: 2009-12-13
forum: Multimedia Software
---

### Post by angelsguitar on 2009-12-13
Hi.

I recently purchased a [Hauppauge ImpactVCB model 558 video capture card]("http://www.hauppauge.com/site/products/data_impactvcb.html") (very cheap on Ebay!) with the idea of being able to watch and record TV on my computer.

I know that this is not a TV Tuner; as I understand it, this type of card is designed to be used for camera security systems.  Also, this card doesn't have any audio ins or outs; just 3 video rca and one s-video, no audio ports. However, I'm currently using it with TV Time and can watch the video out of my satellite box without problems, running the audio through the audio card of my computer.

So, what I need is a way to record the video that I'm getting with the ImpactVCB along with the audio with the audio card of my computer.  My capture card is not a TV Tuner, so I feel that MythTV may be a little too much for what I need to do (but I may be mistaken??)

How can I just record the video+audio output of my satellite box? What software can I use for that?

---

### Post by angelsguitar on 2009-12-13
Bump :(

---

### Post by 73ckn797 on 2009-12-13
I am considering using this capture card.

I believe there are ways to do what you want but cannot immediately recall where I have read about it. I will look around myself and let you know what I find. Hope you find info to share also. Google may be a friend in this search.

---

### Post by angelsguitar on 2009-12-14
Short Update: I believe this could be possible using VLC. I'm looking for some info about it, or a nice how-to...

---

### Post by xc3RnbFO8P on 2009-12-14
Check output of **dmesg** in Terminal and  this:
[http://www.zoneminder.com/]("http://www.zoneminder.com/")

---

### Post by angelsguitar on 2009-12-14
I looked into zoneminder, but currently it doesn't record audio.  It is more oriented towards surveillance systems.

Thanks anyway. Any other ideas are welcome.

---

### Post by HappyFeet on 2009-12-14
Try 
```
cat /dev/video0 > /home/your_user_name
```
Doing that, I can record TV to my home folder.

---

### Post by angelsguitar on 2009-12-14
> **HappyFeet said:**
> Try 
```
cat /dev/video0 > /home/your_user_name
```
Doing that, I can record TV to my home folder.

Ok, I did 

```
cat /dev/video0 > /home/my_user_name/test
```

and seems to be recording, but after that I can't open the file.  It gives an error stating that the file type is unknown.  How do you open the recorded file? What type of media file does it record?

On the other hand, I tried recording with VLC, using the "Open Capture Device" option, but could only get a small video output, barely visible.  Seems there's a problem with resolution, but I don't know how to fix that.  A screenshot is attached.  Any ideas?

---

### Post by LowSky on 2009-12-14
you might need a file extention
like **file.*mp4***

and on VLC, what happens if you go full screen?
See the tab named _View_ check under that to see if there is an option to increase the size

---

### Post by angelsguitar on 2009-12-15
> **LowSky said:**
> 
and on VLC, what happens if you go full screen?
See the tab named _View_ check under that to see if there is an option to increase the size

Same happens if I go full screen, already tried that one.

I see no option to increase size under the View tab. Maybe there's something on the Tools - Preferences section, but honestly I don't know what to look for.

---

### Post by angelsguitar on 2009-12-20
Searching around the net I stumbled upon Cinelerra.  Is Cinelerra able to record from a capture card, or it is just for editing purposes?

---

### Post by Marlonsm on 2009-12-20
> **angelsguitar said:**
> Searching around the net I stumbled upon Cinelerra.  Is Cinelerra able to record from a capture card, or it is just for editing purposes?

It's meant for editing. But it can also record video and audio inputs, so you could try, I just don't know if it's possible to select the channels using it.

---

### Post by angelsguitar on 2009-12-20
> **LowSky said:**
> you might need a file extention
like **file.*mp4***

Tried it with .mp4, and seems to be recording something (it creates the file), but I get the following error when I try to open the recorded file with Totem:

```
Could not determine type of stream.
```

---

### Post by angelsguitar on 2009-12-20
> **Marlonsm said:**
> It's meant for editing. But it can also record but video and audio inputs, so you could try it.

I'll give it a try thanks.

---

### Post by 73ckn797 on 2009-12-26
What has been the results on using the video capture card?

I now have the same card and will be installing it. I will post what my results are. I will be using it to capture old home movies from 8mm camera and VCR tapes.

---

### Post by MartyBuntu on 2009-12-26
This card does not have a hardware MPEG-2 encoder built in.

Honestly, if you even get captures going with a software solution, they will look like garbage.

If you can get an older Hauppauge PVR 150/250/350 on eBay for cheap, do that.

---

### Post by 73ckn797 on 2009-12-26
I am giving this video capture card a go. I get sound by going through the sound card and it comes through when using Kdenlive but I get no video at all no matter what I use. Any suggestions?

lspci:
```
01:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

```It is recognized.

---

### Post by MartyBuntu on 2009-12-26
Have you tried **tvtime**?

---

### Post by 73ckn797 on 2009-12-26
> **MartyBuntu said:**
> Have you tried **tvtime**?

Not yet!!

Tvtime installed and it does pickup video quite well. I cannot make video show in any other program (Kino, Cinelerra, VLC or any other program with capture capability).

---

### Post by angelsguitar on 2009-12-27
> **73ckn797 said:**
> Not yet!!

Tvtime installed and it does pickup video quite well. I cannot make video show in any other program (Kino, Cinelerra, VLC or any other program with capture capability).

The same for me. Right now all I can do is watch the video output of my satellite box through tvtime, running the audio through the integrated audio card of my computer, but nothing more.

The only option I can think of that could work is using ffmpeg through the command line.  I'm searching around for the right options to pass to ffmpeg to be able to do this.

...Or maybe I should get another card, as someone suggested earlier.  This card seems more oriented for security purposes (like runing some CCTV cameras through it for surveillance purposes)

Anyway, if anyone is succesfull in recording something (specially tv) with this card, please share; it will be greatly appreciated.

---

### Post by MartyBuntu on 2009-12-27
> **MartyBuntu said:**
> 
Honestly, if you even get captures going with a software solution, they will look like garbage.

If you are truly looking for a half way decent capture solution you are heading down a dead end.
Consider the fact that you can actually watch TV with this card and call it a day.

---

### Post by angelsguitar on 2009-12-27
> **MartyBuntu said:**
> If you are truly looking for a half way decent capture solution you are heading down a dead end.
Consider the fact that you can actually watch TV with this card and call it a day.

It seems I got the wrong tool for the job.

Right now I'm looking at the Hauppauge PVR 150, which seems like a good option for what I intend to do.  I know this one only handles analog sources, but that shouldn't be a problem as I'll use my DirecTV satellite box to decode and change channels, and use the card to record the output of the satellite box (either by SVideo, RCA or Coaxial cable)

---

### Post by MartyBuntu on 2009-12-27
> **angelsguitar said:**
> 
Right now I'm looking at the Hauppauge PVR 150

Now we're talkin'!

I use the PVR 150  for TV captures which I then edit with AviDemux.
The quality is pretty good.

If there's anything you need to know about getting this card to work, just ask me. Also, I understand that HappyFeet is knowledgeable in this. You can ask him too.

---

### Post by angelsguitar on 2009-12-27
> **MartyBuntu said:**
> Now we're talkin'!

I use the PVR 150  for TV captures which I then edit with AviDemux.
The quality is pretty good.

If there's anything you need to know about getting this card to work, just ask me. Also, I understand that HappyFeet is knowledgeable in this. You can ask him too.

I just got one on ebay!

I'll post back when I receive it.  Thanks for the info, and for offering your help.

---

### Post by 73ckn797 on 2009-12-27
At least my video card was a present and I did not spend a dime on it.

I will also look into the 150. 

I was able to get tvtime to show the video very clearly.

---

### Post by saedelaere on 2009-12-28
In any case someone need a software to watch and record TV using a Hauppauge PVR-150 give [TV-Viewer]("http://ubuntuforums.org/showthread.php?t=763698&page=14") a go.

Best regards

---

### Post by angelsguitar on 2010-01-05
Well, got my PVR-150 yesterday. A pretty good deal, I must say; it came with an ir blaster cable and remote controller plus a few extra cables 8-)

What can I saw? What a big, BIG difference!!!!! Highly recommend it; I should've gotten one of these on first hand. I'm truly satisfied now :)

@saedelaere: I installed [TV-Viewer]("http://home.arcor.de/saedelaere/index_eng.html") and gave it a shot.  Very good app, and user friendly.  Had to install some dependencies and fix some sym-links, but after that it all ran smooth.  In a few minutes I was recording from my satellite box.  Very nice work. TV-Viewer rocks! :guitar: :guitar:

---

### Post by johnaaronrose on 2010-03-12
I tried to install TV-Viewer 0.8.1. I got:
administrator@JohnLaptop:~/Software/TV-Viewer/tv-viewer-0.8.1$ sudo ./tv-viewer_install.tcl
Program error. You'll need Tcl version 8.5 or higher.

Found version: 8.4.19

How do I upgrade tcl in karmic?

---

### Post by angelsguitar on 2010-03-12
> **johnaaronrose said:**
> I tried to install TV-Viewer 0.8.1. I got:
administrator@JohnLaptop:~/Software/TV-Viewer/tv-viewer-0.8.1$ sudo ./tv-viewer_install.tcl
Program error. You'll need Tcl version 8.5 or higher.

Found version: 8.4.19

How do I upgrade tcl in karmic?

Both tcl8.4 and tcl8.5 are on the repos.  Just do

```
sudo apt-get install tcl8.5
```

That should get you going.

---

