---
title: "HP Mini wireless is hard blocked"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by relmoyd on 2011-06-30
One day while waiting to board an aeroplane I pressed Fn <F12> which I believe is the wireless switch and wireless has not worked since.  I am running Ubuntu 11.04 on an HP Mini 110-3500.  I have not been able to unblock or use wireless.



[FONT=Comic Sans MS][FONT=Courier New]$ lspci -nn | grep 14e4
01:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 3c:4a:92:c6:45:90  
          inet addr:10.0.4.247  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::3e4a:92ff:fec6:4590/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:136687 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14843 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26901763 (26.9 MB)  TX bytes:2643422 (2.6 MB)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

$ rfkill list
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
$ sudo rfkill unblock all
$ rfkill list
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

After pressing Fn <F12>:
$ rfkill list
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 88:9f:fa:7a:9d:ec
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:55000000-55003fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 3c:4a:92:c6:45:90
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.0.4.247 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:1000(size=256) memory:52004000-52004fff memory:52000000-52003fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

dpkg -l contains:
ii  bcmwl-kernel-source        5.100.82.38+bdcom-0ubuntu3   Broadcom 802.11 Linux STA wireless driver source
ii  b43-fwcutter               1:013-3                      Utility for extracting Broadcom 43xx firmware
ii  firmware-b43-installer     4.150.10.5-5                 Installer package for firmware for the b43 driver

$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
binfmt_misc            13213  1 
snd_rawmidi            25269  1 snd_seq_midi
i915                  450944  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
uvcvideo               66851  0 
lib80211_crypt_tkip    17203  0 
snd_timer              28659  2 snd_pcm,snd_seq
wl                   2642531  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
psmouse                73312  0 
videodev               75143  1 uvcvideo
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   180037  3 i915,drm_kms_helper
serio_raw              12990  0 
joydev                 17322  0 
i2c_algo_bit           13184  1 i915
lib80211               14570  2 lib80211_crypt_tkip,wl
video                  18951  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  2 
libahci                25548  1 ahci
r8169                  42534  0 

$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument[/FONT]

[/FONT]

---

