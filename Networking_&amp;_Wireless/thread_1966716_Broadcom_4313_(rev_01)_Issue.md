---
title: "Broadcom 4313 (rev 01) Issue"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by ajukilibodin on 2012-04-27
> 04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)



Hello, the built-in, driver that was there with Jockey doesn't work. 

iwconfig

> lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.



Yet it is unable to find any wireless networks.

modprobe b43 didn't work either.

In 11.10 and 11.04, I did [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt) this but it no longer works as I am unable to compile it. Tried both upgraded and a fresh installation of 12.04

> ajukilibodin@Dream:~/Downloads$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic-pae'
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
  CC [M]  /home/ajukilibodin/Downloads/src/wl/sys/wl_linux.o
/home/ajukilibodin/Downloads/src/wl/sys/wl_linux.c:388:2: error: unknown field ‘ndo_set_multicast_list’ specified in initializer
/home/ajukilibodin/Downloads/src/wl/sys/wl_linux.c:388:2: warning: initialization from incompatible pointer type [enabled by default]
/home/ajukilibodin/Downloads/src/wl/sys/wl_linux.c:388:2: warning: (near initialization for ‘wl_netdev_ops.ndo_validate_addr’) [enabled by default]
make[2]: *** [/home/ajukilibodin/Downloads/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/home/ajukilibodin/Downloads] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic-pae'
make: *** [all] Error 2


I don't get why "make" doesn't work.

Wire works.

Thanks for your help in advance.

---

