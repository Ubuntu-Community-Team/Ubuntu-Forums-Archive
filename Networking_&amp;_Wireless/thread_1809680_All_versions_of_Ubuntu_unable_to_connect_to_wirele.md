---
title: "All versions of Ubuntu unable to connect to wireless with AR5007 after update"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by VicVegas on 2011-07-21
Making a new thread here because the [old one]("http://ubuntuforums.org/showthread.php?t=1765367") never had any responses.

I have windows Vista installed on the computer. Technically it's a laptop (parts wise) but it's actually some strange invention of Sony's for a multimedia center. I have no idea why we bought this thing.

Anyway, I've tried installing Ubuntu, Xubuntu, and Kubuntu on this computer using wubi. I started out using Ubuntu 10.04, and for a long while it worked just fine. But when the 11.04 update finally reared it's ugly head, I updated, and since then I've not been able to connect to my wireless. I eventually uninstalled it and replaced it with Xubuntu, which worked for a while, but after an update that required a restart the wireless stopped working for that too. Same happened just now with Kubuntu.

For starters, you read what I just typed. I can connect in Vista just fine on that computer, and am fully aware of the location of the wireless switch on the back. I've tried switching it off and on in Kubuntu, it does nothing. If you bring up the switch you'll just be insulting me.

The wireless card is a built in Atheros AR5007, my router a Linksys WRT54G.

I'll gather up any other information you need ASAP.

I'm about finished with Ubuntu here, which is really sad seeing as how I really like the way it's designed otherwise. Being simple, easy to use, and having low system impact.

---

### Post by VicVegas on 2011-07-25
It's been three days. 

Hello? :confused:

---

