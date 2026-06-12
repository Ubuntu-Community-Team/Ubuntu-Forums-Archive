---
title: "Sudden and mysterious loss of entire eth0 connectivity"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by sjmiller85 on 2009-03-19
Strangely enough (and not the first time over my Ubuntu use), I have lost connectivity to any eth0 connection with my Ubuntu installation.  This is mysterious because I have no idea how it suddenly just stopped.  It is not registering a cat-5 cable even being plugged in.  To add even more confusion, I tested it on my Windows Vista partition that I maintain and it works fine...

One thing that *might* attribute to this (I italicize the "might" because I honestly have no clue), may be that my internet connection requires user authentication (pay for use), which prompts me to type in my user and pass before internet connectivity is established.  I am unable to use any other method at the current moment (and for the next 5 months...), to include wireless, there is no wireless connectivity out here.  It just mysteriously quit.

On top of the aforementioned points of interest, I even went as far as to back-up all my data and re-install Ubuntu 8.10 today, and it still will not register a successful eth0 connection.  I reformatted the ext3 partition and put Ubuntu right back on it.  I honestly have no idea what the problem could possibly be if the hardware works on windows, and whiping and re-installing Ubuntu doesn't resolve the problem... Is this a problem with the ISP?  Where can I start to diagnose this problem?

---

### Post by sjmiller85 on 2009-03-19
Also of note (and not to my surprise), using the installer CD and booting Ubuntu straight from the disk also does not allow me to even register a conneciton.  The eth0 portion of the network manager at the top is grayed out (as is the case without the installer CD).

---

### Post by mathe on 2009-03-19
Same thing here :(
At this very moment, while surfing, it just went stone dead. Thought it was my wireless card. But, like you said, the entire eth0 gone!!!!!! Restarting did not help.
Unbelievable to say the least. I'm sending this through my 8.04 machine that works as usual (i.e. great).
WHAT IS GOING ON HERE???????

/mathe

---

### Post by mathe on 2009-03-20
Well, this is disturbing. I've been brushing up on my network skills and tried a bunch of stuff but I'm stuck. Bringing eth0 back up manually didn't do a thing. I can't even bring my wired connection back up. Seems like the network manager is messed up, but why can't I get it working the good old fashioned way. And why did it get messed up in the first place?
I'm going to get some sleep and try again with newly rested neurons. Meanwhile, if anyone experienced similar spooky behavior, please chime in. Ideally with a solution...

/mathe

---

### Post by tenmoi on 2009-03-20
After the last two days of googling to solve my own problem with setting multiple NICs in LInux I think I can help you.

but first some questions:
- Are you using an ADSL modem or a dialup modem (this one is very unlikely I guess)?
- name and model of your NIC?
- Post results of:
  $ifconfig -a
  $ping localhost
  contents of /etc/network/interfaces
  #lspci
  #ethtool eth0

- And have you enabled the NIC? (system/admistration/network and check the box next to your NIC)
- Try #/etc/init.d/networking restart

---

### Post by sjmiller85 on 2009-03-20
Alright, either my computer is as unstable as Charles Manson, or someone seriously slipped me a mickey that made me hallucinate worse than a monkey on a 2 day 'shroom diet ... Because the problem evidently fixed itself...  I didn't do anything (think all I did was browse over the network settings, add a couple of tools to the top bar, didn't really do anything at all... And now it works.  But, I will do as you asked earlier, to see if anything seems out of whack, in an effort to avoid such an annoyance in the future:

1) Definitely not Dial-up ;)
2) Honestly, not sure what my NIC card brand and model is
3)
```
scotty@free-beer:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:a7:35:e7  
          inet addr:10.3.49.17  Bcast:10.3.49.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fea7:35e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1950 errors:0 dropped:4142974192 overruns:0 frame:0
          TX packets:1993 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1434912 (1.4 MB)  TX bytes:280165 (280.1 KB)
          Interrupt:219 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30448 (30.4 KB)  TX bytes:30448 (30.4 KB)

pan0      Link encap:Ethernet  HWaddr ca:cf:eb:a8:e5:aa  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
```
scotty@free-beer:~$ ping localhost -c 10
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.080 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.048 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.031 ms
64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.123 ms
64 bytes from localhost (127.0.0.1): icmp_seq=5 ttl=64 time=0.033 ms
64 bytes from localhost (127.0.0.1): icmp_seq=6 ttl=64 time=0.031 ms
64 bytes from localhost (127.0.0.1): icmp_seq=7 ttl=64 time=0.074 ms
64 bytes from localhost (127.0.0.1): icmp_seq=8 ttl=64 time=0.036 ms
64 bytes from localhost (127.0.0.1): icmp_seq=9 ttl=64 time=0.039 ms
64 bytes from localhost (127.0.0.1): icmp_seq=10 ttl=64 time=0.031 ms

