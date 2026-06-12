---
title: "Another Dell Studio 1558 wireless problem"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by antonius uno on 2010-03-20
Hi guys,
just registered as I have had already a lot of good use out of this forum. I don't expect to be able to help others as yet but am desparate to phase out windows 7 and get Ubuntu going again on this laptop.

Problem is as follows: I have no wireless on my dell Studio 1558 and no sound (these are common problems as I have found). HW is BCM4312 (or 4315) chipset. funny thing is it worked before until I tried fixing the sound following the other topics on this forum with the evdev.c workaround. So after revising the driver myself I have no sound but also wireless stopped again plus my system froze constantly so I had to revert to the original sound driver.

I use Gnome and when I use NetworkManager it shows me that networking is enable but wireless is grayed out. No possibility whatsoever to convince Ubuntu to turn that option on.
So I used the terminal. Doing iwlist - command gave me a nice scan of all the available wireless networks, but in the GUI I cannot get it to scan.

So my conclusion, the wireless HW is functioning, can scan but the GUI does not do anything.

My questions:
1. For the workaround: how can I on the command line force the wifi to connect to my router?
2. Can anyone help me to get the NetworkManager to function again?.

P.S. I have read quite a lot of topics on these two problems already. The first time (before trying to fix the sound) the Dell support page on wireless was doing the trick for me. But that does not help me anymore.

thanks in advance for any help offered.

---

### Post by coffeeaddict22 on 2010-03-20
Gidday,
Welcome.  I've been using Ubuntu since 8.04, and have to go back to Vista nowadays only to remind myself how slow an OS can be on default install.

Can you open a terminal and post back the output of 
```
nm-tool
sudo iwconfig
cat /etc/network/interfaces
```
So we can see the details?  I think you're going to find you've hard wired your interface in, which makes it invisible to NetworkManager, but there's a couple of other options.

Sound is slightly more complicated at the moment, as I think it's changing in the Lucid (10.04) mix, so doing a whole heap of fiddling is probably a waste of time if you can wait a week for the beta.  If you want to play, start with the sound troubleshooter; in my experience the trick is to open alsamixer (type it in a terminal) and find what's been defaulted to a level of 0.

---

### Post by AntoniusUno on 2010-03-20
Hi,

hereby the requested info. BTW I use Karmic Koala.

> 
x@ubuntu:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth2 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             unavailable
  Default:           no
  HW Address:        F0:7B:CB:24:A3:9D

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        B8:AC:6F:54:68:33

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

x@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

x@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


---

### Post by coffeeaddict22 on 2010-03-21
OK.  Well, not that OK.  Your card is present, wl is attaching, but not announcing it to Network Manager for some reason.  Have you installed wicd as well- or ndiswrapper?

In the terminal, type the following two commands:  ```
lsmod
lshw -C network
```  Post the output of that back.

---

### Post by AntoniusUno on 2010-03-21
Hi,

I have not used ndiswrapper because I wanted to avoid using windows drivers. wicd does not ring a bell to me.

Here is the requested output:

> 
@ubuntu:~$ lsmod
Module                  Size  Used by
isofs                  36424  1 
udf                    88136  0 
crc_itu_t               2336  1 udf
binfmt_misc            10220  1 
ppdev                   8232  0 
joydev                 13088  0 
snd_hda_codec_atihdmi     4320  1 
snd_hda_codec_idt      73008  1 
snd_hda_intel          31880  4 
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_seq_dummy           3460  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
lib80211_crypt_tkip    10016  0 
dell_wmi                3216  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
iptable_filter          3872  0 
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
dell_laptop             9692  0 
v4l1_compat            16644  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
dcdbas                  9136  1 dell_laptop
wl                   1277380  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
fglrx                2234552  33 
lib80211                7812  2 lib80211_crypt_tkip,wl
snd                    77096  20 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
psmouse                57124  0 
serio_raw               6596  0 
sdhci_pci               8928  0 
sdhci                  20484  1 sdhci_pci
led_class               5256  1 sdhci
lp                     11908  0 
parport                40528  2 ppdev,lp
ohci1394               33780  0 
r8169                  38884  0 
mii                     6368  1 r8169
ieee1394              100896  1 ohci1394
intel_agp              33040  0 
video                  23612  0 
output                  3680  1 video

@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth2
       version: 01
       serial: f0:7b:cb:24:a3:9d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: b8:ac:6f:54:68:33
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:35 ioport:5000(size=256) memory:f0404000-f0404fff(prefetchable) memory:f0400000-f0403fff(prefetchable) memory:f0420000-f043ffff(prefetchable)



