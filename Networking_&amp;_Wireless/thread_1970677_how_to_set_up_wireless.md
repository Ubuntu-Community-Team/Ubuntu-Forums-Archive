---
title: "how to set up wireless?"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by bobipod on 2012-05-01
when i want to set up the wireless i get the following boxes
 
SSID:  this box is blank
MODE:  drop down box with 2 choices which is either infrastructure or ad hoc
BSSID:  blank box
DEVICE MAC ADDRESS:  gives a blank box with a pre-filled drop down option WLAN0
CLONED MAC ADDRESS:  blank box
MTU:  automatic bytes
 
What information do i need and where will i get it from?
 
thanks.

---

### Post by ajgreeny on 2012-05-01
> **bobipod said:**
> when i want to set up the wireless i get the following boxes
 
SSID:  this box is blank
MODE:  drop down box with 2 choices which is either infrastructure or ad hoc
BSSID:  blank box
DEVICE MAC ADDRESS:  gives a blank box with a pre-filled drop down option WLAN0
CLONED MAC ADDRESS:  blank box
MTU:  automatic bytes
 
What information do i need and where will i get it from?
 
thanks.
Normally you do not need any of that information.

If you click on the network manager icon in the panel, and there are detected wireless connections available with their SSIDs showing, you can click on the one you want and the system will ask for password to connect (assuming the wireless connection is password protected).

Only if you are connecting to a hidden wireless connection for the first time will any of the info you are asking about be needed, so are you sure you can not connect without all that palaver?

---

### Post by bobipod on 2012-05-02
i've been through network manager and it shows the cable unplugged for ethernet, wireless is active but none found. I can't remember what the third was, something to do with hot spot.
 
If i go through the network connections at the top of the screen it is all blank and requires me to fill in the boxes as in the first post.

---

### Post by ajgreeny on 2012-05-02
So how do you think you are connected; by cable or wireless?

And do you know the SSID of the wireless signal that you think you should be able to connect to?

What hardware do you have?  If you don't know show us the output of ```
lspci
``` and ```
sudo lshw -C network
```Can you ping your router IP address, which will probably be shown on the label on the bottom of the router, something like 192.168.0.1, and see if you are connected to that. ```
ping -c 5 192.168.0.1
```Use your router's IP of course.

---

### Post by bobipod on 2012-05-14
[IMG]http://i147.photobucket.com/albums/r298/Cabble/Screenshotfrom2012-05-14203842.png[/IMG]


[IMG]http://i147.photobucket.com/albums/r298/Cabble/Screenshotfrom2012-05-14203605.png[/IMG]

Hopefully these two help

192.168.0.3 IP

---

### Post by bobipod on 2012-05-16
bump for the day

---

### Post by bobipod on 2012-05-17
no one know how to set up wireless?

---

### Post by jon zendatta on 2012-05-17
It sounds like you mean creating a wireless network from scratch? As opposed to connecting to an existing wireless connection, which would just entail clicking network-manager icon at top right hand corner & clicking your network name then entering your password.
Alternatively if you are creating a new network, you'll need to do some research on your modem/router first.Eg your modem login address,  user name & password.:KS

---

### Post by kurt18947 on 2012-05-17
It looks like you're connected to a wired connection.  You cannot have both a wired and wireless network connection and wired is given priority.  You can use the wired connection to install any networking related software in "additional drivers".  After that, you'll want to shut down, disconnect the wire, then restart.  If the module(s) required by your wireless are present, you should see some signs of life in Network Manager's wireless tab.

---

### Post by bobipod on 2012-05-18
> **jon zendatta said:**
> It sounds like you mean creating a wireless network from scratch? As opposed to connecting to an existing wireless connection, which would just entail clicking network-manager icon at top right hand corner & clicking your network name then entering your password.
Alternatively if you are creating a new network, you'll need to do some research on your modem/router first.Eg your modem login address,  user name & password.:KS

Thank you that is exactly what i've needed to know.

---

### Post by bobipod on 2012-05-26
still no joy with this.

There are no wireless access points being seen by my laptop (the wifi switch is on and working).

I've got all of my information from the router and password for the network.

What information do i enter into which box to set up the network?

At no point when i have tried will the network manager allow me the option to save the details i have entered.

The information needed is in the posts up above.

The information i have from the router is:

wireless name 
password
pin
serial
mac

There is no other information on the router and the tech guys at my isp have not heard of all the information that is listed in the boxes above.

---

### Post by Mopar1973Man on 2012-05-26
Like on my laptop (Sony Vaio) I got to setup what type a security your using (WEP or WPA). Then enter you passwords and such. But its mostly based on getting the right password enter so the communication can even start. 

In a controlled environment I would drop the security of the wireless hub to NONE and then bench test and see if you can hook to it. Then one step at a time increase the security and lock it down.

Like here locally I'm running WPA security and no broadcast of ID's... Hard to hack if you can't see... :)

---

### Post by wildmanne39 on 2012-05-26
Hi, first network manger will set the wirteless connection up for you if it is seeing a wireless connection so please remove what you have entered.

Second it is a myth that a hidden network is harder to hack then one that is broadcsting but it is harder for linux to connect to a hidden network so make sure your is set to broadcast.

Please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by bobipod on 2012-05-26
> **wildmanne39 said:**
> 

Please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
``` 

