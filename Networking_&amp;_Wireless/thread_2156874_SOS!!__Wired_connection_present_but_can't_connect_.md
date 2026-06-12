---
title: "SOS!!  Wired connection present but can't connect to internet??  LINUX NEWBIE!"
date: 2013-06-23
forum: Networking &amp; Wireless
---

### Post by kenobi21 on 2013-06-23
Apologies, but I just can't figure this out...

I am using latest Ubuntu 13.04 release.

Internet was working fine on my _**desktop**_, until this morning.  


Using direct line in from ISP (Xplornet).  It shows as connected and all settings within appear correct.  However, absolutely no internet through browsers, etc.

[B][I]I have a laptop running Zorin (Ubuntu 12.04).  
When I hook direct line into laptop, it detects, connects and runs perfectly.  No issues, so the issue is not my provider.

[/I][/B]
Tried going into Terminal to attempt PING test.

Pinging "www.google.com" results in "unknown host" error
Pinging "8.8.8.8" results in multiple hits.

From what I gather, that may mean there is a DNS issue??

My knowledge is almost NIL on that so I don't know what to do from here.

Any assistance would be GREATLY appreciated!!
Thank you.

---

### Post by steeldriver on 2013-06-23
Hello and welcome to the forum

It sounds like you have done all the right things to isolate and diagnose the problem so far so let's see if we can figure out why your DNS lookup is failing - starting with

```
ls -l /etc/resolv.conf
```

(it should be a symbolic link, in the new 'resolvconf as a service' way of doing things)

```
cat /etc/resolv.conf
```

```
service resolvconf status
```

---

### Post by praseodym on 2013-06-23
Hi,

please open a terminal and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
cat /etc/resolv.conf
rfkill list
```

---

### Post by kenobi21 on 2013-06-23
> **steeldriver said:**
> Hello and welcome to the forum

It sounds like you have done all the right things to isolate and diagnose the problem so far so let's see if we can figure out why your DNS lookup is failing - starting with

```
ls -l /etc/resolv.conf
```

(it should be a symbolic link, in the new 'resolvconf as a service' way of doing things)

```
cat /etc/resolv.conf
```

```
service resolvconf status
```




[B]Hello STEELDRIVER,
Here are the results you requested.... and _thank you so much_ for your assistance!

[/B][I]kenobi21@kenobi21:~$ ls -l /etc/resolv.conf  
```
-rw-r--r-- 1 root root 23 Mar  5 22:41 /etc/resolv.conf
```

kenobi21@kenobi21:~$ cat /etc/resolv.conf  
```
nameserver 192.168.2.1
```

kenobi21@kenobi21:~$ service resolvconf status
```
resolvconf start/running
```[/I]

---

### Post by kenobi21 on 2013-06-23
> **praseodym said:**
> Hi,

please open a terminal and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
cat /etc/resolv.conf
rfkill list
```



