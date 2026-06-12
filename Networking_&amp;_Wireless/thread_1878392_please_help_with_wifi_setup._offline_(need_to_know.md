---
title: "please help with wifi setup. offline (need to know files)"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by slixz85 on 2011-11-09
hi, i have three operating systems on this machine.

i have working wifi connection on two of them. bodhi and ubuntu

the third is debian i installed from debian.org it is the cd and not the dvd because i didnt have a 4.7gb flash drive. The live cd was still 650 mb though so i figured it would have wifi setup already. bodhi does and it is only 370 mb.wow.

I am not sure if i can just copy some files in bodhi or ubuntu and move them over to debian because i have no idea where to get them either from which folder?

obviously since i have two working wifi setups i can download any files i need and just transfer them to the other partition.

this is the wifi driver i use. (can't even figure out which file under synaptic in bodhi it is.

Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp.

---

### Post by praseodym on 2011-11-09
Hi,

please show the outputs "as root" of:

```
uname -a
lsmod
iwconfig
rfkill list
iwlist scan
dmesg | egrep 'rt2|rt3'
```

---

### Post by slixz85 on 2011-11-09
> **praseodym said:**
> Hi,

please show the outputs "as root" of:

```
uname -a
lsmod
iwconfig
rfkill list
iwlist scan
dmesg | egrep 'rt2|rt3'
```

thanks for quick *** response. i did this from bodhi because iwconfig and iwlist don't even work in debian. it must need alot of packages off the live cd

root@gx260:~# uname -a
Linux gx260 3.0.0-12-generic #19 SMP Fri Sep 30 16:08:17 CDT 2011 i686 GNU/Linux
root@gx260:~# lsmod
Module                  Size  Used by
xt_limit               12570  8 
xt_tcpudp              12531  10 
ipt_LOG                12811  8 
ipt_MASQUERADE         12663  0 
xt_DSCP                12549  0 
ipt_REJECT             12512  1 
nf_conntrack_irc       13112  0 
nf_conntrack_ftp       13081  0 
xt_state               12514  6 
iptable_nat            12977  0 
nf_nat                 24663  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      18980  9 iptable_nat,nf_nat
nf_conntrack           69731  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
iptable_mangle         12615  0 
iptable_filter         12706  1 
ip_tables              18008  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21872  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
dm_crypt               22356  0 
arc4                   12473  2 
rt2800usb              22248  0 
rt2800lib              48549  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              19982  1 rt2800usb
rt2x00lib              47798  3 rt2800usb,rt2800lib,rt2x00usb
ppdev                  12900  0 
mac80211              267369  3 rt2800lib,rt2x00usb,rt2x00lib
snd_intel8x0           33232  3 
snd_ac97_codec        105569  1 snd_intel8x0
dcdbas                 14054  0 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                75935  3 snd_intel8x0,snd_ac97_codec
snd_timer              24609  2 snd_pcm
parport_pc             32006  1 
snd                    55680  8 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore              12600  1 snd
shpchp                 32300  0 
lp                     13349  0 
cfg80211              167037  2 rt2x00lib,mac80211
snd_page_alloc         14036  2 snd_intel8x0,snd_pcm
parport                36664  3 ppdev,parport_pc,lp
reiserfs              229640  2 
usbhid                 45614  0 
hid                    81147  1 usbhid
i915                  470128  2 
drm_kms_helper         32653  1 i915
drm                   191731  2 i915,drm_kms_helper
tulip                  52264  0 
e1000                 101066  0 
floppy                 59925  0 
i2c_algo_bit           13152  1 i915
video                  18792  1 i915
root@gx260:~# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Caton"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:25:9C:CC:B6:60   
          Bit Rate=5.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=33/70  Signal level=-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:835  Invalid misc:10   Missed beacon:0

root@gx260:~# rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
root@gx260:~# iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:25:9C:CC:B6:60
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Caton"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000dd6753ee89
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 00054361746F6E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD740050F204104A0001101044000102103B000103104700100000000000001000000000259CCCB6601021000C4C696E6B73797320496E632E10230007575254353447321024000776312E352E303110420001301054000800060050F20400011011000757525435344732100800020084103C000101
          Cell 02 - Address: 98:FC:11:C3:D6:4C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"TheIcon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000cdc01beb9
                    Extra: Last beacon: 1112ms ago
                    IE: Unknown: 000754686549636F6E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD930050F204104A00011010440001021041000100103B000103104700100000000000000001100098FC11C3D64C102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30341042000C4A555430304C3343313137301054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000

root@gx260:~# dmesg | egrep 'rt2|rt3'
[   18.890641] Registered led device: rt2800usb-phy0::radio
[   18.890676] Registered led device: rt2800usb-phy0::assoc
[   18.890705] Registered led device: rt2800usb-phy0::quality
[   18.897097] usbcore: registered new interface driver rt2800usb

---

### Post by slixz85 on 2011-11-09
while i have all that network info up also. you probably know what your looking at. do you see anything fishy with this bodhi setup? the network likes to sit idle when i click things until i click them again alot. it used to load pages up as soon as i clicked them

---

### Post by praseodym on 2011-11-09
Shut off the Power-Management, set the rate automatically, and remove the IPtables:

```
sudo iwconfig wlan0 power off
sudo iwconfig wlan0 rate auto
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
sudo service network-manager restart
iwconfig # from here controls
lsmod
sudo iwlist scan
```

---

### Post by slixz85 on 2011-11-09
> **praseodym said:**
> Shut off the Power-Management, set the rate automatically, and remove the IPtables:

```
sudo iwconfig wlan0 power off
sudo iwconfig wlan0 rate auto
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
sudo service network-manager restart
iwconfig # from here controls
lsmod
sudo iwlist scan
```

thanks alot man! it works as good as it i think it can. whatever the delay and idle problem was it is fixed now.



ace@gx260:~$ sudo lsmod
[sudo] password for ace: 
Module                  Size  Used by
xt_limit               12570  8 
xt_tcpudp              12531  10 
ipt_LOG                12811  8 
ipt_MASQUERADE         12663  0 
xt_DSCP                12549  0 
ipt_REJECT             12512  1 
nf_conntrack_irc       13112  0 
nf_conntrack_ftp       13081  0 
xt_state               12514  6 
iptable_nat            12977  0 
nf_nat                 24663  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      18980  9 iptable_nat,nf_nat
nf_conntrack           69731  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
iptable_mangle         12615  0 
dm_crypt               22356  0 
iptable_filter         12706  1 
ip_tables              18008  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21872  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
arc4                   12473  2 
rt2800usb              22248  0 
rt2800lib              48549  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              19982  1 rt2800usb
rt2x00lib              47798  3 rt2800usb,rt2800lib,rt2x00usb
snd_intel8x0           33232  1 
snd_ac97_codec        105569  1 snd_intel8x0
mac80211              267369  3 rt2800lib,rt2x00usb,rt2x00lib
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                75935  2 snd_intel8x0,snd_ac97_codec
snd_timer              24609  1 snd_pcm
cfg80211              167037  2 rt2x00lib,mac80211
snd                    55680  6 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore              12600  1 snd
snd_page_alloc         14036  2 snd_intel8x0,snd_pcm
ppdev                  12900  0 
shpchp                 32300  0 
parport_pc             32006  1 
dcdbas                 14054  0 
lp                     13349  0 
parport                36664  3 ppdev,parport_pc,lp
reiserfs              229640  2 
usbhid                 45614  0 
hid                    81147  1 usbhid
i915                  470128  2 
drm_kms_helper         32653  1 i915
drm                   191731  2 i915,drm_kms_helper
tulip                  52264  0 
floppy                 59925  0 
e1000                 101066  0 
i2c_algo_bit           13152  1 i915
video                  18792  1 i915
ace@gx260:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 98:FC:11:C3:D6:4C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"TheIcon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d991e5a31
                    Extra: Last beacon: 1116ms ago
                    IE: Unknown: 000754686549636F6E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD930050F204104A00011010440001021041000100103B000103104700100000000000000001100098FC11C3D64C102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30341042000C4A555430304C3343313137301054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: 00:25:9C:CC:B6:60
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Caton"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000de24710171
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 00054361746F6E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD740050F204104A0001101044000102103B000103104700100000000000001000000000259CCCB6601021000C4C696E6B73797320496E632E10230007575254353447321024000776312E352E303110420001301054000800060050F20400011011000757525435344732100800020084103C000101

ace@gx260:~$ 


i could still use some help on figuring out the wifi for the debian install if you get the time. or anyone else reading this.

the debian install is missing alot of dependencies. i have been going to debian package website and downloading a few at a time but every program has about 4 missing. is there a file anyone knows of too be able to install all the stuff like binutils, etc or anything that is commonly shared?

---

### Post by praseodym on 2011-11-09
The iptables are still there (by default in 11.10), so imho it was the Power Management (plus some percentage from the rate). For Debian you should use the package manager (Synaptic?) to install packages with their dependencies. 11.10 lacks the package synaptic, but it can be installed via software center.

---

### Post by slixz85 on 2011-11-09
> **praseodym said:**
> The iptables are still there (by default in 11.10), so imho it was the Power Management (plus some percentage from the rate). For Debian you should use the package manager (Synaptic?) to install packages with their dependencies. 11.10 lacks the package synaptic, but it can be installed via software center.


yeah thanks. i have synaptic installed in debian. but i can tell it is missing alot of packages. it has 550 or so and bodhi has 880 or so by default and it is only 370mb to like 675 of debians. so i installed debian thinking it would be network ready since it was two times the size. it runs smooth i would like to keep it but with no wifi i can't download the packages. i share internet with a friend and only get wifi, i have no way to download updates with synaptic since i dont have an ethernet cable to plug in anywhere. btw bodhi is the system i applied your wifi changes to it is based on 10.04 lts. but i have ubuntu 11.10 installed and it runs wifi out of the box.

if i were to get debian to run the wifi then, is my only chance to install these dependencie packages one at a time, or is there a bulk debian package i can download that has a lot of shared dependencies? i just been transferring packages from my bodhi linux with wifi to the partition of debian to install what i have so far, which is not much.

---

### Post by praseodym on 2011-11-10
Ubuntu packages can be downloaded from [http://packages.ubuntu.com](http://packages.ubuntu.com)

Debian packages from debian.org

---

### Post by slixz85 on 2011-11-10
yeah i have checked those websites my only problem is i cant figure out what to get to make my wifi work

---

### Post by slixz85 on 2011-11-10
i need ALOT of dependencies. i'm wondering if my iso could have had a flaw downloading it

---

### Post by praseodym on 2011-11-10
Before you download the packages one-by-ony I recommend buying a 5 $ Ethernet cable. This is much safer if the connection drops during system updates

---

### Post by slixz85 on 2011-11-10
thats just my problem. i am sharing a friends wifi. i am in an apartment building they are on the other side. i pick up 65 percent connection most of time on average 75 if lucky.

so this is why I have been wanting to figure out what debian files i need so on this system with the three os's i can just copy the files to the sda4 partition that the debian install is on, since this bodhi and the other operating system i got connect fine. my problem is just with this debian install.

---

### Post by slixz85 on 2011-11-14
> **praseodym said:**
> Shut off the Power-Management, set the rate automatically, and remove the IPtables:

```
sudo iwconfig wlan0 power off
sudo iwconfig wlan0 rate auto
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
sudo service network-manager restart
iwconfig # from here controls
lsmod
sudo iwlist scan
```

starting to have a problem with this again. i dont know why i didnt post here but my last post at [http://ubuntuforums.org/showthread.php?t=1880063](http://ubuntuforums.org/showthread.php?t=1880063) shows more info on what is goin on. please take a look at it. the wifi is disconnecting randomly hasnt did this before on some os's just cant remember em. i am hoping you might know some more terminal commands to really found out what is goin, on. thanks for helpin

---

### Post by northd_tech on 2011-11-15
> **slixz85 said:**
> 
if i were to get debian to run the wifi then, is my only chance to install these dependencie packages one at a time, or is there a bulk debian package i can download that has a lot of shared dependencies? i just been transferring packages from my bodhi linux with wifi to the partition of debian to install what i have so far, which is not much.

I haven't run Debian (other than rescue disc and antivirus versions) for any extended periods of time, so I'm not sure about all the Wheezy, Sid, Lenny, and Squeeze business.

Regardless, these 2 pages looked like they might list your dependencies/suggested packages in more 'centralized' locations and might save you a lot of searching:

[B]   rt2800usb
Ralink RT2070, RT2770, RT2870, RT3070, RT3071, RT3072, RT3370, RT3572, RT5370 devices (rt2800usb)[/B]
[http://wiki.debian.org/rt2800usb#supported](http://wiki.debian.org/rt2800usb#supported)

**Package: firmware-ralink (0.28+squeeze1) [non-free] **
[http://packages.debian.org/squeeze/firmware-ralink](http://packages.debian.org/squeeze/firmware-ralink)

If that Ralink is anything like the Broadcom wireless (and several other devices) that I'm familiar with, you are likely missing some firmware file(s).  Those 2 pages looked pretty close to your Debian wireless problem area to me.

---

### Post by slixz85 on 2011-11-15
> **northd_tech said:**
> I haven't run Debian (other than rescue disc and antivirus versions) for any extended periods of time, so I'm not sure about all the Wheezy, Sid, Lenny, and Squeeze business.

Regardless, these 2 pages looked like they might list your dependencies/suggested packages in more 'centralized' locations and might save you a lot of searching:

[B]   rt2800usb
Ralink RT2070, RT2770, RT2870, RT3070, RT3071, RT3072, RT3370, RT3572, RT5370 devices (rt2800usb)[/B]
[http://wiki.debian.org/rt2800usb#supported](http://wiki.debian.org/rt2800usb#supported)

**Package: firmware-ralink (0.28+squeeze1) [non-free] **
[http://packages.debian.org/squeeze/firmware-ralink](http://packages.debian.org/squeeze/firmware-ralink)

If that Ralink is anything like the Broadcom wireless (and several other devices) that I'm familiar with, you are likely missing some firmware file(s).  Those 2 pages looked pretty close to your Debian wireless problem area to me.

thanks,  i will try this on the debian install right now i have pinguy mini 64 bit bodhi 32 bit and debian. i am about to check out those websites and see if that fixes it. i will have to get back to ya tomorrow maybe, but somethin wierd was i dont know how linux works all the way and, on some distros i have used synaptic would show my rt2800 driver i could download, but bodhi is using it and in the synaptic for it it is not listed. so since i dont know how linux works i am probably way off. but could the wifi drivers somehow been embedded hidden somewhere cause i have search as much as i think i can in bodhi's synaptic.

---

### Post by slixz85 on 2011-11-15
reason being i need 3 operating systems with wifi, is i have had two before and i like to experiment to learn so i have crashed a couple. i just always want one available that i can transfer files from partition to partition if i have too.

---

### Post by slixz85 on 2011-11-15
how does this got a tag for ralink 3070. my driver says rt2800usb. i never put a tag on this topic

---

### Post by northd_tech on 2011-11-15
> **slixz85 said:**
> how does this got a tag for ralink 3070. my driver says rt2800usb. i never put a tag on this topic

Um, because of what you told us in post #1:
> **slixz85 said:**
> 
this is the wifi driver i use. (can't even figure out which file under synaptic in bodhi it is.

Bus 001 Device 002: ID 148f:**3070 Ralink** Technology, Corp.

That looks like some sort of output from an **lsusb** terminal command (which I believe LiSts USB hardware) to me. ;)  

I tagged it with 'ralink 3070' because that is apparently the **specific** member of the more general Ralink 2800usb family (that I provided those Debian links to above- take another look at that boldface heading):

[http://wiki.debian.org/rt2800usb](http://wiki.debian.org/rt2800usb)
> **Ralink RT2070, RT2770, RT2870, [COLOR="Red"]RT3070[/COLOR], RT3071, RT3072, RT3370, RT3572, RT5370 devices (rt2800usb)**

This page describes how to enable support for[COLOR="Blue"] WiFi devices based on Ralink 802.11n USB chipsets[/COLOR] on Debian systems. 

I believe that nearly anyone at UF can tag any thread with nearly anything they want (I prefer them to be **highly** hardware specific though).  I also prefer to use an already-existing tag ("ralink 3070" in this case, and I did not see a "ralink 2800" or "rt2800" tag of any kind).   It is an EXTREMELY helpful forum resource though (if ***more*** people would just use it):

[http://ubuntuforums.org/tags.php?tag=ralink+3070](http://ubuntuforums.org/tags.php?tag=ralink+3070)

---

### Post by northd_tech on 2011-11-15
> **slixz85 said:**
>  i am about to check out those websites and see if that fixes it. i will have to get back to ya tomorrow maybe, but somethin wierd was i dont know how linux works all the way and, on some distros i have used synaptic would show my rt2800 driver i could download, but bodhi is using it and in the synaptic for it it is not listed. so since i dont know how linux works i am probably way off. but could the wifi drivers somehow been embedded hidden somewhere cause i have search as much as i think i can in bodhi's synaptic.

Have you compared these files in the Debian vs. the Bodhi partitions against each other?

```
cat /etc/apt/sources.list
ls /etc/apt/
```[https://help.ubuntu.com/community/SourcesList](https://help.ubuntu.com/community/SourcesList)
[https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

---

### Post by slixz85 on 2011-11-17
> **northd_tech said:**
> Um, because of what you told us in post #1:


That looks like some sort of output from an **lsusb** terminal command (which I believe LiSts USB hardware) to me. ;)  

I tagged it with 'ralink 3070' because that is apparently the **specific** member of the more general Ralink 2800usb family (that I provided those Debian links to above- take another look at that boldface heading):

[http://wiki.debian.org/rt2800usb](http://wiki.debian.org/rt2800usb)


I believe that nearly anyone at UF can tag any thread with nearly anything they want (I prefer them to be **highly** hardware specific though).  I also prefer to use an already-existing tag ("ralink 3070" in this case, and I did not see a "ralink 2800" or "rt2800" tag of any kind).   It is an EXTREMELY helpful forum resource though (if ***more*** people would just use it):

[http://ubuntuforums.org/tags.php?tag=ralink+3070](http://ubuntuforums.org/tags.php?tag=ralink+3070)


yeah strange. lsusb is the command i used for that not paying attention. 
ace@ThinkCentre:~$ lsusb
Bus 002 Device 002: ID 04b3:310c IBM Corp. Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ace@ThinkCentre:~$ 

but all other wifi commands i been using show that rt2800usb?
but yeah it is a usb dongle wifi adapter on a pc

---

