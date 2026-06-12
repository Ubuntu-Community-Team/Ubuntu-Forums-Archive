---
title: "Unable to enable wireless on computer"
date: 2012-08-09
forum: Networking &amp; Wireless
---

### Post by Newmandude on 2012-08-09
I can't turn on the wireless hardware button on my computer. When I type in rfkill list, it says the phy0 Wireless Lan is hard blocked (Not soft blocked). Please help ASAP.

---

### Post by anewguy on 2012-08-09
If possible, wait for wildmanne39 to get to you - he's an expert in all of this.  In the mean time, you may want to check one of his recent posts, find the script he has, download it and follow the instructions for running it and posting it back here as that will give you a head-start - see post #8 in this thread:

[http://ubuntuforums.org/showthread.php?t=2038977]("http://ubuntuforums.org/showthread.php?t=2038977")

---

### Post by kurt18947 on 2012-08-09
Anewguy gives you good advice.  In the meantime though you could try this in a terminal - I don't think it'll do any harm.

"rfkill unblock all"  

There were a few wifi adapters that if disabled in Windows had to be enabled in windows then log out of Windows and log into Linux.  I don't know how common that issue was.

---

### Post by Newmandude on 2012-08-09
I did up to post #13. I'm still a newb, but I'm pretty sure i uploaded the link of the txt. if not, please tell me how to do it. Also, the rfkill unblock all idea only unblocks the soft block, not the hard blocked. Unfortunately, I do not have my original OS (which I regret.)

---

### Post by wildmanne39 on 2012-08-09
Hi, please do:
```
gksudo gedit /etc/rc.local
```
Add your three lines above exit 0:
```
modprobe -r ath9k
rfkill unblock all
modprobe ath9k
```
Reboot
Make sure your wireless is turned on, you may need to look at the documentation because some computers have to ways to turn wireless on.
Thanks

---

### Post by Newmandude on 2012-08-10
I should probably tell you that my computer has a wireless button, but it does not work while I'm using Linux.

---

### Post by wildmanne39 on 2012-08-10
Hi Newmandude, that is what we are working on, so I need you to play with the wireless on button or key and check with ```
rfkill list all
```
Did you do what I suggested in my last post? What was the outcome?
Thanks

---

### Post by Newmandude on 2012-08-10
i did what you told me, but there was no change. When I type in rfkill list all, it responds,

```
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

I already know that typing in ```
rfkill unblock all
``` only unblocks the soft block on my computer, but not the hard block. Do I put the three lines you told me right above exit 0, because that's what I did.

---

### Post by wildmanne39 on 2012-08-10
Hi, yes that is where you add them, please post the contents of:
```
gksudo gedit /etc/rc.local
```
Thanks

---

### Post by Newmandude on 2012-08-10
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
modprobe -r ath9k
rfkill unblock all
modprobe ath9k
exit 0
```

these are the contents.

---

### Post by wildmanne39 on 2012-08-10
Hi, can you tell us your computer brand and a link to the manufacturers site please?
Thanks

---

### Post by Newmandude on 2012-08-10
I have an hp pavilion dv5. When you say manufacturers site, what exactly do you mean?

---

### Post by wildmanne39 on 2012-08-10
Hi, go to the hp documentation page for your computer then post a link here so we can look at it.
Thanks

---

### Post by Newmandude on 2012-08-10
I'm not sure if this is what you're looking for:

[http://h10032.www1.hp.com/ctg/Manual/c01550108.pdf]("http://h10032.www1.hp.com/ctg/Manual/c01550108.pdf")

---

### Post by wildmanne39 on 2012-08-10
Hi, if you have windows installed go into windows and turn the wireless off then back on before booting ubuntu.

In ubuntu I recommend also trying fn + f1-f12 one at a time and see if one of those key combinations turn it on. 

One special case the keys that turn wireless on and off was not the expected key. A recent case was not Fn+f12; it was Alt+F12 that activated the wireless so try that as well then check with:
```
rfkill list all
```
to see if the hardblock is gone also watch for the wireless light to come on.
Thanks

---

### Post by Newmandude on 2012-08-11
I tried to do all the fn+f1-12 commands, and the alt+f1-12 commands, but none of them worked.

---

### Post by wildmanne39 on 2012-08-11
Hi, open ```
gksudo gedit /etc/rc.local
```
change [COLOR="Red"]modprobe -r ath9k[/COLOR]
to [COLOR="Red"]rmmod -r ath9k[/COLOR]
save, close gedit and reboot.
Thanks

---

### Post by Hadaka on 2012-08-11
Hi,Look at your Power Plan options. Under Advanced options it may be set to turn off wireless to save battery power. 
under windows..
control panel..
power options...
avanvced..
even though ubuntu is a different os, windows may have a bit set high on your
controller board . change that setting and see if it helps.

---

### Post by Newmandude on 2012-08-11
tried the changing the gedit, but it didn't help.

---

### Post by wildmanne39 on 2012-08-11
Hi, I asked earlier if you have windows installed but I do not believe you said if you do try what I recommended in a previous post.
Thanks

---

### Post by Newmandude on 2012-08-11
no, I do not have windows installed

---

### Post by wildmanne39 on 2012-08-11
Hi, I think I found the issue, open:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
and add a hash (#) in front of [COLOR="Red"]blacklist hp_wmi[/COLOR]
save, close gedit and reboot.

You may still have to turn wireless on with the switch or key combination
Thanks

---

### Post by Newmandude on 2012-08-11
I should probably tell you that my Zorin OS had reset, so will I have to do the steps again?

---

### Post by wildmanne39 on 2012-08-11
Hi, post the script again so we can see what the situation is now before you make any changes.

Do you mean you reinstalled?

---

### Post by Newmandude on 2012-08-11
here. And yes, I mean that It's been re installed. Well really, I replaced the Other Zorin OS withe the same OS. Also, I'm thinking about changing my current OS to Zorin Os 6 Lite. Will this change the script in any way?

---

### Post by wildmanne39 on 2012-08-13
Yes, it can change the script information.

I have went over all the posts in this thread and everything I can think to do is already listed so you can apply the changing to the new install one at a time and see if that helps if not then I am out of idea's.
Thanks

---

### Post by Newmandude on 2012-08-14
Unfortunately, it still does not work. But I want to ask where to find an app called Hardware Drivers.

---

### Post by wildmanne39 on 2012-08-14
Hi, your driver is already loaded for your card and the firmware and your driver does not show up in hardware drivers.
Thanks

---

### Post by Newmandude on 2012-08-16
So wait, I already have the driver for my wireless card, and that It's loaded? If so, then why doesn't the wireless switch work on Ubuntu? I thought it was because the wireless card and/or the driver just doesn't work on Ubuntu.
Also, I won be here for the newt few days. So please don't ask for a reply

---

### Post by wildmanne39 on 2012-08-16
I do not know but I will ask a friend if he will look.
Thanks

---

### Post by jskinner1724 on 2012-08-16
I don't mean to ask the incredibly stupid questions, but what is your result of sudo lspci?

The reason  I ask is that I had a system that loaded the wrong driver by default. I'm sure that this was an isolated event, but just curious...

---

### Post by Newmandude on 2012-08-24
sorry I was gone for a while. Anyways, the result is 

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

By the way, I just upgraded to Zorin OS 6, so the situation might be different

---

### Post by Newmandude on 2013-07-10
I know this is EXTREMELY late, but I finally solved the issue. Simple, really. All I did was go to the bios menu when the computer turns on and select load setup default. Perhaps this [link will]("http://www.youtube.com/watch?v=eB2-oaePlKc") be a better demonstration.

---

