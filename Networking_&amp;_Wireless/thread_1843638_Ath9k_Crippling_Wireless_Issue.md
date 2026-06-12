---
title: "Ath9k Crippling Wireless Issue"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by Corps3Grind3r on 2011-09-13
I'm not really here to look for a solution to my wireless issue because I am already in a state of learned helplessness.  I just want to see if anyone else is having my same issues and how many people are actually affected by this issue.

The issue is simple: My wireless connection drops, randomly.  As network-manager tries to reconnect it just hangs and asks for authentication again, WPA in my case.  Since the passphrase is configured already I just hit connect and network-manager hangs some more until finally it fails to connect.  The only way I have found to reconnect at this point is either to restart the computer or plug in an external wireless card.

I have already tried Wicd instead of Network-Manager and both have the same issue.  I have tried numerous other kernel versions and ubuntu distros.  The external wireless card continues to drop connection as well however, it does reconnect after each drop.  In the syslog I can watch the errors and it seems that as the computer undergoes heavy loads the external wireless card drops and reconnects.  I am assuming this could be happening to the on-board card as well except that the on-board card fails to reconnect.  The errors in the syslog are attributed to the ath on-board card and not the Ralink external card.

I really just hope to create some conversation with this thread.  As crippling and frustrating as this issue has been it has actually helped me learn a lot and understand linux much better.

Output of ```
sudo lshw -C network
```

```
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 1c:4b:d6:da:79:ad
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-11-generic firmware=N/A ip=192.168.1.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn

```

Syslog errors:

```
Sep 13 00:00:39 Apple kernel: [ 6459.008763] ath: Failed to wakeup in 500us
Sep 13 00:00:39 Apple kernel: [ 6459.136324] ath: Chip reset failed
Sep 13 00:00:39 Apple kernel: [ 6459.136341] ath: Unable to reset channel (2412 MHz), reset status -22
Sep 13 00:00:39 Apple kernel: [ 6459.272345] ath: Failed to stop TX DMA in 100 msec after killing last frame
Sep 13 00:00:39 Apple kernel: [ 6459.280589] ath: Failed to stop TX DMA in 100 msec after killing last frame
Sep 13 00:00:39 Apple kernel: [ 6459.288806] ath: Failed to stop TX DMA in 100 msec after killing last frame
Sep 13 00:00:39 Apple kernel: [ 6459.297035] ath: Failed to stop TX DMA in 100 msec after killing last frame
Sep 13 00:00:39 Apple kernel: [ 6459.305286] ath: Failed to stop TX DMA in 100 msec after killing last frame
Sep 13 00:00:39 Apple kernel: [ 6459.313568] ath: Failed to stop TX DMA in 100 msec after killing last frame
Sep 13 00:00:39 Apple kernel: [ 6459.313587] ath: Failed to stop TX DMA!
Sep 13 00:00:39 Apple kernel: [ 6459.327198] ath: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Sep 13 00:00:39 Apple kernel: [ 6459.327214] ath: Could not stop RX, we could be confusing the DMA engine when we start RX up
```

Launchpad Bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/736171](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/736171)

---

### Post by praseodym on 2011-09-13
Try a module parameter:

```
sudo modprobe -rf ath9k
sudo modprobe -v ath9k nohwcrypt=1
sudo service network-manager restart # or wicd or whatever
```
If it works, make it permanent:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

Due to the fact that it occurs with several kernels, etc. you may try to update your router firmware

---

### Post by Corps3Grind3r on 2011-09-14
Thank you for the prompt reply and I apologize for the delay in my response.  

I tried the commands and it still reads "Chip reset failed".

But no worries like I said before I'm just kind of waiting until it gets fixed.

---

### Post by Corps3Grind3r on 2011-09-16
Quick Update:  New issue is arising.  Once again, intermittently, wireless interface isn't loading at boot.  Using ```
sudo /etc/init.d/networking restart
``` doesn't bring the interface up either.

I'm starting to suspect a possible physical failure of hardware.

---

### Post by praseodym on 2011-09-17
Is it recognized with:

```
lspci -nnk | grep -iA2 net
rfkill list
iwconfig
```
Checked BIOS settings?

---

### Post by varunendra on 2011-09-17
Maybe I'm posting here just to keep track of this thread rather than to offer any help, but now that I have joined in, I think it would be interesting to know what is your laptop's brand and model no., and what other modules are currently loaded:
```
lsmod
```

Plus, the outputs from the commands praseodym suggested.

Also, is the output of **lshw -C network** complete that you posted?? I think there must be at least one more entry for Ethernet interface. Please post the complete output so that we can be sure there are no unnecessary drivers in the lsmod list.

One more thing - is it just disconnecting randomly or are you also experiencing packet loss as many other posts suggest:
```
ifconfig -a
```

---

### Post by pdc on 2011-09-17
> The issue is simple: **My wireless connection drops, randomly**.

one find curious posts on this topic

[http://blog.homelinux.org/?p=327](http://blog.homelinux.org/?p=327)

........seemed to work for some !

---

### Post by Corps3Grind3r on 2011-09-23
> **praseodym said:**
> Is it recognized with:

```
lspci -nnk | grep -iA2 net
rfkill list
iwconfig
```
Checked BIOS settings?

The boot issue seems to have gone away or at least it hasn't happened in a while.

Re:**varunendra**

lsmod:
```
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  0 
aes_generic            38023  1 aes_i586
joydev                 17322  0 
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
arc4                   12473  2 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
ath9k                 103633  0 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
eeepc_wmi              18771  0 
snd_seq_midi           13132  0 
i915                  451033  3 
sparse_keymap          13666  1 eeepc_wmi
mac80211              257001  1 ath9k
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
uvcvideo               66851  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
psmouse                73312  0 
videodev               75143  1 uvcvideo
ath                    19141  2 ath9k,ath9k_hw
cfg80211              156212  3 ath9k,mac80211,ath
drm_kms_helper         40745  1 i915
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
drm                   184164  4 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  3 
libahci                25548  1 ahci
atl1c                  36237  0 