(cat /etc/lsb-release; uname -a)

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux dad-Inspiron-1520 3.2.0-24-generic-pae #39-Ubuntu SMP Mon May 21 18:54:21 UTC 2012 i686 i686 i386 GNU/Linux

(lspci -nnk | grep -iA2 net)

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01f1]
    Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge

(lsusb)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

(iwconfig)

lo        no wireless extensions.

eth1      no wireless extensions.


(rfkill list all)

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

(lsmod)

Module                  Size  Used by
joydev                 17393  0 
vesafb                 13516  1 
parport_pc             32114  0 
rfcomm                 38139  0 
bnep                   17830  2 
ppdev                  12849  0 
bluetooth             158438  10 rfcomm,bnep
snd_hda_codec_idt      60251  1 
binfmt_misc            17292  1 
nvidia              10962290  44 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
r592                   17808  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
b44                    31364  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ssb                    50691  1 b44
dell_laptop            13671  0 
r852                   17901  0 
sm_common              16737  1 r852
psmouse                72919  0 
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
dcdbas                 14098  1 dell_laptop
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
serio_raw              13027  0 
nand_ecc               13070  1 nand
memstick               15857  1 r592
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2646601  0 
mac_hid                13077  0 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19068  0 
wmi                    18744  1 dell_wmi
lib80211               14040  1 wl
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci

Hopefully that gives all the info needed to diagnose and direct me to a solution

---

### Post by wildmanne39 on 2012-05-26
Hi, you need to have an ethernet connection then run:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
watch for errors when it is done unplug ehternet connection and reboot.
Thanks

---

### Post by bobipod on 2012-05-27
done as above but still nothing, no wireless found by the laptop and no error messages when doing the above.

---

### Post by wildmanne39 on 2012-05-27
Hi, please do:
```
nm-tool
sudo iwlist scan
lsmod | grep b43

```
Thanks

---

### Post by bobipod on 2012-05-28
[IMG]http://i147.photobucket.com/albums/r298/Cabble/latestfiguration.png[/IMG]

The result of the above post

---

### Post by linuxman94 on 2012-05-28
Can you post the output of this command?

```
rfkill list
```

and this:

```
cat /etc/modprobe.d/* | grep bcm
```

---

### Post by bobipod on 2012-05-31
to the above

[IMG]http://i147.photobucket.com/albums/r298/Cabble/killlist.png[/IMG]

---

### Post by wildmanne39 on 2012-05-31
Hi, please do:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Enter password then remove the complete line beginning with [COLOR="Red"]blacklist b43[/COLOR]
save and close gedit.
Then:
```
sudo modprobe b43
```
Thanks

---

### Post by bobipod on 2012-05-31
> **wildmanne39 said:**
> Hi, please do:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```Enter password then remove the complete line beginning with [COLOR=Red]blacklist b43[/COLOR]
save and close gedit.
Then:
```
sudo modprobe b43
```Thanks


Done this, what is next to do?

There were 4 lines identical to each other one under the other with the above description.

---

### Post by bobipod on 2012-05-31
All sorted. Thank you all for your help!

---

### Post by wildmanne39 on 2012-05-31
Hi, did you remove all the four lines please post output of:
```
cat /etc/modprobe.d/blacklist.conf
```
and please post it by following the directions below no more pictures please.

by clicking on new reply then click # and paste the information between the brackets.
Thank you

---

### Post by wildmanne39 on 2012-05-31
Hi, please use thread tools at the top of the page and mark the thread solved.
Enjoy

---