### Post by wildmanne39 on 2011-07-25
Hi, please run these commands in terminal.
```
sudo lshw -C network
```
```
lsmod
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by VicVegas on 2011-08-05
> **wildmanne39 said:**
> Hi, please run these commands in terminal.
 Sorry I've been busy this week. Didn't think to check my e-mail. :( 

Unfortunately for whatever reason I cannot save any word files to my USB. They either won't save at all or when they do they have 0 bytes and no text in them. What's more, after I last used Kubuntu windows asked to run a CHKDSK.

I'm afraid that even using Ubuntu/Kubuntu is a bad idea at this point. So I'm basically giving up on it entirely now, and am currently uninstalling it.

Know of any other Linux systems that can easily be installed on top of Windows?

---

### Post by wildmanne39 on 2011-08-05
Hi, you can install mint linux, if you choose to install the extra packages it will install all packages needed for your wireless card to work and many other things like media.

---

### Post by chili555 on 2011-08-05
There is an indication on another thread that installing madwif, blacklisting ath5k and ath9k fixes the issue: [http://ubuntuforums.org/showthread.php?t=1815464](http://ubuntuforums.org/showthread.php?t=1815464)

---

### Post by VicVegas on 2011-08-06
> **wildmanne39 said:**
> you can install mint linux
Well I like Wubi's method of installation. So I may try switching back to regular Ubuntu, I had fewer problems with that. IDK Kubuntu just feels... broken and over complicated in comparison. I'll still see how good Mint looks though.
> **chili555 said:**
> There is an indication on another thread that  installing madwif, blacklisting ath5k and ath9k fixes the issue
I think I saw this when I was looking for ways to resolve it on my own. But don't I need a connection to install this? I suppose if I install it **before** updating it will be okay though. :???:

---

### Post by chili555 on 2011-08-06
> I think I saw this when I was looking for ways to resolve it on my own. But don't I need a connection to install this? I suppose if I install it before updating it will be okay though.Yes, indeed. Are the older kernel versions on your computer? Can you use the GRUB menu to boot into an earlier version and download the madwifi package? Then boot back into the latest version and install madwifi.

---

### Post by VicVegas on 2011-08-08
> **chili555 said:**
> Yes, indeed. Are the older kernel versions on your computer? Can you use the GRUB menu to boot into an earlier version and download the madwifi package? Then boot back into the latest version and install madwifi.
I actually remember having that with regular Ubuntu after I updated the first time, which was a full blown update from 10.11 to 11.04 (I think those were the numbers), but I ultimately reinstalled and then after an update it wouldn't work either... Okay, I think I'll try reinstalling regular Ubuntu and before updating I'll just download madwifi then.

Edit: Nevermind, that didn't work. I forgot that the wubi on my desktop was the new one. Is there a way to download madwifi to windows and place it on a USB?

---

### Post by chili555 on 2011-08-08
I am not sure your device is actually supported by madwifi. You were asked, but never responded to provide:```
lspci -nn grep 0280
```Here is a snip from the madwifi README:> Atheros Hardware
----------------

There are currently three "programming generations" of Atheros 802.11
wireless devices (some of these have multiple hardware implementations
but otherwise appear identical to users):

  5210  supports 11a only
  5211  supports both 11a and 11b
  5212  supports 11a, 11b, and 11g[http://madwifi-project.org/wiki/Compatibility/Atheros](http://madwifi-project.org/wiki/Compatibility/Atheros)

I'd hate to put you through the trouble to build madwifi only to find that it doesn't work.

---

### Post by VicVegas on 2011-08-09
> **chili555 said:**
> I am not sure your device is actually supported by madwifi. You were asked, but never responded to provide:```
lspci -nn grep 0280
```

I'd hate to put you through the trouble to build madwifi only to find that it doesn't work.
Well... it might not then. Because that command, out of all of the others I was asked to type, did not do **anything**. :neutral:

---

### Post by nm_geo on 2011-08-09
> **VicVegas said:**
> Well... it might not then. Because that command, out of all of the others I was asked to type, did not do **anything**. :neutral:

Try 

```
lspci -nn | grep 0280
```Even the doctor has a typo sometimes.

That ||| line is called a pipe by the \\\ upper right on my keyboard.

---

### Post by VicVegas on 2011-08-09
> **nm_geo said:**
> Try 

```
lspci -nn | grep 0280
```Even the doctor has a typo sometimes.

That ||| line is called a pipe by the \\\ upper right on my keyboard.
That **is** the line I typed, wildmanne39 had me do that. I reinstalled again though, so it's worth a shot.

Edit: Nope. It failed.

---

### Post by chili555 on 2011-08-09
> That is the line I typed, wildmanne39 had me do that. I reinstalled again though, so it's worth a shot.

Edit: Nope. It failed.Do we have a misunderstanding here? The command is *NOT* designed to get your wireless working. It is designed to gather information that we need to see to help you find the best method to get your wireless working. Until we see those exact details, I'm afraid we can go no farther.

nm_geo and wildmanne39 are very good and I have a few decent moments, but we can't accurately decide what to do without knowing your wireless card's exact name and pci.id.

---

### Post by VicVegas on 2011-08-09
> **chili555 said:**
> Do we have a misunderstanding here?
Absolutely not.
I'm saying the command is inert, does nothing, **shows** nothing, zilch, nadda, kaput.
If it had given me info, I'd tell you what it said. It didn't even tell me that it was an unrecognized command, it just didn't say **anything**. 

Please don't think of me as some kind of **moron**, you even act as if I have not been reading what you guys have said. I switched back to regular Ubuntu because Kubuntu would not let me save word files for some reason. I will go through the process wildmanne39 described again and post what I get later. But one thing I can confirm is that *"lspci -nn | grep 0280"* **does not show anything**.

Edit: And before you say it, I've tried both typing and copy/paste.

---

### Post by wildmanne39 on 2011-08-09
Hi, please try:
```
lspci -nn
```
```
lsusb
```
Thank you

---

### Post by chili555 on 2011-08-09
If I was misinterpreted, I sincerely apologize. We have posters from time to time who think that a command is supposed to magically heal their wireless and complain when it doesn't. I don't think any of those cases, or anyone on this forum is a moron. I think they may be inexperienced. All of us were inexperienced at one time, especially me.

Frequent repliers like me and the Wild Man try, as best we can, to read between the lines and figure out what the poster needs, how experienced he or she may be, the best way to frame the fix, etc. Occasionally, I miss my estimation. I'm sorry.> I can confirm is that "lspci -nn | grep 0280" does not show anything.This implies that there is no working wireless device at all. There may be two exceptions; once in my thousands of cases, I saw a *wireless* device at 0200, usually the identifier for ethernet devices, and  couple of times, I have seen wireless devices built-in to motherboards that were attached to USB buses.

You will be in good hands with wildmanne39.

---

### Post by VicVegas on 2011-08-11
> **chili555 said:**
> If I was misinterpreted, I sincerely apologize.
 And I deeply apologize for my former statement that I suspected you thought me a "moron". In fact I made an error here that I did not expect. You were correct, not wildmanne or nm_geo. The correct code did not include "the pipe" which nm_geo described. 

When I entered the code that chili555 mentioned I naturally assumed he had mistakenly left the bar out, then after what nm_geo said I was almost sure. But I was curious, so I entered the code without the bar and got results. Is it possible that it can vary from case to case?

Here are the full results.
```
davis@ubuntu:~$ sudo lshw -C network
*-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:13:a9:f6:2e:de
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:d8000000-d8003fff ioport:2000(size=256)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:27:96:60
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:da000000-da00ffff
davis@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
arc4                   12473  2 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
nouveau               621970  2 
pcmcia                 39671  0 
ath5k                 144412  0 
snd_seq_midi           13132  0 
ath                    19141  1 ath5k
snd_rawmidi            25269  1 snd_seq_midi
mac80211              257001  1 ath5k
snd_seq_midi_event     14475  1 snd_seq_midi
ttm                    65184  1 nouveau
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 nouveau
uvcvideo               66851  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
tifm_7xx1              12898  0 
drm                   180037  4 nouveau,ttm,drm_kms_helper
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
tifm_core              15040  1 tifm_7xx1
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
videodev               75143  1 uvcvideo
cfg80211              156212  3 ath5k,ath,mac80211
joydev                 17322  0 
sony_laptop            34432  0 
psmouse                73312  0 
serio_raw              12990  0 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13184  1 nouveau
soundcore              12600  1 snd
video                  18951  1 nouveau
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
hid_sony               12623  0 
usbhid                 41704  0 
hid                    77084  2 hid_sony,usbhid
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sky2                   49172  0 
davis@ubuntu:~$ lspci -nn grep 0280
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
davis@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
davis@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
davis@ubuntu:~$ 

