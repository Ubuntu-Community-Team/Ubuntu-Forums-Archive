---
title: "Vodei File Format"
date: 2006-07-04
forum: Multimedia &amp; Video
---

### Post by Ted_Smith on 2006-07-04
I have a film that says that you need 'Vodei Multimedia Processor' to play it : [http://vodei.com/](http://vodei.com/). In their FAQ it says : 

[i]"Does Vodei MP run on Mac or Linux?

No. At this time Vodei MP works only on Windows. We are evaluating the possibility of making a Macintosh and/or Linux version."[/i]

Does anyone know how I can play it on Ubuntu without messing about with Wine? 

Thanks

Ted

---

### Post by PokerFacePenguin on 2006-08-19
> **Ted_Smith said:**
> I have a film that says that you need 'Vodei Multimedia Processor' to play it : [http://vodei.com/](http://vodei.com/). In their FAQ it says : 

[i]"Does Vodei MP run on Mac or Linux?

No. At this time Vodei MP works only on Windows. We are evaluating the possibility of making a Macintosh and/or Linux version."[/i]

Does anyone know how I can play it on Ubuntu without messing about with Wine? 

Thanks

Ted

Did you ever get this one figured out?  I have the same issue.

---

### Post by whatever on 2006-08-19
as far as i can tell this is a proprietary, not standardized closed source codec.
=> if you can't use the win32 dll it will not work at all.


EDIT:
it looks like voidei is not a codec, but rather some kind of drm-spyware which encrypts regular avi files and then tries to make the viewer pay for watching these files. i don't think anyone wants linux-support for this crap.
read this thread: [http://forum.inmatrix.com/index.php?showtopic=2256](http://forum.inmatrix.com/index.php?showtopic=2256)

---

### Post by Ted_Smith on 2006-08-20
I thought it was a bit odd. 

No, I never was able to view on Linux. In the ned I booted into Windows and watched oit on DivX I think and subsequently deleted it. 

Ted

---

### Post by xinel on 2007-05-09
Bugger, I have a few films that need it

---

### Post by dbcad7 on 2008-05-22
Freaking vodei files.. hate em, and you don't know till you get em that
that's what they are.. I read that they were runnable in Windows, but I 
could not find a way to run them with my Linux players so I figured why not give it a try in Wine.

First of all.. I already had wine installed, but that is no big deal in
Ubuntu or Debian just install it using Synaptic.

I won't get into a lot about wine, but if you open a file manager and show
hidden files (in home), you will see a directory .wine  (notice the dot)  you can
work with this directory the same as others you have.. Inside is a directory 
called drive_C  and in that is..  windows and Program Files  and just like the 
"real windows" inside the windows directory you will find a system32  directory....  
basically it's just like having a Windows installation in the drive_C directory ... kinda sorta..

My setup is Debian, XFCE4 .. and after I installed winamp, it shows up in
the main menu under "other" and I click it and it runs like any other app.
also when I downloaded all these ".exe" files it gave me the option of
saving to disk or running with wine.. To save steps I just ran them with
wine.. if you download them normally and your system doesn't give you 
this option, you'll have to figure out how to run things with wine, and
that is too much for me to go into... 
HERE'S HOW I GOT VODEI FILES TO PLAY...


(1)
Download, ([http://www.winampheaven.net/old.php?major=5](http://www.winampheaven.net/old.php?major=5)) this file..
winamp533_full.exe  
(note- this and all other files are for Win98 !!)
and run to install using wine...

(2) Download ([http://www.codecpackguide.com/klmcodec.htm](http://www.codecpackguide.com/klmcodec.htm)) this file..
klmcodec380.exe
and run to install using wine

(3)
Download ([www.dlldump.com](www.dlldump.com))  these 2 files
devnum.dll
quartz.dll
and replace (or add) in .wine's Windows\system32 directory 

(4)
in a terminal type..  winecfg
goto the Libraries tab ...
Click on New override button and select
devnum and  quartz   and click add button
these will put them in the override box... then exit.

(5)
Then run these 2 commands in a terminal eactly as below ...
regsvr32 "C:\windows\system32\devenum.dll"
regsvr32 "C:\windows\system32\quartz.dll"

(6)
Goto ..([http://sourceforge.net/softwaremap/trove_list.php?form_cat=422](http://sourceforge.net/softwaremap/trove_list.php?form_cat=422))
click on ffdshow tryouts download ..
download the  generic build (stable) and install using wine.

(7)
Goto .. ([www.vodei.com](www.vodei.com))
click on the Download Vodei Multimedia Processor
VodeiSetup210.exe is the file
install using wine.

(8)
Now, just run winamp.. and play the files.

---

