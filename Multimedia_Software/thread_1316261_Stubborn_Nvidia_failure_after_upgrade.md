---
title: "Stubborn Nvidia failure after upgrade"
date: 2009-11-05
forum: Multimedia Software
---

### Post by serenegreen on 2009-11-05
I had been running Hardy on my x86 32-bit with an Nvidia 7300 GT card for a couple months with no problems using the drivers off their website.  

I was trying to get my new Ipod to work (always the Ipod haha) and had to upgrade. which threw out the nvidia setup and put me in low graphics mode..  As usual I went to Nvidia's website to get the driver which turned out to be the new 190 one, thought nothing of it.  Now my screen flickers when X is trying to start and Gnome says it can't get my video card settings to work so it stays in low graphics mode.  

I tried a couple things from this forum and Ubuntusolutions and tried the old 185 version, but nothing fixes it.  it won't do a clean reboot either, this freezes the first HP screen I get during boot and I have the unplug.  I've been an Ubuntu user for years and have gotten over all sorts of issues with graphics cards and otherwise, but can't shake this one.  Help?

---

### Post by serenegreen on 2009-11-05
Thinking about a clean re-format.

---

### Post by HappyFeet on 2009-11-05
> **serenegreen said:**
> this freezes the first HP screen I get during boot and I have the unplug.

That right there tells me that it's not a video driver issue. The OS has not loaded yet, and therefore the video driver will have no effect on the boot up screen. Sounds like a hardware issue.

---

### Post by serenegreen on 2009-11-05
Bummer.  I've been considering a hardware upgrade within 2 months but didn't want to rush it.

---

### Post by iruel on 2009-11-05
it was xorg problem, the option is you can reinstall the OS,or you recover it from recover-boot on grub-menu,and then you need to install the driver manually, and the last option you need to reconfigure file **/etc/X11/xorg.conf**
but AFAIK i usually install driver manually, it's for check compatible with the new kernel

---

### Post by serenegreen on 2009-11-08
> and the last option you need to reconfigure file **/etc/X11/xorg.conf**
but AFAIK i usually install driver manually, it's for check compatible with the new kernel

Is it difficult to reconfigure and not have to re-install Hardy?  That's be preferable for sure.

And are we talking a clean install, new boot manager and everything?

---

### Post by iruel on 2009-11-10
no no no,we not talking about clean install with new environment, but it's like this command 
```
sudo nvidia-xconfig
```

---

### Post by serenegreen on 2009-11-10
No... that is part of a standard nvidia install and does not fix it.  

Bump for some help?

---

### Post by HappyFeet on 2009-11-10
> **serenegreen said:**
> it won't do a clean reboot either, this freezes the first HP screen I get during boot and I have the unplug.

I will repeat myself. If you can't get past the first boot up screen, it is not an ubuntu issue. Ubuntu has not loaded yet, therefore it can not be the problem. You probably have a bad video card. But only diagnostics will reveal the real culprit. PM me if you want info on doing diagnostics.

---

### Post by serenegreen on 2009-11-11
Hey, sorry to leave this out but yesterday I tried disconnecting an external hardrive before rebooting and had no problems.  Could it still be a hardware issue?

I'm going to try an old nvidia card anyway, already have the legacy driver.

---

### Post by serenegreen on 2009-11-11
Very weird!

My old card worked with the Nvidia screen flashing before logon.  After logging on it flashed again and the resolution went way down.  I could then use the config utility to get the resolution back up and do multiple displays etc, but after restarting the X server it lost these settings.  I also could not play Planet Penguin Racer which has always been my test.

Put the newer card back in and it exhibits the same behaviour.  It's as if logging on as the user resets the configuration, very strange.

---

### Post by serenegreen on 2009-11-11
With the Nvidia screen flashing and the resolution looking normal during login, can I assume the card is working properly at that point?  Are there user-specific settings that are then over-riding the good configuration and causing the post-logon flashing and suckage?

Also, in the x config utility when I save the file, it gives an error that it can not delete the old backup file.  Does this mean thatg it's not saving the settings?

---

### Post by serenegreen on 2009-11-11
As far as I can tell, the reboot problem wasn't related to this topic... the external drive would just hang when it's getting ready to boot.  A red herring perhaps!  A very exciting problem indeed...

---

### Post by HappyFeet on 2009-11-11
> **serenegreen said:**
> 

Also, in the x config utility when I save the file, it gives an error that it can not delete the old backup file.  Does this mean thatg it's not saving the settings?
Are you doing 
```
sudo nvidia-settings
```???

---

### Post by serenegreen on 2009-11-16
Yes, I've run nvidia-xconfig using sudo.  It's very strange that the display appears to be working properly before logging in.   Any ideas?

---

### Post by iruel on 2009-11-17
i don't get what you meanabout [B]It's very strange that the display appears to be working properly before logging in.

[/B]it's give option or not??

---

