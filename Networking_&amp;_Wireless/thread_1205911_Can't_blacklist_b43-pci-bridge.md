---
title: "Can't blacklist b43-pci-bridge"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by Johan Dahlbäck on 2009-07-06
I have been trying for a few hours to get my wireless BCM4318 card to work in Ubuntu, but I'm stuck at the fact that I can't get the native driver to be blacklisted. The driver is b43-pci-bridge and no matter what I try it still claims my card, so I can't use ndiswrapper.

---

### Post by imbjr on 2009-07-06
> **Johan Dahlbäck said:**
> I have been trying for a few hours to get my wireless BCM4318 card to work in Ubuntu, but I'm stuck at the fact that I can't get the native driver to be blacklisted. The driver is b43-pci-bridge and no matter what I try it still claims my card, so I can't use ndiswrapper.

I believe you need to add b43-pci-bridge to your /etc/modprobe.d/blacklist.conf file.

There's a way to get this to engage without rebooting, but I did not know what that is, so a reboot after editing the file will be required.

---

### Post by kevdog on 2009-07-06
Can you list lsmod?

I think the correct name of the driver for the blacklist file is just b43!

---

### Post by Sankou on 2009-07-06
Add both b43 and b43-pci-bridge to blacklist.conf to be sure. Then run

sudo update-initramfs -k all -u

then reboot

---

### Post by Crafty Kisses on 2009-07-07
Post the results of:
```
lsmod | grep b43
```

---

### Post by Johan Dahlbäck on 2009-07-07
```

lsmod | grep b43

```returns

```
b43                   131484  0
mac80211              217208  1 b43
led_class              12036  1 b43
input_polldev          11912  1 b43
ssb                    41220  2 b43,b44
``````
/etc/modprobe.d/blacklist
```contains

```
blacklist b43-pci-bridge
blacklist b43
```No luck.

---

### Post by t0mppa on 2009-07-08
This is actually a fairly common problem, happens with other wireless drivers too, when using b44 as the wired driver. ssb is the module name for the b43-pci-bridge. So, you'd have to blacklist that one to get rid of it. Only the problem is that the b44 driver that's handling your wired card needs the ssb module to work properly.

What happens is that b44 loads up and then the ssb is loaded too and since b44 tends to get loaded before the wireless drivers, the ssb just hogs up the wireless too as it is unclaimed at the time. And when your wireless driver gets loaded, the wireless is already associated with a driver, so the OS thinks everything is working fine already and doesn't do anything. A bit of a design flaw to have the same module capable of handling both interfaces, since it leads to trouble like this.

The workaround for this is running the following commands:```
sudo modprobe -r b43 b44 ssb 
sudo modprobe ndiswrapper
sudo modprobe b44 ssb
```

What that does is simply unloads all the b4* stuff first, then loads up ndiswrapper and then loads the b44 & ssb for your wired connection again. That way ndiswrapper gets loaded before ssb and should get associated with the wireless interface.

Give it a shot and if it works, you can just add the commands to your /etc/rc.local file before the *exit 0* line, so they automatically get run during bootup.

---

### Post by Johan Dahlbäck on 2009-07-09
One step forward. Now the card is unclaimed, but ndiswrapper won't take it when i load the module. So when b44 and ssb are loaded again we're back to square one.

Is there something a I should check with ndiswrapper?

---

### Post by t0mppa on 2009-07-09
Is ndiswrapper already loaded? Try removing it too first by adding it on the *modprobe -r* command and then reloading it. It will only get associated when the module actually gets loaded, but trying to load it, when it's already up and running won't do any good.

---

### Post by Crafty Kisses on 2009-07-10
Try the following, open up your blacklist configuration file and add the following to the bottom of the blacklist file:
```
blacklist b43
blacklist ssb
```
From what I recall **ssb** is using the wireless device and that's why ndiswrapper is not seeing the wireless device. You need to edit this as root:
```
/etc/modules
```
You need to add the following to the end of this list:
```
ndiswrapper
```
Then you can try rebooting, and see if that solves the issue.

---

### Post by Johan Dahlbäck on 2009-07-10
I tried to unload and reload ndiswrapper when the card was unclaimed, but it still does not work.

---

### Post by t0mppa on 2009-07-10
@Johan: That's odd, do you have ndiswrapper all set up with a driver loaded and ready to go?

@Codename: I don't think that simply blacklisting ssb will work, since b44 will still load it up as a dependency. And even if he did manage to take it down, his wired connection wouldn't work without it, unless some other driver than b44 is used.

---

### Post by Johan Dahlbäck on 2009-07-12
I think ndiswrapper is set up correctly. ```
ndiswrapper -l
``` gives ```
bcmwl5a : driver installed
    device (14E4:4318) present (alternate driver: ssb)
```

---

### Post by kevdog on 2009-07-12
Please list lshw -C network along with lsmod

---

### Post by Johan Dahlbäck on 2009-07-13
lshw -C network

```
*-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:8c:6e:6f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=213.112.199.93 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4a:7b:b0:f2:c2:33
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```lsmod:

```
Module                  Size  Used by
b44                    35984  0 
ssb                    41220  1 b44
mii                    13312  1 b44
ndiswrapper           193436  0 
i915                   65668  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
iTCO_wdt               19108  0 
snd_seq_dummy          10756  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
psmouse                61972  0 
intel_agp              34108  1 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
dcdbas                 15264  0 
pcspkr                 10496  0 
serio_raw              13316  0 
agpgart                42696  3 drm,intel_agp
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  25360  0 
output                 11008  1 video
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
usbhid                 42336  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

---

### Post by kevdog on 2009-07-13
you might be having problems related to this thread.

Take a look:

[http://ubuntuforums.org/showthread.php?t=1188702](http://ubuntuforums.org/showthread.php?t=1188702)

---

### Post by Johan Dahlbäck on 2009-07-13
At last I found out that i was using the wrong driver. Strange that ndiswrapper never complained about it.

So now the card works but i can't connect to the network and there seems to be options missing. I use WPA-Personal, AES. The only option I have is WPA & WPA2 Personal plus the password. And that doesn't work. Any suggestions?

---

