---
title: "BCM4321 failure on upgrade to 11.10"
date: 2011-11-22
forum: Networking &amp; Wireless
---

### Post by gopo on 2011-11-22
I'm having some real issues with my BCM4321 on Oneiric, and wondering if I might have one of those "problem child" chips. It didn't seem appropriate to open a new thread. This card worked fine for me with the STA driver in 11.04.

I've tried both the b43 driver and now the STA/broadcom-wl. Each driver appears to load properly, but I can't seem to find or connect to any wireless networks.

**lsb_release -a**:
```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:   oneiric
```

**Successfully completed**:
```

apt-get --purge remove b43-fwcutter firmware-b43-installer
apt-get update && apt-get install bcmwl-kernel-source
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
```
(Rebooted without Ethernet cable plugged in)

**lspci -nnk | grep -iA2 net**:
```

00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 05)
    Subsystem: Intel Corporation Device [8086:2003]
    Kernel driver in use: e1000e
--
02:02.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
    Subsystem: Netgear WN311B RangeMax Next 270 Mbps Wireless PCI Adapter [1385:7d00]
    Kernel driver in use: wl
    Kernel modules: wl, ssb
```

**lsmod | sort**:
```

Module                  Size  Used by
ahci                   26002  2
binfmt_misc            17540  1
bluetooth             166112  10 bnep,rfcomm
bnep                   18436  2
dm_crypt               23199  1
drm                   236330  4 i915,drm_kms_helper
drm_kms_helper         42558  1 i915
e1000e                160535  0
hid                    95463  1 usbhid
i2c_algo_bit           13423  1 i915
i915                  566711  3
lib80211               14991  2 lib80211_crypt_tkip,wl
lib80211_crypt_tkip    17390  0
libahci                26861  1 ahci
lp                     17799  0
mei                    41480  0
parport                46562  3 parport_pc,ppdev,lp
parport_pc             36962  0
ppdev                  17113  0
psmouse                73882  0
rfcomm                 47946  0
serio_raw              13166  0
shpchp                 37345  0
snd                    68266  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hda_codec_hdmi     32040  1
snd_hda_codec_realtek   330769  1
snd_hda_intel          33390  2
snd_hwdep              13668  2 snd_hda_codec,snd_usb_audio
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
snd_pcm                96755  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_rawmidi            30547  2 snd_seq_midi,snd_usbmidi_lib
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_midi           13324  0
snd_seq_midi_event     14899  1 snd_seq_midi
snd_timer              29991  2 snd_pcm,snd_seq
snd_usb_audio         118064  1
snd_usbmidi_lib        25371  1 snd_usb_audio
soundcore              12680  1 snd
uas                    18027  0
usbhid                 47198  1
usb_storage            57901  0
uvcvideo               72711  0
v4l2_compat_ioctl32    17083  1 videodev
video                  19412  1 i915
videodev               93004  1 uvcvideo
wl                   2568210  0
xhci_hcd               78641  0

```

**tail /var/log/syslog**:
```

Nov 20 22:38:40 bubbyland NetworkManager[1011]: <info> Activation (eth1) starting connection 'orange'
Nov 20 22:38:40 bubbyland NetworkManager[1011]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 20 22:38:40 bubbyland NetworkManager[1011]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Nov 20 22:38:40 bubbyland NetworkManager[1011]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Nov 20 22:38:40 bubbyland NetworkManager[1011]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Nov 20 22:38:40 bubbyland NetworkManager[1011]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Nov 20 22:38:40 bubbyland NetworkManager[1011]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Nov 20 22:38:40 bubbyland NetworkManager[1011]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 20 22:38:40 bubbyland NetworkManager[1011]: <info> Activation (eth1/wireless): connection 'orange' has security, and secrets exist.  No new secrets needed.
Nov 20 22:38:40 bubbyland NetworkManager[1011]: <info> Config: added 'ssid' value 'orange'
Nov 20 22:38:40 bubbyland NetworkManager[1011]: <info> Config: added 'scan_ssid' value '1'
Nov 20 22:38:40 bubbyland NetworkManager[1011]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 20 22:38:40 bubbyland NetworkManager[1011]: <info> Config: added 'psk' value '<omitted>'
Nov 20 22:38:40 bubbyland NetworkManager[1011]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Nov 20 22:38:40 bubbyland NetworkManager[1011]: <info> Config: set interface ap_scan to 1
Nov 20 22:38:40 bubbyland NetworkManager[1011]: <info> (eth1): supplicant interface state: inactive -> scanning
Nov 20 22:39:40 bubbyland NetworkManager[1011]: <warn> Activation (eth1/wireless): association took too long.
Nov 20 22:39:40 bubbyland NetworkManager[1011]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 20 22:39:40 bubbyland NetworkManager[1011]: <warn> Activation (eth1/wireless): asking for new secrets
Nov 20 22:39:40 bubbyland NetworkManager[1011]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 20 22:39:40 bubbyland NetworkManager[1011]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 20 22:39:41 bubbyland NetworkManager[1011]: <info> (eth1): supplicant interface state: scanning -> inactive
Nov 20 22:39:45 bubbyland NetworkManager[1011]: <warn> No agents were available for this request.
Nov 20 22:39:45 bubbyland NetworkManager[1011]: <info> (eth1): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Nov 20 22:39:45 bubbyland NetworkManager[1011]: <warn> Activation (eth1) failed for access point (orange)
Nov 20 22:39:45 bubbyland NetworkManager[1011]: <info> Marking connection 'orange' invalid.
Nov 20 22:39:45 bubbyland NetworkManager[1011]: <warn> Activation (eth1) failed.
Nov 20 22:39:45 bubbyland NetworkManager[1011]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 20 22:39:45 bubbyland NetworkManager[1011]: <info> (eth1): deactivating device (reason 'none') [0]

```

