---
title: "Wireless won't autoconnect after coming back from suspend"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by pretty_whistle on 2011-09-15
The drop down menu thing shows it's connected but it isn't-the word 'disconnect' is not shaded out which means it's giving the option to disconnect as if it were connected.  

To connect, I have to do it manually by finding my network in the list and clicking on it.

Why is it doing that?

Edit:   I forgot to mention which Ubuntu this is, it's 11.04.

---

### Post by pretty_whistle on 2011-09-15
I still need a fix for this.

Anyone?

---

### Post by praseodym on 2011-09-15
Hi,

please show the putputs of:

```
lspci -nnk | grep -iA2 net
lsmod [COLOR="Red"]#complete, and additionally[/COLOR]
lsmod | grep -iE 'usb|1394|hci|ndiswr|forced|8139|hid|802' 
```

With these outputs the "common suspect" modules can be unloaded at SUSPEND/HIBERNATE and reloaded at wake-up (if neccessary).

Did you checkbox "connect automatically" in the network-manager applet?

---

### Post by pretty_whistle on 2011-09-15
> **praseodym said:**
> Hi,

please show the putputs of:

```
lspci -nnk | grep -iA2 net
lsmod [COLOR=Red]#complete, and additionally[/COLOR]
lsmod | grep -iE 'usb|1394|hci|ndiswr|forced|8139|hid|802' 
```With these outputs the "common suspect" modules can be unloaded at SUSPEND/HIBERNATE and reloaded at wake-up (if neccessary).

Did you checkbox "connect automatically" in the network-manager applet?\

Yes I did check "connect automatically" in the applet.

As to the rest of your post:

lspci -nnk | grep -iA2 net

nutin@nutin:~$ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP77 Ethernet [10de:0760] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:360a]
    Kernel driver in use: forcedeth
--
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:137a]
    Kernel driver in use: ath5k





lsmod [COLOR=Red]#complete, and additionally


Module                  Size  Used by
usb_storage            43946  0 
uas                    17676  0 
xt_limit               12541  8 
xt_tcpudp              12531  10 
ipt_LOG                12784  8 
ipt_MASQUERADE         12663  0 
xt_DSCP                12549  0 
ipt_REJECT             12512  1 
nf_conntrack_irc       13138  0 
nf_conntrack_ftp       13106  0 
xt_state               12514  6 
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
iptable_nat            12977  0 
nf_nat                 24827  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19024  9 iptable_nat,nf_nat
nf_conntrack           69744  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
iptable_mangle         12615  0 
iptable_filter         12706  1 
ip_tables              18125  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21907  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
nvidia               7098106  36 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath5k                 144534  0 
psmouse                73312  0 
ath                    19141  1 ath5k
k10temp                12951  0 
soundcore              12600  1 snd
i2c_nforce2            12906  0 
video                  18951  0 
hp_wmi                 13418  0 
shpchp                 32345  0 
lp                     13349  0 
serio_raw              12990  0 
sparse_keymap          13666  1 hp_wmi
joydev                 17322  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
parport                36746  3 parport_pc,ppdev,lp
mac80211              257001  1 ath5k
cfg80211              156212  3 ath5k,ath,mac80211
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  3 
libahci                25548  1 ahci
forcedeth              58190  0 
pata_amd               13762  0 
dm_raid45              88410  0 
xor                    21860  1 dm_raid45





[/COLOR]lsmod | grep -iE 'usb|1394|hci|ndiswr|forced|8139|hid|802'


usb_storage            43946  0 
mac80211              257001  1 ath5k
cfg80211              156212  3 ath5k,ath,mac80211
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  3 
libahci                25548  1 ahci
forcedeth              58190  0 
usb_storage            43946  0 
mac80211              257001  1 ath5k
cfg80211              156212  3 ath5k,ath,mac80211
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  3 
libahci                25548  1 ahci
forcedeth              58190  0

---

### Post by praseodym on 2011-09-15
Maybe the firewall doesnt allow you to get a new IP address? Do you really need it?

The other one you can test:

```
gksudo gedit /etc/pm/config.d/unload_modules
```
Copy this into it:

```
# automatically unload kernel modules often making trouble using SUSPEND/HIBERNATE and reload them during wake-up
SUSPEND_MODULES="$SUSPEND_MODULES usb_storage mac80211 cfg80211 usbhid hid ahci libahci forcedeth ath5k" 
```
save, exit, and set the executable flag:

```
sudo chmod +x /etc/pm/config.d/unload_modules
```
Check it again.

---

### Post by pretty_whistle on 2011-09-15
> **praseodym said:**
> Maybe the firewall doesnt allow you to get a new IP address? Do you really need it?

The other one you can test:

```
gksudo gedit /etc/pm/config.d/unload_modules
```Copy this into it:

```
# automatically unload kernel modules often making trouble using SUSPEND/HIBERNATE and reload them during wake-up
SUSPEND_MODULES="$SUSPEND_MODULES usb_storage mac80211 cfg80211 usbhid hid ahci libahci forcedeth ath5k" 
```save, exit, and set the executable flag:

```
sudo chmod +x /etc/pm/config.d/unload_modules
```Check it again.

Done.  But it didn't help.

But that got me thinking.  I recalled there are 2 listings for my network in the drop down menu.  "Weird.", I thought, "I wonder if that's doing it."  It was- I deleted off the one that didn't have the wifi image by it.  The second I did it, it was fixed.  I tested it a few times to be sure-tests are successful!

It was my fault.  When I put in the wifi network after installing Ubuntu, I put it in twice.  Lol.

Thanks for the help because it led me over there and now it's fixed. :)

But now I have to make a new disk image since the one I made an hour ago has 2 networks on it.  :x

---

