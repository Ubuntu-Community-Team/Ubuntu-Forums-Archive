---
title: "WNA3100 detects every wireless network apart from my own"
date: 2013-03-14
forum: Networking &amp; Wireless
---

### Post by russco on 2013-03-14
So, I finally managed to get my WNA3100 working with 12.04.  

I have to use 12.04, as 12.10 is not compatible with my old laptop.

But I have a problem.  

I can pick up every single wireless network in the area, except my own.

I have tried the adapter in my windows laptop, and it detects it just fine, the internet works great.

So what do you think's going on here?  

I have a hunch it's something to do with the security on the wireless router (WPA & WPA2).  Incidentally, the router is a D-Link DIR 645 using D-Link's latest firmware - v1.03.

Please help, it's doing my head in, and I've been trying stuff for days!

---

### Post by praseodym on 2013-03-14
Try these:[LIST]
[*]
[*]
[*]No hidden network
[*]Fixed channel
[*]pure WPA2-AES
[*]MAC-address filter=off
[/LIST]
Check:```

iwconfig
lsmod
sudo iwlist scan
iwlist chan
```

---

### Post by russco on 2013-03-15
Okay, results:

No hidden network - Check.  The network can be seen by my windows laptop, my housemate's macbook, my other housemate's windows laptop, and any guests who want to connect using their smartphones.
Fixed channel - Check.  I used inssider to establish which channel was the best to use to avoid neighbourhood traffic.  It turned out to be 13.
pure WPA2-AES - Check.
MAC-address filter=off - Check.


After all that, I still have the same problem.

Here's some stuff:

```
~$ iwconfig
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
```

~$ lsmod
Module                  Size  Used by
ndiswrapper           196758  0 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
joydev                 17393  0 
snd_intel8x0           33455  2 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39826  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                96718  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i915                  423416  2 
serio_raw              13027  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
shpchp                 32325  0 
irda                  185517  0 
crc_ccitt              12627  1 irda
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  1 
drm_kms_helper         45466  1 i915
ppdev                  12849  0 
bluetooth             158479  10 rfcomm,bnep
drm                   197641  3 i915,drm_kms_helper
binfmt_misc            17292  1 
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40180  0 
firewire_core          56940  1 firewire_ohci
b44                    31412  0 
ssb                    50691  1 b44
crc_itu_t              12627  1 firewire_core
usb_storage            39646  1 
wbsd                   18452  0 
```

I can't tell if my network is showing up with iwlist, because the list is too massive.
```

~$ iwlist chan
lo        no frequency information.


wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.462 GHz (Channel 11)


eth0      no frequency information.

```
So, there we go.  No joy so far...

---

### Post by praseodym on 2013-03-15
Did you install ndiswrapper from the regular sources? It is buggy...Please show:
```

lsusb
modinfo ndiswrapper
dmesg | grep ndis
```

>  Bit Rate:300 Mb/s Tx-Power:[COLOR="#FF0000"]32[/COLOR] dBm 
WOW! Please try:
```

sudo iwconfig wlan0 txpower 18
```
Where did you get the windows driver from?

---

### Post by russco on 2013-03-15
Nothing showed up when I issued that command.  

I can't remember where I got the driver from, sorry.  It's called bcmwlhigh5 though, if that helps.

I loaded it using the Windows Network Drivers software from the store.

---

### Post by russco on 2013-03-15
...and now it can't see any wireless networks at all.

---

### Post by praseodym on 2013-03-15
```
sudo iwconfig wlan0 txpower 32
```
The problem is the ndiswrapper version from the store. Uninstall it via:
```

sudo apt-get remove --purge ndiswrapper* ndisgtk
```
and download these packages:

[http://forum.ubuntuusers.de/topic/fritz-wlan-stick-probleme-mit-der-installation/#post-5254662](http://forum.ubuntuusers.de/topic/fritz-wlan-stick-probleme-mit-der-installation/#post-5254662)

Check the last one for 32 or 64 bit. Save them in "Downloads" and install via:
```

