---
title: "Waiting for network configuration"
date: 2011-11-29
forum: Networking &amp; Wireless
---

### Post by Leo Reijnen on 2011-11-29
[FONT=DejaVu Sans Mono, monospace]I wish to get rid of the “waiting for network configuration” and “waiting up to 60 more seconds for network configuration” in Ubuntu 11.10. My reasoning is that it only tries to set up the eth0 connection and I don't use that on this laptop. I always use wlan0.[/FONT]
 
[FONT=DejaVu Sans Mono, monospace]I googled a lot and tried out a number of tips:[/FONT]
 
 [FONT=DejaVu Sans Mono, monospace]1) I commented out this line in /etc/udev/rules.d/70-persistent-net.rules

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:69:56:be:81", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="eth0"
[/FONT]
 [FONT=DejaVu Sans Mono, monospace]but that doesn't work because the line is automatically added again each time
[/FONT]
 [FONT=DejaVu Sans Mono, monospace]2) in \etc\network\interfaces I commented out two lines referring to eth0[/FONT]
 
 [FONT=DejaVu Sans Mono, monospace]3) I removed 'network manager' and used WICD to remove eth0 but that has no effect[/FONT]
 
[FONT=DejaVu Sans Mono, monospace]4) In [/FONT][FONT=DejaVu Sans Mono, monospace]/etc/dhcp3/dhclient.conf I set the timeout=20 in stead of 60[/FONT]
 
 [FONT=DejaVu Sans Mono, monospace]5) I have put a bash script called 'disable_eth0.sh' in /etc/init.d/ to run on startup that should turn off eth0;[/FONT]
 [FONT=DejaVu Sans Mono, monospace]sudo ifconfig eth0 down

[/FONT][SIZE=2][FONT=DejaVu Sans Mono, monospace]It appears to do nothing.[/FONT] [FONT=DejaVu Sans Mono, monospace]Does anyone know how to accomplish this, or is it simpy impossible?
Leo[/FONT][/SIZE]

---

### Post by praseodym on 2011-11-29
Why not blacklisting the driver?

---

### Post by Leo Reijnen on 2011-11-29
> **praseodym said:**
> Why not blacklisting the driver?
I'll try anything. How do I go about that? And will this happen prior to the network configuration at startup?

---

### Post by praseodym on 2011-11-29
Yes, please show:

```
lspci -nnk | grep -iA2 net
lsmod
```

---

### Post by Leo Reijnen on 2011-11-29
> **praseodym said:**
> Yes, please show:

```
lspci -nnk | grep -iA2 net
lsmod
```
Thanks for your reply. I have to leave now, but will get back with the results later. Thanks for your patience!

---

### Post by Leo Reijnen on 2011-11-29
> **Leo Reijnen said:**
> Thanks for your reply. I have to leave now, but will get back with the results later. Thanks for your patience!
root@leo-laptop:/home/leo# lspci -nnk | grep -iA2 net
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Askey Computer Corp. WLL3141 (Toshiba PA3613U-1MPC) 802.11bg Wireless Adapter [144f:7128]
    Kernel driver in use: ath5k
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Toshiba America Info Systems Device [1179:ff00]
    Kernel driver in use: r8169
and
root@leo-laptop:/home/leo# lsmod
Module                  Size  Used by
des_generic            21191  0 
md4                    12523  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
snd_hda_codec_realtek   254125  1 
nls_utf8               12493  3 
cifs                  248817  5 
binfmt_misc            17292  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
usbhid                 41905  0 
hid                    77367  1 usbhid
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
psmouse                73673  0 
serio_raw              12990  0 
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39822  0 
tifm_7xx1              12937  0 
i915                  505108  3 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
tifm_core              15040  1 tifm_7xx1
ath5k                 145100  0 
ath                    19387  1 ath5k
drm_kms_helper         32889  1 i915
sparse_keymap          13658  0 
drm                   192226  4 i915,drm_kms_helper
mac80211              393459  1 ath5k
i2c_algo_bit           13199  1 i915
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172392  3 ath5k,ath,mac80211
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
coretemp               13188  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
r8169                  43104  0

