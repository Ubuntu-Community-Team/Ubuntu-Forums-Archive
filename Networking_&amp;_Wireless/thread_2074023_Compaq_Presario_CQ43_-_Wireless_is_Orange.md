---
title: "Compaq Presario CQ43 - Wireless is Orange"
date: 2012-10-20
forum: Networking &amp; Wireless
---

### Post by FangLargo on 2012-10-20
Hello!

I have recently installed Lubuntu on my Presario CQ43, and I noticed that wireless light is orange. Unfortunately, I am a complete newby at Linux, and I have absolutely no idea where to start. I have searched endlessly on Google, and every link has been either a dead end or an endless loop for me.

When I say I am a newb, I mean it. I don't even know how to install packages the correct way. Please speak slowly and softly to me.

Thank you!

---

### Post by SMOKE14 on 2012-10-20
What do you mean by the light is orange? Can you not connect? What version do you have, there is a lot of models.

---

### Post by FangLargo on 2012-10-20
Well presumably, when the wireless light is orange, it means that the operating system isn't using the wireless card/adapter/whatever it is. The light is on the keyboard, and how if it works, it should go white.

And I'm not sure what you mean by "version" and "model". My laptop is a Compaq CQ43-310AU. I'm less sure about my wireless card, and I don't know how to check.

Thanks.

---

### Post by SMOKE14 on 2012-10-20
Okay, -310AU is what I needed. Wasn't in your OP. Let me do a little research.

---

### Post by SMOKE14 on 2012-10-20
[https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)

---

### Post by FangLargo on 2012-10-21
Oh, gosh. Now it freezes at that splash screen with the five dots. I'm sorry SMOKE14, but I can't even check if your link works...

I know this isn't the right place to put it, but the problem's out there.

---

### Post by SMOKE14 on 2012-10-21
Highlight your Ubuntu in grub, and type "e" without the quotes, and highlight the kernel line, remove all options, and type ```
vga=771 init=/bin/sh  
```
Then press enter, then "b" without the quotes to boot.

---

### Post by varunendra on 2012-10-21
First off, Welcome to the forums FangLargo :)

And this is the perfect place for asking the wireless question. As for the booting problem, it is okay to put here as long as it doesn't move the focus of the thread to graphics troubleshooting or other booting related issues.

> **SMOKE14 said:**
> Highlight your Ubuntu in grub, and type "e" without the quotes, and highlight the kernel line, remove all options, and type ```
vga=771 init=/bin/sh  
```
Then press enter, then "b" without the quotes to boot.

I'm not sure about above but if it is intended to let the OP boot into safe graphics mode, then the recommended way to do that is simply choose **failsafeX** option in the Recovery menu of grub screen (which, if doesn't show up by default, can be brought up by press and holding 'Shift' key at boot time).

Alternately, you can manually edit the kernel boot line (by pressing "e" at grub screen as smoke suggested above) and add 'nomodeset' (without quotes) option after the line that ends with "quite splash". Then press Ctrl+X to boot. ([This and other boot options in detail]("http://ubuntuforums.org/showthread.php?t=1613132"))

