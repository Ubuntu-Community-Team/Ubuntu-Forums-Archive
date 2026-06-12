---
title: "Wireless Issue HP pavillion dv6 - ubuntu 11.1"
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by dhoxha on 2012-04-20
Hi everyone,

I am a new Linux user, and I am having tremendous problems with wireless. I have a dual boot on my computer, whenever I restart it and then log on to my Linux, wireless won't work. 

I have managed to fix it a couple of times using different threads on this forum, but whenever I restart it, it does not work again. For a while now I've been trying to find a solution to this problem and it is bugging the hell out of me.

My network adapter driver is broadcom.

Any help will be greatly appreciated.

Thanks!

---

### Post by praseodym on 2012-04-20
Hi,

please show:

```
lspci -nnk | grep -iA2 net
iwconfig
lsmod
rfkill list
```

---

### Post by bkratz on 2012-04-20
> **dhoxha said:**
> Hi everyone,

I am a new Linux user, and I am having tremendous problems with wireless. I have a dual boot on my computer, whenever I restart it and then log on to my Linux, wireless won't work. 

I have managed to fix it a couple of times using different threads on this forum, but whenever I restart it, it does not work again. For a while now I've been trying to find a solution to this problem and it is bugging the hell out of me.

My network adapter driver is broadcom.

Any help will be greatly appreciated.

Thanks!


You might want to drop to the terminal ( cntrl-alt-t) and copy paste the results found from the following commands so that someone knowledgeable about your card can help. 

```
uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list

```use the <> and paste the results between to make it readable.

---

### Post by dhoxha on 2012-04-20
> **praseodym said:**
> Hi,

please show:

```
lspci -nnk | grep -iA2 net
iwconfig
lsmod
rfkill list
```


Executed the commands you asked.

lspci - nnk | grep -iA2 net results:

```

02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1507]
    Kernel driver in use: b43-pci-bridge
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:3627]
    Kernel driver in use: r8169

```iwconfig results:
```
 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```rfkill list results:

```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```I hope this helps, thanks!

---

### Post by praseodym on 2012-04-21
Firmware is missing, see here:

[http://ubuntuforums.org/showpost.php?p=11861126&postcount=9](http://ubuntuforums.org/showpost.php?p=11861126&postcount=9)

---

### Post by praseodym on 2012-04-21
Double posting

---

### Post by praseodym on 2012-04-21
Triple posting

---

### Post by dhoxha on 2012-04-21
> **praseodym said:**
> Firmware is missing, see here:

[http://ubuntuforums.org/showpost.php?p=11861126&postcount=9](http://ubuntuforums.org/showpost.php?p=11861126&postcount=9)

Can you explain what I am supposed to do with that? Cause I downloaded it, and tried to run the commands afterwards but I can't. 

Please explain?!

---

### Post by wildmanne39 on 2012-04-21
Hi, please post the commands you ran.

Did you download the firmware with the first command?
Thanks

---

### Post by dhoxha on 2012-04-21
> **wildmanne39 said:**
> Hi, please post the commands you ran.

Did you download the firmware with the first command?
Thanks

No that was not possible, I'm getting this error:

```
 
$ wget http://media.cdn.ubuntu-de.org/forum...irmware.tar.gz
--2012-04-21 13:31:37--  http://media.cdn.ubuntu-de.org/forum...irmware.tar.gz
Resolving media.cdn.ubuntu-de.org... 213.95.41.13
Connecting to media.cdn.ubuntu-de.org|213.95.41.13|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-04-21 13:31:38 ERROR 404: Not Found.

```

Then, I followed the link and downloaded it from there, but when I tried to copy the files to the /lib/firmware directory, I couldn't since it only has read permissions.

---

### Post by wildmanne39 on 2012-04-21
Hi, is your wired connection not working either?
Thanks

---

### Post by dhoxha on 2012-04-21
> **wildmanne39 said:**
> Hi, is your wired connection not working either?
Thanks

Yes it is, I'm using Ethernet right now.

---

### Post by wildmanne39 on 2012-04-21
When I clicked on the first line of the commands it opened a file to download and that is what it should have done for you then you can run those commands, you may want to try it again and if it does not work we can do it another way.
Thanks

---

### Post by dhoxha on 2012-04-21
> **wildmanne39 said:**
> When I clicked on the first line of the commands it opened a file to download and that is what it should have done for you then you can run those commands, you may want to try it again and if it does not work we can do it another way.
Thanks

I did click on the first file, and I downloaded the file. This is what happened when I ran the second line of the commands

```
tar: 2480236-Broadcom_Firmware.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

```

---

### Post by wildmanne39 on 2012-04-21
Hi, lets just do this:

Download the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

```
Zip file in next post.
Thanks

---

### Post by wildmanne39 on 2012-04-21
Here it is.

---

### Post by dhoxha on 2012-04-21
> **wildmanne39 said:**
> Hi, lets just do this:

Download the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

```Zip file in next post.
Thanks

Executed everything you said.

Zip file in next post? 
Did you mean, I should do the same thing for the other file that was in the tar.gz ?!

---

### Post by wildmanne39 on 2012-04-21
Hi, I forgot to include it in the post so I put it in the next post just look below my previous post.
Thanks

---

### Post by dhoxha on 2012-04-21
> **wildmanne39 said:**
> Hi, I forgot to include it in the post so I put it in the next post just look below my previous post.
Thanks

Executed everything, I'm on board. Any suggestions what to do next ?

---

### Post by wildmanne39 on 2012-04-21
Hi, you downloaded the driver then ran the commands I gave you one at a time?

Did you get any errors? it should have come on.

Please post the output of:
```
nm-tool
sudo iwlist scan
lsmod
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by dhoxha on 2012-04-21
```
nm-tool

NetworkManager Tool

State: unknown


** (process:4217): WARNING **: error: could not connect to NetworkManager

```

```
 sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth2      Scan completed :
          Cell 01 - Address: 00:0B:86:9E:C6:10
                    ESSID:"tlu-facstaff"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:3/5  Signal level:-69 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:0B:86:9E:C6:11
                    ESSID:"tlu-wgn"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:3/5  Signal level:-69 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:0B:86:9E:C6:13
                    ESSID:"tlu-stud"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:3/5  Signal level:-69 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s


```

```
lsmod
Module                  Size  Used by
b43                   341198  0 
ssb                    52752  1 b43
snd_seq_dummy          12798  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
psmouse                73882  0 
serio_raw              13166  0 
snd_hda_intel          33390  6 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
lib80211_crypt_tkip    17390  0 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
rc_rc6_mce             12502  0 
ir_lirc_codec          12898  0 
lirc_dev               19204  1 ir_lirc_codec
ene_ir                 22796  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ir_sony_decoder        12549  0 
ir_jvc_decoder         12546  0 
snd_seq                61896  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
ir_rc6_decoder         12546  0 
ir_rc5_decoder         12546  0 
ir_nec_decoder         12546  0 
rc_core                26963  9 rc_rc6_mce,ir_lirc_codec,ene_ir,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
wl                   2568210  0 
snd                    68266  21 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  571251  3 
lib80211               14991  2 lib80211_crypt_tkip,wl
wmi                    19256  1 hp_wmi
mac80211              462046  1 b43
hp_accel               21880  0 
lis3lv02d              19888  1 hp_accel
input_polldev          13896  1 lis3lv02d
drm_kms_helper         42558  1 i915
cfg80211              199630  2 b43,mac80211
drm                   236290  4 i915,drm_kms_helper
soundcore              12680  1 snd
i2c_algo_bit           13423  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
ums_realtek            13272  0 
usb_storage            57901  1 ums_realtek
hid                    95463  1 usbhid
uas                    18027  0 
ahci                   26002  5 
libahci                26861  1 ahci
r8169                  52788  0 

```

```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
Apr 21 13:14:04 Mr avahi-daemon[873]: Withdrawing workstation service for wlan0.
Apr 21 13:14:04 Mr kernel: [ 1566.764513] b43-pci-bridge 0000:02:00.0: PCI INT A disabled
Apr 21 13:18:08 Mr kernel: [    0.000000]  [<ffffffff8105e8ff>] warn_slowpath_common+0x7f/0xc0
Apr 21 13:18:08 Mr kernel: [    0.000000]  [<ffffffff8105e99f>] warn_slowpath_fmt_taint+0x3f/0x50

```

---

### Post by wildmanne39 on 2012-04-21
Hi, we need to get rid of another driver,  please do:
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot
Thanks

---

### Post by dhoxha on 2012-04-21
> **wildmanne39 said:**
> Hi, we need to get rid of another driver,  please do:
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf
```Then reboot
Thanks


Appreciate it bro. Can you quickly explain to me what we did, and what the problem was. I'm new to linux, and I'm trying to learn how to do this myself.

Thanks again!

---

### Post by wildmanne39 on 2012-04-21
Hi, the last thing we did was to stop a second driver from loading that was conflicting with the b43 driver, please use thread tools at the top of the page to mark the thread solved.
Thanks

---

