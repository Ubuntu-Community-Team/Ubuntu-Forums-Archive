---
title: "Enable radeonhd drivers"
date: 2010-05-01
forum: Multimedia Software
---

### Post by b0wter on 2010-05-01
I'm using a Thinkpad T400 which has a hybrid graphics card. I've only been using the onboard (intel) graphics card and it works like a charm. But I got myself a new monitor that I want to connect to via DVI which is only possible using the discrete graphics card (ATI HD 3400).

I am now trying to figure out how to use the radeonhd driver (I am currently using the radeon driver but the card seems to always run at full power, whereas the radeonhd driver has a powersave option). At first I thought I'd simply edit the xorg.conf file but that file does no longer exist and I couldnt figure out how to make changes without that file :(
Can anyone please help me?

---

### Post by Yellow Pasque on 2010-05-01
```
sudo apt-get install xserver-xorg-video-radeonhd
```
Now, create the xorg.conf file:
```
gksu gedit /etc/X11/xorg.conf
```
Copy/paste this to use as a template and modify to your preference:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeonhd"
        Option          "ForceLowPowerMode" "true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```
Save. Quit. Log out to restart X server.

---

### Post by karhulitos on 2010-05-05
Finally a clear instruction how to enable radeonhd. My problem is: I want tear free video with hdmi sound.

fglrx does hdmi but tears badly
radeon is silent on hdmi but video is tear free
radeonhd never worked for me

I've tried to look all forums and wiki's that my
```

01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc RV710/730
```
should be supported by radeonhd for me to get tear free video and sound out via hdmi.

But using above instruction I get black screen when lappy boots up (backlight is lit). I have 6gig memory on this Sony Vaio VGN-FW41ZJ. Safe mode tells something about error in parsing xorg.conf with above text in it.

By posting this I just hope some wise people would find the obvious error I'm having ;)
Other than that I've given up on ATI, next PC will have nVidia.

[edit] just noticed above xorg.conf example missing "EndSection". Wonder if that was the parse error. Need to test tomorrow.
[edit2] EndSection was needed but unfortunately result is the same: black screen. No go. Now the safe mode errors changed from parse to some AtomBIOS errors that I couldn't paste here. M96 and radeonhd perhaps not a good idea.

---

### Post by Yellow Pasque on 2010-05-05
Sorry about missing EndSection, fixed. As for getting audio through HDMI while using radeon, you'll probably need kernel 2.6.34. If you don't mind experimenting, use the procedure below. It assumes you're using 32-bit (if you're not, change the two occurrences of 'i386' in the package names to 'amd64').
```
cd ~/
mkdir kerneldebs
cd kerneldebs/
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/linux-headers-2.6.34-020634rc6_2.6.34-020634rc6_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/linux-headers-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/linux-image-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb
sudo dpkg -i linux*
```
Reboot and see if you have HDMI sound.

---

### Post by karhulitos on 2010-05-06
Thanks Temüjin for the tip/info. Wow.. kernel tweaking kind of goes out of my territory.

What would you suggest in below scenario:
- wife uses this same PC
- wife-email-facebook-SLA permits max one night down time or I'm screwed

Kernel experimenting or should I just stick with standard offering? (i.e. is it too dangerous?)

[edit] damn that looks tempting.. what happens to (kernel) updates if I go the experimental path?

---

### Post by b0wter on 2010-05-07
You can also try to add the following to your xorg.conf (device section):

```

        Option "Audio" "true"
        Option "HDMI" "all"

```

[source](https://help.ubuntu.com/community/RadeonHD#HDMI Audio)

---

### Post by karhulitos on 2010-05-07
> **b0wter said:**
> 
```

        Option "Audio" "true"
        Option "HDMI" "all"

```


Yes, that just suggests to use radeonhd which isn't working on my hw assuming Temüjin suggested simple config for radeonhd should be ok.
Tried those xorg.conf settings also on readeon driver but no sound out as expected as no threads told that radeon could do that.

---

### Post by b0wter on 2010-05-08
Sry, my bad. I have the same issue with the radeonhd drivers. Tried loads of different options in xorg.conf but none seemed to work.
I also triedd deleting the radeon driver but that would make autoconf choose a default driver model that supports just about nothing :(

---

### Post by b0wter on 2010-05-21
I'm still struggeling with the installation of the radeonhd drivers as I hope I'll be able to play full HD videos properly with them.
My question is, how do I find out which driver is currently used?

---

### Post by skitheo on 2010-05-23
> **Temüjin said:**
> ```
sudo apt-get install xserver-xorg-video-radeonhd
```Now, create the xorg.conf file:
```
gksu gedit /etc/X11/xorg.conf
```Copy/paste this to use as a template and modify to your preference:
```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "radeonhd"
        Option          "ForceLowPowerMode" "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```Save. Quit. Log out to restart X server.
 

This doesn't seem to work (at least on my machine). Following is what I get after following the above steps and rebooting.

```
lspci -v
<snip>
0a:00.0 VGA compatible controller: ATI Technologies Inc RV530GL [FireGL V3400]
    Subsystem: ATI Technologies Inc Device 3b02
    Flags: bus master, fast devsel, latency 0, IRQ 57
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0500000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at 2000 [size=256]
    [virtual] Expansion ROM at f0520000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Kernel driver in use: radeon
    Kernel modules: radeon

0a:00.1 Display controller: ATI Technologies Inc RV530GL [FireGL V3400 (Secondary)]
    Subsystem: ATI Technologies Inc Device 3b03
    Flags: bus master, fast devsel, latency 0
    Memory at f0510000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Express Endpoint, MSI 00
<snip>

uname -a
Linux ubuntu10 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
```

---

### Post by Sneil on 2010-12-17
Dear all,

The apt-get install xserver-xorg-video-radeonhd is not working for me. It says no install candidate available.

With kind Regards,

[EDIT] Maybe it is easy to give some more information:

Laptop is a thinkpad T60p with a ATI FireGL V5200 and I'm using Ubuntu 10.10.

2D works with On board intel grapichs, 3D just fails.

Thanks in advance

[Edit2] I just ran UT 2003 via command line and found this :

```


Backtrace:
[ 1]  ./Core.so(+0xb778a) [0x30b78a]
[ 2]  [0x4a0400]
Signal: SIGSEGV [segmentation fault]
Aborting.
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  65 (X_PolyLine)
  Serial number of failed request:  19
  Current serial number in output stream:  20
Segmentatiefout

```

It's Dutch, so if you don't understand I will try to translate the Dutch parts ;)

Thanks

---

