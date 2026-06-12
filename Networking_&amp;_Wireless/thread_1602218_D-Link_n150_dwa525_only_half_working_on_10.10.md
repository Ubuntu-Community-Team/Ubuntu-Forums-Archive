---
title: "D-Link n150 dwa525 only half working on 10.10"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by lovelypecs on 2010-10-21
Hey everybody! So I've upgraded to Maverick but now I cannot get my wireless card working. In Lucid it didn't work out of the box, but worked perfectly by wrapping the Windows driver with ndiswrapper.

I noticed when I installed Maverick that wireless is enabled in Network-Manager and it gives me the option to create a wireless network or connect to a hidden network but it's not discovering/showing any of the wireless networks in range! So it seems as though the card is being recognized but the driver isn't working fully...? I tried wrapping the windows drivers, but that didn't change the situation at all.

If someone could shed some light on the situation for me I would be very grateful! I wasn't prepared to install linux drivers myself as it seems to be almost working.

Details of my system:

```
Ubuntu 10.10
2.6.35-22-generic x86_64
```

```
Desktop PC:
Intel Core i5 750
4GB ddr3 ram
Intel P55 Whitesburg mainboard
```

```
D-Link n150 DWA-525
RaLink Device 3060
```

```
 wlan0     Link encap:Ethernet  HWaddr 1c:af:f7:0c:81:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

```
Module                  Size  Used by
nls_iso8859_1           4657  1 
nls_cp437               6375  1 
vfat                   10954  1 
fat                    56244  1 vfat
ses                     7065  0 
enclosure               8553  1 ses
usb_storage            50372  1 
parport_pc             30086  0 
ppdev                   6804  0 
binfmt_misc             7984  1 
snd_hda_codec_nvhdmi    14587  4 
joydev                 11363  0 
snd_hda_codec_realtek   299533  1 
wacom                  33261  0 
snd_hda_intel          26019  2 
snd_hda_codec         100919  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
nvidia              10221046  48 
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
arc4                    1497  2 
snd_seq_midi_event      7291  1 snd_seq_midi
rt2800pci              10233  0 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
rt2800lib              31970  1 rt2800pci
rt2x00usb              11316  1 rt2800lib
snd_timer              23850  2 snd_pcm,snd_seq
rt2x00pci               6993  1 rt2800pci
crc_ccitt               1699  1 rt2800pci
rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
led_class               3393  1 rt2x00lib
mac80211              266657  3 rt2x00usb,rt2x00pci,rt2x00lib
lp                     10201  0 
snd                    64117  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport                37032  3 parport_pc,ppdev,lp
cfg80211              170293  2 rt2x00lib,mac80211
eeprom_93cx6            1789  1 rt2800pci
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
firewire_ohci          24679  0 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
usbhid                 42062  0 
hid                    84678  1 usbhid
e1000e                151787  0
```

```
[   11.513988] rt2800pci 0000:05:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.520533] Registered led device: rt2800pci-phy0::radio
[   11.520544] Registered led device: rt2800pci-phy0::assoc
[   11.520556] Registered led device: rt2800pci-phy0::quality
[   12.848066] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
```

```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
```

I hope that is sufficient information. Any help would be much appreciated!!

---

### Post by lovelypecs on 2010-10-21
Anyone? Even if you just point me to a different thread, that would be helpful! :)
 
Thanks in advance

---

### Post by ed_masterplue on 2010-10-25
hi, i have the same problem, but let me tell you it`s a kernel issue, what i`m doing is booting from thye old kernel, as soon as i get a solution i will let you know, if you get it before me, please let me know, but using your old kernel until you get a solution it`s not bad a idea

---

### Post by ed_masterplue on 2010-10-31
Hi again, as i promised i have a solution, it worked for me, I hope this can help you as well
in your console type
> lshw -C network
 you will see the network devices, including RT3060 that is the one of your card, check the driver it should say rt2800pci, then in your terminal run
> sudo gedit /etc/modprobe.d/blacklist.conf

