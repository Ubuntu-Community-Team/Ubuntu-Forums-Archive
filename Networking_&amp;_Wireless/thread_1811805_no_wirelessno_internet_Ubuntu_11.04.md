---
title: "no wireless/no internet Ubuntu 11.04"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by KrisB on 2011-07-25
Hi,

Hoping someone will help me.  I have used a few versions of Ubuntu and never had a problem before I tried "Natty".  I have _**very**_ little knowledge of how to use command line other than what I can copy/paste so please bear with me, ok?  I upgraded to 11.04 and it never booted right again, resorted to starting with a fresh HDD.  Installed on the new drive and all went well this time with the exception of the wireless kept losing the connection.  (had never been an issue with previous installs of any kind).  So I went to the forums and found many people saying how network manager was often dropping connections and that Wicd worked much better.  Also repeatedly read that it didn't work right until the NM was uninstalled.  So I tried it.  Wicd installed but never connected and I kept getting "d-bus" error.  Tried to read on how to fix it but the solutions were either way over my head or involved software I didn't have.  So currently I have no internet b/c I have no wired connection (I live w/ family and can't run a wired connection) But I have access to another computer and a pendrive so I then tried to install wifi radar hoping that would at least get me online.  I seem to keep running into errors.  My system is a custom built desktop w/ an Asus mobo.  I just read the sticky on how to get all the info regarding the specifics so I'll attach it but it's loooong.  I also copied the errors I got trying to install both wicd and wifi radar in hopes that someone can get me online without having to reintall my os all over again.  Anyone please? 

Thanks in advance!

Kris

---

### Post by wildmanne39 on 2011-07-25
Hi, please run these commands in a terminal
```
sudo lshw -C network
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
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

I looked at the attached files but please run them and include the new commands I gave you and post them here so it is easier for us to read and have all the information in one place.
Thank you

---

### Post by KrisB on 2011-07-25
Ok I will- one silly question first- the line between nn and grep- how do I get that? I don't see a line like that on my keyboard anywhere! :confused:

Thanks!

---

### Post by nm_geo on 2011-07-25
Just copy and paste that way no typos   ... The upper right with slash.. shift | it is called pipe

---

### Post by wildmanne39 on 2011-07-25
Deleted.

---

### Post by nm_geo on 2011-07-25
> **wildmanne39 said:**
> Deleted.

You type too slow wildmanne :P

---

### Post by KrisB on 2011-07-25
ok googled it and got it, lol, thanks!  Here's the info:


```
*-network                        description: Ethernet interface  
        product: RTL8111/8168B PCI Express Gigabit Ethernet controller  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: eth0  
        version: 03  
        serial: e0:cb:4e:ff:91:21  
        size: 10Mbit/s  
        capacity: 1Gbit/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s  
        resources: irq:41 ioport:d800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:feaf0000-feafffff  
   *-network  
        description: Wireless interface  
        product: RT2561/RT61 802.11g PCI 
        vendor: Ralink corp.  
        physical id: 5  
        bus info: pci@0000:03:05.0  
        logical name: wlan0  
        version: 00  
        serial: 00:1e:e5:fd:36:9a  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=rt61pci driverversion=2.6.38-10-generic-pae firmware=0.8 latency=64 link=no multicast=yes wireless=IEEE 802.11bg  
        resources: irq:20 memory:febf8000-febfffff  
 

 kris@kris-System-Product-Name:~$ lspci -nn | grep 0280  
 03:05.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]  
 

 kris@kris-System-Product-Name:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     IEEE 802.11bg  ESSID:off/any  
           Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:off  
 

 kris@kris-System-Product-Name:~$ rfkill list all  
 0: phy0: Wireless LAN  
 	Soft blocked: no  
 	Hard blocked: no  
 

 

 kris@kris-System-Product-Name:~$ lsmod  
 Module                  Size  Used by  
 nls_iso8859_1          12617  1  
 nls_cp437              12751  1  
 vfat                   17335  1  
 fat                    55505  1 vfat  
 binfmt_misc            13213  1  
 vesafb                 13449  1  
 snd_hda_codec_hdmi     27535  1  
 snd_hda_codec_via      56765  1  
 arc4                   12473  2  
 snd_seq_midi           13132  0  
 snd_hda_intel          24140  2  
 rt61pci                27265  0  
 crc_itu_t              12627  1 rt61pci 
 snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel  
 rt2x00pci              13986  1 rt61pci 
 snd_rawmidi            25269  1 snd_seq_midi  
 rt2x00lib              39075  2 rt61pci,rt2x00pci  
 snd_hwdep              13274  1 snd_hda_codec  
 mac80211              257001  2 rt2x00pci,rt2x00lib  
 snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec  
 snd_seq_midi_event     14475  1 snd_seq_midi  
 ppdev                  12849  0  
 cfg80211              156212  2 rt2x00lib,mac80211  
 eeprom_93cx6           12653  1 rt61pci 
 snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event  
 joydev                 17322  0  
 sp5100_tco             13456  0  
 fglrx                2434640  54  
 i2c_piix4              13095  0  
 snd_timer              28659  2 snd_pcm,snd_seq  
 snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq  
 k10temp                12951  0  
 snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_rawmidi,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device 
 soundcore              12600  1 snd  
 snd_page_alloc         14073  2 snd_hda_intel,snd_pcm  
 parport_pc             32111  1  
 asus_atk0110           17664  0  
 shpchp                 32345  0  
 lp                     13349  0  
 parport                36746  3 ppdev,parport_pc,lp  
 hid_sunplus            12547  0  
 usbhid                 41704  0  
 hid                    77084  2 hid_sunplus,usbhid  
 usb_storage            43946  1  
 uas                    17676  0  
 ahci                   21591  2  
 r8169                  46630  0  
 pata_atiixp            12968  0  
 libahci                25548  1 ahci
```




Hope this helps!


Kris

---

### Post by nm_geo on 2011-07-25
Kris how far away is your the wireless access point?

```
sudo iwlist scan
```

Can you get closer?

---

### Post by KrisB on 2011-07-25
I'm  up a floor but the signal always said excellent... is showing it as not good?  I've never had trouble connecting before and my windows laptop is picking it up great in the same room.  ??  

```
 kris@kris-System-Product-Name:~$ sudo iwlist scan  
 lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 wlan0     Scan completed :  
           Cell 01 - Address: 00:1A:70:3D:21:4C  
                     Channel:6  
                     Frequency:2.437 GHz (Channel 6)  
                     Quality=32/70  Signal level=-78 dBm   
                     Encryption key:off  
                     ESSID:"linksys" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s  
                               24 Mb/s; 36 Mb/s; 54 Mb/s  
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s  
                     Mode:Master  
                     Extra:tsf=0000003fce8ee184  
                     Extra: Last beacon: 752ms ago  
                     IE: Unknown: 00076C696E6B737973  
                     IE: Unknown: 010882848B962430486C  
                     IE: Unknown: 030106 
                     IE: Unknown: 2A0104 
                     IE: Unknown: 2F0104 
                     IE: Unknown: 32040C121860  
                     IE: Unknown: DD06001018020014  
 

 
```

---

### Post by KrisB on 2011-07-25
I really can't get much closer- b/c It's a desktop and I have to haul the entire system down stairs and my in-laws won't be too thrilled w/ me taking up the dining room table.  :frown:

---

### Post by nm_geo on 2011-07-25
Quality=32/70  Signal level=[COLOR=Red]-78 dBm [/COLOR]  

that is not to good there.  You really would like to see it
lower than 70.. Say maybe -66 or -68 dBm..

You have an installed driver and since you can scan the wireless
that part is working.  I did a modinfo on your driver and the pci
number is shown.   

Like this copy and paste in terminal

```
sudo modinfo rt61pci
```

That listed your wireless card pci number I found in those
attached files.

Please copy and paste in terminal 

```
lspci -nn | grep 0280
```

then paste results ..

---

### Post by nm_geo on 2011-07-25
> **KrisB said:**
> I really can't get much closer- b/c It's a desktop and I have to haul the entire system down stairs and my in-laws won't be too thrilled w/ me taking up the dining room table.  :frown:

I understand.. Who changes the wireless Access point?  Who has control of it?
I changed my channel not long ago and got a 4 dBm change.. Channel 6 is like default usually and everyone uses it.

---

### Post by nm_geo on 2011-07-25
deleted same question

---

### Post by KrisB on 2011-07-25
ok- I think if I read that right, I just do the second one? here's the output:

```

