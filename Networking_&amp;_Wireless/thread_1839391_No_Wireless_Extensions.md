---
title: "No Wireless Extensions"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by Imalearnin on 2011-09-05
This is my first attempt to install Ubuntu and so far it seems to have been really smooth.  It is a lean install on a single hard drive with no Windows contamination.  I did a DoD wipe before using the HD. However, I can't seem to get my wireless working.  I think I may have found my problem but would like to know if there is a work-around for it.

I just discovered that my USB wireless device is not on the supported list  <https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsZonet#USB>.  According to this list the Zonet ZEW2501 is supported.  My ZEW2547 is not on the list.  

I am running 11.04 and I think it sees the hardware but the** LED light on it does not blink** indicating that it is recognized.  Below are some codes that I have run in an attempt to determine the problem although I do not know what all of it means exactly.

I think this tells me that it sees the hardware.

                                 jim@jim-OptiPlex-745:~$** lsusb **
 Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver 
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 [COLOR=#ff0000]**Bus 001 Device 003: ID 148f:5370 Ralink Technology, Corp. **[/COLOR] 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 



I think this tells me that the wireless driver is not being found.



                                  jim@jim-OptiPlex-745:~$** iwconfig **
 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 





Below doesn't display exactly like it did on my terminal screen but the data is correct.  I think this tells me what driver it is trying to use.

                                  

 jim@jim-OptiPlex-745:~$** lsmod** 
 Module                          Size          Used by 
 [COLOR=#ff0000]rt2870sta            410104  0[/COLOR]  
 [COLOR=#ff0000]crc_ccitt                      12595    1  rt2870sta [/COLOR]
 nls_iso8859_1                  12617     0  
 nls_cp437                      12751  0  
 vfat                           17335  0  
 fat                            55505  1 vfat 
 usb_storage                    43946  0  
 uas                            17676  0  
 binfmt_misc                    13213  1  
 snd_hda_codec_analog        75442  1  
 snd_hda_intel                  24140  2  
 snd_hda_codec                  90901  2 snd_hda_codec_analog,snd_hda_intel 
 snd_hwdep                      13274  1 snd_hda_codec 
 snd_pcm                        80244  2 snd_hda_intel,snd_hda_codec 
 snd_seq_midi                   13132  0  
 snd_rawmidi                    25269  1 snd_seq_midi 
 snd_seq_midi_event         14475  1 snd_seq_midi 
 snd_seq                        51291  2 snd_seq_midi,snd_seq_midi_event 
 snd_timer                      28659  2 snd_pcm,snd_seq 
 i915                         450944  3  
 snd_seq_device                14110  3 snd_seq_midi,snd_rawmidi,snd_seq 
 ppdev                          12849  0  
 snd                            55295  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 drm_kms_helper             40745  1 i915 
 dcdbas                         14054  0  
 soundcore                      12600  1 snd 
 snd_page_alloc                 14073  2 snd_hda_intel,snd_pcm 
 parport_pc                     32111  1  
 drm                           180037  4 i915,drm_kms_helper 
 psmouse                        73312  0  
 serio_raw                      12990  0  
 joydev                         17322  0  
 i2c_algo_bit                   13184  1 i915 
 video                          18951  1 i915 
 lp                             13349  0  
 parport                        36746  3 ppdev,parport_pc,lp 
 usbhid                         41704  0  
 hid                            77084  1 usbhid 
 tg3                           131476  0  
 floppy                         60032  0 



This is the information on the mod that I found.



                                  jim@jim-OptiPlex-745:~$ modinfo rt2870sta 
 filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2870/rt2870sta.ko 
 version:        2.1.0.0 
 license:        GPL 
 description:    RT2870/RT3070 Wireless Lan Linux Driver 
 author:         Paul Lin <paul_lin@ralinktech.com> 
 firmware:       rt3071.bin 
 firmware:       rt3070.bin 
 firmware:       rt2870.bin 
 srcversion:     93C0C58E1A016FE5BD4DC9F 
 alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v2019pED14d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v2001p3C0Ad*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v2001p3C09d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip* 
 alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip* 
 depends:        crc-ccitt 
 staging:        Y 
 vermagic:       2.6.38-8-generic SMP mod_unload modversions 686  
 [COLOR=#0000ff]**[COLOR=#ff0000]parm:           mac:rt28xx: wireless mac addr (charp)  [/COLOR]   <is this a concern?>**[/COLOR]


I would think that since my USB Wireless is still in the same family of that which is supported on the list, that it should be backwards compatable.  Not sure if I need to turn it back in and get another device or not. It says it is Linux compatable.


I apologize for the**[COLOR=Blue] INSANELY[/COLOR]** long post but I am trying to do my due dilagence in resolving things on my own. But it is time for me to call in the pros.  Any help will be appreciated.

---

### Post by praseodym on 2011-09-05
Hi,

the ID of your stick **148f:5370** is not listed in the modinfo of the driver. Try to add it manually:

```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
```
This is [COLOR="Red"]one[/COLOR] line, you better copy/paste it. After that reload the module:
```
sudo modprobe -rf rt2870sta
sudo modprobe -v rt2870sta
sudo depmod -a
```
and replugin the stick. Check:

```
iwconfig
rfkill list
sudo iwlist scan
dmesg | grep rt2
```

---

### Post by Imalearnin on 2011-09-05
Ok.  Here are the results:

	  jim@jim-OptiPlex-745:~$ echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf  
 [sudo] password for jim:  
 install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2870/new_id  
 

 jim@jim-OptiPlex-745:~$ sudo modprobe -rf rt2870sta  
 

 jim@jim-OptiPlex-745:~$ sudo modprobe -v rt2870sta  
 insmod /lib/modules/2.6.38-8-generic/kernel/lib/crc-ccitt.ko  
 install modprobe --ignore-install rt2870sta ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2870/new_id  
 insmod /lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2870/rt2870sta.ko 
 

 jim@jim-OptiPlex-745:~$ sudo depmod -a  
 

 [COLOR=#0000ff]**<<  At this point, I unplugged my wireless USB for about 15 seconds and plugged it back in  >>**[/COLOR]
 

 jim@jim-OptiPlex-745:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     Ralink STA  ESSID:""  Nickname:"RT2870STA"          [COLOR=#0000ff]**< This is progress >**[/COLOR]
           Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated    
           Bit Rate:1 Mb/s    
           RTS thr:off   Fragment thr:off  
           Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

 jim@jim-OptiPlex-745:~$ rfkill list  
 

 jim@jim-OptiPlex-745:~$ sudo iwlist scan  
 lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 wlan0     No scan results  
 

 jim@jim-OptiPlex-745:~$ dmesg | grep rt2  
 [35702.265199] [COLOR=#ff0000]**rt2**[/COLOR]870sta: module is from the staging directory, the quality is unknown, you have been warned.  
 [35702.277930] usbcore: registered new interface driver [COLOR=#ff0000]**rt2**[/COLOR]870  
 [59558.400045] usbcore: deregistering interface driver [COLOR=#ff0000]**rt2**[/COLOR]870  
 [59569.917315] [COLOR=#ff0000]**rt2**[/COLOR]870sta: module is from the staging directory, the quality is unknown, you have been warned.  
 [59569.931157] usbcore: registered new interface driver[COLOR=#ff0000]** rt2**[/COLOR]870  
 [59570.635426] <==== [COLOR=#ff0000]**rt2**[/COLOR]8xx_init, Status=0  
 [59571.544299] <==== [COLOR=#ff0000]**rt2**[/COLOR]8xx_init, Status=0  
 [59633.234391] <==== [COLOR=#ff0000]**rt2**[/COLOR]8xx_init, Status=0  
 [59634.173389] <====[COLOR=#ff0000]** rt2**[/COLOR]8xx_init, Status=0  
 jim@jim-OptiPlex-745:~$ 



At this point, I right-clicked on the network icon in the upper right corner and saw that I now have a new line "Enable Wireless" and it was checked.  I then clicked on "Create new wireless network".  In the window that opened, I filled in the Network Name, Wireless Security, and Password to match the settings on my working PC that is running 10.04.


I now have an entry in the Network Connection window in the Wireless tab.  I also edited it to match my other working PC and saved the settings.  With all of the changes being made, I did a restart on my PC.  



Still no LED light on my USB dongle.  AND, I re-ran the iwconfig and there was no difference from the one above.

---

### Post by praseodym on 2011-09-06
Ok, remove that file:

```
sudo rm /etc/modprobe.d/rt2870sta.conf
```
Do you have a wired connection? If so you can install the current Ralink driver (adapted for NetworkManager, etc.):
```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/2831641/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO.tar.gz
tar xvf angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO.tar.gz
cd angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO
sudo make
sudo make install
```
From [here]("http://forum.ubuntuusers.de/topic/c300ru-usb-rt2860-kein-ieee-802-11n/?highlight=rt5370#post-2831641")

Reboot and check:

```
lsmod
dmesg | egrep 'rt2|rt5'
iwconfig
sudo iwlist scan
rfkill list
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by Imalearnin on 2011-09-06
The first code to remove the file seems to have executed properly.

jim@jim-OptiPlex-745:~$ sudo rm /etc/modprobe.d/rt2870sta.conf
[sudo] password for jim: 

The next code had an error:

jim@jim-OptiPlex-745:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) build-essentiel dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**[COLOR=Red]E: Unable to locate package build-essentiel[/COLOR]**
jim@jim-OptiPlex-745:~$ 

It looked to me like there were six separate lines of code to execute in the second section so I only entered the top line and executed it.  The error above is what I got.  I did a search in Synaptic Package Manager for "build-essentiel" but it found nothing.  Is this something I need to download from somewhere else?

---

### Post by praseodym on 2011-09-06
The package name is **build-essenti[COLOR="Red"]a[/COLOR]l**

Sorry it was a typo from my side. I correct the line.

---

### Post by Imalearnin on 2011-09-06
Ok.  Below are the results of part 3 of your instructions above.  It looks like the Network Manager shows that networking and wireless are both enabled but I still have no LED light on my USB device.  I also noticed that iwconfig no longer shows wlan0 in the list.



jim@jim-OptiPlex-745:~$ lsmod  
 Module                  Size  Used by  
 binfmt_misc            13213  1  
 snd_hda_codec_analog    75442  1  
 snd_hda_intel          24113  2  
 snd_hda_codec          90901  2 snd_hda_codec_analog,snd_hda_intel  
 snd_hwdep              13274  1 snd_hda_codec  
 snd_pcm                80042  2 snd_hda_intel,snd_hda_codec  
 snd_seq_midi           13132  0  
 snd_rawmidi            25269  1 snd_seq_midi  
 i915                  451033  3  
 ppdev                  12849  0  
 snd_seq_midi_event     14475  1 snd_seq_midi  
 snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event  
 dcdbas                 14054  0  
 snd_timer              28659  2 snd_pcm,snd_seq  
 snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq  
 joydev                 17322  0  
 drm_kms_helper         40745  1 i915  
 drm                   184164  4 i915,drm_kms_helper  
 snd                    55295  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 psmouse                73312  0  
 parport_pc             32111  1  
 serio_raw              12990  0  
 i2c_algo_bit           13184  1 i915  
 video                  18951  1 i915  
 soundcore              12600  1 snd  
 snd_page_alloc         14073  2 snd_hda_intel,snd_pcm  
 [COLOR=#ff0000]**rt2870sta             410104  0 **[/COLOR] 
 [COLOR=#ff0000]**crc_ccitt              12595  1 rt2870sta **[/COLOR] 
 lp                     13349  0  
 parport                36746  3 ppdev,parport_pc,lp  
 usbhid                 41704  0  
 hid                    77084  1 usbhid  
 floppy                 60032  0  
 tg3                   131476  0  
 

 jim@jim-OptiPlex-745:~$ dmesg | [COLOR=#0000ff]**egrep 'rt2|rt5'   <<It looks like we are substituting driver **[/COLOR][COLOR=#ff0000]**rt5370sta**[/COLOR][COLOR=#0000ff]** for rt2870sta. is this correct?  >>**[/COLOR]
 [   14.325167] [COLOR=#ff0000]**rt2**[/COLOR]870sta: module is from the staging directory, the quality is unknown, you have been warned.  
 [   14.357872] usbcore: registered new interface driver [COLOR=#ff0000]**rt2**[/COLOR]870  
 [   14.921225] [COLOR=#ff0000]**rt5**[/COLOR]370sta: module license 'unspecified' taints kernel.  
 [   14.922713] [COLOR=#ff0000]**rt5**[/COLOR]370sta: Unknown symbol usb_alloc_urb (err 0)  
 [   14.922888] [COLOR=#ff0000]**rt5**[/COLOR]370sta: Unknown symbol usb_free_urb (err 0)  
 [   14.923186] [COLOR=#ff0000]**rt5**[/COLOR]370sta: Unknown symbol usb_alloc_coherent (err 0)  
 [   14.927521] [COLOR=#ff0000]**rt5**[/COLOR]370sta: Unknown symbol usb_register_driver (err 0)  
 [   14.935870] [COLOR=#ff0000]**rt5**[/COLOR]370sta: Unknown symbol usb_put_dev (err 0)  
 [   14.936069] [COLOR=#ff0000]**rt5**[/COLOR]370sta: Unknown symbol usb_get_dev (err 0)  
 [   14.936347] [COLOR=#ff0000]**rt5**[/COLOR]370sta: Unknown symbol usb_submit_urb (err 0)  
 [   14.936756] [COLOR=#ff0000]**rt5**[/COLOR]370sta: Unknown symbol usb_free_coherent (err 0)  
 [   14.937175] [COLOR=#ff0000]**rt5**[/COLOR]370sta: Unknown symbol usb_control_msg (err 0)  
 [   14.937675] [COLOR=#ff0000]**rt5**[/COLOR]370sta: Unknown symbol usb_deregister (err 0)  
 [   14.949168] [COLOR=#ff0000]**rt5**[/COLOR]370sta: Unknown symbol usb_kill_urb (err 0)  
 

 jim@jim-OptiPlex-745:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.     [COLOR=#0000ff]**<< Now it appears that wlan0 is no longer available.  Is there a registration of the new driver that needs to happen or is that what you did above? >>**[/COLOR]
 

 jim@jim-OptiPlex-745:~$ sudo iwlist scan  
 [sudo] password for jim:  
 lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 jim@jim-OptiPlex-745:~$ rfkill list  
 

 jim@jim-OptiPlex-745:~$ cat /var/lib/NetworkManager/NetworkManager.state  
 

 [main]  
 NetworkingEnabled=true  
 WirelessEnabled=true  
 WWANEnabled=true  
 jim@jim-OptiPlex-745:~$

---