you have to add this line
 blacklist rt2800pci

save it and reboot

then you will see the card is disable, because there is no driver for your card, 
the next thing i did was download the drivers 
[COLOR="Red"][[COLOR="Red"][SIZE="5"]DRIVERS DWA-525[/SIZE][/COLOR]]("http://www.ralinktech.com/download.php?t=U0wyRnpjMlYwY3k4eU1ERXdMekEzTHpFMkwyUnZkMjVzYjJGa05qZ3lOVE14TnpnMU1DNWllakk5UFQweU1ERXdYekEzWHpFMlgxSlVNekEyTWw5TWFXNTFlRjlUVkVGZmRqSXVOQzR3TGpBdWRHRnlD")[/COLOR]
compile the drivers running (before compiling you have to read README_STA file)
> sudo make
> sudo make install

reboot again and you should have your DLink card running

that is what i did and worked for me, i could not find information about this issue, it's been a long week making it work, so i hope this helps you :P

---

### Post by surajrajpurohit on 2010-11-23
hi everybody....
 Even i hve the same problem..my adapter is dlink n a50 dwa 525 with ralink 3060 chipset...im using ubuntu 10.10 version.....
my friend ed_master plue has given da link to get the drivers...but the link is not working...its showing ERORR:Page not found...im new to Ubuntu...i request u all to help me...

---

### Post by lovelypecs on 2010-11-25
Hey, so sorry I'm only replying now! Thanks a lot ed_masterplue for the help! I am going to go try it right now, I will report back with results... good or bad.

surajrajpurohit, I also get the error message so I went to [www.ralinktech.com](www.ralinktech.com), clicked on Software at the top then chose Linux from the side menu on the left and then downloaded the RT3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT3592) file because it says 3060 which is the dwa-525. I hope it is the right one, Im gonna go find out now!

Thanks again for the help guys.

---

### Post by lovelypecs on 2010-11-25
Just gave your instructions a go and it didn't work :( Did I download the correct drivers from ralink? Also, the instructions in the README_STA file were quite vague to me. I was able to edit a few things like the path to my kernel source but the rest was greek to me, so maybe I need to change something in the config before I compile it?

Also my wireless card doesn't show up at all anymore. ifconfig gives me lo and eth0 but no wlan0 anymore. lshw -C network recognizes a pci ralink device but says that it is UNCLAIMED and has no driver.

So I think I've taken a step or two backwards :( I'm considering just hardwiring the network here and forgetting about wireless :-P

Thanks for the help though, glad it worked for you!

---

### Post by dchky on 2010-12-01
I'll add another "not working for me either"

I can scan for networks okay, driver is installed and functional, but whenever it actually tries to connect to a network it hard locks my computer.

---

### Post by surajrajpurohit on 2010-12-08
Some success n some failure...

As it was greek n latin for me to install drivers from READ_STA file..
So i tried using _**ndiswrapper**_.....with my adopter i got drivers cd for xp...so using ndiswrapper i tried to install drivers...and i think the drivers got installed ...it shows wlan0 when i give command ifconfig or iwconfig...BUT NOW THE PROBLEM IS....
my network manager is not detecting any network to connect...i tried by installing drivers again....the same story repeats........ 
i advice lovelypecs to try ndiswrapper
i request all the ubuntu memebers plz to me as i'm new to ubuntu....

---

### Post by surajrajpurohit on 2010-12-08
IM sending a LINK on Ndiswrapper.... might it'll b usefull for all the members who r having dis problem...

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Introduction](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Introduction)

---

### Post by surajrajpurohit on 2010-12-13
HURRY!!!!!!!!! i got connected......by using ndiswrapper....

---

### Post by totterdell91 on 2010-12-26
If you have 

a)downloaded the drivers and unpacked them
and
b) you have blacklisted the rt2800pci using root privileges and saved the blacklist configuration file

To get it working, simply change to the driver directory,
do a 

