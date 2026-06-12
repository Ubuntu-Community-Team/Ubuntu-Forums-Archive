---
title: "Issue with ASUS N13 WiFi Adapter"
date: 2012-04-26
forum: Networking &amp; Wireless
---

### Post by Dietrpro1123 on 2012-04-26
Hello,

I've been working on installing an ASUS USB N13 wireless adapter.  I'm running Ubuntu Server 11.10. I followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=1930616") and it seems like I've successfully installed the drivers, but the adapter is still not working.

I tried this:

```
lee@HomeServer:~$ dmesg | grep rtl
[   10.350031] usbcore: registered new interface driver rtl8192cu
[   10.832194] Error: Driver 'rtl8192cu' is already registered, aborting...
[  712.737663] Error: Driver 'rtl8192cu' is already registered, aborting...
```

Not sure if that has anything to do with anything.  

Any assistance would be greatly appreciated!

---

### Post by chili555 on 2012-05-03
Let's have a look at:```
lsusb
dmesg | grep -e 8192 -e wlan
iwconfig
```Thanks.

---

### Post by Dietrpro1123 on 2012-05-03
Thanks for taking a look at this for me!

lsusb:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0b05:17ab ASUSTek Computer, Inc. 
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver

```

dmesg...:

```
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.172784] PM: Registering ACPI NVS region at 1fe70000 (8192 bytes)
[    0.456376] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.456392] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[   10.350031] usbcore: registered new interface driver rtl8192cu
[   10.832194] Error: Driver 'rtl8192cu' is already registered, aborting...
[  712.737663] Error: Driver 'rtl8192cu' is already registered, aborting...


```

iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.


```

---

### Post by chili555 on 2012-05-03
> [   10.832194] Error: Driver 'rtl8192cu' is already registered, aborting...
[  712.737663] Error: Driver 'rtl8192cu' is already registered, aborting...Very interesting. Please reboot so we have a clean slate and post:```
lsmod

```Thanks.

---

### Post by Dietrpro1123 on 2012-05-03
RTM'd

lsmod:

```
Module                  Size  Used by
snd_ca0106             39311  0 
snd_rawmidi            25241  1 snd_ca0106
snd_seq_device         14172  1 snd_rawmidi
snd_ac97_codec        106082  1 snd_ca0106
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_ca0106,snd_ac97_codec
snd_timer              28932  1 snd_pcm
snd                    55902  6 snd_ca0106,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm,snd_timer
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_ca0106,snd_pcm
i915                  509594  1 
drm_kms_helper         32889  1 i915
drm                   196290  2 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
shpchp                 32356  0 
video                  19069  1 i915
joydev                 17393  0 
dcdbas                 14098  0 
ppdev                  12849  0 
parport_pc             32114  1 
rtl8192cu              97651  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95614  1 rtl8192cu
mac80211              393421  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              172427  2 rtlwifi,mac80211
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
e100                   36289  0 
floppy                 60310  0 

```

---

### Post by chili555 on 2012-05-04
Hmmm, that looks remarkably perfect. Let's dig deeper. May we see:```
cat /etc/modules
cat /etc/modprobe.d/blacklist.conf
ls /etc/modprobe.d
modinfo rtl8192cu | head -n4
```I love a mystery!

---

### Post by Dietrpro1123 on 2012-05-04
Yeah, that sounds like me.  I tend to find new and interesting ways to break things...

cat /etc/modules:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtl8192cu

```

cat /etc/modprobe.d/blacklist.conf:
```

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

```

ls /etc/modprobe.d:
```

blacklist-ath_pci.conf   blacklist-framebuffer.conf
blacklist.conf           blacklist-rare-network.conf
blacklist-firewire.conf  blacklist-watchdog.conf

```

modinfo rtl8192cu | head -n4:
```
filename:       /lib/modules/3.0.0-19-generic-pae/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL

```

Thanks for taking a look at all this for me!

---

