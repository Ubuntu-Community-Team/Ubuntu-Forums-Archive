---
title: "Unable to play Blu Ray disc"
date: 2013-11-10
forum: Multimedia Software
---

### Post by Coder88 on 2013-11-10
Help needed! 
I am unable to play blu ray movie discs. I can play DVD movie discs using VLC, just not blu ray-- so I have the libdvdcss2 installed, I use /dev/sr0 to access the dvd/bluray drive.

If I put in a blu ray movie disc and run VLC and choose to open disc, click blu ray, change the default location /dev/dvd to /dev/sr0 (what I use for playing dvds), I get an error window in VLC that says:
 Blu-Ray error:
Path doesn't appear to be a bluray
Your input can't be opened:
VLC is unable to open the MRL 'bluray:///dev/sr0'. Check the log for details.[COLOR=#ff0000]

[/COLOR][COLOR=#000000]If I mount the bluray disc then repeat above, I get:
Blu-Ray error:
Missing AACS configuration file!
Your input can't be opened:
VLC is unable to open the MRL 'bluray:///dev/sr0'. Check the log for details.[/COLOR]

I have no idea where a log file is for VLC.
Any tricks to try and get VLC to play blu ray discs (or some other app to play blu ray discs)?
I am not interested in ripping blu ray, just being able to view the movies.


[COLOR=#000000]

[/COLOR]

---

### Post by Yellow Pasque on 2013-11-11
Disclaimer: Check your local laws before circumventing encryption...

This should work for Ubuntu 13.10 (and probably earlier versions). You may have to turn disc menus off in VLC.
```
sudo apt-get install libbluray-bdj libaacs0
mkdir ~/.config/aacs/
cd ~/.config/aacs/ && wget http://vlc-bluray.whoknowsmy.name/files/KEYDB.cfg
```

Source: [http://www.webupd8.org/2012/08/how-to-get-encrypted-blu-rays-working.html](http://www.webupd8.org/2012/08/how-to-get-encrypted-blu-rays-working.html)

---

### Post by Coder88 on 2013-11-11
> **Temüjin said:**
> Disclaimer: Check your local laws before circumventing encryption...

This should work for Ubuntu 13.10 (and probably earlier versions). You may have to turn disc menus off in VLC.
```
sudo apt-get install libbluray-bdj libaacs0
mkdir ~/.config/aacs/
cd ~/.config/aacs/ && wget http://vlc-bluray.whoknowsmy.name/files/KEYDB.cfg
```

Source: [http://www.webupd8.org/2012/08/how-to-get-encrypted-blu-rays-working.html](http://www.webupd8.org/2012/08/how-to-get-encrypted-blu-rays-working.html)

I actually had found that method a day ago, tried it, no joy. Tried it again just now but when I try to open a blu ray disc using VLC after following the above suggestion, VLC displays these errors in a window:

 [COLOR=#ff0000]Blu-Ray error:[/COLOR]
 [COLOR=#000000]Path doesn't appear to be a bluray[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'bluray:///dev/sr0'. Check the log for details.[/COLOR]
 [COLOR=#ff0000]Blu-Ray error:[/COLOR]
 [COLOR=#000000]Path doesn't appear to be a bluray[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'bluray:///dev/sr0'. Check the log for details.[/COLOR]
 [COLOR=#ff0000]Blu-Ray error:[/COLOR]
 [COLOR=#000000]AACS Host certificate revoked.[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'bluray:///dev/sr0'. Check the log for details


I think perhaps that KEYDB file is outdated or something.

Blu Ray playback of movies in linux appears to be a weakness of linux over windows. Of course I don't do it that often, just that it would be nice to see it be able to be done in linux (until then, i gotta keep a dual boot system with Windows 7).


[/COLOR]

---

### Post by restlessnomad2 on 2014-03-09
To anyone who has this issue after installing the ACSS files (and has rebooted...a critcal step)...follow this process:

1. Insert Blu-Ray Movie

2. Launch VLC

3. CTRL+D to enter Disc Menu

4. Select Blu-Ray Option and check: **No Menu** option.

5. Under drive select browse and highlight your drive only on the left side (not the 3 folders on the right)

6. Select Play from the former "Open Media" screen. 

Viola! The movie plays every time in crisp HD Blu-Ray goodness. No more Dual-Booting M$ Windows for that reason. I hope this helps anyone looking to play Blu-Rays and had the same experience outlined in this forum.

---

### Post by David006 on 2014-04-28
Confirm (per posting #2 and #4) this works in **Ubuntu 14.04 LTS (64-bit)**.

But only for some discs ..

---

### Post by puchrojo on 2014-06-05
I get this error:

libaacs: libaacs/mmc.c:1049: Host key / Certificate has been revoked by your drive ?
libaacs: libaacs/mmc.c:1047: Certificate (id 0xFFFF00000064) can not be used with bus encryption capable drive
libaacs: libaacs/aacs.c:515: Host certificate FFFF000000AE has been revoked.
libaacs: libaacs/mmc.c:1047: Certificate (id 0xFFFF000000AE) can not be used with bus encryption capable drive
libaacs: libaacs/aacs.c:515: Host certificate FFFF0000000C has been revoked.
libaacs: libaacs/mmc.c:1047: Certificate (id 0xFFFF0000000C) can not be used with bus encryption capable drive
libbluray/bluray.c:836: aacs_open() failed!
libbluray/bdj/bdj.c:128: Opening /usr/lib/jvm/java-6-sun/jre/jre/lib/amd64/server/libjvm ...
libbluray/bdj/bdj.c:342: BD-J check: Failed to load JVM library
[0x7f2bd4003c58] libbluray demux: First play: 1, Top menu: 1
HDMV Titles: 598, BD-J Titles: 4, Other: 4
[0x7f2bd80009b8] main input error: open of `bluray:///dev/sr0' failed

---

### Post by Massimo_Ciani on 2014-08-17
Bingo! It works. May God blees you, restlessnomad2! 
I thought the possibility of watching Blu RAy movies on Ubuntu was an urban legend.  It isn't.  I followed your instructions, and  - lo and behold! - I wachted an entire Blu Ray movie flawlessly. I couldn't believe my eyes! More exactly, at the beginning the subtitles seemed to be lost forever, but in a few minutes, by simply modifying the VLC settings, they suddenly appeared. And you know what?  Since I auto-assembled my PC and happened to install *two* Blu-Ray burners (and old, yet perfectly working, Samsung Blu-Ray burner and a new Asus one), I can see the Blu Ray movies only with the Asus burner: the Samsung burner still gives an error message. On top of that, I can't watch *all* Blu Ray movies: some of them still give an error message.  Well, I don't care. Thank you, thank you, thank you!

---

### Post by shantiq on 2014-08-19
yes discs produced after say 2012   do not play for reasons explained [here]("http://ubuntuforums.org/showthread.php?t=2238603&p=13097077#post13097077")  ie    the AAc keys are not up to date ...   ones prior to that play flawlessly   and even better in [XBMC]("http://wiki.xbmc.org/index.php?title=How-to:Install_XBMC_for_Linux") than in VLC

---

### Post by ibhollow1975 on 2014-09-17
Thank you very much Temujin! I had been trying all night to get the damn thing to work. You simple script had I found it earlier would have saved me loads of time and headache. 

> **Temüjin said:**
> Disclaimer: Check your local laws before circumventing encryption...

This should work for Ubuntu 13.10 (and probably earlier versions). You may have to turn disc menus off in VLC.
```
sudo apt-get install libbluray-bdj libaacs0
mkdir ~/.config/aacs/
cd ~/.config/aacs/ && wget http://vlc-bluray.whoknowsmy.name/files/KEYDB.cfg
```

Source: [http://www.webupd8.org/2012/08/how-to-get-encrypted-blu-rays-working.html](http://www.webupd8.org/2012/08/how-to-get-encrypted-blu-rays-working.html)

---

### Post by infoanalysis2 on 2014-11-03
I did all that and I still get the error message
 [COLOR=#ff0000]Blu-Ray error:[/COLOR]
 [COLOR=#000000]Your system AACS decoding library does not work. Missing keys?[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'bluray:///media/CAPT_AMERICA_WINTER_SOLDIER'. Check the log for details.
[/COLOR]

cd ~/.config/aacs/ && wget [http://vlc-bluray.whoknowsmy.name/files/KEYDB.cfg](http://vlc-bluray.whoknowsmy.name/files/KEYDB.cfg)[COLOR=#000000]even after I run this command 
[/COLOR]

---

### Post by Lance_Ryan on 2014-11-14
> **Temüjin said:**
> Disclaimer: Check your local laws before circumventing encryption...

This should work for Ubuntu 13.10 (and probably earlier versions). You may have to turn disc menus off in VLC.
```
sudo apt-get install libbluray-bdj libaacs0
mkdir ~/.config/aacs/
cd ~/.config/aacs/ && wget http://vlc-bluray.whoknowsmy.name/files/KEYDB.cfg
```

Source: [http://www.webupd8.org/2012/08/how-to-get-encrypted-blu-rays-working.html](http://www.webupd8.org/2012/08/how-to-get-encrypted-blu-rays-working.html)

THANK YOU!  I've been trying to get BluRay discs working in VLC for some time and your help finally made them work. You kick ass!  :)

---

### Post by mark bower on 2015-07-10
@restlessnomad2
 I am using Ubuntu 15.04 on 32bit.

Your instructions did the trick for me.  Else, I could not get VLC to run a Blu-ray made for me from super8 movies.

---

