---
title: "New USB Wireless Adaptor, Setup or Throw Away?"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by n.hinton on 2010-07-09
Just bought a new GetNet GN-531U Wireless 150Mbps USB Adapter, cos 1/ it was cheap, 2/ thought it might be a good idea to have a backup for my (working perfectly) D-Link air plus.

When I first connected the D-Link, my network (and others) immediately showed up, gave network manager the wireless key, and job done all working.

Just plugged in the getnet dongle and nothing! Had a look at its accompanying CD and low and behold a directory called Linux drivers. I read the readme and perused the makefile and another file the readme mentioned, and realised I could not be more out of my depth if I was at the bottom of the 'Mariana Trench'.

I would like to try and get it working, providing nothing would adversely impact my perfectly functional wireless connection. Have attached the 'Linux drivers' If anyone would be kind enough to provide some guidance. The bit about plugging it into a USB socket I'm fine with, its the other stuff ;-)

---

### Post by Sonsum on 2010-07-09
Whew. Thats a brutal ReadMe. Haha. Okay, I'll try and take this step by step with you and maybe we can figure this out together.

For the first step you'll need to place that archive in the home folder. Then run ```
tar -xvzf 2009_0525_RT3070_Linux_STA_v2.1.1.0.tar.gz
```

that should extract it to your home directory.

(NOTE: Just for my own ease of use, I'm extracting the building instructions in the readme here)

> Build Instructions:  
====================

1> $tar -xvzf DPB_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	   => #>cd wpa_supplicant-x.x
	   => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
	** Build for being controlled by WpaSupplicant with Ralink Driver
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   => #>cd wpa_supplicant-0.5.7
	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make
	# compile driver source code
	# To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	  => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
	$/sbin/rmmod rt2870sta
	

---

### Post by n.hinton on 2010-07-09
Thanks Sonsum,

2009_0525_RT3070_Linux_STA_v2.1.1.0 is already in my home directory copied as is from CD (I tar.gz'ed it to upload to forum).

When I read the readme I thought they had forgotten to translate it from Taiwanese/Chinese or whatever!

---

### Post by Sonsum on 2010-07-09
> **n.hinton said:**
> Thanks Sonsum,

2009_0525_RT3070_Linux_STA_v2.1.1.0 is already in my home directory copied as is from CD (I tar.gz'ed it to upload to forum).

When I read the readme I thought they had forgotten to translate it from Taiwanese/Chinese or whatever!

Okay, the next step appears to be to run ```
cd  /2009_0525_RT3070_Linux_STA_v2.1.1.0
```
which should get the terminal into that folder.

---

### Post by n.hinton on 2010-07-09
yes thanks again Sonsum,

Now what is it I need to do with the ```
/home/kingfisher/2009_0525_RT3070_Linux_STA_v2.1.1.0/Makefile
``` and ```
/home/kingfisher/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/config.mk
```

---

### Post by n.hinton on 2010-07-09
Hi again Sonsum,

Have been reading through the makefile and can't for the life of me see anything that doesn't look preconfigured for Lucid, but then I don't really understand much of the contents. So haven't edited anything in it yet.

In config.mk I have edited from the instruction in part 3 (Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.)
so as that section now reads ```
#ifdef WPA_SUPPLICANT_SUPPORT
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y
#endif // WPA_SUPPLICANT_SUPPORT //

