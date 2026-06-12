---
title: "Problem with Cnet CWP-905 Wireless card"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by bobman321123 on 2011-08-07
Hello
I am having difficulty with getting my Cnet CWP-905 wireless card to work in Linux. It works in windows. I used the win drivers with Ndiswrapper, which seemed to work and said "hardware present: yes". But it did not work. When I checked dmesg  it showed
"
[ 1489.855050] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[ 1489.893322] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 1489.893333] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2860'
[ 1489.894355] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2860; check system log for messages from 'loadndisdriver'
"
lspci gives
"01:07.0 Network controller: Ralink corp. Device 3062"

I assume this means I need the 64 bit driver. (driver was copied form 32 bit windows so it is 32 bit) Do you know where I can find it?  OR is there another solution here? thanks in advance

---

### Post by walt.smith1960 on 2011-08-07
Bad Magic indeed.  To use NDISwrapper, you'd need 64 bit **WinXP** drivers.  NDISwrapper only works with XP drivers.   If you can open a terminal and type this "lspci"(lowercase L) you should get a line something like this:
```
Bus 002 Device 003: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]
```This device is USB but the idea is the same.  The above tells us that the wireless adapter's manufacturer is Netgear (I.D. 0846), the device I.D. is 9030 and the chipset is an Atheros AR9271.  I can then look around or ask and find the module that works with that chip set is an Ath9k_htc. You should have something similar.  If you don't recogize your wireless device, post the whole of "lspci" and we'll figure it out.  If you can find the proper module and make sure it's loading and not conflicting with others, your wireless should work.

Edit: if [this]("http://www.wikidevi.com/wiki/CNet_CWP-905") is correct, your device has a Ralink 2760 or 2720 chip.  Ralink seems pretty well supported. It would still be nice to see the results of "lspci" though.

---

### Post by walt.smith1960 on 2011-08-08
> **bobman321123 said:**
> 
lspci gives
"01:07.0 Network controller: Ralink corp. Device 3062"

I assume this means I need the 64 bit driver. (driver was copied form 32 bit windows so it is 32 bit) Do you know where I can find it?  OR is there another solution here? thanks in advance

I think the best solution would be getting it working with a native Linux driver. NDISwrapper is really intended to use when a native driver does not exist for your device and not long ago that was a very common state of affairs. Today drivers  are readily available from Ralink but if you get the Ralink driver, you have to compile it yourself.  I haven't done this successfully so don't claim to be knowledgeable . Linux does come with open source drivers but they can be problematic in that more than one driver loads at the same time and they conflict.

You might try the command "lsmod" and "iwconfig" and post the output.  This will show what modules are being loaded.  Perhaps someone can see what is going on.  If you want/need to use a driver from Ralink, here is what looks like a pretty good tutorial:
[http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/](http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/)

It talks about specific model card but I'd expect the procedure for most Ralink cards to be similar.  Here is a link to Ralink's driver download page. 

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

 The files you need appear to be the 7th line down.  The release notes should have directions on how to install.  The downside to compiling your own drivers is that if you upgrade the Linux Image (kernel) you have to redo the make/install steps.  You could also do a search in the networking & wireless forum using the search term ralink 3062.  Just remember that there are many dead ends and some misinformation in the threads but there may be helpful tips as well.

---

### Post by bobman321123 on 2011-08-08
When I use "lsmod", it gives me:
Module                  Size  Used by
vesafb                 13761  1 
binfmt_misc            17565  1 
snd_hda_codec_via      62470  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
nvidia              10709116  44 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
edac_core              53845  0 
lp                     17825  0 
k10temp                13119  0 
edac_mce_amd           23464  0 
asus_atk0110           17976  0 
snd                    67382  13 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ndiswrapper           249811  0 
ppdev                  17113  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_nforce2            13058  0 
parport_pc             36959  1 
parport                46458  3 lp,ppdev,parport_pc
usbhid                 46956  0 
hid                    91020  1 usbhid
forcedeth              63555  0 
sata_nv                32054  2 
pata_amd               14130  0 


When I type "iwconfig" it says:
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by walt.smith1960 on 2011-08-08
So no open source drivers e.g. rt2800pci are being loaded.  If it were me, I'd uninstall NDISwrapper...WinXP 64 bit drivers are going to be difficult to find.   You could also look in** etc/modprobe.d/blacklist.conf** to see if RT2xxxxx are being blacklisted.  They may have been blacklisted by NDISwrapper, I don't know. Then restart and see if anything with rtxxxxxx shows up in "lsmod".  If not, I don't think you have any choice but to download the Ralink driver, modify the files as directed in the 'readme' file, and proceed as directed.  If you have more money than patience, you could get an adapter known to work out of the box.  Being able to download, compile and install a driver can produce a feeling of accomplishment; it can also produce a feeling of frustration depending on how the process goes.

Again, I've never had to deal with Ralink devices so I'm just saying how I'd go about it if I were you.  Perhaps someone with more experience/knowledge can jump in here.

---

### Post by bobman321123 on 2011-09-16
Thank you, it's now working perfectly. It has some issues with keeping a connection, but I think that may be the card's fault, and not Linux.
Thanks a bunch!

---

