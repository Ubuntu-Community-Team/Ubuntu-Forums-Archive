---
title: "Compat-wireless making fails"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by Ritherz on 2010-01-21
Hi guys.  First post, and I hope I don't get flamed lol...

I read the HOWTO post a wireless problem guide.  So here's my info:

Computer: Acer aspire 5630

```
$ lspci -nn | grep 'Wireless'
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
``````
$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"Queenofhearts"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:51:3A:F8:79   
          Bit Rate=36 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``````
$ lsmod
Module                  Size  Used by
bridge                 56384  0 
stp                     3012  1 bridge
bnep                   15168  0 
btusb                  14260  0 
binfmt_misc            10220  1 
ppdev                   8232  0 
joydev                 13088  0 
snd_hda_codec_realtek   277860  1 
arc4                    2144  2 
ecb                     3296  2 
pcmcia                 40116  0 
iwl3945                90208  0 
iwlcore               133600  1 iwl3945
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
mac80211              210008  2 iwl3945,iwlcore
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
gspca_vc032x           23552  0 
iptable_filter          3872  0 
gspca_main             26816  1 gspca_vc032x
ip_tables              21200  1 iptable_filter
videodev               43360  1 gspca_main
v4l1_compat            16804  1 videodev
x_tables               25832  1 ip_tables
v4l2_compat_ioctl32    13344  1 videodev
acer_wmi               18504  0 
sdhci_pci               8928  0 
yenta_socket           27628  1 
rsrc_nonstatic         11840  1 yenta_socket
sdhci                  20484  1 sdhci_pci
pcmcia_core            42692  3 pcmcia,yenta_socket,rsrc_nonstatic
led_class               5256  4 iwl3945,iwlcore,acer_wmi,sdhci
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
psmouse                57124  0 
serio_raw               6596  0 
cfg80211              109144  3 iwl3945,iwlcore,mac80211
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
lp                     11908  0 
parport                40528  2 ppdev,lp
usbhid                 43968  0 
b44                    34352  0 
ssb                    40944  1 b44
mii                     6368  1 b44
video                  23612  0 
output                  3680  1 video
intel_agp              32816  0 
``````
$ dmesg
```(nothing)

```
$ sudo lshw -C network
[sudo] password for ritherz: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:54:00:31
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.68 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:d2100000-d2100fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:aa:92:e1
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:21 memory:d2000000-d2001fff
``````
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:23:51:3A:F8:79
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Queenofhearts"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001bc0b181
                    Extra: Last beacon: 86090ms ago
                    IE: Unknown: 000D517565656E6F66686561727473
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
``````

$ lsb_release -d
Description:    Ubuntu 9.10
``````

$ uname -mr
2.6.31-17-generic x86_64
``````
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]

```Ok, so now that's all out of the way... (tried to make it as pretty as possible)
The issue I'm having is that I'm trying to install the compat drivers for my network card, but it keeps giving me errors:

```
ritherz@ubuntu:~/Downloads$ tar -xjf compat-wireless-2.6.31-rc7.tar.bz2 
ritherz@ubuntu:~/Downloads$ cd compat-wireless-2.6.31-rc7/
ritherz@ubuntu:~/Downloads/compat-wireless-2.6.31-rc7$ make
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.31-17-generic/build M=/home/ritherz/Downloads/compat-wireless-2.6.31-rc7 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  LD      /home/ritherz/Downloads/compat-wireless-2.6.31-rc7/drivers/misc/eeprom/built-in.o
make[3]: *** No rule to make target `/home/ritherz/Downloads/compat-wireless-2.6.31-rc7/drivers/misc/eeprom/max6875.c', needed by `/home/ritherz/Downloads/compat-wireless-2.6.31-rc7/drivers/misc/eeprom/max6875.o'.  Stop.
make[2]: *** [/home/ritherz/Downloads/compat-wireless-2.6.31-rc7/drivers/misc/eeprom] Error 2
make[1]: *** [_module_/home/ritherz/Downloads/compat-wireless-2.6.31-rc7] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [modules] Error 2
ritherz@ubuntu:~/Downloads/compat-wireless-2.6.31-rc7$ 

