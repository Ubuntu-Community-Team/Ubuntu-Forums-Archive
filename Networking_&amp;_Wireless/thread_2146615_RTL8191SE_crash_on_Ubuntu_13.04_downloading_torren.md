---
title: "RTL8191SE crash on Ubuntu 13.04 downloading torrents"
date: 2013-05-18
forum: Networking &amp; Wireless
---

### Post by adrdown on 2013-05-18
Hello,


WIFI drops constantly downloading torrents ...


My WIFI is rtl8191se, here make command gives error:

```

root@NOTADR:/home/rtl# make
make -C /lib/modules/3.8.0-19-generic/build M=/home/rtl modules
make[1]: Entrando no diretório `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /home/rtl/base.o
/home/rtl/base.c: Na função ‘_rtl_init_mac80211’:
/home/rtl/base.c:319:6: erro: ‘IEEE80211_HW_BEACON_FILTER’ undeclared (first use in this function)
/home/rtl/base.c:319:6: nota: each undeclared identifier is reported only once for each function it appears in
/home/rtl/base.c: Na função ‘rtl_action_proc’:
/home/rtl/base.c:861:25: erro: ‘RX_FLAG_MACTIME_MPDU’ undeclared (first use in this function)
/home/rtl/base.c: Na função ‘rtl_send_smps_action’:
/home/rtl/base.c:1414:16: erro: ‘struct <anônimo>’ has no member named ‘sta’
make[2]: ** [/home/rtl/base.o] Erro 1
make[1]: ** [_module_/home/rtl] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-3.8.0-19-generic'
make: ** [all] Erro 2
```

[Driver download Realtek link]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2262")

---

### Post by varunendra on 2013-05-18
Hi adrdown, welcome to the forums ! :)

Let's do some routine checks first to make sure you are trying the correct driver for correct device. Accordingly, please post outputs of :
```
lspci -nnk | grep -iA2 net
lsmod
```

The errors you got are typical for the latest kernel, and there exists a very crude workaround that allows the source to compile, but compromises its performance. So I want to make sure if we really need it.

**PS:**
Please use 'Code' tags to post commands and outputs. It preserves the formatting and makes it easier to read. Please follow the "Code tags example" link in my signature to see how to do it.

---

### Post by adrdown on 2013-05-19
Thanks Varun, with tag 'Code' is very better, updated post...

My WIFI is a rtl819**1**se not rtl819**2**se

Objective is eliminate the constant crashs, especially with torrents ...

```

root@NOTADR:/home/adr# lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
	Subsystem: Quanta Microsystems, Inc Device [1a32:0308]
	Kernel driver in use: rtl8192se
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8131 Gigabit Ethernet [1969:1063] (rev c0)
	Subsystem: LG Electronics, Inc. Device [1854:0821]
	Kernel driver in use: atl1c
```


```

