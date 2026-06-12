---
title: "Installing Wireless Card Driver"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by mrgoodfox on 2011-10-17
I have a [wireless adapter]("http://www.buffalotech.com/products/wireless/client-adapters/") that  i want to install on my newly installed Linux driver

The driver page doesn't have a [Linux version]("http://www.buffalotech.com/support/downloads/airstation-highpower-n300-compact-usb-20-wireless-adapter-wli-uc-g300hp/"). And I cant find anything in the Software Central.

What should i do?

---

### Post by grahammechanical on 2011-10-17
If you do not mind me saying, you are thinking as a Microsoft Windows user.

Plug in the adapter. Boot up and see if Ubuntu recognises the device. Click the network manager icon and see if it detects any nearby wireless access points. You may need to enable Networking and wireless by clicking them.

With Linux drivers for many devices are built into the OS. You may need to install a driver.

With a cable connection to the router open additional Drivers and authenticate any additional drivers that may be available. They may include a driver for this adapter.

This will do for a start. See how you go. Also check the section of this forum called Networking and wireless. You will find that your problem has already been answered there. May be.

Regards.

P.S. Ubuntu comes with Help documentation. Read that on how to set up a wireless connection and wireless troubleshooting.

---

### Post by mrgoodfox on 2011-10-17
You're right. I am thinking like a windows user :(

I put the card in and booted Ubuntu up but even when i had enabled wireless it wasn't recognizing the USB adapter so i thought maybe there is a driver that i need to download somewhere

Update:

I found [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/801248"). Is it related?

---

### Post by Mark Phelps on 2011-10-17
If you want to research this, then go to the Networking forum, do a search on NDISWrapper, and look for threads that mention the make and model wireless adapter you have.

If you find them, they will probably also have instructions on how to use the NDISWrapper approach to use your MS Windows drivers in Linux.

---

### Post by gandaran on 2011-10-17
> **mrgoodfox said:**
> You're right. I am thinking like a windows user :(

I put the card in and booted Ubuntu up but even when i had enabled wireless it wasn't recognizing the USB adapter so i thought maybe there is a driver that i need to download somewhere

Update:

I found [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/801248"). Is it related?
you may need to install driver or just do some minor fix, what we need to know is the wireless chipset model and brand to find out which driver works
type in terminal paste the output
```
lsusb
```

---

### Post by mrgoodfox on 2011-10-17
It's Buffalo WLI-UC-G300HP Wireless LAN Adapter

The "lsusb" command did pick up the name. The device itself never comes active (powered up) or show any wireless connections though (I've enabled wireless too)

---

### Post by gandaran on 2011-10-17
> **mrgoodfox said:**
> It's Buffalo WLI-UC-G300HP Wireless LAN Adapter

The "lsusb" command did pick up the name. The device itself never comes active (powered up) or show any wireless connections though (I've enabled wireless too)
please we need the lsusb output, I suspect it has the ralink rt2860 chipset, if it is correct it will be easy to make the adapter work.
and paste the output of this command too
```
lsmod
```

---

### Post by mrgoodfox on 2011-10-17
```

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0411:0148 MelCo., Inc. Buffalo WLI-UC-G300HP Wireless LAN Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 17ef:480c Lenovo 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```


```

Module                  Size  Used by
binfmt_misc            17565  1 
sha256_generic         21031  2 
cryptd                 20510  0 
aes_x86_64             17208  272 
aes_generic            38279  1 aes_x86_64
parport_pc             36959  0 
dm_crypt               22993  1 
ppdev                  17113  0 
snd_hda_codec_conexant    57511  1 
snd_hda_intel          33176  2 
arc4                   12529  2 
snd_hda_codec         103768  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
thinkpad_acpi          81587  0 
snd_pcm                96297  2 snd_hda_intel,snd_hda_codec
rt2800usb              18235  0 
snd_seq_midi           13324  0 
rt2800lib              45181  1 rt2800usb
snd_rawmidi            30386  1 snd_seq_midi
crc_ccitt              12667  1 rt2800lib
snd_seq_midi_event     14899  1 snd_seq_midi
rt2x00usb              20330  1 rt2800usb
rt2x00lib              49235  3 rt2800usb,rt2800lib,rt2x00usb
snd_seq                61585  2 snd_seq_midi,snd_seq_midi_event
mac80211              290274  3 rt2800lib,rt2x00usb,rt2x00lib
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               68099  0 
cfg80211              178528  2 rt2x00lib,mac80211
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17042  1 videodev
snd                    67346  14 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,thinkpad_acpi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tpm_tis                18537  0 
tpm                    22267  1 tpm_tis
psmouse                73535  0 
nvram                  14419  1 thinkpad_acpi
tpm_bios               13684  1 tpm
lp                     17789  0 
serio_raw              13166  0 
joydev                 17606  0 
parport                46458  3 parport_pc,ppdev,lp
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
usbhid                 46956  0 
hid                    91020  1 usbhid
i915                  515121  3 
ahci                   25951  4 
drm_kms_helper         42136  1 i915
libahci                26642  1 ahci
drm                   227498  4 i915,drm_kms_helper
e1000e                159096  0 
i2c_algo_bit           13400  1 i915
video                  19438  1 i915


```

---

### Post by gandaran on 2011-10-17
> Device 003: ID 0411:0148
I couldn't get the exact chipset model with this device key and ubuntu failed the correct identification too but in fact it is a ralink chipset as 'lsmod' shows several ralink drivers loaded
> rt2800usb              18235  0 
rt2800lib              45181  1 
rt2x00usb              20330  1 rt2800usb
rt2x00lib              49235  3 rt2800usb,rt2800lib,rt2x00usb
the rt2800usb driver is probably the wrong driver loaded so lets try blacklist the driver, if this doesn't work you can undo it later.
type in terminal
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
add this line at the bottom and save 
```
blacklist rt2800usb
```
now reboot the PC, a different driver should load and work, if still doesn't work paste the output of 'lsmod' again

---

### Post by mrgoodfox on 2011-10-17
I just tried to do that and (for the second time since I've installed Ubuntu) it's not accepting my password. 

It's interesting because the same password is working for all other Administrative actions but it seems like it needs a different password than the main one. Is there a place that i should go to modify that?

Thanks for all the help

---

### Post by gandaran on 2011-10-17
> **mrgoodfox said:**
> I just tried to do that and (for the second time since I've installed Ubuntu) it's not accepting my password. 

It's interesting because the same password is working for all other Administrative actions but it seems like it needs a different password than the main one. Is there a place that i should go to modify that?

Thanks for all the help
sorry cant help you with this but there is only one administrator root password, try 'sudo' instead of 'gksu' maybe from the terminal it'll accept the password.

---

### Post by mrgoodfox on 2011-10-17
'sudo' allowed me to make the change.

After restart the USB adapter still doesnt work and the option to "Enable Wireless" on the OS is gone too.

---

### Post by gandaran on 2011-10-17
> **mrgoodfox said:**
> 'sudo' allowed me to make the change.

After restart the USB adapter still doesnt work and the option to "Enable Wireless" on the OS is gone too.
so which ralink driver was loaded in 'lsmod'? or none?
also try removing and connecting the adapter.

---

### Post by mrgoodfox on 2011-10-17
This is what lsmod shows me

> Module                  Size  Used by
sha256_generic         21031  2 
cryptd                 20510  0 
aes_x86_64             17208  231 
aes_generic            38279  1 aes_x86_64
parport_pc             36959  0 
ppdev                  17113  0 
dm_crypt               22993  1 
binfmt_misc            17565  1 
snd_hda_codec_conexant    57511  1 
snd_hda_intel          33176  2 
thinkpad_acpi          81587  0 
snd_hda_codec         103768  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_seq_midi           13324  0 
joydev                 17606  0 
uvcvideo               68099  0 
snd_pcm                96297  2 snd_hda_intel,snd_hda_codec
snd_rawmidi            30386  1 snd_seq_midi
tpm_tis                18537  0 
videodev               82052  1 uvcvideo
psmouse                73535  0 
v4l2_compat_ioctl32    17042  1 videodev
snd_seq_midi_event     14899  1 snd_seq_midi
serio_raw              13166  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
snd_seq                61585  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67346  14 snd_hda_codec_conexant,snd_hda_intel,thinkpad_acpi,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tpm                    22267  1 tpm_tis
soundcore              12680  1 snd
nvram                  14419  1 thinkpad_acpi
tpm_bios               13684  1 tpm
lp                     17789  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
e1000e                159096  0 
ahci                   25951  2 
libahci                26642  1 ahci
i915                  515121  3 
drm_kms_helper         42136  1 i915
drm                   227498  4 i915,drm_kms_helper
i2c_algo_bit           13400  1 i915
video                  19438  1 i915


---

### Post by mrgoodfox on 2011-10-17
Damn, this is taking too much time... Someone told me to buy Buffalo products because they work great on Linux. I guess I feel for that one.

I also found this [solution]("http://www.computertrouble.co.uk/forum/viewtopic.php?t=4686") somewhere else. Should I do that? It seems way too complicated to get a simple wireless card working.

---

### Post by gandaran on 2011-10-18
> **mrgoodfox said:**
> Damn, this is taking too much time... Someone told me to buy Buffalo products because they work great on Linux. I guess I feel for that one.

I also found this [solution]("http://www.computertrouble.co.uk/forum/viewtopic.php?t=4686") somewhere else. Should I do that? It seems way too complicated to get a simple wireless card working.
about the 'lsmod' command I was hopping the 'rt2870sta' would load instead but in fact no other ralink driver was loaded so before you undo the blacklisting try running this command 
```
sudo modprobe rt2870sta
```
if it doesn't fix the issue then all I can say go the _windows XP driver_ way with ndiswrapper.
but don't use the link you posted as that is for a different Bufallo adapter with broadcom chipset not ralink.
hope you get it working.

---

### Post by gandaran on 2011-10-18
> Someone told me to buy Buffalo products because they work great on Linux. I guess I feel for that one.
they do work but sometimes the problem is the product is so brand new it's not yet supported on Linux

---

### Post by mrgoodfox on 2011-10-18
I did that too and still no change.

Here is another thing, when i clicked on the connection icon on top right of the desktop, in the dropdown, the "Enable Wireless" is checked but two lines above that it says (in light gray) "Wireless is Disabled". 

I thought that might might be my computer's hard wireless button but it wasn't. What is that? Could that be the cause of the problem?

---

### Post by gandaran on 2011-10-18
> **mrgoodfox said:**
> I did that too and still no change.

Here is another thing, when i clicked on the connection icon on top right of the desktop, in the dropdown, the "Enable Wireless" is checked but two lines above that it says (in light gray) "Wireless is Disabled". 

I thought that might might be my computer's hard wireless button but it wasn't. What is that? Could that be the cause of the problem?
the computer has built in wireless card?

---

### Post by mrgoodfox on 2011-10-18
yes. It stopped working a while ago (when I was running Windows 7). I figured the driver had been corrupted. 

this month I installed a brand new Windows 8 OS and Ubuntu dual boot. (I need Windows for my works stuff). but the wireless driver never seemed to fix. so I just continued what I've always done which is using USB wireless card(s)

---

### Post by gandaran on 2011-10-18
> **mrgoodfox said:**
> yes. It stopped working a while ago (when I was running Windows 7). I figured the driver had been corrupted. 

this month I installed a brand new Windows 8 OS and Ubuntu dual boot. (I need Windows for my works stuff). but the wireless driver never seemed to fix. so I just continued what I've always done which is using USB wireless card(s)
lets check the card then
```
lspci
```
some diagnostics
```
rfkill list
```
if anything turns out blocked
```
rfkill unblock all
```

---

### Post by mrgoodfox on 2011-10-18
I ran the first command (couldnt save it and post it here cause no internet on that OS).

I ran the second one (rfkill list) and nothing came up. I still ran the last one and nothing came up (i imagine those were both run in the background).

---

### Post by mrgoodfox on 2011-10-18
Here is the result of the "lspci" command

> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)


---

### Post by gandaran on 2011-10-19
> **mrgoodfox said:**
> Here is the result of the "lspci" command
no wireless card was detected (networking), try checking in BIOS if the card is disabled or just try reset BIOS to default settings and if possible also check if the card is properly seated, another possibility could be the card is damaged.

---

### Post by howefield on 2011-10-19
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by mrgoodfox on 2011-10-19
I checked in BIOS and everything seemed Enabled.

How do i check whether the card is properly seated? Open the hardware?

I actually do suspect that the wireless card is toasted. So I might be better off focusing on getting one of the wireless adapters working.

---

### Post by mrgoodfox on 2011-10-19
I just got off the phone with [Buffalo Tech]("http://www.buffalotech.com/products/wireless/client-adapters/airstation-highpower-n300-compact-usb-20-wireless-adapter-wli-uc-g300hp/") people and they said that Linux is not a supported operating system at all for their products.

---

### Post by praseodym on 2011-10-19
Please show the outputs of

```
pccardctl info
lsusb
```

maybe its an internal USB-device or a pcmcia. See here:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#By_Manufacturer](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#By_Manufacturer)

---

### Post by mrgoodfox on 2011-10-19
The 'pccardctl info' command didn't give any results but here is the result of the lsusb:

> Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0411:0148 MelCo., Inc. Buffalo WLI-UC-G300HP Wireless LAN Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 17ef:480c Lenovo 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by praseodym on 2011-10-19
Try the ndiswrapper solution from here:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBuffalo#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBuffalo#USB)

the links at the bottom right

---

### Post by mrgoodfox on 2011-10-19
Thanks, i think this will take a while :(

i downloaded the first [package]("http://packages.ubuntu.com/natty/misc/ndiswrapper-common") here, extracted it into the /Downloads/ folder and put it in /ndiswrapper-common/ folder and then ran the command below (both while in /Downloads/ directory and once in /ndiswrapper-common/ directory.

> sudo dpkg -i ndiswrapper-common_*.deb

But its not working. I'm getting the following mssage.
> dpkg: error processing ndiswrapper-common_*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ndiswrapper-common_*.deb


---

### Post by praseodym on 2011-10-19
Here is ndiswrapper-utils-1.9:

[http://packages.ubuntu.com/natty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/natty/misc/ndiswrapper-utils-1.9)

Take care downloading 32 or 64 bit, whatever you need.

Ndisgtk:

[http://packages.ubuntu.com/natty/misc/ndisgtk](http://packages.ubuntu.com/natty/misc/ndisgtk)

the same here. Install all three _together_ with:

```
sudo dpkg -i ~/Downloads/*.deb
```

---

### Post by mrgoodfox on 2011-10-19
I keep getting the same error:

> 
dpkg: error processing /home/curus/Downloads/*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/cyrus/Downloads/*.deb



This is the command i ran

> 
cyrus@SA:~$ sudo dpkg -i ~/Downloads/*.deb


Am i entering the commands correctly?

---

### Post by praseodym on 2011-10-19
Just to be sure. Open a new Terminal with CTRL+ALT+T and type:

```
cd Downloads/
sudo dpkg -i *.deb
```
You have all three .deb files there?

---

### Post by mrgoodfox on 2011-10-19
Actually I dont think there are any .deb files in /Downloads/

I'm downloading the .orig.tar.gz version. Is that right? or should i be downloading the .debian one? what's the difference?

(thanks for the help)

---

### Post by praseodym on 2011-10-19
No,

click on the 2 links I posted above, scroll down and click on either "i386" for 32bit or "amd64" for 64bit, depending on your system and then on one of the mirror links. Then this one:

[http://packages.ubuntu.com/natty/misc/ndiswrapper-common](http://packages.ubuntu.com/natty/misc/ndiswrapper-common)

click on "all" and one of the mirrors.

---

### Post by mrgoodfox on 2011-10-19
That worked. 

I have another issue (related an unrelated). When I try to run some of the software on the OS through the "Software Manager" (Top left of desktop), and it required password, it doesn't accept my password. The password always works in the terminal though. I have indeed checked and double checked the entered password 100 times. Do you know what would cause this or perhaps a setting i had to set from beginning?

It seems like its not accepting my password as a root but my user is an Admin with all privileges, so i dont know whats going on

---

### Post by mrgoodfox on 2011-10-20
The reason I say that is because i can't open the Network Drivers application through the application terminal because of that password issue

---

### Post by gandaran on 2011-10-20
> **praseodym said:**
> Here is ndiswrapper-utils-1.9:

[http://packages.ubuntu.com/natty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/natty/misc/ndiswrapper-utils-1.9)

Take care downloading 32 or 64 bit, whatever you need.

Ndisgtk:

[http://packages.ubuntu.com/natty/misc/ndisgtk](http://packages.ubuntu.com/natty/misc/ndisgtk)

the same here. Install all three _together_ with:

```
sudo dpkg -i ~/Downloads/*.deb
```
hi
why download these packages when they can be installed from software center
```
sudo apt-get install ndisgtk 
```
ndisgtk also pulls and install the other two dependencies

---

### Post by mrgoodfox on 2011-10-20
well, they are already both installed but i can't open the ndisgtk from application manager now. It's not accepting my user password as if it's asking for a different level of user (Root). 

Any idea why?

---

### Post by praseodym on 2011-10-20
If you are the user set up at the installation you already have the "root"-flag. Just type in _your_ password

---

### Post by gandaran on 2011-10-20
> **mrgoodfox said:**
> well, they are already both installed but i can't open the ndisgtk from application manager now. It's not accepting my user password as if it's asking for a different level of user (Root). 

Any idea why?
no, but I have seen this same problem on some threads, if I remember correctly gksu as to be in the sudo group or something like that, try searching for the fix.
anyway try opening ndisgtk from terminal
```
sudo ndisgtk
```

---

### Post by mrgoodfox on 2011-10-21
Thanks, I can't find my wireless adapter in this list. Do I just use the only Buffalo Tech driver that is there or do i look to find one with exact Chipset ID as mine (0411-0148)

Also, there is an Ubuntu update. Should i upgrade first?

---

### Post by praseodym on 2011-10-21
Try the one named there, and maybe search on the Buffalo homepage for a XP driver

---

### Post by mrgoodfox on 2011-10-28
I finally found the solution.

When typing "*rfkill list*", I was getting the following results:

```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: ye

```

Which apparently they both should be set to "No". So my wireless was really disabled and not working and it had nothing to do with the wireless card.

I had to type the following command to enable it and everything was working.

```

rfkill unblock wifi

```


Now that being said, enabling the wireless allowed me to use one of my wireless USB adapters. My Buffalo USB adapter is still not working. So I'll continue to try to use the Network Driver tool to install the driver and get that to work too. 

**Thanks **for all the help with this issue.

---