make, 
then "sudo make install", 
then a "sudo modprobe rt3562sta".

the driver should work at this point

then shut down
then restart

and make sure it will work from a cold boot ( this is something I had a problem with)

---

### Post by JCBrand on 2011-03-25
Installing the **rt3562sta** drivers didn't work for me the first few times.

Until I found this page (in Russian):
[http://beta.ubuntu.ru/index.php?action=printpage;topic=134661.0](http://beta.ubuntu.ru/index.php?action=printpage;topic=134661.0)

Here are the steps that need to be done:

[LIST]
[*]First download the driver (as explained earlier in this thread).
[*]Also download the firmware (this was never mentioned!).
[*]Copy (as superuser) the firmware *.bin file to /lib/firmware
[/LIST]

Next you need to edit os/linux/config.mk (in the directory of the driver's tar file that you extracted).

In the terminal:

[INDENT]sudo gedit os/linux/config.mk[/INDENT]

Changing the parameters of lines on "y"
[INDENT]HAS_WPA_SUPPLICANT = y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = y
[/INDENT]

Now run: sudo make && sudo make install

This worked for me, hope it helps!

---

### Post by Pougmahone on 2011-03-27
> **surajrajpurohit said:**
> IM sending a LINK on Ndiswrapper.... might it'll b usefull for all the members who r having dis problem...
 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Introduction](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Introduction)
 
this is a very helpful link, thanks for that, BUT, when i get to the 
**3.3. Downloading Windows Drivers**

part of it, i run into an issue, that being i cannot find either: the dlink dwa-525 card listed, or any other card in the list that has the same chipset....
 
so wich one do i use?

---

### Post by lovelypecs on 2011-06-14
Hey! I decided to give this one more go yesterday. And I got it working with the open source drivers on Elementary OS Jupiter 64bit (has the same kernel as Ubuntu 10.10)! I first attempted the ndiswrapper route but the was unsuccessful.

To get it working I first blacklisted these drivers in /etc/modprobe.d/blacklist.conf:

```
blacklist rt2800pci

blacklist bcm43xx

blacklist b43

blacklist b43legacy

blacklist ssb
```The extra stuff I blacklisted there was suggested by the ndiswrapper manual.

I then compiled the "DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217" driver found on RaLinks website and started the driver as per totterdell91's instructions. After a reboot it worked!

Now I'm trying to get it working on Natty but having major issues with booting with the card in the pci slot :-/ I started a thread about that issue _**[here]("http://ubuntuforums.org/showthread.php?p=10937538#post10937538")**_. Thanks a lot to ed_masterplue, totterdell91 and JCBrand for their suggestions. And sorry that I took so long to actually do this :-P

---

### Post by aggrey69 on 2012-07-11
> **ed_masterplue said:**
> Hi again, as i promised i have a solution, it worked for me, I hope this can help you as well
in your console type
> lshw -C network
 you will see the network devices, including RT3060 that is the one of your card, check the driver it should say rt2800pci, then in your terminal run
> sudo gedit /etc/modprobe.d/blacklist.conf

you have to add this line
 blacklist rt2800pci

save it and reboot

then you will see the card is disable, because there is no driver for your card, 
the next thing i did was download the drivers 
[COLOR=Red][[COLOR=Red][SIZE=5]DRIVERS DWA-525[/SIZE][/COLOR]]("http://www.ralinktech.com/download.php?t=U0wyRnpjMlYwY3k4eU1ERXdMekEzTHpFMkwyUnZkMjVzYjJGa05qZ3lOVE14TnpnMU1DNWllakk5UFQweU1ERXdYekEzWHpFMlgxSlVNekEyTWw5TWFXNTFlRjlUVkVGZmRqSXVOQzR3TGpBdWRHRnlD")[/COLOR]
compile the drivers running (before compiling you have to read README_STA file)
> sudo make
> sudo make install

reboot again and you should have your DLink card running

that is what i did and worked for me, i could not find information about this issue, it's been a long week making it work, so i hope this helps you :P


got the following when I tried to make & make install..

make -C tools
make[1]: Entering directory `/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/tools'
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/tools/bin2h
cp -f os/linux/Makefile.6 /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/Makefile
make -C /lib/modules/3.2.0-23-generic-pae/build SUBDIRS=/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic-pae'
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/crypt_md5.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/crypt_aes.o
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/crypt_aes.c:1522:1: warning: the frame size of 1360 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/crypt_aes.c:1592:1: warning: the frame size of 1360 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/crypt_aes.c:2265:1: warning: the frame size of 1096 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/mlme.o
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/mlme.c:4222:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined [-Wsequence-point]
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/mlme.c:4589:1: warning: the frame size of 1588 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/cmm_wep.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/action.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/cmm_data.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/rtmp_init.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/cmm_aes.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/cmm_sync.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/eeprom.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/cmm_info.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/dfs.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/spectrum.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/rt_channel.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/cmm_profile.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/cmm_asic.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../sta/assoc.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../sta/auth.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../sta/sync.o
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../sta/sync.c:1073:1: warning: the frame size of 1260 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../sta/sync.c:766:1: warning: the frame size of 1264 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../sta/sync.c:1730:1: warning: the frame size of 1300 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../sta/sanity.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../sta/connect.o
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../sta/connect.c:312:1: warning: the frame size of 1612 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../sta/wpa.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/sta_ioctl.o
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwencode’:
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/sta_ioctl.c:1447:3: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’ [-Wparentheses]
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/sta_ioctl.c:605:1: warning: the frame size of 1288 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwmlme’:
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/sta_ioctl.c:1893:1: warning: the frame size of 1588 bytes is larger than 1024 bytes [-Wframe-larger-than=]
In file included from /usr/src/linux-headers-3.2.0-23-generic-pae/arch/x86/include/asm/uaccess.h:573:0,
                 from /usr/src/linux-headers-3.2.0-23-generic-pae/arch/x86/include/asm/sections.h:5,
                 from /usr/src/linux-headers-3.2.0-23-generic-pae/arch/x86/include/asm/hw_irq.h:26,
                 from include/linux/irq.h:357,
                 from /usr/src/linux-headers-3.2.0-23-generic-pae/arch/x86/include/asm/hardirq.h:5,
                 from include/linux/hardirq.h:7,
                 from include/linux/interrupt.h:12,
                 from /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/include/os/rt_linux.h:49,
                 from /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/include/rtmp_os.h:42,
                 from /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/include/rt_config.h:59,
                 from /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/sta_ioctl.c:40:
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/sta_ioctl.c:2976:28:
/usr/src/linux-headers-3.2.0-23-generic-pae/arch/x86/include/asm/uaccess_32.h:211:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct [enabled by default]
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/sta_ioctl.c:3473:28:
/usr/src/linux-headers-3.2.0-23-generic-pae/arch/x86/include/asm/uaccess_32.h:211:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct [enabled by default]
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/sta_ioctl.c:5756:1: warning: the frame size of 1340 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/sta_ioctl.c:5954:1: warning: the frame size of 1340 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlRF’:
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/sta_ioctl.c:6138:1: warning: the frame size of 2328 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.o
/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.c:1646:10: error: unknown field ‘ndo_set_multicast_list’ specified in initializer
make[2]: *** [/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic-pae'
make: *** [LINUX] Error 2
packstream@packstream-Veriton-M275:~/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2$ sudo make install
make -C /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux'
rm -rf /etc/Wireless/RT3060STA
#
#mkdir /etc/Wireless/RT3060STA
mkdir -p /etc/Wireless/RT3060STA
cp /home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/RT3060STA.dat /etc/Wireless/RT3060STA/.
install -d /lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/
install -m 644 -c rt3562sta.ko /lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/
install: cannot stat `rt3562sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/packstream/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux'
make: *** [install] Error 2

---

### Post by wildmanne39 on 2012-07-11
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