```

---

### Post by VicVegas on 2011-08-14
OK it's been a while so now I'm going to "bump" as it were.

I think I understand why people would be busy though, especially now.

---

### Post by VicVegas on 2011-08-18
:-\"
Here we go again...

---

### Post by ubontik on 2011-08-21
All of a sadden I stepped in similar problem. I have Ubuntu 11.04. It was fine till yesterday. Yesterday I found out that lost my WiFi. I don't see even my router...
As you suggested earlier I've run some codes. The outputs I provided below:
**************
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:64:fa:e6
       capacity: 100Mbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:42 memory:f6488000-f6488fff ioport:30f8(size= memory:f6489c00-f6489cff memory:f6489800-f648980f
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:e1:57:c7:f1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-11-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f6000000-f600ffff

================
$ lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  504 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
parport_pc             32111  0 
dm_crypt               22463  0 
ppdev                  12849  0 
vesafb                 13449  1 
nvidia               9766978  30 
snd_hda_codec_conexant    43782  1 
iptable_nat            12977  0 
nf_nat                 24827  1 iptable_nat
nf_conntrack_ipv4      19024  3 iptable_nat,nf_nat
nf_conntrack           69744  3 iptable_nat,nf_nat,nf_conntrack_ipv4
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
joydev                 17322  0 
arc4                   12473  2 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
iptable_mangle         12615  0 
snd_hwdep              13274  1 snd_hda_codec
iptable_filter         12706  0 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
ip_tables              18125  3 iptable_nat,iptable_mangle,iptable_filter
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
x_tables               21907  4 iptable_nat,iptable_mangle,iptable_filter,ip_tables
ath5k                 144534  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ath                    19141  1 ath5k
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
r852                   17878  0 
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
nand_ids                8547  1 nand
mac80211              257001  1 ath5k
k8temp                 12872  0 
nand_ecc               13070  1 nand
hp_wmi                 13418  0 
mtd                    26720  2 sm_common,nand
psmouse                73312  0 
serio_raw              12990  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  3 ath5k,ath,mac80211
sparse_keymap          13666  1 hp_wmi
i2c_nforce2            12906  0 
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
forcedeth              58190  0 
pata_amd               13762  0 
video                  18951  0 
sdhci_pci              13623  0 
libahci                25548  1 ahci
sdhci                  22720  1 sdhci_pci
============
$ lspci -nn | grep 0280
 No output
===========
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSIDff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thrff   Fragment thr: off
          Power Management: 0ff
==========
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thrff
          Power Management: off
===========          
$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Thanks in advance...

---

### Post by praseodym on 2011-08-21
Looks similar to [this]("http://ubuntuforums.org/showpost.php?p=11174074&postcount=4"). hp_wmi needs an additional option. Dont forget to reboot.

---

### Post by chili555 on 2011-08-21
> **praseodym said:**
> Looks similar to [this]("http://ubuntuforums.org/showpost.php?p=11174074&postcount=4"). hp_wmi needs an additional option. Dont forget to reboot.My version of hp_wmi doesn't have that parameter:> chili@LAPTOP60:~$ modinfo hp-wmi
filename:       /lib/modules/2.6.38-11-generic/kernel/drivers/platform/x86/hp-wmi.ko
alias:          wmi:5FB7F034-2C63-45e9-BE91-3D44E2C707E4
alias:          wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C
license:        GPL
description:    HP laptop WMI hotkeys driver
author:         Matthew Garrett <mjg59@srcf.ucam.org>
srcversion:     3C7DE6BAC976582505A4C3D
depends:        sparse-keymap
vermagic:       2.6.38-11-generic SMP mod_unload modversions 686 Won't this just lead to "unknown parameter" in dmesg?

---

### Post by praseodym on 2011-08-21
In that [other Thread]("http://ubuntuforums.org/showthread.php?t=1775555") (Starting with #7) it worked there. I also have Lucid installed like that user. With Lucid this module doesn't have that parameter, either.

If it doesn't work you can easily remove that new file **hp_wmi.conf**

---

### Post by ubontik on 2011-08-21
After rebooting I ran those codes and got the following results:
*******
$ sudo rfkill unblock all
$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan result
$ dmesg | egrep 'b43|wmi'
[    0.200012] wmi: Mapper loaded
[   33.033198] hp_wmi: Unknown parameter `wireless'
$ echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp_wmi.conf
options hp_wmi wireless=1

