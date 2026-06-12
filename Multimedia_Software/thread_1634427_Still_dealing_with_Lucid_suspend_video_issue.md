---
title: "Still dealing with Lucid suspend video issue"
date: 2010-11-30
forum: Multimedia Software
---

### Post by nerdybrunette on 2010-11-30
Hey all,
 
It seems that this has been posted numerous times all over the place, but I still cannot find a working solution for me.
 
When I execute on my PC
 
```
s2ram --force --vbe_mode --pci_save --acpi_sleep 1
```
 
Then when I hit the power button to wake back up, the video never comes back. The monitor never even wakes back up. 
 
I don't know what video card I'm running, or even how to find out.

---

### Post by Ceyx on 2010-11-30
You can find your video card with the command:

lspci

in terminal.

---

### Post by nerdybrunette on 2010-11-30
Okay, I had done that before but I didn't know if that was it, since it isn't very descriptive.
 
Here's the output of that command:
 
```
00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)

```
 
And here's more:
 
```

# lspci -v -s `lspci | awk '/VGA/{print $1}'`
 
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
 Subsystem: Intel Corporation Device 8119
 Flags: bus master, fast devsel, latency 0, IRQ 11
 Memory at 94000000 (32-bit, non-prefetchable) [size=512K]
 I/O ports at 4070 [size=8]
 Memory at 80000000 (32-bit, non-prefetchable) [size=256M]
 Memory at 94080000 (32-bit, non-prefetchable) [size=256K]
 Capabilities: [d0] Power Management version 2
 Capabilities: [b0] Vendor Specific Information <?>

```

---

### Post by Ceyx on 2010-11-30
So there : You have an Intel Graphics card.

What exactly is it you want to deal with ?

---

### Post by nerdybrunette on 2010-11-30
I need to be able to bring video back up after suspending the system.

---

### Post by Ceyx on 2010-11-30
Are you using a notebook computer ?

Try to turn off ACPI in the Grub Boot Loader :

"sudo gedit /etc/default/grub"

Change the line that looks like :

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"

Save the file.  Update Grub:

"sudo update-grub"

reboot your machine.  If the problem goes away then it is ACPI that is causing your headaches - there are different acpi=xxxx options for you to research and play with.

Good luck !

---

### Post by nerdybrunette on 2010-12-01
Well, we made progress :D Thanks for helping!
 
Now, the s2ram command puts the PC to sleep, but it is kicked back out of it almost immediately, bringing the PC right back to the desktop (video works). 
 
Do you know of anything that may kick it out of suspend mode (with the acpi=off option on)?

---

### Post by Ceyx on 2010-12-01
Great ! Progress is good....

Two questions : 1: what is the name/model of the computer you are using ?

2: why are you using suspend to ram commands ?  There is a symbol of a power button on your menu bar at the top.  Within that there should be a suspend/hibernate option one could use.  Have you tried it ??

ACPI is an issue some of us Linux users have been dealing with, some with better luck than others.  We should be able to nail this one though !


Ciao !

---

### Post by nerdybrunette on 2010-12-01
I'm actually on a PC that I built myself. :)
 
The suspend button does not work either, unfortunately. 
 
I know that the chipset uses GMA500, which seems to be causing a lot of people a lot of grief according to my research ](*,)

---

### Post by Ceyx on 2010-12-01
Random thoughts:

Look at the Bios settings, under "power", also check "Wake on Lan" which would wake it up.

Does Hibernate work ?

Is this an Atom Board ?  Does it support "suspend to ram" ?

Try using a keypress instead of the power key to resume...

In Synaptic - search for pm-utils, and add its recommendations.

Keep me posted !

Ciao

---

### Post by nerdybrunette on 2010-12-02
Hibernate doesn't work. I get a bunch of error messages. 
 
As far as BIOS settings are concerned, I have the following settings:
P-States <Enabled>
Hyper Threading Support <Enabled>
C-States <Enabled>
Enhanced C-States <Enabled>
C6-State <Enabled>
 
This: [http://www.cpu-world.com/CPUs/Atom/Intel-Atom%20Z520PT%20CH80566EE014DT.html](http://www.cpu-world.com/CPUs/Atom/Intel-Atom%20Z520PT%20CH80566EE014DT.html) is my board. Yes, it's an Atom board, and yes it supports suspend to ram.
 
When I press a key on the keyboard, all of the lights light up on it for a quick second, but nothing else happens. 
 
According to the Synaptic Package Manager, I have the latest version of pm-utils (1.3.0-1ubuntu2) and pm-utils-powersave-policy (0.3.1)

---

### Post by Ceyx on 2010-12-02
"When I press a key on the keyboard, all of the lights light up on it for a quick second, but nothing else happens."

Ahha !

Two suggestions.

1: Try ACPI=Linux  in Grub

2. Note the computers time of day ...suspend / resume ( using the keyboard first ), then have a look at the logs in /var/log  ; in particular pm-suspend and pm-powersave.

pm-suspend takes a bit to get used to but the idea is that it puts the state of the computer away, goes to sleep, and when it wakes up it reverses the order of what it put away, if you will.  It should be here that you find what is not happening.  The order should be 1,2,3, etc, etc, -suspend then -awake, etc,etc,3,2,1.  ;)

Take a lOOk !

---

### Post by nerdybrunette on 2010-12-03
No luck with the acpi=linux option :frown:
 
What sucks is that I'm booting from a stick (I can't install it to the HD) so there is no help for me concerning messages in log files from shutdown - as they don't exist when I boot back up. 
 
I'm sure those would give me very valuable information concerning what's happening here, especially since I hear an noise signifying that an error message or something is popping up (which I of course, cannot see) after I hit the power button to bring it back from suspend, and it fails.

---

### Post by Ceyx on 2010-12-03
Get rid of the "quiet splash" option in grub.....you may see more of the error messages.

Can you clone the stick ?  If so, boot with each, put one to sleep and use the other to look at the messages.  Perhaps 1/2 of the process would be in /var/log/pm-suspend ?

You may not want to hear this, but some things have taken me months to figure out - but I did and it was worth it. Great way to learn.....

Ciao !

---

### Post by nerdybrunette on 2011-01-14
> **Ceyx said:**
> Get rid of the "quiet splash" option in grub.....you may see more of the error messages.
 
Can you clone the stick ? If so, boot with each, put one to sleep and use the other to look at the messages. Perhaps 1/2 of the process would be in /var/log/pm-suspend ?
 
You may not want to hear this, but some things have taken me months to figure out - but I did and it was worth it. Great way to learn.....
 
Ciao !
 
Ceyx, thanks a lot for all of your input. 
 
I've decided to take a break from this issue for a while, and hopefully when I return to it, it will be with fresh eyes!
 
Thanks again for all of your help!

---

### Post by Ceyx on 2011-01-14
HeH...taking a break always works for me ! 

Let me know when you are back on the air - perhaps we can figure it out yet..

Ciao !

---

### Post by Ceyx on 2011-01-14
:d

---

