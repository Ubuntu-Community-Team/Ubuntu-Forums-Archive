---
title: "WNDA3100 Wireless Adapter Issue"
date: 2012-06-15
forum: Networking &amp; Wireless
---

### Post by Relinies on 2012-06-15
Okay, so according to the list here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear) the given adapter (2nd from very bottom) is listed as supported in Karmic, 9.10. I understand this doesn't necessarily mean it's going to work anymore, but I've got to try. So, I have installed the Driver with ndiswrapper already, and I've gotten the light to turn on, but i'm not sure whether it will be automatic from there or if I could do anything. 
I'll have the information you guys might need (lsusb iwconfig ndiswrapper -l and some others) in just a few minutes

EDIT: Okay, here we go
```
relinies@Relinies-Ubuntu:~$ cat /etc/lsb-release; uname -aDISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux Relinies-Ubuntu 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

relinies@Relinies-Ubuntu:~$ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP77 Ethernet [10de:0760] (rev a2)
	Subsystem: Hewlett-Packard Company Device [103c:2a9e]
	Kernel driver in use: forcedeth

relinies@Relinies-Ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f2:0841 Chicony Electronics Co., Ltd 
Bus 003 Device 003: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 004: ID 050d:615a Belkin Components F7D4101 / F9L1101 802.11abgn Wireless Adapter [Broadcom BCM4323]
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer

relinies@Relinies-Ubuntu:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.

relinies@Relinies-Ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
bnep                   18281  2 
snd_hda_codec_realtek   223867  1 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
joydev                 17693  0 
usbhid                 47199  0 
hid                    99559  1 usbhid
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
nouveau               774571  3 
ttm                    76949  1 nouveau
drm_kms_helper         46978  1 nouveau
drm                   242038  5 nouveau,ttm,drm_kms_helper
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13423  1 nouveau
k10temp                13166  0 
mxm_wmi                12979  1 nouveau
edac_core              53746  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
edac_mce_amd           23709  0 
psmouse                87603  0 
serio_raw              13211  0 
video                  19596  1 nouveau
wmi                    19256  1 mxm_wmi
mac_hid                13253  0 
i2c_nforce2            13058  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49198  1 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
forcedeth              63460  0 

relinies@Relinies-Ubuntu:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
	device (050D:615A) present

```

---

### Post by chili555 on 2012-06-15
It is doubtful you'll ever get this going in a 64-bit system. Nonetheless, let's see if there are any interesting clues:```
dmesg | grep ndis
```

---

### Post by Relinies on 2012-06-15
Wow, didn't expect a reply from you. You seem to be the big authority in this area.

I typed the command in, it did nothing whatsoever. Just went straight to the next line, no other output. Closing the terminal didn't bring up any warning about running processes.

---

### Post by chili555 on 2012-06-15
Please try a slightly more complex sequence:```
sudo modprobe ndiswrapper 
dmesg | grep ndis
```Thank you for your kind comments.

---

### Post by Relinies on 2012-06-15
Both of them as one command or as two seperate ones?

---

### Post by chili555 on 2012-06-15
Do the first, press Enter and note any errors or warnings. There may be none. Then do the second and press Enter. Note any output and post it here.

---

### Post by Relinies on 2012-06-15
```
relinies@Relinies-Ubuntu:~$ sudo modprobe ndiswrapper
relinies@Relinies-Ubuntu:~$ dmesg | grep ndis
[   45.007466] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   45.059028] usbcore: registered new interface driver ndiswrapper
[  112.453946] ndiswrapper: driver bcmwlhigh5 (Belkin International, Inc.,02/17/2011, 5.60.180.11) loaded
```


I have NO idea what was different, but sudo modprobe ndiswrapper is a command i've used before, and it's always failed. It never moved on to a new line for typing a command, instead kinda glitched out and made symbols like: ]> for arrow keys and etc.
But it worked.

---

