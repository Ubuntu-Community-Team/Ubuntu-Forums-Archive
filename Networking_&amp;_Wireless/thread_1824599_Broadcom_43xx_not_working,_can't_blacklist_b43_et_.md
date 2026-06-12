---
title: "Broadcom 43xx not working, can't blacklist b43 et al, usual fixes not working"
date: 2011-08-14
forum: Networking &amp; Wireless
---

### Post by Unparallelogram on 2011-08-14
I have two Broadcom cards in my laptop, one for wired and one for wireless networking.

> mpan@unparallelogram:~$ sudo -i
[sudo] password for mpan: 
root@unparallelogram:~# lspci | grep Broadcom
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
root@unparallelogram:~# 

I would like to use the wl module for my wireless card. It loads fine at boot.

> root@unparallelogram:~# lsmod | grep wl
wl                   2642531  0 
lib80211               14570  1 wl
root@unparallelogram:~# 

Unfortunately, so do the legacy Broadcom drivers in the form of the b43, b44, and b43legacy modules.

> root@unparallelogram:~# lsmod | grep b4
b44                    35301  0 
ssb                    45942  1 b44
root@unparallelogram:~# 

As far as I can tell, they are fighting each other to bind the hardware and the wrong one is winning. I get no light, no response, and nothing recognizes anything.

I have tried numerous methods suggested here and elsewhere that have not worked in my case:

* blacklisting them in modprobe.d conf files
* blacklisting them in modprobe.conf
* removing them with modprobe commands from /etc/rc.local and loading the desired ones
* removing them by had with rmmod

If I poke around too much, things break. For example, forcefully removing b44 with rmmod will break my wired network. I'm not sure what the dependency concern is but apparently I just ran into it.

I hear my wired card needs ssb to remain alive.

Here's lsmod output:

> root@unparallelogram:~# lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
radeon                896428  2 
snd_rawmidi            25269  1 snd_seq_midi
ttm                    65184  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
b44                    35301  0 
drm_kms_helper         40745  1 radeon
joydev                 17322  0 
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
snd_timer              28659  2 snd_pcm,snd_seq
binfmt_misc            13213  1 
ssb                    45942  1 b44
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop            13515  0 
wl                   2642531  0 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   180037  4 radeon,ttm,drm_kms_helper
dcdbas                 14054  1 dell_laptop
pcspkr                 12614  0 
psmouse                73312  0 
soundcore              12600  1 snd
sp5100_tco             13456  0 
serio_raw              12990  0 
ati_agp                13202  0 
i2c_piix4              13095  0 
i2c_algo_bit           13184  1 radeon
lib80211               14570  1 wl
k8temp                 12872  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
shpchp                 32345  0 
video                  18951  0 
evbug                  12581  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  3 
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
libahci                25548  1 ahci
pata_atiixp            12968  0 
root@unparallelogram:~# 


Someone please help. How can I get these modules to go away? Preferably, I would like to retain my wired connection and not need to reapply a fix every kernel update.

Thanks!

---

### Post by garvinrick4 on 2011-08-14
Open Synaptics and type bcm in search and uninstall all else but these two in the b43
install the two in screenshot and reboot.

---

### Post by bkratz on 2011-08-14
> **Unparallelogram said:**
> I have two Broadcom cards in my laptop, one for wired and one for wireless networking.



I would like to use the wl module for my wireless card. It loads fine at boot.



Unfortunately, so do the legacy Broadcom drivers in the form of the b43, b44, and b43legacy modules.



As far as I can tell, they are fighting each other to bind the hardware and the wrong one is winning. I get no light, no response, and nothing recognizes anything.

I have tried numerous methods suggested here and elsewhere that have not worked in my case:

* blacklisting them in modprobe.d conf files
* blacklisting them in modprobe.conf
* removing them with modprobe commands from /etc/rc.local and loading the desired ones
* removing them by had with rmmod

If I poke around too much, things break. For example, forcefully removing b44 with rmmod will break my wired network. I'm not sure what the dependency concern is but apparently I just ran into it.

I hear my wired card needs ssb to remain alive.

Here's lsmod output:



Someone please help. How can I get these modules to go away? Preferably, I would like to retain my wired connection and not need to reapply a fix every kernel update.

Thanks!


Not really about the modules (except, yes the b44 does require ssb),since you are using a Dell--it will probably be interesting 
to see the output of 

rfkill list all

and look to see if "blocked"

---

### Post by Unparallelogram on 2011-08-14
@Gavin

I would much prefer to use the wl (as in, Broadcom STA) driver, not the b43 driver, if at all possible. I have had good results with wl in the past, whereas b43 seems to be rather flaky especially when it comes to my particular model.

@bkratz

> root@unparallelogram:~# rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
root@unparallelogram:~# 

---

### Post by nm_geo on 2011-08-14
Please give us 

```
cat /etc/lsb-release; uname -r
``````
lspci -nn | grep 0280
```The STA (wl) driver has lots of problems running well in Natty.. & Oneiric..on my chipset anyway.

Mine is:

```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

```

---

### Post by Unparallelogram on 2011-08-14
> mpan@unparallelogram:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
mpan@unparallelogram:~$ uname -r
2.6.38-8-generic
mpan@unparallelogram:~$ 


> mpan@unparallelogram:~$ lspci -nn | grep 0280
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
mpan@unparallelogram:~$ 


What is it about wl and this particular release that causes issues? wl has been working fine for me in many past versions (years worth iirc) of Ubuntu and Fedora.

---

### Post by nm_geo on 2011-08-14
> What is it about wl and this particular release that causes issues? wl  has been working fine for me in many past versions (years worth iirc) of  Ubuntu and Fedora.That is an excellent question but  I do not have an adequate answer for you.  I can tell you that during early testing of Natty I was using the STA (wl) driver and after a kernel upgrade I could not get it to work anymore.  So I loaded b43-fwcutter and the firmware-b43-installer... Then I edited the blacklists that the STA (wl) driver creates on b43 & ssb.  

I still try the STA (wl) driver on each new install but have only had it work on Maverick 10.10.  Some Natty users have gone back to the Maverick STA version with good results.  You could try that route I guess.  The b43 works very well on my chipset so I stay with it.

---

### Post by Unparallelogram on 2011-08-14
Seems quite strange. For the moment, I've switched to using the b43 driver with fwcutter. No issues so far.

Thanks everyone! If someone else encounters this, I recommend you try out b43 and it may work better than previously.

---

### Post by nm_geo on 2011-08-14
Please marked Solved if you feel it is resolved. Have fun I think the B43 will work well for you.  By the way a newer version of b43-fwcutter will come out in Oneiric.

---