Hello [URL="http://ubuntuforums.org/member.php?u=1411497"][B][COLOR=#000000]praseodym,
[/COLOR][/B][COLOR=#000000]First off I'd like to thank you as well for your quick reply and offer of assistance with my dilemma!!  I can't thank you enough.
Anyways, on to the task at hand.  Please find below the information you requested...


[/COLOR][/URL][                         ]("http://ubuntuforums.org/member.php?u=1411497")kenobi21@kenobi21:~$ uname -a  
 ```
Linux kenobi21 3.8.0-25-generic #37-Ubuntu SMP Thu Jun 6 20:47:30 UTC 2013 i686 athlon i686 GNU/Linux
```


 kenobi21@kenobi21:~$ lspci -nnk | grep -iA2 net  

 ```
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)  

     Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]  

     Kernel driver in use: r8169
```
  

 kenobi21@kenobi21:~$ lsusb  

 ```
Bus 004 Device 002: ID 07b5:9903 Mega World International, Ltd  

 Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse  

 Bus 007 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader  

 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  

 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  

 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  

 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  

 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  

 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  

 Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  

 Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  

 Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
```
  

 kenobi21@kenobi21:~$ lsmod  

 ```
Module                  Size  Used by  

 snd_hrtimer            12648  1  

 parport_pc             27504  0  

 ppdev                  12817  0  

 rfcomm                 37420  0  

 bnep                   17669  2  

 bluetooth             202069  10 bnep,rfcomm  

 binfmt_misc            17260  1  

 snd_hda_codec_hdmi     36185  1  

 xt_hl                  12465  6  

 ip6t_rt                12473  3  

 nf_conntrack_ipv6      13871  7  

 nf_defrag_ipv6         13025  1 nf_conntrack_ipv6  

 ipt_REJECT             12485  1  

 xt_LOG                 17192  9  

 xt_limit               12541  12  

 xt_tcpudp              12531  22  

 xt_addrtype            12563  4  

 nf_conntrack_ipv4      14071  7  

 nf_defrag_ipv4         12649  1 nf_conntrack_ipv4  

 xt_state               12514  14  

 kvm                   376505  0  

 joydev                 17097  0  

 ip6table_filter        12711  1  

 ip6_tables             17819  1 ip6table_filter  

 nf_conntrack_netbios_ns    12585  0  

 nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns  

 nf_nat_ftp             12548  0  

 nf_nat                 20857  1 nf_nat_ftp  

 nf_conntrack_ftp       13118  1 nf_nat_ftp  

 nf_conntrack           67003  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_state,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6 

 iptable_filter         12706  1  

 ip_tables              17791  1 iptable_filter  

 x_tables               21974  12 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_state,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype 

 snd_hda_codec_realtek    63791  1  

 snd_hda_intel          38307  5  

 radeon                875070  3  

 snd_hda_codec         117580  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel  

 snd_hwdep              13272  1 snd_hda_codec  

 snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel  

 snd_page_alloc         14230  2 snd_pcm,snd_hda_intel  

 snd_seq_midi           13132  0  

 snd_seq_midi_event     14475  1 snd_seq_midi  

 snd_rawmidi            25114  1 snd_seq_midi  

 ttm                    71289  1 radeon  

 snd_seq                51280  3 snd_seq_midi_event,snd_seq_midi  

 snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi  

 snd_timer              24411  3 snd_hrtimer,snd_pcm,snd_seq  

 drm_kms_helper         47545  1 radeon  

 snd                    56485  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device 

 wmi                    18590  0  

 drm                   228489  5 ttm,drm_kms_helper,radeon  

 i2c_algo_bit           13197  1 radeon  

 sp5100_tco             13447  0  

 mac_hid                13037  0  

 i2c_piix4              13066  0  

 k10temp                12958  0  

 microcode              18286  0  

 serio_raw              13031  0  

 soundcore              12600  1 snd  

 lp                     13299  0  

 parport                40753  3 lp,ppdev,parport_pc  

 pata_acpi              12886  0  

 usb_storage            47684  0  

 hid_generic            12484  0  

 usbhid                 41805  0  

 hid                    82666  2 hid_generic,usbhid  

 floppy                 55441  0  

 firewire_ohci          35292  0  

 firewire_core          61718  1 firewire_ohci  

 r8169                  61531  0  

 crc_itu_t              12627  1 firewire_core  

 pata_jmicron           12662  0  

 pata_atiixp            13058  0  

 ahci                   25507  2  

 libahci                26108  1 ahci
```
  

 kenobi21@kenobi21:~$ iwconfig  

 ```
lo        no wireless extensions.  

 

 eth0      no wireless extensions.
```  

 

 kenobi21@kenobi21:~$ cat /etc/resolv.conf  

 ```
nameserver 192.168.2.1
```
  

 kenobi21@kenobi21:~$ rfkill list  

 ```
kenobi21@kenobi21:~$
```  

  [URL="http://ubuntuforums.org/member.php?u=1411497"]
[/URL]

---

### Post by praseodym on 2013-06-24
Do you need the firewall:
```

sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

### Post by jdthood on 2013-06-24
> **kenobi21 said:**
> 
kenobi21@kenobi21:~$ ls -l /etc/resolv.conf  
```
-rw-r--r-- 1 root root 23 Mar  5 22:41 /etc/resolv.conf
```

kenobi21@kenobi21:~$ cat /etc/resolv.conf  
```
nameserver 192.168.2.1
```

kenobi21@kenobi21:~$ service resolvconf status
```
resolvconf start/running
```


If you were running Ubuntu then I would say that something is wrong here. The resolvconf Upstart job is in the "running" state but /etc/resolv.conf is not a symbolic link to ../run/resolvconf/resolv.conf. If you were running Ubuntu then I would then advise you to run "sudo dpkg-reconfigure resolvconf" in order to restore the symbolic link and then to reboot.

But you are running Zorin OS about which I have no special knowledge. You might be better off asking your question on a Zorin OS forum.

---

### Post by kenobi21 on 2013-06-24
> **jdthood said:**
> If you were running Ubuntu then I would say that something is wrong here. The resolvconf Upstart job is in the "running" state but /etc/resolv.conf is not a symbolic link to ../run/resolvconf/resolv.conf. If you were running Ubuntu then I would then advise you to run "sudo dpkg-reconfigure resolvconf" in order to restore the symbolic link and then to reboot.

But you are running Zorin OS about which I have no special knowledge. You might be better off asking your question on a Zorin OS forum.



Actually, I am running Ubuntu on the computer that is having the issues.
I have Zorin on my laptop, which is working fine.  Right now it's my only access to this forum and anything else!

I will try your suggestion above and see what happens.
Thx!!

---

### Post by kenobi21 on 2013-06-24
> **praseodym said:**
> Do you need the firewall:
```

sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```




entered values above to no effect.
status remains the same.

---

### Post by kenobi21 on 2013-06-24
> **kenobi21 said:**
> Actually, I am running Ubuntu on the computer that is having the issues.
I have Zorin on my laptop, which is working fine.  Right now it's my only access to this forum and anything else!

I will try your suggestion above and see what happens.
Thx!!




Well, I entered what you advised and rebooted.  It had no effect on my situation.
Thanks for trying.

---

### Post by kenobi21 on 2013-06-24
Just want to thank you all for your assistance.
I am completely lost as to what to do right now.

On that note, I am laying my trust with you and your advice.
[I][B]If I enter anything into terminal in an effort to rectify my situation and it does not work, I will need to be told if I need to undo said change and also how to do that.
[/B][/I]
I apologize for my ignorance, but I am trying to learn from all of you so please bear with me.
Thanks for your patience!

---

### Post by steeldriver on 2013-06-24
what answers did you give to the reconfigure questions? does 

```
ls -l /etc/resolv.conf
```

now show a symbolic link instead of a regular file? Also, is the device at 192.168.2.1 (from your original resolv.conf) actually providing a DNS service?

```
dig @192.168.2.1
```

What IP range is your computer actually in?

```
ifconfig eth0
```

---

### Post by kenobi21 on 2013-06-24
> **steeldriver said:**
> what answers did you give to the reconfigure questions? does 

```
ls -l /etc/resolv.conf
```

now show a symbolic link instead of a regular file? Also, is the device at 192.168.2.1 (from your original resolv.conf) actually providing a DNS service?

```
dig @192.168.2.1
```

What IP range is your computer actually in?

```
ifconfig eth0
```




Here are the answers to your queries...  (Your initial questions from yesterday were answered earlier in these postings if that helps)
Unfortunately, I don't really understand a lot of this so I'm afraid I'm not much help.  Doing what I can.


                        kenobi21@kenobi21:~$ ls -l /etc/resolv.conf  
 ```
lrwxrwxrwx 1 root root 29 Jun 24 08:50 /etc/resolv.conf -> ../run/resolvconf/resolv.conf
```  

 kenobi21@kenobi21:~$ dig @192.168.2.1  
 
 ```
; <<>> DiG 9.9.2-P1 <<>> @192.168.2.1  

 ; (1 server found)  

 ;; global options: +cmd  

 ;; connection timed out; no servers could be reached
```  

 kenobi21@kenobi21:~$ ifconfig eth0  
 
```
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:e1:6e:38   

           inet addr:192.168.209.4  Bcast:192.168.209.255  Mask:255.255.255.0  
           inet6 addr: fe80::6ef0:49ff:fee1:6e38/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:7 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:197 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  

           RX bytes:1288 (1.2 KB)  TX bytes:31671 (31.6 KB)
```

---

### Post by steeldriver on 2013-06-24
So is resolv.conf still picking up nameserver 192.168.2.1 ? if it is, we need to find out where that's coming from as it's clearly not going to work (dig is not able to get DNS service from that address)

```
cat /etc/resolv.conf
```

How are you setting up your network connection (via the Network Manager / GUI applet?) and if so what are the IPv4 settings (particularly DHCP)? You can dump out the network manager status using

```
nm-tool
```

Do you know what LAN device 192.168.2.1 is (is it your router?)

---

### Post by kenobi21 on 2013-06-24
> **steeldriver said:**
> So is resolv.conf still picking up nameserver 192.168.2.1 ? if it is, we need to find out where that's coming from as it's clearly not going to work (dig is not able to get DNS service from that address)

```
cat /etc/resolv.conf
```

How are you setting up your network connection (via the Network Manager / GUI applet?) and if so what are the IPv4 settings (particularly DHCP)? You can dump out the network manager status using

```
nm-tool
```

Do you know what LAN device 192.168.2.1 is (is it your router?)




Not sure about first question.  Hopefully you find your answers below.

Network Mgr takes care of setup.  

My ISP is through XPLORNET.  Uses cell towers to transmit signals.  I have a dish on my roof that relays/receives data, then the cable comes into the house.
It was connected to a router, but I disconnected that as soon as I started having trouble yesterday.

I am hardlined in with that one cable. Right now, I have to switch back and forth between my laptop and the ailing desktop whenever I need to test or examine the system.
Likewise, I have to switch it back to the laptop so that I can convey my answers to you.
Tedious.

Here is the data you requested:
  	 	 	 	   kenobi21@kenobi21:~$ cat /etc/resolv.conf  
 

 ```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)  

 #     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
```  


kenobi21@kenobi21:~$ nm-tool  
 

 ```
NetworkManager Tool  

 

 State: connected (global)  
 

 - Device: eth0  [Wired connection 1] -------------------------------------------  
   Type:              Wired  
   Driver:            r8169  
   State:             connected  
   Default:           yes  
   HW Address:        6C:F0:49:E1:6E:38  
 

   Capabilities:  
     Carrier Detect:  yes  
     Speed:           100 Mb/s  
 

   Wired Properties  
     Carrier:         on  
 

   IPv4 Settings:  
     Address:         192.168.209.4  
     Prefix:          24 (255.255.255.0) 
     Gateway:         192.168.209.1
```  

  
  	 	 	 	Broadcast Address:  192.168.209.255

---

### Post by kenobi21 on 2013-06-24
One other thing....  I'm 99% sure that my router is fried.

I'm going to pick a new one up later today.


??  Would I be better off re-installing Ubuntu??
Just a thought. 

I'm willing to work it out, but don't want to take up everybody's time either.

---

### Post by jdthood on 2013-06-25
> **kenobi21 said:**
> 
kenobi21@kenobi21:~$ ls -l /etc/resolv.conf  
 ```
lrwxrwxrwx 1 root root 29 Jun 24 08:50 /etc/resolv.conf -> ../run/resolvconf/resolv.conf
```  


That is now correct; /etc/resolv.conf is a symbolic link to the file that resolvconf generates at /run/resolvconf/resolv.conf.

You are running NetworkManager. Resolvconf writes resolv.conf based on what NetworkManager tells it.

NetworkManager usually obtains configuration information via DHCP. However, in your case NM hasn't obtained a DNS nameserver address. (See below.) So your machine does not know where to send DNS queries.

Earlier your /etc/resolv.conf did contain an address, 192.168.2.1.

> 
 kenobi21@kenobi21:~$ dig @192.168.2.1  
 
 ```
; <<>> DiG 9.9.2-P1 <<>> @192.168.2.1  

 ; (1 server found)  

 ;; global options: +cmd  

 ;; connection timed out; no servers could be reached

```

kenobi21@kenobi21:~$ ifconfig eth0  
 
```
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:e1:6e:38   

           inet addr:192.168.209.4  Bcast:192.168.209.255  Mask:255.255.255.0  
           inet6 addr: fe80::6ef0:49ff:fee1:6e38/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:7 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:197 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  

           RX bytes:1288 (1.2 KB)  TX bytes:31671 (31.6 KB)

```


The dig output indicates that dig could not contact a nameserver at 192.168.2.1.

The fact that the nameserver is supposed to be listening at LAN address 192.168.* suggests that it is running on your modemrouter. In that case I would expect it to be listening at an address on the LAN subnet, i.e., on 192.168.209/24.

My guess is that some program other than resolvconf wrote the line "nameserver 192.168.2.1" into /etc/resolv.conf, clobbering the symlink in the process, at some time when there was in fact a nameserver available at that address; but in the current situation the nameserver is listening at something like 192.168.209.1.

> **kenobi21 said:**
> 
kenobi21@kenobi21:~$ cat /etc/resolv.conf  

```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)  

 #     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