### Post by chili555 on 2012-04-27
> Hello, the built-in, driver that was there with Jockey doesn't work.We suspect this is a fault in 12.04. There is a bug report in place and it's being addressed. Let's see what we need to do to get you going. It depends on the exact details of your card.Please post:```
lspci -nn | grep 0280
```We can fix this pretty quickly.

---

### Post by ajukilibodin on 2012-04-27
lspci -nn | grep 0280

> 04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)


Thank you for helping!

---

### Post by chili555 on 2012-04-27
Please try:```
sudo apt-get install bcmwl-kernel-source
```If it reports that the package is already installed, then:```
sudo apt-get install --reinstall bcmwl-kernel-source
```Now load the driver:```
sudo modprobe wl
```Any improvement? Note and post back any errors or warnings.

---

### Post by ajukilibodin on 2012-04-27
ReInstalls perfect. Yet Ubuntu still fails to recognize any wireless networks. 

None of these drivers worked for me back in 11.10. I had to install the STA from the Broadcom website. It fails to "make" now. 

No warnings no errors.

---

### Post by chili555 on 2012-04-27
Please let us see:```
modinfo wl | grep 4727
```Thanks.

---

### Post by ajukilibodin on 2012-04-27
modinfo wl | grep 4727

> alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*


---

### Post by chili555 on 2012-04-27
Please do:```
sudo modprobe wl
sudo iwlist eth1 scan  <--it may be wlan0
rfkill list all
dmesg | grep wl
```

---

### Post by ajukilibodin on 2012-04-27
> 
ajukilibodin@Dream:~$ sudo modprobe wl
[sudo] password for ajukilibodin: 
ajukilibodin@Dream:~$ sudo iwlist eth1 scan
eth1      Interface doesn't support scanning.

ajukilibodin@Dream:~$ sudo iwlist wlan0 scan
wlan0     No scan results

ajukilibodin@Dream:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
ajukilibodin@Dream:~$ dmesg | grep wl
[    0.000000] DMI: Hewlett-Packard HP Pavilion g6 Notebook PC      /1670, BIOS F.32 07/28/2011
[   13.692159] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.061966] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.063035] ADDRCONF(NETDEV_UP): wlan0: link is not ready


There

---

### Post by chili555 on 2012-04-27
This just gets crazier by the second. No less than *three* drivers claim your device:```
chili@LAPTOP60:~$ modinfo bcma | grep 4727
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
chili@LAPTOP60:~$ modinfo brcmsmac | grep 4727
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
chili@LAPTOP60:~$ modinfo wl | grep 4727
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
```Are the other two loaded?```
lsmod | grep -e brc -e bcma
```If so, we need to blacklist them:```
sudo su
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
```Reboot and let us have your report.

---

### Post by 1204 on 2012-04-27
Does this help? It solved my wlan issues and I guess it's same package (my chip BCM4311)
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

---

### Post by chili555 on 2012-04-27
> I guess it's same package (my chip BCM4311)Since the title of this thread is Broadcom **4313**; well, no I *don't* think it is.

---

### Post by 1204 on 2012-04-27
> **chili555 said:**
> Since the title of this thread is Broadcom **4313**; well, no I *don't* think it is.Yeah but it is b43 so I guess 4313 and 4311 has same package. [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

" STA - BCM4311, BCM4312, BCM4313, BCM4321, BCM4322, BCM43224, BCM43225, **BCM43227, **BCM43228 "

---

### Post by ajukilibodin on 2012-04-27
> ajukilibodin@Dream:~$ lsmod | grep -e brc -e bcma
bcma                   25651  1 b43
brcmsmac              540875  0 
mac80211              436455  2 b43,brcmsmac
brcmutil               14675  1 brcmsmac
cfg80211              178679  3 b43,brcmsmac,mac80211
crc8                   12781  1 brcmsmac
cordic                 12487  1 brcmsmac


Well, looks like they are all loaded :D

After blacklist and restart;

> ajukilibodin@Dream:~$ lsmod | grep -e brc -e bcma
bcma                   25651  1 b43

Yet still nothing. Not even after modprobing.

Maybe trying to compile the Broadcom STA package would help?

---

### Post by chili555 on 2012-04-27
Notice that 4311 is listed in both STA and b43? You have to look at the pci.id, not just the model number. Then you have to look at current notes to know what works with what.> Yeah but it is [COLOR="Red"]b43[/COLOR] so I guess 4313 and 4311 has same package. [https://help.ubuntu.com/community/Wi...Driver/bcm43xx](https://help.ubuntu.com/community/Wi...Driver/bcm43xx)

" [COLOR="Red"]STA[/COLOR] - BCM4311, BCM4312, BCM4313, BCM4321, BCM4322, BCM43224, BCM43225, **BCM43227, **BCM43228 " You said b43 but quoted STA.

I know, it's tricky.

---

### Post by ajukilibodin on 2012-04-27
So, what to do now? :/

---

### Post by chili555 on 2012-04-27
> **ajukilibodin said:**
> So, what to do now? :/Please follow the procedure in post #10. Were the other drivers loaded? Did you blacklist?

---

### Post by ajukilibodin on 2012-04-27
Your eyes must have skipped my post #14 (: 


> **ajukilibodin said:**
> Well, looks like they are all loaded :D

After blacklist and restart;



Yet still nothing. Not even after modprobing.

Maybe trying to compile the Broadcom STA package would help?

---

### Post by chili555 on 2012-04-27
> After blacklist and restart;

Quote:
ajukilibodin@Dream:~$ lsmod | grep -e brc -e bcma
bcma 25651 1 b43 It looks like bcma didn"t get blacklisted effectively. Please check:```
sudo gedit /etc.modprobe.d/blacklist.conf
```There should be two lines at the end:```
blacklist bcma
blacklist brcmsmac
```If not, please correct. As well, we wonder how b43 got in there. Please add another line:```
blacklist b43
```Proofread, save and close gedit. Reboot and let us have your report.> Your eyes must have skipped my post #14Yes, indeed. I need to wipe a few layers of dirt off these old glasses! Sorry.

---

### Post by ajukilibodin on 2012-04-27
Blacklisted b43 and it worked, bcma was blacklisted already.

So now I get connection. But it's odd. 

This is my speedtest with wireless, 2m away from the router

[IMG]http://www.speedtest.net/result/1919043515.png[/IMG]

This is the speed test with wire

[IMG]http://www.speedtest.net/result/1919047962.png[/IMG]

I **should** have a 16 mbit download and 1 mbit upload speed. Wire is close enough yet wireless is doing horrible :/

---

### Post by chili555 on 2012-04-27
We're getting closer! Any clues here?```
sudo cat /var/log/syslog | grep wl
```

---

### Post by ajukilibodin on 2012-04-27
> Apr 27 16:24:52 Dream kernel: [    0.000000] DMI: Hewlett-Packard HP Pavilion g6 Notebook PC      /1670, BIOS F.32 07/28/2011
Apr 27 16:24:52 Dream kernel: [    9.530255] wl: module license 'MIXED/Proprietary' taints kernel.
Apr 27 16:24:55 Dream NetworkManager[880]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:04:00.0/net/wlan0, iface: wlan0)
Apr 27 16:24:55 Dream NetworkManager[880]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Apr 27 16:24:55 Dream NetworkManager[880]: <info> (wlan0): using nl80211 for WiFi device control
Apr 27 16:24:55 Dream NetworkManager[880]: <info> (wlan0): new 802.11 WiFi device (driver: 'brcmsmac' ifindex: 3)
Apr 27 16:24:55 Dream NetworkManager[880]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 27 16:24:55 Dream NetworkManager[880]: <info> (wlan0): now managed
Apr 27 16:24:55 Dream NetworkManager[880]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 27 16:24:55 Dream NetworkManager[880]: <info> (wlan0): bringing up device.
Apr 27 16:24:55 Dream NetworkManager[880]: <info> (wlan0): preparing device.
Apr 27 16:24:55 Dream NetworkManager[880]: <info> (wlan0): deactivating device (reason 'managed') [2]
Apr 27 16:24:55 Dream kernel: [   15.307181] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 27 16:24:55 Dream kernel: [   15.308136] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 27 16:24:56 Dream NetworkManager[880]: <info> (wlan0): supplicant interface state: starting -> ready
Apr 27 16:24:56 Dream NetworkManager[880]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Apr 27 16:24:56 Dream NetworkManager[880]: <info> (wlan0): supplicant interface state: ready -> inactive
Apr 27 16:47:54 Dream kernel: [    0.000000] DMI: Hewlett-Packard HP Pavilion g6 Notebook PC      /1670, BIOS F.32 07/28/2011
Apr 27 16:47:54 Dream kernel: [   13.692159] wl: module license 'MIXED/Proprietary' taints kernel.
Apr 27 16:47:54 Dream NetworkManager[790]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:04:00.0/net/wlan0, iface: wlan0)
Apr 27 16:47:54 Dream NetworkManager[790]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Apr 27 16:47:54 Dream NetworkManager[790]: <info> (wlan0): using nl80211 for WiFi device control
Apr 27 16:47:54 Dream NetworkManager[790]: <info> (wlan0): new 802.11 WiFi device (driver: 'brcmsmac' ifindex: 3)
Apr 27 16:47:54 Dream NetworkManager[790]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 27 16:47:54 Dream NetworkManager[790]: <info> (wlan0): now managed
Apr 27 16:47:54 Dream NetworkManager[790]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 27 16:47:54 Dream NetworkManager[790]: <info> (wlan0): bringing up device.
Apr 27 16:47:54 Dream NetworkManager[790]: <info> (wlan0): preparing device.
Apr 27 16:47:54 Dream NetworkManager[790]: <info> (wlan0): deactivating device (reason 'managed') [2]
Apr 27 16:47:54 Dream kernel: [   14.061966] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 27 16:47:54 Dream kernel: [   14.063035] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 27 16:47:54 Dream NetworkManager[790]: <info> (wlan0): supplicant interface state: starting -> ready
Apr 27 16:47:54 Dream NetworkManager[790]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Apr 27 16:47:54 Dream NetworkManager[790]: <info> (wlan0): supplicant interface state: ready -> inactive
Apr 27 16:51:48 Dream &#65279;AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'apport'), dbus.String(u'apport-gtk'), dbus.String(u'bcmwl-kernel-source'), dbus.String(u'firefox'), dbus.String(u'firefox-globalmenu'), dbus.String(u'firefox-gnome-support'), dbus.String(u'linux-libc-dev'), dbus.String(u'python-apport'), dbus.String(u'python-problem-report'), dbus.String(u'sessioninstaller')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))
Apr 27 16:51:48 Dream &#65279;AptDaemon.Worker: INFO: Committing packages: dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'apport'), dbus.String(u'apport-gtk'), dbus.String(u'bcmwl-kernel-source'), dbus.String(u'firefox'), dbus.String(u'firefox-globalmenu'), dbus.String(u'firefox-gnome-support'), dbus.String(u'linux-libc-dev'), dbus.String(u'python-apport'), dbus.String(u'python-problem-report'), dbus.String(u'sessioninstaller')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Apr 27 19:33:28 Dream kernel: [    0.000000] DMI: Hewlett-Packard HP Pavilion g6 Notebook PC      /1670, BIOS F.32 07/28/2011
Apr 27 19:33:28 Dream kernel: [   10.017111] wl: module license 'MIXED/Proprietary' taints kernel.
Apr 27 19:33:28 Dream kernel: [   10.027731] wl 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 27 19:33:28 Dream kernel: [   10.027747] wl 0000:04:00.0: setting latency timer to 64
Apr 27 19:33:32 Dream NetworkManager[884]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Apr 27 20:40:02 Dream kernel: [    0.000000] DMI: Hewlett-Packard HP Pavilion g6 Notebook PC      /1670, BIOS F.32 07/28/2011
Apr 27 20:40:02 Dream kernel: [   17.250411] wl: module license 'MIXED/Proprietary' taints kernel.
Apr 27 20:40:02 Dream kernel: [   17.330471] wl 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 27 20:40:02 Dream kernel: [   17.330491] wl 0000:04:00.0: setting latency timer to 64
Apr 27 20:40:02 Dream NetworkManager[739]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)


I should pay more attention, forgot to hit the Post Quick Reply button >.<

---

### Post by chili555 on 2012-04-27
Well, there are *no* clues. Is power management on or off?```
iwconfig eth1
```For example:> wlan0     IEEE 802.11abg  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:13:10:62:8D:xx[COLOR="Red"][/COLOR]   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          [COLOR="Red"]Power Management:off[/COLOR]
          Link Quality=53/70  Signal level=-57 dBm  
If yours is on, please try:```
sudo iwconfig eth1 power off
```Is your router set to WPA2 only or the tricky WPA and WPA2 mixed mode?

---

### Post by ajukilibodin on 2012-04-27
> **chili555 said:**
> Well, there are *no* clues. Is power management on or off?```
iwconfig eth1
```For example:If yours is on, please try:```
sudo iwconfig eth1 power off
```Is your router set to WPA2 only or the tricky WPA and WPA2 mixed mode?

> ajukilibodin@Dream:~$ iwconfig eth1
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:2  Signal level:184  Noise level:167
          Rx invalid nwid:0  invalid crypt:4  invalid misc:0

ajukilibodin@Dream:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:2  Signal level:185  Noise level:166
          Rx invalid nwid:0  invalid crypt:4  invalid misc:0

eth0      no wireless extensions.

ajukilibodin@Dream:~$ 


No info on power management. Router is WPA2.

Do you think maybe I should go with the standard Broadcom STA from their website and try to compile that seeing none of the ones in Ubuntu repos work? :/

---

### Post by chili555 on 2012-04-27
> Do you think maybe I should go with the standard Broadcom STA from their website and try to compile that seeing none of the ones in Ubuntu repos work? :/Sure; why not. Download the newest version, extract it and, before you compile, open src/wl/sys/wl_linux.c with a text editor such as gedit or nano. At line 388, change ```
.ndo_set_multicast_list = wl_set_multicast_list,
```...to read:```
.ndo_set_[COLOR="Red"]rx_mode[/COLOR] = wl_set_multicast_list,

