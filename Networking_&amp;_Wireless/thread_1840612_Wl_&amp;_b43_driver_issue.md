---
title: "Wl &amp; b43 driver issue"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by roadkillguy on 2011-09-07
I was messing with aircrack-ng, for which I installed the b43 driver, and I blacklisted the wl (STA) driver.  Unfortunately, I believe b43 isn't as good (I have trouble remaining connected to wireless networks around campus) and I'd like to switch back to the proprietary driver (wl).

When my computer starts up, it instantly connects to a wireless connection, but a couple seconds later disconnects.  Using lsmod, I find that both wl and b43 are running even though I've blacklisted b43 in /etc/modprobe.d/blacklist.conf.  When I get rid of b43 using modprobe -r b43, I no longer have any sort of wireless at all even though Additional Drivers says wl is running and in use.

Any help would be greatly appreciated.

I'm running Ubuntu 11.04 and I believe I have the most recent kernel(2.6.38-11-generic i686).  I believe I have a Broadcom 4315 card in my HP Mini 110. -01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

Thanks in advance

---

### Post by wildmanne39 on 2011-09-07
Hi, thats is because that card needs the b43  driver 11.04 and you need to blacklist the wl driver it needs the LP-PHY firmware, any problems post back we are happy to help.

in synaptic make sure under broadcom only the b43fwcutter and LP-PHY firmware is installed remove anything else there with a green square by it, then restart your computer.
Thank you

---

### Post by roadkillguy on 2011-09-07
So the wl driver no longer works with this kernel?  Wl is the driver I was trying to switch back to... I'm not sure if I've updated the kernel since I switched to b43...

---

### Post by wildmanne39 on 2011-09-07
When you update to 11.04 you install a new kernel, of course there has been about three kernel upgrades since 11.04 came out.
B43 is a good driver but the firmware you need is a low power firmware so it might not have as good of signal strength but I am not sure of that, it is probably another issue like having two drivers installed at the same time usually causes disconnections

Thank you

---

### Post by roadkillguy on 2011-09-08
> **wildmanne39 said:**
> When you update to 11.04 you install a new kernel, of course there has been about three kernel upgrades since 11.04 came out.
B43 is a good driver but the firmware you need is a low power firmware so it might not have as good of signal strength but I am not sure of that, it is probably another issue like having two drivers installed at the same time usually causes disconnections

Thank you

???

Anyway, I want to use WL.  Currently, the system starts up b43 even when blacklisted.

How?

---

### Post by bkratz on 2011-09-08
> **roadkillguy said:**
> ???

I should be thanking **you**... when my problem is solved.

Anyway, I want to use WL.  Currently, the system starts up b43 even when blacklisted.

How?

Copied and modified from an nm-geo post  Quote


```
gksudo gedit /etc/rc.local
```

add this line before the exit 0

```
modprobe -rf b43
```

Save and close terminal


"[COLOR="RoyalBlue"]I have used that when a module loads after blacklisting doesn't stop their install[/COLOR]."

Probably will require a reboot to see effect. If it doesn't work simply remove it and reboot again.

[COLOR="Red"]Freely  from his post (with a few additions!)[/COLOR]

---

### Post by wildmanne39 on 2011-09-08
Hi, good work bkratz, I saw that one too, have just been to busy to get back here since his post I have everybody at once answering my other posts.
Thank you

---

### Post by roadkillguy on 2011-09-08
Well, wl is running (without b43), but my wireless card's LED is permanently orange, and I have no wireless options through network manager.  Editing rc.local seems like a temporary fix to me... is there any other way?  There is nothing wrong with getting rid of b43 at this point.

It's a good thing I have ethernet.

EDIT:  wl works after stopping and then starting it using "modprobe -r wl" and then "modprobe wl", but I don't like a lot of things in my rc.local file.

---

### Post by wildmanne39 on 2011-09-08
Hi, this  is the only driver and firmware that works with your card in 11.04.

Like I said the issue is probably two drivers installed at the same time and we can check for that and other things after you remove the wl driver and install the other.
> b43fwcutter and LP-PHY firmware 
Thank you

---

### Post by roadkillguy on 2011-09-08
I already have b43-fwcutter installed.  (I remember now that it was the low power one)

```
david@david-netbook:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by bkratz on 2011-09-08
@wildmanne39 check your PM's

---

### Post by roadkillguy on 2011-09-08
> **bkratz said:**
> @wildmanne39 check your PM's

??? Something against me? :P

In that case, sorry about those edits; I was messing with my b43 firmware, but I'm back to square one.

---

### Post by wildmanne39 on 2011-09-08
Hi, no he was telling me that there is a possible work around to use the wl driver so I have been reading up on it.
Thank you

---

### Post by wildmanne39 on 2011-09-08
Hi, I have been discussing this with my friend and the best option for getting it to work is the b43 so please run these commands so I can see what is loaded.
```
lsmod
```
```
iwconfig
```
```
sudo lshw -C network 
```
Thank you

---

### Post by roadkillguy on 2011-09-08
$ lsmod
```
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24113  4 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
i915                  451033  2 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
snd_timer              28659  2 snd_pcm,snd_seq
drm_kms_helper         40745  1 i915
uvcvideo               66851  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               75143  1 uvcvideo
joydev                 17322  0 
psmouse                73312  0 
drm                   184164  3 i915,drm_kms_helper
snd                    55295  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
arc4                   12473  2 
b43                   296610  0 
video                  18951  1 i915
ssb                    45942  1 b43
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  2 
atl1c                  36237  0 
libahci                25548  1 ahci

```

$ iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"BLUEZONE"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 16:0B:04:CF:E9:AA   
          Bit Rate=5.5 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:203  Invalid misc:250   Missed beacon:0


```

$ sudo lshw -C network
```
PCI (sysfs)  

```

Anything else?  Interestingly enough after reinstalling the firmware it's not acting like it used to.  B43 ran great (and started up much faster than wl) before I started messing with airodump-ng.  After a few days, airodump-ng stopped working after 4 seconds after being run, and my card wouldn't stay connected.  So far, neither has happened.

But yeah, I'd still like to be able to switch to wl without b43 starting up.

---

### Post by wildmanne39 on 2011-09-08
Hi, I have been doing some research and the b43 driver is ok with what you want according to the documentation, however I did not know what you was trying to accomplish until I looked it up and it is against forum policy to discuss that program.

I do not believe it is the driver and believe it is because both of them were loading now that the wl is not you should be ok, I know that the sta worked in previous versions of ubuntu and with some kind of work around it might be possible, but I do not want to get into trouble now that I know the program is against forum policy, I hope you understand.

If I have been helpful would you show your support for me becoming and ubuntu member? and if your connection continues to work would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by roadkillguy on 2011-09-08
Ahh ok sorry about that.  Delete this thread if necessary.  Thanks for all the help.

---

### Post by wildmanne39 on 2011-09-08
Hi, your very welcome! it cant be deleted except by a staff member but we should be ok, I just need to check things a little closer next time.
I hope it continues to work well if not start and new thread just about your wireless card.
Thank you

---

