---
title: "[SOLVED] ok this SHOULD be easy"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by Ripfox on 2007-11-06
I have an install of Kubuntu 7.10 and I want to install an ati 9250. All the how-to's I have read are old. How do we get this workin? I have an intel onboard, which is what I am using now. I haven't even put it in yet.


Thnx

---

### Post by Bliepo32 on 2007-11-06
> **ripfox said:**
> I have an install of Kubuntu 7.10 and I want to install an ati 9250. All the how-to's I have read are old. How do we get this workin? I have an intel onboard, which is what I am using now. I haven't even put it in yet.


Thnx

That the tutorials are old(er), doesn't mean they are bad. In fact, I found a how-to (sort of) which is just 3 weeks old: [http://ubuntuforums.org/showthread.php?t=575843](http://ubuntuforums.org/showthread.php?t=575843)

---

### Post by eye208 on 2007-11-06
> **ripfox said:**
> I have an install of Kubuntu 7.10 and I want to install an ati 9250. All the how-to's I have read are old. How do we get this workin?
As of Kubuntu 7.10 (Gutsy Gibbon) the recommended way to install the binary driver is to open System Settings KMenu &#8594; System Settings, go to the Advanced tab and click Restricted Drivers. Then click the Administrator Mode button and check the box marked Enable to install the driver. This should install the right package for your card and set it up for you.

---

### Post by Ripfox on 2007-11-06
Yes I found that one too, seems good but here's the problem. When I plug in the Radeon 9250, all I get is a blank screen on reboot. When I unplug it I get a gui via my onboard intel graphics chip. Do I follow the steps THEN plug in the pci card or how does that work?

Thanks for the reply!

---

### Post by eye208 on 2007-11-06
> **ripfox said:**
> When I plug in the Radeon 9250, all I get is a blank screen on reboot.
This is because X.org is configured for the Intel chip right now which will be automatically disabled by the BIOS when you insert the ATI card. You have to reset X.org to use the VESA driver, which works with any type of video card. You can do this by entering

sudo dpkg-reconfigure -pmedium xserver-xorg

into a terminal. Choose manual configuration and select the "vesa" driver from the list. Leave all the other settings unchanged. When you are done with configuration, reboot your system. X.org will now run in VESA mode. This will work with both Intel and ATI cards, so you can just put in the ATI card afterwards. X.org should not complain.

Then you can enable the binary ATI driver using the method outlined above.

---

### Post by Ripfox on 2007-11-06
Well I have done a frsh install of Gutsy, using the intel onboard video. The I used the dpkg interface to reconfigure the xorg to use vesa. Then I powered down, inserted the ATI 9250 (128) powered up, and it just hangs after the boot splash saying "cheacking battery state" and freezes. I canot even get to the desktop to USE the restricted driver manager.

Rip

---

### Post by Ripfox on 2007-11-06
Bump

---

### Post by bingoUV on 2007-11-06
In some motherboards, you have to explicitly disable onboard graphics to be able to use add-on graphics card. Can you try doing that?

---

### Post by Ripfox on 2007-11-06
Well, I know it was trying to use th ati card, because the boot splash was much smaller and better resolution. But when its full bar boot splash dissapears and goes to "checking battery state".

I tried to go into the bios and disable the onbord video but didn't see an option there...

Thanks for helping this is a real necessity as we are going broke and would like to start using some more economical means to record and playback media, but unfortunately this is the only pc I have right now..:(

---

### Post by Ripfox on 2007-11-06
I am very close to installing medio on this machine...:(

Anyone?

---

### Post by Lostincyberspace on 2007-11-06
If you can plug the card in then install it should work it self out.

---

### Post by Ripfox on 2007-11-06
Tried that too...wont boot to the desktop off the live cd.

---

### Post by Ripfox on 2007-11-06
FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device
FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device


Here's an error I am getting just before dpkg-reconfigure xserver-xorg.

Maybe this is significant.

---

### Post by wade32505 on 2007-11-07
I get the same error message. I installed Xubuntu 7.04 on a AMD DecTop. Resolution was fine till I upgraded to 7.10. Tried "sudo dpkg-reconfigure -phigh xserver-xorg" and get:
FATAL: Error inserting battery (?lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device.
Resolution is stuck on HUGE and the video driver is stuck on vesa, will not attach to AMD. 

Any ideas?

---

### Post by Ripfox on 2007-11-07
I think this might be a prolem with the bios being out of date in my case. Not sure but it stinks of that lol. Weirdly enough Dreamlinux boots to the ATI card fine. I don't want to use Dreamlinux, I want to use Ubuntu.

??

---

### Post by Ripfox on 2007-11-07
Ok so this ati card should boot to a desktop on the live cd? It goes BLANK!  :mad:

---

### Post by Ripfox on 2007-11-09
it was the bios. I tried a different batch of desktops and it boots. No tv out via svideo though :(

---

### Post by Ripfox on 2007-11-13
[http://ubuntuforums.org/showthread.php?t=215763](http://ubuntuforums.org/showthread.php?t=215763)

This thread solved my issues. :)

---