### Post by chili555 on 2012-05-04
If the device is listed in the aliases for your driver, there should be no need to explicitly load the driver in /etc/modules. Unfortunately, 10.10 is one version I no longer have in my herd, so you'll need to check for us:```
modinfo rtl8192cu | grep 17AB
```We get the 17AB from your usb.id:> Bus 001 Device 004: ID 0b05:[COLOR="Red"]17ab[/COLOR] ASUSTek Computer, Inc.If the command comes up blank, your device is not claimed; we can fix it pretty easily.

If it is listed, we'll need to look deeper for answers.

---

### Post by Dietrpro1123 on 2012-05-04
Looks like we might have a winner!  That command returns no response.  Let me know what I need to do to get the device claimed.

---

### Post by chili555 on 2012-05-04
First, I saw a reference to blacklist in the instructions you referenced. Please check:```
sudo gedit /etc/modprobe.d/blacklist.conf
```If any reference to rtl8192cu is in there, delete it. Proofread, save and close gedit. Do the same here:```
sudo gedit /etc/modules
```

Now let's try the quick, easy way before we try the hard, messy way.```
sudo gedit /etc/rc.local
```Right above exit 0 add these two lines:```
modprobe rtl8192cu
echo "0b05 17ab" > /sys/bus/usb/drivers/rtl8192cu/new_id
```Proofread carefully, save and close gedit. Cross your fingers and toes and reboot.

Dare I say it? Any wireless action??

---

### Post by Dietrpro1123 on 2012-05-04
Ugh,

```
lee@HomeServer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

I forgot to cross my toes.  Looks like you're going to have to tell me about the hard way.

Quick question before we do that though.  I don't really have anything of values on this server yet.  Do you think I would be better off starting with a clean install of version 12.04 and seeing if I have any more luck that way?

---

### Post by chili555 on 2012-05-04
> Do you think I would be better off starting with a clean install of version 12.04 and seeing if I have any more luck that way?Here is my thought:```
$ modinfo rtl8192cu | grep -e modules -e 17AB
filename:       /lib/modules/[COLOR="Red"]3.2.0-24[/COLOR]-generic-pae/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
alias:          usb:v[COLOR="Red"]0B05[/COLOR]p[COLOR="Red"]17AB[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```However, rtl8192cu is known to be twitchy and the installation you did is one of the suggested fixes.