```Now I am knowledgeable of some coding like c++/java so I've seen these errors before, so I've tried going out and getting that max6875.c file (off the net) and putting it where it needs to be and trying to make clean, then make again.  It gets further, but then is stopped by another file... then another, etc.

I'm NOT very knowledgeable of how linux works so I'm not sure if I'm just missing some source files or what?

I've seen the same question posted all over the internet with no solutions :(

---

### Post by chili555 on 2010-01-21
Your wireless card is working beautifully, we see:> broadcast=yes driver=iwl3945 ip=192.168.1.68 What do you need compat-wireless for, some kinda injection/aircrack/h4x0r deal? Yeah, we thought so.

Do you have build-essential installed? What are the other requirements in the INSTALL or README? All in place? If those steps still don't result in a clean make, please let us have a link to where you downloaded compat so we can examine the files.> I've tried going out and getting that max6875.c file (off the net) and putting it where it needs to be This almost never works. These .c files are usually, not always, part of a bigger package and the compat Makefile needs the whole car, not just the ashtray.

---

### Post by chili555 on 2010-01-21
NM, I think I got it. Please do:```
sudo apt get install build-essential
cd ~/Downloads/compat-wireless-2.6.31-rc7/
./scripts/driver-select intel
make
sudo make install
```Post back if you are still stuck.

---

### Post by Ritherz on 2010-01-21
Ok, I've never heard of this "build-essential" thing, but i tried your sudo line and it worked, installed it and all.

Where I'm stuck is "./scripts/driver-select intel".  I came across this solution on the internet somewhere (notably WITHOUT the build-essential install), but I couldn't get it to work none the less.  Here's what it gives me:

```

Setting up build-essential (11.4) ...
ritherz@ubuntu:~$ cd Downloads/compat-wireless-2.6.31-rc7/
ritherz@ubuntu:~/Downloads/compat-wireless-2.6.31-rc7$ ./scripts/driver-select intel
bash: ./scripts/driver-select: No such file or directory
ritherz@ubuntu:~/Downloads/compat-wireless-2.6.31-rc7$ /scripts/driver-select intel
bash: /scripts/driver-select: No such file or directory

```
I guess I'm a bit further at least lol.
Also, can you tell me what that line does even?  Like is it a pearl script or something (have no idea honestly).
Thank you!

---

### Post by chili555 on 2010-01-21
> compat-wireless-2.6.31-rc7/Oops! Sorry. I downloaded and experimented with 2.6.32-rc7, not x.31. 

32 has the ability to select the driver you want to build and skip all the Zydas, Broadcom, etc. that you don't want or need. 31 evidently doesn't. My bad!

Just run 'make' and 'sudo make install.'

---

### Post by Ritherz on 2010-01-21
righto.  I tried that and I came up with the same error (forgot to include in my last post):
```

ritherz@ubuntu:~/Downloads/compat-wireless-2.6.31-rc7$ ./scripts/driver-select intel
bash: ./scripts/driver-select: No such file or directory
ritherz@ubuntu:~/Downloads/compat-wireless-2.6.31-rc7$ make
make -C /lib/modules/2.6.31-17-generic/build M=/home/ritherz/Downloads/compat-wireless-2.6.31-rc7 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
make[3]: *** No rule to make target `/home/ritherz/Downloads/compat-wireless-2.6.31-rc7/drivers/misc/eeprom/max6875.c', needed by `/home/ritherz/Downloads/compat-wireless-2.6.31-rc7/drivers/misc/eeprom/max6875.o'.  Stop.
make[2]: *** [/home/ritherz/Downloads/compat-wireless-2.6.31-rc7/drivers/misc/eeprom] Error 2
make[1]: *** [_module_/home/ritherz/Downloads/compat-wireless-2.6.31-rc7] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [modules] Error 2
```When I look in the folder drivers/misc/eeprom/ there is no max6875.c.  That is why I tried just finding another file to put in there to make it work (as I wouldn't be using the max6875 driver anyways - least thats what i thought lol)

Edit: would it be an idea just to upgrade/update to 2.6.3x (whatever is the newest)?  I have no idea how to do that... but just a thought.
Edit2: Link to where I got it: [http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)
:(  Thanks again

---

### Post by chili555 on 2010-01-21
I get the same error when I try to build x.31. 32 makes and installs properly. Go figure.

If you must have compat wireless, I suggest 32. Actually the iwl3945 you are using does monitor mode and, according to all I've read, packet injection.

---

### Post by Ritherz on 2010-01-22
Thanks a bunch, I'm further then I've ever been now.

I tried make-ing the 32 and it worked.  Installed, (some warnings) and it worked.  Now I've tried unloading - it disconnected my wireless as it should.  But then it stopped working trying to unload.  So I've just restarted.  This is what it gave me before the restart:

```