Once you are able to boot into your Ubuntu, please run the following command to download & run a script (courtesy - dave, wildman and others) that will create a summary of your wireless and related configuration (just copy-paste it in a terminal):
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will generate a file named "netinfo.txt" in your home directory. Copy paste its contents here (click on **#** at the top of edit box while writing new post, then paste the contents of the file in-between the generated 'code' tags).

I hope I didn't give you too much trouble :)

---

### Post by SMOKE14 on 2012-10-21
> **varunendra said:**
> *Snip*
Yep, that was my intention. And I just got served :p

---

### Post by FangLargo on 2012-10-21
> **SMOKE14 said:**
> Highlight your Ubuntu in grub, and type "e" without the quotes, and highlight the kernel line, remove all options, and type ```
vga=771 init=/bin/sh  
```Then press enter, then "b" without the quotes to boot.

I assume the kernal line is the one that starts with "Linux" right? I'll have a go. 

As for that script, I'll get to it as soon as I get this mess sorted. 

Thanks everyone!

By the way, there were signs that although the wireless wouldn't work on boot, it seemed to work fine during the install. Is that weird?

---

### Post by FangLargo on 2012-10-21
Here is that text:

```

*************** info trace ****************



**** uname -a ****


Linux ubuntu 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:3577]
    Kernel driver in use: r8169


**** lsusb ****


Bus 002 Device 002: ID 0c45:6321 Microdia 
Bus 003 Device 002: ID 04f3:0230 Elan Microelectronics Corp. 3D Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****




**** rfkill ****




**** lsmod ****


Module                  Size  Used by
vesafb                 13797  1 
joydev                 17457  0 
kvm                   414070  0 
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_codec_realtek    77876  1 
snd_hda_intel          33491  3 
snd_hda_codec         134212  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
microcode              22803  0 
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                95552  0 
serio_raw              13215  0 
snd                    78734  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k10temp                13126  0 
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
rts_pstor             433804  0 
sp5100_tco             13697  0 
i2c_piix4              13167  0 
rfcomm                 46619  0 
video                  19335  0 
bnep                   18140  2 
mac_hid                13205  0 
bluetooth             209199  10 rfcomm,bnep
parport_pc             32688  0 
ppdev                  17073  0 
wmi                    19070  1 hp_wmi
binfmt_misc            17500  1 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
r8169                  61650  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1




**** NetworkManager.state ****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search home


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[    0.000000] DMI: Hewlett-Packard Presario CQ43 Notebook PC       /3577, BIOS F.43 12/13/2011
[   21.592437] wmi: Mapper loaded


**************** done ********************


```

At least I can use this with my wires now...

---

### Post by Starcruiser322 on 2012-10-21
I had the same problem with my Compaq CQ62, and it turned out that there were several factors at play:
1. The default drivers do not work. We have weird, old wireless cards, I guess.
2. Once you find drivers that do work, such as in a ppa, they do not work with the 3.X kernel, found in ubuntu since 11.10.
If, after more suggestions and failures, you still cannot enable the wireless or the wireless crashes the kernel when connecting to WPA, then your best bet is to, on your older laptop, use an older version of linux, such as 11.04, or even 10.04, and find working drivers.
I would link you to the proper drivers, but according to HP you could have one of 4 wireless cards???
If you open the cover on the bottom of the computer over the wireless card you can see the model on the card. It should start with "Atheros", "Realtek", "Ralink", or "BroadCom". I can point you in the right direction if you post the card model.

---

### Post by varunendra on 2012-10-21
I don't think a driver issue has come into scene yet.

@FangLargo,
There is no trace of any wireless interface detection in your output, which means your wireless adapter is 'disabled' or powered off (either from a physical switch, or from BIOS). From the [wireless support page]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01884605&tmp_task=useCategory&cc=us&dlc=en&lc=en&product=5194540#N71") for your model (under "Setup for the first time" section)-
> **To turn on the wireless device, simply move the switch to the On position**. The power switch for the wireless LAN device, and the Bluetooth device (if equipped), is located on the side of the case or above the keyboard depending on the model. On some computers, the switch is actually a touch point on the panel above the keyboard.
For most computers, there is an LED light that glows blue when the wireless device is turned on and enabled, and **glows orange when off or disabled**. Some newer models use different a different color scheme.

Accordingly, please make sure your physical switch is turned 'On'. Look into your user manual if not sure where it is and how to use it.

If it is already powered on from the switch, please go into BIOS and make sure it is enabled there.

---

### Post by Starcruiser322 on 2012-10-21
If the switch was just off, it would at least show up in lspci and ifconfig output, and our BIOS (I have the same) does not have much level of customization, and has no wireless or other interface config.

---

### Post by FangLargo on 2012-10-21
Well what would happen if I can't turn the switch on? Off to the BIOS then I guess... 

The button just won't react, and it stays stubbornly orange...

---

### Post by varunendra on 2012-10-21
> **FangLargo said:**
> Well what would happen if I can't turn the switch on? Off to the BIOS then I guess...
yep!

Please tell us whether it is a physically movable switch, a touch-point or something else. Check the BIOS anyway. Also, it seems your laptop had win7 pre-installed. If so, have you checked the switch there? You may try to turn it on from win7, leave it on > restart > try in Ubuntu.

---

### Post by varunendra on 2012-10-21
@Starcruiser,
Sorry, I missed your post.
> **Starcruiser322 said:**
> If the switch was just off, it would at least show up in lspci and ifconfig output..
NOT if the adapter can't receive power (truly powered-off). Consider it like an external device which is connected but 'powered-off'.

---

### Post by FangLargo on 2012-10-21
Annoyingly, it's not a switch per se. It's doubled up with F12, and even with Win7, it doesn't really come on. The only way I can do that is by hard resetting, then spamming F12 while Win7 boots. Then it's almost a 50:50 chance that it might come on.

What I'm curious about now is why the light was white when Ubuntu was installing, but it came orange after the reboot...

Oh well, let me have a hard reset.

---

### Post by Starcruiser322 on 2012-10-21
> **FangLargo said:**
> It's doubled up with F12, and even with Win7, it doesn't really come on.
There is a button at the bottom left of the keyboard that says "fn", short for function. Did you try pressing and holding that, then pressing F12?

---

### Post by wildmanne39 on 2012-10-21
Hi, from the looks of the output your card my being failing.

You can go into the bios and see if it is turned off, if not then you have a failed card because even if it is off by the switch it would show up with the commands I put in that script.

You can also turn off your system and remove the battery for 30 minutes and see if that helps sometimes it does.
Thanks

---

### Post by pqwoerituytrueiwoq on 2012-10-21
i have a CQ60
it light blinks between its 2 colors when i use it, if i click it it turn my wifi off and getting it to turn back on can be annoying
as a result of this i never push that button

you may need to push it once and reboot or something

---

### Post by Starcruiser322 on 2012-10-21
If you had Windows installed on the laptop before, did the wireless work then? That could narrow it down a bit (like the failed card suggestion - unlikely, but not impossible).

Or you could save some trouble and listen to the person who has a similar laptop, went through 3 cards (1 USB), and finally decided that 11.10+ doesn't like relatively old Compaq laptops.

@pq
Sorry, you posted while I was typing. I don't push the button EVER either, it screws everything up.

---

### Post by FangLargo on 2012-10-22
I haven't got my Ubuntu here, so I can't say anything now, sorry.

But just off topic, I always seem to lose my wireless whenever I close the lid. Does that happen to anyone? And occasionally, upon reboot to Windows, I find that I have to hammer at the wireless button during boot for Wifi to work again.

Is this normal? Especially the part about the lid?

Thanks. I'll get back, ASAP.

---

### Post by varunendra on 2012-10-22
Can't comment on the physical switches except that it is not uncommon to find them irritating.

As for the part about 'closing lid', the default behaviour of Ubuntu, IIRC, is to go to 'sleep' state when that happens. Now there are some drivers which fail to comeback properly after waking up. Of course that's a bug in them. A workaround for such identified problems is to unload the drivers before going to sleep, then load them back after waking up. This can be automated by adding a relevant script in /etc/pm/sleep.d directory.

Alternatively you can just change the behaviour of lid-closing event in 'System-settings > Power' settings so it doesn't go to sleep (suspend) when that happens.

---

### Post by FangLargo on 2012-10-22
From what I can see, the Wireless working in Ubuntu is independent from that of Windows. I can make it work in Windows, and it might not work when rebooting into Ubuntu, and vice versa. 

Also, I once launched System Testing, and until I shut down, it worked! Hurrah!

And finally, I found out what brand the thingy is. Ralink RT5390 802.11 b/g/n

Thanks guys.

---

