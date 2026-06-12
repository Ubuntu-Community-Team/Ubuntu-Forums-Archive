---
title: "Can not connect via wireless connection"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by Gyurltrini on 2011-04-01
HI! I'm fairly new here and usually when I have ubuntu problems would google the solutions and try everything I can find, but, the problem I'm having right now I can not seem to find a solution that works.

Maybe I should give a background.
I'm running a ubuntu 10.10 lamp server with a Ra Link (I think that's the name, but I cold be wrong) wireless networking card. I should note here the ip address was also a static ip address.

Up to last week the server seemed to be running fine and was up to date.

This week I had no need to use it, so it was not switched on til today.

The first problem I had, was hardware ... the memory needed reseating ... that was fixed

Then when booting, it did not boot as normal ... so I had to do a recovery ... that seemed to fix that problem

Then when I booted up, I could not connect to the network at all ... there was no network manager icon in the notifications tray

I got my Dad to help and we went through a whole bunch of solutions

We also ran as many tests as possible to determine the conditions of the hardware and everything ... the tests all said the hardware was detected and was fine.

We could not get anything to work

Eventually we figured out how to get the Network Manager to work / display in the notification area, but we still could not get the computer to connect to the network.

Eventually we decided to borrow a modem and cables to connect on the wired network & that worked with changing the ip to dhcp

**_but we still can't get the computer to connect to the network via wireless._**

I should also note at this point, all the wireless network connection settings both in Network Manager and in etc/network/interfaces did not appear to have changed from what they were before, when the wireless did work ... and I reiterate ... _the computer is detecting the network card_. 

So, can anyone suggest a solution here?

---

### Post by Gyurltrini on 2011-04-01
Just an update ... we looked into the driver for the hardware and although we see it listed as installed, when we try to look for the driver module to see if it is loaded or not we hit a little stumbling block ... not understanding how to locate / manually load it via terminal (or any other solution)... well that's what I gathered from my Dad where progress is concerned.

If there's any information that anyone reading this thread needs to help us resolve this, please feel free to ask and I will do my best to get it to you. My Dad's a technician and he's stumped by this problem.

---

### Post by Razorback on 2011-04-01
Probably need to do a few commands
ifconfig
iwconfig
sudo lshw -C network

and see what comes back.

---

### Post by Gyurltrini on 2011-04-02
Thanks, well I know we did run ifconfig and iwconfig but I can't recall exactly what came back right now, so will try again in the morning & post that output.

But I'll just note here that in running atleast one of those commands ... when following other instructions on this problem, we were told to look out for specific things pertaining to wlan and they simply weren't there.

---

### Post by Gyurltrini on 2011-04-02
Ok so here's the output we received from running those & other commands:

_**[COLOR="Red"]1. nm-tool:[/COLOR]**_
> NetworkManager Tool 
 
State: disconnected 
 
- Device: wlan0 ---------------------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            rt61pci 
  State:             disconnected 
  Default:           no 
  HW Address:        AE:66:2A:92:A9:F5 
 
  Capabilities: 
 
  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 
 
 Wireless Access Points  
 
 
- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            forcedeth 
  State:             unavailable 
  Default:           no 
  HW Address:        00:E0:4D:94:56:5D 
 
  Capabilities: 
    Carrier Detect:  yes 
 
  Wired Properties 
    Carrier:         off 

**_[COLOR="Red"]2. sudo lshw -C network:[/COLOR]_**
>   *-network DISABLED       
       description: Wireless interface 
       product: RT2561/RT61 802.11g PCI 
       vendor: RaLink 
       physical id: 6 
       bus info: pci@0000:01:06.0 
       logical name: wlan0 
       version: 00 
       serial: ae:66:2a:92:a9:f5 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=rt61pci driverversion=2.6.35-28-server firmware=N/A latency=32 link=yes multicast=yes wireless=IEEE 802.11abg 
       resources: irq:18 memory:fd800000-fd807fff 

**_[COLOR="Red"]3. sudo lspci:[/COLOR]_**
> 01:06.0 Network controller: RaLink RT2561/RT61 802.11g PCI 
 