---

### Post by chili555 on 2011-08-21
> **praseodym said:**
> In that [other Thread]("http://ubuntuforums.org/showthread.php?t=1775555") (Starting with #7) it worked there. I also have Lucid installed like that user. With Lucid this module doesn't have that parameter, either.

If it doesn't work you can easily remove that new file **hp_wmi.conf**In the thread you linked, he was asked to create the .conf file and do:> Reboot your system and:

Code:

sudo rfkill unblock all

Why do you assert that the .conf file, which errored out, is the fix?> [ 15.062788] hp_wmi: Unknown parameter `wireless'Help me understand, please.

---

### Post by VicVegas on 2011-08-22
What just happened in here? :confused:

---

### Post by praseodym on 2011-08-23
Did you reboot and

```
sudo rfkill unblock all
```
? Please post the same outputs again afterwards.

Though the error message in "dmesg" this parameter often works (but sometimes not, strange I know...). 

The module **ath5k** also has the option "nohwcrypt", you can test that on-the-fly with

```

sudo service network-manager stop
sudo modprobe -rf ath5k
sudo modprobe -v ath5k nohwcrypt=1
sudo rfkill unblock all
sudo service network-manager start
```
Controls like named above but
```

dmesg | egrep 'firm|ath|wmi|kill|switch|radio'
```

---

### Post by ubontik on 2011-08-23
Thanks to all who responded on my message. I've figured out what went wrong. I have HP Presario F700, and there is a switch in front next to the WiFi light. Accidentally I turned it off. I called to the HP support and guess what?... They wanted to signed me for $14.99 monthly service, and did not do anything. How fair is that?

---

### Post by praseodym on 2011-08-23
Then this is a "real" hardware switch, which cannot be detected in any way by software (rfkill) or "dmesg".

---

### Post by VicVegas on 2011-08-28
Hate to bother, but I did post my output 2 weeks ago...

---

### Post by wildmanne39 on 2011-08-28
Hi, I am sorry I have been away from the computer until a couple of days ago.

I was very sick and my wife was in the hospital for a week.

The out put you showed us was not correct, it did not produce the results we need, it is not any one's fault, so please try the two commands I posted in post 16 and see if it tells us anything.

Also since you reinstall please tell us what version of ubuntu you installed.
Thank you

---

### Post by VicVegas on 2011-09-01
> **wildmanne39 said:**
> Hi, I am sorry I have been away from the computer until a couple of days ago.
My apologies. You're absence is completely understandable. That and I've been neglecting to check my e-mails once again anyway... so it doesn't really matter.
```
davis@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G72M [GeForce Go 7400] [10de:01d8] (rev a1)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 16)
06:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
08:03.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
08:03.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
08:03.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
08:05.0 Multimedia controller [0480]: Fujitsu Limited. Device [10cf:202a]
davis@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 054c:024b Sony Corp. Vaio VGX Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:1836 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
davis@ubuntu:~$ 