### Post by chili555 on 2012-06-15
It looks pretty normal. Let's load it on boot automatically.```
sudo su
echo ndiswrapper >> /etc/modules
exit
iwconfig
```Can you connect?

---

### Post by Relinies on 2012-06-15
I still can't connect, but the given commands brought on two changes. First: The bright green light on the adapter was replaced with two dim lights, one green one orange. One is the indicator that it works, the other shows a padlock and I assume it indicated the use of a protected network. The second can be seen in the log, the new wlan0 listing.
I don't think that's right.

The log: 
```
relinies@Relinies-Ubuntu:~$ sudo su
[sudo] password for relinies: 
root@Relinies-Ubuntu:/home/relinies# echo ndiswrapper >> /etc/modules
root@Relinies-Ubuntu:/home/relinies# exit
exit
relinies@Relinies-Ubuntu:~$ iwconfig
lo        no wireless extensions.
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
eth0      no wireless extensions.
```

---

### Post by chili555 on 2012-06-15
> I still can't connect,That's the frequent behavior for your driver bcmwlhigh5.inf on 64-bit; everything looks perfect but it won't actually connect. Does it scan?```
sudo iwlist wlan0 scan
```

You might try turning N speeds and encryption off in the router, momentarily, of course. We might learn something helpful if we isolate what is and isn't working: N? WPA2? WPA? etc.

It certainly looks close.

---

### Post by Relinies on 2012-06-15
If that's the usual behaviour in 64 bit, is there an alternative that works in 64 bit? I suppose there isn't, since there wasn't any other on the disc.

I'll edit this post with the results in a moment, but I won't be able to turn off encryption or N speeds. I'm not the only one using the router, i'm afraid.
Boom:
```
relinies@Relinies-Ubuntu:~$ sudo iwlist wlan0 scan
[sudo] password for relinies: 
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:B3:38:69:A9
                    ESSID:"2WIRE320"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00083257495245333230
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0103
                    IE: Unknown: 32043048606C
          Cell 02 - Address: 00:14:A5:8B:A7:F7
                    ESSID:"schroeder"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0009736368726F65646572
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD050010180101
          Cell 03 - Address: 00:22:A4:8A:6A:99
                    ESSID:"2WIRE093"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Quality:20/100  Signal level:-83 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00083257495245303933
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 050400010100
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 04 - Address: B8:E6:25:39:65:41
                    ESSID:"mimi04"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00066D696D693034
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 05 - Address: 00:1D:5A:BD:62:D1
                    ESSID:"2WIRE881"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00083257495245383831
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 06 - Address: 00:14:BF:CD:86:4B
                    ESSID:"spindlk2"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00087370696E646C6B32
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F0
          Cell 07 - Address: 00:24:56:B3:25:59
                    ESSID:"2WIRE522"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00083257495245353232
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030109
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
```


So it detects each and every wireless network my usual one does, but the built in program in Ubuntu doesn't see it. What do I do?

---

### Post by Relinies on 2012-06-15
I understand I can't expect instant replies, but it's been over an hour and i've got to go soon.

---

### Post by nothingspecial on 2012-06-16
Please do not bump your thread more than once every 24 hours or so.

---

### Post by chili555 on 2012-06-16
> So it detects each and every wireless network my usual one does, but the built in program in Ubuntu doesn't see it. I'm not sure I understand. Are you saying that when you click the Network Manager icon at the top right that you do *not* see any networks? If you do see your network, can you click it and try to connect? What happens if you do?> I understand I can't expect instant replies, but it's been over an hour and i've got to go soon. Sadly, at least once a day, I sleep.

---

### Post by Relinies on 2012-06-16
Haha, of course

I'm saying that the network manager isn't showing ANYTHING at all, but the command you gave seems to detect every network as normal. How can I connect to them?

---

### Post by chili555 on 2012-06-16
Please do:```
sudo gedit /etc/network/interfaces
```Make sure it only includes:```
auto lo
iface lo inet loopback
```If there is anything more in there, please remove it, proofread, save and close gedit. Now do:```
sudo gedit /etc/NetworkManager/NetworkManager.conf
```Make sure the line is managed=true. If not, change it, proofread, save and close gedit. Now do:```
sudo service network-manager restart
```Now do networks appear?

---

### Post by Relinies on 2012-06-16
It worked! I'm connected on my Ubuntu partition! Thank you so much, chili!
How do I switch the tag to Solved, or does a mod do that for me?

---

### Post by chili555 on 2012-06-16
You use thread tools at the top to mark Solved. As far as I know, you are the only 64-bit and bcmwlhigh5.inf case that actually works! Welcome to the new frontier!

Are all the steps you undertook mentioned in this thread? The searchers and I will be grateful for the exact details.

---

### Post by Relinies on 2012-06-16
> **chili555 said:**
> You use thread tools at the top to mark Solved. As far as I know, you are the only 64-bit and bcmwlhigh5.inf case that actually works! Welcome to the new frontier!

Are all the steps you undertook mentioned in this thread? The searchers and I will be grateful for the exact details.

All the steps I took are here, apart from installing the driver via normal ndiswrapper methods.
Placing the driver on the desktop, using CD to target it, sudo ndiswrapper -i drivername.inf. I'd have to go read the name of the driver, cause I'd never remember it off the bat.

---

### Post by chili555 on 2012-06-16
I'm sure it's bcmwlhigh5.inf and you used the Windows ***XP*** 64-bit version from th CD?

---

### Post by Relinies on 2012-06-16
You would be correct, except for the fact that there was only one .inf file. All the other files had alternatives in 64 bit. I don't know how ndiswrapper works, so I can't be sure what it did with the other files, or if it did anything at all with them.

---

### Post by chili555 on 2012-06-16
It depends on the specific chipset but bcmwlhigh5.inf does require and use other files. ndiswrapper takes care of this automagically with no input on your part. You can see what else it needed here:```
ls /etc/ndiswrapper/bcmwlhigh5/
```

---

### Post by Relinies on 2012-06-16
> **chili555 said:**
> It depends on the specific chipset but bcmwlhigh5.inf does require and use other files. ndiswrapper takes care of this automagically with no input on your part. You can see what else it needed here:```
ls /etc/ndiswrapper/bcmwlhigh5/
```

This:
```
relinies@Relinies-Ubuntu:~$ ls /etc/ndiswrapper/bcmwlhigh5/
050D:6050.F.conf  050D:825C.F.conf  bcmwlhigh5.inf
050D:615A.F.conf  bcmwlhigh564.sys

