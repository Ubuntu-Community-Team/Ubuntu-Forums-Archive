---
title: "Broadcom 43224 drivers"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by Baga255 on 2010-10-10
Hi,

after days and countless read threads I can't seem to find any way to get my  wireless card working in Ubuntu. I got the Broadcom STA drivers installed with Ubuntu but they dont work for me, I can scan for networks but can't connect to any of them (to unsecured either).
Broadcom announced their new open  source drivers are avaliable which support my Broadcom chipset  (Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)).
Tried a lot of ways to get it to work, but eventually I quit beacuse I  read that the driver support will be added in Maverick. I currently have  Maverick installed but the problem persists. I believe that the driver I  need is called **brcm80211**, but still I havent found a way to get it to work in Ubuntu.
I read it's possible to get them to work by backporting, but I dont think im ready to try that beacuse I'm still new to linux.
 
I'm using HP min 5101 netbook, with Ubuntu 10.10 (2.6.35-22-generic i686) installed.
lspci -nn report:

```
Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
```iwconfig report:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:167
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```lsmod report:

```
Module                  Size  Used by
binfmt_misc             6599  1 
rfcomm                 33811  4 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_analog    59649  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
lib80211_crypt_tkip     7736  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
i915                  290938  3 
joydev                  8735  0 
hp_accel               12532  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         30200  1 i915
drm                   168054  4 i915,drm_kms_helper
i2c_algo_bit            5168  1 i915
intel_agp              26360  2 i915
uvcvideo               55847  0 
lis3lv02d               8524  1 hp_accel
btusb                  10969  2 
snd                    49006  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   1959533  0 
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
video                  18712  1 i915
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
psmouse                59033  0 
input_polldev           3491  1 lis3lv02d
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
lib80211                5058  2 lib80211_crypt_tkip,wl
serio_raw               4022  0 
led_class               2633  1 hp_accel
hp_wmi                  5191  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
ahci                   19013  0 
libahci                21667  3 ahci
sky2                   45127  0 

```iwlist scan report:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

```If anyone has encountered this problem or knows a way to solve it, help would be appericiated :smile:

---

### Post by Baga255 on 2010-10-10
bump

---

### Post by chili555 on 2010-10-10
I believe the module *wl* is correct for your device:> $ modinfo wl | grep 4353
alias:          pci:v0000[COLOR="Red"]14E4[/COLOR]d0000[COLOR="Red"]4353[/COLOR]sv*sd*bc*sc*i*Indeed, *wl* is loaded:> Module Size Used by
--- snip ---
wl 1959533 0
--- snip ---
lib80211 5058 2 lib80211_crypt_tkip,wl
--- snip ---Let's see if there are any kernel messages that will help us understand why it's not working. Please post:```
rfkill list all
dmesg | grep -e wl -e eth
```Thanks.

---

### Post by Baga255 on 2010-10-10
Thanks for the reply :)

rfkill list all report:

 ```
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```dmesg | grep -e wl -e eth report:

```
[    0.782657] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.C2E8] (Node f7026108), AE_AML_PACKAGE_LIMIT
[    0.782724] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.C2E7] (Node f70260f0), AE_AML_PACKAGE_LIMIT
[    0.782789] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.TZ2_._TMP] (Node f70267c8), AE_AML_PACKAGE_LIMIT
[    1.705245] sky2 0000:20:00.0: eth0: addr 18:a9:05:dc:8f:e6
[    5.922603] wl: module license 'MIXED/Proprietary' taints kernel.
[    6.010392] wl 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.010411] wl 0000:08:00.0: setting latency timer to 64
[    7.039408] eth1: Broadcom BCM4353 802.11 Hybrid Wireless Controller 5.60.48.36 
[   12.648949] sky2 0000:20:00.0: eth0: enabling interface
[   12.649907] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.347551] sky2 0000:20:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
[   14.347991] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.809052] eth1: no IPv6 routers present
[   24.504052] eth0: no IPv6 routers present

```

---

### Post by gale401 on 2010-10-10
Hi
etc/modprobe.d broadcom sta.conf  is set to blacklist b43  with the message   wl module from Broadcom conflicts with ssb    and also states We must blacklist the following modules  ( that includes b43 )

This is why when you try to install  additional drivers the GUI program at System it momentarily ( if you look quickly ) tries to get the correct info - but then etc/modprobe advices stop b43 STA wireless drivers installing.