root@NOTADR:/home/adr# lsmod
Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  12 
joydev                 17377  0 
snd_hda_codec_hdmi     36996  4 
nvidia               9410995  58 
snd_hda_codec_realtek    47037  1 
snd_hda_intel          43715  7 
snd_hda_codec         188899  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
snd_hwdep              13602  1 snd_hda_codec
arc4                   12615  2 
snd_pcm                97451  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
mxm_wmi                13021  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
rtl8192se              63284  0 
rtlwifi                79673  1 rtl8192se
snd                    68876  23 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
wmi                    19070  1 mxm_wmi
video                  19390  0 
uvcvideo               80847  0 
mac80211              606457  2 rtlwifi,rtl8192se
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
soundcore              12680  1 snd
btusb                  22474  0 
cfg80211              510937  2 mac80211,rtlwifi
mac_hid                13205  0 
lpc_ich                17061  0 
psmouse                95870  0 
microcode              22881  0 
bluetooth             228619  22 bnep,btusb,rfcomm
serio_raw              13215  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
atl1c                  41071  0 
ahci                   25731  2 
libahci                31364  1 ahci
```

---

### Post by varunendra on 2013-05-19
> **adrdown said:**
> My WIFI is a rtl819**1**se not rtl819**2**se
Thanks for pointing that out, I really missed it earlier :)
Although it shouldn't affect the patch since basic build process is same. 

However, I'd suggest to try a driver parameter first -
```
sudo modprobe -rfv rtl8192se
sudo modprobe -v rtl8193se swenc=1
```

If that doesn't help, you may try a few other parameters separately or simultaneously -
```
sudo modprobe -rfv rtl8192se
sudo modprobe -v rtl8192se swenc=1 ips=0 fwlps=0
```
Also, make sure power management is "off" on wireless -
```
sudo iwconfig wlan0 power off
```
assuming your wireless interface is "wlan0"

If none of these help, we'll try compiling the proprietary one.

I am working on the drivers from the links you posted (you seem to have corrected the link now). The one from the [earlier link]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2302") seems to be newer (2013 vs 2011 for the current one) and looks like the fix has already been applied in it. I'll post back after some testing.

Although it (the driver from the earlier link) says "rtl8192se", its "Readme" says it has support for your device. But let me make sure first. Meanwhile, please post back if the above suggested changes make any difference.

---

### Post by coffeecat on 2013-05-19
Moved to own thread. (Different kernel from original thread.)

---

### Post by praseodym on 2013-05-19
Which driver version is it? The latest is 0012.0207.2013

See here:

[http://forum.ubuntuusers.de/topic/realtek-rtl8188ce-treiber-installieren/2/#post-5443987](http://forum.ubuntuusers.de/topic/realtek-rtl8188ce-treiber-installieren/2/#post-5443987)

Your card is supported, see the grey boxes

---

### Post by adrdown on 2013-05-19
Thank you all for the support and sorry for my English, I'm learning here with you Linux and English at the same time :D

Good news!!


Yesterday wifi crashed, ran the commands given by Varun

```

sudo modprobe -rfv rtl8192se
sudo modprobe -v rtl8192se swenc=1

```

Wifi stable so far, for 17 hours straight !!!

I ran the command:

```

echo "options rtl8192se swenc=1" > /etc/modprobe.d/rtl8192se.conf

```

Restarted notebook, I will continue testing, so do not put thread as solved ...

Set power management in "off" for wireless, gives error:

```

root@NOTADR:/home/adr# **iwconfig wlan0 power off**
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

```

> **praseodym said:**
> Which driver version is it? The latest is 0012.0207.2013

See here:

[http://forum.ubuntuusers.de/topic/realtek-rtl8188ce-treiber-installieren/2/#post-5443987](http://forum.ubuntuusers.de/topic/realtek-rtl8188ce-treiber-installieren/2/#post-5443987)

Your card is supported, see the grey boxes

Praseodym, very interesting your comment, ethtool installed via apt-get and ran the command:

```

root@NOTADR:/home/adr# **ethtool -i wlan0**
driver: rtl8192se
version: 3.8.0-19-generic
firmware-version: N/A
bus-info: 0000:02:00.0
supports-statistics: yes
supports-test: no
supports-eeprom-access: no
supports-register-dump: no
supports-priv-flags: no

```

Modinfo also did not help, any suggestions?

```

root@NOTADR:/home/adr# **modinfo rtl8192se**
filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     1BE0F8051988F4889071D73
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.8.0-19-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

```

---

### Post by varunendra on 2013-05-19
> **adrdown said:**
> Good news!!

Yesterday wifi crashed, ran the commands given by Varun

```

sudo modprobe -rfv rtl8192se
sudo modprobe -v rtl819**[COLOR="#FF0000"]3[/COLOR]**se swenc=1

```

Wifi stable so far, for 17 hours straight !!!
I assume the above is just a typo in the second command. There is no driver called rtl819**[COLOR="#FF0000"]3[/COLOR]**se as far as I know ;)

Good news indeed! Because yesterday I wasted almost half a day trying to compile the proprietary driver(s) on 13.04, couldn't succeed :P
The workaround I mentioned earlier turns out to work on Quantal and earlier ones only, not on 13.04.

However, I doubt about this additional command you ran -
> ```

