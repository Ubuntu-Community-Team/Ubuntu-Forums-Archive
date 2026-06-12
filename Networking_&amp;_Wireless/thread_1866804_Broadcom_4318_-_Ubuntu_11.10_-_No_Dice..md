---
title: "Broadcom 4318 - Ubuntu 11.10 - No Dice."
date: 2011-10-22
forum: Networking &amp; Wireless
---

### Post by Roasted on 2011-10-22
I just installed Ubuntu 11.10 32 bit on this laptop which has a Broadcom card. Normally I'd rip Broadcom out of the system and toss it on the nearest highway but since this chip worked on the laptop before with 10.04 I'm giving it another shot. However, it's proving difficult as my wireless is simply not working.

I installed the firmware in Synaptic because NOTHING showed up in "Additional Drivers" except "software modem" which is clearly not it.

Any specific insight on how to get this gizmo working? It would be greatly appreciated!

---

### Post by Roasted on 2011-10-22
Hm, seems as if I got it working. I had to install the firmware that I found in Synaptic and then I ran sudo modprobe b43 and it came to life. I'm just a little baffled why it didn't show up in the Additional Drivers menu?

Man Broadcom never seizes to amaze me just why I avoid them at all costs. Nonetheless, glad this card is working.

---

### Post by Roasted on 2011-10-26
Well, seems as if the card isn't fully working. Upon further inspection, each time I would reboot it would act up. I would have to run "sudo modprobe b43" again each time I booted up for it to work.

The fix?

Add "b43" on a separate line to /etc/modules. Now each time I boot up, the wireless card works just like that. 

Is this considered a bug? Can I report this to Ubuntu? I'd much rather see this already implemented so somebody else doesn't have to fight over something so simple like I did in this case.

---

### Post by andied on 2011-10-26
What software did you install from Synaptic? The b43-fwcutter and firmware-b43-installer or bcmwl-kernel-source?

---

### Post by Roasted on 2011-10-28
> **andied said:**
> What software did you install from Synaptic? The b43-fwcutter and firmware-b43-installer or bcmwl-kernel-source?

I'm not even totally sure, to be honest... Is there a big difference between the two?

My big question is - why on earth didn't the 4318 come up with drivers in the Additional Drivers menu? I mean, my 4322 on another laptop did... *shrug*

---

### Post by RavanH on 2011-10-29
> **andied said:**
> What software did you install from Synaptic? The b43-fwcutter and firmware-b43-installer or bcmwl-kernel-source?

I can confirm that installing the dirver with ```
sudo apt-get install firmware-b43-installer
``` (which installs b43-fwcutter too) does indeed have this effect. The dirver is installed but after each boot the driver module needs to be activated with ```
sudo modprobe b43
``` to get the thing working. This was not the case in 10.10 (I skipped 11.04 since it did not support Gnome3) so it would seem to me like a missing piece (can you call that a bug?) in the firmware installer package...

For those that need a step by step, add the kernel module manually like this in a terminal window:
```
sudo gedit /etc/modules
```
Then add b43 on a new line at the end and save/close... Reboot.

---

### Post by Roasted on 2011-10-29
Id like to report this as a bug. But where? I thought I could just post on launchpad but evidently I can't do that...

ravanH, which card in particular do you have? 4318??

---

### Post by RavanH on 2011-10-31
> **Roasted said:**
> Id like to report this as a bug. But where? I thought I could just post on launchpad but evidently I can't do that...

ravanH, which card in particular do you have? 4318??

Yes, to be precise:
```
~$ lspci -vvnn | grep 14e4
00:15.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```

---

### Post by mörgæs on 2011-10-31
Moved to Networking and Wireless.

---

### Post by Roasted on 2011-10-31
Is there no way to "post" a new bug in Ubuntu or do you HAVE to go through the ubuntu-bug tracker or whatever it is that you launch from ALT F2?

---

### Post by Roasted on 2011-11-03
:confused::confused::confused::confused:

---

### Post by mörgæs on 2011-11-03
You can also post the bug straight into Launchpad:
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

- but take a good look around first. There are already some bug reports for this card, so maybe it is better if you confirm one of these.

---

### Post by Roasted on 2011-11-04
> **mörgæs said:**
> You can also post the bug straight into Launchpad:
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

- but take a good look around first. There are already some bug reports for this card, so maybe it is better if you confirm one of these.

Of course. Thanks for the link. :guitar:

---

### Post by mörgæs on 2011-11-04
You are welcome. Please mark the thread 'solved' if Launchpad is the solution (for now).

---

### Post by gefalu2008 on 2011-11-10
I just want to to confirm that the method described in post #6 by RavanH worked for me, too. My laptop is Acer 3620. Thanks very much, everyone!

---

### Post by alexxtasi on 2011-11-12
I also want to confirm that RavanH's method (in post #6) worked for a HP Pavilion DV5000 (dv5063EA) laptop.
But another problem came out :-(

[LIST=1]
[*]When I disable the wireless card using the hardware switch (just on top of the keyboard), it turns off and the networking applet shows "wireless is disabled by hardware switch" - which is fine...

[*]Using the same switch to activate the card again, the network applet shows "device not ready" and the card cannot work even if I try "sudo modprobe b43" in the terminal (don't know much about kernel, but I just tried this one ;-))

[*]Only when I reboot the wireless card works again!
[/LIST]

The network applet's messages are correct and I suppose that there is no problem with the keyboard's switch...

Is this a drivers problem which has to be reported?
any suggestions or solution?

thank you

**edit**: using the laptop, I found that I can enable or disable the wireless card pressing the proper keyboard button (hardware switch is called by network applet...) only once after restarting the machine

---