(lots before this)
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
Updating Ubuntu's initramfs for 2.6.31-wl under /boot/ ...
Cannot find /lib/modules/2.6.31-wl
Will now run update-grub to ensure grub will find the new initramfs ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found Windows NT/2000/XP on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
depmod will prefer updates/ over kernel/ -- OK!
WARNING: -e needs -E or -F
Currently detected wireless subsystem modules:

updates/net/mac80211/mac80211.ko
updates/net/wireless/cfg80211.ko
updates/net/wireless/lib80211.ko
updates/drivers/net/wireless/adm8211.ko
updates/drivers/net/wireless/ath/ar9170/ar9170usb.ko
updates/drivers/net/wireless/at76c50x-usb.ko
updates/drivers/net/wireless/ath/ath.ko
updates/drivers/net/wireless/ath/ath5k/ath5k.ko
updates/drivers/net/wireless/ath/ath9k/ath9k.ko
updates/drivers/net/wireless/b43/b43.ko
updates/drivers/net/wireless/b43legacy/b43legacy.ko
updates/drivers/net/b44.ko
updates/drivers/net/usb/cdc_ether.ko
updates/drivers/misc/eeprom/eeprom_93cx6.ko
updates/drivers/net/wireless/ipw2x00/ipw2100.ko
updates/drivers/net/wireless/ipw2x00/ipw2200.ko
updates/drivers/net/wireless/iwlwifi/iwl3945.ko
updates/drivers/net/wireless/iwlwifi/iwlagn.ko
updates/drivers/net/wireless/iwlwifi/iwlcore.ko
updates/net/wireless/lib80211_crypt_ccmp.ko
updates/net/wireless/lib80211_crypt_tkip.ko
updates/net/wireless/lib80211_crypt_wep.ko
updates/drivers/net/wireless/libertas/libertas.ko
updates/drivers/net/wireless/libertas/libertas_cs.ko
updates/drivers/net/wireless/libertas/libertas_sdio.ko
updates/drivers/net/wireless/libertas/libertas_spi.ko
updates/drivers/net/wireless/libertas_tf/libertas_tf.ko
updates/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
updates/drivers/net/wireless/ipw2x00/libipw.ko
updates/drivers/net/wireless/mac80211_hwsim.ko
updates/drivers/net/wireless/mwl8k.ko
updates/drivers/net/wireless/p54/p54common.ko
updates/drivers/net/wireless/p54/p54pci.ko
updates/drivers/net/wireless/p54/p54spi.ko
updates/drivers/net/wireless/p54/p54usb.ko
updates/drivers/net/usb/rndis_host.ko
updates/drivers/net/wireless/rndis_wlan.ko
updates/drivers/net/wireless/rt2x00/rt2400pci.ko
updates/drivers/net/wireless/rt2x00/rt2500pci.ko
updates/drivers/net/wireless/rt2x00/rt2500usb.ko
updates/drivers/net/wireless/rt2x00/rt2x00lib.ko
updates/drivers/net/wireless/rt2x00/rt2x00pci.ko
updates/drivers/net/wireless/rt2x00/rt2x00usb.ko
updates/drivers/net/wireless/rt2x00/rt61pci.ko
updates/drivers/net/wireless/rt2x00/rt73usb.ko
updates/drivers/net/wireless/rtl818x/rtl8180.ko
updates/drivers/net/wireless/rtl818x/rtl8187.ko
updates/drivers/ssb/ssb.ko
updates/drivers/net/wireless/libertas/usb8xxx.ko
updates/drivers/net/usb/usbnet.ko
updates/drivers/net/wireless/zd1211rw/zd1211rw.ko