--- localhost ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 8997ms
rtt min/avg/max/mdev = 0.031/0.052/0.123/0.030 ms

```
```
auto lo
iface lo inet loopback

```
```
scotty@free-beer:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
09:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

ethtool is not installed on my laptop, and nor can it be installed, says there is no package named ethtool to download from the apt

---

### Post by tenmoi on 2009-03-20
Now that your NIC is working I should only give you some advice so the next time you can at least solve your own problems.

- It's strange that your interfaces file lists only the lo. And according to your ifconfig result there should be this line: iface eth0 inet static (you can replace static with dhcp if you want a dynamic IP address) in it too.
- A sudo /etc/init.d/networking restart will restart your NIC.
- Next time the interface shall not disappear ghostly any more.
- If eth0 should vanish into thin air, you can do an ifconfig -a, look for eth* and update it accordingly in the interfaces file and /etc/init.d/networking restart and you'll be fine.

As to the ethtool you can search in synaptics for it. It is included in another package so installing that package will install ethtool and other useful networking tools. This tool is useful in that it shows you if your interface is up or down. Do a google search for an ethtool howto.

Here's your NIC's info. read the result of lspci.
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express bla bla

Regards.

---

### Post by mathe on 2009-03-21
Just to report on my problems, now solved:
I got rid of network manager and then got manual static network settings working again in /etc/network/interfaces
One odd thing (at least to me) was I had to change my router to 'open' instead of previous 'shared'. Strange, since it had been working for a few years under shared mode. Oh well...
As for network manager, it will be a long time before I try that crap again.
Command line rules;)

---

### Post by sjmiller85 on 2009-03-21
Well, luck would have it that my laptop would start up with this crap again...

I went to my interfaces file and appended:
iface eth0 inet dhcp

to the file and ran an /etc/init.d/networking restart to no avail.  When I go into the System->Administration->Network Tools and select eth0 from the drop down list, nothing is listed in the box below and everything is described at the bottom as disable or some other text to the effect of "I am broken".

Any ideas past this point?

---

### Post by mathe on 2009-03-22
I can only recommend to completely remove network manager from your system. It's clear to me it is doing a bunch of stuff without leaving me as a user with a clue to status and where things broke. With it installed, looking for solutions is a needle in the infamous haystack.
So, even when you're doing changes to e.g. the interface file, you have no idea what the stupid gui is doing.
Since I'm in ranting mode, I wish the people programming those network guis to be stuck with them for the rest of their lives.
The guiding philosophy should be to leave every possible hint to why things are broken rather than trying to have it work at all times (utopia!).
Meanwhile, thanks to all drivers that has been produced over the years and good command line tools, IT IS pretty easy to set it all up manually from the good old prompt.

---

### Post by sjmiller85 on 2009-03-22
My only hesitation with getting rid of the network manager is that I am not familiar enough with networking through the command prompt to feel comfortable trying to set it up.  If there are any very detailed instructions on how to go about doing it, it will help the comfort level, but at this point, I don't think it would be wise for me to just say "Scrape the only way that I know how to configure my network connection".

---

### Post by tenmoi on 2009-03-22
> **sjmiller85 said:**
> Well, luck would have it that my laptop would start up with this crap again...

I went to my interfaces file and appended:
iface eth0 inet dhcp

to the file and ran an /etc/init.d/networking restart to no avail.  When I go into the System->Administration->Network Tools and select eth0 from the drop down list, nothing is listed in the box below and everything is described at the bottom as disable or some other text to the effect of "I am broken".

Any ideas past this point?

I thought you said your NIC was up and running. Why did you add "dhcp"? What was the original file like?