#ifdef NATIVE_WPA_SUPPLICANT_SUPPORT
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
#endif // NATIVE_WPA_SUPPLICANT_SUPPORT //
```

The next two lines appear to me to be pointing somewhere else in the file system, and as for 'GCC and LD' and CFLAGS, whatever they are, well (probably sea flags to point me at that 'Mariana Trench') best I stop messing with stuff and wait for your much appreciated help.

---

### Post by roosh on 2010-07-09
Just throwing this out there:
You might not need to compile the driver (I don't even think compiling will solve the problem). From what I've seen from your post, it looks like you're building the rt2780sta driver. Ubuntu already has this driver, but it conflicts with the rt2800usb driver.

Try running ```
sudo rmmod rt2800usb
``` 

That should fix the problem.

More information (including info on getting the wireless to work on boot) can be found here: [http://ubuntuforums.org/showthread.php?t=1453549](http://ubuntuforums.org/showthread.php?t=1453549)

---

### Post by Sonsum on 2010-07-10
> **roosh said:**
> Just throwing this out there:
You might not need to compile the driver (I don't even think compiling will solve the problem). From what I've seen from your post, it looks like you're building the rt2780sta driver. Ubuntu already has this driver, but it conflicts with the rt2800usb driver.

Try running ```
sudo rmmod rt2800usb
``` 

That should fix the problem.

More information (including info on getting the wireless to work on boot) can be found here: [http://ubuntuforums.org/showthread.php?t=1453549](http://ubuntuforums.org/showthread.php?t=1453549)

I sure hope this works. Sounds MUCH easier. :lolflag:

---

### Post by roosh on 2010-07-10
> **Sonsum said:**
> I sure hope this works. Sounds MUCH easier. :lolflag:

I agree. I was about to suggest using ndiswrapper one time before I realized that.

---

### Post by n.hinton on 2010-07-10
Thanks for that roosh,

Is there any way of testing this first before removing a module, because I want to keep using my D-link USB Wireless Adaptor (which works great out the box) and have the Getnet one as a working backup.

I'm just worried here about doing something here that affect the D-Link one.

Just don't understand too much about the workings of Linux yet.

---

### Post by n.hinton on 2010-07-10
Hi roosh Just tried the following from the link you posted > My Solution after installation:

1/ Open a terminal
Code:

Applications -> Accessories -> Terminal

    a window will open

2/ Type:
Code:

sudo gedit /etc/modprobe.d/blacklist.conf

    enter your root password.

    this will open a text editor focused on the blacklist.conf a file dedicated to removing modules that conflict others

3/ Scroll as far as you can to the bottom of the text and create a new line.

4/ Type:
Code:

blacklist rt2800usb

5/ Save the file.

6/ Restart the pc.

7/ After reboot you should be able to select wireless access points and connect But made no difference.

If I run ```
sudo rmmod rt2800usb
``` and it causes an issue how would I undo the change?

P.S. Looking at the build instructions from the readme it appears to me the instructions are for RT2870

---

### Post by roosh on 2010-07-10
The code I suggested, sudo rmmod rt2800usb, will tempoarily disable the conflicting driver. You can always load it again by rebooting or with the command, sudo modprobe rt2800usb. What you did (opening blacklist and adding blacklist rt2800usb) will not allow rt2800usb to load on boot. 

That doesn't work?
Could you run ```
lsmod
``` with the adapter that's giving you trouble plugged-in?

---

### Post by n.hinton on 2010-07-10
Hi roosh,
Thank you for your post, and the sudo rmmod info.

A little progress has been made. Have left 'blacklist rt2800usb' in 'blacklist.conf' for time being, and tried Netget in different USB, and it tries to connect (network is visible). I live in a remote part of the UK east coast, and have setup my hub as a wi-fi access point, to share some of my bandwidth with any passers by who may want a connection.

What shows up in available networks then are BTHomeHub2-xxxx (my network), BTFON and BTOpenzone, both of the latter are wi-fi access points and have no security. The Netget dongle will connect to either of these almost instantly, but not my network! (which uses WPA & WPA2 Personal).

I dont know if the following quotes from my terminal using lsmod you mentioned are of help.

The first is with my D-Link (doing what it should )connected to my network:

> kingfisher@kingfisher-desktop:~$ lsmod
Module                  Size  Used by
rt2870sta             461811  0 
binfmt_misc             6587  1 
xt_limit                1382  8 
xt_tcpudp               2011  7 
ipt_LOG                 4542  8 
ipt_MASQUERADE          1407  0 
xt_DSCP                 1677  0 
ipt_REJECT              1928  1 
nf_conntrack_irc        3332  0 
nf_conntrack_ftp        5381  0 
xt_state                1098  7 
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
snd_atiixp_modem        9103  0 
snd_via82xx_modem       8486  0 
snd_intel8x0m          10751  0 
iptable_nat             4414  0 
nf_nat                 15735  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      10672  10 iptable_nat,nf_nat
nf_conntrack           61583  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
iptable_mangle          2771  0 
iptable_filter          2271  1 
ip_tables               9991  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               14299  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
snd_ens1371            18814  2 
gameport                9089  1 snd_ens1371
snd_ac97_codec        100646  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ens1371
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  6 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
arc4                    1153  2 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_ens1371,snd_seq_midi
nls_utf8                1069  1 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nls_cp437               4919  1 
vfat                    8933  1 
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fat                    47767  1 vfat
rt73usb                22434  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
crc_itu_t               1371  1 rt73usb
snd_timer              19098  2 snd_pcm,snd_seq
font                    7557  1 fbcon
rt2x00usb               9703  1 rt73usb
bitblit                 4707  1 fbcon
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt2x00lib              27509  2 rt73usb,rt2x00usb
softcursor              1189  1 bitblit
led_class               2864  1 rt2x00lib
vga16fb                11385  1 
snd                    54148  18 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vgastate                8961  1 vga16fb
mac80211              205146  2 rt2x00usb,rt2x00lib
ppdev                   5259  0 
soundcore               6620  1 snd
amd_k7_agp              4892  1 
lp                      7028  0 
parport_pc             25962  1 
usblp                  10481  0 
cfg80211              126517  2 rt2x00lib,mac80211
snd_page_alloc          7076  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_pcm
i2c_amd756              4151  0 
shpchp                 28820  0 
agpgart                31724  1 amd_k7_agp
parport                32635  3 ppdev,lp,parport_pc
usbhid                 36110  0 
usb_storage            39425  0 
hid                    67032  1 usbhid
floppy                 53016  0 
pata_amd                8766  3 
This second one is with the Netget connected to BTFON


> kingfisher@kingfisher-desktop:~$ lsmod
Module                  Size  Used by
rt2870sta             461811  1 
binfmt_misc             6587  1 
xt_limit                1382  8 
xt_tcpudp               2011  10 
ipt_LOG                 4542  8 
ipt_MASQUERADE          1407  0 
xt_DSCP                 1677  0 
ipt_REJECT              1928  1 
nf_conntrack_irc        3332  0 
nf_conntrack_ftp        5381  0 
xt_state                1098  7 
aes_i586                7268  0 
aes_generic            26863  1 aes_i586
snd_atiixp_modem        9103  0 
snd_via82xx_modem       8486  0 
snd_intel8x0m          10751  0 
iptable_nat             4414  0 
nf_nat                 15735  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      10672  10 iptable_nat,nf_nat
nf_conntrack           61583  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
iptable_mangle          2771  0 
iptable_filter          2271  1 
ip_tables               9991  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               14299  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
snd_ens1371            18814  2 
gameport                9089  1 snd_ens1371
snd_ac97_codec        100646  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ens1371
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  6 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
arc4                    1153  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_ens1371,snd_seq_midi
nls_utf8                1069  1 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nls_cp437               4919  1 
vfat                    8933  1 
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fat                    47767  1 vfat
rt73usb                22434  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
crc_itu_t               1371  1 rt73usb
snd_timer              19098  2 snd_pcm,snd_seq
font                    7557  1 fbcon
rt2x00usb               9703  1 rt73usb
bitblit                 4707  1 fbcon
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt2x00lib              27509  2 rt73usb,rt2x00usb
softcursor              1189  1 bitblit
led_class               2864  1 rt2x00lib
vga16fb                11385  1 
snd                    54148  18 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vgastate                8961  1 vga16fb
mac80211              205146  2 rt2x00usb,rt2x00lib
ppdev                   5259  0 
soundcore               6620  1 snd
amd_k7_agp              4892  1 
lp                      7028  0 
parport_pc             25962  1 
usblp                  10481  0 
cfg80211              126517  2 rt2x00lib,mac80211
snd_page_alloc          7076  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_pcm
i2c_amd756              4151  0 
shpchp                 28820  0 
agpgart                31724  1 amd_k7_agp
parport                32635  3 ppdev,lp,parport_pc
usbhid                 36110  0 
usb_storage            39425  0 
hid                    67032  1 usbhid
floppy                 53016  0 
pata_amd                8766  3 

The cursor just sits flashing while Netget is trying and failing to connect to my network, and the remaining is with the Netget manually switched to disconected

> kingfisher@kingfisher-desktop:~$ lsmod
Module                  Size  Used by
rt2870sta             461811  1 
binfmt_misc             6587  1 
xt_limit                1382  0 
xt_tcpudp               2011  0 
ipt_LOG                 4542  0 
ipt_MASQUERADE          1407  0 
xt_DSCP                 1677  0 
ipt_REJECT              1928  0 
nf_conntrack_irc        3332  0 
nf_conntrack_ftp        5381  0 
xt_state                1098  0 
aes_i586                7268  0 
aes_generic            26863  1 aes_i586
snd_atiixp_modem        9103  0 
snd_via82xx_modem       8486  0 
snd_intel8x0m          10751  0 
iptable_nat             4414  0 
nf_nat                 15735  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      10672  3 iptable_nat,nf_nat
nf_conntrack           61583  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
iptable_mangle          2771  0 
iptable_filter          2271  0 
ip_tables               9991  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               14299  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
snd_ens1371            18814  2 
gameport                9089  1 snd_ens1371
snd_ac97_codec        100646  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ens1371
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  6 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
arc4                    1153  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_ens1371,snd_seq_midi
nls_utf8                1069  1 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nls_cp437               4919  1 
vfat                    8933  1 
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fat                    47767  1 vfat
rt73usb                22434  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
crc_itu_t               1371  1 rt73usb
snd_timer              19098  2 snd_pcm,snd_seq
font                    7557  1 fbcon
rt2x00usb               9703  1 rt73usb
bitblit                 4707  1 fbcon
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt2x00lib              27509  2 rt73usb,rt2x00usb
softcursor              1189  1 bitblit
led_class               2864  1 rt2x00lib
vga16fb                11385  1 
snd                    54148  18 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vgastate                8961  1 vga16fb
mac80211              205146  2 rt2x00usb,rt2x00lib
ppdev                   5259  0 
soundcore               6620  1 snd
amd_k7_agp              4892  1 
lp                      7028  0 
parport_pc             25962  1 
usblp                  10481  0 
cfg80211              126517  2 rt2x00lib,mac80211
snd_page_alloc          7076  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_pcm
i2c_amd756              4151  0 
shpchp                 28820  0 
agpgart                31724  1 amd_k7_agp
parport                32635  3 ppdev,lp,parport_pc
usbhid                 36110  0 
usb_storage            39425  0 
hid                    67032  1 usbhid
floppy                 53016  0 
pata_amd                8766  3 

So we are at least getting somwhere even if the Netget is still not a backup for the D-Link.

---

### Post by n.hinton on 2010-07-10
Don't think the above post is much use, the only differences are in a few of the 'used by' numbers otherwise identical.

---

### Post by roosh on 2010-07-10
Well, as far as I can see, you have two different drivers working at the same time (and possibly conflicting). They are:

rt73usb

rt2870sta

(also there is rt2x00usb, but it seems as if it works with rt73usb). Try the command:

```
sudo rmmod rt73usb
```
and if that still doesn't work,
```
sudo rmmod rt2x00usb
```

---

### Post by Kognit on 2010-07-11
Hi

Try this [http://forum.ubuntuusers.de/topic/wlan-usb-adapter-installieren-1/#post-2248624]("http://forum.ubuntuusers.de/topic/wlan-usb-adapter-installieren-1/#post-2248624")

The page is in german. Just translate it in webbrowser.

Hope it works

---

### Post by n.hinton on 2010-07-11
Well that was fun. sadly no closer to getting the getnet connected to my network though.

sudo rmmod rt73usb put lucid in a semi comatose state, even the D-Link didn't work, although that may not be relevant as neither would nautilus or my terminal, and it wouldn't shut down. First hardware reset, it froze during boot (never done that before), second hardware reset had it up and running. sudo rmmod rt2x00usb made no perceptible difference to anything, and neither did the probably pointless exercise of blacklisting it and rebooting.

Noticed in the German link posted by Kognit, they got one working by blacklisting rt2800usb (already done) and rt3070sta, which I don't have anyway. Also a command, ```
rt2870sta echo | sudo tee -a /etc/modules
```

You can call me stupid, but I make it a policy not to run any command unless, I know exactly what it does and how to undo it (or if it can be undone). My guess is that it adds rt2870sta to /etc/modules, my /etc/modules just contains ```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
``` but rt2870sta is being loaded, so what would be the point?

To summarise then, situation is the same as after blacklisting rt2800usb, getnet can login to wi-fi access points but not my network, D-Link Air Plus works perfectly.

---

### Post by roosh on 2010-07-12
It could be that there is trouble logging in through an encrypted network then. Try temporarily disabling encryption on your network and see if you can connect.

Also, it could be that rt2870sta is the wrong driver. Try running ```
lsusb
``` with the new card plugged-in.

---

### Post by n.hinton on 2010-07-12
Hi roosh,

Nope, wouldn't connect to my network with without security. You were right first time, the rt2870sta is the driver supplied on the CD (drivers attached to post one of this thread) or downloadable from [[color=blue]Linux Driver[/color]](http://www.getnet.eu/data/Driver/Linux%20Driver.rar) at the [[color=blue]getnet www.getnet.eu website[/color]](http://www.getnet.eu/products_GN-531U.html)

Interestingly as never tried before, D-Link will **not** connect to my wi-fi access points, and you can plug both dongles in, D-Link connected to my network and Netget GN-531 connected to my wi-fi points the following is with just one at a time though.
,

This output is with D-Link```