So there is obviously work being done to solve this broadcom driver issue, I just wish it would happen very soon. 

Regards /   Chris :)

---

### Post by gale401 on 2010-10-10
There may be answer at the Mint Debian edition forums - that possibly could assist Ubuntu including 10.10 users     here:             [http://community.linuxmint.com/tutorial/view/218](http://community.linuxmint.com/tutorial/view/218)

Can someone see if these suggestions would work. :)

Regards /  Chris

---

### Post by Baga255 on 2010-10-10
Hi,
well I tried every possible guide to broadcom drivers and reinstalled the system a lot after every failed solution.
I blacklisted the b43 driver beacuse I think they arent the drivers I need (not for this chipset). Ubuntu preinstalls these drivers [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) and they should work for this chipset but the more I googled the more i was convinced i need the brcm80211 drivers, which arent implemented yet (should be as of kernel 2.6.35.7). So I'm trying to find a way to import it into this kernel (2.6.35-22). But I'm inexperienced in that field so if there's any way to accomplish that, any help is welcome :)

I'll check the Mint Debian guide and see if that works,

thanks for the reply :)

Regards

---

### Post by Baga255 on 2010-10-10
Tried the guide from the Mint Debian forums but to no avail.
Still the same problem, detects the networks, tries to connect (to and unsecured network) for about half a minute, disconnects.
Any other suggestions?

---

### Post by chili555 on 2010-10-10
> sky2 0000:20:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control bothIs your wired ethernet connected? Network Manager doesn't like that at all. [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themCan you please detach the ethernet cable, reboot and run the tests as above?

---

### Post by Ayuthia on 2010-10-10
If you are looking for the new drivers from Broadcom, you might try the [OpenSUSE link]("http://forums.opensuse.org/english/get-help-here/hardware/447485-bcm43224-bcm43225-bcm4313-installation-guide.html").  The kernel module that you need is the brcm80211.ko module and it looks like it might need some firmware to make it run also.

EDIT: You will most likely need to blacklist the b43 and wl modules too.

---

### Post by chargersfan420 on 2010-10-10
I've got the same card, and a similar problem.  The card works, but very poorly.

The OpenSUSE link was very helpful - I was able to compile the brcm80211 driver, but when I try to insmod it, I get this:
 
```
$ sudo insmod /lib/modules/`uname -r`/brcm80211.ko
insmod: error inserting '/lib/modules/2.6.35-22-generic/brcm80211.ko': -1 Unknown symbol in module
```

Also taking a look at dmesg after trying the insmod, I see this:

```
[36161.720555] brcm80211: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe (err 0)
[36161.721057] brcm80211: Unknown symbol ieee80211_free_hw (err 0)
[36161.721260] brcm80211: Unknown symbol ieee80211_alloc_hw (err 0)
[36161.721380] brcm80211: Unknown symbol regulatory_hint (err 0)
[36161.721511] brcm80211: Unknown symbol ieee80211_register_hw (err 0)
[36161.721745] brcm80211: Unknown symbol ieee80211_tx_status_irqsafe (err 0)
[36161.721956] brcm80211: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe (err 0)
[36161.722371] brcm80211: Unknown symbol ieee80211_wake_queues (err 0)
[36161.722654] brcm80211: Unknown symbol ieee80211_stop_queues (err 0)
[36161.722853] brcm80211: Unknown symbol ieee80211_unregister_hw (err 0)
[36161.723275] brcm80211: Unknown symbol ieee80211_rx_irqsafe (err 0)
```

Anyone know how to get around this problem?

---

