---
title: "Enable Wireless greyed out | 10.04 | Packard Bell Etna-GL"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by RowanEmslie on 2012-04-23
Hi there. I have been using 10.04 for about 6 months and had very few problems. Yesterday my wireless stopped detecting automatically. I had a look and saw the 'enable wireless' button is unchecked and greyed out. I tried to edit this in the NetworkManager.state file (from false to true) but was told I didn't have the permission to save the changes - I don't know why this is, I am the only user on this machine.

Needless to say, I have little knowledge or experience of Linux or coding or anything like that.

Following the rules of the '[how to post wireless complaints]("http://ubuntuforums.org/showthread.php?p=6183681")' post...

**lspci gets this result:**

[INDENT]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
[/INDENT]

**lsusb gets this result:**

[INDENT]Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b112 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/INDENT]

[B]iwconfic wlan0 gets:
[/B]
[INDENT]wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
[/INDENT]

**lsmod gets:**

[INDENT]Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203472  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74297  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  290035  2 
drm_kms_helper         29329  1 i915
uvcvideo               57438  0 
videodev               34457  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
drm                   163779  3 i915,drm_kms_helper
ath5k                 121632  0 
mac80211              205434  1 ath5k
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
ath                     7611  1 ath5k
serio_raw               3978  0 
cfg80211              126528  3 ath5k,mac80211,ath
led_class               2864  1 ath5k
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            40033  0 
r8169                  34140  0 
mii                     4381  1 r8169
[/INDENT]

[B]sudo lshw -C network gets:
[/B]
[INDENT]  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:1a:3a:91
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.13 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:2000(size=256) memory:f4010000-f4010fff(prefetchable) memory:f4000000-f400ffff(prefetchable) memory:f4020000-f403ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:17:c4:3f:41:ac
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f4200000-f420ffff
[/INDENT]

**iwlist scan gets:**

[INDENT]lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down
[/INDENT]

**lsb release -d**

[INDENT]Description:	Ubuntu 10.04.4 LTS[/INDENT]

**uname -mr**

[INDENT]2.6.32-41-generic i686
[/INDENT]

**sudo /etc/init.d/networking restart**

[INDENT] * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
[RIGHT][ OK ][/RIGHT]
[/INDENT]

Hope this means anything to anyone - I'm moving to Kenya in a week and really need to get this fixed!

---

### Post by chili555 on 2012-04-23
> *-network [COLOR="Red"]DISABLED[/COLOR]
description: Wireless interface
product: AR5001 Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 0This often but not always means that the physical switch is turned to Off. Is there a switch? Can you find it and switch it? Please post:```
rfkill list all
```Thanks.

---

### Post by RowanEmslie on 2012-04-24
Lo and behold, this morning it is working:

[INDENT]0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no[/INDENT]

I have a button which is basically non functioning. I don't understand why the wireless works sometimes but not at others? As I said, it's worked well for several months before stopping on the weekend.

Do you know what I would have to do when it is hard blocked (as it was yesterday) if 'rfkill unblock all' doesn't work?

---

