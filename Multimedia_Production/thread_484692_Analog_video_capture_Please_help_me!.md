---
title: "Analog video capture: Please help me!"
date: 2007-06-26
forum: Multimedia Production
---

### Post by stoodleysnow on 2007-06-26
I have tried everything including the kitchen sink to try and get a simple GUI video capture app working on my PC so I can copy videos from VHS to DVD (PAL UK) and occasionally record TV programs. I need to use the analog tuner part of my Pinnacle TV card for this, as the S-Video will be otherwise engaged. My system spec is as follows:
:D
Asus P5B motherboard
Intel Core 2 Duo 2.13Ghz CPU
1 GB DDR2 RAM
500GB Sata Hard Drive
IDE DVD ROM drive
IDE DVD+/-RW drive
Internal USB Smart card reader
1.44MB Floppy disk drive
Hiper 400 or 450W (I forgot) PSU
3 system fans and a Cooler Master ATCs Chassis, so it's cool enough.
Nvidia Geforce 7600 SLI ready PCI-E 16x Graphics card
Dial up modem (just in case)
Pinnacle PCTV 40/50/110i (I think that's what it's called) TV card with analog tuners for TV and FM radio and S-Video inputs.
Ubuntu 7.04 installed with Compiz-fusion WM

The questions I need answering:
What application will provide a simple GUI to capture video files from the analog tuner (and S-Video if needed) without resorting to command lines and complex configurations to get it working?:-k
How do I install that application in a way which allows me to still use my PC as normal, and only bring up that app if I need it?:neutral:
How do I then use that app?:???:

In case you hadn't gathered, I'm a hardware person, and can't do with software and it's complicated codes, scripts and errors.](*,)
All I ask is for a free open-source OS that can do more than M$ can dream of. :wink: That's not too much to ask, right?

right???
Yours hopefully
stoodleysnow

---

### Post by derby007 on 2007-06-26
I havent managed 'easy' recording yet, ie. MythTV (video will be in .nuv format), but try out ProjectX for demuxing & DVDAuthor for authoring.

---

### Post by dad311 on 2007-06-26
For transfering from VHS-DVD I use a [ADVC110]("http://www.canopus.com/products/ADVC110/index.php").  Works great with Kino.

---

### Post by stoodleysnow on 2007-06-26
derby007, can .nuv be converted to MP2?:?: and dad311, your method sounds great but I'm on a tight budget (all money spent on the PC):rolleyes:

---

### Post by stoodleysnow on 2007-06-26
And I already have dvd95, dvd ::rip, gxine, gxvattr, LIVES, Pitivi, TVTime (which won't pick up the tv signal), XawTV (which seems to be equally unfathomable) and Zapping TV Viewer (which closes if I click on anything)
:(
told you Ive tried everything including the kitchen sink.;)

---

### Post by fsman on 2007-06-27
I use a kworld analogue capture card from ebay - cheap and does the job.
I've found that you need to do a bit of searching of "video4linux" website etc. to try to identify your chipset.
personally i've never been successfully with a gui tool.

i've found that mjpegtools and/or lavrec works fine for me. But it was trial and error to get it working.

---

### Post by stoodleysnow on 2007-07-03
Does anyone else have any ideas?:?:

---

### Post by Steve.the.Goolie on 2007-11-23
Eyup!

I (along with many others it would seem) am having the same problem, there is no gui to give a simple solution to analogue recording.
So I looked at ways to avoid all the tedious typing into the terminal just to get lavrec to do something and came up with this (until I have learned a bit of programming skills!)

I have a Pinnacle DC10+ card with composite and SVideo inputs and wanted to record from my analogue camcorder to the SVHS input.

I looked at the following website to find all the lavrec commands.

[http://linux.die.net/man/1/lavrec](http://linux.die.net/man/1/lavrec)

Then I played with the commands, typing them into the terminal until I came up with something that worked for me. The commands are not complicated, they are just single letters preceded by a hyphen and sometimes followed by a number.

I then typed the command string into an ordinary text file and saved it with the name "record"

Then I right clicked on the just saved file and chose "properties"

In the properties dialogue there is an option where it says "run this file as a program" if you tick this option, when you double-click the file, a dialogue opens which asks if you want to open or run the file. If you choose run, it will run it in the terminal, so no need to do any more typing!

The string I used looked like this:

[COLOR="Red"]-fa -iP -d1 -q50 test.avi[/COLOR]

[COLOR="red"]-f [/COLOR]means "format" (lavrec will record .avi or .qt movies)
[COLOR="red"]a[/COLOR] means "record using hardware MJPEG encoder"

[COLOR="red"]-i[/COLOR] means "input"
[COLOR="red"]P [/COLOR]means "record PAL from SVHS input"

[COLOR="red"]-d1[/COLOR] means "record picture at full size"

[COLOR="red"]-q50[/COLOR] means "record with quality level of 50%" (adequate for SVHS in my opinion)

[COLOR="red"]test.avi[/COLOR] is the filename it will save the recording as.

Press [COLOR="red"]ctrl-c[/COLOR] to stop recording!

There are many other commands, all explained on the website.

I hope this is some help, I have many home videos I want to transfer to DVD so I hope to learn enough to be able to program a *simple* gui to do the job :confused:

I have also abandoned the idea of being able to edit the video in Ubuntu, the programs available simply do not work, I wish they would.

Steve

---

### Post by stoodleysnow on 2008-03-07
I've found plenty of editing apps, just no analogue capture apps that work. Has anything new appeared recently?
BTW, there's a USB capture dongle available from Dazzle with composite and S-Vid inputs. Would that work with Kino?

---

### Post by kc8hr on 2008-03-17
> **stoodleysnow said:**
> I've found plenty of editing apps, just no analogue capture apps that work. Has anything new appeared recently?
BTW, there's a USB capture dongle available from Dazzle with composite and S-Vid inputs. Would that work with Kino?

Hi,

I use motv. It's not pretty, but it works pretty well. It is availabe in the repository.

Good Luck!
Tim

---

### Post by cotcot on 2008-03-17
I am searching as well. I installed TVTime to check if i get the VHS on my PC through the composite connector. That is OK. (I have the camcorder connected with the PC with the yellow composite and the sound with a seperate cable composite (RCA) to 3.5 mm jack to plug in the microphone in of the tv-card.
With ```
mencoder -tv norm=PAL:driver=v4l2:width=720:height=576:input=1:fps=25 tv:// -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf pp=lb/ha/va/dr,hqdn3d,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1500:vrc_maxrate=8000:vbitrate=7000:keyint=15:acodec=mp2:abitrate=192:aspect=4/3 -o capture.mpg 
``` I can capture video and sound, but the sound is of bad quality. So i record the sound separately with the sound recorder (see applications menu). I am going to combine the audio file and video file with cinelerra or blender. 

This is the best i found up till now.

---