### Post by Baga255 on 2010-10-11
Reports without the wired connection active:

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```lsmod:
```
Module                  Size  Used by
usbhid                 36882  0 
hid                    67742  1 usbhid
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_analog    59649  1 
rfcomm                 33811  4 
binfmt_misc             6599  1 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_analog,snd_hda_intel
i915                  290938  3 
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
drm_kms_helper         30200  1 i915
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
joydev                  8735  0 
lib80211_crypt_tkip     7736  0 
hp_wmi                  5191  0 
drm                   168054  4 i915,drm_kms_helper
uvcvideo               55847  0 
snd_timer              19067  2 snd_pcm,snd_seq
wl                   1959533  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  10969  2 
i2c_algo_bit            5168  1 i915
hp_accel               12532  0 
intel_agp              26360  2 i915
videodev               43098  1 uvcvideo
lis3lv02d               8524  1 hp_accel
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
psmouse                59033  0 
video                  18712  1 i915
input_polldev           3491  1 lis3lv02d
snd                    49006  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4022  0 
v4l1_compat            13359  2 uvcvideo,videodev
led_class               2633  1 hp_accel
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 drm,intel_agp
lib80211                5058  2 lib80211_crypt_tkip,wl
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19013  0 
libahci                21667  3 ahci
sky2                   45127  0 
```rfkill list all:
```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```dmesg | grep -e wl -e eth:
```
[    0.778430] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.C2E8] (Node f7026108), AE_AML_PACKAGE_LIMIT
[    0.778498] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.C2E7] (Node f70260f0), AE_AML_PACKAGE_LIMIT
[    0.778564] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.TZ2_._TMP] (Node f70267c8), AE_AML_PACKAGE_LIMIT
[    1.618146] sky2 0000:20:00.0: eth0: addr 18:a9:05:dc:8f:e6
[   11.165422] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.697892] wl 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.697909] wl 0000:08:00.0: setting latency timer to 64
[   11.942614] eth1: Broadcom BCM4353 802.11 Hybrid Wireless Controller 5.60.48.36 
[   12.896215] sky2 0000:20:00.0: eth0: enabling interface
[   12.896878] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.897040] eth1: no IPv6 routers present
```

Tried the OpenSUSE way couple of times before but none of them succeded. I will try again later and see if I can figure it out.

---

### Post by Ayuthia on 2010-10-11
> **chargersfan420 said:**
> I've got the same card, and a similar problem.  The card works, but very poorly.

The OpenSUSE link was very helpful - I was able to compile the brcm80211 driver, but when I try to insmod it, I get this:
 
```
$ sudo insmod /lib/modules/`uname -r`/brcm80211.ko
insmod: error inserting '/lib/modules/2.6.35-22-generic/brcm80211.ko': -1 Unknown symbol in module
```

Also taking a look at dmesg after trying the insmod, I see this:

```
[36161.720555] brcm80211: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe (err 0)
[36161.721057] brcm80211: Unknown symbol ieee80211_free_hw (err 0)
[36161.721260] brcm80211: Unknown symbol ieee80211_alloc_hw (err 0)
[36161.721380] brcm80211: Unknown symbol regulatory_hint (err 0)
[36161.721511] brcm80211: Unknown symbol ieee80211_register_hw (err 0)
[36161.721745] brcm80211: Unknown symbol ieee80211_tx_status_irqsafe (err 0)
[36161.721956] brcm80211: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe (err 0)
[36161.722371] brcm80211: Unknown symbol ieee80211_wake_queues (err 0)
[36161.722654] brcm80211: Unknown symbol ieee80211_stop_queues (err 0)
[36161.722853] brcm80211: Unknown symbol ieee80211_unregister_hw (err 0)
[36161.723275] brcm80211: Unknown symbol ieee80211_rx_irqsafe (err 0)
```

Anyone know how to get around this problem?

It looks like the ieee80211 module needs to be compiled also.  I am trying to see if I can find the correct version.

---

### Post by Ayuthia on 2010-10-11
> **chargersfan420 said:**
> I've got the same card, and a similar problem.  The card works, but very poorly.

The OpenSUSE link was very helpful - I was able to compile the brcm80211 driver, but when I try to insmod it, I get this:
 
```
$ sudo insmod /lib/modules/`uname -r`/brcm80211.ko
insmod: error inserting '/lib/modules/2.6.35-22-generic/brcm80211.ko': -1 Unknown symbol in module
```

Also taking a look at dmesg after trying the insmod, I see this:

```
[36161.720555] brcm80211: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe (err 0)
[36161.721057] brcm80211: Unknown symbol ieee80211_free_hw (err 0)
[36161.721260] brcm80211: Unknown symbol ieee80211_alloc_hw (err 0)
[36161.721380] brcm80211: Unknown symbol regulatory_hint (err 0)
[36161.721511] brcm80211: Unknown symbol ieee80211_register_hw (err 0)
[36161.721745] brcm80211: Unknown symbol ieee80211_tx_status_irqsafe (err 0)
[36161.721956] brcm80211: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe (err 0)
[36161.722371] brcm80211: Unknown symbol ieee80211_wake_queues (err 0)
[36161.722654] brcm80211: Unknown symbol ieee80211_stop_queues (err 0)
[36161.722853] brcm80211: Unknown symbol ieee80211_unregister_hw (err 0)
[36161.723275] brcm80211: Unknown symbol ieee80211_rx_irqsafe (err 0)
```

Anyone know how to get around this problem?

Please try the following:
```

