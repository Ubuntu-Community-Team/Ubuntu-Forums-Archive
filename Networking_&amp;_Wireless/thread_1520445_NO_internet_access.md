---
title: "NO internet access"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by TheTinyt1 on 2010-06-29
I have an e-machine that is working fine with vista but I really dislike vista or windows in general. But this tells me that it is not the hardware that is not functioning properly though.

as I said I am running an e-machine with the following specs:
code name Conroe 
Intel Celeron E1400
duel core
a McP73VT-PM  mother board 
nvidia GeForce 7050/nforce 619i GPU 
2gig 333.4Mhz ram

I am using the 10.04 64 bit version

For some reason unknown to me it quit recognizing the wired and wireless connections yesterday. I do not remember doing anything or changing anything. all I did do was transfer data (non-Linux) data to a backup drive.
It does not show a wired network at all thought I am currently sending you this message over the wired network via Vista.
The wireless is recolonized but for some reason will not lock on to it. It times out trying. I have hunted and hunted for some solution but to no avail. I am using a realtek wireless card not sure of the numbers though.
I use the generic Linux install set up and have changed nothing since the install.

I am hoping that this is simple and that someone can direct me to what I need to do. I am not a programmer and am not too good with the command line though I can use it if given explicit directions.

Thanks for any help you may be able to provide

sincerely
Charles Ellibee
TheTiny1:confused:

---

### Post by gareththered on 2010-06-29
Hi,

At a terminal (sorry!), type>  ip linkand post the results.

Regards,

Gareth

---

### Post by TheTinyt1 on 2010-06-29
Here is what it shows.  I was able to use the wireless connection about 15 minutes ago and it lasted about an hour.  

	 	 chuck@chuck-desktop:~$ ip link  
 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN  
     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00  
 2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000  
     link/ether 00:00:00:00:00:00 brd ff:ff:ff:ff:ff:ff  
 3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state DORMANT qlen 1000  
     link/ether 00:02:6f:58:31:81 brd ff:ff:ff:ff:ff:ff  
 chuck@chuck-desktop:~$  
 

I hope this helps...


Chuck

---

### Post by gareththered on 2010-06-30
Hi Chuck,

Now for some more command line antics I'm afraid.

First, post the output of:-> iwlist wlan0 scanThe above command displays the Access Points your computer can see.

Next, you will need to fetch some information from the logs, compress this info (as the forum only allows small text file attachments but large compressed ones!) and attach it to your next post.

Type the following at a terminal> grep wlan0 /var/log/daemon.log | gzip > ~/wlan0.txt.gzThe above command searches through the daemon log (located in /var/log/) for any line that has the phrase 'wlan0' in it, compresses it and finally stores it in 'wlan0.txt.gz' in your home directory.

Next do the same for your ethernet connection (with the ethernet cable connected)> grep eth0 /var/log/daemon.log | gzip > ~/eth0.txt.gzNow reply to this post and attach (using the paperclip icon) the two files you've created that should now be located in your home directory (/home/chuck).

Good luck!

Gareth

---

### Post by TheTinyt1 on 2010-06-30
First, Thanks for the help. 

I have enclosed the information you asked for and hope it is of help.

	 	 chuck@chuck-desktop:~$ iwlist wlan0 scan  
 wlan0     Scan completed :  
           Cell 01 - Address: 00:26:F2:FA:68:A4  
                     Protocol:802.11b/g/n  
                     ESSID:"gnome-e5e0a3067-Wireless"  
                     Mode:Managed  
                     Channel:1  
                     Quality:65/100  Signal level:-64 dBm  Noise level:-97 dBm  
                     Encryption key:on  
                     Bit Rates:18 Mb/s  
                     IE: WPA Version 1  
                         Group Cipher : TKIP  
                         Pairwise Ciphers (2) : CCMP TKIP  
                         Authentication Suites (1) : PSK  
                     IE: IEEE 802.11i/WPA2 Version 1  
                         Group Cipher : TKIP  
                         Pairwise Ciphers (2) : CCMP TKIP  
                         Authentication Suites (1) : PSK  
 

 chuck@chuck-desktop:~$  
 

