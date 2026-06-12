---
title: "Radeon HD 3650 driver"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by sploutch on 2008-02-26
Hi,

I try to run Ubuntu 7.10 with an ATI Radeon card. The model is Radeon HD 3650 but I cannot found the good driver...

Maybe someone had the same card and had found an solution to install this?
Please help me...

Thanks.
Sploutch.

---

### Post by xc3RnbFO8P on 2008-02-26
You could try Envy:

> [http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb)

And read this:

> [http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

---

### Post by sploutch on 2008-02-26
Thanks, but I already tried Envy and it didn't works...

Here is the Envy error code:
```
Envy - Version 0.9.10
Ubuntu Gutsy 32bit
ENVY ERROR: Envy does not recognise your card as compatible with any version of the driver.this might happen because either your card is not supported by the driver or Envy's hardwaredetection failed. You can try the manual installation at your risk.
```

I'm sorry... Anything else?

---

### Post by sploutch on 2008-03-03
Please help me !!!

---

### Post by sploutch on 2008-03-07
No body knows?

---

### Post by markoloka on 2008-03-07
Try this: [http://www.phoronix.com/forums/showthread.php?t=7193](http://www.phoronix.com/forums/showthread.php?t=7193)
and also look help from this section: [http://www.phoronix.com/forums/forumdisplay.php?f=19](http://www.phoronix.com/forums/forumdisplay.php?f=19)

---

### Post by Marcusdegrote on 2008-03-10
I have the same problem. It still doesn't work. Does anybody has a fix?

Many thanks

---

### Post by Marcusdegrote on 2008-03-12
Please help i still can't find anything

---

### Post by BlueKoala on 2008-03-14
Heh, I'm on the same boat with a new rig. I tried a whole bunch of things, I couldn't ever get the amdcccle working, it complained about a missing libGL.so.1 or something along those lines. It would be nice to have the amd catalyst drivers with the restricted drivers manager.

---

### Post by BlueKoala on 2008-03-15
Ok, I've gone through all the necessary steps as outlined in the guide [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

It just doesn't work.
The restricted drivers manager does not have a selection for the ati restricted drivers.


My video card is the Sapphire radeon HD3650 with 512mbs DDR2.
It works fine under Windows MCE as I just set one up on my girlfriend's PC.
Actually the image quality is great and the performance is more than reasonnable.
It's a great buy.
I just can't wait for it to work in Ubuntu =p

I'll try to install from the ATI website again.
I haven't done it as outlined in  [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
But I will do it later this afternoon and I will post my results.

Stay tuned =]

---

### Post by BlueKoala on 2008-03-16
Alrighty.
Last night, when I felt I was running out of options...
I decided to upgrade my distribution to 8.04
Once I did that, I magically was greeted with the restricted drivers manager telling me there's something new for me.
Then it was just a matter of checking the ati drivers and rebooting.
Now everything works well.
I got my tv hooked up to HDMI.
The card performs very well for its price.
I can play doom3 on ultra quality at a custom resolution and get 12fps min. Usually hovers around 40-60fps.
I do have the DDR2 version which is slower and also considerably cheaper.
The only thing that doesn't work so far is HDMI audio.
I can see the device is recognized, but as far as using the audio, it just doesn't work.
I am using alsa:

Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Mar 11 2008 for kernel 2.6.24-12-generic (SMP).

Which is 5 days old.
I wonder which direction I should be looking.
It could also be my cable, I haven't tested in windows either.

I think I'll start a new thread for ATI HDMI audio.

I hope this helped!!

---

### Post by BlueKoala on 2008-03-16
Oh yes, BTW:
the driver used is fglrx.
Once it's working, amdcccle (Catalyst Control Center Linux Edition) is really easy to install.
Just type amdcccle in a terminal and it'll tell you how to install it in one short line.

Although amdcccle is not feature rich, I'm counting on it having more within the next year.
Hopefully more options for control over multiple displays.

Cheers!

---

### Post by borgking583 on 2008-03-16
Cool, Thanks. I'll start this and post back when its all working. I hope this works for me, I really hate 1280x1024 when i'm use to 1680x1050.

---

### Post by borgking583 on 2008-03-16
Dam, saddly I can't get this to work. I upgraded to 8.04, but now everytime I log in, my gnome session tells me xorg only lasted for 10 secs and I have to log back in, using failsafe. Once I disable the restricted driver for the ATI, everything seems to work again, but now i have no 3D and i'm stuck at 800x600.

Help anyone?

---

### Post by BlueKoala on 2008-03-16
Do you know if the card works under a more money hungry OS?

---

### Post by BlueKoala on 2008-03-20
Also, which card are you using specifically?

---

### Post by mike.oldfield on 2008-03-20
I have a Sapphire ATI Radeon HD 3650. I too have the FGLRX driver working fine for graphics within Ubuntu Hardy, and I have a similar HDMI sound issue.

I am able to get sound running through most programs, but **only** if I mute and unmute the sound. If I'm listening to music, it'll cut out when it skips track (at least on Totem it does...)

I use Amarok as my media player, and it refuses to play through my HDMI sound card. I get an error saying that 'xine is unable to initialize any audio drivers' when using ALSA, and when using OSS, it plays through my onboard soundcard.

Is there any way I can resolve this issue?

---

### Post by Rippy on 2008-03-21
I just bought one of these cards, trusting in Ubuntu's ability to seemingly work with anything. I was reading this thread with increasing dread until I got to the part about upgrading to Heron.

I'm doing so now, and if it works I'll say so here. If not, I'll be posting my problem I guess :P

Edit: Yes, upgrading to hardy fixed my problems. I haven't had a chance to try any graphics intensive software yet, but glxgears nets me ~8000 FPS, which is 4 times what my last card could achieve :P

---

### Post by TeoLinuX on 2008-03-28
> **sploutch said:**
> Thanks, but I already tried Envy and it didn't works...

Here is the Envy error code:
```
Envy - Version 0.9.10
Ubuntu Gutsy 32bit
ENVY ERROR: Envy does not recognise your card as compatible with any version of the driver.this might happen because either your card is not supported by the driver or Envy's hardwaredetection failed. You can try the manual installation at your risk.
```

I'm sorry... Anything else?

Use the Envy Option  Install ATI driver manually
then choose the Catalyst 8.3 (or whatever new by the time you read this)

---

### Post by TeoLinuX on 2008-03-31
> **BlueKoala said:**
> Do you know if the card works under a more money hungry OS?

I use it under winXP in my dual boot PC. It works very well. Good game performances.
HDMI is perfect and autocofigures well (attached to a Sony 40" LCD).
I can get the sound via HDMI only with winMP10 and Nero ShowTime (fantastic BTW)
I cannot get the sound via HDMI vith VLC and divX Player.
I guess it's due to HDCP/DRM issues, but I didn't try hard to fix it

I'll let you know in few days.

Under Gutsy: half a tragedy. I correctly install drivers 8.3 catalyst through ENVY (manual install option), but I can't get compiz to work and no HDMI video/audio at all!

I will upgrade to 8.04, but still I wonder why it works under 8.04 and not under 7.10 (which are the differences involved in this behaviour?)

---

### Post by TeoLinuX on 2008-04-11
Ok, now the driver works fine, Compiz is running, though I have problems executing glxgears+compiz, which crashes the Xserver...
My experience is: configure well the xorg.conf, and be careful that atiinstall doesn't overwrite it!

BTW: I still use Gutsy.. I know that everything works just fine with Hardy, but I WANT to learn why before upgrading :confused: 
I tried a Live of Mandirva 2008.1 (spring) and it works flawlessly and i get a 8000 fps score with glxgears vs 5500 with gutsy-no compiz    uhmmmmmmmm :(

Anyone solved issues with HDMI audio?

---

### Post by HughR on 2008-05-13
> **BlueKoala said:**
> Alrighty.
Last night, when I felt I was running out of options...
I decided to upgrade my distribution to 8.04
Once I did that, I magically was greeted with the restricted drivers manager telling me there's something new for me.
Then it was just a matter of checking the ati drivers and rebooting.
Now everything works well.

I've had no such luck.  I installed Ubuntu 8.04 AMD64 on my system.  It worked OK with the integrated Intel video.

I then installed an HD3650 card.  I was offered a restricted driver, accepted, and then X (presumably) crashed the system and it rebooted.  It offered to disable the driver and I accepted.  The VGA works, but not at the native resolution of the display.

When I manually run the driver, the system crashes.

I've written this up: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/229467](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/229467)

Any suggestions?

---

