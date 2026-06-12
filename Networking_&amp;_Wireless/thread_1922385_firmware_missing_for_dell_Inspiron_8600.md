---
title: "firmware missing for dell Inspiron 8600"
date: 2012-02-08
forum: Networking &amp; Wireless
---

### Post by jkevans on 2012-02-08
I have a dell inspiron 8600.  The Card/Model is BCM 4309, and the PCI ID: 14e4:4324
I cannot get the wireless to work I have tried all sorts of the things suggested on the forum.  I cannot locate a driver for my wireless card.  Does anybody have some experience with this and can give me some advice, please.

Thanks for the help.

---

### Post by varunendra on 2012-02-08
Hello jkevans, welcome to the forums!

Assuming you have really tried 'everything', please try this first:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
sudo apt-get install firmware-b43-installer b43-fwcutter
```Restart and see if you get wireless working. If not, please post the outputs of:
```
lspci -nnk | grep -iA2 net
lsmod
cat /etc/modprobe.d/blacklist.conf | grep -i b43
ls /etc/modprobe.d/blacklist*
```

---

### Post by jkevans on 2012-02-09
```
kadene@kadene-Inspiron-8600:~$ lspci -nnk | grep -iA2
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
kadene@kadene-Inspiron-8600:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
radeon                896428  3 
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25269  1 snd_seq_midi
b43                   296610  0 
ttm                    65184  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 radeon
pcmcia                 39671  0 
joydev                 17322  0 
mac80211              257001  1 b43
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   180037  5 radeon,ttm,drm_kms_helper
cfg80211              156212  2 b43,mac80211
yenta_socket           27230  0 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                 14054  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                73312  0 
soundcore              12600  1 snd
video                  18951  0 
i2c_algo_bit           13184  1 radeon
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
b44                    35301  0 
firewire_ohci          31504  0 
ssb                    45942  2 b43,b44
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
kadene@kadene-Inspiron-8600:~$ cat /etc/modprobe.d/blacklist.conf | grep -i b43
# replaced by b43 and ssb.
kadene@kadene-Inspiron-8600:~$ ls /etc/modprobe.d/blacklist*
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/blacklist-rare-network.conf
/etc/modprobe.d/blacklist-watchdog.conf
kadene@kadene-Inspiron-8600:~$[/CODE
```

---

### Post by varunendra on 2012-02-09
> **jkevans said:**
> kadene@kadene-Inspiron-8600:~$ lspci -nnk | **grep -iA2**
Usage: grep [OPTION]... PATTERN [FILE]...
Sorry, there should have been "net" after "grep -iA2", I missed that! I've corrected that in my original post. So please post again the result of:
```
lspci -nnk | grep -iA2 net
```Rest of everything seems as expected. The correct drivers are loaded:
> **jkevans said:**
> kadene@kadene-Inspiron-8600:~$ lsmod
Module                  Size  Used by
..
..
b43                   296610  0 
..
..
b44                    35301  0 
..
ssb                    45942  2 b43,b44

However, I've read there is a design flaw in the driver ssb (which is actually its 'capability' to control both wired and wireless controllers). Due to this, I suspect you still might not be able to use the wireless. **Please confirm this**.

And and if this is correct, please try this (temporary workaround):
```
sudo modprobe -rfv b43
sudo modprobe -rfv b44
sudo modprobe -rfv ssb
```then, in the exact following sequence:
```
sudo modprobe -v b43
sudo modprobe -v b44
sudo modprobe -v ssb
```and post back whether it works or not.

Also while posting, please wrap the outputs in 'code' tags by clicking on **#** at the top of the box (in which you create new posts) to create the tags, then copy-paste the outputs in-between the tags. This preserves the output formatting and makes it easy-to-read.

**_PS_:**
Please edit your previous post also to wrap the outputs in the same code tags.

---

### Post by jkevans on 2012-02-10
Here is the output I got.

```
kadene@kadene-Inspiron-8600:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
    Subsystem: Dell Device [1028:8127]
    Kernel driver in use: b44
--
02:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 03)
    Subsystem: Dell Truemobile 1450 MiniPCI [1028:0003]
    Kernel driver in use: b43-pci-bridge