### Post by chili555 on 2012-04-24
> I have a button which is basically non functioning. How is that? Because the button doesn't change color? In some cases, the button works but the LED doesn't. The next time it's not working, try running:```
rfkill list all
```Press the button and try again:```
rfkill list all
```Is there any improvement?

Laptops usually require a laptop-mode or wmi module to get the unique keys on your particular laptop to be recognized: Fn+f4 or the bluetooth button,for example. Perhaps it didn't load correctly. You might copy a listing of all the loaded modules to a text file:```
lsmod > lsmod.txt
```The next time the wireless is not working, run:```
lsmod
```Compare the output to your text file *lsmod.txt*. Is something missing? If so, load it:```
sudo modprobe some_module
```If that brings your wireless to life, instruct the system to load it on boot automatically:```
sudo su
echo some_module >> /etc/modules
exit
```If in doubt, of course, check with us first.

---

### Post by RowanEmslie on 2012-04-28
Hi there. Once again my wireless has ceased to function. I even bought a wireless adapter as a friend told me it would help (it has not), the link to the one I got is here. It seems to say just plugging it in will make it work... [http://www.ebuyer.com/220220-edimax-wireless-n150-nano-usb-adapter-ew-7811un]("http://www.ebuyer.com/220220-edimax-wireless-n150-nano-usb-adapter-ew-7811un")

Do you know why this adapter wouldn't be working?

Anyway, I tried to do the lsmod > lsmod.txt thing but nothing seemed to happen. Any thoughts? Am I typing it in wrong or something?

My wifi button on/off doesn't make any difference to the rfkill list all.

---

### Post by chili555 on 2012-04-28
Please do:```
rfkill list all > rowan.txt
dmesg >> rowan.txt
lsmod >> rowan.txt
zip rowan.zip rowan.txt
```Look in your home directory and find the file called rowan.zip and attach it to your reply using the paperclip tool at the top of the reply box. We'll get to the bottom of this!

---

### Post by RowanEmslie on 2012-04-30
Ok, here's the file. Weirdly, now that the wireless usb adapter is in, I often (but not always) have my wireless enabled but still no actual connections...

---

### Post by chili555 on 2012-04-30
Frankly,your readings look perfect. I see nothing wrong or even suspicious to work on to fix. I do know that ath5k and the wireless switch have a touchy relationship. When it is not working, please try:```
sudo modprobe -r ath5k
sudo rfkill unblock all
sudo modprobe ath5k
```If it helps, we can tweak one file and make it persistent.

---

### Post by RowanEmslie on 2012-04-30
I did those things and now my wireless is disabled and the enable wireless box is greyed out again! I did it both with the usb wireless adapter in and with it out; same result.

---

### Post by chili555 on 2012-04-30
> with the usb wireless adapter in and with it out;Frankly, you need to decide if we're going to get the internal going or the USB going. I have trouble working on both simultaneously and having you switch gears at will. 

Please decide.

---

### Post by RowanEmslie on 2012-04-30
Fair enough! I'll go with the external one (might as well use it now I've bought it) if that's fine

---

### Post by chili555 on 2012-04-30
First, we're going to blacklist the driver for the internal and not speak of it again.```
sudo su
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf
exit
```Now, insert the USB and run and post:```
lsusb
```Reboot and we'll get the USB going.

---

### Post by RowanEmslie on 2012-04-30
OK great, did the first thing, rebooted and here's the lsusb:

[INDENT]Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 7392:7811  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b112 Chicony Electronics Co., Ltd
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/INDENT]

---

### Post by chili555 on 2012-04-30
> 7392:7811 This device is driven by the tricky rtl8192cu in Ubuntu 12.04 and by nothing at all in 10.04. We could, in order of easiness:

* Return the device and get a known supported device; or
* Install Ubuntu 12.04 in place of 10.04; or
* Use ndiswrapper to install the Windows XP driver files; or
* Download and compile from source code the Realtek 8192CU driver.

What is your choice?

Posts 1-3 here show the compile process: [http://ubuntuforums.org/showthread.php?t=1590873&highlight=7811](http://ubuntuforums.org/showthread.php?t=1590873&highlight=7811)

Here is more information on rtl8192cu: [http://ubuntuforums.org/showthread.php?t=1949810&highlight=7811](http://ubuntuforums.org/showthread.php?t=1949810&highlight=7811)

---

### Post by RowanEmslie on 2012-04-30
I'm moving to Kenya today so 1 is out. I installed 12.04 before only to discover that my wireless adapter wasn't compatible. I suppose this is no longer an issue so that one (as it's the next easiest).

---

### Post by chili555 on 2012-04-30
Good luck in your move; I know moves are difficult. 

You can always try the live CD to see which device works better; both are supported.

---

### Post by RowanEmslie on 2012-04-30
You'd suggest installing 12.04 from CD rather than upgrading? I've back up my files etc. Should I upgrade in steps online instead?

Once I've done that, what will I need to do to get the usb wifi adapter working?

Sorry if I'm being unusually dense. You have been amazingly helpful!

---

### Post by chili555 on 2012-04-30
I would download and burn the CD. You can try it live and see which wireless device works better and install from there. The advantage of the live CD is that you don't have to be stuck if something doesn't work; sound, touchpad, etc.

---

### Post by RowanEmslie on 2012-04-30
I'm currently running the Live CD of 12.04. Wireless is neither enabled (on the drop down menu it is un-ticked and I cannot tick it) nor operational. Please advise. 

In the drop down menu it lists both the internal and external wireless adapters as disabled.

I ran rfkill list all:[INDENT]0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


[/INDENT]

I'd also like to point out that it has not remembered any of my files or downloads. Don't know if that tells you anything more.

---

### Post by chili555 on 2012-04-30
Please do:```
sudo modprobe -r acer-wmi
sudo rfkill unblock all
```Now does it work? If so, I suggest you go ahead and install and we'll remove and blacklist *acer-wmi*.

---

### Post by RowanEmslie on 2012-04-30
It works! You're a genius!

Let's blacklist that acer then

---

### Post by chili555 on 2012-04-30
Did you go ahead and install 12.04? If so, please do:```
sudo su
modprobe -r acer-wmi
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```You should be all set.

---

### Post by RowanEmslie on 2012-05-02
Terrific. I'm in my BnB in Nairobi using the wireless with no more problems. Thanks a lot man!

---

### Post by chili555 on 2012-05-02
Awesome! Glad it's working. Would you please use thread tools at the top and Mark Solved?

---