[http://ubuntuforums.org/showthread.php?t=1949810&highlight=8192cu](http://ubuntuforums.org/showthread.php?t=1949810&highlight=8192cu)

Maybe we can see what happened:```
dmesg | grep 8192
lsmod | grep 8192
cat /sys/bus/usb/drivers/rtl8192cu/new_id
```

---

### Post by Dietrpro1123 on 2012-05-05
Hmmm...When I enter the same command, I don't get the alias line:

```
lee@HomeServer:~$ modinfo rtl8192cu | grep -e modules -e 17AB
filename:       /lib/modules/3.0.0-19-generic-pae/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko

```

dmesg | grep 8192
```
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.168781] PM: Registering ACPI NVS region at 1fe70000 (8192 bytes)
[    0.452472] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.452487] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[   11.003819] 8192cu: disagrees about version of symbol module_layout
[   13.293410] usbcore: registered new interface driver rtl8192cu
[   13.294269] Modules linked in: rtl8192cu rtl8192c_common rtlwifi mac80211 cfg80211 ppdev dcdbas snd_ca0106 snd_rawmidi snd_seq_device snd_ac97_codec joydev ac97_bus snd_pcm snd_timer snd soundcore snd_page_alloc i915 parport_pc shpchp drm_kms_helper drm i2c_algo_bit lp parport video usbhid hid e100 floppy

```

lsmod | grep 8192
```
rtl8192cu              97651  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95614  1 rtl8192cu
mac80211              393421  3 rtl8192cu,rtl8192c_common,rtlwifi

```

cat /sys/bus/usb/drivers/rtl8192cu/new_id
```
umm....
```

Every time I try to run that last one it tells my "permission denied".  I tried putting "sudo" in front of it, and also running it from root with no luck.  Pardon my newbishness.  Any ideas?

---

### Post by chili555 on 2012-05-05
> 3.0.0-19-generic-paeWere you going to install 12.04? I believe that kernel is 11.10.> Every time I try to run that last one it tells my "permission denied". I tried putting "sudo" in front of it, and also running it from root with no luck.Me, too. I naively assumed what we echoed, we could read; evidently it's a bit more complicated.> 8192cu: disagrees about version of symbol module_layoutDoesn't sound at all hopeful.> ```
sudo gedit /etc/rc.local
```

Right above exit 0 add these two lines:

```
modprobe rtl8192cu
echo "0b05 17ab" > /sys/bus/usb/drivers/rtl8192cu/new_id
```

I've actually seen it two ways, the perhaps more prevalent is:```
echo 0b05 17ab > /sys/bus/usb/drivers/rtl8192cu/new_id
```That is, without quotes. Would you please change /etc/rc.local to remove the quotes, reboot and let us see:```
dmesg | grep 8192
iwconfig
```

So are you trying to install 12.04 or at least try the live CD? Or should we begin the hard, messy way, as if it hasn't been messy so far!!

---

### Post by Dietrpro1123 on 2012-05-06
Well, quotes or no quotes didn't seem to make a difference:

```
lee@HomeServer:~$ dmesg | grep 8192
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.168780] PM: Registering ACPI NVS region at 1fe70000 (8192 bytes)
[    0.452420] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.452435] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[   10.504143] 8192cu: disagrees about version of symbol module_layout
[   13.120935] usbcore: registered new interface driver rtl8192cu
[   13.121828] Modules linked in: rtl8192cu rtl8192c_common rtlwifi mac80211 cfg80211 ppdev dcdbas snd_ca0106 snd_rawmidi snd_seq_device snd_ac97_codec ac97_bus snd_pcm snd_timer snd soundcore joydev snd_page_alloc parport_pc i915 shpchp drm_kms_helper drm i2c_algo_bit video lp parport usbhid hid floppy e100
lee@HomeServer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

I'll trust your opinion.  If you think I should try an upgrade, or a clean install of the 12.04, then I'll give that a shot.  If not I'm ready to try the (more) messy method.  Messy sounds educational, and I want to learn Linux, so messy aligns with my goals.

---

### Post by chili555 on 2012-05-06
You can always download the live CD for 12.04 and try it without installing it. If your wireless (video, sound, et al) works well, then I'd install it. 

If you'd prefer instead, we'll slip on our welding gloves and get messy. It's your call.

---

### Post by Dietrpro1123 on 2012-05-07
Ahhhh, I see what you're getting at.  I didn't understand what you were suggesting the first time around.  That's a good plan. I'll load 12.04 it onto a pendrive and let you know how things go.  Thanks so much for your assistance thus far!

---

### Post by Dietrpro1123 on 2012-05-09
Woohoo!

```

lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

```

Ubuntu 12.04 recognized it immediately.  I've been working on trying to connect.  You recommended a link to this string in another post: [HTML]http://ubuntuforums.org/showthread.php?t=318539[/HTML], so I'm going to give the instructions there a shot.

Thank you so much for all your help with this! Should I go ahead and set this thread to SOLVED?

---

### Post by chili555 on 2012-05-09
> You recommended a link to this string in another post:

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

, so I'm going to give the instructions there a shot.Yikes! Those are dated 2006, so they're quite a bit outdated.

In a server, without Network Manager, you need to amend /etc/network/interfaces something like this:```
auto lo
iface lo inet loopback

auto wlan1
iface wlan1 inet static
address 192.168.1.xx
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8
wpa-ssid mynetwork
wpa-psk mysecretkey
```Of course, substitute your details.

Let's hold off on Solved until you connect seamlessly.

I'm glad you've almost conquered it!

---