03:05.0 network Controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
```

---

### Post by KrisB on 2011-07-25
It's my husband's father's router which I doubt he'll let me reconfigure.  He's a little possessive of his tech.  Too bad b/c it's an old router- but like I said, I'm surprised it's weak b/c I have four out five bars on my windows machine and never had a connection issue before two days ago.  Maybe if I tell him the experts say to change the channel he'll listen! lol

---

### Post by nm_geo on 2011-07-25
> **KrisB said:**
> ok- I think if I read that right, I just do the second one? here's the output:

```

03:05.0 network Controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
```

Yeah that is the one ..
 You may have two driver trying to claim the wireless.. We are working on it as we speak.

---

### Post by nm_geo on 2011-07-25
> **KrisB said:**
> It's my husband's father's router which I doubt he'll let me reconfigure.  He's a little possessive of his tech.  Too bad b/c it's an old router- but like I said, I'm surprised it's weak b/c I have four out five bars on my windows machine and never had a connection issue before two days ago.  Maybe if I tell him the experts say to change the channel he'll listen! lol

Let;s try a few other ways first :P

We don't want him mad..

---

### Post by KrisB on 2011-07-25
Yay!!!  I love this place!!  Actual help!!  :)  Thank you! I can't even express my gratitude that you're giving me your time!

---

### Post by nm_geo on 2011-07-25
It is no problem .. We all have had problems and we just kinda pay-it-forward.. Your wireless is not my specialty but we have a doctor chili who has seen it all.. Maybe he will drop by and tell us something good.

I re-read the modinfo stuff let me paste it here..
 
```
filename:       /lib/modules/3.0.0-0300rc2-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B83AB64D509586953986FF9
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*[COLOR=Red]
**depends:        rt2x00lib,rt2x00pci,crc-itu-t,eeprom_93cx6**[/COLOR]
vermagic:       3.0.0-0300rc2-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

```[COLOR=Black]That kinda tells us that your driver depends/needs those modules.. [/COLOR]

---

### Post by wildmanne39 on 2011-07-25
Hi, also I have noticed this IEEE 802.11bg  ESSID:off/any have you clicked on internet icon in the top right corner, then edit connections and put your SSID in there it should look like this.

---

### Post by wildmanne39 on 2011-07-25
Hi, I have double checked the lsmod and all the modules are loaded.

---

### Post by KrisB on 2011-07-25
only problem is I no longer have the icon b/c network manager was uninstalled when I installed wicd.  (from advice I read in multiple forums elsewhere it had to be taken out for wicd to work right)  Now I don't know how to find the connection since I can't get wicd or wifi radar to work.  I could try to reinstall network manager since it at least partially worked- but is there a download for that?  I am so clueless.  Someday I need to go and get a command line for dummies book and learn how to do this stuff.  Normally I don't need it except when I break things. (like now)

---

### Post by nm_geo on 2011-07-25
Have you tried to type
 ```
wicd 
```
in terminal

it might just start the GUI

---

### Post by KrisB on 2011-07-25
it says: rename failed Root privileges are required for the daemon to run properly. Exiting.  

Should I try sudo wicd? would that work?

---

### Post by KrisB on 2011-07-25
tried it anyway.  Still says rename failed.

---

### Post by nm_geo on 2011-07-25
try it it will not hurt..

---

### Post by nm_geo on 2011-07-25
```
wicd-curses
```Try that one LOL

---

### Post by wildmanne39 on 2011-07-25
Hi, try 
```
sudo wicd
```

I am going to be gone for a few minutes.

---

### Post by KrisB on 2011-07-25
It says:
```
Traceback (most recent call last):
  File "/usr/share/wicd/curses/wicd-curses.py", line 41, in <module>
       import urwid
ImportError: No module named urwid
```

---

### Post by nm_geo on 2011-07-25
Kris

I am also out of ideas here .. I will message chili and see if he has an idea.. if so he will add to this link maybe later or tomorrow.. We don't give up easily..

---

### Post by KrisB on 2011-07-25
ok thank you sooooooo much for the help you gave.  If nothing else you helped narrow this down! I appreciate it!

I'll check back tomorrow night.  Gotta get some sleep for work.

---

### Post by wildmanne39 on 2011-07-25
Hi, you might open synaptic and right click on wcid and remove it completely then install network manger again in synaptic, then see if it works, or you can wait for chili555.

---

### Post by KrisB on 2011-07-25
If I go to synaptic and try to reinstall network manager will it let me? I have no connection right now.  I'm posting from a different computer.

---

### Post by wildmanne39 on 2011-07-25
Hi, no wired connection at all ok, you can enabled cdrom updates in synaptic by going to settings,repositories,then put a check by cdrom, then put the livecd in the cd drive and it should allow you to install network manager but do not remove wcid until you know it will install network manager.

---

### Post by KrisB on 2011-07-25
ok first thing when I get home tomorrow.  Thanks!

---

### Post by wildmanne39 on 2011-07-25
Hi, ok and hopefully chili555 will stop by tomorrow.

---

### Post by chili555 on 2011-07-26
Wow! You guys have been busy! If I may summarize, so we don't have to go back over four pages:

#He has a working driver rt61pci and a healthy iwconfig.

#He can scan and sees his desired access point.

#Network Manager is uninstalled; Wicd is not working properly and maybe not at all.

#How to connect???

Has anyone thought of the obvious:```
sudo killall wicd
sudo iwconfig wlan0 essid linksys
sudo dhclient wlan0
```Even if there are errors, they will be informative. If this works, I suggest we ditch Wicd and write up /etc/network/interfaces and be done.

I, too am concerned by: > Cell 01 - Address: 00:1A:70:3D:21:4C  
                     Channel:6  
                     Frequency:2.437 GHz (Channel 6)  
                     [COLOR="Red"]Quality=32/70[/COLOR]  Signal level=-78 dBm   
                     Encryption key:off  
                     ESSID:"linksys" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s  
                               24 Mb/s; 36 Mb/s; 54 Mb/s  
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s  
                     Mode:Master  If it doesn't connect, please let us immediately see:```
