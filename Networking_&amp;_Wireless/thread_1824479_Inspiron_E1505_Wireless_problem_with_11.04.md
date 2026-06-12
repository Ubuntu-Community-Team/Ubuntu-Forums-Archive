---
title: "Inspiron E1505 Wireless problem with 11.04"
date: 2011-08-13
forum: Networking &amp; Wireless
---

### Post by M@ Tux on 2011-08-13
I have recently upgraded from 10.06 to 11.04 today and am having problems getting my wireless working. On 10.06 it was working just fine after I used the additional driver utility. Now on 11.04 I have used the additional driver utility and installed the Broadcom STA wireless driver that it says is required, but the internet connections on the top toolbar only recognizes my wired connection. Any advice?

---

### Post by varunendra on 2011-08-14
Hi M@ Tux and welcome to the forums!

Please post the outputs of:
```
iwconfig
```
```
ifconfig -a
```
```
sudo lshw -C network
```
```
rfkill list all
```
```
lsmod | grep bc
```

Also, how did you install the sta driver? If you followed some guide or tutorial, please post its link. And I assume you mean 10.04 since Ubuntu has only .04 and .10 versions of releases (04=April, 10=October). Just FYI.

---

### Post by M@ Tux on 2011-08-14
**iwconfig**

lo no wireless extensions
eth0 no wireless extensions

**if config -a**