sudo modprobe mac80211
sudo insmod brcm80211.ko

```
It looks like the only thing that was missing was the loading of the mac80211 driver.

I don't have this Broadcom card, but I was able to load the module successfully after I loaded the mac80211 driver.  I received the same message as you before I loaded it.

---

### Post by Baga255 on 2010-10-11
> **Ayuthia said:**
> Please try the following:
```

sudo modprobe mac80211
sudo insmod brcm80211.ko

```It looks like the only thing that was missing was the loading of the mac80211 driver.

I don't have this Broadcom card, but I was able to load the module successfully after I loaded the mac80211 driver.  I received the same message as you before I loaded it.

Thanks :)

I followed the OpenSUSE way again and got the same error as chargersfan420 and I entered the commands you gave and it seems that worked.
Still the wl drivers load and nothing changes. How do I enable the brcm80211 drivers instead of wl?

---

### Post by Ayuthia on 2010-10-11
> **Baga255 said:**
> Thanks :)

I followed the OpenSUSE way again and got the same error as chargersfan420 and I entered the commands you gave and it seems that worked.
Still the wl drivers load and nothing changes. How do I enable the brcm80211 drivers instead of wl?

Before we start blacklisting drivers, lets try the following:
```

sudo modprobe -r wl mac80211 brcm80211
sudo modprobe mac80211
sudo insmod brcm80211.ko

```
The first command should try and remove the currently loaded modules and then we can try loading just the ones that we need.  Hopefully that will get you up and running.

---

### Post by Baga255 on 2010-10-11
> **Ayuthia said:**
> Before we start blacklisting drivers, lets try the following:
```

sudo modprobe -r wl mac80211 brcm80211
sudo modprobe mac80211
sudo insmod brcm80211.ko

