---
title: "upgraded to 9.10 from 9.04 - sound dummy output?"
date: 2009-11-01
forum: Multimedia Software
---

### Post by psidrum on 2009-11-01
i get a Dummy Output for Sound, and not detecting my audio hardware, im using SB X-Fi,

---

### Post by waspbr on 2009-11-01
try this in the terminal

```
sudo alsactl restore
```

your problem has been somewhat discussed in this thread 

[http://ubuntuforums.org/showthread.php?p=8100171#post8100171]("http://ubuntuforums.org/showthread.php?p=8100171#post8100171")

gl

---

### Post by t-force on 2009-11-01
I'm getting the same problem (using an old Soundblaster Audigy), and I've tried doing the terminal command suggested, but I get a message saying:

alsactl: load_state:1608: No soundcards found...

Anyone got any ideas? My sound was fine in 9.04.

---

### Post by p110011 on 2009-11-01
Same problem....on-board AC-97

At least my Bluetooth A2DP headphones work now?

---

### Post by bhaskaran on 2009-11-01
same problem for me
'sudo lshw -C sound'  returns both my sound cards but 'sudo alsactl restore' returns "Nosound card found..." Pl help

---

### Post by psidrum on 2009-11-01
> **waspbr said:**
> try this in the terminal

```
sudo alsactl restore
```your problem has been somewhat discussed in this thread 

[http://ubuntuforums.org/showthread.php?p=8100171#post8100171](http://ubuntuforums.org/showthread.php?p=8100171#post8100171)

gl

i tried this command, still doesnt work,

---

### Post by epek on 2009-11-01
on my hp nx7400 this issue was caused by the proprietary modem driver:

workaroud  if you don´t need the modem:
German: System/Systemverwaltung/Hardware Treiber 
English, I suppose: System/Administration/Drivers

-> then deactivate the modem.

---

### Post by fabio.hipolito on 2009-11-01
> **epek said:**
> on my hp nx7400 this issue was caused by the proprietary modem driver:

workaroud  if you don´t need the modem:
German: System/Systemverwaltung/Hardware Treiber 
English, I suppose: System/Administration/Drivers

-> then deactivate the modem.

Thank you,

I formated and installed just now Ubuntu 9.10 Karmic Koala and then installed nVIDIA's and SmartLink modem proprietary software. After that I noticed that I had no sound, after having deactivated the proprietary modem driver and the problem was solved.

Best regards.

---

### Post by p110011 on 2009-11-01
I got sound! I was booting to the Jaunty kernel, for some reason, and after uninstalling linux-headers-2.6.28-11 and installing linux-headers-2.6.31-14 my sound works, and so does my bluetooth stereo!

My wireless DID quit tho:(

But I found a thread to fix that too.....

---

### Post by Tubbytee on 2009-11-08
Hi, I've got the same problem, but have no proprietary modem drivers installed, hence nothing to disable in Hardware Drivers!

lspci gives:

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
```

but

aplay -l gives:

```
aplay: device_list:223: no soundcards found...
```

Hmm....

What do ya think? (Complete newb at a dead end!)

Thanks in advance guys.

Tubby

---

### Post by p110011 on 2009-11-08
Are you using the correct kernel in 9.10?

uname -a

---

### Post by Tubbytee on 2009-11-08
Ok, 

uname -a gives:

```
Linux toaster-laptop 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux
```

But I upgraded using the Upgrade Manager, so I'm assuming that it used the correct kernel when it did the upgrade?

Thanks again

Tubby

---

### Post by p110011 on 2009-11-08
> **Tubbytee said:**
> Ok, 

uname -a gives:

```
Linux toaster-laptop 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux
```But I upgraded using the Upgrade Manager, so I'm assuming that it used the correct kernel when it did the upgrade?

Thanks again

Tubby

To get the Kernel for 9.10 I used the package manager System>Administration>Synaptic Package Manager

In the quick search type 2.6.31 and install Linux-Headers-2.6.31.14-Generic and Linux-Image-2.6.31-14-Generic

---

### Post by timmson on 2009-11-09
May be usefull:
[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/430515](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/430515)
I had solved my problem.

---

### Post by p110011 on 2009-11-09
Bug report of what I was seeing:[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/463853](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/463853)

And the cause (probably user)```
           > Uname: Linux 2.6.28-16-generic x86_64 
 Please note that this is the 9.04 kernel, not the 9.10 kernel.
 Were you prompted to reboot after upgrade?  Have you done so?
 If you have rebooted and the 9.04 kernel is still the one running, were you prompted during the upgrade about whether to keep changes to /boot/grub/menu.lst vs. letting the system overwrite this file? Please attach /boot/grub/menu.lst and /boot/grub/menu.lst~ from the affected system in this case.

        

```

---

### Post by Tubbytee on 2009-11-10
Doh!

Yes you're right, it was just the wrong kernel being loaded by grub! I obviously wasn't thinking when I upgraded and didn't let it overwrite the menu.lst! I've edited it now and it's loading the right kernel which has made my sound card work!

Thanks for your help guys,

Tubby

---

### Post by Tubbytee on 2009-11-10
Just a quick question (and trying to further my Linux knowledge!)

Why would the upgrade process give you the option of keeping a kernel that wasn't properly compatible with the 9.10 upgrade? Why wouldn't it just automatically update the menu.lst file so it was loading the correct kernel like it does upon normal kernel updates?

Cheers,

Tubby

---

### Post by p110011 on 2009-11-10
I was thinking the same thing Tubby, makes no sense to me:confused:

---

### Post by psidrum on 2009-11-12
I fixed my problem,

my problem was it was loading the old kernel from 9.04 but yet the system was being read as Karmic 9.10

what i did was install Grub-pc, after that i was able to see the new 9.10 kernel in the boot menu, then automatically ran it,

after running the new kernel, it started to read everything, my soundcard was detected as well as my graphic card.

so if you upgraded  check to see if your system is actually running the 9.10 kernel which is 2.31, if it is not loading it, install grub-pc

---

### Post by wavesound on 2009-11-23
HI All
I too have this problem.
M-audio 2496 card worked in all my buntu's apart from this new upgrade

Is this a pulse Audio thing? also why is sound not working such a low priority in Ubuntu now? Basically these days no sound is no PC working.

So we upgrade and things stop working. great for the windows fan boys
bad  for Linux in general.
I don't seem to see a solution to this on here ** I do now re the kernel so I must install grub=pc and if that fails I have no PC! Not really ready for the general user then!.
Here goes
*********************************************

 Ok I installed grub-pc and still cannot get the newer kernel, So no sound at moment, so how do I get grub to show the new kernel ( first time this has happened! Does synaptic not install the kernal correctly?)
Cheers
Bob

---

### Post by p110011 on 2009-11-23
> **wavesound said:**
> HI All
I to have this problem.
M-audio 2496 card worked in all my buntu's apart from this new upgrade

Is this a pulse Audio thing? also why is sound not working such a low priority in Ubuntu now? Basically these days no sound is no PC working.

So we upgrade and things stop working. great for the windows fan boys
bad  for Linux in general.
I don't seem to see a solution to this on here

Cheers
Bob

For me, "This problem" was I did not use the new Kernel information for Grub1, I think they gave the choice of overwriting or not. Either use Linux-kernel 2.6.31 in Grub, or upgrade to Grub2

---

### Post by wavesound on 2009-11-23
HI
I did upgrade to grub-pc but you need to run an update script to install the new grub.
This not a normal thing to do when installing via synaptic.
I now have grub2 and the new kernels so sound is working.
Is this  worth doing an upgrade?
I would recommend a new install untill theses problems are sorted out.
Thanks for the help.

Cheers
Bob

---

### Post by limescout on 2010-07-23
Here is the solution I used for this problem, after trying the others.

1.  Navigate to /sys/bus/pci/devices
2.  in terminal, enter ```
lspci
``` to list pci devices.
3.  One of the items in the list should be an audio device.  On the far left of the entry is a sequence like 00.1b.0 or something in a similar format.  Remember this.
4.  back in the devices directory, find the subdirectory with the same code displayed in lspci.  Mine was "0000.00.1b.0"
5.  In this directory, there is a file called "enable".  Open it with ```
sudo gedit enable
``` there should be one character, a 1.  Change the "1" to a "0" (no quotes), save, reboot.

I apologize if this is hard to understand or does not follow a proper format, it's my first solution I discovered on my own.

---

### Post by limescout on 2010-07-24
Oops!  On subsequent reboots, value of "enable" changes back to 1.  Does anyone know how to fix this?

---