I hope that I did the attachment correctly.

Bright Blessings
TheTiny1

---

### Post by akelsall on 2010-06-30
Let's check layer 1 first:

1. When you look on the back of you computer (where your lan cable is plugged in), do you see a green LED on the card? 

2. Have you tried reseating the cable that plugs into your network card (where your LAN cable plugs in)?

3. Have you checked the connection between your PC an router?

4. Have you tried bypassing the router and plugging directly into your DSL/cable modem?

Can you post the output of **ifconfig**? That may help point to a problem. 

Is your router running DHCP? If so, have made any changes that may affect how many IPs it "doles out"?

Andy

---

### Post by gareththered on 2010-06-30
I concur :-)

The logs for eth0 show the carrier as DOWN.  This suggest a suspect cable, connector etc.  Maybe swap the cable to a different port of your router.

The wlan0 logs show you connecting many times and receiving an IP address from DHCP.  On the other hand, it fails on 30th June (today).  Have you rebooted your router, just in case it's playing up?

Gareth

---

### Post by TheTinyt1 on 2010-06-30
Thanks Gareth;

Here is the ifconfig settings:
chuck@chuck-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:820 (820.0 B)  TX bytes:820 (820.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:02:6f:58:31:81  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:6fff:fe58:3181/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:160348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36889 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:115555846 (115.5 MB)  TX bytes:5016656 (5.0 MB)
          Interrupt:18 

First off let me tell you this, I rebooted my machine 4 times and on the 4th time it finally locked on to the signal and longed on to the net. So right now I am using it. Unfortunately this is hit and misc and seldom works. 
Now to answer your questions:
1) yes there is a green light. And Vista has no problem longing on to the net with it.
2) Yes I have unplugged all the cables and plugged them back in.
3) Yes as I said Vista logs in with no problem.
4) No This is the one thing I have not tried but see little use in it since Vista has no problems.
As for DHCP, I am not sure about that and will find out and let you know shortly.


I hope this helps


Bright Blessings
TheTiny1

---

### Post by gid on 2010-06-30
Oddly enough I'm having a similar problem.  Both wired and wireless networking connections are not working on my Dell Mini 9 running 10.04.  Wireless works very briefly then dies, same with the wired.  Granted I haven't used wired with 10.04 much at all as the netbook stays upstairs most of the time.  Other computers in the house are fine.

from daemon.log
NetworkManager: <info> deactivating device (reason: 2)


Actually... n/m.  I rebooted the router and all is back to normal.  (odd that my other computers didn't have any issues)  My router is usually rock solid running tomato on it, but it is a few years old and it may be showing it's age.

---

### Post by gareththered on 2010-07-01
The logs show that you are using DHCP - it's what gives you your IP address. Typing> grep -i dhcp /var/log/daemon.logat the terminal will show you this.

If rebooting the router doesn't work for the wifi, then I suggest you temporarily reconfigure your router to run without encryption - just as an experiment.  If that works then we can take things from there.

I think some more head scratching is needed for the eth0 connection though!

Regards,

Gareth

---

### Post by TheTinyt1 on 2010-07-02
Thanks, I did as you suggested and still not go. I am wondering why it will log one day and not the next. as for the hard wire I am at a lose too.

Now this is what I have tried but no good.
removed the wireless card and still no land line.
the green light lights up showing a connection.
vista does long in through the land line'

As for the wireless it makes no sense to me.
one day it logs in fine.
but like to day it shows a 3 and 4 bar signal but will not long into it. the icon for the wireless as it twirls shows only 1 green and 1 gray dot. so i suppose that it is showing a signal but not able to lock on. Why is beyond me.

Would it be better to just scrap this version of ubuntu and down grade to 9.01?

I do need this system up and running and Kubuntu gave me fits and so does ubuntu. though I do not remember having nearly as much trouble. 

Or would WICD work better for me if I can ever get the machine to log in long enough to install it?

These are all I can see to do. I like Ubuntu and want to keep using it but I have got to do  something to get a more stable system running.

Please advise...

And thanks for all your help...

TheTiny1

---

### Post by gareththered on 2010-07-03
Hi,

I've noticed that your eth0 interface is missing from the output of 'ifconfig' that you previously posted.  Try the following command:-> sudo ip link set eth0 up(It may ask for your password)

This command should change the state to 'UP'.  Now try> ifconfigagain and see if 'eth0' is in the output.  If it appears, it might be worth trying to connect to the Internet with your Ethernet cable again.  If it doesn't then post the output of:-> ip addr show eth0I wouldn't try another distro yet. But if you have a LiveCD it may be worth booting that to see if you can get online.

Regards,

Gareth

---

### Post by TheTinyt1 on 2010-07-04
Ok here is what I got when I typed in these commands:

  	 	 	 	 	 	  chuck@chuck-desktop:~$ sudo ip link set eth0 up  
 RTNETLINK answers: Cannot assign requested address  
 chuck@chuck-desktop:~$ ifconfig  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:8 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:8 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)  
 

 wlan0     Link encap:Ethernet  HWaddr 00:02:6f:58:31:81   
           inet6 addr: fe80::202:6fff:fe58:3181/64 Scope:Link  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:8328 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:3007 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:2671111 (2.6 MB)  TX bytes:0 (0.0 B)  
           Interrupt:18  
 

 chuck@chuck-desktop:~$ ip addr show eth0  
 2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000  
     link/ether 00:00:00:00:00:00 brd ff:ff:ff:ff:ff:ff  
 chuck@chuck-desktop:~$  
 