Now go to this site: [http://tldp.org/HOWTO/Ethernet-HOWTO-4.html](http://tldp.org/HOWTO/Ethernet-HOWTO-4.html) and read the parts on  realtek. I cannot find a matching driver for your card but you can try all of them ONE BY ONE and see if things work for you. Load the module for your NIC for use this way:


A/ BRowse to /lib/modules/your kernel name/kernel/drivers/net and look for one of the 8*.ko the website above gives you.
B/ sudo modprobe -v 8* (without the "ko")
C/ sudo nano /etc/modules and add "alias eth0 8*" (without quotes) on a separate line of its own (still without "ko") to the file - save. Now reboot.
D/ If this one fails, sudo modprobe -r 8* and repeat from A and remember to remove from /etc/modules the .ko that does not work.

(And jugding from your result of ifconfig, your netmask of 255.255.255.0 is wrong, which I overlooked. Google around a little on subnetting and spend 15 - 30 minutes learning and you're quite good to do some funny stuff.)

ONLY If your ADSL is configured to assign IP addresses dynamically can you change your NIC configuration to dhcp. 

AS Mathe suggested you may try removing network manager and do things on the command line. Here are some tips for you:

1. ifconfig -a // tells you your NIC IP address, MAC address, and the NIC name. So for example, ifconfig should spit out "eth0, lo, eth1" etc, etc. you know your linux machine recognizes those many NICs. Open your /etc/network/interfaces and modify it accordingly.

2. ifconfig eth* up/down ( * add your own number from the result of ifconfig -a) // enables/ disables your NICs.

3. Modify your interfaces file.
 - iface eth* inet dhcp // the interface is assigned IP address dynamically
 - iface eth0 inet static // your must supply the IP address mannually
  address 10.3.49.17
  netmask 255.0.0.0
  gateway xxx.xxx.xxx.xxx

 - sudo /etc/init.d/networking restart for the modification to take effect.

/Bie

---

### Post by sjmiller85 on 2009-03-22
I apologize for not clarifying in my last post.  Yes, it was working.  Strangely enough, I came in 2 nights ago ready to buckle down for a long night of diagnostics, trial and error, etc.. etc.. and out of no-where, I go to fire up my ubuntu installation with note-pad full of notes in hand, and it worked!  I had no idea what happened, I didn't mess with anything, notta, it just worked.  So I was happy, why fix what isn't broken right?  I let it be thinking it would be fine.  I ran a few installations (no updates, was 250 some MBs, was gonna hold on that for a bit).  The next day, I come back, fire up the laptop, blamo, it's broken again... No impact, no idea, right in one ear and out the other.

I'm gonna have to write down your notes letter for letter and rehearse this in my head about 20 times before I take a stab at it.  doesn't sound too smooth, but if that's what it takes...  I wish it could just be something as freakin' easy as my less than satisfactory ISP being a little pain in the rear with this and could tell me they are going to fix their issues therefor fixing mine (if only that were the case right?).  I appreciate all the help you've given me, now to start graying my hairs with diagnostics...

As far as the file, adding that line to the end of it, i did that as a test to see once my connectivity crapped out again yesterday.  Wanted to see if adding that line to my file would get it to work, guess I was wrong...

---

### Post by sjmiller85 on 2009-03-23
I owe both of you an apology, as I found out the problem, and I am both extremely relieved, as well as angered by the simple step that I over-looked thinking that it didn't apply to me:

Networking wasn't enabled on start-up.

I saw it mentioned in several other topics, "Check to see if networking starts on boot-up".  I did not believe that to be the problem, because I assumed it started since my windows installation ran just fine with the NIC working squeaky-clean.  So I believed that if Windows ran fine with networking enabled, than networking had to start at boot-up, but I was sadly mistaken.  I guess Ubuntu doesn't start networking like windows does, and it must have caused some lack of configuration.  On top of all of that, I further was led to believe this assumption was accurate, because I found no reason as to why one day my networking capabilities would drop, and the next it would work, only to drop again the next, this is beyond me...

Long story short, enabling networking in the BIOS at start-up fixed my problem, and I am sorry for waisting the time of the other 2 that have contributed to my catastrophe.  I am deeply apologetic.  Thank you very much for trying to help!

---