sudo dpkg -i ~/Downloads/*.deb
```
Do not install the GUI (package "ndisgtk") because it reinstalls the wrong ndiswrapper version due to dependencies. You may want to compile the gui on your own:```

sudo apt-get install python python-glade2 python-gtk2 intltool
wget launchpad.net/ndisgtk/0.8/0.8.5/+download/ndisgtk-0.8.5.tar.gz
tar xvf ndisgtk-0.8.5.tar.gz
cd ndisgtk-0.8.5
make
sudo make install
sudo cp *.png /usr/share/icons
sudo cp *.xpm /usr/share/icons 
```
Reinstall the windows driver with the new gui.

---

### Post by russco on 2013-03-15
Thanks for your time here.

I uninstalled ndiswrapper, and downloaded those 3 files to the Downloads folder, and then the 32-bit file to the same folder.  Here's what happened:

```
~$ sudo dpkg -i ~/Downloads/*.deb
Selecting previously unselected package ndiswrapper-common.
(Reading database ... 182346 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.58~rc1-0ubuntu1_all.deb) ...
Selecting previously unselected package ndiswrapper-dkms.
Unpacking ndiswrapper-dkms (from .../ndiswrapper-dkms_1.58~rc1-0ubuntu1_all.deb) ...
Selecting previously unselected package ndiswrapper-source.
Unpacking ndiswrapper-source (from .../ndiswrapper-source_1.58~rc1-0ubuntu1_all.deb) ...
Preparing to replace ndiswrapper-utils-1.9 1.58~rc1-0ubuntu1 (using .../ndiswrapper-utils-1.9_1.58~rc1-0ubuntu1_i386.deb) ...
Unpacking replacement ndiswrapper-utils-1.9 ...
Setting up ndiswrapper-common (1.58~rc1-0ubuntu1) ...
dpkg: dependency problems prevent configuration of ndiswrapper-dkms:
 ndiswrapper-dkms depends on dkms (>= 2.1.0.0); however:
  Package dkms is not installed.
dpkg: error processing ndiswrapper-dkms (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ndiswrapper-source:
 ndiswrapper-source depends on module-assistant; however:
  Package module-assistant is not installed.
dpkg: error processing ndiswrapper-source (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Setting up ndiswrapper-utils-1.9 (1.58~rc1-0ubuntu1) ...
Errors were encountered while processing:
 ndiswrapper-dkms
 ndiswrapper-source
```

---

### Post by russco on 2013-03-15
Actually it's okay, solved that one.  Now I'm compiling the GUI...

---

### Post by varunendra on 2013-03-15
> **russco said:**
> Actually it's okay, solved that one.
Then please mark the thread as such. (follow the 'see how' link in my signature to see how).

Thanks!

---

### Post by russco on 2013-03-15
Nah, I solved that one smaller problem.  The overall problem is still happening.

---

### Post by russco on 2013-03-15
I did everything that was listed, but I'm still in the same position.  In the meantime I opened the network (no security at all), and still had the same problem.

---

### Post by praseodym on 2013-03-15
Did you install the compiling tools?
```

sudo apt-get install linux-headers-$(uname -r) build-essential dkms
```

---

### Post by russco on 2013-03-15
I did everything you said to, and when I reloaded the windows driver, it was in a screen that looked no different to the first time I did it.  You might need to treat me like an absolute tard, I'm afraid.

When I ran the command to install the compiling tools, everything was already at the latest version.

---

### Post by praseodym on 2013-03-15
Try to install the Windows driver via terminal:
```

sudo modprobe -rfv ndiswrapper
sudo ndiswrapper -i /path/to/driver.INF
```
Check:```

ndiswrapper -l
cat /etc/modprobe.d/ndiswrapper.conf
```
Load the driver:
```

sudo modprobe -v ndiswrapper
```
Replug the stick and check:
```
iwconfig
sudo iwlist scan
rfkill list
dmesg | grep ndis
```

---

### Post by russco on 2013-03-15
Ok, the check:

```
ndiswrapper -l
bcmwlhigh5 : driver installed

~/Documents/WNA3100$ cat /etc/modprobe.d/ndiswrapper.conf
alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper
```

```
$ sudo modprobe -v ndiswrapper
insmod /lib/modules/3.2.0-38-generic/updates/dkms/ndiswrapper.ko
```

```
/$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.
```

```
/$ sudo iwlist scan
lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.
```

```
/$ rfkill -list
Usage:	rfkill [options] command
Options:
	--version	show version (0.4-1ubuntu2 (Ubuntu))
Commands:
	help
	event
	list [IDENTIFIER]
	block IDENTIFIER
	unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
	<idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
```

```
/$ dmesg | grep ndis
[   25.831084] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
[   27.379997] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[   27.394563] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c7e000, 16000, 4
[   27.394574] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c81e80, 16000, 5
[   27.394581] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c85d00, 16000, 5
[   27.394586] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c89b80, 16000, 5
[   27.394593] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c8da00, 16000, 5
[   27.394599] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c91880, 16000, 5
[   27.394604] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c95700, 16000, 5
[   27.394610] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c99580, 16000, 5
[   27.394616] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c9d400, 16000, 5
[   27.394622] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ca1280, 16000, 5
[   27.394628] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ca5100, 16000, 4
[   27.394633] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ca8f80, 16000, 5
[   27.394639] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cace00, 16000, 5
[   27.394645] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cb0c80, 16000, 5
[   27.394651] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cb4b00, 16000, 5
[   27.394656] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cb8980, 16000, 5
[   27.394662] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cbc800, 16000, 5
[   27.394668] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cc0680, 16000, 5
[   27.394674] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cc4500, 16000, 5
[   27.394679] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cc8380, 16000, 5
[   27.394685] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ccc200, 16000, 5
[   27.394691] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cd0080, 16000, 4
[   27.394697] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cd3f00, 16000, 5
[   27.394702] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cd7d80, 16000, 5
[   27.394708] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cdbc00, 16000, 5
[   27.394714] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cdfa80, 16000, 5
[   27.394719] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ce3900, 16000, 5
[   27.394725] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ce7780, 16000, 5
[   27.394731] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ceb600, 16000, 5
[   27.394737] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cef480, 16000, 5
[   27.394743] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cf3300, 16000, 5
[   27.394748] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cf7180, 16000, 4
[   27.394754] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cfb000, 16000, 4
[   27.394760] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cfee80, 16000, 5
[   27.394766] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d02d00, 16000, 5
[   27.394772] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d06b80, 16000, 5
[   27.394784] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d0aa00, 16000, 5
[   27.394790] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d0e880, 16000, 5
[   27.394796] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d12700, 16000, 5
[   27.394802] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d16580, 16000, 5
[   27.394807] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d1a400, 16000, 5
[   27.394813] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d1e280, 16000, 5
[   27.394819] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d22100, 16000, 4
[   27.394825] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d25f80, 16000, 5
[   27.394830] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d29e00, 16000, 5
[   27.394836] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d2dc80, 16000, 5
[   27.394842] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d31b00, 16000, 5
[   27.394847] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d35980, 16000, 5
[   27.394853] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d39800, 16000, 5
[   27.394859] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d3d680, 16000, 5
[   31.400407] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[   31.400419] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   31.400435] ndiswrapper (mp_halt:254): device f369d480 is not initialized - not halting
[   31.400441] ndiswrapper: device eth%d removed
[   31.400585] ndiswrapper: probe of 1-2:1.0 failed with error -22
[   31.400654] usbcore: registered new interface driver ndiswrapper
[  115.264393] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[  115.666890] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8b90000, 16000, 4
[  115.666904] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8b93e80, 16000, 5
[  115.666911] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8b97d00, 16000, 5
[  115.666917] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8b9bb80, 16000, 5
[  115.666924] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8b9fa00, 16000, 5
[  115.666930] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ba3880, 16000, 5
[  115.666937] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ba7700, 16000, 5
[  115.666944] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bab580, 16000, 5
[  115.666950] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8baf400, 16000, 5
[  115.666956] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bb3280, 16000, 5
[  115.666962] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bb7100, 16000, 4
[  115.666968] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bbaf80, 16000, 5
[  115.666974] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bbee00, 16000, 5
[  115.666981] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bc2c80, 16000, 5
[  115.666987] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bc6b00, 16000, 5
[  115.666993] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bca980, 16000, 5
[  115.666999] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bce800, 16000, 5
[  115.667006] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bd2680, 16000, 5
[  115.667012] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bd6500, 16000, 5
[  115.667018] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bda380, 16000, 5
[  115.667025] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bde200, 16000, 5
[  115.667031] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8be2080, 16000, 4
[  115.667037] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8be5f00, 16000, 5
[  115.667044] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8be9d80, 16000, 5
[  115.667050] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bedc00, 16000, 5
[  115.667056] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bf1a80, 16000, 5
[  115.667062] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bf5900, 16000, 5
[  115.667068] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bf9780, 16000, 5
[  115.667074] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bfd600, 16000, 5
[  115.667080] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c01480, 16000, 5
[  115.667086] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c05300, 16000, 5
[  115.667092] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c09180, 16000, 4
[  115.667098] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c0d000, 16000, 4
[  115.667104] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c10e80, 16000, 5
[  115.667111] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c14d00, 16000, 5
[  115.667117] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c18b80, 16000, 5
[  115.667123] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c1ca00, 16000, 5
[  115.667129] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c20880, 16000, 5
[  115.667136] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c24700, 16000, 5
[  115.667142] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c28580, 16000, 5
[  115.667147] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c2c400, 16000, 5
[  115.667154] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c30280, 16000, 5
[  115.667160] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c34100, 16000, 4
[  115.667166] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c37f80, 16000, 5
[  115.667172] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c3be00, 16000, 5
[  115.667178] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c3fc80, 16000, 5
[  115.667187] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c43b00, 16000, 5
[  115.667193] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c47980, 16000, 5
[  115.667199] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c4b800, 16000, 5
[  115.667205] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c4f680, 16000, 5
[  115.686624] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[  742.084160] ndiswrapper (iw_get_scan:1276): getting BSSID list failed (C001000C)
[  785.176540] ndiswrapper: device wlan0 removed
[ 2824.039852] usbcore: deregistering interface driver ndiswrapper
[ 3060.064836] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
[ 3060.110585] usbcore: registered new interface driver ndiswrapper
```

Doesn't look too promising.

---

### Post by varunendra on 2013-03-15
> **russco said:**
> ```

wlan0     **[COLOR="#B22222"]IEEE 802.11g[/COLOR]**  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          **Bit Rate:[COLOR="#FF0000"]300 Mb/s[/COLOR]**   Tx-Power:32 dBm   
```

Can a ndiswrapper driver even operate at such a high speed?

I think it is supposed to use XP driver at most which don't support n channel. And g channel can support 54 Mb/s max.

May be try a different XP driver, or disable n-channel in router for a test?



**PS:**
@ russco,
Please use 'Code' tags while posting terminal outputs. It preserves formatting and makes the post neat, compact and more readable.
Follow the 'Code Tags example' link in my signature (again.. ;)) to see how to do it.

---

### Post by russco on 2013-03-15
Okay, let me try that again.  I kind of forgot to plug the usb back in...

```
/$ iwconfiglo        no wireless extensions.


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


```
sudo iwlist scan
``` produced too many results to see what's going on.  But I couldn't see my network in the list.```
[COLOR=#222222][FONT=Verdana]/$ dmesg | grep ndis[/FONT][/COLOR][   25.831084] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
[   27.379997] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[   27.394563] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c7e000, 16000, 4
[   27.394574] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c81e80, 16000, 5
[   27.394581] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c85d00, 16000, 5
[   27.394586] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c89b80, 16000, 5
[   27.394593] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c8da00, 16000, 5
[   27.394599] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c91880, 16000, 5
[   27.394604] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c95700, 16000, 5
[   27.394610] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c99580, 16000, 5
[   27.394616] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c9d400, 16000, 5
[   27.394622] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ca1280, 16000, 5
[   27.394628] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ca5100, 16000, 4
[   27.394633] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ca8f80, 16000, 5
[   27.394639] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cace00, 16000, 5
[   27.394645] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cb0c80, 16000, 5
[   27.394651] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cb4b00, 16000, 5
[   27.394656] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cb8980, 16000, 5
[   27.394662] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cbc800, 16000, 5
[   27.394668] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cc0680, 16000, 5
[   27.394674] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cc4500, 16000, 5
[   27.394679] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cc8380, 16000, 5
[   27.394685] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ccc200, 16000, 5
[   27.394691] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cd0080, 16000, 4
[   27.394697] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cd3f00, 16000, 5
[   27.394702] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cd7d80, 16000, 5
[   27.394708] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cdbc00, 16000, 5
[   27.394714] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cdfa80, 16000, 5
[   27.394719] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ce3900, 16000, 5
[   27.394725] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ce7780, 16000, 5
[   27.394731] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ceb600, 16000, 5
[   27.394737] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cef480, 16000, 5
[   27.394743] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cf3300, 16000, 5
[   27.394748] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cf7180, 16000, 4
[   27.394754] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cfb000, 16000, 4
[   27.394760] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8cfee80, 16000, 5
[   27.394766] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d02d00, 16000, 5
[   27.394772] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d06b80, 16000, 5
[   27.394784] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d0aa00, 16000, 5
[   27.394790] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d0e880, 16000, 5
[   27.394796] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d12700, 16000, 5
[   27.394802] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d16580, 16000, 5
[   27.394807] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d1a400, 16000, 5
[   27.394813] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d1e280, 16000, 5
[   27.394819] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d22100, 16000, 4
[   27.394825] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d25f80, 16000, 5
[   27.394830] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d29e00, 16000, 5
[   27.394836] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d2dc80, 16000, 5
[   27.394842] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d31b00, 16000, 5
[   27.394847] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d35980, 16000, 5
[   27.394853] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d39800, 16000, 5
[   27.394859] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d3d680, 16000, 5
[   31.400407] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[   31.400419] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   31.400435] ndiswrapper (mp_halt:254): device f369d480 is not initialized - not halting
[   31.400441] ndiswrapper: device eth%d removed
[   31.400585] ndiswrapper: probe of 1-2:1.0 failed with error -22
[   31.400654] usbcore: registered new interface driver ndiswrapper
[  115.264393] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[  115.666890] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8b90000, 16000, 4
[  115.666904] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8b93e80, 16000, 5
[  115.666911] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8b97d00, 16000, 5
[  115.666917] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8b9bb80, 16000, 5
[  115.666924] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8b9fa00, 16000, 5
[  115.666930] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ba3880, 16000, 5
[  115.666937] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ba7700, 16000, 5
[  115.666944] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bab580, 16000, 5
[  115.666950] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8baf400, 16000, 5
[  115.666956] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bb3280, 16000, 5
[  115.666962] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bb7100, 16000, 4
[  115.666968] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bbaf80, 16000, 5
[  115.666974] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bbee00, 16000, 5
[  115.666981] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bc2c80, 16000, 5
[  115.666987] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bc6b00, 16000, 5
[  115.666993] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bca980, 16000, 5
[  115.666999] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bce800, 16000, 5
[  115.667006] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bd2680, 16000, 5
[  115.667012] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bd6500, 16000, 5
[  115.667018] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bda380, 16000, 5
[  115.667025] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bde200, 16000, 5
[  115.667031] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8be2080, 16000, 4
[  115.667037] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8be5f00, 16000, 5
[  115.667044] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8be9d80, 16000, 5
[  115.667050] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bedc00, 16000, 5
[  115.667056] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bf1a80, 16000, 5
[  115.667062] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bf5900, 16000, 5
[  115.667068] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bf9780, 16000, 5
[  115.667074] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bfd600, 16000, 5
[  115.667080] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c01480, 16000, 5
[  115.667086] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c05300, 16000, 5
[  115.667092] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c09180, 16000, 4
[  115.667098] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c0d000, 16000, 4
[  115.667104] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c10e80, 16000, 5
[  115.667111] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c14d00, 16000, 5
[  115.667117] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c18b80, 16000, 5
[  115.667123] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c1ca00, 16000, 5
[  115.667129] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c20880, 16000, 5
[  115.667136] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c24700, 16000, 5
[  115.667142] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c28580, 16000, 5
[  115.667147] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c2c400, 16000, 5
[  115.667154] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c30280, 16000, 5
[  115.667160] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c34100, 16000, 4
[  115.667166] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c37f80, 16000, 5
[  115.667172] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c3be00, 16000, 5
[  115.667178] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c3fc80, 16000, 5
[  115.667187] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c43b00, 16000, 5
[  115.667193] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c47980, 16000, 5
[  115.667199] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c4b800, 16000, 5
[  115.667205] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c4f680, 16000, 5
[  115.686624] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[  742.084160] ndiswrapper (iw_get_scan:1276): getting BSSID list failed (C001000C)
[  785.176540] ndiswrapper: device wlan0 removed
[ 2824.039852] usbcore: deregistering interface driver ndiswrapper
[ 3060.064836] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
[ 3060.110585] usbcore: registered new interface driver ndiswrapper
[ 3933.148241] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[ 3933.552355] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8b90000, 16000, 4
[ 3933.552370] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8b93e80, 16000, 5
[ 3933.552376] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8b97d00, 16000, 5
[ 3933.552383] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8b9bb80, 16000, 5
[ 3933.552390] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8b9fa00, 16000, 5
[ 3933.552397] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ba3880, 16000, 5
[ 3933.552403] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8ba7700, 16000, 5
[ 3933.552410] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bab580, 16000, 5
[ 3933.552416] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8baf400, 16000, 5
[ 3933.552422] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bb3280, 16000, 5
[ 3933.552428] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bb7100, 16000, 4
[ 3933.552435] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bbaf80, 16000, 5
[ 3933.552441] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bbee00, 16000, 5
[ 3933.552447] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bc2c80, 16000, 5
[ 3933.552454] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bc6b00, 16000, 5
[ 3933.552461] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bca980, 16000, 5
[ 3933.552468] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bce800, 16000, 5
[ 3933.552474] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bd2680, 16000, 5
[ 3933.552481] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bd6500, 16000, 5
[ 3933.552487] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bda380, 16000, 5
[ 3933.552581] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bde200, 16000, 5
[ 3933.552588] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8be2080, 16000, 4
[ 3933.552594] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8be5f00, 16000, 5
[ 3933.552600] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8be9d80, 16000, 5
[ 3933.552606] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bedc00, 16000, 5
[ 3933.552613] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bf1a80, 16000, 5
[ 3933.552620] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bf5900, 16000, 5
[ 3933.552627] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bf9780, 16000, 5
[ 3933.552633] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8bfd600, 16000, 5
[ 3933.552639] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c01480, 16000, 5
[ 3933.552648] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c05300, 16000, 5
[ 3933.552654] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c09180, 16000, 4
[ 3933.552661] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c0d000, 16000, 4
[ 3933.552667] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c10e80, 16000, 5
[ 3933.552673] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c14d00, 16000, 5
[ 3933.552680] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c18b80, 16000, 5
[ 3933.552686] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c1ca00, 16000, 5
[ 3933.552692] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c20880, 16000, 5
[ 3933.552698] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c24700, 16000, 5
[ 3933.552705] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c28580, 16000, 5
[ 3933.552712] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c2c400, 16000, 5
[ 3933.552718] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c30280, 16000, 5
[ 3933.552724] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c34100, 16000, 4
[ 3933.552730] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c37f80, 16000, 5
[ 3933.552736] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c3be00, 16000, 5
[ 3933.552743] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c3fc80, 16000, 5
[ 3933.552749] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c43b00, 16000, 5
[ 3933.552757] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c47980, 16000, 5
[ 3933.552763] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c4b800, 16000, 5
[ 3933.552769] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8c4f680, 16000, 5
[ 3933.575680] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[ 4079.077172] ndiswrapper (iw_get_scan:1276): getting BSSID list failed (C001000C)
[ 4081.584636] ndiswrapper: device wlan0 removed
[ 4082.230760] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[ 4082.635501] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f933d000, 16000, 4
[ 4082.635515] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9340e80, 16000, 5
[ 4082.635523] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9344d00, 16000, 5
[ 4082.635529] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9348b80, 16000, 5
[ 4082.635535] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f934ca00, 16000, 5
[ 4082.635541] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9350880, 16000, 5
[ 4082.635547] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9354700, 16000, 5
[ 4082.635553] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9358580, 16000, 5
[ 4082.635560] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f935c400, 16000, 5
[ 4082.635566] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9360280, 16000, 5
[ 4082.635572] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9364100, 16000, 4
[ 4082.635579] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9367f80, 16000, 5
[ 4082.635585] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f936be00, 16000, 5
[ 4082.635591] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f936fc80, 16000, 5
[ 4082.635598] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9373b00, 16000, 5
[ 4082.635604] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9377980, 16000, 5
[ 4082.635610] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f937b800, 16000, 5
[ 4082.635617] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f937f680, 16000, 5
[ 4082.635624] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9383500, 16000, 5
[ 4082.635630] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9387380, 16000, 5
[ 4082.635636] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f938b200, 16000, 5
[ 4082.635642] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f938f080, 16000, 4
[ 4082.635648] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9392f00, 16000, 5
[ 4082.635655] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9396d80, 16000, 5
[ 4082.635661] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f939ac00, 16000, 5
[ 4082.635666] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f939ea80, 16000, 5
[ 4082.635672] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93a2900, 16000, 5
[ 4082.635678] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93a6780, 16000, 5
[ 4082.635684] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93aa600, 16000, 5
[ 4082.635690] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93ae480, 16000, 5
[ 4082.635697] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93b2300, 16000, 5
[ 4082.635703] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93b6180, 16000, 4
[ 4082.635709] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93ba000, 16000, 4
[ 4082.635716] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93bde80, 16000, 5
[ 4082.635722] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93c1d00, 16000, 5
[ 4082.635728] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93c5b80, 16000, 5
[ 4082.635734] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93c9a00, 16000, 5
[ 4082.635742] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93cd880, 16000, 5
[ 4082.635748] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93d1700, 16000, 5
[ 4082.635755] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93d5580, 16000, 5
[ 4082.635761] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93d9400, 16000, 5
[ 4082.635768] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93dd280, 16000, 5
[ 4082.635774] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93e1100, 16000, 4
[ 4082.635780] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93e4f80, 16000, 5
[ 4082.635787] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93e8e00, 16000, 5
[ 4082.635793] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93ecc80, 16000, 5
[ 4082.635799] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93f0b00, 16000, 5
[ 4082.635805] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93f4980, 16000, 5
[ 4082.635811] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93f8800, 16000, 5
[ 4082.635817] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f93fc680, 16000, 5
[ 4082.655709] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[ 4221.462522] ndiswrapper: device wlan0 removed
[ 4222.111041] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[ 4222.117627] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9b8c000, 16000, 4
[ 4222.117642] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9b8fe80, 16000, 5
[ 4222.117649] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9b93d00, 16000, 5
[ 4222.117655] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9b97b80, 16000, 5
[ 4222.117661] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9b9ba00, 16000, 5
[ 4222.117667] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9b9f880, 16000, 5
[ 4222.117675] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9ba3700, 16000, 5
[ 4222.117682] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9ba7580, 16000, 5
[ 4222.117688] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9bab400, 16000, 5
[ 4222.117695] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9baf280, 16000, 5
[ 4222.117702] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9bb3100, 16000, 4
[ 4222.117708] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9bb6f80, 16000, 5
[ 4222.117714] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9bbae00, 16000, 5
[ 4222.117720] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9bbec80, 16000, 5
[ 4222.117726] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9bc2b00, 16000, 5
[ 4222.117734] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9bc6980, 16000, 5
[ 4222.117740] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9bca800, 16000, 5
[ 4222.117747] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9bce680, 16000, 5
[ 4222.117753] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9bd2500, 16000, 5
[ 4222.117760] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9bd6380, 16000, 5
[ 4222.117766] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9bda200, 16000, 5
[ 4222.117772] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9bde080, 16000, 4
[ 4222.117779] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9be1f00, 16000, 5
[ 4222.117785] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9be5d80, 16000, 5
[ 4222.117791] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9be9c00, 16000, 5
[ 4222.117798] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9beda80, 16000, 5
[ 4222.117804] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9bf1900, 16000, 5
[ 4222.117810] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9bf5780, 16000, 5
[ 4222.117816] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9bf9600, 16000, 5
[ 4222.117823] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9bfd480, 16000, 5
[ 4222.117830] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c01300, 16000, 5
[ 4222.117837] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c05180, 16000, 4
[ 4222.117843] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c09000, 16000, 4
[ 4222.117849] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c0ce80, 16000, 5
[ 4222.117856] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c10d00, 16000, 5
[ 4222.117862] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c14b80, 16000, 5
[ 4222.117869] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c18a00, 16000, 5
[ 4222.117875] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c1c880, 16000, 5
[ 4222.117881] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c20700, 16000, 5
[ 4222.117887] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c24580, 16000, 5
[ 4222.117893] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c28400, 16000, 5
[ 4222.117899] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c2c280, 16000, 5
[ 4222.117905] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c30100, 16000, 4
[ 4222.117913] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c33f80, 16000, 5
[ 4222.117919] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c37e00, 16000, 5
[ 4222.117925] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c3bc80, 16000, 5
[ 4222.117931] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c3fb00, 16000, 5
[ 4222.117937] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c43980, 16000, 5
[ 4222.117944] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c47800, 16000, 5
[ 4222.117949] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f9c4b680, 16000, 5
[ 4222.135392] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[ 4230.180657] ndiswrapper: device wlan0 removed
[ 4230.816323] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[ 4230.824915] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa3db000, 16000, 4
[ 4230.824931] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa3dee80, 16000, 5
[ 4230.824937] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa3e2d00, 16000, 5
[ 4230.824943] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa3e6b80, 16000, 5
[ 4230.824950] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa3eaa00, 16000, 5
[ 4230.824956] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa3ee880, 16000, 5
[ 4230.824963] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa3f2700, 16000, 5
[ 4230.824969] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa3f6580, 16000, 5
[ 4230.824975] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa3fa400, 16000, 5
[ 4230.824981] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa3fe280, 16000, 5
[ 4230.824987] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa402100, 16000, 4
[ 4230.824993] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa405f80, 16000, 5
[ 4230.825000] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa409e00, 16000, 5
[ 4230.825006] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa40dc80, 16000, 5
[ 4230.825013] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa411b00, 16000, 5
[ 4230.825019] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa415980, 16000, 5
[ 4230.825025] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa419800, 16000, 5
[ 4230.825031] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa41d680, 16000, 5
[ 4230.825037] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa421500, 16000, 5
[ 4230.825043] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa425380, 16000, 5
[ 4230.825049] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa429200, 16000, 5
[ 4230.825056] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa42d080, 16000, 4
[ 4230.825062] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa430f00, 16000, 5
[ 4230.825068] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa434d80, 16000, 5
[ 4230.825074] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa438c00, 16000, 5
[ 4230.825080] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa43ca80, 16000, 5
[ 4230.825087] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa440900, 16000, 5
[ 4230.825122] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa444780, 16000, 5
[ 4230.825129] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa448600, 16000, 5
[ 4230.825136] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa44c480, 16000, 5
[ 4230.825142] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa450300, 16000, 5
[ 4230.825148] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa454180, 16000, 4
[ 4230.825154] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa458000, 16000, 4
[ 4230.825161] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa45be80, 16000, 5
[ 4230.825167] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa45fd00, 16000, 5
[ 4230.825173] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa463b80, 16000, 5
[ 4230.825179] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa467a00, 16000, 5
[ 4230.825186] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa46b880, 16000, 5
[ 4230.825192] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa46f700, 16000, 5
[ 4230.825199] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa473580, 16000, 5
[ 4230.825205] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa477400, 16000, 5
[ 4230.825212] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa47b280, 16000, 5
[ 4230.825221] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa47f100, 16000, 4
[ 4230.825227] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa482f80, 16000, 5
[ 4230.825233] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa486e00, 16000, 5
[ 4230.825239] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa48ac80, 16000, 5
[ 4230.825246] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa48eb00, 16000, 5
[ 4230.825252] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa492980, 16000, 5
[ 4230.825259] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa496800, 16000, 5
[ 4230.825265] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fa49a680, 16000, 5
[ 4230.844189] ndiswrapper (ndis_encode_setting:383): unknown type: 3
```

Sorry. :)

---

### Post by praseodym on 2013-03-15
> ```
[   31.400585] ndiswrapper: probe of 1-2:1.0 failed with error -22
```

Try the driver attached. IMHO error -22 comes from the network-manager. Remove your current profile and create a new one.

---