```Proofread carefully, save and close the text editor. Compile as you started on page 1. After sudo make install, reboot.

---

### Post by ajukilibodin on 2012-04-27
Thank you, that worked. For the sake of learning; what exactly did I change and what did it do?

As a report; even with these drivers, my wireless performance is very poor. :/

---

### Post by chili555 on 2012-04-27
The change corrected a coding error in the driver. I Googled your error from page one and found the suggestion. I applied it and it compiled perfectly for me.

You might try WPA instead of WPA2 or try another channel in the router. I am getting low on ideas.

---

### Post by ajukilibodin on 2012-04-28
> **chili555 said:**
> The change corrected a coding error in the driver. I Googled your error from page one and found the suggestion. I applied it and it compiled perfectly for me.

You might try WPA instead of WPA2 or try another channel in the router. I am getting low on ideas.

It's not the router, speedtests from my phone and other computer are completely normal :/

---

### Post by chili555 on 2012-04-28
This is a long shot, but let's see if any of the drivers you blacklisted works better:```
sudo modprobe -r wl
sudo modprobe bcma
```Can you connect? Is it faster now? Or else:```
sudo modprobe -r bcma
sudo modprobe brcmsmac
```So does one work better than wl? We may need to adjust our blacklists.

---

### Post by ajukilibodin on 2012-04-28
That completely cut the wireless. :/

---

### Post by chili555 on 2012-04-28
So evidently wl is the best and only driver. I'm sorry, I have no more ideas. Let's clean up with a reboot.

---

### Post by ajukilibodin on 2012-04-28
At least I get connection. Thanks for trying (:

---

### Post by bou3lam on 2013-04-04
chili555 please help, i have the same card in an hp g6 , i cant blacklist b43 or bcma or ssb , at additional drivers wireless sta is enabled but not in use

---

### Post by bou3lam on 2013-04-05
removed eveything, rebooted, reinstalled bcmwl-kernel-source + 2 broadcom things, now  my bcm4313 is working very good and my lsmod show :

```