kingfisher@kingfisher-desktop:~$ lsusb
Bus 004 Device 002: ID 03f0:0604 Hewlett-Packard DeskJet 840c
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 07d1:3c03 D-Link System DWL-G122 802.11g Adapter [ralink rt73]
Bus 002 Device 002: ID 045e:001e Microsoft Corp. IntelliMouse Explorer
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1307:0330 Transcend Information, Inc. 
Bus 001 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```



This output is with Getnet GN-531```

kingfisher@kingfisher-desktop:~$ lsusb
Bus 004 Device 002: ID 03f0:0604 Hewlett-Packard DeskJet 840c
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:001e Microsoft Corp. IntelliMouse Explorer
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 003: ID 1307:0330 Transcend Information, Inc. 
Bus 001 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


Beginning to think the 'throw away' part of this thread title, is becoming the most appealing option!

P.S. Thank you for your patience.

Getnet GN-531
Specifications
[IMG]http://www.getnet.eu/images/GN-531U_table.jpg[/IMG]

---

### Post by n.hinton on 2010-07-13
Hi roosh,

It would seem I'm to impatient, closing my hub/router interface after applying no security must have stopped it applying 'no security'.

Spent a little more time today confirming 'no security', the getnet logged straight into my network 97% signal strength.

So it seems the problem is logging in through an encrypted network then.