```  


The file is empty, so the resolver won't be able to find any nameserver at all (unless there is one running locally and listening at the resolver's default address 127.0.0.1).

> 
kenobi21@kenobi21:~$ nm-tool  

```
NetworkManager Tool  

 

 State: connected (global)  
 

 - Device: eth0  [Wired connection 1] -------------------------------------------  
   Type:              Wired  
   Driver:            r8169  
   State:             connected  
   Default:           yes  
   HW Address:        6C:F0:49:E1:6E:38  
 

   Capabilities:  
     Carrier Detect:  yes  
     Speed:           100 Mb/s  
 

   Wired Properties  
     Carrier:         on  
 

   IPv4 Settings:  
     Address:         192.168.209.4  
     Prefix:          24 (255.255.255.0) 
     Gateway:         192.168.209.1

```  

 	 	 	 	Broadcast Address:  192.168.209.255


It seems that your modemrouter is not currently providing an address for the DNS nameserver.

Check your modemrouter configuration.

If your laptop works then it's possibly because it has a valid *static* configuration.

---

### Post by praseodym on 2013-06-25
Try to reset the router, remove any profile in "wired" and "DSL" and reboot your system.

---

### Post by kenobi21 on 2013-06-25
THAT DID IT!!

SUCCESS!   :D

Installed brand new router, deleted previous settings in Network Manager.
Reset and BINGO... off to the races.

I can't begin to thank all of you that lent your time, knowledge and experience in trying to assist me.

You are a credit to this forum and to the Linux community.

Hopefully, some day, I will be able to be the one helping someone as you did with me.


Again, my sincerest thanks and respect.

CHEERS!!!

---