sudo tail -n20 /var/log/syslog
```

---

### Post by KrisB on 2011-07-26
Hi Chili,

Believe it or not I'm a girl, lol.  Bet you don't get a lot of girls in here. 

Anyway, two things...  I was looking at Wildmanne's suggestion, and I was looking for where "Settings" went to in 11.04. Everything is set up so differently.  I opened the Software Center and for the first time i got a message that: Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now?  If I click Repair it complains about no internet connection. ](*,)
I have no idea how it got broken!  

Also did what what said, and here's the output:
```
 kris@kris-System-Product-Name:~$ sudo killall wicd  
 [sudo] password for kris:  
 wicd: no process found  
 

 kris@kris-System-Product-Name:~$ sudo iwconfig wlan0 essid linksys  
 

 kris@kris-System-Product-Name:~$ sudo dhclient wlan0  
 

 kris@kris-System-Product-Name:~$ sudo tail -n20 /var/log/syslog  
 Jul 26 11:19:30 kris-System-Product-Name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3  
 Jul 26 11:19:33 kris-System-Product-Name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4  
 Jul 26 11:19:37 kris-System-Product-Name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4  
 Jul 26 11:19:41 kris-System-Product-Name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10  
 Jul 26 11:19:51 kris-System-Product-Name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14  
 Jul 26 11:20:05 kris-System-Product-Name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15  
 Jul 26 11:20:20 kris-System-Product-Name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11  
 Jul 26 11:20:31 kris-System-Product-Name dhclient: No DHCPOFFERS received.  
 Jul 26 11:20:31 kris-System-Product-Name dhclient: No working leases in persistent database - sleeping.  
 Jul 26 11:20:31 kris-System-Product-Name avahi-autoipd(wlan0)[1850]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 108).  
 Jul 26 11:20:31 kris-System-Product-Name avahi-autoipd(wlan0)[1850]: Successfully called chroot().  
 Jul 26 11:20:31 kris-System-Product-Name avahi-autoipd(wlan0)[1850]: Successfully dropped root privileges.  
 Jul 26 11:20:31 kris-System-Product-Name avahi-autoipd(wlan0)[1850]: Starting with address 169.254.9.186  
 Jul 26 11:20:32 kris-System-Product-Name ntpd_intres[1042]: host name not found: 0.ubuntu.pool.ntp.org  
 Jul 26 11:20:32 kris-System-Product-Name ntpd_intres[1042]: host name not found: 1.ubuntu.pool.ntp.org  
 Jul 26 11:20:32 kris-System-Product-Name ntpd_intres[1042]: host name not found: 2.ubuntu.pool.ntp.org  
 Jul 26 11:20:32 kris-System-Product-Name ntpd_intres[1042]: host name not found: 3.ubuntu.pool.ntp.org  
 Jul 26 11:20:32 kris-System-Product-Name ntpd_intres[1042]: host name not found: ntp.ubuntu.com  
 Jul 26 11:20:35 kris-System-Product-Name avahi-autoipd(wlan0)[1850]: Callout BIND, address 169.254.9.186 on interface wlan0  
 Jul 26 11:20:39 kris-System-Product-Name avahi-autoipd(wlan0)[1850]: Successfully claimed IP address 169.254.9.186  
 kris@kris-System-Product-Name:~$  
 
```

I see it says an IP address was claimed, but when I open Firefox it doesn't even pretend to connect.  Just says "server not found".  :(

---

### Post by KrisB on 2011-07-26
I found repositories, checked off the CD and it ran. When i search for "network" i see several things.  also there's plain "networking", "networking (multiverse)", and "networking (universe)".  So many choices!

I don't want to install the wrong one! Truthfully Network Manager worked poorly to begin with but again, only since 11.04  Worked Great in all previous versions.  

I see Wicd as a choice in universe- and isn't showing it installed.  It's still in the "apps" though.  ??

---

### Post by KrisB on 2011-07-26
PS I'm learning all kinds of new things here!

---

### Post by KrisB on 2011-07-26
never mind it's installed found it lower down in the list.

---

### Post by chili555 on 2011-07-26
Kris-

I certainly can believe you are a girl. We get more here than you might imagine. The guys I was referring to are nm_geo and the Wild Man who *both* asked me to look in. I was interested to see that the thread exploded into four pages and no-one tried the simplest thing!

You were assigned a 169.xx address:> Successfully claimed IP address 169.254.9.186That's a place-holder when the system can't get a response from the DHCP server in the router. Part of the reason to run this command is to see if any warnings, errors, clues, etc. emerge. It is looking good so far.

Manual methods almost never work when Network Manager is installed, which, evidently, it is:> never mind it's installed found it lower down in the list. So what do you see when you click the Network Manager icon? Do you see your network linksys? When you click it, does it try to connect?

If you don't see the icon, open a terminal and type:```
nm-applet &
```Leave it open and look somewhere at the top right for the icon. Please see attached.

We can work on restoring the icon and getting some encryption on the network after we simply connect.

---

### Post by KrisB on 2011-07-26
Sorry I should have been more specific.  It was Wicd and Wi-Fi radar that I saw installed.  i do also see Network-manager-pptp installed in Package Manager.  I have no wireless icon.   I typed in nm-applet & and it says:

[1] 2555
Kris@kris-system-product-name:~$The program 'nm-applet' can be found in the following packages:
 *network-manager-gnome
 *mythbuntu-diskless-client
Try: sudo apt-get install <selected package>


I used to have the applet.  :(  I should have never listened to bad advice.

---

### Post by KrisB on 2011-07-26
Also thanks for looking in for me.  Sorry for misunderstanding your pronouns.  ;)

---

### Post by chili555 on 2011-07-26
> i do also see Network-manager-pptp installed in Package Manager.I suggest you remove it. As far as you know, is Wicd broken? Is it running or trying to run on your system?```
ps aux | grep -i wicd
```Is the router you are trying to connect to close or far or ??? Is the router yours? Many have a setting for transmit power; is yours dialed up to the maximum?

---

### Post by KrisB on 2011-07-26
Hi,


I "marked" network-manager-pptp and network manager for removal but I get an error which says something about "Failed to fetch" and gives a URL so I think it's b/c I have no internet?  

Doesn't appear to uninstall.  Just highlights them in red with an orange x in the box.  

Wicd does try to run but after I put in the password it asks for it says: "could not connect to wicd's D-Bus interface. Check the wicd log for error messages."

Typed in your code:
```
 kris@kris-System-Product-Name:~$ ps aux | grep -i wicd  
 kris      1307  0.0  0.5  95160 21548 ?        Sl   11:13   0:00 /usr/bin/python -O /usr/share/wicd/gtk/wicd-client.py  
 kris      2750  0.0  0.0   4156   860 pts/0    R+   13:41   0:00 grep --color=auto -i wicd  
 kris@kris-System-Product-Name:~$  
 
```

As far as the router....  it's an older one.  I live with my husbands parents temporarily (semi) and my father in law is not one to let me play with it.  It is one floor below me and as I type I'm on a windows laptop in the same room with full signal.  i've always had full signal showing before I installed "Natty".  Makes me kind of want to downgrade to be honest.  I've had only problems since the upgrade.  I honestly don't think it is the router for that reason, but I obviously don't know much so I could be very wrong.  Just seems weird that it's suddenly got weak signal only for my one machine and only after I upgraded.    ?

---

### Post by chili555 on 2011-07-26
It ought to remove with no problems. Please try:```
sudo apt-get remove --purge network-manager*
```Next, do:```
sudo killall wicd-client.py
```That might error out or give us a clue.```
sudo iwconfig wlan0 essid linksys
sudo dhclient wlan0
sudo tail -n20 /var/log/syslog
```It's perfectly reasonable to downgrade if some peculiarity in Natty's implementation  of the driver is not working well. My wife still loves her Lucid. Whenever I mention Natty, she reaches for the rolling pin.

You might also try:```
sudo /sbin/dhclient3 wlan0
```

---

### Post by KrisB on 2011-07-26
lol re: the rolling pin!  

On step one- (purge network-manager) it says the resource is temporarily unavailable, and that it is unable to lock the administration directory (/var/lib/dpkg/) and asks if another process is using it?

---

### Post by KrisB on 2011-07-26
```
 kris@kris-System-Product-Name:~$ sudo apt-get remove --purge network-manager*  
 [sudo] password for kris:  
 E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)  
 E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?  
 