eth0      Link encap:Ethernet  HWaddr 00:19:b9:4e:03:ff  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe4e:3ff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:918 errors:0 dropped:0 overruns:0 frame:0
          TX packets:818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:765680 (765.6 KB)  TX bytes:118798 (118.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1296 (1.2 KB)  TX bytes:1296 (1.2 KB)

**sudo lshw -C network**

*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:4e:03:ff
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.3 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff

**rfkill list all**

0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes


the last command gave no input, just went to next terminal input line like it accepted the command and did what i asked.

Thank for the welcome, I have been wanting to switch to a linux based OS forever and finally did it about 6 months ago and I am never turning back. Thanks for the help and I do belive you are right about my previous version being .04 haha. Oh and I installed the STA Driver from the Additional Drivers Application built into the OS.

---

### Post by bkratz on 2011-08-14
In my opinion you will end up removing the STA (wl) driver and installing:
b43-fwcutter
firmware-b43-installer

Before you are done. 
 The STA driver often blacklists the ssb module which B44 uses for your wired connection, but it would appear that you don't have this problem. Anyway, first try a simple

sudo rfkill unblock all

and try the 
rfkill list all 
command again. If no different post the output of 

lsmod

It is rather long so please use the code<> tags to make it readable.

---

### Post by varunendra on 2011-08-14
@M@ Tux,
I'd just do what bkratz suggested. You seem to have got the right person on job now :)

Apart from doing what he suggested, this maybe interesting for you: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by M@ Tux on 2011-08-14
Ok I used **sudo rfkill unblock all** then **rfkill list all **and my output was:

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

I then uninstalled my STA Driver and installed **b43-fwcutter** but the command **firmware-b43-installer** is telling me that the command is not found. I will post the **lsmod **list below. (Sorry I only copied and pasted it I am not exactly sure what you mean buy the code <> tags.) I am fairly new to Linux and I appreciate all the help you guys can offer.

Module                  Size  Used by
binfmt_misc            13213  1
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
b44                    35301  0 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
r852                   17878  0 
ssb                    45942  1 b44
wl                   2642531  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
snd_timer              28659  2 snd_pcm,snd_seq
nand_ids                8547  1 nand
i915                  450934  3 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
nand_ecc               13070  1 nand
mtd                    26720  2 sm_common,nand
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         40745  1 i915
lib80211               14570  1 wl
soundcore              12600  1 snd
joydev                 17322  0 
drm                   180037  4 i915,drm_kms_helper
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
dell_laptop            13515  0 
dell_wmi               12601  0 
video                  18951  1 i915
sparse_keymap          13666  1 dell_wmi
psmouse                73312  0 
lp                     13349  0 
dcdbas                 14054  1 dell_laptop
serio_raw              12990  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
sdhci_pci              13623  0 
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core

---

### Post by bkratz on 2011-08-14
> **M@ Tux said:**
> Ok I used **sudo rfkill unblock all** then **rfkill list all **and my output was:

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

I then uninstalled my STA Driver and installed **b43-fwcutter** but the command **firmware-b43-installer** is telling me that the command is not found. I will post the **lsmod **list below. (Sorry I only copied and pasted it I am not exactly sure what you mean buy the code <> tags.) I am fairly new to Linux and I appreciate all the help you guys can offer.

Module                  Size  Used by
binfmt_misc            13213  1
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
b44                    35301  0 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
r852                   17878  0 
ssb                    45942  1 b44
wl                   2642531  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
snd_timer              28659  2 snd_pcm,snd_seq
nand_ids                8547  1 nand
i915                  450934  3 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
nand_ecc               13070  1 nand
mtd                    26720  2 sm_common,nand
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         40745  1 i915
lib80211               14570  1 wl
soundcore              12600  1 snd
joydev                 17322  0 
drm                   180037  4 i915,drm_kms_helper
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
dell_laptop            13515  0 
dell_wmi               12601  0 
video                  18951  1 i915
sparse_keymap          13666  1 dell_wmi
psmouse                73312  0 
lp                     13349  0 
dcdbas                 14054  1 dell_laptop
serio_raw              12990  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
sdhci_pci              13623  0 
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core



The hard block usually says that the wireless is not switched on. Assuming that it is (whether by switch or keystrokes) it probably would be worth the time to try

sudo rmmod -f dell-laptop

This module sometimes gets confused reading the switch state. This command will temporary remove the offender. It will not be permanent at reboot and will return. After doing it try the rfkill list all again and see if that last pesky block goes away.

---

### Post by varunendra on 2011-08-14
> **M@ Tux said:**
> ....installed **b43-fwcutter** but the command **firmware-b43-installer** is telling me that the command is not found. I will post the **lsmod **list below. (Sorry I only copied and pasted it I am not exactly sure what you mean buy the code <> tags.).
Sorry for intrusion.. just a quick hint..
**firmware-b43-installer** is also a package that you'll have to install, not a command. For tagging a text, select it with your cursor (in the post where you pasted it) and click on the **# **symbol located at the top of the edit box in which you create/edit posts. This will automatically create the tags ([ code] and .... [ /code]) around the selected text for you.

Also, as the output of rfkill hinted, make sure the adapter is physically switched 'On' if there is a switch or keyboard shortcut to do so.

I'll hand over to bkratz now :)

---

### Post by RadarReady on 2011-08-14
Wow! I just installed 11.04 on the same exact machine yesterday and i'm getting the exact problem so far. There must be an elegant solution to it. I'll  follow along with you guys and see what happens.

---

### Post by RadarReady on 2011-08-14
As far as the wireless switch on the keyboard goes here's the difference when you hit the "switch" (**Fn + F2** for our E1505s) between entering the rfkill list all command. 

```

ian@Fienix-MM061:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```Press **Fn + F2**

```
ian@Fienix-MM061:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
```So which way do we want to have it? It doesn't seem to be the final solution we're looking for.

AHA, I got the soft block to go away by entering the ```
rfkill unblock all
``` command again. So now I have a wireless LAN that is both not soft or hard blocked... what now?

---

### Post by bkratz on 2011-08-14
> **RadarReady said:**
> As far as the wireless switch on the keyboard goes here's the difference when you hit the "switch" (**Fn + F2** for our E1505s) between entering the rfkill list all command. 

```

ian@Fienix-MM061:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```Press **Fn + F2**

```
ian@Fienix-MM061:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
```So which way do we want to have it? It doesn't seem to be the final solution we're looking for.


Leave yours in the hard block no position and do a 

sudo rfkill unblock all

you don't want either to show as blocked.  Then see if rfkill list all show both as no. One is software the other hardware.

---

### Post by RadarReady on 2011-08-14
Done that, now have this:

```
ian@Fienix-MM061:~$ sudo rfkill unblock all
ian@Fienix-MM061:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```This does not seem to help in any obvious way, however.

---

### Post by bkratz on 2011-08-14
> **RadarReady said:**
> Done that, now have this:

```
ian@Fienix-MM061:~$ sudo rfkill unblock all
ian@Fienix-MM061:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```This does not seem to help in any obvious way, however.


Have you (with a wired connection) installed software? What packages?

---

### Post by RadarReady on 2011-08-14
Same as OP. I have a wired connection now (working from the machine to talk to you now). The exact driver i have updated now is:

[I]Broadcom 802.11 Linux STA wireless driver

for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based hardware.[/I]

I got it from clicking on the "Additional Drivers" app that automatically ran when I first installed 11.04

---

### Post by bkratz on 2011-08-14
> **RadarReady said:**
> Same as OP. I have a wired connection now (working from the machine to talk to you now). The exact driver i have updated now is:

[I]Broadcom 802.11 Linux STA wireless driver

for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based hardware.[/I]

I got it from clicking on the "Additional Drivers" app that automatically ran when I first installed 11.04



The b43 package described earlier works with less problems on the bcm4311, esp. on the wired connection. Anyway this was copied from an NM_Geo posting.

"

Go to Synaptic and search for bcm > enter

Then remove the bcmwl-kernel-source and bcmwl-modaliases and any other with sta in the package name.

You probably will need to check the blacklisted drivers. 

"

To check this enter the following (copy/paste) in the terminal

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'

```

It you see either b43 or ssb listed we will have to edit the blacklist files. " We will have to find those files.

If not in the list 

You need two files, the installer is firmware-b43-installer  Then you need b43-fwcutter installed. Reboot and enjoy. Both of these files are in synaptic also, just search for bcm

---

### Post by RadarReady on 2011-08-14
> **bkratz said:**
> 

"

Go to Synaptic and search for bcm > enter

Then remove the bcmwl-kernel-source and bcmwl-modaliases and any other with sta in the package name.

You probably will need to check the blacklisted drivers. 

"

To check this enter the following (copy/paste) in the terminal

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'

```It you see either b43 or ssb listed we will have to edit the blacklist files. " We will have to find those files.

If not in the list 

You need two files, the installer is firmware-b43-installer  Then you need b43-fwcutter installed. Reboot and enjoy. Both of these files are in synaptic also, just search for bcm

Brilliant! Followed this exactly and didn't have anything blacklisted. Wi-Fi works perfect now. You are a gentleman and a scholar. I don't know about OP but this fixes my problem. Thanks for your time.

---

### Post by bkratz on 2011-08-14
Glad to have helped, enjoy your wireless!

---

### Post by M@ Tux on 2011-08-14
That helped me out too running fine now, thanksBkratz

---

### Post by bkratz on 2011-08-14
> **M@ Tux said:**
> That helped me out too running fine now, thanksBkratz



Was wondering if it helped, congratulations! and please mark the thread as solved with the thread tools above in case it helps someone else.

---

### Post by gadoth on 2012-02-18
This is just awesome... I know nothing about Linux and tried Ubuntu for the first time. It worked fantastic. You are so kind !

---