---

### Post by antonius uno on 2010-03-21
Just for my learning, So far I understand the following (correct me if I am wrong):
1. nm-tool shows the status of the networkmanager. NWMan says eth2 is unavailable.
2. iwconfig shows the status of the wifi which says it is ok, just not connected.
3. cat /etc/network/interfaces shows the contents of the /etc/network/interfaces to see if wireless card is recognised as an interface, which it is not as it is not listed.
4. lsmod shows all loaded modules (including the wl module). Not sure what else to read from it.
5. lshw -C network gives a detailed view of the wifi card properties.

yes I am not so familiar with the command line stuff from Ubuntu/Linux which is what I really like to improve (playfully ;) )

---

### Post by chenxiaolong on 2010-03-21
Everything is right, except for number 3. /etc/network/interfaces are interfaces that are configured by Linux's default network daemon, rather than networkmanager. Anything listed in this file is not managed by networkmanager. (But do not remove the lines that contain "lo")

---

### Post by coffeeaddict22 on 2010-03-21
Hi,
as Chen says, all pretty good.  Network manager won't manage any interface named in your /etc/network/interfaces file.  Lshw is short for something along the lines of "List Hardware"; for more info on it (as with any terminal command), type man lshw into a terminal.  If you're looking for commands on a topic, "apropos *topic*" in a terminal gives you your options.

Can't see a good reason for Network Manager to not let you play in all that.  So what happens if you right click the network manager icon and try to enable wireless?

---

### Post by AntoniusUno on 2010-03-22
Right clicking the network Manager still gives me a greyed out wireless option so I cannot turn it on. When I do Edit Connections I can setup the stuff for wireless but it just does not use it. 

Left clicking on the network manager tells me Wired network is enable, but wireless network is disabled. 

Will sudo apt-get install networkmanager help in this case?

Is there a way from command line to force the wireless to connect to the router?

How can I reinstall the proprietary driver? Can I just do remove and after it select it again from the menu option Hardware Drivers?

---

### Post by bkratz on 2010-03-22
> **AntoniusUno said:**
> Right clicking the network Manager still gives me a greyed out wireless option so I cannot turn it on. When I do Edit Connections I can setup the stuff for wireless but it just does not use it. 

Left clicking on the network manager tells me Wired network is enable, but wireless network is disabled. 

Will sudo apt-get install networkmanager help in this case?

Is there a way from command line to force the wireless to connect to the router?

From the discussion you already have network manager installed, I would look at the contents of 

```
rfkill list
```

and see if posts 3 to 5 of this thread apply.

