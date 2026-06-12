---
title: "Intel 4965AGN Next-Gen Wireless-N PCIe Mini Card Network Adapter"
date: 2013-03-23
forum: Networking &amp; Wireless
---

### Post by Healinghands on 2013-03-23
I recently installed a new wireless adapter in my Toshiba Notebook.   I rebooted the Ubuntu and it saw the new device and worked just fine.
The speed I was getting off of [www.speedtest.net](www.speedtest.net) was not what I was expecting.  I then installed the Windows driver with
Windows Wireless Driver App in Ubuntu.   I Rebooted the computer and Ubuntu does not see my device.  It is UNCLAIMED.

   How do I get Ubuntu to see this device using the latest driver?????

  Anyone want to get on my computer remotely I would accept that...

  Thank you

---

### Post by chili555 on 2013-03-23
Please try an experiment. Open a terminal and do:```
sudo modprobe -r ndiswrapper
sudo modprobe iwl4965 11n_disable=1
```Is your wireless working? Is it faster?

---

### Post by Healinghands on 2013-03-23
sudo modprobe -r ndiswrapper

Got Error message 
 
FATAL: Module ndiswrapper not found.

Then I ran 
 
 
sudo modprobe iwl4965 11n_disable=1

Wireless kickes on for about 10 seconds then does not see my Network Card.

Thank you for your help...

---

### Post by Healinghands on 2013-03-23
*-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:95:c6:a3
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.1.7 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f0000000-f0003fff ioport:2000(size=256)
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f1000000-f1001fff


Maybe this can help

---

### Post by Healinghands on 2013-03-23
Update when I run

 

sudo modprobe iwl4965 11n_disable=1

Wireless works until I restart...Then I run command again and it works.

How can I make Wireless Work when I restart the computer without running the command?????

---

### Post by ahallubuntu on 2013-03-23
~

---

### Post by Healinghands on 2013-03-23
Made file iwl4965.conf and saved it into /etc/modprobe.d

  When I hit the save button it told me I do not have permissions to save this file.

What next?
 
 I am not familar with the swcrypto command

---

### Post by chili555 on 2013-03-23
Please do:```
gksudo gedit /etc/modprobe.d/iwl4965.conf
```A new empty file will open. Add a single line:```
options iwl4965 11n_disable=1
```Proofread, save and close gedit. You should be all set.

---

### Post by Healinghands on 2013-03-23
I am sorry to inform you that it does not work...:(

What can I do next?

---

### Post by chili555 on 2013-03-23
May I see:```
cat /etc/modprobe.d/blacklist.conf
cat /etc/modprobe.d/blacklist
cat /etc/modprobe.d/ndiswrapper
```Thanks.

---

### Post by Healinghands on 2013-03-23
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

             When I ran   cat /etc/modprobe.d/blacklist   it told me cat: /etc/modprobe.d/blacklist: No such file or directory

        When I ran cat /etc/modprobe.d/ndiswrapper  cat: /etc/modprobe.d/ndiswrapper: No such file or directory
             When I ran

---

### Post by Healinghands on 2013-03-23
Thank you

---

### Post by chili555 on 2013-03-23
When you reboot and it doesn't work, is iwl4965 loading?```
lsmod | grep iwl
```Does it start working as expected if you do:```
sudo modprobe iwl4965 11n_disable=1
```Let's be sure there is no ndiswrapper declaration in the way:```
sudo apt-get remove --purge ndiswrapper*
sudo rm -rf /etc/ndiswrapper/*
```Reboot and let us have your report.

---

### Post by Healinghands on 2013-03-23
lsmod | grep iwl
iwl4965               106889  0 
iwlegacy               87811  1 iwl4965
mac80211              461261  2 iwl4965,iwlegacy
cfg80211              175574  3 iwl4965,iwlegacy,mac80211




Yes when I run   

sudo modprobe iwl4965 11n_disable=1    the wireless turns on and works.


I did purge the 
ndiswrapper


Rebooted computer and still not working when I run  
sudo modprobe iwl4965 11n_disable=1
IT turn on..

 What shall I do next?

---

### Post by chili555 on 2013-03-23
> lsmod | grep iwl
iwl4965 106889 0
iwlegacy 87811 1 iwl4965
mac80211 461261 2 iwl4965,iwlegacy
cfg80211 175574 3 iwl4965,iwlegacy,mac80211
So are you confirming this is the state when you boot and do nothing? I am regrettably about to resort to the ugly hack method.

May I also see:```
cat /etc/modprobe.d/iwl4965.conf
ls /etc/modprobe.d
```

---

### Post by Healinghands on 2013-03-23
cat /etc/modprobe.d/iwl4965.conf
options iwl4965 11n_disable=1

alsa-base.conf              blacklist-modem.conf         iwlwifi.conf
blacklist-ath_pci.conf      blacklist-oss.conf           ndiswrapper.conf
blacklist.conf              blacklist-rare-network.conf  vmwgfx-fbdev.conf
blacklist-firewire.conf     blacklist-watchdog.conf
blacklist-framebuffer.conf  iwl4965.conf


Thank you again,  I appreciate it...

---

### Post by chili555 on 2013-03-23
Ah, haaa! Let's see this; we probably don't want it:```
cat /etc/modprobe.d/iwlwifi.conf
cat /etc/modprobe.d/ndiswrapper.conf
cat /etc/modules
```Let's step right along; I owe myself a Solved before bedtime.

---

### Post by Healinghands on 2013-03-23
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
james22@james22-Satellite-Pro-A200:~$ cat /etc/modprobe.d/ndiswrapper.conf
alias pci:v00008086d00004229sv00001100sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004229sv00001101sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004229sv00001102sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004229sv00001103sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004229sv00001104sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004229sv00001120sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004229sv00001121sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004229sv00001122sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004229sv00001123sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004229sv00001124sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004229sv*sd*bc*sc*i* ndiswrapper
alias pci:v00008086d00004230sv00001110sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004230sv00001111sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004230sv00001112sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004230sv00001113sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004230sv00001114sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004230sv*sd*bc*sc*i* ndiswrapper



# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp

---

### Post by chili555 on 2013-03-23
Please try:```
sudo su
rm /etc/modprobe.d/ndiswrapper.conf
echo iwl4965 >> /etc/modules
exit
```Now reboot and cross your fingers!

---

### Post by Healinghands on 2013-03-23
It worked...Good work dude...
 
  One more thing I have Verizon FIOS and I paying for 50 down/25 up 

  Just went to speedtest.net and getting 27 down and 19 up

 ANy suggestions?

---

### Post by chili555 on 2013-03-23
Are you close enough to the router? Good signal strength? Often, another channel except the default 6 works better; I use 11.

Off for the evening. Glad it's working.

---

### Post by Healinghands on 2013-03-23
Yes about 5 feet away from my Router....I am using channel 11...

  Thank you again.

---

