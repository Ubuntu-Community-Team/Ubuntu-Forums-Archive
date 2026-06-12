---
title: "Atheros AR8151 drivers"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by corkscrew on 2011-07-17
Hi have a toshiba satellite L745 running Lucid Lynx

I need drivers for the Atheros AR8151 ethernet card.

Every post I have read on installing the driver give links to Atheros but they are all broken.

Does anybody know where I can download driver?

---

### Post by wildmanne39 on 2011-07-17
> **corkscrew said:**
> Hi have a toshiba satellite L745 running Lucid Lynx

I need drivers for the Atheros AR8151 ethernet card.

Every post I have read on installing the driver give links to Atheros but they are all broken.

Does anybody know where I can download driver?
Hi, I am looking to see if I can find the driver.

---

### Post by corkscrew on 2011-07-17
yes i found that as well but i just get errors when trying to follow the instructions in that link

---

### Post by wildmanne39 on 2011-07-17
Hi, is it the driver that you need? or just the patch? If you are not sure run these commands in a terminal
```
sudo lshw -C network 
```
```
lsmod
```
```
lspci -nn
```
```
rfkill list All
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by corkscrew on 2011-07-17
took a little time because i have t copy & paste to txt file then transfer by usb stick to this machine here are the outputs from all the commands
```
:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:c5:2e:87
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:c3200000-c320ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:0a:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:c3100000-c313ffff ioport:2000(size=128)
============================================

:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat
usb_storage            49961  1 
rfcomm                 40393  4 
binfmt_misc             7960  1 
ppdev                   6375  0 
sco                     9649  2 
bridge                 53216  0 
stp                     2171  1 bridge
bnep                   11884  2 
l2cap                  34807  16 rfcomm,bnep
joydev                 11104  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  1 
vgastate                9857  1 vga16fb
snd_hda_intel          25741  2 
arc4                    1473  2 
snd_hda_codec          85759  1 snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 329117  0 
mac80211              238896  1 ath9k
nouveau               515227  0 
ttm                    60847  1 nouveau
snd                    71251  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath                     9723  1 ath9k
drm_kms_helper         30742  1 nouveau
btusb                  13001  2 
bluetooth              58685  9 rfcomm,sco,bnep,l2cap,btusb
uvcvideo               62819  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
video                  20623  0 
output                  2503  1 video
cfg80211              148725  3 ath9k,mac80211,ath
soundcore               8052  1 snd
led_class               3764  1 ath9k
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
drm                   198948  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
xhci                   41830  0 
psmouse                64576  0 
serio_raw               4918  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   37870  4 
==============================================
:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Sandy Bridge PCI Express Root Port [8086:0101] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b4)
00:1c.5 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 6 [8086:1c1a] (rev b4)
00:1c.6 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 7 [8086:1c1c] (rev b4)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a4)
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1c49] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 04)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0dec] (rev a1)
01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0bea] (rev a1)
08:00.0 USB Controller [0c03]: NEC Corporation Device [1033:0194] (rev 04)
09:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
0a:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)
==================================================

:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

---

### Post by corkscrew on 2011-07-17
i have replied below to all your commands

---

### Post by wildmanne39 on 2011-07-17
Hi, it looks like you do need drivers for the ethernet. 

Also you have a AR9285 Wireless Network Adapter in your computer do you want to try and get it working? Or have you clicked on the internet icon in the top right corner to see if wireless is enabled? Let me know if it is already working. 

I have done a lot of searching and for now there is no new driver atheros was bought out and the new company has not posted any drivers. What errors did you get when you tried to install the one I had in the link earlier?

---

### Post by corkscrew on 2011-07-17
There is no wireless available where I am at the moment but the card is recognized. I only have LAN access. Basiclly I have 2 laptops the one i am trying to set up is new and i have just installed lucid on it from a disk without internet access.So there will be load of updates missing.
I think the one in the link is just a patch anyway I run the tar command ok but when i run the make install i get
> make: *** no rule to make target 'install'.stop 

---

### Post by wildmanne39 on 2011-07-17
> **corkscrew said:**
> There is no wireless available where I am at the moment but the card is recognized. I only have LAN access. Basiclly I have 2 laptops the one i am trying to set up is new and i have just installed lucid on it from a disk without internet access.So there will be load of updates missing.
I think the one in the link is just a patch anyway I run the tar command ok but when i run the make install i get
Hi, yes it is a patch the other post said that the driver is included in the kernel and just needs a patch to make it work. 

I have never seen a ethernet card that did not work by default so it probably does just need the patch, but that one may be to old for the kernel in natty.

Run this command it is suppose to tell everything that is loaded by the kernel.
```
sudo lspci -k
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by corkscrew on 2011-07-17
Here you go looks like there is adriver of some sort loaded btw its Lucid


```
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 6 (rev b4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.6 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 7 (rev b4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 04)
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
	Kernel modules: i2c-i801
01:00.0 VGA compatible controller: nVidia Corporation Device 0dec (rev a1)
	Kernel modules: nvidiafb, nouveau
01:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)
08:00.0 USB Controller: NEC Corporation Device 0194 (rev 04)
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Kernel driver in use: ath9k
	Kernel modules: ath9k