[http://ubuntuforums.org/showthread.php?t=1414946&highlight=dell-laptop](http://ubuntuforums.org/showthread.php?t=1414946&highlight=dell-laptop)

---

### Post by AntoniusUno on 2010-03-22
rfkill list gives me:

> 
@ubuntu:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes


I will look into the other post and come back if any or no results.

---

### Post by bkratz on 2010-03-22
> **AntoniusUno said:**
> rfkill list gives me:



I will look into the other post and come back if any or no results.


Well I am probably wrong! , but I think the hardblock is referring to the switch itself, so either it is in the wrong state or not being read correctly.

---

### Post by bkratz on 2010-03-22
Here is a bug report that sure sounds familiar, it is about a different Dell Model, but it seems to apply.

[https://bugzilla.kernel.org/show_bug.cgi?id=14098](https://bugzilla.kernel.org/show_bug.cgi?id=14098)

and another similar thread

[http://ubuntuforums.org/showthread.php?t=1377829](http://ubuntuforums.org/showthread.php?t=1377829)

---

### Post by AntoniusUno on 2010-03-24
Just got added another problem, after updating I can't boot anymore. "Must load kernel first".

Nice... Have seen this bug report already but if ubuntu wants to become a usable os for the common people this kind of errors should not happen. It is too much work to get it up and running. Once running it is great and all but you have to persevere.

Will post more findings once tried.

---

### Post by coffeeaddict22 on 2010-03-25
Don't blame Ubuntu.  Hardware vendors produce cards, and then for some dumb reason won't let anyone access the info needed to write drivers for them; you can have any driver for a Broadcom card, so long as it's written by Broadcom.  
  
The Linux drivers are constantly improving, but while hardware vendors insist on selling us a chunk of metal without open sourcing the API to talk to it, drivers are a gamble on Linux.  

wrt your card, I know there were some HP models where there was a chip that held the card status, and was only accessible in Windows.  Boot into Win, and make sure your card is enabled.  Going by the other post, disabling dell-laptop or updating your BIOS would be a good plan too.

---

### Post by antonius uno on 2010-03-26
> **coffeeaddict22 said:**
> Don't blame Ubuntu.  Hardware vendors produce cards, and then for some dumb reason won't let anyone access the info needed to write drivers for them; you can have any driver for a Broadcom card, so long as it's written by Broadcom.  
  
The Linux drivers are constantly improving, but while hardware vendors insist on selling us a chunk of metal without open sourcing the API to talk to it, drivers are a gamble on Linux.  

wrt your card, I know there were some HP models where there was a chip that held the card status, and was only accessible in Windows.  Boot into Win, and make sure your card is enabled.  Going by the other post, disabling dell-laptop or updating your BIOS would be a good plan too.


Yep done that check already. I noticed that the wireless on/off key did not show any apparent signs of functioning in Ubuntu but did indeed turn off the wireless. Did make sure windows has wireless, but still ubuntu does not recognise it. I am very reluctant though to do a BIOS upgrade as I have very bad experience with that plus it worked first time I installed Karmic so there should not be a reason why it does not work now.

---

### Post by antonius uno on 2010-03-26
> **bkratz said:**
> Here is a bug report that sure sounds familiar, it is about a different Dell Model, but it seems to apply.

[https://bugzilla.kernel.org/show_bug.cgi?id=14098](https://bugzilla.kernel.org/show_bug.cgi?id=14098)

and another similar thread

[http://ubuntuforums.org/showthread.php?t=1377829](http://ubuntuforums.org/showthread.php?t=1377829)


YEP! Worked like a charm. Wireless is back on and working.:D
thanks you guys. Good support.

sudo rmmod -f dell_laptop was the solution.

---

### Post by coffeeaddict22 on 2010-03-26
And the sound?

---

### Post by AntoniusUno on 2010-03-27
> **coffeeaddict22 said:**
> And the sound?

As i said before the sound i tried fixing but messed up some other things. I got the advice to wait for next release unless any of you have more info

---

### Post by AntoniusUno on 2010-03-27
OK have to admit, without sound, Ubuntu cannot yet replace Windows 7. So I dive into this issue.

> **coffeeaddict22 said:**
> 
Sound is slightly more complicated at the moment, as I think it's changing in the Lucid (10.04) mix, so doing a whole heap of fiddling is probably a waste of time if you can wait a week for the beta.  If you want to play, start with the sound troubleshooter; in my experience the trick is to open alsamixer (type it in a terminal) and find what's been defaulted to a level of 0.

ALSAmixer shows all playback levels at max. Had checked that before when running through this post:
[[ubuntu] [HOWTO] Fix for Stuck Volume/Multimedia Keys - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=974723") 

Under sound preferences in the GUI I have two options for HW:
1. Analogue stereo duplex
2. R700 Audio device (Radeon HD4000 series)

Currently HW is set to #1. For analogue stereo HW I can also choose input/output/duplex. As far as I understand this option I want duplex because I want speakers and mic to function both (for skype etc).

On the input side I get a signal in the signalbars when testing the mic levels. But I don't hear anything.

So shoot....;)

---

### Post by bkratz on 2010-03-27
Since it is no longer a wireless issue, perhaps you should mark this as solved and repost the sound issues on the following

[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

I'm sure that you would get good advice there: that is their specialty.

---

### Post by AntoniusUno on 2010-03-27
sure thought about that already. Will mark this one as solved if you tell me how

---

### Post by bkratz on 2010-03-27
> **AntoniusUno said:**
> sure thought about that already. Will mark this one as solved if you tell me how

Sure, just go to the thread tools above and select [solved], only you can do it since it is your thread.

---

### Post by AntoniusUno on 2010-03-27
I get only 3 options but none of them say [solved]. Only talking about email to friend, show printable version and subsribe.

---

### Post by bcbc on 2010-03-27
> **AntoniusUno said:**
> I get only 3 options but none of them say [solved]. Only talking about email to friend, show printable version and subsribe.

You seem to be logging on with 2 separate accounts. One created in Feb 2009 and one in Mar 2010.  You'll need to be logged on with the one that started the thread to mark it as solved.

---

### Post by abhiram.g on 2011-08-16
the dell studio1558 has being problem with wifi is connecting
but it is dis conecting automatically some times it is not showing network conections

---

### Post by chanhteo on 2013-02-25
[sudo] password for "user": 
ERROR: Removing 'dell_laptop': No such file or directory

I got this message ...

---

### Post by howefield on 2013-02-25
Old thread closed.

Feel free to start a fresh one.

---