I tried the destro disk that I have and it could not long into the internet either wire or wireless. I then removed the wireless card and still could not get it to recognise the the wired hook up. I did go to vista to verify that it would load the internet and it did. I then burned a i386 10.04 disk and tried it with not luck. 
I booted back to the hard drive and 10.04 that I am trying to get right and it booted to the network with no problem (wireless that is). 

I know that the card is a realtek N300 card also if that has anything to do with it. 

I still can not for the life of me figure out why it will not find the land line though.

I hope some of this will be of help...

Bright Blessings
TheTiny1

---

### Post by gareththered on 2010-07-04
Hi,

If you can, please post the output of > sudo lshw -c network(which lists the details of all your network hardware) and > lsmod (which lists all kernel modules loaded [generally meaning drivers]).

From the last output that you posted, it seems that the wired connection is down.  The first command I asked you to type should have enabled it.  This is rather strange!  If you post the output of the two commands above, then we can try and figure out exactly what hardware you have.  Make sure the wireless card is plugged in when you do this.  

By the way, I couldn't find any references to Realtek N300 on Google!!  Can you confirm the details of the card?

Regards,

Gareth

---

### Post by TheTinyt1 on 2010-07-04
Here is the information you requested:

chuck@chuck-desktop:~$ sudo lshw -c network 
[sudo] password for chuck: 
  *-network               
       description: Wireless interface
       product: RT2760 Wireless 802.11n 1T/2R Cardbus
       vendor: RaLink
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: wlan0
       version: 00
       serial: 00:02:6f:58:31:81
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.1.7 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=RT2860 Wireless
       resources: irq:18 memory:feaf0000-feafffff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:e800(size=256) memory:febff000-febfffff memory:febe0000-febe1fff(prefetchable)
chuck@chuck-desktop:~$ lsmod 
Module                  Size  Used by
nls_iso8859_1           4633  0 
nls_cp437               6351  0 
vfat                   10866  0 
fat                    55350  1 vfat
nls_utf8                1421  0 
isofs                  33399  0 
snd_hda_codec_realtek   279040  1 
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_intel          25677  4 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usbhid                 41084  0 
psmouse                64576  0 
nvidia              10832442  38 
vga16fb                12757  1 
usblp                  12407  0 
vgastate                9857  1 vga16fb
hid                    83440  1 usbhid
serio_raw               4918  0 
snd                    71106  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rt2860sta             542482  1 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
i2c_nforce2             6099  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
usb_storage            49833  0 
ahci                   37838  3 
r8169                  39650  0 
mii                     5237  1 r8169
pata_amd               11962  0 
chuck@chuck-desktop:~$ 


