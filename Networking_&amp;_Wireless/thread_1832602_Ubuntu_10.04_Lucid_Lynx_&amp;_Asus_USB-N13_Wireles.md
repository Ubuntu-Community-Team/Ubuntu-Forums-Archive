---
title: "Ubuntu 10.04 Lucid Lynx &amp; Asus USB-N13 Wireless Adaptor Problems"
date: 2011-08-25
forum: Networking &amp; Wireless
---

### Post by garnr1 on 2011-08-25
Hi there,

I am experiencing difficulty at the moment with setting up my Asus N13 wireless adaptor on Ubuntu 10.04.3 I Have followed the instructions in post #2 of the following thread

[I][http://ubuntuforums.org/showthread.php?t=1499153](http://ubuntuforums.org/showthread.php?t=1499153)

[/I]     *Code:*
     *sudo gedit /etc/udev/rules.d/network_drivers.rules* 
*Add one long line:*     *Code:*
     *ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt2870sta"* 
*Notice we changed the driver to rt2870sta. Proofread carefully, save and close gedit. Now do:*     *Code:*
     *sudo gedit /etc/modprobe.d/network_drivers.conf* 
*Add one long line:*     *Code:*
     *install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id* 
*Proofread carefully, save and close gedit.*

This works and allows the adaptor to then be recognised. However everytime I try and connect it  keeps asking me for the WPA network key after 2 minutes or so of  entering it. It is definitely being entered correctly because it works perfectly when I boot into Windows 7. I have also tried a friends DWL-G122 adaptor and that works perfectly with Ubuntu 10.04. I just cant get my own adaptor (Asus USB N13) to work. Please  please can somebody help me? Any help would be hugely appreciated.

Kind Regards,

GarnR1

---

### Post by praseodym on 2011-08-25
Hi,

please show the following outputs:

```
lsmod
iwconfig
sudo iwlist scan
```

---

### Post by garnr1 on 2011-08-26
Thanks so much for your reply. Sure thing:

*Module                  Size  Used by  *
*rt2870sta             461843  1  *
*binfmt_misc             6587  1  *
*ppdev                   5259  0  *
*mt352                   5498  1  *
*snd_hda_codec_realtek   203376  0  *
*saa7134_dvb            22167  0  *
*saa7134_alsa           10380  1  *
*videobuf_dvb            5175  1 saa7134_dvb  *
*dvb_core               86206  1 videobuf_dvb  *
*snd_hda_intel          22069  2  *
*snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel  *
*snd_hwdep               5412  1 snd_hda_codec  *
*tuner_xc2028           19769  2  *
*snd_pcm_oss            35308  0  *
*snd_mixer_oss          13746  1 snd_pcm_oss  *
*snd_pcm                70694  4 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss  *
*tuner                  20412  1  *
*fbcon                  35102  71  *
*tileblit                1999  1 fbcon  *
*font                    7557  1 fbcon  *
*bitblit                 4707  1 fbcon  *
*softcursor              1189  1 bitblit  *
*snd_seq_dummy           1338  0  *
*vga16fb                11385  1  *
*vgastate                8961  1 vga16fb  *
*snd_seq_oss            26722  0  *
*snd_seq_midi            4557  0  *
*snd_rawmidi            19056  1 snd_seq_midi  *
*saa7134               143423  2 saa7134_dvb,saa7134_alsa  *
*ir_common              38875  1 saa7134  *
*snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi  *
*snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  *
*v4l2_common            15431  2 tuner,saa7134  *
*videodev               34361  3 tuner,saa7134,v4l2_common  *
*v4l1_compat            13251  1 videodev  *
*snd_timer              19098  2 snd_pcm,snd_seq  *
*snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  *
*videobuf_dma_sg        10782  3 saa7134_dvb,saa7134_alsa,saa7134  *
*nouveau               467048  0  *
*videobuf_core          16356  3 videobuf_dvb,saa7134,videobuf_dma_sg  *
*snd                    54244  19 snd_hda_codec_realtek,saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device *
*ttm                    50103  1 nouveau  *
*drm_kms_helper         29329  1 nouveau  *
*soundcore               6620  1 snd  *
*drm                   162377  3 nouveau,ttm,drm_kms_helper  *
*tveeprom               11102  1 saa7134  *
*xhci                   36936  0  *
*snd_page_alloc          7076  2 snd_hda_intel,snd_pcm  *
*agpgart                31724  2 ttm,drm  *
*i2c_algo_bit            5028  1 nouveau  *
*psmouse                63677  0  *
*lp                      7028  0  *
*serio_raw               3978  0  *
*shpchp                 28835  0  *
*parport                32635  2 ppdev,lp  *
*usbhid                 36110  0  *
*hid                    67288  1 usbhid  *
*ohci1394               26950  0  *
*floppy                 53016  0  *
*ieee1394               81181  1 ohci1394  *
*r8169                  34140  0  *
*mii                     4381  1 r8169  *
*ahci                   32360  3  *
*rhys@rhys-desktop:~$ iwconfig  *
*lo        no wireless extensions.  *
 
*eth0      no wireless extensions.  *
 
*wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"  *
*          Mode:Auto  Frequency=2.412 GHz  Access Point: 74:EA:3A:E0:D0:4A    *
*          Bit Rate=1 Mb/s    *
*          RTS thr:off   Fragment thr:off  *
*          Link Quality=10/100  Signal level:-57 dBm  Noise level:-87 dBm  *
*          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  *
*          Tx excessive retries:0  Invalid misc:0   Missed beacon:0  *
 
Kind Regards,

GarnR1

---

### Post by praseodym on 2011-08-26
```
sudo iwlist scan
```is missing.

You can update the firmware with the package **linux-firmware** and reboot.

You know this thread:

[http://ubuntuforums.org/showpost.php?p=9445731&postcount=58](http://ubuntuforums.org/showpost.php?p=9445731&postcount=58)

---

### Post by garnr1 on 2011-08-27
Thanks for your reply, I went through synaptic package manager and it shows the firmware as already update. I tried the "sudo iwlist scan" command again and got this:
[I]
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 74:EA:3A:E0:D0:4A
                    Protocol:802.11b/g/n
                    ESSID:"TP-LINK_E0D04A"
                    Mode:Managed
                    Channel:1
                    Quality:83/100  Signal level:-57 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 08:76:FF:7A:19:A4
                    Protocol:802.11b/g/n
                    ESSID:"Thomson7A19A4"
                    Mode:Managed
                    Channel:1
                    Quality:100/100  Signal level:-47 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:22:75:CB:1C:D9
                    Protocol:802.11b/g
                    ESSID:"TRAC-PC_Network"
                    Mode:Managed
                    Channel:6
                    Quality:31/100  Signal level:-77 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:36 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 04 - Address: 00:26:44:2A:65:FB
                    Protocol:802.11b/g
                    ESSID:"Shackleton"
                    Mode:Managed
                    Channel:9
                    Quality:73/100  Signal level:-61 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK[/I]


Any help would be great,

Kind Regards,

Rhys

---

### Post by garnr1 on 2011-08-29
Please can someone help me?

---

### Post by praseodym on 2011-08-29
Which of these networks you want to connect to?

Did you copy/paste the Key from Windows using Wordpad?

---

### Post by garnr1 on 2011-08-29
Im trying to connect to TP-LINK_E0D04A.

Regards,

GarnR1

---

### Post by garnr1 on 2011-08-29
I typed it letter for letter and have tried it several times. Cheers

---

### Post by praseodym on 2011-08-29
Try WPA2-AES encryption instead of mixed WPA/WPA2.

---

### Post by garnr1 on 2011-08-29
Great thanks for your help. Will definitely try that. Im a bit confused though because it works perfectly when I plug in my friends DWL-G122 adaptor and use the exact same network.

---

### Post by garnr1 on 2011-08-29
It works. Thank you so much!!!!!!!!

---

