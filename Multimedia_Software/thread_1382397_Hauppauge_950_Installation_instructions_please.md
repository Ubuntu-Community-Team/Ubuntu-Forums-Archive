---
title: "Hauppauge 950 Installation instructions please"
date: 2010-01-15
forum: Multimedia Software
---

### Post by ubdoobdu on 2010-01-15
I have looked around the forums and other websites but I cannot find anything that tells me in simplest or even less simple terms. How do I make my Hauppauge 950 work on Ubuntu Karmic Koala? 
Starting from scratch, I have just inserted the USB Hauppauge 950. I installed TVTime. I don't think my Toshiba Laptop is even seeing the 950 right, but I have tried both USB ports.
lsusb shows my 950 as a 980:
Bus 001 Device 003: ID 2040:6513 Hauppauge WinTV HVR-980
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Please be gentle.  :)
Thanks

---

### Post by marshmallow1304 on 2010-01-15
Edit:  This should help. [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950)


[Here]("http://www.hauppauge.com/Pages/faq/support_faq_linux.html"), it says

[QUOTE=http://www.hauppauge.com/Pages/faq/support_faq_linux.html]
WinTV-HVR-950 Linux support:

Information in an experimental driver for the WinTV-HVR-950 can be found here[/QUOTE]
but their link goes nowhere.


Edit:

However, [this wiki page]("http://www.linuxtv.org/wiki/index.php/Hauppauge") lists the 950 as "supported".

---

### Post by ubdoobdu on 2010-01-15
Wow, that's interesting. You're right, it goes nowhere. I used their TS page to tell them I needed help a few minutes ago. Hopefully they can help.
Thanks for the link anyway. Maybe they'll fix that.

---

### Post by marshmallow1304 on 2010-01-15
> **ubdoobdu said:**
> Wow, that's interesting. You're right, it goes nowhere. I used their TS page to tell them I needed help a few minutes ago. Hopefully they can help.
Thanks for the link anyway. Maybe they'll fix that.

Yes, but did you see my second edit?  The first link looks the most promising. [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950)

---

### Post by ubdoobdu on 2010-01-15
> **marshmallow1304 said:**
> Yes, but did you see my second edit?  The first link looks the most promising. [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950)

Just now.

Thanks :)

---

### Post by Chamillo on 2010-02-06
Any luck with this? I also have the same TV card, but I have not been able to make it work. I have been struggling with this for months. I did try the link posted here for Linux TV, but no luck. I tried to use Kaffeine, but it doesn't pick the device. I would greatly appreciate some help here.

---

### Post by bkcevilmonkey on 2010-02-25
sorry to bump a (somewhat) old thread, but I have the same card and I just got it to work (the video, anyway).

I followed the instructions here [http://ubuntuforums.org/showthread.php?t=990185](http://ubuntuforums.org/showthread.php?t=990185)

lsusb showed my tuner, but it said 980, when mine's a 950 (i wasn't too concerned with this)

I tried myth, tvtime, vlc, but nothing worked.  Then I installed kaffeine.  It got a signal automatically, scanned in all the channels, and tuned to the channel.   
The screen doesnt show, but it allows me to record tv **without sound!!!**

Currently my setup is to record the tv from kaffeine and open the recording in vlc.

The big problem is that there's no sound.  a google search told me to run
```
sox -r 48000 -c 2 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp
```but this doesn't really do much...what is this command supposed to do?

edit - I see now, you run that and it enables the sound.
However, when watching tv in kaffeine and i run that sox command, it stops the playing of the video.

---

### Post by Chamillo on 2010-02-27
Thank you for the link. I followed the instrcutions and everything seemed to install correctly; however, when I open Kaffeine it doesn't recognize the Hauppauge device. It says that the default device is an LG Electronics LGDT3303 VSB/QAM Frontend. Of course it also says that the device is not connected because I don't have that device. Kaffeine doesn't give me the option to change my default device. I went to the Kaffeine support page and it says that to re-run the wizzard I should run the command:

kaffeine -w

Unfortunately this gives me an error and so I'm stuck. Any suggestions?

---

### Post by bkcevilmonkey on 2010-02-27
mine also says LG Electronics LGDT3303 VSB/QAM Frontend, although I never looked into it much.  I must have been too excited by the signal meter ;)

I'll try running kaffeine -w and report back afterwards.

edit:  kaffeine -w doesnt do anything.  Checked kaffeine --help, and -w isnt listed anywhere.

---