```The first command should try and remove the currently loaded modules and then we can try loading just the ones that we need.  Hopefully that will get you up and running.

Entered the commands and the chipset now uses the "brcm80211 - [phy0]" drivers. wl still loads after reboot. Blacklisting it would keep it from loading? Should I blacklist any other?

---

### Post by chargersfan420 on 2010-10-11
Yes, blacklisting should keep it from loading on startup.  Ayuthia's idea of "not blacklisting anything yet" was to check to see if the new driver helps.  After running the commands he listed, and before rebooting, can you use wireless effectively?

I did something stupid on an unrelated note and had to reinstall.  I'm cloning the git repo right now and should be caught up shortly.

---

### Post by Ayuthia on 2010-10-11
> **Baga255 said:**
> Entered the commands and the chipset now uses the "brcm80211 - [phy0]" drivers. wl still loads after reboot. Blacklisting it would keep it from loading? Should I blacklist any other?

You should only have to blacklist this one as far as I know.  Please let us know if you do not know how to do this.

---

### Post by Baga255 on 2010-10-11
I blacklisted wl by adding "blacklist wl" to the /etc/modprobe.d/blacklist.conf file and everything seems to work now :)
brcm80211 drivers load on boot and I can use wireless and connect normally.

Thank you very much for your help, Ayuthia :) Regards

---

### Post by Ayuthia on 2010-10-11
> **Baga255 said:**
> I blacklisted wl by adding "blacklist wl" to the /etc/modprobe.d/blacklist.conf file and everything seems to work now :)
brcm80211 drivers load on boot and I can use wireless and connect normally.

Thank you very much for your help, Ayuthia :) Regards

That is great to hear!  Thanks for letting us know that it works!

---

### Post by chargersfan420 on 2010-10-12
Apparently it gets even easier.  I went into "System - Administration - Additional Drivers", and deactivated the "Broadcom STA wireless driver".  After rebooting, the system automatically started using the brcm80211 driver, and the menu option now shows it is using the "Broadcom 802.11n wireless LAN driver."

So far performance is working nicely, but the page the git repository is posted on says to expect some instablility... I'll report any issues if I find them.

Thank you very much for the help Ayuthia!

---

### Post by Ayuthia on 2010-10-12
> **chargersfan420 said:**
> Apparently it gets even easier.  I went into "System - Administration - Additional Drivers", and deactivated the "Broadcom STA wireless driver".  After rebooting, the system automatically started using the brcm80211 driver, and the menu option now shows it is using the "Broadcom 802.11n wireless LAN driver."

So far performance is working nicely, but the page the git repository is posted on says to expect some instablility... I'll report any issues if I find them.

Thank you very much for the help Ayuthia!

Thanks for letting us know!  It is nice to see that the Additional Drivers application is now improved enough to prevent the loading of the driver.  That is one less command that we will need to use in the Terminal!

---

### Post by goinglinux on 2010-10-12
My HP Pavilion dm4 notebook has the bcm4313 and worked with the proprietary driver provided with Ubuntu 10.04 but did not work with the corresponding driver provided with Ubuntu 10.10. The solution that worked for me was to install "broadcom-sta-common" and its dependencies using Synaptic. After enabling the proprietary driver (System > Administration > Additional Drivers) and rebooting, wireless works. 

Out-of-the-box, Ubuntu 10.10 apparently supports only BCM4311-, BCM4312-, BCM4321-, and
BCM4322-based hardware. Installing the broadcom-sta-common package includes support for all of these network cards and adds support for BCM4313-based hardware.

---

### Post by Ayuthia on 2010-10-12
> **goinglinux said:**
> My HP Pavilion dm4 notebook has the bcm4313 and worked with the proprietary driver provided with Ubuntu 10.04 but did not work with the corresponding driver provided with Ubuntu 10.10. The solution that worked for me was to install "broadcom-sta-common" and its dependencies using Synaptic. After enabling the proprietary driver (System > Administration > Additional Drivers) and rebooting, wireless works. 

Out-of-the-box, Ubuntu 10.10 apparently supports only BCM4311-, BCM4312-, BCM4321-, and
BCM4322-based hardware. Installing the broadcom-sta-common package includes support for all of these network cards and adds support for BCM4313-based hardware.

It also covers some 4328 cards also.  The b43/b43legacy driver covers the 4301/4306/4311/4312/4320 and several other older versions.  The Broadcom STA driver covers the ones you mention.  The newer brcm80211 version covers the 43224, 43225, and the 4727? cards.  However, the brcm80211 version came out during the late stages of Maverick testing so it was not able to be included.

I will have to look at the broadcom-sta-common package because I thought that was the same as the driver provided in Additional Drivers.

According to the [linuxwireless]("http://linuxwireless.org/en/users/Drivers/b43") site, it looks like the 4313 card is supposed to work with the b43 driver (it is reported to possibly work with this brcm80211 driver also).  Out of curiosity, did you try that one or the brcm80211 driver?

---

### Post by chargersfan420 on 2010-10-12
With the new brcm80211 driver, I have already experienced several kernel panics.  I notice on the [[COLOR="Red"]linuxwireless[/COLOR]]("http://linuxwireless.org/en/users/Drivers/brcm80211") site, it says this:
43224/5 has a locking issue, stable with maxcpus=1, can crash otherwise after random period.

(I'm not sure if "kernel panic" is the right phrase, but when it happens, the screen freezes, and nothing responds (keyboard, mouse, etc).  Also the caps lock and scroll lock lights blink.)

Ayuthia, do you know how this can help me?  I would guess that the maxcpus flag needs to be inserted into a file somewhere before building the driver, but I have no idea where.

In the meantime I'm going to switch back to the STA driver and install the broadcom-sta-common package and see if that makes things better with that driver.

---

### Post by Ayuthia on 2010-10-12
> **chargersfan420 said:**
> With the new brcm80211 driver, I have already experienced several kernel panics.  I notice on the [[COLOR="Red"]linuxwireless[/COLOR]]("http://linuxwireless.org/en/users/Drivers/brcm80211") site, it says this:
43224/5 has a locking issue, stable with maxcpus=1, can crash otherwise after random period.

(I'm not sure if "kernel panic" is the right phrase, but when it happens, the screen freezes, and nothing responds (keyboard, mouse, etc).  Also the caps lock and scroll lock lights blink.)

Ayuthia, do you know how this can help me?  I would guess that the maxcpus flag needs to be inserted into a file somewhere before building the driver, but I have no idea where.

In the meantime I'm going to switch back to the STA driver and install the broadcom-sta-common package and see if that makes things better with that driver.
It has been a while since I have done something like this, but I think that it is accomplished by creating a file in /etc/modprobe.d:
```