```

Full lshw -C network output:
```
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 1c:4b:d6:da:79:ad
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-11-generic firmware=N/A ip=10.105.69.26 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 20:cf:30:50:46:52
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:f7fc0000-f7ffffff ioport:ec00(size=128)

```

Re: **pdc**

I already tried using that module parameter as **praseodym** suggested and it did not work.  The issue isn't a poor connection but a complete drop in connection and a failure to reacquire.

---

### Post by praseodym on 2011-09-23
Update the driver with:

```
sudo apt-get install linux-backports-modules-cw-2.6.39-natty-generic
```
and reboot. I recommend WPA2-AES (CCMP) encryption, if possible.

---

### Post by dave01945 on 2011-09-23
i have the same card and it always used to drop connection under heavy load and sometime wouldn't reconnect and was asking for the pass-phrase until i restarted the card

i have now entered the **BSSID** in network manager settings and haven't had the problem since

i don't know if this will help everybody but it solved my problem or at least has done for the last 4 weeks

---

### Post by Corps3Grind3r on 2011-09-26
I updated the driver.  When I get home I'm going to set the BSSID in network manager to see if that alleviates the issue.

---

### Post by collisionystm on 2011-09-26
I just want you to know you are not alone with this crappy atheros card. I gave up on making it work. I now have a different laptop with an Intel card! Much better.

---

### Post by rabideau on 2011-10-04
Here is a solution that I found on the Arch site.  It works for me... no warranty is expressed or implied.   ):P

ath9k Network Fix (from suspend)

Create a custom script inside /etc/pm/sleep.d with the name ath.sh.
chmod +x the new script.

What follows is the script I use, I hope this helps everyone with an ASUS laptop or an ath9k wireless:

------------------------------------------------------
#!/bin/sh

case "$1" in
    hibernate|suspend)
        nmcli nm sleep true

        rmmod ath9k
        ;;
    thaw|resume)
        modprobe ath9k

        nmcli nm sleep false
        ;;
    *) exit $NA
        ;;
esac

------------------------------------------------------

Good luck!

---

### Post by phunt on 2012-03-09
> **praseodym said:**
> Try a module parameter:

```
sudo modprobe -rf ath9k
sudo modprobe -v ath9k nohwcrypt=1
sudo service network-manager restart # or wicd or whatever
```
If it works, make it permanent:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

Due to the fact that it occurs with several kernels, etc. you may try to update your router firmware

I just registered to say that this seems to have worked for me. My problem was not the same as the OP, but this is still useful for anyone else with the same issue as myself. I installed Ubuntu 11.10 on my Samsung Series 5 Chromebook and found that after a bit (maybe after bringing it out of sleep?) the wireless would be very slow. It would stay connected but it was almost unusable, sometimes pages would fail to load.

After following this advice on running the modprobe commands I'm getting my normal fast performance.  Thanks praseodym!

Also, not sure if it matters, but my network uses WPA2-TKIP for auth.

---

### Post by zinadork on 2012-03-10
Do any of you notice it on some routers and not others?  My home network is hit or miss and more often miss, while my mother's and office work fine.  Does the ath9k driver have issues with wpa encryption? 

I have a cr48 that has issues with chrome os and Ubuntu and an HP that works in Windows 7 and doesn't in Ubuntu.  I've run all updates and terminal commands I've seen on the subject with no success. I've been tethering my phone for connectivity in Ubuntu.

---

### Post by phunt on 2012-03-10
I've used my chromebook on a few routers in ChromeOS and it's always been fine. When running Ubuntu I've only connected it to my Asus RT-N16 running DD-WRT. That's where I experienced the issues that are now solved.
Possibly related: I previously installed Mint Linux instead of Ubuntu and was experiencing the same symptoms. I wasn't able to solve the problem so that was part of the reason to install Ubuntu instead (even though they're nearly identical).

---

### Post by sentythee on 2012-12-21
I have what I believe is the same problem as Corps3Grind3r. To restart the wireless card without rebooting, this should work:  Navigate to /sys/module/ath9k/drivers/pci:ath9k ```
cd /sys/module/ath9k/drivers/pci:ath9k
```  There should be a symlink there consisting of only numbers, colons, and periods. For me, this is 0000:03:00.0. Move into that directory. ```
cd 0000:03:00.0
```  Here, you can disable and re-enable your card: ```
echo 1 > remove;
``````
echo 1 > rescan
```  I will try fixing the BSSID to see if that stops the issue altogether, or at least makes it less common. If you don't hear back from me, then it probably worked.

Edit: It didn't work.

---

