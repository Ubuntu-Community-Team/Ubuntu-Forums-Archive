---
title: "ALSA -&gt; How do I swap the sound device ?!?"
date: 2006-06-07
forum: Multimedia &amp; Video
---

### Post by Stormbringer on 2006-06-07
Hi!

Did a clean install of Ubuntu 6.06 --- so far everything went just fine, but there's only one "problem" that's driving me nuts ...

I have two sound devices attached to my box:

- OnBoard Realtek ALC655 AC97 Audio
- CMedia USB Headset Set

In Breezy, the Onboard Codec was configured as /dev/ds0 while the USB Headset was configured as /dev/dsp1.

Now, in Dapper it's the other way round ](*,) 

Anybody knows what I would have to do to swap the sound devices and make the change permanent? I'm unable to to figure it out.

I want ...

/dev/dsp1 (Onboard AC97) to become /dev/dsp0
/dev/dsp0 (USB Headset) to become /dev/dsp1

Thanks for your thoughts in advance,
Storm.

---

### Post by hauger on 2006-06-07
Hi.

Good luck.  I asked that question many days ago, and never got an answer.  I had the same problem, with the "solution" being to disconnect all hardware but my soundcard (for my setup this required the use of a screwdriver), reboot to force proper ordering of the devices, then turning it off and reconnecting.

One of the conflicting devices was my Webcam (USB) with microphone.  I've tried plugging it back in, and it gets ordered to the top of the list again, thus resulting in a loss of sound.

Anyways, try removing hardware and see if the sound flows as you expect.

---

### Post by Sutekh on 2006-06-07
You guys should look into using [udev]("http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev.html").  
 
 You should be be able to use it to consistently map the soundcard of your choice to /dev/dsp#, or to whatever you would like to call them, /dev/onboard or /dev/headset for example.
 
 I actually wrote a HOWTO for using udev to control the mapping of devices to persistant device nodes.  In the HOWTO I used USB devices, but the concept is the same for *any* device.
 
 [Ubuntu Forums - Create your own udev rules to control removable devices]("http://www.ubuntuforums.org/showthread.php?t=168221")

I hope you can get it to do what you need.  If not I'm sure I can help out with the process.

---

### Post by Stormbringer on 2006-06-07
Hi, hauger

I already tried rebooting with the USB Headset disconnected ... but as soon as I plug it back in it turns out the same way as in your case.

Seems as I'll have no other option than to work out the difference to my previous Breezy installation (been wise enough to keep a copy of it) and see if I can get it done the way I want it to.

Will let you know if I'm able to work something out.

[EDIT]
SUTEKH --- you are my hero ... finally ... a useable and easy to understand documentation about that udev thing.
Thanks for the HOWTO! (somehow I missed that while searching through the board)
[/EDIT]

Still ... I think Ubuntu should put a useable documentation online how to hack into things ...

---

### Post by Sutekh on 2006-06-07
[quote=Stormbringer]

[EDIT]
SUTEKH --- you are my hero ... finally ... a useable and easy to understand documentation about that udev thing.
Thanks for the HOWTO! (somehow I missed that while searching through the board)
[/EDIT][/quote]

Great!  I hope it helps out.  
 
 I'd appreciate if you posted your udev rules on the HOWTO thread aswell for future references.

[quote=Stormbringer]
Still ... I think Ubuntu should put a useable documentation online how to hack into things ...[/quote]

Well the udev documentation (I linked to it in my HOWTO) is excellent.  It also has specific rule situations for devices like audio, usb, network, printers etc.  I wrote the HOWTO so people here would be aware of udev.

---