Now run:

make unload

And then load the wireless module you need. If unsure reboot.
``````

ritherz@ubuntu:~/Downloads/compat-wireless-2.6.32.3$ make unload
Unloading ssb...
FATAL: Module ssb is in use.
Unloading iwl3945...
FATAL: Error removing iwl3945 (/lib/modules/2.6.31-17-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko): Operation not permitted
Unloading iwlcore...
FATAL: Module iwlcore is in use.
Unloading mac80211...
FATAL: Module mac80211 is in use.
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
ritherz@ubuntu:~/Downloads/compat-wireless-2.6.32.3$ sudo make unload
Unloading ssb...
FATAL: Module ssb is in use.
Unloading iwl3945...
ritherz@ubuntu:~/Downloads/compat-wireless-2.6.32.3$ sudo make load 
all              install-modules  Makefile         unload
clean            install-scripts  modules          
install          load             uninstall        
ritherz@ubuntu:~/Downloads/compat-wireless-2.6.32.3$ sudo make load ipw3945
Unloading ssb...
FATAL: Module ssb is in use.
Loading ipw2100...
Loading ipw2200...
Loading libertas_cs...
Loading usb8xxx...
Loading p54pci...
Loading p54usb...
Loading adm8211...
Loading zd1211rw...
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
Loading p54usb...
Loading iwl3945...
Loading iwlagn...
Loading ath...
Loading ar9170usb...
Loading rtl8180...
Loading rtl8187...
Loading rt2400pci...
Loading rt2500pci...
Loading rt61pci...
Loading rt2500usb...
Loading rt73usb...
Loading rndis_wlan...
Loading at76_usb...
Loading mwl8k...
Loading mac80211_hwsim...
Loading at76c50x_usb...
Module ath_pci not detected -- this is fine
ath5k loaded successfully
ath9k loaded successfully
Module bcm43xx not detected -- this is fine
Module wl not detected -- this is fine
FATAL: Error inserting b43 (/lib/modules/2.6.31-17-generic/updates/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting b43legacy (/lib/modules/2.6.31-17-generic/updates/drivers/net/wireless/b43legacy/b43legacy.ko): Unknown symbol in module, or unknown parameter (see dmesg)
b43 loaded successfully
b43legacy loaded successfully
make: *** No rule to make target `ipw3945'.  Stop.
ritherz@ubuntu:~/Downloads/compat-wireless-2.6.32.3$ sudo make unload
Unloading ipw2100...
Unloading ipw2200...
Unloading libertas_cs...
Unloading usb8xxx...
Unloading adm8211...
Unloading zd1211rw...
Unloading ssb...
FATAL: Module ssb is in use.
Unloading iwl3945...
Unloading iwlagn...
Unloading ath9k...
Unloading ath5k...
Unloading ar9170usb...
Unloading p54pci...
Unloading p54usb...
Unloading rt2400pci...
Unloading rt2500pci...
Unloading rt61pci...
Unloading rt2500usb...
Unloading rt73usb...
Unloading rtl8180...
Unloading rtl8187...
Unloading mwl8k...
Unloading mac80211_hwsim...
Unloading at76c50x_usb...
./scripts/unload.sh: line 48: 21592 Killed                  modprobe -r --ignore-remove $i
Unloading at76_usb...
```
Unloading this took waaaay too long so I decided to restart (as per the first message this would just automatically work it out for me)

Is there any way to find out if it installed properly?  I'm kind of confused at this point.  It seems to be using the same driver- so is it using the updated version?  Hopefully I'm nearing the end of my escapades lol.

Thank you so much for getting me this far :)

---

### Post by Ritherz on 2010-01-22
Seems to be working now, thank you very much.

---