### Post by chili555 on 2011-06-30
Will you try an experiment for me? In a terminal, do:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```Any improvement?

---

### Post by relmoyd on 2011-06-30
No improvement:
[FONT=Courier New]
$ sudo rmmod -f hp-wmi
$ sudo rfkill unblock all
$ rfkill list all
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes[/FONT]

---

### Post by chili555 on 2011-06-30
With hp-wmi removed, does the Fn+F12 key now respond to key presses?

---

### Post by relmoyd on 2011-06-30
No, Fn+F12 does not change blocking:

[FONT=Courier New]rfkill list all
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
[/FONT]

---

### Post by amahi on 2011-06-30
hi,

[]("http://ubuntuforums.org/sudo%20rm%20/var/lib/NetworkManager/NetworkManager.state")> [LEFT]sudo rm /var/lib/NetworkManager/NetworkManager.state[/LEFT]


then reset.

---

### Post by relmoyd on 2011-06-30
How do I "reset"?

---

### Post by chili555 on 2011-06-30
I think you may have one or two problems here. One is the support for rfkill in the wireless driver module. Please see posts #21-23 here: [http://ubuntuforums.org/showthread.php?t=1753072&page=3](http://ubuntuforums.org/showthread.php?t=1753072&page=3)> In the case of Broadcom STA I figured out that according to [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt) the driver itself might not have support for rfkill in kernel 2.6.38? **I'm unable to rfkill unblock the device due to its "Hard blocked: yes" status** as said in #1.The other problem might be the module hp-wmi. Laptops require a small module to translate key presses, primarily Function keys, to useful information, such as, "Please turn on the wireless, Mr. Kernel." Here is a very interesting post: [http://ubuntuforums.org/showpost.php?p=10026302&postcount=20](http://ubuntuforums.org/showpost.php?p=10026302&postcount=20) The gist is that hp-wmi does, indeed, translate keypresses to action, but may be mapped to the wrong key. I suggest you try reloading hp-wmi:```
sudo modprobe hp-wmi
```Next, try the other Function combinations to see if 'hard blocked' changes to no. You can recall the previous terminal command with the Up arrow; keep trying:```
rfkill list all
```I love a mystery.

---

### Post by relmoyd on 2011-06-30
It looks like it is Alt+F12; the wireless indicator changed.

---

### Post by relmoyd on 2011-06-30
... and it looks like I can connect.

Thank you very much.

---

### Post by chili555 on 2011-06-30
Awesome! There are a few hp-wmi problems on this forum and others. You have helped a great many searchers and me.

[SIZE="3"]**Alt**+F12[/SIZE]

NOTE TO HP LAPTOP OWNERS: The key combination may not be Alt+F12 on each and every HP model. It is up to you to experiment until you find it. We'd appreciate it if you'd post your HP model number and the key combination that worked for you.

---

### Post by relmoyd on 2011-06-30
On rebooting, I find that this works without removing hp-wmi.

---

### Post by relmoyd on 2011-06-30
It's a pleasure to be a part of the solution.

---

### Post by amahi on 2011-07-01
>  NOTE TO HP LAPTOP OWNERS: The key combination may not be Alt+F12 on each  and every HP model. It is up to you to experiment until you find it.  We'd appreciate it if you'd post your HP model number and the key  combination that worked for you. 	   


I think this link will help. 

[COLOR=Red]View a list of keys[/COLOR][COLOR=Red]:[/COLOR]

[http://forums.speedguide.net/showthread.php?214308-How-to-turn-on-off-Wireless-in-various-Laptop-Models](http://forums.speedguide.net/showthread.php?214308-How-to-turn-on-off-Wireless-in-various-Laptop-Models)

;)

---

### Post by memors on 2011-07-18
this does not work with my HP Mini 100e 

friends helpme pleaseee! :C :C :C :C

---

### Post by memors on 2011-07-18
help me guys :C

---

### Post by chili555 on 2011-07-18
> **memors said:**
> this does not work with my HP Mini 100e 

friends helpme pleaseee! :C :C :C :CMay we see some details? Please open a terminal and run and post:```
lspci -nn | grep 0280
iwconfig
rfkill list all
```Thanks.

---

### Post by amahi on 2011-07-18
memors:


> this does not work with my HP Mini 100e 

friends helpme pleaseee! :C :C :C :C 

What you mean? 

More information is needed.

---

### Post by spin415 on 2011-07-24
I have the same problem but none of my fn + fwhatever keys are wifi. I also just re-formatted my drive, if that helps.

---

### Post by chili555 on 2011-07-24
> **spin415 said:**
> I have the same problem but none of my fn + fwhatever keys are wifi. I also just re-formatted my drive, if that helps.Which key *does* enable/disable the wireless? What does this tell us?```
rfkill list all
```

---

### Post by spin415 on 2011-07-24
Output:
1: phy0: Wireless LAN
              Soft blocked: yes
              Hard blocked: yes
3: hp-wifi: Wireless LAN
              Soft blocked: yes
              Hard blocked: no


Sorry, no connection on my laptop so I typed the results on my android. Don't worry though tripple checked. 

This is the output of; rfkill list all 
With the wireless switched on with no blue led

---

### Post by chili555 on 2011-07-24
Please try this sequence:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```Thanks.

---

### Post by spin415 on 2011-07-24
1: phy0: Wireless LAN
              Soft blocked: no
              Hard blocked: yes

The results look the same with the hardware switch on and off.
Thanks for the quick replies, by the way.

---

### Post by chili555 on 2011-07-24
I'm not sure I have any other suggestions if you've tried every other Fn, Alt and Ctrl key with F1 all the way to F12 and found no way to unblock the wireless.

---

### Post by spin415 on 2011-07-24
Should I just chalk it up to a bad copy of Ubuntu, and start over?

---

### Post by chili555 on 2011-07-24
That's a possibility. If you still have the install disk, can you run it live and see?

---

### Post by ST_ on 2011-09-22
Thanks!  

The following worked on my HP Mini 2133 running 10.10 UNR, but the hard block returns every time I boot up...

```

sudo rmmod -f hp-wmi 
sudo rfkill unblock all 
rfkill list all

```Any suggestions for a permanent fix (preferably without upgrading to Natty)?

---

### Post by chili555 on 2011-09-22
Please try:```
sudo su
echo "blacklist hp-wmi" >> /etc/modprobe.d/blacklist.conf
gedit /etc/rc.local
```Add a line above exit 0:```
rfkill unblock all
```Proofread, save and close gedit.```
exit
```Reboot and you should be all set.

---

### Post by ST_ on 2011-09-25
The edits to /etc/microprobe.d/blacklist.conf and /etc/rc.local worked perfectly.

Thanks again!

---

