---
title: "FYI Feisty Mplayer/Mencoder"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by JimmyME on 2007-04-21
From the Devede website:


Note for Ubuntu Feisty users: currently (as April 20, 2007), the Mplayer/Mencoder version in Ubuntu Feisty is buggy and produces noisy sound when used with DeVeDe. While the maintainer doesn't fix it, you can use the .deb package created by from the CVS sources (it's available in the Download section).

---

### Post by Steve H on 2007-04-21
I have been experiencing problems with DeVeDe. It just produces audio static for the audio track.

Is there a fix yet? Or an alternative app?

---

### Post by Nrvnqsr on 2007-04-22
thank you, thank you, thank you for the notice, I was wondering what is wrong with mencoder.

@Steve H
If I understand your comments,
the problem is not DeVeDe, it is Mplayer that the Ubuntu devs compiled, it very buggy.
So the DeVeDe devs compiled a fixed version of Mplayer for the DeVeDe. you just need to go to their site and locate at the bottom of their page and they have a deb package ready to install

---

### Post by Steve H on 2007-04-22
Cheers for the heads up, Nrvnqsr. Bizarrely I had been to that site a few times and not noticed the link at the bottom of the page (or had not paid attention to it). I´m downloading the mplayer/mencoder as we speak.

p.s. I have just tried installing the Devede mplayer/mencoder and got a conflict message, so I presume I´ve got to uninstall the old version, to allow the new one to install.......

I´ll let you know how it goes....

Thanks again

---

### Post by Steve H on 2007-04-22
I have just tried running mplayer, but it doesn´t work anymore. If i call gmplayer from the command line i get:

~$ gmplayer
MPlayer dev-SVN-r22974-4.1.2 (C) 2000-2007 MPlayer Team
CPU: AMD Duron(tm) processor (Family: 6, Model: 7, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
Warning unknown option vo_dxr3_device at line 6
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
[skin] file ( /usr/local/share/mplayer/skins/default/skin ) not found.
Skin not found (default).


I have tried reinstalling the older version, but it marks the newer one for uninstallation if i do that.

Any ideas what i have done wrong??

---

### Post by Nrvnqsr on 2007-04-22
hmm... so far I have not have any of these issues when I have installed the deb package, only issues I have received are subfont.ttf error.

before I go on, have you also removed the mencoder package too? If not, remove the Ubuntu mencoder and  mplayer package together and reinstall the DeVeDe package.

I typed on my command line and got this:
> 
~$ gmplayer
MPlayer dev-SVN-r22974-4.1.2 (C) 2000-2007 MPlayer Team
CPU: AMD Turion(tm) 64 Mobile Technology ML-30 (Family: 15, Model: 36, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
/home/nrvnqsr/.mplayer/fonts/arial.ttf doesn't look like a bitmap font description, ignoring.
Cannot load bitmap font: /home/nrvnqsr/.mplayer/fonts/arial.ttf
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


> 
Warning unknown option vo_dxr3_device at line 6

my guess for this is to check the **Preference** and both the **Video** and **Codecs and Muxers** tabs and see if they are set correctly.

> 
[skin] file ( /usr/local/share/mplayer/skins/default/skin ) not found.
Skin not found (default).

this, you just need to get a skin package for Mplayer site and make a "skin" folder in "/home/(user name)/.mplayer" folder

thats all I can able to help, not much of a linux guru. :(

---

### Post by Steve H on 2007-04-22
I am well on my way to getting this sorted now.

Yep, i did remove both mplayer & mencoder at the same time. I have now installed a skin from the MplayerHQ, which solved the problem of the skins error.

I have even managed to sort out the subfont.ttf error

> cp /usr/share/fonts/truetyp/ttf-bitstream-vera/vera.ttf ~/.mplayer/subfont.ttf

So i´m now encoding an avi, to see if i actually get any sound now. Thanks for your help though. The only downside of all this is now i don have the Mozilla Mplayer plugin for Firefox, cos that was uninstalled with the old version as well........

---

### Post by Nrvnqsr on 2007-04-22
same here, but I have to use totem-firefox for now, but its lacking a lot of things that mplayer-plugin has.

---

### Post by Steve H on 2007-04-22
OK then, DeVeDe (with the new mencoder) has encoded the avi to DVD beautifully. The sound is all ok. And it seemed a bit faster when encoding.


But now, I can´t watch online streaming videos, and Mplayer can find my DVD once I´ve made it.Mplayer just sits there doing nothing when i ask it to play a DVD. It is definitely processing something (as it shows it in System Monitor). But it just hangs.......

I´m still hunting for fixes, but at least it is encoding now.

---

### Post by Steve H on 2007-04-22
Phew! looks like everything is sorted now.

I followed [_this page_]("http://ubuntuforums.org/showthread.php?t=380612") and now everything seems to work. I´ve also installed VLC player as well, as the Mplayer version supplied by DeVeDe doesn´t seem to like playing DVD´s anymore. But it´s no biggie now cos VLC does the job brilliantly. Online streaming video works now as well.

Looks like it was the Restricted Formats that were causing the problems with DVD´s and online streaming. There is a good page [_here_]("https://help.ubuntu.com/community/RestrictedFormats")

Hope this helps.

---

### Post by bogolisk on 2007-07-12
AFAICT, It's just the mp3lib codec that caused problems with mplayer. I forced ffmpeg codecs and sound is nice and dandy. mplayer rocks. I haven't looked at mencoder yet to see if there's a problem with mp3lib, but you should use lavc anyway.

for mp3, I've added

```
afm=ffmpeg
```

in /etc/mplayer/mplayer.conf and to favour ffmpeg over other codec families. Probably should do the same for /etc/mplayer/mencoder.conf as well.

EDIT: mencoder doesn't seem to read /etc/mplayer/mencoder.conf, put
```
afm=libmad,ffmpeg
```
in ~/.mplayer/mencoder.conf fixed the static noise problem with encoding.

---