I am Sorry about that but it is a Rosewill RNX-N300 or atleast this is what the driver disk says for it.

I have no idea where I got that other name from. 

Thanks for the help

Bright Blessings
TheTiny1

---

### Post by gareththered on 2010-07-05
Hi again!

I've found this interesting [link]("http://adam.rosi-kessel.org/weblog/2008/06/21/a-much-simpler-fix-for-the-r8169-link-down-problem") for the eth0 wired problem - no guarantees, but sounds promising! The auto negotiate problem is a known network world issue and my work suffers from it quite often.

As to the wireless, I noticed from your previous post that you do have an IP address for this (192.168.1.7).  This suggests that it's connected?  There are a few posts out on the Internet about people struggling with this card (or more specific, the chipset inside).  I have an earlier version of that chipset in one of my PCs and it's useless!  If you get wired working, then it might be worth investigating NDIS drivers for this card (using NDISWRAPPER).  This is a system where you use Windows drivers on your Linux computer - it has helped people out quite often as long as the Windows driver isn't also buggy!

It seems like your machine has two network devices that aren't 100% compatible with Linux - how unfortunate is that!!  If you have another card it may be worth swapping them over.

Regards,

Gareth

---

### Post by TheTinyt1 on 2010-07-05
gareththered I appreciate what you have tried to do for me and all. I guess I just have to grin and bear this problem with the wireless for now. I will try the ndis wrappers and see if they may help. 

You mention a thread about the wired but did not include it in the last post. What is the thread. If I could get it working then I could worry less about the wireless. 

Thanks again for all the help you have given me.

Bright blessings
TheTiny1

---

