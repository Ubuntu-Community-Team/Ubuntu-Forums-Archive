---
title: "system freezes and tuner cards swapped on boot"
date: 2008-03-20
forum: Mythbuntu
---

### Post by Errorsmith on 2008-03-20
Hi

I'm using mytbuntu 7.10.  I'm using it with an AMD XP 3000 on an Asus A/V600-X Board. I have two tuner cards. On the one hand I have a Hauppauge WinTV PCI FM and on the other hand a Hauppauge PVR350.

The first problem I have is that, whe I record something with the PVR350, my system freezes after a while. It doesn't matter if I watch the recording at the same time or if the frontend is running. When I press the reset button, mythbackend tries to continue the recording wich leads to a new freeze almost immediatly (it keeps running max 5 minutes). 

At first I thought my card might get too hot. After mounting a 40mm fan on the heatsink of the encoder chip, I found out that either the fan is too small or overheating ist not the problem. The system locks anyway. Also I get errors like this in /var/log/messages:
```

Mar 19 21:18:13 mythtv kernel: [ 6342.797975] msp3400 2-0040: I/O error #0 (read 0x12/0x18)
Mar 19 21:21:28 mythtv kernel: [ 6537.565524] msp3400 2-0040: I/O error #0 (read 0x12/0x18)
Mar 19 21:21:53 mythtv kernel: [ 6562.546164] msp3400 2-0040: I/O error #0 (read 0x12/0x18)
Mar 19 21:26:58 mythtv kernel: [ 6867.176063] msp3400 2-0040: I/O error #0 (read 0x12/0x18)

```
I already tried using different PCI slots for my various cards, googled, enabled and disabled ACPI and APIC and finally tried to reinstall the system using another distro but nothing worked. Is there a starting point where I can look for problems, anything wich helps me to find out where the problem sits?

My second problem is that my tuner cards get shuffled around after each cold start. Lets say I have 
```

/dev/video0 => PVR350
/dev/video1 => WinTV PCI FM

```
When I shut down the system now, I have a good chance the get something like this:
```

/dev/video0 => WinTV PCI FM
/dev/video1 => PVR 350

```
This confuses mythbackend wich "forgets" about my tuner cards. Is there something I can do about this? Somewhere I've read about "blacklisting" ivtv. Can someone tell me what this means? 


system data wich might be of interest:

uname -a;
Linux mythtv 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

dmesg | grep ivtv
```

[   25.557761] bttv0: i2c: checking for TDA9875 @ 0xb0... <6>ivtv:  ==================== START INIT IVTV ====================
[   25.811964] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   26.748600] ivtv0: Autodetected Hauppauge card (cx23415 based)
[   27.545923] ivtv0: loaded v4l-cx2341x-enc.fw firmware (4158524000 bytes)
[   27.578895] ivtv0: loaded v4l-cx2341x-dec.fw firmware (4158524008 bytes)
[   27.800358] ivtv0: Encoder revision: 0x02050032
[   27.800363] ivtv0: Recommended firmware version is 0x02060039.
[   27.808365] ivtv0: Decoder revision: 0x02020023
[   27.817270] msp3400 2-0040: MSP4418G-A2 found @ 0x80 (ivtv i2c driver #0)
[   27.834300] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   27.906125] ivtv0: Autodetected Hauppauge WinTV PVR-350
[   27.964900] saa7115 2-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   28.130492] saa7127 2-0044: saa7127 found @ 0x88 (ivtv i2c driver #0)
[   28.411329] ivtv0: Registered device video1 for encoder MPEG (4 MB)
[   28.411696] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   28.412077] ivtv0: Registered device vbi1 for encoder VBI (1 MB)
[   28.412296] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   28.412689] ivtv0: Registered device radio1 for encoder radio
[   28.412858] ivtv0: Registered device video16 for decoder MPEG (1 MB)
[   28.413049] ivtv0: Registered device vbi8 for decoder VBI (1 MB)
[   28.413651] ivtv0: Registered device vbi16 for decoder VOUT
[   28.413814] ivtv0: Registered device video48 for decoder YUV (1 MB)
[   28.471623] ivtv0: loaded v4l-cx2341x-init.mpg firmware (4158524944 bytes)
[   28.671337] ivtv0: Initialized Hauppauge WinTV PVR-350, card #0
[   28.671384] ivtv:  ====================  END INIT IVTV  ====================

```