```
so it only needed two files. Cool

---

### Post by chili555 on 2012-06-16
> relinies@Relinies-Ubuntu:~$ ls /etc/ndiswrapper/bcmwlhigh5/
050D:6050.F.conf  050D:825C.F.conf  [COLOR="Red"]bcmwlhigh5.inf[/COLOR]
050D:615A.F.conf  [COLOR="Red"]bcmwlhigh564.sys[/COLOR]Exactly. The searchers will need those two in the same directory and will hopefully be successful. Thanks for the additional assistance.

---

### Post by Relinies on 2012-06-16
No, thank you! I could never have done this myself, and it's not like a guide for this exists elsewhere.

---

### Post by hidden0 on 2012-12-01
Greetings!  This is my first time posting in the Ubuntu help forums.  Typically, I can solve my problems after reading around the web a bit.  Unfortunately, my issue seems to be either unique or of a different nature than I am aware of.

I followed the details in this thread in order to get my WNDA3100 v2 wireless adapter working in Ubuntu 12.10 64-bit.  Actually, I had no problems getting the drivers installed with ndiswrapper and loading the module.  Wireless connectivity worked immediately.

Now I am facing an issue with the stability of the connection.  Sometimes, as in the case right now, I have extended use of the connection.  At other times, it will stop functioning all together, and it can happen frequently or rarely.

It is interesting, because my system tells me I am still connected to a wireless network during all of this.  Restarting connections/network manager/services do not seem to fix the issue.

What DOES fix the issue is unplugging the device and plugging it back in.  I have to do this more frequently when using multiple applications that connect to the internet.  If I am only on my web browser, it will do it rarely.  If I open ubuntu software center and install something, it stops working after about 1 MB is transferred.  Same with other applications (Steam, Mumble).

I'm open to any suggestions. I even tried to write a script that would essentially power down the USB port and force a re-enumeration of the device, but I could not make the script work...and this would be a poor fix.  Any ideas?

Thank you!
New Ubuntu User

---

### Post by chili555 on 2012-12-01
A Windows driver in a Linux wrapper, also known as ndiswrapper, is always a dicey proposition. 64-bit even more so. You might try reloading ndiswrapper:```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```You might survey the logs for clues:```
cat /var/log/syslog | grep -e ndis -e etwork
```You might install 32-bit or at least try it on a live CD to see if it helps. Finally, you might retire it. Drastic suggestions, I know.

---

### Post by hidden0 on 2012-12-01
Thank you for your quick reply!

I have been troubleshooting this for a while now.  I have tried quite a number of methods to get this working, including removing the ndiswrapper module and placing it back in.

The commands you listed above execute without error.  When ndiswrapper is reloaded, the options to connect to a wireless interface do not appear.  It is not until I disconnect the usb device physically, then reconnect it, that it works.

I decided I would actively "break" the wireless by initiating a large download, whilst simultaneously running a constant ping to my gateway device (192.168.1.1)

I receive the message "ping: sendmsg: No buffer space available"

I think I'm going to try ubuntu 12.10 32-bit this time around.....unless the buffer space message gives anyone else a clue.

---

### Post by chili555 on 2012-12-01
I suggest you try the live CD. ndiswrapper in on the CD and you can transfer the .inf and .sys files on a USB key. Then you can see if it works reliably before you install.> unless the buffer space message gives anyone else a clue. It means nothing to me.

---

### Post by hidden0 on 2012-12-02
The same problem persists in 32-bit architecture.  The nature of the problem is identical.  I am thinking of simply buying wireless USB stick that is natively supported by the distribution.

Does ubuntu 12.10 64-bit have a supported hardware listing online somewhere? I have been unable to find which wireless dongles would be natively supported and which ones require ndiswrapper.

Thanks for your assistance Chili.  A coworker and I were thinking the buffer message had something to do with a memory leak eating up all the buffer space, or the stack was not getting flushed out every time it was read.  In both cases, the stack ends up full and is much like old DDOS attacks in which your buffer is filled to the point it rejects incoming packets.

---

### Post by chili555 on 2012-12-02
> Does ubuntu 12.10 64-bit have a supported hardware listing online somewhere? I have been unable to find which wireless dongles would be natively supported and which ones require ndiswrapper.You might check here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Also, there are many questions on this forum about 'works out of the box USB dongle.' [http://ubuntuforums.org/showthread.php?t=2048914&highlight=usb+dongle](http://ubuntuforums.org/showthread.php?t=2048914&highlight=usb+dongle) for example.

I'm sorry I could not have been more help.

---

### Post by hidden0 on 2012-12-02
No Chili you have helped a great deal!  I appreciate your quick responses and outside viewpoint on the matter.

I am still trying some things such as (painstakingly) updating my system's linux headers to the latest release. Perhaps some mundane bug was fixed that solves the problem.

Thank you for the links, this was precisely what I was looking for.  Sometimes I fail at google :)

Have a good day Chili!  I'll be sure to be posting around here when I run into more issues.

---

