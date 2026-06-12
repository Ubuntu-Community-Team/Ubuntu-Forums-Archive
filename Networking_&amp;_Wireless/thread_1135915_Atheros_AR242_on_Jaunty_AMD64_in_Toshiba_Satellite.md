---
title: "Atheros AR242 on Jaunty AMD64 in Toshiba Satellite A205 - No Wireless"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by linux4me on 2009-04-24
I did an upgrade from 8.10 with working wireless--all I had to do was load linux-backport-modules-intrepid to get it to work--but have had zero luck getting WiFi to work with Jaunty. I'm stuck and I could sure use some help!

I'm using 2.6.28-11-generic x86_64.

Output of lspci for wireless:
> 05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Output of ifconfig:
> wlan0     Link encap:Ethernet  HWaddr 00:21:63:31:54:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Output of lsmod:
> Module                  Size  Used by
i915                   75272  2 
drm                   123232  3 i915
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
sbp2                   34700  0 
lp                     19588  0 
joydev                 20864  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557364  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
arc4                   10240  2 
ecb                    11392  2 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
pcmcia                 47640  0 
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tifm_7xx1              14976  0 
ath5k                 136068  0 
psmouse                64028  0 
snd_timer              34064  2 snd_pcm,snd_seq
yenta_socket           35596  1 
rsrc_nonstatic         19584  1 yenta_socket
lbm_cw_mac80211       259000  1 ath5k
sdhci_pci              16896  0 
sdhci                  27396  1 sdhci_pci
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tifm_core              17736  1 tifm_7xx1
pcmcia_core            49188  3 pcmcia,yenta_socket,rsrc_nonstatic
pcspkr                 11136  0 
serio_raw              14468  0 
lbm_cw_cfg80211        85048  2 ath5k,lbm_cw_mac80211
iTCO_wdt               21712  0 
iTCO_vendor_support    12420  1 iTCO_wdt
snd                    78792  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
led_class              13064  1 ath5k
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
intel_agp              39408  1 
input_polldev          12688  0 
video                  29204  0 
output                 11648  1 video
sha256_generic         17792  0 
aes_x86_64             16384  2 
aes_generic            36264  1 aes_x86_64
cbc                    12288  1 
dm_crypt               22792  1 
ohci1394               42036  0 
ieee1394              108288  2 sbp2,ohci1394
r8169                  46596  0 
mii                    14464  1 r8169
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

Here's where it gets a little interesting. The output of dmesg looks like this with a lot of repititions:
> 160.594994] __ratelimit: 5 callbacks suppressed
[  160.595001] ath5k phy0: noise floor calibration timeout (2452MHz)
[  161.005862] ath5k phy0: gain calibration timeout (2457MHz)
[  161.351357] ath5k phy0: noise floor calibration timeout (2457MHz)
[  161.762428] ath5k phy0: gain calibration timeout (2462MHz)
[  162.150391] ath5k phy0: noise floor calibration timeout (2462MHz)
[  162.452817] ath5k phy0: noise floor calibration timeout (2462MHz)
[  162.865433] ath5k phy0: gain calibration timeout (2412MHz)
[  163.210186] ath5k phy0: noise floor calibration timeout (2412MHz)
[  167.956689] ath5k phy0: gain calibration timeout (2417MHz)
[  168.301614] ath5k phy0: noise floor calibration timeout (2417MHz)
[  168.712325] ath5k phy0: gain calibration timeout (2422MHz)
[  169.057270] ath5k phy0: noise floor calibration timeout (2422MHz)
[  169.468361] ath5k phy0: gain calibration timeout (2427MHz)
[  169.813269] ath5k phy0: noise floor calibration timeout (2427MHz)
[  170.232570] ath5k phy0: gain calibration timeout (2432MHz)
[  170.577616] ath5k phy0: noise floor calibration timeout (2432MHz)
[  170.985452] ath5k phy0: gain calibration timeout (2437MHz)
[  171.327514] ath5k phy0: noise floor calibration timeout (2437MHz)

My network configuration looks like this:
>  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:3b:7c:ff
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.0.0.5 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 01
       serial: 00:21:63:31:54:38
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 56:02:17:ce:77:f6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

When I run iwlist scan, I get "No scan results."

Restarting the network has made no difference, nor has rebooting. If I go System->Administration->Hardware Drivers and try to activate the alternate Atheros driver, no driver is downloaded and it says the driver is not activated even after a reboot.

I have gone through all the files in /etc/modprobe.d/ and verified that ath5k is not blacklisted. 

I have successfully run:
```
sudo apt-get install linux-backports-modules-jaunty
```
and rebooted, but still no joy.

I also tried installing the madwifi drivers and blacklisting ath5k, but that didn't work, either. I have subsequently run 
```
sudo make unload
``` 
and
```
sudo make uninstall
```
from the folder where I un-tarred the madwifi drivers.

I really like Jaunty and don't want to go back to Intrepid. Any help will be greatly appreciated. 

TIA

---

### Post by linux4me on 2009-04-24
I spent hours trying to get Wifi to work, and must have done 20 restarts as well as restarting networking through Terminal. I was starting to feel like a Winblowx user again. 

I shut the laptop off to take a break, came back, fired it up, and now wireless is working. Very weird.

---

### Post by luddite666 on 2009-04-27
Oh please tell me how you achieved this - I am in the same boat - only ethernet is working.

---

### Post by linux4me on 2009-04-28
> **luddite666 said:**
> Oh please tell me how you achieved this - I am in the same boat - only ethernet is working.

I can tell you what I think needs to be done, but since there seemed to be a bit of voodoo involved, I'm not sure. First of all, let me stress that this was an upgrade from 8.10, not a clean install, so the procedure would be a bit different for a clean install.

If you're dealing with an upgrade install, you should first look through all the files in /etc/modprobe.d/ to make sure that ath5k is not blacklisted. To do so use the following command:
```
gksudo gedit
```
That will open gedit with the permissions you need to edit the files. Use the Open button to browse to /etc/modprobe.d and open each file associated with networking--or all of them you're not sure aren't networking--and make sure there are no lines blacklisting ath5k that look like this:
```
blacklist ath5k
```
If you find any, comment them out like this:
```
#blacklist ath5k
```
save the file, and move on to the next one. Once you're sure that you've got them all, browse to /etc/modules in gedit and take a look in it. Make sure that there are no lines loading ath_pci or ath_hal left over from a madwifi install. If there are, comment them out and save the file. Close gedit.

Finally, and this step applies to a clean install of Jaunty as well as an upgrade, run the following command to install backports:
```
sudo apt-get install linux-backports-modules-jaunty
```

Now, if there is no voodoo involved, you should be able to just reboot and wireless will work; however, just in case, do a complete shutdown, wait for 15 seconds or so in order for the hard drive to spin down, and then restart. 

If wireless is working, you're done. If not, right-click the network icon on the panel and make sure enable wireless is checked. If it is and you're still not connected, try running the following command and look for ath5k in the list of modules:
```
lsmod
```

If it's there, the only other thing I can think of you can try is to make sure you don't have the restricted driver activated, too. Go System->Administration->Hardware Drivers and see if the restricted driver for the Atheros is active. If it is, you could try deactivating it and rebooting. If it's not, I would say start a new thread here according to the guidelines for help with wireless and see if someone can come up with a solution. Let us know what you figure out.

---