simo@Simo:~$ lsmod
Module                  Size  Used by
option                 30161  0 
cdc_ether              13536  0 
usbnet                 26212  1 cdc_ether
usb_wwan               20491  1 option
usbserial              47077  2 option,usb_wwan
usb_storage            49243  0 
michael_mic            12612  8 
lib80211_crypt_tkip    17390  0 
wl                   3074895  0 
lib80211               14381  2 lib80211_crypt_tkip,wl
snd_hrtimer            12744  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
arc4                   12529  4 
parport_pc             32866  0 
psmouse                97485  0 
ppdev                  17113  0 
rfcomm                 47604  12 
bnep                   18281  2 
snd_hda_intel          33719  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
rt2800usb              22773  0 
rt2800lib              58967  1 rt2800usb
crc_ccitt              12707  1 rt2800lib
rt2x00usb              20808  1 rt2800usb
rt2x00lib              55326  3 rt2800usb,rt2800lib,rt2x00usb
serio_raw              13211  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  3 snd_seq_midi,snd_seq_midi_event
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
btusb                  18332  2 
bluetooth             180153  23 rfcomm,bnep,btusb
snd_timer              29990  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  20 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                5198957  96 
mac_hid                13253  0 
soundcore              15091  1 snd
wmi                    19256  1 hp_wmi
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
rts_pstor             445241  0 
mac80211              506862  3 rt2800lib,rt2x00usb,rt2x00lib
i915                  477626  2 
drm_kms_helper         46978  1 i915
drm                   241971  3 i915,drm_kms_helper
cfg80211              205774  3 wl,rt2x00lib,mac80211
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47238  0 
hid                    99636  1 usbhid
r8169                  62154  0 