```

---

### Post by chili555 on 2011-07-26
I betcha some other process *is* using it. Do you have Synaptic sitting open and minimized? Please close it and try again.

---

### Post by KrisB on 2011-07-26
Good call- that worked.  

```
 kris@kris-System-Product-Name:~$ sudo apt-get remove --purge network-manager*  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 Note, selecting 'network-manager' for regex 'network-manager*'  
 Note, selecting 'network-manager-pptp-kde' for regex 'network-manager*'  
 Note, selecting 'network-manager-dev' for regex 'network-manager*'  
 Note, selecting 'network-manager-gnome' for regex 'network-manager*'  
 Note, selecting 'network-manager-kde' for regex 'network-manager*'  
 Note, selecting 'network-manager-pptp' for regex 'network-manager*'  
 Note, selecting 'network-manager-vpnc-kde' for regex 'network-manager*'  
 Note, selecting 'network-manager-openvpn-kde' for regex 'network-manager*'  
 Note, selecting 'network-manager-pptp-gnome' for regex 'network-manager*'  
 Note, selecting 'network-manager-openconnect' for regex 'network-manager*'  
 Note, selecting 'network-manager-openconnect-gnome' for regex 'network-manager*'  
 Note, selecting 'network-manager-openvpn' for regex 'network-manager*'  
 Note, selecting 'network-manager-openvpn-gnome' for regex 'network-manager*'  
 Note, selecting 'network-manager-strongswan' for regex 'network-manager*'  
 Note, selecting 'network-manager-strongswan-kde' for regex 'network-manager*'  
 Note, selecting 'network-manager-vpnc' for regex 'network-manager*'  
 Note, selecting 'network-manager-vpnc-gnome' for regex 'network-manager*'  
 Package network-manager-dev is not installed, so not removed  
 Package network-manager-kde is not installed, so not removed  
 Package network-manager-pptp-kde is not installed, so not removed  
 Package network-manager-openconnect is not installed, so not removed  
 Package network-manager-openconnect-gnome is not installed, so not removed  
 Package network-manager-openvpn is not installed, so not removed  
 Package network-manager-openvpn-gnome is not installed, so not removed  
 Package network-manager-openvpn-kde is not installed, so not removed  
 Package network-manager-strongswan is not installed, so not removed  
 Package network-manager-strongswan-kde is not installed, so not removed  
 Package network-manager-vpnc is not installed, so not removed  
 Package network-manager-vpnc-gnome is not installed, so not removed  
 Package network-manager-vpnc-kde is not installed, so not removed  
 You might want to run 'apt-get -f install' to correct these:  
 The following packages have unmet dependencies:  
  wifi-radar : Depends: menu but it is not going to be installed  
 E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).  
 



kris@kris-System-Product-Name:~$ sudo killall wicd-client.py  
 wicd-client.py: no process found  
 



kris@kris-System-Product-Name:~$ sudo iwconfig wlan0 essid linksys  
 

kris@kris-System-Product-Name:~$ sudo dhclient wlan0  
 



kris@kris-System-Product-Name:~$ sudo tail -n20 /var/log/syslog  
 Jul 26 14:54:30 kris-System-Product-Name avahi-autoipd(wlan0)[1850]: Got SIGTERM, quitting.  
 Jul 26 14:54:30 kris-System-Product-Name avahi-autoipd(wlan0)[1850]: Callout STOP, address 169.254.9.186 on interface wlan0  
 Jul 26 14:54:30 kris-System-Product-Name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3  
 Jul 26 14:54:33 kris-System-Product-Name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5  
 Jul 26 14:54:38 kris-System-Product-Name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9  
 Jul 26 14:54:47 kris-System-Product-Name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8  
 Jul 26 14:54:55 kris-System-Product-Name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12  
 Jul 26 14:55:07 kris-System-Product-Name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19  
 Jul 26 14:55:26 kris-System-Product-Name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5  
 Jul 26 14:55:31 kris-System-Product-Name dhclient: No DHCPOFFERS received.  
 Jul 26 14:55:31 kris-System-Product-Name dhclient: No working leases in persistent database - sleeping.  
 Jul 26 14:55:31 kris-System-Product-Name avahi-autoipd(wlan0)[3245]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 108).  
 Jul 26 14:55:31 kris-System-Product-Name avahi-autoipd(wlan0)[3245]: Successfully called chroot().  
 Jul 26 14:55:31 kris-System-Product-Name avahi-autoipd(wlan0)[3245]: Successfully dropped root privileges.  
 Jul 26 14:55:31 kris-System-Product-Name avahi-autoipd(wlan0)[3245]: Starting with address 169.254.9.186  
 Jul 26 14:55:36 kris-System-Product-Name avahi-autoipd(wlan0)[3245]: Callout BIND, address 169.254.9.186 on interface wlan0  
 Jul 26 14:55:40 kris-System-Product-Name avahi-autoipd(wlan0)[3245]: Successfully claimed IP address 169.254.9.186  
 Jul 26 14:55:48 kris-System-Product-Name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3  
 Jul 26 14:55:51 kris-System-Product-Name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7  
 Jul 26 14:55:58 kris-System-Product-Name dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8  
 
```

---

### Post by lkjoel on 2011-07-26
Also, you can try downloading the shell script I attached, move it to your desktop and type in a Terminal window:
```
cd ~/Desktop
chmod +x wirelessGUI.sh
./wirelessGUI.sh &
```And for the error message above:
```
sudo apt-get -f install

```

---

### Post by KrisB on 2011-07-26
did that- I got a box that says "Wireless" and asks what network name I want to connect to.  in the field it says NXL6DO.  (not one I've ever seen come up before-is that part of your script?)

---

### Post by KrisB on 2011-07-26
This was the last one:

[CODE][ kris@kris-System-Product-Name:~/Desktop$ sudo apt-get -f install  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 Correcting dependencies... Done  
 The following extra packages will be installed:  
   menu  
 Suggested packages:  
   menu-l10n  
 The following NEW packages will be installed:  
   menu  
 0 upgraded, 1 newly installed, 0 to remove and 184 not upgraded.  
 1 not fully installed or removed.  
 Need to get 452 kB of archives.  
 After this operation, 2,093 kB of additional disk space will be used.  
 Do you want to continue [Y/n]? y  
 WARNING: The following packages cannot be authenticated!  
   menu  
 Install these packages without verification [y/N]? y  
 Err http://us.archive.ubuntu.com/ubuntu/ natty/universe menu i386 2.1.44ubuntu1  
   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/menu/menu_2.1.44ubuntu1_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?  
 kris@kris-System-Product-Name:~/Desktop$ 
 /CODE]

---

### Post by lkjoel on 2011-07-26
> **KrisB said:**
> did that- I got a box that says "Wireless" and asks what network name I want to connect to.  in the field it says NXL6DO.  (not one I've ever seen come up before-is that part of your script?)
Sorry! It was not coded correctly.
I made this for a friend, and their network name was NXL6DO. Just replace it to your network name.

---

### Post by lkjoel on 2011-07-26
> **KrisB said:**
> This was the last one:

```
 kris@kris-System-Product-Name:~/Desktop$ sudo apt-get -f install  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 Correcting dependencies... Done  
 The following extra packages will be installed:  
   menu  
 Suggested packages:  
   menu-l10n  
 The following NEW packages will be installed:  
   menu  
 0 upgraded, 1 newly installed, 0 to remove and 184 not upgraded.  
 1 not fully installed or removed.  
 Need to get 452 kB of archives.  
 After this operation, 2,093 kB of additional disk space will be used.  
 Do you want to continue [Y/n]? y  
 WARNING: The following packages cannot be authenticated!  
   menu  
 Install these packages without verification [y/N]? y  
 Err http://us.archive.ubuntu.com/ubuntu/ natty/universe menu i386 2.1.44ubuntu1  
   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/menu/menu_2.1.44ubuntu1_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?  
 kris@kris-System-Product-Name:~/Desktop$ 
 