echo "options rtl8192se swenc=1" > /etc/modprobe.d/rtl8192se.conf

```
Unless you are root (**sudo su** before the command), the above command should return "permission denied" error. If so, the .conf file you tried won't have been created yet, so the wireless will load with default settings again after reboot.

So double-check -
```
cat /etc/modprobe.d/rtl8192se.conf
```
If the file is there, it'll show its contents, else it'll return "no such file or directory" error.
If you get the error, create it as follows -
```
echo "options rtl8192se swenc=1" | sudo tee /etc/modprobe.d/rtl8192se.conf
```

Also, I couldn't understand anything about what you said about praseodym's comment. Did you guys have some 'off-the-record' conversation? (pm, irc, etc??)
Nevermind if it is something that is none of my business :P


**PS:**
For some weird reason, this thread is not coming up in my search results (I have to keep it open in a separate tab and refresh to notice any new posts). So feel free to PM me if I lost track of it and you needed help.

Good Luck!

---

### Post by adrdown on 2013-05-20
> **varunendra said:**
> 
I assume the above is just a typo in the second command. There is no driver called rtl819**[COLOR=#FF0000]3[/COLOR]**se as far as I know ;)


Yes, it was a typo error, I edited the post and fix the command to help future readers

> **varunendra said:**
> 
Good news indeed! Because yesterday I wasted almost half a day trying to compile the proprietary driver(s) on 13.04, couldn't succeed :P
The workaround I mentioned earlier turns out to work on Quantal and earlier ones only, not on 13.04.


Guess work and difficulty, thanks a lot, but I believe the command you have suggested will solve, I keep testing to make sure

> **varunendra said:**
> 
However, I doubt about this additional command you ran -

Unless you are root (**sudo su** before the command), the above command should return "permission denied" error. If so, the .conf file you tried won't have been created yet, so the wireless will load with default settings again after reboot.

Yes always use "sudo su", I think more practical

> **varunendra said:**
> 
So double-check -
```
cat /etc/modprobe.d/rtl8192se.conf
```
If the file is there, it'll show its contents, else it'll return "no such file or directory" error.
If you get the error, create it as follows -
```
echo "options rtl8192se swenc=1" | sudo tee /etc/modprobe.d/rtl8192se.conf
```


Yes, I checked, all ok, "/etc/modprobe.d/rtl8192se.conf" was created correctly

> **varunendra said:**
> 
Also, I couldn't understand anything about what you said about praseodym's comment. Did you guys have some 'off-the-record' conversation? (pm, irc, etc??)
Nevermind if it is something that is none of my business :P


No, it was not a conversation PM, forgot to quote the post Praseodym

> **varunendra said:**
> 
**PS:**
For some weird reason, this thread is not coming up in my search results (I have to keep it open in a separate tab and refresh to notice any new posts). So feel free to PM me if I lost track of it and you needed help.

Good Luck!


For now all ok


Thanks a lot,

---

### Post by varunendra on 2013-05-20
> **adrdown said:**
> Yes always use "sudo su", I think more practical
But 'More risky' as well :). Because any files you create while being root, are owned by root, and with exclusive permissions to root-only. Thus if you are not careful, you may end up creating stuff in your own home that is owned by root and you can't open it ;)

> For now all ok

Thanks a lot,
Let's hope it stays that way. I'll eagerly wait for it to be marked as [Solved] :)

---

### Post by adrdown on 2013-05-20
Solved !!!!


Thank you all,


Commands

```

sudo modprobe -rfv rtl8192se
sudo modprobe -v rtl8192se swenc=1

```

After setting to load at boot:

```

echo "options rtl8192se swenc=1" | sudo tee /etc/modprobe.d/rtl8192se.conf

```

---

### Post by odetosummer on 2013-09-26
Those commands above did not work for me, yet I managed to stop wifi from crashing by configuring the torrent client settings in a way that requires encryption from peers - for some reason that's all it takes for my wifi to work flawlessly.

---

