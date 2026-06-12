---
title: "Difficulty Connecting to Wireless Network"
date: 2012-02-27
forum: Networking &amp; Wireless
---

### Post by CidNight on 2012-02-27
Hello everyone,

As you can tell I am brand new to the forums and as you will soon find out, brand new to Linux.  I recently installed Ubuntu and am attempting to connect to my wireless router, which is a NETGEAR WGR614 v.7.  When I attempt to connect to the network it just spins for a while, asks for my password, then spins for a while longer before asking for the password again.  This repeats endlessly.  From what I can tell, I may have a driver problem.  I downloaded the firmware (WGR614v9-V1.2.30_41.0.44NA.chk) on another computer and brought it over to this one using a thumb drive.  

My questions are these: How do I tell if this is a driver issue?  If it is, how might I install this firmware that I've gotten from NETGEAR or do I need something else?

I apologize if something similar to this was answered earlier, but I welcome any and all advice.  

Thanks again.

---

### Post by sadaruwan12 on 2012-02-27
Hi ! and welcome to the forum.

First of all run the below command in the terminal and post the out put here so we can have a clear idea.

To open the terminal press Ctrl + Alt + t

```
lspci
```

---

### Post by grahammechanical on 2012-02-27
If Ubuntu can see your wireless network or other wireless networks. Then you do not have a driver problem.

When you click on the network icon do you see a list of available networks? If so then you have a working wireless driver.

When you select your wireless network (the router that has the name of your ISP) to connect to and you are asked for a password, what password are you putting in?

Is it your log in password? If so then that is the wrong password. You need the pass phrase or wireless key for the router.

You may not have the correct encryption method. But network manager usually works that out for you. Are you using Network Manager to make the connection or are using editing the connection details yourself?

The router should have this information on a label stuck on it somewhere.

By the way, we do not need drivers for the router. Sometimes we need a driver for the wireless card/adapter in the computer. Often the wireless adapter is detected during the install of Ubuntu and the correct driver is installed as part of the operating system. This is especially true if we installed with a cable connection to the router.

Those times when we need to install a wireless driver or a video driver we use the Additional Drivers utility which will find a driver and activate it. We need a cable connection to the router for this to work.

Regards.

---

### Post by CidNight on 2012-02-27
Thank you for the helpful and timely replies!  Actually, I managed to solve the problem.  What I did was reset my router to factory settings, then reinstalled it and used security settings that seemed more in line with Linux.  After doing this, I configured the network in Ubuntu to the correct settings, entered the passphrase - et voila!  So you were right, it was not a driver problem but a security settings problem, I guess.  This would seem to explain why Ubuntu would repeatedly ask me for the router's passphrase even while it was successfully detecting the router.

---

### Post by CidNight on 2012-02-28
Hi again everyone,

Looks like I was wrong.  Connection to the network went on without a hitch until I turned the comp off and back on this evening.  After the reboot, it was right back to where it started; which is to say continuously spinning and asking for my pass phrase over and over again while trying to connect to the wireless network.  I am recognizing my network just fine, it just fails to connect to it - seemingly because of some sort of issue with the pass phrase.  

So, changing my connection and security settings doesn't seem to have helped.  Apparently the connection I got last night was a fluke.  Anyone have any other ideas?  Here is the output that was asked for last night, any help at all would be very very appreciated!

 00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
    00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
    00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
    00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
    00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
    00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
    00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
    00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
    00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
    00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
    00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
    00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
    00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
    00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
    00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
    00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    01:09.0 Network controller: Ralink corp. RT2760 Wireless 802.11n 1T/2R Cardbus
    [FONT=&quot]04:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GT] (rev a1)[/FONT]

To clear up some previous questions:

*Is it your log in password? If so then that is the wrong password. You need the pass phrase or wireless key for the router.*

I am using the passphrase for my network, not my password for logging onto the OS.

*You may not have the correct encryption method. But network manager  usually works that out for you. Are you using Network Manager to make  the connection or are using editing the connection details yourself?*

I guess I am using the network manager, because I have not tried to edit anything myself.

---

### Post by CidNight on 2012-02-28
Here is info about the router and network:

Netgear 54MBPS WGR614 v.7
Security Type: WPA2-PSK
Connection Type: DHCP
Dynamic IP

Some of my ignorance is showing as I must admit that some of this means nothing to me.

---