```
I forgot that you didn't have internet access lol!
Could you give me the output of:
```
uname -a
```
and
```
lsb_release -a
```

---

### Post by KrisB on 2011-07-26
aahhh!! the box is gone.  let me run that again.  Would my network be linksys?

---

### Post by lkjoel on 2011-07-26
> **KrisB said:**
> aahhh!! the box is gone.  let me run that again.  Would my network be linksys?
Don't run it again!
Type in a Terminal window:
```
killall wirelessGUI.sh
```

Could you give me the output of:
```
nm-tool
```

---

### Post by KrisB on 2011-07-26
kris@kris-System-Product-Name:~$ uname -a  
 Linux kris-System-Product-Name 2.6.38-10-generic-pae #46-Ubuntu SMP Tue Jun 28 16:54:49 UTC 2011 i686 athlon i386 GNU/Linux  
 



kris@kris-System-Product-Name:~$ lsb_release -a  
 No LSB modules are available.  
 Distributor ID:	Ubuntu  
 Description:	Ubuntu 11.04  
 Release:	11.04  
 Codename:	natty  
 kris@kris-System-Product-Name:~$

---

### Post by KrisB on 2011-07-26
Sure!
 



kris@kris-System-Product-Name:~$ nm-tool  
 

 NetworkManager Tool  
 

 State: disconnected  
 

 - Device: eth0 -----------------------------------------------------------------  
   Type:              Wired  
   Driver:            r8169  
   State:             unavailable  
   Default:           no  
   HW Address:        E0:CB:4E:FF:91:21  
 

   Capabilities:  
     Carrier Detect:  yes  
     Speed:           10 Mb/s  
 

   Wired Properties  
     Carrier:         off  
 

 

 - Device: wlan0 ----------------------------------------------------------------  
   Type:              802.11 WiFi  
   Driver:            rt61pci  
   State:             disconnected  
   Default:           no  
   HW Address:        00:1E:E5:FD:36:9A  
 

   Capabilities:  
 

   Wireless Properties  
     WEP Encryption:  yes  
     WPA Encryption:  yes  
     WPA2 Encryption: yes  
 

   Wireless Access Points  
     linksys:         Infra, 00:1A:70:3D:21:4C, Freq 2437 MHz, Rate 54 Mb/s, Strength 40

---

### Post by lkjoel on 2011-07-26
> **KrisB said:**
> kris@kris-System-Product-Name:~$ uname -a  
 Linux kris-System-Product-Name 2.6.38-10-generic-pae #46-Ubuntu SMP Tue Jun 28 16:54:49 UTC 2011 i686 athlon i386 GNU/Linux  
 



kris@kris-System-Product-Name:~$ lsb_release -a  
 No LSB modules are available.  
 Distributor ID:    Ubuntu  
 Description:    Ubuntu 11.04  
 Release:    11.04  
 Codename:    natty  
 kris@kris-System-Product-Name:~$
On the computer you are using (the one with internet that you are using for posting this), download the attachment, put it in a USB stick, and plug the USB stick on the other computer (without internet). Copy and paste the menu.tar file to your home directory, and type in a Terminal window:
```
cd ~
tar -xf menu.tar
sudo dpkg -i `tar -tvf menu.tar | awk '{print $6}'`
```Copy and paste the last command, as it contains backquotes and quotes.
After that, type in it:
```
sudo apt-get -f install
```

---

### Post by KrisB on 2011-07-26
Done.



kris@kris-System-Product-Name:~$ cd ~  
 kris@kris-System-Product-Name:~$ tar -xf menu.tar  
 kris@kris-System-Product-Name:~$ sudo dpkg -i `tar -tvf menu.tar | awk '{print $6}'`  
 [sudo] password for kris:  
 Selecting previously deselected package menu.  
 (Reading database ... 161569 files and directories currently installed.)  
 Unpacking menu (from menu_2.1.44ubuntu1_i386.deb) ...  
 Setting up menu (2.1.44ubuntu1) ...  
 Processing triggers for man-db ...  
 Processing triggers for install-info ...  
 Processing triggers for doc-base ...  
 Processing 1 added doc-base file(s)...  
 Registering documents with scrollkeeper...  
 Processing triggers for menu ...

---

### Post by lkjoel on 2011-07-26
> **KrisB said:**
> Done.



kris@kris-System-Product-Name:~$ cd ~  
 kris@kris-System-Product-Name:~$ tar -xf menu.tar  
 kris@kris-System-Product-Name:~$ sudo dpkg -i `tar -tvf menu.tar | awk '{print $6}'`  
 [sudo] password for kris:  
 Selecting previously deselected package menu.  
 (Reading database ... 161569 files and directories currently installed.)  
 Unpacking menu (from menu_2.1.44ubuntu1_i386.deb) ...  
 Setting up menu (2.1.44ubuntu1) ...  
 Processing triggers for man-db ...  
 Processing triggers for install-info ...  
 Processing triggers for doc-base ...  
 Processing 1 added doc-base file(s)...  
 Registering documents with scrollkeeper...  
 Processing triggers for menu ...
Great! Now just type in it:
```
sudo apt-get -f install
```
Then download the script attached, transfer it into your other computer (the one without internet), into your home directory, and then type in a Terminal window:
```
cd ~
chmod +x wireless.sh
./wireless.sh wlan0 linksys
```

---

### Post by KrisB on 2011-07-26
it hesitated a bit but now says Finished!

---

### Post by lkjoel on 2011-07-26
> **KrisB said:**
> it hesitated a bit but now says Finished!
Great! Type in the Terminal window:
```
ping google.com
```
If you see pings, you are connected! Press CTRL+C to exit the app
If you don't see pings, press CTRL+C, and then type in the Terminal window:
```
sudo apt-get remove --purge network-manager*