```

 the wireless sta from additional drivers is not activated, rt2800usb and the others are from my just-unplugged usb tp-link modem, now im afraid to reboot and b43, bcma and ssb will reload and conflict with wl :(

---

### Post by chili555 on 2013-04-05
>     now im afraid to reboot and b43, bcma and ssb will reload and conflict with wl When you install bcmwl-kernel-source, it is supposed to blacklist those modules, as we say in the southern USA, six ways from Sunday. It creates its own file, in fact, called /etc/modprobe.d/blacklist-bcm43.conf. Check its contents with:```
cat /etc/modprobe.d/blacklist-bcm43.conf
```You will see that the blacklists you need are right there. If, for some unexplainable reason, they are not, it's easy enough to recreate:```
gksudo gedit /etc/modprobe.d/blacklist-bcm43.conf
```Add these lines:```
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

```Proofread, save and close gedit and enjoy your wireless!

---

### Post by bou3lam on 2013-04-05
```


simo@Simo:~$ cat /etc/modprobe.d/blacklist-bcm43.conf
# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma
simo@Simo:~$ 




```
so if i reboot now nothing gonna change ? maybe we should check something please just in case :) ? because i did the same before maybe many times, when rebooted the b43 loaded from nowhere :)

---

### Post by chili555 on 2013-04-05
OK, let's make sure b43 isn't explicitly called in /etc/modules:```
cat /etc/modules
```

---

### Post by bou3lam on 2013-04-05
upss rebooted before you last msg, as before the wifi has gone, im connected now with usb tp-link here lsmod before and after the tp-link
```