0a:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)
callum@L745:~$ callum@L745:~$ rfkill list all
callum@L745:~$: command not found
callum@L745:~$ 0: hci0: Bluetooth
0:: command not found
callum@L745:~$ Soft blocked: no
Soft: command not found
callum@L745:~$ Hard blocked: no
No command 'Hard' found, did you mean:
 Command 'card' from package 'a2ps' (universe)
Hard: command not found
callum@L745:~$ 1: phy0: Wireless LAN
1:: command not found
callum@L745:~$ Soft blocked: no
Soft: command not found
callum@L745:~$ Hard blocked: no
```

---

### Post by wildmanne39 on 2011-07-17
Hi, the one you saw is for your wireless card, I did not see one for your ethernet card. I am about to go to bed, I will check on this thread tomorrow, hopefully someone will pop in here that knows where and how to get the driver.

---

### Post by corkscrew on 2011-07-17
the very last entry says Athernot ethernet card ?

---

### Post by wildmanne39 on 2011-07-17
> **corkscrew said:**
> the very last entry says Athernot ethernet card ?
Hi, yes I saw that last night but it does not show any drivers in use for it. I asked a friend to take a look maybe he knows how to get the driver.

---

### Post by nm_geo on 2011-07-17
i found this link where others got the driver working.  Tough to do if you have no internet but you do have flash drive and another connection.

[http://ubuntuforums.org/showthread.php?t=1677122](http://ubuntuforums.org/showthread.php?t=1677122)

Check that one out.

---

### Post by wildmanne39 on 2011-07-17
> **nm_geo said:**
> i found this link where others got the driver working.  Tough to do if you have no internet but you do have flash drive and another connection.

[http://ubuntuforums.org/showthread.php?t=1677122](http://ubuntuforums.org/showthread.php?t=1677122)

Check that one out.Hi, thanks geo I showed that one to him last night he tried it but it did not work, and he has no way to use his wireless card he only has a wired connection where he lives.
I appreciate any ideas you come up with.

---

### Post by nm_geo on 2011-07-17
That is a tough one for sure .. Maybe Chili555 might have an idea.

---

### Post by chili555 on 2011-07-17
I believe this card wants the module atl1c. I'd download the tarball for compat-wireless.  [http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball](http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball)

Install linux-headers and build-essential: I think they're on the CD or DVD. Extract the package and do:```
cd Desktop/compat
```Press the Tab key so the rest fills in.```
./scripts/driver-select atl1c
make
sudo make install
sudo modprobe atl1c
```This is not intended to be an exhaustive tutorial; hopefully wildmanne39 and nm_geo can take over while I eat supper.

---

### Post by wildmanne39 on 2011-07-17
Hi chili555, thank you for your help I greatly appreciate it.

---

### Post by corkscrew on 2011-07-17
how do I do this > Install linux-headers and build-essential: I think they're on the CD or DVD.from disk? I presume you mean the lucid install disk

---

### Post by nm_geo on 2011-07-17
> **corkscrew said:**
> how do I do this from disk? I presume you mean the lucid install disk


You are correct.. You use the CD that you installed from.. It would be nice if they were already installed.

Open Synaptic  Package Manager
go to Settings>Repositories select/click the CD on in the box
Then search in the Synaptic search box for the packages below
install the build-essential  and linux-headers-generic

The we will figure out a way to get the Linux compat-wireless on your desktop and do what Chili555 said with it.

Be back in a few going to boot up my Lucid version.

---

### Post by corkscrew on 2011-07-17
Hi I'm at work now so i'll have to do it when i get back tonight I have downloaded the package chilli suggested and have it on a usb stick so I can copy onto laptop when i get back (i'm in australia at the moment so big time difference

---

### Post by nm_geo on 2011-07-17
> **corkscrew said:**
> Hi I'm at work now so i'll have to do it when i get back tonight I have downloaded the package chilli suggested and have it on a usb stick so I can copy onto laptop when i get back (i'm in australia at the moment so big time difference
no problem
 
If you find a wifi hot spot there somewhere down-under like a coffee house or a friend it might be faster if the wireless picks up. But this is good practice too. If you do find wireless get the build-essential and the linux-headers-generic..;  deleted bad information..

---

### Post by wildmanne39 on 2011-07-17
Hi, looks like your getting there.

---

### Post by corkscrew on 2011-07-17
ok just so i am clear dont want to muck this up

First I > get the build-essential and the linux-headers-generic then do the red line below
After I have done that do i still need to do the instructions chilli gave?

---

### Post by corkscrew on 2011-07-17
making progress will see tonight when I try some of this out

many thanks for everybody's help

---

### Post by wildmanne39 on 2011-07-17
> **corkscrew said:**
> making progress will see tonight when I try some of this out

many thanks for everybody's helpHi, yes after you get the headers you need to do what chili said, he is the expert here for networking that is why I asked for help.

---

### Post by nm_geo on 2011-07-18
> **corkscrew said:**
> ok just so i am clear dont want to muck this up
 
First I 
After I have done that do i still need to do the instructions chilli gave?
 
My reply was not correct [COLOR=red]**do not do the red lined info**[/COLOR]...
I did not get the driver you need doing that red lined stuff. I am going to follow Chili555 instructions to you and see how it goes here.
 
**_Do what Chili555 said._**

Ok, at lunch today I downloaded the latest dated tar ball and extracted it did a make and installed the atl1c driver and it has your ethernet drive pci number listed (so it should work). I did this in Lucid 10.04 to make sure.. I have to assume your laptop is like a pretty new model correct? I will post the modinfo later today when I am back on my Linux Box.

---

### Post by wildmanne39 on 2011-07-18
Hi, when you have time let us know how it is going.

---

### Post by corkscrew on 2011-07-18
Hi Guys,
just red your message in time about not doing > the red linelast night after work I found a wifi hot spot it connected straight away!! I downloaded > build-essential and the linux-headers-generic and a whole lot of other updates (140mb) but forgot the red line instruction!!

nm_geo you are correct the laptop is brand new a toshiba L745, so am i ok to try the Chilli555 instructions now ? or do I wait I could have a go in my lunch hour

---

### Post by wildmanne39 on 2011-07-18
Hi, you are clear to do it as soon as you like. Just follow chili555 directions and post back if you need help.

---

### Post by nm_geo on 2011-07-18
> **wildmanne39 said:**
> Hi, you are clear to do it as soon as you like. Just follow chili555 directions and post back if you need help.
 
+1 I agree you are cleared for take-off. Use the Chili555 method .. It will provide the driver you need ... even though I do not use or need the athl1c I did it today at lunch just to do it, and like wildmanne says we will be here if you need a little help.. Out till later

---

### Post by chili555 on 2011-07-18
Go, man, go! We are all waiting with fingers crossed (making it hard to type answers to posts!)

---

### Post by corkscrew on 2011-07-19
Eureka !!!!!!

Worked 1st time many thanks too you all, just reminds me why I swapped from windows all the great help out there

---

### Post by chili555 on 2011-07-19
> **corkscrew said:**
> Eureka !!!!!!

Worked 1st time many thanks too you all, just reminds me why I swapped from windows all the great help out thereAwesome! We are all happy it's working. Whenever Update Manager gives you a new kernel version or linux-image as it's known in Ubuntu World, you'll need to rebuild the driver for the newer kernel:```
[COLOR="Red"]./scripts/driver-select restore[/COLOR]
./scripts/driver-select atl1c
[COLOR="Red"]make clean[/COLOR]
make
sudo make install
sudo modprobe atl1c
```Please make a note of this for the future.

Finally, please use thread tools at the top and Marked Solved.

---

### Post by nm_geo on 2011-07-19
Anothther happy camper.. That compat-wireless and chili555 gets 'er done..
Please mark Solved for others corkscrew..

---

### Post by wildmanne39 on 2011-07-19
Hi, I am happy that it is working, and I am grateful for the help of chili555 and nm_geo.

---

### Post by corkscrew on 2011-07-19
> **chili555 said:**
> Awesome! We are all happy it's working. Whenever Update Manager gives you a new kernel version or linux-image as it's known in Ubuntu World, you'll need to rebuild the driver for the newer kernel:```
[COLOR="Red"]./scripts/driver-select restore[/COLOR]
./scripts/driver-select atl1c
[COLOR="Red"]make clean[/COLOR]
make
sudo make install
sudo modprobe atl1c
```Please make a note of this for the future.

Finally, please use thread tools at the top and Marked Solved.

Do I have to re install the driver 1st from the tar ball or just do the above ie

---

### Post by chili555 on 2011-07-19
> **corkscrew said:**
> Do I have to re install the driver 1st from the tar ball or just do the above ieYou should certainly do:```
cd Desktop/compat-whatever
```before you recompile, substituting your details of course.

---

### Post by corkscrew on 2011-07-19
> **chili555 said:**
> You should certainly do:```
cd Desktop/compat-whatever
```before you recompile, substituting your details of course.

So for completeness I want too keep this in a txt file I can refer to any time I upgrade kernel I do

download the tarball for compat-wireless or do I use the one I have now?


cd Desktop/compat

```
./scripts/driver-select atl1c
make
sudo make install
sudo modprobe atl1c

./scripts/driver-select restore
./scripts/driver-select atl1c
make clean
make
sudo make install
sudo modprobe atl1c 
```

---

### Post by chili555 on 2011-07-19
> I use the one I have now?Yes, until at some point it no longer works; many years from now. Then you'll need a new copy. By then, you may have upgraded to a more recent Ubuntu version, Zippy Zebra, that includes atl1c.

```
cd Desktop/compat
```Press Tab so the remainder of the file name fills in; then press Enter.
```
./scripts/driver-select restore
./scripts/driver-select atl1c
make clean
make
sudo make install
sudo modprobe atl1c

```

---

### Post by aidan.whitehouse on 2012-09-04
I have found package linux-backports-modules-compat-wireless-3.3-lucid-generic which would be a better solution for keeping things up-to-date.  Of course the initial pointer to get things working is needed if you don't have an alternative network connection on the same computer...

---

