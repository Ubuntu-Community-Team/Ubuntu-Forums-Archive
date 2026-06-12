---
title: "Video Hangs, blank in full screen"
date: 2009-07-29
forum: Multimedia Software
---

### Post by elliotn on 2009-07-29
Suddenly when playing videos in every player I get a blank picture when I play in full screen, the sound works fine. Help

---

### Post by xc3RnbFO8P on 2009-07-29
What is your computer spec.?
and is Compiz enable?

---

### Post by igorzwx on 2009-07-29
I have a kind of the "Brown Screen of Death" for about two days
time after time (Ubuntu 9.04)
My wife has Ubuntu 8.04 (Dell notebook).
She has such things for a weak.
Ubuntu 9.10 Alpha 2 & 3 always hang on my boxes.
It was perhaps a kernal update (security problems):

[http://www.theregister.co.uk/2009/07...ernel_exploit/]("http://www.theregister.co.uk/2009/07/17/linux_kernel_exploit/")
**[Clever attack exploits fully-patched *Linux kernel* • The Register]("http://www.theregister.co.uk/2009/07/17/linux_kernel_exploit/")**

The exploit code was released Friday by *Brad Spengler* of grsecurity, **...** "Why is it that whenever there is an exploitable *vulnerability* in *Linux*, **...**
[www.theregister.co.uk/2009/07/17/]("http://www.theregister.co.uk/2009/07/17/")**linux**_**kernel**_exploit/ - [Cached]("http://209.85.135.132/search?q=cache:wZBH3pYFhz0J:www.theregister.co.uk/2009/07/17/linux_kernel_exploit/+vulnerability+linux+kernel+PulseAudio+Brad+Spengler&cd=2&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:www.theregister.co.uk/2009/07/17/linux_kernel_exploit/")
			 		   		 		 		[http://www.milw0rm.com/exploits/9208](http://www.milw0rm.com/exploits/9208)
**[PulseAudio (setuid) Priv. Escalation *Exploit* (ubu/9.04)(slack/12.2.0)]("http://www.milw0rm.com/exploits/9208")**

20 Jul 2009 **...** :razz: Tested with success on *Ubuntu* 9.04 (x86-64) and slackware 12.2.0 **...** groups=17(audio),100(users),104(*pulse*-rt) sh-3.1# uname -a Linux **...**
[www.milw0rm.com/]("http://www.milw0rm.com/")**exploits**/9208 - [Cached]("http://209.85.129.132/search?q=cache:6FD4c7qzX2wJ:www.milw0rm.com/exploits/9208+ubuntu+pulse+exploit&cd=4&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:www.milw0rm.com/exploits/9208")

---

### Post by rannable on 2009-07-29
good question about compiz, you beat me to it!

---

### Post by elliotn on 2009-07-30
No compiz is not enabled

---

### Post by elliotn on 2009-07-30
> **Ringi said:**
> What is your computer spec.?
and is Compiz enable?

1.8ghz amd 3000+ processor, sis gxf card, 768mb ram and 1gb swap

My gfx doesnt support compiz

---

### Post by xc3RnbFO8P on 2009-07-30
Try:
> sudo gedit /etc/modules
and add this:
> sisfb
save and restart.

Be sure that you are using resolution that is supported.

---

