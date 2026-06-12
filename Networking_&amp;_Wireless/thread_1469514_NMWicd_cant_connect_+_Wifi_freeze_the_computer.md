---
title: "NM/Wicd cant connect + Wifi freeze the computer"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by MightyMouse on 2010-05-02
I have updated to Lucid and experience serious Wifi problems, as do apparently a lot of people. After the update my built-in WiFi card was not automatically detected (I have a SMC 2802W which was detected out-of-the-box with Karmic). This problem I solve with installing linux-firmware-nonfree-1.6 (see [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/509265](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/509265)), after that my WiFi card was detected.

Here my basic info:
lspci:
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0b.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:50:bf:e3:15:ec  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:fee3:15ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10933 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8555922 (8.5 MB)  TX bytes:1309199 (1.3 MB)
          Interrupt:17 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:04:e2:d6:4a:76  
          inet6 addr: fe80::204:e2ff:fed6:4a76/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2533 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:108952 (108.9 KB)  TX bytes:22696 (22.6 KB)


iwconfig: (the wireless is not connected but I can see my AP when I click on the NM icon as available)
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:">\x05\xF1\xEC\xD9g3\xB7\x99P\xA3\xE3\x14\xD3\xD94\xF7^\xA0\xF2\x10\xA8\xF6\x05\x94\x01\xBE\xB4\xBCDx\xFA"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


lsmod:
Module                  Size  Used by
binfmt_misc             6587  1 
arc4                    1153  2 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_via82xx            20058  2 
snd_ac97_codec        100646  1 snd_via82xx
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          7076  2 snd_via82xx,snd_pcm
snd_mpu401_uart         5617  1 snd_via82xx
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nouveau               467048  1 
ttm                    49943  1 nouveau
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29297  1 nouveau
p54pci                  6948  0 
drm                   162471  3 nouveau,ttm,drm_kms_helper
p54common              24225  1 p54pci
led_class               2864  1 p54common
i2c_algo_bit            5028  1 nouveau
snd                    54148  15 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ns558                   3056  0 
sn9c102               137320  0 
i2c_viapro              5573  0 
ppdev                   5259  0 
mac80211              209734  2 p54pci,p54common
via_ircc               21745  0 
via_agp                 5310  1 
gameport                9089  3 snd_via82xx,ns558
videodev               34361  1 sn9c102
v4l1_compat            13251  1 videodev
psmouse                63245  0 
serio_raw               3978  0 
parport_pc             25962  1 
cfg80211              130639  2 p54common,mac80211
soundcore               6620  1 snd
shpchp                 28820  0 
irda                  186556  1 via_ircc
crc_ccitt               1339  1 irda
agpgart                31724  3 ttm,drm,via_agp
compat_firmware_class     7043  1 p54pci
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
8139too                18545  0 
pata_via                7272  3 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
floppy                 53016  0 

sudo lshw -C network:
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 10
       serial: 00:50:bf:e3:15:ec
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.0.1 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:17 ioport:d000(size=256) memory:ea002000-ea0020ff
  *-network:1
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wlan1
       version: 01
       serial: 00:04:e2:d6:4a:76
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=p54pci driverversion=2.6.32-21-generic firmware=N/A latency=32 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:ea000000-ea001fff


Now the problems

I use the network-manager but have also tried Wicd with no sucess. Both NM and Wicd have problems with connecting to the AP. Both Wicd and NM keep asking for the password (which is definitely correct, checked more than once, Wicd claims I use a 'bad password', NM just keeps asking for the password and at some point gives up) and seem to 'see' the AP and my Network.
When I disconnect from the wired connection I can not get NM to connect, this is what I see if I iwconfig during the scan

anja@anja-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"privat16B486"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:68:DD:0F:AB   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


this goes on for some minutes and finally says I am disconnected, then iwconfig gives this:


anja@anja-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"\x05\xEF\xF7\x00\xE9\xA1:\xE5\xCA\x0B\xCB\xD0HGd\xBD\x1F#\x1E\xA8\x1C{d\xC5\x14sZ\xC5^Kyc"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

On occasion I actually had a wirelss connection, to have this I have to pull the wired connection, restart the computer and at least once or twice I then had a working connection (both with Wicd and NM). Unfortunately once I open a web browser and attempt to connect to the Internet not only is the connection slow as a snail but the computer completely freezes and needs a hard restart to come to live (again, both with NM and Wicd!).

Obviously there are some issues between NM and the AP and Lucid that make it almost impossible to get the Wifi working.

In Karmic installing Wicd instead of NM was a simple solution but unfortunately in Lucid this doesn't seem to do the trick any longer.

Are there others that experience these problems and has anybody figure out how to solve these?

Main issues are:
1. NM/Wicd can't connect to AP (WEP 128-bit passphrase in NM/Wicd has worked before and still is on other Computers connected to the same AP)
2. Once Wifi is up it completely freezes the computer somewhere between 1-5 minutes after a Browser has tried to get access.

Any help is greatly appreciated!

MightyMouse

---

### Post by MightyMouse on 2010-05-02
Anyone? :confused:

---

### Post by MightyMouse on 2010-05-03
bump

---