administrator@katan1:~$ lsmod 
Module                  Size  Used by 
xt_multiport            1949  1  
binfmt_misc             7952  1  
ip6table_filter         1719  0  
ip6_tables             20295  1 ip6table_filter 
ipt_MASQUERADE          1919  3  
iptable_nat             4593  1  
nf_nat                 20067  2 ipt_MASQUERADE,iptable_nat 
nf_conntrack_ipv4      13143  4 iptable_nat,nf_nat 
nf_defrag_ipv4          1569  1 nf_conntrack_ipv4 
xt_state                1386  1  
nf_conntrack           75238  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state 
ipt_REJECT              2440  2  
xt_tcpudp               2627  4  
iptable_filter          1778  1  
ip_tables              18769  2 iptable_nat,iptable_filter 
x_tables               24391  10 xt_multiport,ip6table_filter,ip6_tables,ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,ip_tables 
bridge                 79540  0  
stp                     2195  1 bridge 
snd_hda_codec_realtek   300173  1  
snd_hda_intel          26147  2  
snd_hda_codec         100855  2 snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep               6482  1 snd_hda_codec 
snd_pcm                88118  2 snd_hda_intel,snd_hda_codec 
arc4                    1497  2  
snd_seq_midi            5932  0  
snd_rawmidi            21775  1 snd_seq_midi 
snd_seq_midi_event      7291  1 snd_seq_midi 
nouveau               569296  2  
snd_seq                57032  2 snd_seq_midi,snd_seq_midi_event 
ttm                    68180  1 nouveau 
rt61pci                21957  0  
crc_itu_t               1739  1 rt61pci 
ppdev                   6644  0  
rt2x00pci               6993  1 rt61pci 
snd_timer              23518  2 snd_pcm,snd_seq 
drm_kms_helper         32836  1 nouveau 
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq 
rt2x00lib              31575  2 rt61pci,rt2x00pci 
led_class               3393  1 rt2x00lib 
edac_core              46822  0  
psmouse                62080  0  
drm                   205238  4 nouveau,ttm,drm_kms_helper 
mac80211              266346  2 rt2x00pci,rt2x00lib 
serio_raw               4942  0  
cfg80211              170485  2 rt2x00lib,mac80211 
i2c_algo_bit            6208  1 nouveau 
k8temp                  4128  0  
edac_mce_amd            9387  0  
parport_pc             30086  1  
eeprom_93cx6            1789  1 rt61pci 
snd                    63684  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore               1240  1 snd 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm 
i2c_nforce2             6155  0  
lp                     10169  0  
parport                36936  3 ppdev,parport_pc,lp 
floppy                 65235  0  
pata_amd               12050  0  
forcedeth              55649  0  
sata_nv                23770  2  

**_[COLOR="Red"]4. iwconfig:[/COLOR]_**
> lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11abg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
           
virbr0    no wireless extensions. 

**_[COLOR="Red"]5. sudo ifconfig:[/COLOR]_**
> eth0      Link encap:Ethernet  HWaddr 00:e0:4d:94:56:5d   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:43  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:50104 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:50104 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:4540733 (4.5 MB)  TX bytes:4540733 (4.5 MB) 
 
virbr0    Link encap:Ethernet  HWaddr e6:af:f7:02:34:dd   
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0 
          inet6 addr: fe80::e4af:f7ff:fe02:34dd/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:900 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 B)  TX bytes:73321 (73.3 KB) 

**_[COLOR="Red"]6. sudo ifconfig wlan0 up:[/COLOR]_**
> SIOCSIFFLAGS: Device or resource busy

---

### Post by matt_symes on 2011-04-02
Hi

```
*-network DISABLED 
description: Wireless interface 
product: RT2561/RT61 802.11g PCI 
vendor: RaLink 
physical id: 6 
bus info: pci@0000:01:06.0 
logical name: wlan0 
version: 00 
serial: ae:66:2a:92:a9:f5 
width: 32 bits 
clock: 33MHz 
capabilities: pm bus_master cap_list ethernet physical wireless 
configuration: broadcast=yes driver=rt61pci driverversion=2.6.35-28-server firmware=N/A latency=32 link=yes multicast=yes wireless=IEEE 802.11abg 
resources: irq:18 memory:fd800000-fd807fff
```