Anyone have a good understanding of steps I can take, or further information I can provide?

---

### Post by gopo on 2011-11-22
Here's what the NetworkManager menu reads, before attempting to connect:

[IMG]http://i.imgur.com/vQuxa.png[/IMG]

---

### Post by olivierb2 on 2011-11-23
Hi Pogo,

I endure exactly the same issue has you. But the issue is more complicated than it appears :

[LIST]
[*]The same card **is working** in my old Dell computer with Ubuntu 11.10 64bits
[*]The card **is also working** in my new computer with Ubuntu 11.10 32bits
[*]But **there is no wireless available** with my new computer with Ubuntu 11.10 64bits
[*]I've a wireless key working fine (ralink) with my new computer with Ubuntu 11.10 64bits
[*]I've tried an other distribution under 64bits (Linux Mint Debian) and I endure the same issue than Ubuntu.
[/LIST]

So this problem looks to be definitely linked with hardware ressources. I've also tried to compile latest hybrid broadcom module without success. In all case, the module detect correctly the wireless card, but never shows any wireless network.

From command line, ```
sudo iwlist ethx scanning
``` give ```
No scan results
```.

---

### Post by gopo on 2011-11-27
> **olivierb2 said:**
> ...In all case, the module detect correctly the wireless card, but never shows any wireless network.

oliverb2, exactly! My card doesn't scan for wireless networks either.

Did you notice, however, that you can *create* a wireless network by clicking on the NetworkManager tray icon and choosing "Create New Wireless Network?" (Does this work for you?) Why is that the case?

