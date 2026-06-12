---
title: "USB drivers?"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by Muskiet on 2010-06-14
I just bought a Ralink Technology USB wireless adapter.
When Googling I find all sorts of information on how to use the Windows drivers through  Ndiswrapper.
Now I'm pretty new to Ubuntu and I have no clue what  Ndiswrapper is really, but I did find that the driver CD actually comes with Linux software.

Among the files there is a readme which is very long, but some of the stuff says:

  	 	 	 	 	> [COLOR=#000000][FONT=Geneva][SIZE=3]ModelName:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]===========[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]RT2870 Wireless Lan Linux Driver[/SIZE][/FONT][/COLOR]
 

 

 [COLOR=#000000][FONT=Geneva][SIZE=3]=======================================================================[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]Driver lName:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]===========[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]rt2870.o/rt2870.ko[/SIZE][/FONT][/COLOR]
 

 

 [COLOR=#000000][FONT=Geneva][SIZE=3]=======================================================================[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]Supporting Kernel:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]===================[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]linux kernel 2.4 and 2.6 series. [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Geneva][SIZE=3]Tested in Redhat 7.3 or later.[/SIZE][/FONT][/COLOR]
 

 

 [COLOR=#000000][FONT=Geneva][SIZE=3]=======================================================================[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]Ralink Hardware:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]===================[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]Ralink 802.11n Wireless LAN Card.[/SIZE][/FONT][/COLOR]
 

 

 [COLOR=#000000][FONT=Geneva][SIZE=3]=======================================================================[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]Description:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]=============[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]This is a linux device driver for Ralink RT2870 USB ABGN WLAN Card.[/SIZE][/FONT][/COLOR]
 

 

 [COLOR=#000000][FONT=Geneva][SIZE=3]=======================================================================[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]Contents:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]=============[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]Makefile	        : Makefile[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]*.c					: c files[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]*.h					: header files[/SIZE][/FONT][/COLOR]
 

 

 [COLOR=#000000][FONT=Geneva][SIZE=3]=======================================================================[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]Features:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]==========[/SIZE][/FONT][/COLOR]
 [COLOR=#000000]  [FONT=Geneva][SIZE=3]This driver implements basic IEEE802.11. Infrastructure and adhoc mode with [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000]  [FONT=Geneva][SIZE=3]open or shared or WPA-PSK or WPA2-PSK authentication method. [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000]  [FONT=Geneva][SIZE=3]NONE, WEP, TKIP and AES encryption. [/SIZE][/FONT][/COLOR] 
 

 

 [COLOR=#000000][FONT=Geneva][SIZE=3]=======================================================================[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]Build Instructions:  [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Geneva][SIZE=3]====================[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Geneva][SIZE=3]1> $tar -xvzf DPB_RT2870_Linux_STA_x.x.x.x.tgz[/SIZE][/FONT][/COLOR]
 [COLOR=#000000]   [FONT=Geneva][SIZE=3]go to "./DPB_RT2870_Linux_STA_x.x.x.x" directory.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000]   [/COLOR] 
 [COLOR=#000000][FONT=Geneva][SIZE=3]2> In Makefile[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]	 define the linux kernel source include file path LINUX_SRC[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]	 modify to meet your need.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Geneva][SIZE=3]3> In os/linux/config.mk [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Geneva][SIZE=3]	define the GCC and LD of the target machine[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]	define the compiler flags CFLAGS[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]	modify to meet your need.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]	** Build for being controlled by NetworkManager or wpa_supplicant wext functions[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]	   => #>cd wpa_supplicant-x.x[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]	   => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]	** Build for being controlled by WpaSupplicant with Ralink Driver[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]	   => #>cd wpa_supplicant-0.5.7[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Geneva][SIZE=3]4> $make[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]	# compile driver source code[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]	# To fix "error: too few arguments to function iwe_stream_add_event"[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]	  => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Geneva][SIZE=3]5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat[/SIZE][/FONT][/COLOR]
 [COLOR=#000000]   [/COLOR] 
 [COLOR=#000000][FONT=Geneva][SIZE=3]6> load driver, go to "os/linux/" directory.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000]   [FONT=Geneva][SIZE=3]#[kernel 2.4][/SIZE][/FONT][/COLOR]
 [COLOR=#000000]   [FONT=Geneva][SIZE=3]#    $/sbin/insmod rt2870sta.o[/SIZE][/FONT][/COLOR]
 [COLOR=#000000]   [FONT=Geneva][SIZE=3]#    $/sbin/ifconfig ra0 inet YOUR_IP up[/SIZE][/FONT][/COLOR]
 [COLOR=#000000]       [/COLOR] 
 [COLOR=#000000]   [FONT=Geneva][SIZE=3]#[kernel 2.6][/SIZE][/FONT][/COLOR]
 [COLOR=#000000]   [FONT=Geneva][SIZE=3]#    $/sbin/insmod rt2870sta.ko[/SIZE][/FONT][/COLOR]
 [COLOR=#000000]   [FONT=Geneva][SIZE=3]#    $/sbin/ifconfig ra0 inet YOUR_IP up[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Geneva][SIZE=3]7> unload driver    [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000]   [FONT=Geneva][SIZE=3]$/sbin/ifconfig ra0 down[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]	$/sbin/rmmod rt2870sta[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Geneva][SIZE=3]	[/SIZE][/FONT][/COLOR]
 

Does anybody know what I do with these files to make my adapter work?

---

### Post by b k on 2010-06-15
> **Muskiet said:**
> I just bought a Ralink Technology USB wireless adapter.
When Googling I find all sorts of information on how to use the Windows drivers through  Ndiswrapper.
Now I'm pretty new to Ubuntu and I have no clue what  Ndiswrapper is really, but I did find that the driver CD actually comes with Linux software.

Among the files there is a readme which is very long, but some of the stuff says:

                          

Does anybody know what I do with these files to make my adapter work?

Hi there, you may not need to install anything if you are using Ubuntu 10.04 LTS.

Try this:

Go to : *Applications > Accessories > Terminal*

```
sudo gedit /etc/modprobe.d/blacklist.conf
```The text editor gedit will open the file blacklist.conf
Add the following line to the end ot the opened file.

```
blacklist rt2800usb
```Proofread carefully. [COLOR=Red]Save[/COLOR] and close gedit.

 Reboot.

If your wireless adapter does not work please post the output of the following commands:


```
lsusb
```and

```
lsmod
```Good luck and let us know if it works.

---

### Post by Muskiet on 2010-06-15
> **b k said:**
> Hi there, you may not need to install anything if you are using Ubuntu 10.04 LTS.

Try this:

Go to : *Applications > Accessories > Terminal*

```
sudo gedit /etc/modprobe.d/blacklist.conf
```The text editor gedit will open the file blacklist.conf
Add the following line to the end ot the opened file.

```
blacklist rt2800usb
```Proofread carefully. [COLOR=Red]Save[/COLOR] and close gedit.

 Reboot.



Thanx b k!
I am indeed using 10.04 and your solution worked like a charm!
Several hours of fiddeling and here's a ten second solution ](*,)

Thanx again!

---

### Post by ausgado on 2010-06-16
Hi- there can someone give an explanation of what blacklist does in simple terms

---

### Post by b k on 2010-06-16
> **ausgado said:**
> Hi- there can someone give an explanation of what blacklist does in simple terms
 
Hi there, some times upon boot up more than one driver (in this case for a wireless adapter) is loaded.
 
The adapter needs just one driver (the correct one for that specific device) and it becomes sort of confused and would probably not work if more than one driver is loaded.
 
When we blacklist a driver, we are deliberately stopping/preventing the incorrect driver/drivers from loading at boot up.
 
Hope this explanation helps.

---

### Post by Tumpelo666 on 2011-12-07
> **b k said:**
> Hi there, you may not need to install anything if you are using Ubuntu 10.04 LTS.

Try this:

Go to : *Applications > Accessories > Terminal*

```
sudo gedit /etc/modprobe.d/blacklist.conf
```The text editor gedit will open the file blacklist.conf
Add the following line to the end ot the opened file.

```
blacklist rt2800usb
```Proofread carefully. [COLOR=Red]Save[/COLOR] and close gedit.

 Reboot.

If your wireless adapter does not work please post the output of the following commands:


```
lsusb
```and

```
lsmod
```Good luck and let us know if it works.

Arrr. It almost works. Ubuntu finds adapter and trying to connect to Wlan, but... It just keep asking password. 

tumpelo@Raamattu:~$ lsusb
Bus 002 Device 003: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 002 Device 002: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 129b:1667 CyberTAN Technology 802.11bg
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




tumpelo@Raamattu:~$ lsmod
Module                  Size  Used by
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
arc4                    1153  2 
zd1211rw               42217  0 
mac80211              205434  1 zd1211rw
cfg80211              126080  2 zd1211rw,mac80211
binfmt_misc             6587  1 
fglrx                2625736  74 
agpgart                31724  1 fglrx
snd_hda_codec_atihdmi     2367  1 
snd_hda_codec_analog    58598  1 
snd_seq_dummy           1338  0 
snd_hda_intel          22069  2 
snd_seq_oss            26722  0 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
joydev                  8740  0 
snd                    54244  16 snd_hda_codec_analog,snd_hda_intel,snd_seq_oss,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
rt2870sta             461811  1 
parport_pc             25962  1 
asus_atk0110            9017  0 
k8temp                  3152  0 
serio_raw               3978  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
i2c_nforce2             5199  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ohci1394               26950  0 
floppy                 53016  0 
ieee1394               81181  1 ohci1394
sata_nv                19376  4 
forcedeth              49556  0 
pata_amd                8766  0 

Please help ASAP :)

---

