---
title: "Download -FULL , Browser - NULL ...?"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by raja.genupula on 2011-10-30
Hi I wanna say one thing " why all this crazy issues occur for me only ?" 

Here we go , I have a 512Kbps new connection.When i am doing browsing anything with my two browsers(F,GC) its not doing fast and sometimes try again or reload warning messages but when i put download anything its good giving me a rate of 60KB/S , but browsing not good . if its a connection problem then both things not gonna be good but download is good enough to me but why browsing have problem , please help me friends my OS is Ubuntu 11.10.

Please........:(

Thanks in advance.....

---

### Post by JRV on 2011-10-30
You listed your connection speed as 512Kbps (Kilobits/Second) and your actual download speed as 60KB/S (KiloBytes/Second).  It sounds like everything is right and you just have a slow connection.

---

### Post by raja.genupula on 2011-10-30
Hmm lemme explain clearly 

I have observed everything with system monitor.I have seen the data transmission while doing Browsing and as well as Downloading .

* While doing browsing that browsers(FF&GC) are very slow and if i click anything then that action going to take much amount of time and among 5 to 6 clicks only one action going to done and they are not going to respond and some warning messages like "reload " and "try again"

* for more confirmation i did this . I have put a download and as i have said the rate of downloading is good for me (60KB is ok) then i pause it and open the browser but its not loading and its loaded after some time with very low data rate.

* I am sure , Browsers have some problem with this net connection(they are working good if i connect with my modem).but when i am using this new 512kbps connection they're not working properly . But downloads with this connection are good.

I need help to solve this .

Thanks advance.

---

### Post by wildmanne39 on 2011-10-30
Hi raja, this does sound strange is this a wireless connection? If it is I might be able to help but at this time I know very little about ethernet connections.

Please post the results of:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
nm-tool
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by raja.genupula on 2011-10-31
Hi Larry 
I am fine.


```
assassin@assassin-ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux assassin-ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
assassin@assassin-ubuntu:~$ sudo lshw -C network
[sudo] password for assassin: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:4c:14:de:0b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=11.11.110.93 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:ee00(size=256) memory:fddff000-fddfffff memory:fdde0000-fddeffff
assassin@assassin-ubuntu:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:E0:4C:14:DE:0B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         11.11.110.93
    Prefix:          24 (255.255.255.0)
    Gateway:         11.11.110.1

    DNS:             119.235.48.3


assassin@assassin-ubuntu:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
	Kernel driver in use: r8169
assassin@assassin-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

assassin@assassin-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:14:de:0b  
          inet addr:11.11.110.93  Bcast:11.11.110.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe14:de0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2919 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:743098 (743.0 KB)  TX bytes:143556 (143.5 KB)
          Interrupt:44 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

assassin@assassin-ubuntu:~$ rfkill list all
assassin@assassin-ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

assassin@assassin-ubuntu:~$ sudo iflist scan
sudo: iflist: command not found
assassin@assassin-ubuntu:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
binfmt_misc            17292  1 
ppdev                  12849  0 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  4 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                73673  0 
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
parport_pc             32114  1 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  505108  4 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm_kms_helper         32889  1 i915
drm                   192226  5 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
r8169                  43104  0 
assassin@assassin-ubuntu:~$ 
```


please help me larry ! :(

Thanks ....

---

### Post by ubu_dynamite on 2011-10-31
Just don't download a file and browse the web ad the same time your Internet connection is not fast enough.

Or get a faster Internet connection.

---

### Post by raja.genupula on 2011-10-31
> **ubu_dynamite said:**
> Just don't download a file and browse the web ad the same time your Internet connection is not fast enough.

Or get a faster Internet connection.

come on man.....

before this connection i had run ubuntu forums and updates to my Ubuntu OS with a 236 kbps modem (20 KBPS speed).Now i am doing with 512 kbps.when i am doing downloads how can i browse ? i have given complete  description about my problem.I am not downloading while doing browsing ......I need a solution GUYS

Please HELP ME ON THIS ...ITS REALLY MAKING ME OFF:(:(:(:(

---

### Post by ubu_dynamite on 2011-10-31
If you have a router or your modem has [QOS]("http://en.wikipedia.org/wiki/Quality_of_service") support turn it on and give your browser high priority or use iptables or something for traffic shaping.

Install adblockplus to block ads will safe some bandwidth to.

Thats all i can think of right now but don,t have much experience with such a slow network got 1250KB/s up and 15000KB/s down myself so never have had your problem.

Sorry that i can't be more off help.

---

### Post by raja.genupula on 2011-10-31
> **ubu_dynamite said:**
> If you have a router or your modem has [QOS]("http://en.wikipedia.org/wiki/Quality_of_service") support turn it on and give your browser high priority or use iptables or something for traffic shaping.

Install adblockplus to block ads will safe some bandwidth to.

Thats all i can think of right now but don,t have much experience with such a slow network got 1250KB/s up and 15000KB/s down myself so never have had your problem.

Sorry that i can't be more off help.

My GOD....your internet connection is tooooo fast man.OK lemme have a look at QOS and i dont have problems with Ad problems.

Thanks for your reply man.

---

### Post by wildmanne39 on 2011-10-31
Hi Raja, I am researching your problem give me a few minutes.
Thank you

---

### Post by raja.genupula on 2011-10-31
> **wildmanne39 said:**
> Hi Raja, I am researching your problem give me a few minutes.
Thank you

HI larry ...its good to see you again.Yeah i will be here my friend .

Thank you man.

---

### Post by praseodym on 2011-10-31
Hi,

please show:

```
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
dmesg | grep r8
```
You may want to add the nameservers of your ISP (or the google ones 8.8.8.8 and 8.8.4.4) directly in the NM applet. Did you deactivate IPv6 in Firefox?

---

### Post by wildmanne39 on 2011-10-31
Hi Raja, I did not find anything exactly that would help so I asked praseodym to take a look he works with ehternet connections a lot more then I do.

I was hoping it was a driver issue that we could fix but it does not look like it.

Thank you praseodym

---

### Post by raja.genupula on 2011-10-31
Hi Guys .....the issue solved.The reason for this behavior is my network provider, he had lost his server and repaired . now its too fast (He offered me 1Mbps for this day .Wow getting 100 KBPS download)fast but  i cant trust him so i don't wanna mark this thread as solved permanently . If again my browsers come again like this then first i will ask him and and then get back to you.   

Thanks to all who pick this to help me.

thank you very much one and all.

EDIT: Hi Praseodym  thanks for your time man , its pleasure to meet you.Hi Larry , everything is from my network guy.Now he make it fine.Thank you Larry.

---

### Post by wildmanne39 on 2011-10-31
Hi Raja, I am glad to hear that it is fixed and I wondered if it was an ISP issue but I did not want to say that without checking other things first.
Thank you

---

### Post by raja.genupula on 2011-10-31
> **wildmanne39 said:**
> Hi Raja, I am glad to hear that it is fixed and I wondered if it was an ISP issue but I did not want to say that without checking other things first.
Thank you

Yeah ! actually i had asked him that check once and he said everything is good so i came to post here.

aah! Larry one thing my network providers wanna run their server on ubuntu they said they need something like "cache server something sounds similar to it". is it possible to do with ubuntu if yes show me some links of it will give to them.

---

### Post by wildmanne39 on 2011-10-31
Hi, here are some links for servers.
[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)
[https://help.ubuntu.com/11.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/11.04/serverguide/C/ftp-server.html)
[https://help.ubuntu.com/11.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/11.04/serverguide/C/openssh-server.html)
I hope it helps.

---

### Post by raja.genupula on 2011-10-31
> **wildmanne39 said:**
> Hi, here are some links for servers.
[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)
[https://help.ubuntu.com/11.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/11.04/serverguide/C/ftp-server.html)
[https://help.ubuntu.com/11.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/11.04/serverguide/C/openssh-server.html)
I hope it helps.

yeah thank you Larry . I will send this links to his mail.

---

### Post by ubu_dynamite on 2011-10-31
Squid proxy server
[https://help.ubuntu.com/11.10/serverguide/C/squid.html](https://help.ubuntu.com/11.10/serverguide/C/squid.html)


[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)
[http://www.ubuntugeek.com/apt-cacher-ng-http-download-proxy-for-software-packages.html#more-849](http://www.ubuntugeek.com/apt-cacher-ng-http-download-proxy-for-software-packages.html#more-849)
[http://embraceubuntu.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://embraceubuntu.com/2006/08/02/local-dns-cache-for-faster-browsing/)

---

### Post by raja.genupula on 2011-10-31
> **ubu_dynamite said:**
> Squid proxy server
[https://help.ubuntu.com/11.10/serverguide/C/squid.html](https://help.ubuntu.com/11.10/serverguide/C/squid.html)


[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)
[http://www.ubuntugeek.com/apt-cacher-ng-http-download-proxy-for-software-packages.html#more-849](http://www.ubuntugeek.com/apt-cacher-ng-http-download-proxy-for-software-packages.html#more-849)
[http://embraceubuntu.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://embraceubuntu.com/2006/08/02/local-dns-cache-for-faster-browsing/)

Hi man...its good to see you.
 actually those guys need the server for maintaining the proper connectivity to all users.They are network providers and for that purpose only they need a sever.i have mailed the above post links to them and waiting for reply.

Thank you man.

---