---

### Post by n.hinton on 2010-07-13
I have had to apologise to my new Netget GN-531, I've called it names, threatened it with the trash can, treated it with contempt and all in all been quite unpleasant toward it.

After I established it would connect to my network from lucid with security disabled, then discovered it worked with wpa2 or wap or wep. It occurred to me to try it with my live Jaunty CD, and there was my network asking for the wpa & wpa2 key, and once provided it worked flawlessly, outperforming my D-Link which cost 5 times the price.

So I hearby formally apologise, sincerely sorry Netget GN-531.

---

### Post by roosh on 2010-07-14
Happy it works (although not as well as it should...) :)

---

### Post by n.hinton on 2010-07-14
Hi roosh,

Thanks for your help, I just wanted it for a backup (because using ethernet would be a major pain). As things stand if the D-Link broke, I could use a Jaunty disk to get on line with the getnet and reconfigure security to work with lucid. So it is a backup.

It seems to be a kernel issue not helped by lack off cooperation from Ralink Technology Corporation, and there maybe an upstream fix in the pipeline, so think I'll hang on for that. See bug [[color=blue]#496093[/color]](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093?comments=all) lot of conflicting posts, but that's the nature of bug reports.

Anyway thanks again.

---

### Post by n.hinton on 2010-07-23
Had one more attempt at the Getnet, and installed 'linux-backports-modules-wireless-lucid-generic' - Magic - all works! even removed 'blacklist rt2800usb' from '/etc/modprobe.d/blacklist.conf', and all works like a dream '802.11n' as well!

The solution to post #1 was, install:
linux-backports-modules-wireless-lucid-generic

---

### Post by antonvaltaz on 2010-09-16
Hi,

Sorry to be very dense (I'm new to Linux although pretty experienced in Windows). I found this thread as I have the same wireless dongle which I'm trying to get to work with Lucid.

To try to install linux-backports-modules-wireless-lucid-generic, I used:

```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```However I got the following error in Terminal:

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```Am I doing something really dense? Is anyone able to advise? (Currently I'm using my HTC Hero as a wireless modem as a workaround, but I'd really like to get my dongle working!).

Thank-you!

---

### Post by n.hinton on 2010-09-16
Try closing any Synaptic's down

---

### Post by antonvaltaz on 2010-09-17
Hi,

I got it working after closing down Firefox. Software installed, rebooted - and all works fine now. :D

Thanks for doing the hard work and finding out what was needed! ;)

---