```

---

### Post by KrisB on 2011-07-26
It says ping: unknown host google.com
So I did the second step and it purged NM.

---

### Post by KrisB on 2011-07-26
ris@kris-System-Product-Name:~$ ping google.com  
 ping: unknown host google.com  
 kris@kris-System-Product-Name:~$ ^C  
 kris@kris-System-Product-Name:~$ sudo apt-get remove --purge network-manager*  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 Note, selecting 'network-manager' for regex 'network-manager*'  
 Note, selecting 'network-manager-pptp-kde' for regex 'network-manager*'  
 Note, selecting 'network-manager-dev' for regex 'network-manager*'  
 Note, selecting 'network-manager-gnome' for regex 'network-manager*'  
 Note, selecting 'network-manager-kde' for regex 'network-manager*'  
 Note, selecting 'network-manager-pptp' for regex 'network-manager*'  
 Note, selecting 'network-manager-vpnc-kde' for regex 'network-manager*'  
 Note, selecting 'network-manager-openvpn-kde' for regex 'network-manager*'  
 Note, selecting 'network-manager-pptp-gnome' for regex 'network-manager*'  
 Note, selecting 'network-manager-openconnect' for regex 'network-manager*'  
 Note, selecting 'network-manager-openconnect-gnome' for regex 'network-manager*'  
 Note, selecting 'network-manager-openvpn' for regex 'network-manager*'  
 Note, selecting 'network-manager-openvpn-gnome' for regex 'network-manager*'  
 Note, selecting 'network-manager-strongswan' for regex 'network-manager*'  
 Note, selecting 'network-manager-strongswan-kde' for regex 'network-manager*'  
 Note, selecting 'network-manager-vpnc' for regex 'network-manager*'  
 Note, selecting 'network-manager-vpnc-gnome' for regex 'network-manager*'  
 Package network-manager-dev is not installed, so not removed  
 Package network-manager-kde is not installed, so not removed  
 Package network-manager-pptp-kde is not installed, so not removed  
 Package network-manager-openconnect is not installed, so not removed  
 Package network-manager-openconnect-gnome is not installed, so not removed  
 Package network-manager-openvpn is not installed, so not removed  
 Package network-manager-openvpn-gnome is not installed, so not removed  
 Package network-manager-openvpn-kde is not installed, so not removed  
 Package network-manager-strongswan is not installed, so not removed  
 Package network-manager-strongswan-kde is not installed, so not removed  
 Package network-manager-vpnc is not installed, so not removed  
 Package network-manager-vpnc-gnome is not installed, so not removed  
 Package network-manager-vpnc-kde is not installed, so not removed  
 The following packages will be REMOVED: 
   network-manager* network-manager-gnome* network-manager-pptp*  
   network-manager-pptp-gnome*  
 0 upgraded, 0 newly installed, 3 to remove and 184 not upgraded.  
 After this operation, 1,942 kB disk space will be freed.  
 Do you want to continue [Y/n]? y  
 (Reading database ... 161749 files and directories currently installed.)  
 Removing network-manager ...  
 network-manager stop/waiting  
 Purging configuration files for network-manager ...  
 Removing network-manager-gnome ...  
 Purging configuration files for network-manager-gnome ...  
 Removing network-manager-pptp-gnome ... 
 Purging configuration files for network-manager-pptp-gnome ...  
 Removing network-manager-pptp ...  
 Purging configuration files for network-manager-pptp ...  
 Processing triggers for man-db ...  
 Processing triggers for ureadahead ...  
 ureadahead will be reprofiled on next reboot  
 Processing triggers for libc-bin ...  
 ldconfig deferred processing now taking place

---

### Post by lkjoel on 2011-07-26
> **KrisB said:**
> ris@kris-System-Product-Name:~$ ping google.com  
 ping: unknown host google.com  
 kris@kris-System-Product-Name:~$ ^C  
 kris@kris-System-Product-Name:~$ sudo apt-get remove --purge network-manager*  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 Note, selecting 'network-manager' for regex 'network-manager*'  
 Note, selecting 'network-manager-pptp-kde' for regex 'network-manager*'  
 Note, selecting 'network-manager-dev' for regex 'network-manager*'  
 Note, selecting 'network-manager-gnome' for regex 'network-manager*'  
 Note, selecting 'network-manager-kde' for regex 'network-manager*'  
 Note, selecting 'network-manager-pptp' for regex 'network-manager*'  
 Note, selecting 'network-manager-vpnc-kde' for regex 'network-manager*'  
 Note, selecting 'network-manager-openvpn-kde' for regex 'network-manager*'  
 Note, selecting 'network-manager-pptp-gnome' for regex 'network-manager*'  
 Note, selecting 'network-manager-openconnect' for regex 'network-manager*'  
 Note, selecting 'network-manager-openconnect-gnome' for regex 'network-manager*'  
 Note, selecting 'network-manager-openvpn' for regex 'network-manager*'  
 Note, selecting 'network-manager-openvpn-gnome' for regex 'network-manager*'  
 Note, selecting 'network-manager-strongswan' for regex 'network-manager*'  
 Note, selecting 'network-manager-strongswan-kde' for regex 'network-manager*'  
 Note, selecting 'network-manager-vpnc' for regex 'network-manager*'  
 Note, selecting 'network-manager-vpnc-gnome' for regex 'network-manager*'  
 Package network-manager-dev is not installed, so not removed  
 Package network-manager-kde is not installed, so not removed  
 Package network-manager-pptp-kde is not installed, so not removed  
 Package network-manager-openconnect is not installed, so not removed  
 Package network-manager-openconnect-gnome is not installed, so not removed  
 Package network-manager-openvpn is not installed, so not removed  
 Package network-manager-openvpn-gnome is not installed, so not removed  
 Package network-manager-openvpn-kde is not installed, so not removed  
 Package network-manager-strongswan is not installed, so not removed  
 Package network-manager-strongswan-kde is not installed, so not removed  
 Package network-manager-vpnc is not installed, so not removed  
 Package network-manager-vpnc-gnome is not installed, so not removed  
 Package network-manager-vpnc-kde is not installed, so not removed  
 The following packages will be REMOVED: 
   network-manager* network-manager-gnome* network-manager-pptp*  
   network-manager-pptp-gnome*  
 0 upgraded, 0 newly installed, 3 to remove and 184 not upgraded.  
 After this operation, 1,942 kB disk space will be freed.  
 Do you want to continue [Y/n]? y  
 (Reading database ... 161749 files and directories currently installed.)  
 Removing network-manager ...  
 network-manager stop/waiting  
 Purging configuration files for network-manager ...  
 Removing network-manager-gnome ...  
 Purging configuration files for network-manager-gnome ...  
 Removing network-manager-pptp-gnome ... 
 Purging configuration files for network-manager-pptp-gnome ...  
 Removing network-manager-pptp ...  
 Purging configuration files for network-manager-pptp ...  
 Processing triggers for man-db ...  
 Processing triggers for ureadahead ...  
 ureadahead will be reprofiled on next reboot  
 Processing triggers for libc-bin ...  
 ldconfig deferred processing now taking place

Now, type in it:
```
sudo apt-get install network-manager network-manager-gnome network-manager-pptp-gnome network-manager-pptp
```

Can other computers access the internet?

---

### Post by KrisB on 2011-07-26
Yes, actually all of them can (my laptop, dad's laptop, dad's desktop, mom's laptop) except my broken desktop.  :frown:
kris@kris-System-Product-Name:~$ sudo apt-get install network-manager network-manager-gnome network-manager-pptp-gnome network-manager-pptp  
 [sudo] password for kris:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following NEW packages will be installed:  
   network-manager network-manager-gnome network-manager-pptp  
   network-manager-pptp-gnome  
 0 upgraded, 4 newly installed, 0 to remove and 184 not upgraded.  
 Need to get 987 kB of archives.  
 After this operation, 3,916 kB of additional disk space will be used.  
 WARNING: The following packages cannot be authenticated!  
   network-manager network-manager-gnome network-manager-pptp  
   network-manager-pptp-gnome  
 Install these packages without verification [y/N]? y  
 Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main network-manager i386 0.8.4~git.20110319t175609.d14809b-0ubuntu3  
   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main network-manager-gnome i386 0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1  
   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main network-manager-pptp i386 0.8.1+git.20110207t142407.7e1d989-0ubuntu1  
   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main network-manager-pptp-gnome i386 0.8.1+git.20110207t142407.7e1d989-0ubuntu1  
   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8.4~git.20110319t175609.d14809b-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8.4~git.20110319t175609.d14809b-0ubuntu3_i386.deb)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1_i386.deb)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-pptp/network-manager-pptp_0.8.1+git.20110207t142407.7e1d989-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-pptp/network-manager-pptp_0.8.1+git.20110207t142407.7e1d989-0ubuntu1_i386.deb)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-pptp/network-manager-pptp-gnome_0.8.1+git.20110207t142407.7e1d989-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-pptp/network-manager-pptp-gnome_0.8.1+git.20110207t142407.7e1d989-0ubuntu1_i386.deb)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?  
 
```