### Post by cblah001 on 2010-05-04
Honestly, I'm new to Linux and have been on less than a week. I was experiencing the problem where I could connect via the ethernet cable but not through the wireless. What I had to do is update the drivers from the "system" tab. I think it was System>Administration>Check Drivers, or something to that accord. Then it listed the wireless card drivers that I needed, I downloaded them, restarted, and connected right away.
 
I would tell you the exact path that I went through but I am on my Windows 7 OS right now since my system is also freezing once I connect through the WiFi after a few minutes.

---

### Post by MightyMouse on 2010-05-10
Hi, thanks for the suggestion but unfortunately I have no drivers in that section. And in fact my card is detected, just not able to connect to the network properly. 

Cheers,
MightyMouse

---

### Post by konradpiskorz on 2010-05-10
Hello MightyMouse

I am having the exact same problem as you have described.  Although I have a little to add, hopefully we can solve this together.

First off wireless was working perfectly fine for few days after installing Lucid.  No odd behaviour, no disconnections.  No update's were installed during the time when it stopped working however.  Wireless just completely crapped out as I was browsing the internet and started acting just as you had described, always asking for a password even though it's correct.  However I must add that my neighbours unprotected wireless is also inaccessible.

nm-applet will not allow me to connect with either wired or wireless.  As you stated before, wireless keeps asking for the password again and again until it fails.  For an unprotected AP, it simply fails to connect.

WICD also fails saying bad password or just fails to connect to an unprotected AP.  I will parse my logs to see if I can find anything of value.  Could it be a kernel issue?  I haven't ever had these problems running Ubuntu Gutsy, Hardy or Debian etch, lenny, squeeze or Gentoo...

Hardware: Toshiba Tecra A6
Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

---

### Post by sidarali on 2010-05-11
Hello, I have the same behaviour as konradpiskorz described. Wireless was working fine after upgrade but then after reboot password is rejected by wifi accesspoint. 
Have to use wired connection now :(
__

---

### Post by konradpiskorz on 2010-05-14
I might add that my wired stopped working through nm-applet but would work if I set it up as the following in /etc/network/interfaces

> auto eth0
iface eth0 inet dhcp

Then in terminal would write out
> killall nm-applet
sudo ifconfig eth0 down
sudo ifconfig eth0 up

Then I'd get a wired connection...

Well it is working now.  I changed my /etc/network/interfaces to say
> iface eth0 inet static
Note the lack of auto eth0.

Then in /etc/NetworkManager
> [main]
plugins=ifupdown,keyfile

#no-auto-default=00:16:d4:8b:73:a9,

[ifupdown]
managed=true

I changed managed from false to true and commented out the no-auto-default line and both my wired and wireless started working again...  The problem is I don't understand WHY this would cause a problem...  Or if it this was even why the problem became fixed, but it is working consistantly since I made those changes...

---

### Post by MightyMouse on 2010-05-18
Well,

I have not worked on this problem because I am seriously considering downgrading that specific computer back to Karmic. 
There are all kinds of suggestions on the forums about changing the type of security or turning it off but that seems the wrong approach to me. I have several computers on the same wireless router and would not want to have to run in problems with those just to 'solve' a Lucid problem. My advice is to wait and downgrade until Canonical has figured out why Lucid is causing this much problems. Main argument for this approach is that even if one finds a work-around this might be broken with the next update. Unless the undelying problem is fixed it's not worth trying to fix one's own computer. Seeing the number of complains and postings (not only in the wireless section) concerning Lucid, maybe this time it might be better to sit it out.

MightyMouse

---

### Post by linuxd00 on 2010-05-29
i seem to have a similar problem:

[http://ubuntuforums.org/showthread.php?t=1495857](http://ubuntuforums.org/showthread.php?t=1495857)

anyone found a solution?

is wifi so broken? there seems to be some problems with the ath5k driver. How can i change it?

---

### Post by sushiseru on 2010-09-18
Ok, firstly the basic rule of wireless connecting is Network Manager is no good. I won't trash it here, but that program needs work.

So the general rule is ONE or the OTHER.
You can't not have BOTH wicd and network-manager on the same machine at the same time. I tried it - I was tearing my hair out for hours before something told me to remove NM.

So remove network-manager ... I'm on KDE so I don't know how to do it graphically in GNOME, but type in Terminal (Gnome)/Konsole (KDE):

Make sure to have wicd already installed otherwise you won't be able to dl it after removing NM and will have to reinstall it from the disc and then get wicd.

sudo apt-get remove network-manager

So now open wicd and you should then be able to connect...

If your wireless network is hidden... you need to follow the steps here:
[https://bugs.launchpad.net/wicd/+bug/388116](https://bugs.launchpad.net/wicd/+bug/388116)

Otherwise your wireless network will come out like /x00/x00/x00 where /x00 = length of the SSID name in letters and will result in a "bad password error"

As for drivers... I got my drivers from the compatwireless package somewhere on the internet when I was Kubuntu 8.10...

However if it was set up OOTBox on Karmic, same should be on Lucid.

Comp specs:
I am on a ThinkPad T60 w/ an Intel Centrino 3945ABG wireless ... thingy.

---

