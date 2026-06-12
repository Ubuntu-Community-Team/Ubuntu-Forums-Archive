---
title: "Random Reboot"
date: 2012-12-15
forum: Mythbuntu
---

### Post by GJLenon on 2012-12-15
I have Mythbuntu 12.04.1 running and am experiencing random reboots.

I have ruled out all hardware issues (Memory, Power, etc)
I have monitored cpu and system tempratures.
I have tried running 64 and 32 bit OS variants.
I have checked the system, kernel, dmesg, and Xorg logs, with no indication of trouble.

I'm running a Biostar NM70I-847 MB with onboard Intel Graphics, no additional drivers used.

I'm at wit's end. Where do I go from here?

---

### Post by chadk5utc on 2012-12-15
How old is the machine? is the power supply large enough to handle the load? Have you recently Installed anything new?? Changed Anything? More often than not its hardware related although it can be software related just not as often.

---

### Post by GJLenon on 2012-12-15
> **chadk5utc said:**
> How old is the machine? is the power supply large enough to handle the load? Have you recently Installed anything new?? Changed Anything? More often than not its hardware related although it can be software related just not as often.


Thanks for the reply. It's a new build. All components replaced. System is stable under Win7 build.

---

### Post by GJLenon on 2012-12-16
Apparently it only reboots when the Myth Backend is running...

---

### Post by tomono on 2013-01-23
> **GJLenon said:**
> I have Mythbuntu 12.04.1 running and am experiencing random reboots.


I experienced same random reboots on NM70I-847 too.
There is no problem and stable on WindowsXP, Windows8, CentOS6.3 and FreeBSD9.0.
(FreeBSD is only CUI)
Rebooting occurs on Ubuntu12.10, LinutMint13, LinuxMint14.

I feel this rebooting occurs on newer linux kernel.
So, I built newest kernel 3.7.1 and tried on Mint14. But rebooting occured.

Finally, I am using NM70I-847 with Windows8. It's very stable.

---

### Post by MadOCer on 2013-01-29
Hi guys (and gals ;) ),
 
I also bought this mainboard a while ago and also found that it runs perfectly stable with Win8 and older Linux Distros, like CentOS and Debian Stable. So, anything with an older kernel. Running Ubuntu 12.04, 12.10, Debian Testing/Wheezy or even OpenSuse 12.3 resulted in the mentioned sporadic reboots.
 
That seemed kind of suspicious, which is why I continued with some more testing.
 
What I came up with is the following theory:
 
It seems that the random crashes/reboots are based on Intel i915 RC6 (graphics core deep sleep) being enabled.
 
When I tested the theory on my Debian Wheezy install (yeah, I know, no Ubuntu :D ), the reboots stopped.
 
Try to add "[FONT=Courier New]i915.i915_enable_rc6=0[/FONT]" to /etc/default/grub "GRUB_CMDLINE_LINUX_DEFAULT". Should look something like this then:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=0"
```
 
Then run:
```
 
sudo update-grub