Module                  Size  Used by
snd_hrtimer            12744  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
option                 30161  0 
cdc_ether              13536  0 
snd_hda_intel          33719  6 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
psmouse                97485  0 
serio_raw              13211  0 
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
usb_wwan               20491  1 option
parport_pc             32866  0 
usbnet                 26212  1 cdc_ether
ppdev                  17113  0 
usbserial              47077  2 option,usb_wwan
snd_seq_midi           13324  0 
rfcomm                 47604  12 
snd_rawmidi            30748  1 snd_seq_midi
bnep                   18281  2 
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72627  0 
btusb                  18332  2 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
bluetooth             180153  23 rfcomm,bnep,btusb
snd_seq                61929  3 snd_seq_midi,snd_seq_midi_event
wmi                    19256  1 hp_wmi
fglrx                5198957  81 
snd_timer              29990  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  477626  2 
wl                   3074895  0 
snd                    79041  23 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
lib80211               14381  1 wl
drm_kms_helper         46978  1 i915
drm                   241971  3 i915,drm_kms_helper
b43                   365819  0 
mac80211              506862  1 b43
rts_pstor             445241  0 
mei                    41616  0 
cfg80211              205774  3 wl,b43,mac80211
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
bcma                   26696  1 b43
ssb                    52752  1 b43
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49243  0 
usbhid                 47238  0 
hid                    99636  1 usbhid
r8169                  62154  0 




```


```


Module                  Size  Used by
arc4                   12529  2 
rt2800usb              22773  0 
rt2800lib              58967  1 rt2800usb
crc_ccitt              12707  1 rt2800lib
rt2x00usb              20808  1 rt2800usb
rt2x00lib              55326  3 rt2800usb,rt2800lib,rt2x00usb
snd_hrtimer            12744  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
option                 30161  0 
cdc_ether              13536  0 
snd_hda_intel          33719  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
psmouse                97485  0 
serio_raw              13211  0 
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
usb_wwan               20491  1 option
parport_pc             32866  0 
usbnet                 26212  1 cdc_ether
ppdev                  17113  0 
usbserial              47077  2 option,usb_wwan
snd_seq_midi           13324  0 
rfcomm                 47604  12 
snd_rawmidi            30748  1 snd_seq_midi
bnep                   18281  2 
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72627  0 
btusb                  18332  2 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
bluetooth             180153  23 rfcomm,bnep,btusb
snd_seq                61929  3 snd_seq_midi,snd_seq_midi_event
wmi                    19256  1 hp_wmi
fglrx                5198957  87 
snd_timer              29990  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  477626  2 
wl                   3074895  0 
snd                    79041  17 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
lib80211               14381  1 wl
drm_kms_helper         46978  1 i915
drm                   241971  3 i915,drm_kms_helper
b43                   365819  0 
mac80211              506862  4 rt2800lib,rt2x00usb,rt2x00lib,b43
rts_pstor             445241  0 
mei                    41616  0 
cfg80211              205774  4 rt2x00lib,wl,b43,mac80211
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
bcma                   26696  1 b43
ssb                    52752  1 b43
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49243  0 
usbhid                 47238  0 
hid                    99636  1 usbhid
r8169                  62154  0 



```

```


simo@Simo:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


lp
rtc
b43
wl
simo@Simo:~$ 



```

b43 is here :)

---

### Post by chili555 on 2013-04-05
Easy enough to fix:```
gksudo gedit /etc/modules
```Change the last lines to:```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


lp
rtc
wl
```In other words, remove b43. Proofread, save and close gedit. Remove the USB, reboot and give us your report.

I will be away for a while, so my reply may not be instant. They insist I stop for food and a nap once in a while!

---

### Post by bou3lam on 2013-04-05
that worked :) its working fine now :) super :) thanks a lot :) bon appetit :)

```


Module                  Size  Used by
option                 30161  0 
usb_wwan               20491  1 option
usbserial              47077  2 option,usb_wwan
cdc_ether              13536  0 
usbnet                 26212  1 cdc_ether
michael_mic            12612  8 
arc4                   12529  4 
snd_hrtimer            12744  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33719  3 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  12 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
bnep                   18281  2 
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  3 snd_seq_midi,snd_seq_midi_event
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
btusb                  18332  2 
v4l2_compat_ioctl32    17128  1 videodev
bluetooth             180153  23 rfcomm,bnep,btusb
snd_timer              29990  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19256  1 hp_wmi
fglrx                5198957  91 
psmouse                97485  0 
snd                    79041  17 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13211  0 
mac_hid                13253  0 
rts_pstor             445241  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  477626  2 
drm_kms_helper         46978  1 i915
lib80211_crypt_tkip    17390  0 
drm                   241971  3 i915,drm_kms_helper
mei                    41616  0 
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
wl                   3074895  0 
cfg80211              205774  1 wl
lib80211               14381  2 lib80211_crypt_tkip,wl
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49243  0 
usbhid                 47238  0 
hid                    99636  1 usbhid
r8169                  62154  0 




```

thanks a lot :)

---

