---
title: "Driving 2560x1440 Korean monitor with Nvidia driver"
date: 2012-06-22
forum: Multimedia Software
---

### Post by woogeroo on 2012-06-22
I recently picked up a cheap Korean 2560x1440 monitor from ebay. They use the same panel as the 27" iMac, with a DVI-D input only, and no scaling hardware. My model is called the Potalion.

Another monitor with the same panel, and similar electronics is the Catleap Q270. 

I have an Nvidia GTX 560 Ti, and I've been using the Nvidia-current driver, installed from here [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

The card and driver worked fine with my old monitor, but I've not been able to get any picture out of it in X after the Ubuntu splash screen on boot - n.b. I can see my bios screens, grub etc. during boot, but get a blank display when lightDM loads.

The system boots OK, as far as lightDM, but I'm simply unable to see anything. I can switch to another tty and get a terminal shown - no issues there.

I've tried booting with both my old (Samsung TFT) and new monitors connected - I can see in Nvidia settings that my new monitor is detected only as 'unknown' and has a resolution of 640x480 that I'm unable to change.

The (new) monitor works fine when I'm booted into Windows. The monitor is detected fine and displays the live version of Ubuntu at it's native resolution if I boot from an Ubuntu 12.04 live USB stick - presumably using the Nouveau driver.

Where can I go from here? Do I need to customise my xorg.conf to add the correct resolution as default?

Thanks in advance.

---

### Post by arubislander on 2012-06-22
Is it an option for you to try the Nouveau driver on your installation or are there other drawbacks with that?

---

### Post by woogeroo on 2012-06-22
It's an option I guess, and I'm happy to try it -  but from a performance point of view there's no point in having this graphics card If I'm only going to get the performance that Nouveau offers, for video decoding, 3D etc. 

I actually have an Ivy Bridge chip with built in Intel HD 4000 graphics, which I believe would offer better performance than the 560ti under Nouveau.

n.b.
I can't use the HD 4000 with the new monitor at the moment as my motherboard doesn't have a DVI-D output.

---

### Post by woogeroo on 2012-06-26
OK, an update. I disconnected the big monitor and booted with only my old 1280x1024 Samsung monitor attached. This allowed me to login, purge the nvidia driver & delete my xorg.conf.

After re-booting, I was back on my desktop, using the nouveau driver with no issues again.

When I boot with both monitors connected, Ubuntu never boots, does not reach a login screen, and does not allow me to switch to another tty. 

I just get a cycle of messages in the boot console about EDID errors - details to follow as soon as I get home.

If I disconnect the Potalion, things are fine again.

---

### Post by Mearis on 2012-08-08
> **woogeroo said:**
> OK, an update. I disconnected the big monitor and booted with only my old 1280x1024 Samsung monitor attached. This allowed me to login, purge the nvidia driver & delete my xorg.conf.

After re-booting, I was back on my desktop, using the nouveau driver with no issues again.

When I boot with both monitors connected, Ubuntu never boots, does not reach a login screen, and does not allow me to switch to another tty. 

I just get a cycle of messages in the boot console about EDID errors - details to follow as soon as I get home.

If I disconnect the Potalion, things are fine again.


I am having the exact same issues that you are having with the same monitor, only I have an Nvidia GTX 670.  The monitor works great in Windows, in Ubuntu it gives a blank screen.

Were you able to solve your issue at all?

---

### Post by NertSkull on 2012-08-09
I appear to also be having the same issues using the nvidia GTX 460.

I know the monitor works when I don't use the nvidia driver, and I know it works in Windows.  Its only when the nvidia driver is activated that it doesn't work.

I have a dual monitor setup, so with nvidia enabled I can use the other monitor still.  And I see in nvidia-settings that it only recognizes the new monitor as DFP-2(DFP-2 on GPU-0).  

If anyone has any thoughts for those of us in this thread it would be great.  thanks!

---

### Post by Malfernion on 2012-08-09
Hi,

I'm having a similar problem trying to run a korean FSM-270YG monitor on intel integrated graphics (HD3000) on my laptop. 
By messing around with xrandr I can get the external to work (supposedly at 2560x1440), but the screen shows a sort of tiling, where the desktop is shown four times on the external.. pic hopefully attached.

Does anyone have any idea what could be up here?

Here are the commands used to get this happening:

gtf 2560 1440 60

xrandr --newmode "2560x1440_60.0"  311.83  2560 2744 3024 3488  1440 1441 1444 1490  -HSync +Vsync

xrandr --addmode HDMI1 2560x1440_60.0

---

### Post by mips on 2012-08-09
EDID issue maybe?

Also is the mode on the monitor set to PC and not AV or whatever?

What do you guys have in your log files?

---

### Post by NertSkull on 2012-08-09
> **mips said:**
> EDID issue maybe?

Also is the mode on the monitor set to PC and not AV or whatever?

What do you guys have in your log files?


I'm not super familiar with EDID, but would that really be an issue if it works with the native Kubuntu drivers (not the nvidia) and works in windows.  Clearly the monitor must be reporting the right stuff if it works otherwise, no?

I'm not at home, so I'll see if there is anything in log files later.

I'm beginning to wonder if I can manually set up an xorg file without nvidia-settings to make this work.

---

### Post by NertSkull on 2012-08-09
I was able to solve this problem on my system.  I tried to write up how I did it in the post I made on this topic.  Post #4.

[http://ubuntuforums.org/showthread.php?t=2038997](http://ubuntuforums.org/showthread.php?t=2038997)

Let me know if anyone has any questions.

---

### Post by mips on 2012-08-10
So my hunch was right :biggrin:

On a unrelated note apparently you can 'overclock' those monitors for higher refresh rates & better image quality if you are interested. When I say 'overclock' I'm using the term lightly, google has more info ;)

---

### Post by rockets on 2012-08-11
This was very serendipitous. I just got my Catleap monitor today and set it up successfully by following your link and adjusting for my second monitor particulars.

THANK YOU!

---