```
And reboot. 
 
If it remains stable that way, let me know! ):P 
Also if anyone knows how to check if RC6 is enabled in Windows, let me know about that, too. Would be great to know if Win8 runs stable with or without RC6 being active.
Because the question that needs answering the most is: Is this a BIOS problem, or is it the Linux Kernel? :confused:
 
**Edit:**
It seems like RC6 is disabled in Win8 by default. For one, the power consumption always was a little higher in Win8, in comparison to Linux with i915 RC6 enabled per command line. And, when disabling RC6 completely in BIOS, the power consumption figures didn't increase while idling in Win8. So, this could still be a BIOS issue, which only hits Linux, because Windows has the problematic option disabled by default.
 
**Edit 2:**
Should also work to just completely disable the two BIOS options concerning RC6. The effect should be the same, as changing the /etc/default/grub file.

[B]Edit 3:
Last edit after a long time. The procedure, described in "Edit 2" does NOT work! The BIOS option either doesn't work at all, or just gets ignored by the Linux kernel. So, the way with editing the grub file is the only one tht seems to work, so far.[/B]

---

### Post by tomono on 2013-02-10
> **MadOCer said:**
> 
Try to add "[FONT=Courier New]i915.i915_enable_rc6=0[/FONT]" to /etc/default/grub "GRUB_CMDLINE_LINUX_DEFAULT". 

I tried this on USB stick.(Since I'm already in Win8 stable operation for TV recording.)
Operating system is LinuxMint 13 MATE Edition 32bit.
Kernel version is 3.2.34 build without SATA drivers.

Before the change of GRUB setting, reboot occured twice within 3 hours.
After the change of GRUB setting, no reboot occured within 20 hours.

I think this change is to be effective!:P
Thank you!

---

### Post by MadOCer on 2013-03-20
Just a little follow up on this problem. I sent two mails to Biostar support about this problem + an additional one about USB booting. Obviously Biostar doesn't give a "you know what"! :frown: I never heard back from them and there is no fix! So, you know what to make of this. It's a real shame.:( They should be embarassed by their own lack of support, but it seems they just don't care.

---

### Post by MadOCer on 2013-11-20
Well, well, well...
 After months that the board just laid around, and BIOSTAR not giving a damn about the obvious problems with it, I had enough.
 I still would like to use the board, but then it should work like it is supposed to!
 So, I went ahead, installed Win7 + the great application "Thottlestop", which can display exactly which C-States the CPU uses to save power. With that data as proof I fired off a new suppot case to Biostar.
The CPU doesn't ever reach the C6 state, which is supposed to be its deepest sleep state. And that, even though it is explicitly enabled in BIOS. 
The wrong/erroneous implementation of the C6 (RC6) sleep state is also the problem that causes the Linux kernel to crash. I tested it! Problem is that the Linux Kernel even ignores the BIOS setting (if that even works). I set the RC6 feature in BIOS to disabled, but the Linux kernel still tried to use it and crashed. Added the bootargs, like described above, to disable i915 RC6 and it works.

 Now I am VERY interested to see, if a) they even understand the problem, b) pass it on correctly to a BIOS engineer and c) fix it accordingly, now that it's a "Windows problem". :D

---

### Post by victoraur.santos on 2013-11-22
I've also this MB, and also randomly reboots, disabling RC6 on i915 module stopped the reboots.

Ps: on BIOS it's already disabled but continues rebooting if not disable in i915 module!

a lot of thanks for you[COLOR=#000000] **MadOCer**[/COLOR]!

---

### Post by MadOCer on 2013-11-29
BTW, still no answer to the support request this time. And this time it was made clear that the problem concerns Windows, too.
So, I would conclude that Biostar's Support just is non existant! Worst company ever!
At the moment I would not recommend a single Biostar product to anyone, if support is simply not there, like it seems at the moment.

---

### Post by ergosteur on 2014-01-19
Thanks @MadOCer for the details and workaround! Having the same issue on Ubuntu, Debian, Arch... seems to be anything running a relatively recent kernel. Hopefully Biostar releases a BIOS update but not holding my breath.

I wonder if this is something that could be patched without Biostar's help? I know the OSX86 community hacks around with BIOS/ACPI stuff...

---

### Post by MadOCer on 2014-12-26
A small update after some time.
The NM70I-847 is now working as my parents' main desktop system. For that purpose it is OK, but as ever, it could still be way better.

First, because of changes in the i915 kernel module in recent kernel versions, the line that needs to be added to the "**/etc/default/grub**" file has changed.
It should now read:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.enable_rc6=0"
```

The kernel developers finally simply dropped the superfluous "**i915_**", so that it now looks more logical.

PLUS, I found another problem with the board. While using it with a SSD, a HDD and a DVD drive **in AHCI mode**, the system kept dropping the HDD while reading from DVD and resetting the complete SATA-bus in the course of that. GREAT STUFF!!! :rolleyes::rolleyes::rolleyes:
Those guys from Biostar can be really proud of what they released. =d>

**Setting the SATA ports to "[SIZE=4]IDE mode[/SIZE]" solved that problem.**
So I recommend that setting to anyone, who needs a stable system.

---

### Post by jpliberalino on 2015-09-21
I'm running a Biostar NM70I-847 MB and my Ubuntu 14.04 always reboots  randomly. I tried to add the line  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.enable_rc6=0" to the  "etc/default/grub" file, but it seems like that didn't work too. 

Has the parameter changed again?

---

### Post by MadOCer on 2015-09-23
I don't have the board anymore, so I cannot do a quick check. However, a simple question:
After editing the file, did you run "update-grub"?
If not, then this is the problem.

---

### Post by jpliberalino on 2015-09-23
Thank you for the answer! And yes, I did. Also, I have tested both parameters in the 64 bits version of Ubuntu 14.04. Now I am testing the second (i915.enable_rc6=0) on the 32 bits version of the system. Until now it didn't rebooted by itself (I'm running it in the past 7 hours), but for now this doesn't mean so much because this thing happens randomly. If the problem is really solved I will update this topic in a few days.

---

### Post by jpliberalino on 2015-10-04
**UPDATE:** the system looks more stable now. 
It isn't rebooting randomly anymore, the parameter "i915.enable_rc6=0" to be added to the line "GRUB_CMDLINE_LINUX_DEFAULT= " is really effective, but I was confused because the desktop was rebooting by itself when suspended too. 
So I followed the instructions of [this thread]("http://ubuntuforums.org/showthread.php?t=1556934") and it doesn't reboot by itself in any way.

---

