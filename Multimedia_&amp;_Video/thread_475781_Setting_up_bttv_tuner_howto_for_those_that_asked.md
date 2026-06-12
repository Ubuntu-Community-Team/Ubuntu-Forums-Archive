---
title: "Setting up bttv tuner howto for those that asked"
date: 2007-06-16
forum: Multimedia &amp; Video
---

### Post by crispy_420 on 2007-06-16
Seems there is many posts on setting up a bttv tuner based TV card so is here is my simple howto:

First we to know the card type

```
dmesg
```

You then get a ton of info about your system but look for the bttv reference. It will say (card=XX) where the "XX" is some number.

Does it have an FM tuner? Simple yes or no here.

What is you TV standard?

Once why have all this now to do a simple edit of your modules.

```
sudo gedit /etc/modules
```

Near the bottom just copy and paste my setup.

```
# TV
alias   char-major-81   bttv
pre-install bttv        modprobe -k tuner; modprobe -k msp3400
options bttv            radio=1 card=34
options tuner           type=2
```

Now you just need to change mine so it matches your hardware.

tuner= will be your TV standard, check the chart at this page:
[http://linuxtv.org/v4lwiki/index.php?title=Leadtek_WinFast_2000&printable=yes](http://linuxtv.org/v4lwiki/index.php?title=Leadtek_WinFast_2000&printable=yes)
Look about mid way through page the # that matches your standard/country.

card= that number you got from dmesg

radio= 1 is you have an FM tuner and 0 for none (not 100% sure of this part)

Save the modules file and you are done with setup. Now you can install a TV viewing app and FM radio app. I like tvtime for tv and gnomeradio for FM.

```
sudo apt-get install tvtime gnomeradio
```

Now you can either load the modules or reboot and you should be set to go.

Sometimes my ideas don't get relayed correctly so if this does not add up or work, post back.

Almost forgot, if tvtime fails to launch from menu try launching from terminal to get the error. Most likely it is a video driver issue.

---

### Post by midnight2036 on 2007-06-19
Crispy_420

You failed to mention which Kernel you are running. In my case as posted I'm running Fiesty for AMD X86-64. The package manager bungled the install as near as I can tell. I created a bash script to uninstall BTTV and BT878 driver and then reinstall. The tuner works fine this way.

I had tried using /ect/modules but that did not work. I also might add Fiesty is one of the slickest packages yet even though it failed to run a TV card out of the box that has run on every Linux version since 2.4...Red Hat, Fedora, Mandrake, Mandriva , Suse ect.

Bob

---

### Post by crispy_420 on 2007-06-21
I have the most current stock kernel on 32-bit OS. I never used 64-bit so I can't comment on that but could you ust add that in to my post to help others too.

---

### Post by midnight2036 on 2007-06-22
crispy_420,
I had seen your earlier post and had tried the traditional edit of /ect/modules, ala modules.config but it had no effect. I see where you are using 6.06. The problem listed is occurring in almost all distros of the latest kernels except for maybe Mandriva which has KDE configuration tool to edit the driver configuration.  I find this strange because the Linux video project bttv has been stable for a long time with no significant changes.

I am not a programmer but hinge on experienced user level as I've used linux desktop since about 1998. In messages and dmesg it appears as though there are duplicate instances of bt878 being run which give the final fatal errorat the end of the driver install. The catch 22 is the manual removal and manual install work! :)

In mean time my script works and someone more skill than I will figure it out. I beleive it has to do with the kernel changes and modules.d

sincerely,

Bob

---

### Post by crispy_420 on 2007-06-24
This has worked for me since my first install of Ubuntu. So I think 5.04. Also I am currently running 6.06 and 7.04 and it worked on both.

---

### Post by crobinson55331 on 2007-09-30
I am sorry that I cannot follow your instructions.  My dmesg returned the following:
[   13.748000] ivtv:  ==================== START INIT IVTV ====================
[   13.748000] ivtv:  version 0.10.1 (tagged release) loading
[   13.748000] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   13.748000] ivtv:  In case of problems please include the debug info between
[   13.748000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   13.748000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   13.748000] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   13.748000] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   13.748000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 20
[   13.776000] NET: Registered protocol family 17
[   13.784000] Linux agpgart interface v0.102 (c) Dave Jones
[   13.816000] nvidia: module license 'NVIDIA' taints kernel.
[   14.424000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   14.640000] ivtv0: Encoder revision: 0x02050032
[   14.640000] ivtv0: Recommended firmware version is 0x02060039.
[   14.704000] tveeprom 0-0050: Hauppauge model 26152, rev E5B2, serial# 10384978
[   14.704000] tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   14.704000] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   14.704000] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   14.704000] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   14.704000] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter
[   14.704000] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   14.704000] ivtv0: reopen i2c bus for IR-blaster support
[   14.764000] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   14.920000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   18.184000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   18.268000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   18.312000] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   18.312000] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   18.312000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   18.312000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   18.312000] tuner 0-0061: type set to 50 (TCL 2002N)
[   18.648000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   18.648000] ivtv:  ====================  END INIT IVTV  ====================

I see no reference to bttv.  TVTime says there is no signal - IVTV invalid argument - cannot open capture device /dev/video0  ??  Any help for this noob would be appreciated.

---