regards,
Errorsmith

---

### Post by mekis on 2008-03-21
I  had a similar problem with TV Tuner cards in different order after each cold start too and found help here: [http://ubuntuforums.org/archive/index.php/t-542903.html]("http://ubuntuforums.org/archive/index.php/t-542903.html")

The solution that oscarsfriend describes worked for me too using a Hauppauge Nova-T-500, two receivers, and a DVB-S card.

---

### Post by Errorsmith on 2008-03-21
Hi

Thanks for your answer. Unfortunately this didn't help me until now. 

The udev rules are for dvb devices only, my tuner cards are analog ones. As I don't really know about udev and its rules, I'm a bit afraid to modify the files, as the other poster writes:
> However, unless you know what you're doing, you should not modify udev rule files you did not create yourself ... that includes opening one & saving it without making any changes.

Can you give me a hint how to modify the ruleset to apply to my tuners?

regards,
Errorsmith

---

### Post by oscarsfriend on 2008-03-22
> **Errorsmith said:**
> Can you give me a hint how to modify the ruleset to apply to my tuners?

I think the way to go here is not to hack the default udev rules (like I did in the post quoted above - but I've since undone that after changing my set-up) but to create a new one that creates two symlinks to your devices.

You'll have to figure some of this out yourself, so please don't follow what I say exactly, it is meant more to guide you in the right direction.

We need to get some information to distinguish your two devices.  You will need to run the following command to list up the info:
```

udevinfo -a -p $(udevinfo -q path -n /dev/video0 )

```
and again for video1.  The output is mostly in the form:
```

  SOMETEXT=="SOMEVALUE"

```
What we are looking for is something that distinguishes between the two, and doesn't change on rebooting.

Now I'd suggest mapping your two devices to whatever the highest number mythtv allows, and the one below (I will assume 7 and 6 here, but you better check in myth-setup first!).  So you'd have (in addition to /dev/video0 and /dev/video1) /dev/video6 and /dev/video7.

Use "sudo nano" or "sudo gedit" or whatever your favourite text editor is to create a file with the following name (or edit one if it already exists): /etc/udev/rules.d/10-local.rules and add the following lines to it and save it:

```

KERNEL=="video*",[COLOR="Red"]XXX[/COLOR],SYMLINK="video7"
KERNEL=="video*",[COLOR="Red"]YYY[/COLOR],SYMLINK="video6"

```

The XXX and YYY marked above will be your identifying information, given in the form SOMETEXT=="SOMEVALUE" you found above.  If you need more than one lot of information then separate with commas.  You can also use * as a wildcard.

For example: I have two identical nova dvb cards, and I need to create a symlink to the one with the remote attached (otherwise the remote doesn't work on some reboots) -- to do this I use the KERNELS line from the output from udevinfo to identify which PCI port the device is connected to, like this:
```

KERNEL=="event*",[COLOR="Red"]SYSFS{vendor}=="0x14f1",KERNELS=="0000:01:09.*"[/COLOR],SYMLINK="input/irremote"

```

You will have to play about with this yourself to get it working.  Also, don't forget to set mythtv to use /dev/video6 and /dev/video7.

EDIT: You will need to reboot for udev to create your symlinks, or you can probably just restart udev with: sudo /etc/init.d/udev restart

---

### Post by Errorsmith on 2008-03-24
Hi

Thank you for your reply and detailled info on the udev rules. And sorry for my late reply, I was out of town because of the holidays for two days. (Witihin the computer just again freezed during a recording). I'll give it a try tomorrow and report back. 

Just for information: Would it be possible to give the symlinks complete other names like /dev/mpgvideo0 and /dev/bttvideo0. I think it might confuse myth-setup but any other tool should get along with this, shouldnt it?

Greetings,
Errorsmith

---

### Post by KillerKiwi on 2008-03-25
Heres my script that I use to create udev rules

usage

sudo python udev.py /dev/video1 /dev/video/hauppauge_150

that will do what you need

---

### Post by oscarsfriend on 2008-03-25
> **Errorsmith said:**
> Just for information: Would it be possible to give the symlinks complete other names like /dev/mpgvideo0 and /dev/bttvideo0.

I just took a peek in myth-setup and I now see that it is different for analogue tuner cards.  For DVB cards you just specify a number and it looks up the device name - it seems that for analogue cards you can specify the full device name.  So It'd be a good idea to do something like you suggest instead.  You might also want to look at the python script posted by the person above, which looks like it will do the job for you.

---

### Post by Errorsmith on 2008-03-25
Hi again

This worked like a charm. :)
I did as told and created the rules file. After testing, I added some more rules to symlink the vbi and radio devices too. (both have a fm tuner and a vbi decoder). 

For the archives:
my  /etc/udev/rules.d/10-local.rules
now looks like this:

```

# create symlinks for partivular video devices
# Hauppauge PVR350 => /dev/mpg*
KERNEL=="video*",ATTR{name}=="ivtv0 encoder MPEG", ATTRS{vendor}=="0x4444", ATTRS{device}=="0x0803", SYMLINK="mpgvideo0" 
KERNEL=="vbi*",ATTR{name}=="ivtv0 encoder VBI", ATTRS{vendor}=="0x4444", ATTRS{device}=="0x0803",SYMLINK="mpgvbi0"
KERNEL=="radio*",ATTR{name}=="ivtv0 encoder radio", ATTRS{device}=="0x0803", ATTRS{vendor}=="0x4444", SYMLINK="mpgradio0"

# Hauppauge WinTV PCI FM => /dev/btt*
KERNEL=="video*", ATTRS{device}=="0x036e", ATTRS{vendor}=="0x109e", SYMLINK="bttvideo0" 
KERNEL=="vbi*", ATTRS{device}=="0x036e", ATTRS{vendor}=="0x109e", SYMLINK="bttvbi0"
KERNEL=="radio*",  ATTRS{device}=="0x036e", ATTRS{vendor}=="0x109e", SYMLINK="bttradio0"

```

Thank you all very much for this. I found it very annoying to reboot twice or more to get the devices in correct order. ;)

Now I only have to find out why the machine locks up when I record something with the bttv card. Has anyone an idea where I can look?
Things I have done so far:
- Swap the cards around.
- play with IRQ, APIC and ACPI settings in BIOS and the Kernel
- doublecheck temperatures, voltages and other enviroment conditions
- doublechecked and excluded hardware failure (cards are working fine in a windows machine)

I've read something about problems with the kerneldriver for bttv cards but couldn't determine if these issues have been resolved already. Does anybody know something about this?

regards,
Errorsmith

---

### Post by Errorsmith on 2008-03-25
Hi
Thank you very much for this. I saved the script an it seems to works for my system. Nice work. :)

greetings,
Errorsmith

---

### Post by KillerKiwi on 2008-03-25
Glad you found the script useful... by default it dosnt use the device name as I had issues with using the name with one of my cards..

Any body know how to lock down to a pci slot for identical cards?

---

### Post by oscarsfriend on 2008-03-26
> **KillerKiwi said:**
> Any body know how to lock down to a pci slot for identical cards?

I use the KERNELS parameter to identify by pci slot which of my two nova-t dvb has the remote detector plugged in, like this:

```

KERNEL=="event*",SYSFS{vendor}=="0x14f1",[COLOR="Red"]KERNELS=="0000:01:09.*"[/COLOR],SYMLINK="input/irremote"

```

---