### Post by gareththered on 2010-07-05
The word 'link' in my post is the link, if you get my drift.  If not, the URL is [http://adam.rosi-kessel.org/weblog/2008/06/21/a-much-simpler-fix-for-the-r8169-link-down-problem](http://adam.rosi-kessel.org/weblog/2008/06/21/a-much-simpler-fix-for-the-r8169-link-down-problem)

Remember that NDIS-Wrappers will work for any network device, so maybe you can resolve both wired and wireless with it.  It's sometimes helps and at other times causes your system to crash due to buggy Windows drivers.

Good luck!

Regards,

Gareth

---

### Post by TheTinyt1 on 2010-07-05
gareththered I was wondering if there could be some kind of conflict with two different drivers in this?

I have tried to do an ndiswraper but to no avail. I can't even figure out how to get the windows driver recognized by ndis once I installed it.

I am about feed up to the eys with this. From what I can find out the drivers for this particular card are build into linux. if this is the case what is going on. and the wired connection is even stranger.  I am going to have to go back do version 8 at least until I can get this figured out.

Any suggestions on where to go next or what to do would be appreciated.

I do thank you for all the trouble I have already put you through.

Bright Blessings
TheTiny1

---

### Post by gareththered on 2010-07-06
Hi,

From reading through all our posts again, I'm beginning to feel that these are both driver issues.  The first post in this 'Networking & Wireless' forum is on NDIS-Wrapper, but I do agree, it's a little awkward to get working.

While there is a possibility of a driver conflict, the 'lsmod' command you posted only shows one driver for each - 'rt2860sta' and 'r8169' for the wireless and wired respectively.

_**For your wireless:**_

Many posts suggest that the newer versions of Ubuntu use a different driver - a 'rt2860sta'.  This ties in with your statement that an earlier version worked.  Apparently, this new driver isn't always successful at connecting.  The suggested answer is to download a later version from RaLink and compile it yourself.  The post at [https://bugs.launchpad.net/ubuntu/lucid/+source/linux-backports-modules-2.6.32/+bug/496093](https://bugs.launchpad.net/ubuntu/lucid/+source/linux-backports-modules-2.6.32/+bug/496093) shows how it's done - the instructions are around post 25 and a link to the download at 80. Give it a try - it looks more scary than it actually is!

_**For your wired:**_

Did you try installing 'ethtool'.  It's a very good utility for checking/setting you ethernet port. Post the output of> sudo ethtool eth0also post the output of > dmesg | grep eth0Regards,

Gareth

---

### Post by TheTinyt1 on 2010-07-06
Sorry; I messed up somehow and am now completely unable to get into ubuntu. looks like I deleted something and trashed the system.  I did how ever get to type in  "sudo ethtool eth" and got not installed.  What ever that means.  Looks like ethtool is not part of the basic install from the hard drive. I will have to completely reinstall the os before I can go any further. So that is how it goes I guess.

I will reinstall the os and let you know what these codes come up with if anything.

Sorry for the delay.

Thanks again...

TheTiny1

---

### Post by gareththered on 2010-07-06
Before you do that, you could always boot with the LiveCD and attempt a repair.  On the other hand, maybe a re-install will sort everything.

Good luck!

Gareth

---

### Post by TheTinyt1 on 2010-07-08
I did try the disk with no good results.  I did just for academics sake tried to boot SUSe and Mandriva and they both have the same problem.  Only I don't even get the some times wireless. So I installed the 64bit version of 10.04 and it booted the first time I went into it with not problem.  The second time I booted it found the wireless just fine. And sense then it hasn't booted to the internet. I went ahead and made this a duel boot drive so that I could use it for both systems. 
The funny thing is that ubuntu has a hard time with Wired and wireless on this machine but windows XP pro and Vista both have no problems. I guess that the manufacture of the emachines figured that that was all anyone would want to use them for. 

So now I am back to square 1. I will try and figure out how to do an ndiswrapper and see if I can't get it to work. In the mean time I will have to use windows[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG] to do my work until I can get the internet working with ubuntu.

I do appriciate you help with this gareththered and hope you can still give me some pointers on just how to get this ndiswrapper working.

Thanks again for the help.
I will post the readings to you on what you asked about shortly.

---

### Post by gareththered on 2010-07-08
Hi,
 
The alternative to battling with the eMachine's wired and wireless network card would be to get hold of another brand.  Make sure that it uses a different chipset to the current one and see if that helps.  Could you borrow one from a friend to see if it works and to save you the expense of buying one and finding it's not Linux friendly!  You might be able to borrow an USB wireless adapter.  If that works, you could always try to buy an internal one with the same chipset.
 
Of course, I'll try and help you with NDIS-Wrapper if you go down that route.  It has been a while since I've used it, so I might be a little rusty!
 
It was an excellent move to try the other distros and the 64-bit version.  At least you know it's not an Ubuntu only issue.  Like you said, it seems that both wired and wireless are not happy with Linux.  Strange thing is, other users have managed to get those devices working with Linux in the end.
 
Good luck,
 
Gareth

---

### Post by francesco44 on 2010-07-08
Hello friends....

Sorry to interfere...BUT.....I have the same problem on TWO different machines AT THE SAME TIME...1 Thinkpad X31, 1 Thinkpad X60...this hapenned after a recent update...You will find the same thing on Many thread...One of the last upgrade is obviously faulty...Fortunately...I did not upgraded my other X31 (I have 2) and my T60!

Therefore the developers should go backward...till this effect disappear...and compare version...

Otherwise.....We will fill 45 pages of thread...

francesco

---

### Post by gareththered on 2010-07-08
We may two different faults here.
 
francesco44's fault appeared after an update, while TheTinyT1 has problems even with LiveCDs which will have relative old (and not updatable) software.
 
Regards.
 
Gareth

---

### Post by TheTinyt1 on 2010-11-03
gareththered:

Sorry for the delay in getting back to you. But as you said My wireless card was not compatible for some reason with ubuntu and for some reason so was the built in Ethernet adapter wasn't either. 
What I did was reinstalled ubuntu and still no help, then I resigned myself for a while using windows xp for the internet until I could bear it no longer.  A friend of mine gave me a cheep ethernet card with just a wired connection on it. I can not even tell you want brand it is. I stuck it in the machine and ubuntu took to it like a fish to water and now I only use windows xp for dvdfab. Other than that I am now ubuntu all the way. 

Thanks for the help and next time I will make sure that what ever machine i get it will be Ubuntu compatible or they can keep it.  

I do appreciate the help you gave.

Bright Blessings
Charles Ellibee
TheTiny1

---