Here are the other strange things I've uncovered. Under **both** drivers, it appears that:
[LIST=1]
[*]the module (**b43** or **wl**) is properly loaded into the kernel, 
[*]the interface is created (with **wl**, "eth1" is created, and with **b43**, it's called "wlan0"), and
[*]information about the card is available to the OS.
[/LIST]

For example, using the **STA/broadcom-wl** driver:
```
# iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

eth1      IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0
```

The **bcmwl-kernel-source** package, when installed, doesn't show any errors when downloading and excising the firmware, and compiling the module. It's built properly, and its "info" fields seem to indicate that it's meant for our old friend the 14e4:4329, among others:

```
# modinfo wl
filename:       /lib/modules/3.0.0-13-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     1E121706FBA8C851ED8D2F6
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000435Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A99Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          **pci:v000014E4d00004329sv*sd*bc*sc*i***
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
depends:        lib80211
vermagic:       3.0.0-13-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           name:string
```

---

### Post by olivierb2 on 2011-12-04
Sorry for the delay, I forgot to subscribe to the post.

It seems that I can create an adhoc wireless network, but others wireless device doesn't seen it.

I really think that the issue is related to the kernel ressources when using 64bits.

I will make others test (do you know if there is ppa kernel 3.1.1 somewhere ?). I let you know of my advance.

---

### Post by gopo on 2011-12-05
> **olivierb2 said:**
> I really think that the issue is related to the kernel resources when using 64bits.

That is interesting! Have you tried either of these drivers on an i386 machine?

> I will make others test (do you know if there is ppa kernel 3.1.1 somewhere ?). I let you know of my advance.

I don't know if there's a PPA available, though I did find certain instructions on installing a 3.1 (RC2) kernel in 11.10 at [http://www.howopensource.com/2011/08/how-to-install-linux-kernel-3-1-rc2-oneiric-in-ubuntu-11-04-10-10-and-10-04/]("http://www.howopensource.com/2011/08/how-to-install-linux-kernel-3-1-rc2-oneiric-in-ubuntu-11-04-10-10-and-10-04/").

I also realized that these forums have conflicting information regarding whether or not this particular chip version is supported!

---

### Post by praseodym on 2011-12-05
Hi,

please show

```
rfkill list
```
and try WPA2-AES encryption

---

### Post by gopo on 2011-12-05
> **praseodym said:**
> please show "rfkill list" and try WPA2-AES encryption

praseodym, thank you! Isn't this weird? I am currently using WPA2 + TKIP. I'm not sure if AES is enabled. I will check later today.

*edit: I had it set to WPA2 Personal with TKIP / AES encryption. Changed to WPA2+AES [in my reply below]("http://ubuntuforums.org/showpost.php?p=11516605&postcount=9").*

---

### Post by gopo on 2011-12-06
> **praseodym said:**
> Hi, please show *rfkill list* and try WPA2-AES encryption

Okie dokie, here goes.

```

$ sudo rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Here's the log when I set the router to use WPA2-AES and try reconnecting. The router is a Linksys E3000 running TomatoVPN v.128. Note that I'm using the **b43** driver, which creates the 'wlan0' interface.

```

Dec  5 21:33:59 bubbyland NetworkManager[1113]: <info> Activation (wlan0) starting connection 'orange'
Dec  5 21:33:59 bubbyland NetworkManager[1113]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec  5 21:33:59 bubbyland NetworkManager[1113]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  5 21:33:59 bubbyland NetworkManager[1113]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec  5 21:33:59 bubbyland NetworkManager[1113]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec  5 21:33:59 bubbyland NetworkManager[1113]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec  5 21:33:59 bubbyland NetworkManager[1113]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec  5 21:33:59 bubbyland NetworkManager[1113]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec  5 21:33:59 bubbyland NetworkManager[1113]: <info> Activation (wlan0/wireless): connection 'orange' has security, and secrets exist.  No new secrets needed.
Dec  5 21:33:59 bubbyland NetworkManager[1113]: <info> Config: added 'ssid' value 'orange'
Dec  5 21:33:59 bubbyland NetworkManager[1113]: <info> Config: added 'scan_ssid' value '1'
Dec  5 21:33:59 bubbyland NetworkManager[1113]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Dec  5 21:33:59 bubbyland NetworkManager[1113]: <info> Config: added 'psk' value '<omitted>'
Dec  5 21:33:59 bubbyland NetworkManager[1113]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec  5 21:33:59 bubbyland NetworkManager[1113]: <info> Config: set interface ap_scan to 1
Dec  5 21:33:59 bubbyland NetworkManager[1113]: <info> (wlan0): supplicant interface state: inactive -> scanning
Dec  5 21:35:00 bubbyland NetworkManager[1113]: <warn> Activation (wlan0/wireless): association took too long.
Dec  5 21:35:00 bubbyland NetworkManager[1113]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Dec  5 21:35:00 bubbyland NetworkManager[1113]: <warn> Activation (wlan0/wireless): asking for new secrets
Dec  5 21:35:00 bubbyland NetworkManager[1113]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Dec  5 21:35:00 bubbyland NetworkManager[1113]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Dec  5 21:35:02 bubbyland NetworkManager[1113]: <info> (wlan0): supplicant interface state: scanning -> inactive
Dec  5 21:35:11 bubbyland NetworkManager[1113]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Dec  5 21:35:11 bubbyland NetworkManager[1113]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  5 21:35:11 bubbyland NetworkManager[1113]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec  5 21:35:11 bubbyland NetworkManager[1113]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Dec  5 21:35:11 bubbyland NetworkManager[1113]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec  5 21:35:11 bubbyland NetworkManager[1113]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec  5 21:35:11 bubbyland NetworkManager[1113]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec  5 21:35:11 bubbyland NetworkManager[1113]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec  5 21:35:11 bubbyland NetworkManager[1113]: <info> Activation (wlan0/wireless): connection 'orange' has security, and secrets exist.  No new secrets needed.
Dec  5 21:35:11 bubbyland NetworkManager[1113]: <info> Config: added 'ssid' value 'orange'
Dec  5 21:35:11 bubbyland NetworkManager[1113]: <info> Config: added 'scan_ssid' value '1'
Dec  5 21:35:11 bubbyland NetworkManager[1113]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Dec  5 21:35:11 bubbyland NetworkManager[1113]: <info> Config: added 'psk' value '<omitted>'
Dec  5 21:35:11 bubbyland NetworkManager[1113]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec  5 21:35:11 bubbyland NetworkManager[1113]: <info> Config: set interface ap_scan to 1
Dec  5 21:35:11 bubbyland NetworkManager[1113]: <info> (wlan0): supplicant interface state: inactive -> scanning
Dec  5 21:36:11 bubbyland NetworkManager[1113]: <warn> Activation (wlan0/wireless): association took too long.
Dec  5 21:36:11 bubbyland NetworkManager[1113]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Dec  5 21:36:11 bubbyland NetworkManager[1113]: <warn> Activation (wlan0/wireless): asking for new secrets
Dec  5 21:36:11 bubbyland NetworkManager[1113]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Dec  5 21:36:11 bubbyland NetworkManager[1113]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Dec  5 21:36:14 bubbyland NetworkManager[1113]: <info> (wlan0): supplicant interface state: scanning -> inactive
Dec  5 21:36:14 bubbyland NetworkManager[1113]: <warn> No agents were available for this request.
Dec  5 21:36:14 bubbyland NetworkManager[1113]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Dec  5 21:36:14 bubbyland NetworkManager[1113]: <warn> Activation (wlan0) failed for access point (orange)
Dec  5 21:36:14 bubbyland NetworkManager[1113]: <info> Marking connection 'orange' invalid.
Dec  5 21:36:14 bubbyland NetworkManager[1113]: <warn> Activation (wlan0) failed.
Dec  5 21:36:14 bubbyland NetworkManager[1113]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Dec  5 21:36:14 bubbyland NetworkManager[1113]: <info> (wlan0): deactivating device (reason 'none') [0]

```

Thanks again!

---

### Post by KapitaenM on 2011-12-06
14e4:4329?

I've only got mine working via PIO mode. You can try it out with

```
rmmod b43; modprobe b43 pio=1

or

rmmod b43; modprobe b43 pio=1 qos=0
```

Hopefully b43 can make usable the 4329 chipset in DMA, because it's **slow** in PIO.
You may find some success in broadcom-wl, but I have a feeling your system will seize up like my amd64 Debian box has done since 2.6.37+ (currently using 3.1).

---

### Post by gopo on 2011-12-06
> **KapitaenM said:**
> Hopefully b43 can make usable the 4329 chipset in DMA, because it's **slow** in PIO.

KapitaenM, uh, oh, I certainly hope that's not the case -- I bought the router and card **because** of their speed. And I found that things worked **just fine** when using the x86_64 10.04.

---

### Post by gopo on 2011-12-07
> **KapitaenM said:**
> I've only got mine working via PIO mode. You can try it out with *rmmod b43; modprobe b43 pio=1*

Thanks KapitaenM, this does at least allow me to connect, though at a severe performance penalty. I get less than 25% of normal download speeds.

Sigh. Under "Known Issues" for the b43 driver ([http://wireless.kernel.org/en/users/Drivers/b43]("http://wireless.kernel.org/en/users/Drivers/b43")), I see
> BCM4321: some cards do not work in DMA mode (PIO is needed).

I don't understand the difference between DMA and PIO. Is DMA the "normal" or "high-speed" mode of the card, and PIO the "legacy" slowed-down speed?

---

### Post by KapitaenM on 2011-12-07
The difference is we don't get direct memory access (DMA), so a lot more CPU is used.

But yes, programmed input/output is pretty old, albeit easier to implement. DMA support is supposedly in progress, from what I researched.

Other than that, the alternative is going back to 2.6.36 or sooner, and using broadcom-wl.

---

### Post by olivierb2 on 2011-12-08
> **gopo said:**
> That is interesting! Have you tried either of these drivers on an i386 machine?

Yes as written in my first post, the card is working fine on i386, but I cannot use my 6GB of RAM in this case :(

---

### Post by mechsin on 2011-12-11
So I am glad I finally found this post I have been looking for one since 10.10 that is when my card stop working. I had found lots of post related to other bcm43 chips but none specifically for 4321. So KapitaneM the work around you gave here 
```

rmmod b43; modprobe b43 pio=1 qos=0

```

worked for me. I didn't try the first one. I agree with gopo though my card now says it is only 11 Mb/s. None the less at least I can stop using my phone as my wireless connection having it plugged in all the time has destroyed the battery. 

Does anyone know why the wl module isn't working though? I tried both the Ubuntu build and building it myself off Broadcom's website. I am actually talking with Broadcom's tech support right now via email though they don't seem very helpful. Has a bug been filed somewhere?

Thanks again KapitaneM

---

### Post by mechsin on 2011-12-11
Well after a few hours of using my connection cuts in and out every once in a while. I guess I will just live with it for the time being.
I also wanted to point out I had to create a b43.conf file afterwards to make sure the module was loaded with the correct options. See this thread
[http://ubuntuforums.org/showthread.php?t=1266620]("http://ubuntuforums.org/showthread.php?t=1266620")

---