That's your problem. The network interface is disabled.

Have a read through this thread. The same card, driver and problem and it's marked as solved.

[http://ubuntuforums.org/showthread.php?t=1433233](http://ubuntuforums.org/showthread.php?t=1433233)

BTW: It's better you use code tags than quotes for that kind of info. The # button next to the quote button. It's more readable and no similes in the info.

Kind regards

---

### Post by Gyurltrini on 2011-04-02
> **matt_symes said:**
> Hi

```
*-network DISABLED 
description: Wireless interface 
product: RT2561/RT61 802.11g PCI 
vendor: RaLink 
physical id: 6 
bus info: pci@0000:01:06.0 
logical name: wlan0 
version: 00 
serial: ae:66:2a:92:a9:f5 
width: 32 bits 
clock: 33MHz 
capabilities: pm bus_master cap_list ethernet physical wireless 
configuration: broadcast=yes driver=rt61pci driverversion=2.6.35-28-server firmware=N/A latency=32 link=yes multicast=yes wireless=IEEE 802.11abg 
resources: irq:18 memory:fd800000-fd807fff
```

That's your problem. The network interface is disabled.

Have a read through this thread. The same card, driver and problem and it's marked as solved.

[http://ubuntuforums.org/showthread.php?t=1433233](http://ubuntuforums.org/showthread.php?t=1433233)

BTW: It's better you use code tags than quotes for that kind of info. The # button next to the quote button. It's more readable and no similes in the info.

Kind regards

Thank You for the information ... we will check it out and let you know if the solution you posted works for us or not.

---

### Post by Gyurltrini on 2011-04-02
Ok, we did try the solution in that thread and it did not work, so we are using the airdriver command to determine what drivers are installed and apparently it can not detect the driver for the card in the directory it is looking in ... also a number of errors for the drivers it is finding.

Also just want to point out that the solved thread you provided was for Ubuntu 9:10 whereas I'm using 10:10 with grub 2

---

### Post by matt_symes on 2011-04-02
Hi

> **Gyurltrini said:**
> Ok, we did try the solution in that thread and it did not work, so we are using the airdriver command to determine what drivers are installed and apparently it can not detect the driver for the card in the directory it is looking in ... also a number of errors for the drivers it is finding.

Also just want to point out that the solved thread you provided was for Ubuntu 9:10 whereas I'm using 10:10 with grub 2

Yes, i did notice that it was for 9.10. I thought it might be new enough to still work.

I will have a think.

Kind regards

---

### Post by Gyurltrini on 2011-04-02
> **matt_symes said:**
> Hi



Yes, i did notice that it was for 9.10. I thought it might be new enough to still work.

I will have a think.

Kind regards

Thanks! let me know if you need any more information.

---

### Post by Gyurltrini on 2011-04-03
Anyone else have a solution to suggest?

---

### Post by matt_symes on 2011-04-03
Hi

Do you get any hints as to what might be happening from the dmesg kernel ring buffer ?

After a fresh boot...

```
dmesg | egrep 'rt61|wlan0'
```

That might give some clues. Post results back here.

Can you boot into an older kernel. Do you still get the same issue ?

Kind regards

---

### Post by Gyurltrini on 2011-04-03
Well this morning brought another problem ... when we tried to boot, it got as far as the grub loader and could not load further than that ... further inspection seems to indicate (from testing the drive on other computers) that the boot sector files got corrupted ... right now we're running it as a secondary drive on another ubuntu 10.10 computer and can only read one partition on the drive ... the one that has the grub on it.

We also checked it in windows and windows detected two partitions (though it could not read the partitions), but in ubuntu it only detects / reads one partition. We're trying to see if there is a way to detect both partitions in ubuntu.

---

### Post by safarin on 2011-04-03
> **Gyurltrini said:**
> Anyone else have a solution to suggest?

Have you try this solution?? I don't know it will work or not.. 
[URL="http://ubuntuforums.org/showthread.php?t=1490833"]
[SOLVED] *-network DISABLED [/URL]

---

### Post by Gyurltrini on 2011-04-03
thanks for your input ... we had tried some of the suggestions proposed in that thread and were about to try others that were also suggested (actually I think we had just made some of those changes) when we rebooted and found basically the core files of the boot sector (needed to boot the os) seemed to have become corrupted ... as in we could not boot.

Currently we have been able to plugin the hardware to another pc and currently backing up the most important files.

We still haven't figured out how to get the server to boot yet, but atleast with the backups in place, we can reinstall. & hopefully then we will not have problems with wireless again.

---

### Post by matt_symes on 2011-04-03
Hi

Check the SMART status of the hard drive just to be safe.

You can use

```
man smartctl
```

Run a test and then read the results. I would do this from a liveCD.

install package

```
sudo apt-get install smartmontools
```

Just a though.

Kind regards

---

### Post by Gyurltrini on 2011-04-03
hmm, well I've tried to check all that ... but instead of putting the hard drive back in the server tower, I have it running as a secondary drive on this ubuntu system ... so I installed the smart software recommended and since I did not know what to do next, I then went to System>Administration>Disk Utility and when I selected the drive (it does read the drive) it said Partitioning: not partitioned and SMART status: not supported.

---

### Post by matt_symes on 2011-04-03
Hi

How old is the drive ? 

What make and model is it ? 

I don't think you are having much luck at the moment :(

Kind regards

---

### Post by Gyurltrini on 2011-04-03
the harddrive itself is not that old ... probably not even a year ... but it's reading one partition of the drive quite well (where the grub is located) and the other one (which is where the partition got corrupted) right now is only being read because of a command to mount it via terminal.

So I've basically recovered my personal files (which mostly appear to not have been harmed / corrupted at all) ... but there are some directories which are unreadable on that partition.

Actually I just checked something on the Disk Utility ... this 1 hard drive has two partitions on it ... the display for the actual hard drive shows that the SMART status is Healthy and the Partitioning says: Master Boot Record, but when you select the individual partition that holds the boot record (& most other files), it says SMART status: Not Supported and Partitioning: not partitioned.

---

### Post by Gyurltrini on 2011-04-18
Ok here's the wierd thing ... we changed the power supply (thinking possibly the power supply was shorting out the hard drive) and then booted up (without reinstalling) & suddenly it boots up again as normal

& now the only problem remaining is the original problem ... still can not connect via wireless.

---

### Post by matt_symes on 2011-04-18
Hi

The power supply eh ? I've been bitten by that one before as well.

Try this

Open a terminal and type

```
sudo modprobe -r rt61pci
sudo modprobe rt61pci
```

to unload and reload the driver. 

I have been doing some research and i believe you are using the correct driver. If i am mistaken about this (as i have been busy recently) someone will pipe up. I will keep trying to see if you are using the correct driver and version.

Kind regards

---

### Post by Gyurltrini on 2011-04-18
lol, well it turned out that some of the files (for software, such as mysql) had in fact become corrupted, so had to reinstall everything.

We decided to go with the latest 11.04 (which is not yet officially released) and try with that. 

Problem with that is when we try to download the driver with ndiswrapper and we insert the administrator password we get caught with a password error.

Now, I should just note here that the same administrator password used does work for logging in and updating the server, but it is only ndiswrapper that does not recognise it.

So does anyone have a suggestion that I could use perhaps as a alternative way of downloading and installing the linksys driver (which I ralink 2500)?

---

### Post by Gyurltrini on 2011-04-21
No if anyone knows how (on 11.04 beta) to connect via a wireless device ... drivers are installed and it's reading the card, but, it keeps asking me for the password to the network and every time it tries to connect it seems to set up a new wireless connection account ... although it has a wireless connection account already set up with the network password in it ... no matter what it is not accepting the network password.

---