### Post by CidNight on 2012-02-28
[http://ubuntuforums.org/showthread.php?t=1932665](http://ubuntuforums.org/showthread.php?t=1932665)

Hi everyone,

I posted this thread yesterday in the beginner forum before I saw this subforum that seemed quite a bit more appropriate.  Hope this sort of link is allowed.  Any help would be greatly, greatly appreciated!

---

### Post by clausrei on 2012-02-29
> 
Netgear 54MBPS WGR614 v.7
This is your Adapter.

> 
Security Type: WPA2-PSK
This is the type of  encryption used. ( [more here]("http://www.webopedia.com/TERM/W/WPA2_PSK.html") )

> 
Connection Type: DHCP
Dynamic IP
This is the Protocol used to assign your IP address. Which in this case is changing with every new session. It is the most common in use Protocol (Dynamic Host Configuration Protocol).

Nothing unusual until here or mis configured until now.

---

### Post by CidNight on 2012-02-29
> **clausrei said:**
> This is your Adapter.

This is the type of  encryption used. ( [more here]("http://www.webopedia.com/TERM/W/WPA2_PSK.html") )

This is the Protocol used to assign your IP address. Which in this case is changing with every new session. It is the most common in use Protocol (Dynamic Host Configuration Protocol).

Nothing unusual until here or mis configured until now.

Thanks for the info, especially about the encryption type - that was very informative.  But nothing here looks amiss that might be causing the issue?

---

### Post by CidNight on 2012-02-29
I'm reading quite a bit about ndiswrapper as a method for solving problems similar to mine, but it looks like it is mostly useful when you are unable to detect the network at all.  Since I can detect the network but cannot successfully connect to it, is there another method that can be helpful?

---

### Post by CidNight on 2012-02-29
An update: I tried, moments ago, to turn off the security settings on my network - still no luck.  Just spins without connecting, but now without asking for a security pass phrase.  So Maybe it isn't security?

Any ideas?

---

### Post by varunendra on 2012-03-01
CidNight,

I am quoting here the output part of your post in [this thread]("http://ubuntuforums.org/showthread.php?p=11728965#post11728965") for others to see:
```
bill@bill-MS-7325:~$ lsb_release -d
Description:    Ubuntu 11.10

bill@bill-MS-7325:~$ uname -mr
3.0.0-16-generic-pae i686

bill@bill-MS-7325:~$ lspci -nnk | grep -iA2 net
00:0a.0 Bridge [0680]: nVidia Corporation CK804 Ethernet Controller [10de:0057] (rev f3)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7325]
    Kernel driver in use: forcedeth
--
01:09.0 Network controller [0280]: **Ralink corp. RT2760 Wireless 802.11n 1T/2R Cardbus [1814:0701]**
    Subsystem: Ralink corp. RT2760 Wireless 802.11n 1T/2R Cardbus [1814:0701]
    Kernel driver in use: **rt2800pci**

bill@bill-MS-7325:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse

bill@bill-MS-7325:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
vesafb                 13489  1 
binfmt_misc            17292  1 
nvidia               7098131  34 
ppdev                  12849  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
rt2800pci              18340  0 
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48146  3 rt2800pci,rt2800lib,rt2x00pci
parport_pc             32114  1 
mac80211              393421  3 rt2800lib,rt2x00pci,rt2x00lib
psmouse                63474  0 
serio_raw              12990  0 
cfg80211              172427  2 rt2x00lib,mac80211
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
eeprom_93cx6           12653  1 rt2800pci
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,sn  d_seq,snd_timer,snd_seq_device
k8temp                 12905  0 
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
forcedeth              58103  0 
sata_nv                23379  2 
pata_amd               13753  0 

bill@bill-MS-7325:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:db:23:ea:27  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9920 (9.9 KB)  TX bytes:9920 (9.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:02:6f:69:c8:e6  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:6fff:fe69:c8e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14673 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14856096 (14.8 MB)  TX bytes:2928593 (2.9 MB)


bill@bill-MS-7325:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Quechee"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:2A:78:B0:A8   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:33  Invalid misc:98   Missed beacon:0


bill@bill-MS-7325:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


bill@bill-MS-7325:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```I would suggest to try the driver downloaded directly from Ralink's site, which is apparently most stable with this card.

Just to make sure you have everything required to build the driver is preinstalled, run these commands while you are connected to internet via cable:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```(it would reinstall the headers, build-essential and dkms packages even if they are already installed)

Then download the rt2860sta driver from here: [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)
(You can also download the firmware from above link if required, although I see it already exists in /lib/firmware directory in 11.10, so shouldn't be required.)

Afterwards, follow this guide to build and install the driver: [http://michael-peeters.blogspot.in/2011/06/fixing-rt2860-wifi-chipset-under-ubuntu.html](http://michael-peeters.blogspot.in/2011/06/fixing-rt2860-wifi-chipset-under-ubuntu.html)
(it is written for RT2860 chip, but would be same for your card).
The download link in the above linked guide is broken, the correct one is what I have provided above.

Let's hope it works for you as it has for many others.

---

### Post by varunendra on 2012-03-01
You can always request the mods to move your threads/posts to a suitable section by using the "Report Abuse" button.

Don't mind what it says, it can be used for anything that requires mods/admins' attention.

It'll be better to move that thread to this section instead, and close this one to avoid dilution of efforts. I'm going to request that for you.

---

### Post by sffvba[e0rt on 2012-03-01
Threads merged into the relevant section...


404

---

### Post by CidNight on 2012-03-01
> **not found said:**
> Threads merged into the relevant section...


404
Thanks for the merge.

Trying the fix now, will let you know how it comes out.

---

### Post by CidNight on 2012-03-01
Well I went through most of the process and many of the steps seemingly worked - but my problem seems to arise right at step one: extracting the tar file.  I downloaded the appropriate file (RT2860PCI...) from Ralink and placed it in my home directory, but when I attempt to extract it I get this error message:

"An error occurred while loading the archive.

bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error is not recoverable: exiting now

I think this leads to my terminal not being able to find certain files and directory in later stages of the fix which leads to the process failing.  During step 5, for example, this command fails because the terminal states that there is no such file or directory:

sudo mv /lib/modules/$(uname -r)/kernel/drivers/staging/rt2860/rt2860sta.ko /lib/modules/$(un

Any ideas?

---

### Post by varunendra on 2012-03-01
> **CidNight said:**
> ..but my problem seems to arise right at step one: extracting the tar file.  I downloaded the appropriate file (RT2860PCI...) from Ralink and placed it in my home directory, but when I attempt to extract it I get this error message:

"An error occurred while loading the archive.

bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error is not recoverable: exiting now
What is the exact command you are using to extract the files? As the linked guide suggests, the extension name (bz2) is misleading, and hence if you are trying to extract it via GUI (double-click > extract, or right-click > extract here), it would return the error you got. So please try the command:
```
tar -xvf ~/2010*
``` while you are in the same directory as the downloaded archive. The GUI method would also work correctly if you simply remove the".bz2" part from its name (so it becomes only ".tar")

If the above command fails, then you almost certainly have a broken archive. Try re-downloading it.

---

### Post by CidNight on 2012-03-04
> **varunendra said:**
> The GUI method would also work correctly if you simply remove the".bz2" part from its name (so it becomes only ".tar")


Alright, I did this and then ran through the steps again and it seems like I've got a strong connection.  I even put security settings back up, and successfully reconnected.  Going to try a reboot now and see how that goes.

Seems like it worked though!

---

### Post by CidNight on 2012-03-04
Success!  I'm going to set this to solved now.

---

### Post by lisanels47 on 2012-03-04
If possible, setup your WiFi for OPEN mode and see if it connects reliably that way.  You can put MAC filtering on for a bit to help with the security. 

Then when you are convinced that it's working well, change to WPA-PSK mode If available.  I know some devices I had did not support WPA2-PSK, but worked fine with WPA-PSK.

Also on the router; some give you the choice of AES or TKIP.  AES is better, but try both.

---

### Post by CidNight on 2012-03-04
> **lisanels47 said:**
> If possible, setup your WiFi for OPEN mode and see if it connects reliably that way.  You can put MAC filtering on for a bit to help with the security. 

Then when you are convinced that it's working well, change to WPA-PSK mode If available.  I know some devices I had did not support WPA2-PSK, but worked fine with WPA-PSK.

Also on the router; some give you the choice of AES or TKIP.  AES is better, but try both.


Right now I'm on WPA2-PSK TKIP and seem to be connecting very reliably.  I had it set to open while working on the problem but once I got a reliable connection I switched WPA2 back on and had no problems connecting.  So far, it seems to be working well.  But if it starts to act up again, I will try switching to AES or MAC filtering and see if that improves the situation.

---

### Post by varunendra on 2012-03-05
> **CidNight said:**
> Success!
^ the sweetest word in the entire world! :)

Hope it stays that way. But if not, we'd be keen to dig more! Thanks for the feedback.

---