gksudo gedit /etc/modprobe.d/brcm80211.conf

```
inside that file add the following:
```

options brcm80211 maxcpus=1

```
and save the file.

The next time you start up, the system should read this file and use that option.

I hope that helps.

---

### Post by chargersfan420 on 2010-10-12
Thanks again Ayuthia!  

The STA driver with the broadcom-sta-common package didn't seem to help.  I have moved back to the brcm80211 driver and added the .conf file as you suggested.  Hopefully this helps; I'll see how stability is in the next little while here and report back.

---

### Post by chargersfan420 on 2010-10-12
Shoot, I thought we had it here!  Had another kernel panic.  After booting up, I noticed a message flash across the screen, and I also found it in dmesg:

```
brcm80211: Unknown parameter 'maxcpus'
```

A little bit of googling suggests that 'maxcpus' is a kernel boot parameter, which I suppose means that in order to use that setting, my whole system would be forced to use only one cpu... If I'm reading this right, that's not an option I'd like to go with.

Maybe it's just not stable enough on 2.6.35-22-generic.  

Baga255, are you having any luck with the brcm80211 driver?  Which kernel are you on?  (to ask that another way, what is the output of the command "uname -r"?)

---

### Post by Baga255 on 2010-10-13
Using the same kernel as you are. So far no major problems. Haven't used it much though. If anything goes wrong I'll be sure to let you know :)
I'd be glad to help you but I'm new to linux so I don't think I'm of any use :(

---

### Post by chargersfan420 on 2010-10-13
I have gone back to the STA driver with the broadcom-sta-common package installed and it actually seems to be working much better than it did before.  Thank you to goinglinux for the suggestion!  And thanks again to Ayuthia for the assistance!  It is people like you who make Ubuntu such a great distro.

---

### Post by Ayuthia on 2010-10-13
> **chargersfan420 said:**
> I have gone back to the STA driver with the broadcom-sta-common package installed and it actually seems to be working much better than it did before.  Thank you to goinglinux for the suggestion!  And thanks again to Ayuthia for the assistance!  It is people like you who make Ubuntu such a great distro.

Thanks for letting us know and thank you, goinglinux for suggesting it!  I wasn't aware that the broadcom-sta driver works with the 43224 cards.

---

### Post by goinglinux on 2010-10-17
> **Ayuthia said:**
> It also covers some 4328 cards also.  The b43/b43legacy driver covers the 4301/4306/4311/4312/4320 and several other older versions.  The Broadcom STA driver covers the ones you mention.  The newer brcm80211 version covers the 43224, 43225, and the 4727? cards.  However, the brcm80211 version came out during the late stages of Maverick testing so it was not able to be included.

I will have to look at the broadcom-sta-common package because I thought that was the same as the driver provided in Additional Drivers.

According to the [linuxwireless]("http://linuxwireless.org/en/users/Drivers/b43") site, it looks like the 4313 card is supposed to work with the b43 driver (it is reported to possibly work with this brcm80211 driver also).  Out of curiosity, did you try that one or the brcm80211 driver?

I did not try the brcm80211 driver. However, my wireless stopped working again after using PCCMOSCleaner to reset the factory-set password. (I did not retrieve the password before I blew away the Windows 7 installation to install Ubuntu). If I can't get it working using the b43/sta driver, I'll give brcm80211 a try.

---

### Post by goinglinux on 2010-10-18
> **goinglinux said:**
> If I can't get it working using the b43/sta driver, I'll give brcm80211 a try.

OK, now I'm just frustrated. I'm still working on getting the drivers working that are available from the repository before I try compiling brcm80211. Since the topic is really different from the one for this thread, I have created a [new thread]("http://ubuntuforums.org/showthread.php?p=9991215#post9991215") for the HP dm4 / Broadcom 4313 issue.

---

### Post by ShouriChatterjee on 2010-10-22
I followed the suse guideline and compiled the brcm80211 driver for myself.

I have bcm4313 (pci id 14e4:4727), and the proprietary "wl" driver works. There are certain issues with the proprietary "wl" driver - after a suspend the wl driver would not look for the currently available networks but would try to login to the older network even though I have travelled from office to home... A module reload would be the only way to fix the issue.

The compilation worked fine. I had an initial glitch with the makefile.
Instead of writing "ccflags-y += -I$(SUBDIRS)/include etc,
I had to put the includes directly into the ccflags-y variable which is right beneath.

Subsequently there were no compilation errors.

The brcm80211 driver works fine. If you do "depmod" once before loading the module for the first time, then you will no longer have to manually insert mac80211.

Comments on use:

1. Somehow, my wireless is very fast now! The driver seems to be doing a better job than "wl".
2. brcm80211 connects to networks much faster than wl. With the wl driver it would take me a good 30 seconds to change from one network to another. brcm80211 connects in a second or 2.
3. The driver is not mature enough to handle suspend-hibernates. My laptop suspended without any problems. After wake-up, the module seemed to be running, but no networks were detected. Subsequently, I re-loaded the module (sudo modprobe -r brcm80211 ; sudo modprobe brcm80211), and then it was blazing fast again.

---

### Post by ShouriChatterjee on 2010-10-22
Forgot to mention:
jockey recognises the brcm80211 driver!! Attached is a screenshot.

---

### Post by ShouriChatterjee on 2010-10-22
> **ShouriChatterjee said:**
> 
3. The driver is not mature enough to handle suspend-hibernates. My laptop suspended without any problems. After wake-up, the module seemed to be running, but no networks were detected. Subsequently, I re-loaded the module (sudo modprobe -r brcm80211 ; sudo modprobe brcm80211), and then it was blazing fast again.

To fix this, you have to do the following:
```
cd /etc/pm/config.d/
sudo echo "SUSPEND_MODULES=\"brcm80211\"" > suspend-modules

