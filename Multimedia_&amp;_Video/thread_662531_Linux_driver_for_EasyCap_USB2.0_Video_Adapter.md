---
title: "Linux driver for EasyCap USB2.0 Video Adapter"
date: 2008-01-09
forum: Multimedia &amp; Video
---

### Post by prachi on 2008-01-09
Hi,

I need the linux driver for EasyCap USB2.0 Video Capture Adapter.

---

### Post by Hugh Mulqueen on 2008-01-09
Hi 
I have the EasyCap USB thing and i have been trying to get the drivers and software for a month and a half. :(

I have come up with software that might work, unicap which you can get at:

[http://www.unicap-imaging.org/download.htm]("http://www.unicap-imaging.org/download.htm")

and camorama to test it, which can be got with apt-get:
[FONT="Arial"]
sudo apt-get install camorama[/FONT]

Now as for drivers, the best one I could come up with was a driver for a web cam called stk11xx-1.2.3. it might work with your machine. Check it out anyway. heres the address:

[http://sourceforge.net/project/showfiles.php?group_id=178178]("http://sourceforge.net/project/showfiles.php?group_id=178178")

Get the tarball and extract it. read the readme file.
And pray that it works.

There is a tutorial on how to install the driver in ubuntu forums:

[http://ubuntuforums.org/showthread.php?t=451200&highlight=Syntek+Semiconductor]("http://ubuntuforums.org/showthread.php?t=451200&highlight=Syntek+Semiconductor")

Hope this helps, Let me know how you got on! 

Good Luck!!!

---

### Post by prachi on 2008-01-11
Thanks a lot for the info.

I tried compiling the driver ..its giving me a lot of warnings(no errors), tho' the stk11xx.ko is built successfully.

After the make, when I tried insmod stk11xx.ko it gives me the following error:
stk11xx: Unknown symbol ClearPageReserved
stk11xx: Unknown symbol SetPageReserved
stk11xx: no version for "video_get_drvdata" found: kernel tainted.
stk11xx: Unknown symbol to_video_device
insmod: error inserting 'stk11xx.ko': -1 Unknown symbol in module

Could u help?:confused:

---

### Post by Hugh Mulqueen on 2008-01-13
I found somebody that has the same problem as yourself. Theres a catch though in the forum is suggesting that you write a bit onto a file. Perhaps the module "gksu gedit /etc/modules" or gksu gedit /etc/rc.local??? Or else one of the files in the folder stk11xx-1.2.3?

You can view the forum at:
[http://sourceforge.net/forum/forum.php?thread_id=1700887&forum_id=616182]("http://sourceforge.net/forum/forum.php?thread_id=1700887&forum_id=616182")

If Anybody else could help that would be great.

---

### Post by saj0577 on 2008-03-31
Any update on this?


Saj

---

### Post by Hugh Mulqueen on 2008-04-16
As far as I know the driver does is not yet programmed specifically for the EasyCAP device. 
After you plug in the device to your PC, Hardware Information shows various ALSA inputs but no mention of the actual video chip so I think the programmers will need a good bit of work on that. I'd say give it a bit of time. 

I'll rewrite the instructions for future reference:

1. Download and install the new version of the driver from the sourcefordge link above.

2. Extract the package to your home folder (Or your desktop where ever you want). For this example I'm using the home directory.

3. Open up the terminal and type cd, drag and drop the folder (from your window manager or Desktop) beside the command and press enter.

4. Type:
sudo ./configure && make
(After this command the file stk11xx.ko is created in the stk11xx-1.3.1 folder)
sudo modprobe videodev
sudo modprobe v4l1-compat
sudo insmod stk11xx.ko

5.Press ALT+F2 and executes &#8216;gksu gedit /etc/modules&#8217; then adds the lines:
# modules for infrastructure to support the video
videodev
v4l1-compat

6.Press ALT+F2 and executes &#8216;gksu gedit /etc/rc.local&#8217; then adds the following line:
insmod /home/<your login name>/stk11xx-1.3.1/stk11xx.ko 
(this line must be added before last line &#8220; exit 0 &#8221;)

Test with Camorama or even better zapping which can be got with the command
$ sudo apt-get install zapping

Thats all folks!!!!
P.S. Im thinking of thinking of tinkering around with the the driver myself, if anybody would be interested that would be great. Send a message through the forums.

---

### Post by Flocke on 2008-05-20
Hi all,
I followed the instructions of Hugh Mulqueen...
everything worked fine ...
But when I started Zapping it reports 

»/dev/video0« could not be opened:
The device cannot be attached to any controller

What did I do wrong ?

THX
-=Flocke=-

---

### Post by michaelAust on 2008-07-14
I too have an easycap and found the following page
[http://doc.ubuntu-fr.org/em28xx_generique](http://doc.ubuntu-fr.org/em28xx_generique)
Translated by google
[http://translate.google.com.au/translate?u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fem28xx_generique&sl=fr&tl=en&hl=en&ie=UTF-8](http://translate.google.com.au/translate?u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fem28xx_generique&sl=fr&tl=en&hl=en&ie=UTF-8)
This may have been an earlier easycap version. The lsusb id is different (mine is 05e1:0408 ) and it uses the em28xx driver, but it says model Dc60 like mine. So I tried it but it didn't work.

---