```

---

### Post by lkjoel on 2011-07-26
> **KrisB said:**
> Yes, actually all of them can (my laptop, dad's laptop, dad's desktop, mom's laptop) except my broken desktop.  :frown:
kris@kris-System-Product-Name:~$ sudo apt-get install network-manager network-manager-gnome network-manager-pptp-gnome network-manager-pptp  
 [sudo] password for kris:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following NEW packages will be installed:  
   network-manager network-manager-gnome network-manager-pptp  
   network-manager-pptp-gnome  
 0 upgraded, 4 newly installed, 0 to remove and 184 not upgraded.  
 Need to get 987 kB of archives.  
 After this operation, 3,916 kB of additional disk space will be used.  
 WARNING: The following packages cannot be authenticated!  
   network-manager network-manager-gnome network-manager-pptp  
   network-manager-pptp-gnome  
 Install these packages without verification [y/N]? y  
 Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main network-manager i386 0.8.4~git.20110319t175609.d14809b-0ubuntu3  
   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main network-manager-gnome i386 0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1  
   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main network-manager-pptp i386 0.8.1+git.20110207t142407.7e1d989-0ubuntu1  
   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main network-manager-pptp-gnome i386 0.8.1+git.20110207t142407.7e1d989-0ubuntu1  
   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8.4~git.20110319t175609.d14809b-0ubuntu3_i386.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8.4%7Egit.20110319t175609.d14809b-0ubuntu3_i386.deb")  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1_i386.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8.4%7Egit.20110318t152954.9c4c9a0-0ubuntu1_i386.deb")  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-pptp/network-manager-pptp_0.8.1+git.20110207t142407.7e1d989-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-pptp/network-manager-pptp_0.8.1+git.20110207t142407.7e1d989-0ubuntu1_i386.deb)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-pptp/network-manager-pptp-gnome_0.8.1+git.20110207t142407.7e1d989-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-pptp/network-manager-pptp-gnome_0.8.1+git.20110207t142407.7e1d989-0ubuntu1_i386.deb)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)  
 E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?  
 

Sorry, I still forgot about your internet!
Transfer the attachment to your broken computer, into the home folder, and type in the Terminal window:
```
cd ~
mkdir nm-tar
mv nm.tar nm-tar
cd nm-tar
tar -xf nm.tar
rm -f nm.tar
sudo dpkg -i *
```
Notice the dash and the dot.

---

### Post by KrisB on 2011-07-26
ok done

```
 Selecting previously deselected package network-manager.  
 (Reading database ... 161666 files and directories currently installed.)  
 Unpacking network-manager (from network-manager_0.8.4~git.20110319t175609.d14809b-0ubuntu3_i386.deb) ...  
 Selecting previously deselected package network-manager-gnome.  
 Unpacking network-manager-gnome (from network-manager-gnome_0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1_i386.deb) ...  
 Selecting previously deselected package network-manager-pptp.  
 Unpacking network-manager-pptp (from network-manager-pptp_0.8.1+git.20110207t142407.7e1d989-0ubuntu1_i386.deb) ...  
 Selecting previously deselected package network-manager-pptp-gnome.  
 Unpacking network-manager-pptp-gnome (from network-manager-pptp-gnome_0.8.1+git.20110207t142407.7e1d989-0ubuntu1_i386.deb) ...  
 Setting up network-manager (0.8.4~git.20110319t175609.d14809b-0ubuntu3) ...  
 Setting up network-manager-pptp (0.8.1+git.20110207t142407.7e1d989-0ubuntu1) ...  
 Processing triggers for man-db ...  
 Setting up network-manager-pptp-gnome (0.8.1+git.20110207t142407.7e1d989-0ubuntu1) ...  
 Processing triggers for ureadahead ...  
 Setting up network-manager-gnome (0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1) ...  
 Processing triggers for hicolor-icon-theme ...  
 Processing triggers for bamfdaemon ...  
 Rebuilding /usr/share/applications/bamf.index...  
 Processing triggers for desktop-file-utils ...  
 Processing triggers for python-gmenu ...  
 Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...  
 Processing triggers for gconf2 ...  
 Processing triggers for libc-bin ...  
 ldconfig deferred processing now taking place  
 Processing triggers for python-support ...  
 
```

---

### Post by lkjoel on 2011-07-26
Can you see the list of networks available?

Also, have you tried entering your livecd in the tray, rebooting into the livecd, and checking if you have internet there?

---

### Post by KrisB on 2011-07-26
You, Sir, are a God!!  It works!!!  I restarted and it froze totally after a long error string.  My heart stopped as I hit reset b/c cntl-alt-delete didn't do anything.  But then it loaded normally- and nm is there, and it's so far staying connected.  I still got the wicd dbus error so I still have to unstall wicd right? But so far so good w/ nm!!!  Thank you sooooo very much!!!!

---

### Post by KrisB on 2011-07-26
Acually software center is finally letting me in, and says wicd and wi-fi radar are both there

---

### Post by KrisB on 2011-07-26
Even if I leave them..... it works!!! Thanks everyone!!!

---

### Post by lkjoel on 2011-07-26
Great! Can you mark this thread as solved? (Thread Tools->Mark this thread as solved)

---

### Post by KrisB on 2011-07-26
absolutely!!  I owe you my undying gratitude!!

---

### Post by chili555 on 2011-07-26
Awesome job, lkjoel. Thanks.

---

### Post by wildmanne39 on 2011-07-26
Great I am glad you got it working, Thank you lkjoel,chili555 and nm-geo.  I was over my head on this one.

---

### Post by Boxiflor on 2011-08-08
Hi all

I got a very similar problem with my wireless connection. The wireless keeps losing the connection and the only way to get it back is to reboot. I've read topics on the subject and try several solutions: removing network manager and installing wicd, loading windows driver with nsdiswrapper or lkjoel'solution wireless.sh ... but no success ... My connection is still unstable. Anyone could help me on this one?

Thanks in advance !

My configuration :

```

$nm-tool
NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt61pci
  State:             disconnected
  Default:           no
  HW Address:        C8:3A:35:C1:85:A6

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Livebox-B00F:    Infra, 00:18:E7:3A:B2:CD, Freq 2437 MHz, Rate 54 Mb/s, Strength 88 WPA


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        6C:62:6D:EC:E2:73

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty


$ uname -a
Linux amsterdam 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux

```

---

### Post by lkjoel on 2011-08-08
Do you still have the wireless.sh script? If so, open up a Terminal window, go to the directory where you downloaded the script, and type in it:
```
chmod +x wireless.sh
./wireless.sh wlan0 Livebox-B00F

```
You should be connected now.

---

### Post by Boxiflor on 2011-08-09
Hi lkjoel

Yes I still have it. I run it again and it says finished but again I get disconnected after a few minutes. I'll add the syslog file below. Do you have an idea how to restart the wifi without rebooting?

Thanks !


```

$ ./wireless.sh wlan0 Livebox-B00F
!!
!!
!!
!!
!!
!!



Finished!

```/var/log/syslog

```