```

---

### Post by facebuntu on 2010-10-31
I've got a HP Probook 6540b and it has the BCM 43224 wireless and since I upgraded from 10.04 to 10.10 my wireless performance suffered.

Ping latency from my lappy to wireless router goes between 1ms and up to 300ms.  Even a telnet session is painful to use.  

Does not have issue dual boot in Windows 7 so must be the new 10.10 drivers?  I've tried removing the BC STA drivers completely and rebuilding manually and so on but no change.

Have this issue with all different APs while other wireless devices does not connected to the same AP.

Any one come across this or have any suggestions?

---

### Post by chargersfan420 on 2010-11-02
@ facebuntu - Yes.  Using the BCM 43224 card on an Alienware M17x.  The STA driver sucks.  I get dropped from my network every 20 minutes or so.  Reconnecting can take 30 seconds or more.  Packet loss is common.  Downloading large files, I see my network usage peak, and then flatline, over and over again.  I hate this driver.

Since the brcm80211 driver seems to cause kernel panics for me, it looks like I am stuck with STA for now.  The card seems to work fine in Win7, which I didn't test very much.

My router is using a "g" network, although I can switch to use "n" equipment, although I don't think it will really help.

So, I am afraid I am not much help, but if you get anywhere with it, I'd love to hear about it.

---

### Post by facebuntu on 2010-11-08
I tried using ndiswrapper with a winxp 64bit driver for the broadcom 43224 from the HP support page.

Good news is that it seems to fix my wireless latency issue as latency is very stable 1ms and below constant.

Bad news is Ubuntu will refuse to boot and hang on boot 9 out 10 attempts with various ndis related issue.  I had to remove it when I get it to boot again.  I need this laptop for work so can't screw around with it too much so have not tried another windows 64bit driver.

---

### Post by vsh3r on 2010-11-08
Hi,

If you are having some boot issues you should take a look at the /var/log/messages file and see the last few messages.

V$H.

---

### Post by chargersfan420 on 2010-11-20
Still using the STA driver, I decided to try out a new router.  I replaced my old wireless-g model and I am now using a dual band N router.  Using the 5GHz band, performance has been great so far.  Speed is much faster, no random drops to speak of (so far).  Upload and download speeds are constant, no more peaking and flatlining.  My network is also using WPA2-personal, and the g network was unsecured.

Hopefully this helps someone...

---