```Pretty sure this is what you need.

Oh and I've switched back to regular old Ubuntu now, it's easier for me to use than Kubuntu.

---

### Post by wildmanne39 on 2011-09-01
Hi, that is what I needed, please post the results of these commands I need to see if you are missing the firmware, which I suspect you are.
```
cat /etc/lsb-release; uname -a
```
```
rfkill list all
```
```
dmesg | egrep 'ath|firm'
```
Thank you

---

### Post by VicVegas on 2011-09-01
> **wildmanne39 said:**
> Hi, that is what I needed, please post the results of these commands I need to see if you are missing the firmware, which I suspect you are.

Okay.
```
davis@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
davis@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
davis@ubuntu:~$ dmesg | egrep 'ath|firm'
[    1.152463] device-mapper: multipath: version 1.2.0 loaded
[    1.152467] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.293332] ath5k 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.293348] ath5k 0000:06:00.0: setting latency timer to 64
[   12.293403] ath5k 0000:06:00.0: registered as 'phy0'
[   12.845704] ath: EEPROM regdomain: 0x65
[   12.845709] ath: EEPROM indicates we should expect a direct regpair map
[   12.845714] ath: Country alpha2 being used: 00
[   12.845716] ath: Regpair used: 0x65
[   12.880602] ath5k phy0: Atheros AR5414 chip found (MAC: 0xa0, PHY: 0x61)
davis@ubuntu:~$ 


```

---

### Post by wildmanne39 on 2011-09-01
Hi, I am looking over bug reports that appears to be the problem with your wireless card, it is late here so I am going to get back to you tomorrow, I want to find the best course of action.

If you are interested you can google the error message and it will show bug reports and work arounds.
> ath5k 0000:06:00.0: registered as 'phy0'
Thank you

---

### Post by wildmanne39 on 2011-09-01
Hi, before we try more drastic measures lets try this:

Open synaptic
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall linux-backports-modules-wireless-natty-generic
sudo apt-get update
sudo apt-get upgrade
sudo modprobe ath5k

```
Then unplug your wired connection and reboot.
Thank you

---

### Post by VicVegas on 2011-09-23
> **wildmanne39 said:**
> Then unplug your wired connection and reboot.
Thank you
Right, I should have posted this a few days ago. It worked, thanks for your help! Though I was hoping I wouldn't have to wire the thing up since it's hard to get to the wired connection, being as it's hooked up to a tower that's shoved inside of a desk. Still, from what I'd read prior to even posting this thread I figured it would have to be done this way, so whatever.

Thanks again.

---

### Post by wildmanne39 on 2011-09-23
Hi, your welcome! glad it is working, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.
Enjoy

---