---

### Post by praseodym on 2011-11-29
Deactivation:

```
echo "blacklist r8169" | sudo tee /etc/modprobe.d/blacklist-r8169.conf
sudo modprobe -rfv r8169
```
On-the-fly activation
```
sudo modprobe -v r8169
```
Permanent activation:
```
sudo rm /etc/modprobe.d/blacklist-r8169.conf
sudo modprobe -v r8169
```

---

### Post by Leo Reijnen on 2011-11-29
That's very thoughtful of you, to include the 'undo'-examples as well. I executed the code and got back some message that seem to confirm the action.
Unfortunately, upon reboot all was the same. Apparently, blacklisting the driver doesn't stop Ubuntu from trying to configure eth0.
This is one tough bastard, isn't it?

---

### Post by praseodym on 2011-11-29
Unload the module and build the initram again:

```
sudo modprobe -rfv r8169
sudo depmod -a
sudo update-initramfs -u
```

---

### Post by Leo Reijnen on 2011-11-29
Okay, I did that:

root@leo-laptop:/home/leo# sudo modprobe -rfv r8169
rmmod /lib/modules/3.0.0-13-generic/kernel/drivers/net/r8169.ko
root@leo-laptop:/home/leo# depmod -a
root@leo-laptop:/home/leo# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic
root@leo-laptop:/home/leo# 

Now what do I do? Repeat the earlier blacklisting? Or just Reboot?

By the way - stupid newbie question - how do you make the tidy boxes with the code in them?

---

### Post by praseodym on 2011-11-29
Yes, reboot, the driver is still blacklisted. Codebox: Mark the text in "Advanced Mode" and klick on the "#"-Button

---

### Post by Leo Reijnen on 2011-11-29
I have now become convinced that this is a bug and will wait for updates that repair it.
Thanks for trying to help, Praseodym!

---

### Post by hmandmpsaunders on 2011-11-30
Did you upgrade to Oneiric. If so, I found a workaround that fixes this.  It involves /var/run/dbus if I remember.

---

### Post by Leo Reijnen on 2011-11-30
> **hmandmpsaunders said:**
> Did you upgrade to Oneiric. If so, I found a workaround that fixes this.  It involves /var/run/dbus if I remember.
Yes, Oneiric it is. Please tell me about the orkaround. I have already tried the trick with the \var and \var\run thing, but I can't remember anything about dbus.

---

### Post by gandalf2000 on 2011-12-02
I have just upgraded to 11.10 with Gnome shell and liked what I saw. But, when I booted up the 'puter the next time I got the same messages about waiting for network configuration.  The problem is that the damn thing won't boot up at  all.  After waiting the next 60 seconds the screen just goes blank and sits there doing nothing.  

I pressed F2 an got  a bunch of messages and pressed it again and the 'puter  said it will boot with out the network config thing but just went blank again and didn't boot!!!

Can anyone tell me how  to get it to boot up, please?

I had to resort to Windows to submit this (shudder).

---

### Post by Leo Reijnen on 2011-12-02
For this particular problem, take a look here: [http://uksysadmin.wordpress.com/2011/10/14/upgrade-to-ubuntu-11-10-problem-waiting-for-network-configuration-then-black-screen-solution/](http://uksysadmin.wordpress.com/2011/10/14/upgrade-to-ubuntu-11-10-problem-waiting-for-network-configuration-then-black-screen-solution/)

---

### Post by gandalf2000 on 2011-12-02
Thanks for the quick relpy, Leo.  Unfortunately, this didn't work for me.  Anyone else before I do a complete new install?

**UPDATE.**

I had a more careful look at the script, the printer printed it out very small and I ended up using a magnifying glass, and noticed a couple of gaps that I had not put in the first couple of attempts.  Once I did right IT WORKS.  The first gap was in line  4 between "/run and /run".  The second was  in line 5 between "/var/run and /var/lock".  The third was line 6 between "/run and /var" and the last was line 7 between "/run/lock and /var"  Hope that helps someone in the future.
 
Thank you very much, Leo.

---