kadene@kadene-Inspiron-8600:~$ 

```

> However, I've read there is a design flaw in the driver ssb (which is  actually its 'capability' to control both wired and wireless  controllers). Due to this, I suspect you still might not be able to use  the wireless. **Please confirm this**.

You are right that I am still unable to use the wireless.  So I tried the codes you sent.  Here is the output:
```
kadene@kadene-Inspiron-8600:~$ sudo modprobe -rfv b43
[sudo] password for kadene: 
rmmod /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/b43/b43.ko
rmmod /lib/modules/2.6.38-8-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/2.6.38-8-generic/kernel/net/wireless/cfg80211.ko
kadene@kadene-Inspiron-8600:~$ sudo modprobe -rfv b44
rmmod /lib/modules/2.6.38-8-generic/kernel/drivers/net/b44.ko
rmmod /lib/modules/2.6.38-8-generic/kernel/drivers/ssb/ssb.ko
kadene@kadene-Inspiron-8600:~$ sudo modprobe -rfv ssb
kadene@kadene-Inspiron-8600:~$ sudo modprobe -v b43
insmod /lib/modules/2.6.38-8-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/2.6.38-8-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/2.6.38-8-generic/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/b43/b43.ko 
kadene@kadene-Inspiron-8600:~$ sudo modprobe -v b44
insmod /lib/modules/2.6.38-8-generic/kernel/drivers/net/b44.ko 
kadene@kadene-Inspiron-8600:~$ sudo modprobe -v ssb
kadene@kadene-Inspiron-8600:~$ 

```

---

### Post by varunendra on 2012-02-11
Hmm.. but after running the last three commands, the wireless interface should have started working. Did you check that?

If it still didn't work, please try again with-
```
sudo modprobe -rfv b43
sudo modprobe -rfv b44
```then, only:
```
sudo modprobe -v b43
```
Of course this would temporarily disable the ethernet interface (since you unloaded the driver and didn't load it back). But we just want to see if it helps the wireless or not.

After running the command, wait a few seconds (maybe a minute) to let the wireless get ready, then see if it gets activated. Additionally, please post the output of (after running the above commands):
```
lsmod | grep b4
```

If b43 couldn't help it (although it should, as listed in [this table]("http://linuxwireless.org/en/users/Drivers/b43#Supported_devices")), we may have to resort to [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

---

### Post by jkevans on 2012-02-19
Here is the output that I got after running the commands that you suggested.  

```
kadene@kadene-Inspiron-8600:~$ sudo modprobe -rfv b43
rmmod /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/b43/b43.ko
rmmod /lib/modules/2.6.38-8-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/2.6.38-8-generic/kernel/net/wireless/cfg80211.ko
kadene@kadene-Inspiron-8600:~$ sudo modprobe -rfv b44
rmmod /lib/modules/2.6.38-8-generic/kernel/drivers/net/b44.ko
rmmod /lib/modules/2.6.38-8-generic/kernel/drivers/ssb/ssb.ko
kadene@kadene-Inspiron-8600:~$ sudo modprobe -v b43
insmod /lib/modules/2.6.38-8-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/2.6.38-8-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/2.6.38-8-generic/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/b43/b43.ko 
kadene@kadene-Inspiron-8600:~$ lsmod | grep b4
b43                   296610  0 
ssb                    45942  1 b43
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
```I still am unable to use wireless.  I assume that to check the wireless interface is to look in the upper right hand corner of my screen.  If so, it still says that firmware is missing.

---

### Post by varunendra on 2012-02-20
> **jkevans said:**
> it still says that firmware is missing.
Hmm.. let's see if the firmware has been extracted correctly. Please post the outputs of:
```
dpkg --get-selections | grep -e firmware -e fwcutter
ls -l /lib/firmware/b43
```

It seems the firmware does not get extracted correctly sometimes, I don't know why. If the second command returns any errors, we may have to alternatively download the firmware from here-
[http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)

---