Aug  9 19:20:52 amsterdam kernel: [  138.432825] irq 17: nobody cared (try booting with the "irqpoll" option)
Aug  9 19:20:52 amsterdam kernel: [  138.432832] Pid: 0, comm: swapper Tainted: P            2.6.38-10-generic #46-Ubuntu
Aug  9 19:20:52 amsterdam kernel: [  138.432834] Call Trace:
Aug  9 19:20:52 amsterdam kernel: [  138.432842]  [<c10b14ac>] ? __report_bad_irq.clone.2+0x2c/0x90
Aug  9 19:20:52 amsterdam kernel: [  138.432845]  [<c10b016c>] ? handle_IRQ_event+0x4c/0x160
Aug  9 19:20:52 amsterdam kernel: [  138.432849]  [<c10b17fa>] ? note_interrupt+0x15a/0x1a0
Aug  9 19:20:52 amsterdam kernel: [  138.432853]  [<c10b241c>] ? handle_fasteoi_irq+0xac/0xd0
Aug  9 19:20:52 amsterdam kernel: [  138.432857]  [<c10b2370>] ? handle_fasteoi_irq+0x0/0xd0
Aug  9 19:20:52 amsterdam kernel: [  138.432859]  <IRQ>  [<c1510d42>] ? do_IRQ+0x42/0xc0
Aug  9 19:20:52 amsterdam kernel: [  138.432867]  [<c1056880>] ? irq_exit+0x60/0x80
Aug  9 19:20:52 amsterdam kernel: [  138.432872]  [<c1510e1b>] ? smp_apic_timer_interrupt+0x5b/0x8a
Aug  9 19:20:52 amsterdam kernel: [  138.432876]  [<c1003670>] ? common_interrupt+0x30/0x38
Aug  9 19:20:52 amsterdam kernel: [  138.432882]  [<c1406635>] ? poll_idle+0x35/0x80
Aug  9 19:20:52 amsterdam kernel: [  138.432886]  [<c14066fd>] ? cpuidle_idle_call+0x7d/0x160
Aug  9 19:20:52 amsterdam kernel: [  138.432889]  [<c10019ca>] ? cpu_idle+0x8a/0xc0
Aug  9 19:20:52 amsterdam kernel: [  138.432894]  [<c1038dde>] ? complete+0x4e/0x60
Aug  9 19:20:52 amsterdam kernel: [  138.432899]  [<c14f127d>] ? rest_init+0x5d/0x70
Aug  9 19:20:52 amsterdam kernel: [  138.432904]  [<c178d7e1>] ? start_kernel+0x35f/0x366
Aug  9 19:20:52 amsterdam kernel: [  138.432908]  [<c178d3d5>] ? pass_all_bootoptions+0x0/0xa
Aug  9 19:20:52 amsterdam kernel: [  138.432913]  [<c178d0e0>] ? i386_start_kernel+0xe0/0xe8
Aug  9 19:20:52 amsterdam kernel: [  138.432915] handlers:
Aug  9 19:20:52 amsterdam kernel: [  138.432917] [<f9843140>] (azx_interrupt+0x0/0x170 [snd_hda_intel])
Aug  9 19:20:52 amsterdam kernel: [  138.432924] [<f995de20>] (rt61pci_interrupt+0x0/0x80 [rt61pci])
Aug  9 19:20:52 amsterdam kernel: [  138.432929] Disabling IRQ #17
[B]Aug  9 19:20:56 amsterdam kernel: [  142.202350] ieee80211 phy0: wlan0: No probe response from AP 00:18:e7:3a:b2:cd after 500ms, disconnecting.
Aug  9 19:20:58 amsterdam wpa_supplicant[857]: CTRL-EVENT-DISCONNECTED bssid=00:18:e7:3a:b2:cd reason=0
Aug  9 19:20:58 amsterdam NetworkManager[845]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Aug  9 19:20:58 amsterdam kernel: [  143.833591] cfg80211: All devices are disconnected, going to restore regulatory settings
Aug  9 19:20:58 amsterdam kernel: [  143.833596] cfg80211: Restoring regulatory settings[/B]
Aug  9 19:20:58 amsterdam kernel: [  143.833600] cfg80211: Calling CRDA to update world regulatory domain
Aug  9 19:20:58 amsterdam kernel: [  143.837728] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Aug  9 19:20:58 amsterdam kernel: [  143.837733] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam kernel: [  143.837736] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Aug  9 19:20:58 amsterdam kernel: [  143.837739] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam kernel: [  143.837741] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Aug  9 19:20:58 amsterdam kernel: [  143.837744] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam kernel: [  143.837747] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Aug  9 19:20:58 amsterdam kernel: [  143.837749] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam kernel: [  143.837752] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Aug  9 19:20:58 amsterdam kernel: [  143.837755] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam kernel: [  143.837757] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Aug  9 19:20:58 amsterdam kernel: [  143.837760] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam kernel: [  143.837762] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Aug  9 19:20:58 amsterdam kernel: [  143.837765] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam kernel: [  143.837768] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Aug  9 19:20:58 amsterdam kernel: [  143.837771] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam kernel: [  143.837773] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Aug  9 19:20:58 amsterdam kernel: [  143.837776] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam kernel: [  143.837778] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Aug  9 19:20:58 amsterdam kernel: [  143.837781] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam kernel: [  143.837784] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Aug  9 19:20:58 amsterdam kernel: [  143.837787] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam kernel: [  143.837789] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Aug  9 19:20:58 amsterdam kernel: [  143.837792] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam kernel: [  143.837794] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Aug  9 19:20:58 amsterdam kernel: [  143.837797] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam kernel: [  143.837800] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Aug  9 19:20:58 amsterdam kernel: [  143.837802] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam kernel: [  143.837806] cfg80211: World regulatory domain updated:
Aug  9 19:20:58 amsterdam kernel: [  143.837808] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug  9 19:20:58 amsterdam kernel: [  143.837811] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam kernel: [  143.837813] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam kernel: [  143.837816] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam kernel: [  143.837819] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam kernel: [  143.837822] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  9 19:20:58 amsterdam NetworkManager[845]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> (wlan0): device state change: 8 -> 3 (reason 11)
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> (wlan0): deactivating device (reason: 11).
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1632
Aug  9 19:21:13 amsterdam avahi-daemon[816]: Withdrawing address record for 192.168.1.35 on wlan0.
Aug  9 19:21:13 amsterdam avahi-daemon[816]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.35.
Aug  9 19:21:13 amsterdam avahi-daemon[816]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Activation (wlan0) starting connection 'Auto Livebox-B00F'
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Activation (wlan0/wireless): access point 'Auto Livebox-B00F' has security, but secrets are required.
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Activation (wlan0/wireless): connection 'Auto Livebox-B00F' has security, and secrets exist.  No new secrets needed.
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Config: added 'ssid' value 'Livebox-B00F'
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Config: added 'scan_ssid' value '1'
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Config: added 'psk' value '<omitted>'
Aug  9 19:21:13 amsterdam NetworkManager[845]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  9 19:21:13 amsterdam NetworkManager[845]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug  9 19:21:13 amsterdam NetworkManager[845]: <info> Config: set interface ap_scan to 1
Aug  9 19:21:16 amsterdam NetworkManager[845]: <info> (wlan0): supplicant connection state:  disconnected -> scanning

```

---

### Post by lkjoel on 2011-08-09
To restart the wifi:
```
sudo /etc/init.d/networking restart

```

---

### Post by wildmanne39 on 2011-08-09
Hi, run these commands please:
```
lspci -nn | grep 0280
```
```
sudo lshw -C network
```
```
lsmod
```
Thank you

---

### Post by Boxiflor on 2011-08-09
It didn't work. Thanks a lot for your quick answer. I like this forum :)

```

$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.

```

---

### Post by Boxiflor on 2011-08-09
Hi wildmanne39

```

$ lspci -nn | grep 0280
05:01.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]


$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: Ralink corp.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: wlan0
       version: 00
       serial: c8:3a:35:c1:85:a6
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=2.6.38-10-generic firmware=0.8 latency=32 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fa300000-fa307fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 6c:62:6d:ec:e2:73
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:d000(size=256) memory:dc104000-dc104fff memory:dc100000-dc103fff


$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
ipt_MASQUERADE         12663  0 
xt_state               12514  0 
ipt_REJECT             12512  0 
xt_tcpudp              12531  0 
iptable_filter         12706  0 
nf_nat_h323            12749  0 
nf_conntrack_h323      52200  1 nf_nat_h323
nf_nat_pptp            12536  0 
nf_conntrack_pptp      13562  1 nf_nat_pptp
nf_conntrack_proto_gre    13353  1 nf_conntrack_pptp
nf_nat_proto_gre       12671  1 nf_nat_pptp
nf_nat_tftp            12420  0 
nf_conntrack_tftp      12817  1 nf_nat_tftp
nf_nat_sip             16922  0 
nf_conntrack_sip       24652  1 nf_nat_sip
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12548  0 
nf_conntrack_ftp       13106  1 nf_nat_ftp
iptable_nat            12977  0 
nf_nat                 24827  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19024  3 iptable_nat,nf_nat
nf_conntrack           69744  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18125  2 iptable_filter,iptable_nat
x_tables               21907  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
binfmt_misc            13213  1 
parport_pc             32111  1 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hda_codec_hdmi     27535  4 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
nvidia               9766978  40 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
rt61pci                27265  0 
rt2x00pci              13986  1 rt61pci
rt2x00lib              39075  2 rt61pci,rt2x00pci
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              257001  2 rt2x00pci,rt2x00lib
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
cfg80211              156212  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt61pci
shpchp                 32345  0 
xpad                   17834  0 
ff_memless             12945  1 xpad
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
psmouse                73312  0 
joydev                 17322  0 
serio_raw              12990  0 
usbhid                 41704  0 
usb_storage            43946  0 
hid                    77084  1 usbhid
uas                    17676  0 
r8169                  42534  0 
xhci_hcd               68062  0 
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  2 rt61pci,firewire_core

```

---

