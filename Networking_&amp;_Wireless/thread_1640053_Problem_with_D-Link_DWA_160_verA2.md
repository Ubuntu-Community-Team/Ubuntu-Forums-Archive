---
title: "Problem with D-Link DWA 160 ver:A2"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by jamk on 2010-12-07
Hi,
 
I have installed Ubuntu 10.10 on a 64-bit machine (Intel Xenon 4 core), running in paralell with Windows 7. To access the Wi-Fi, I bought a D-Link DWA160 A2, but it does not run on Ubuntu.
 
I found this, but there seemed to be some problems with access to the the lib-folder.
[http://www.backtrack-linux.org/forums/backtrack-howtos/1042-how-get-ar9170-chipset-usb-adapter-working.html](http://www.backtrack-linux.org/forums/backtrack-howtos/1042-how-get-ar9170-chipset-usb-adapter-working.html)
 
Do you have any solution to this problem.
 
kind regards
John

---

### Post by TBABill on 2010-12-07
What chipset does it have? Does lsusb provide any info on it or just the brand? I have seen some posts that the A2 may use the Ralink driver RT2870 but need to be sure.

---

### Post by xubuntu84 on 2010-12-07
> **TBABill said:**
> What chipset does it have? Does lsusb provide any info on it or just the brand? I have seen some posts that the A2 may use the Ralink driver RT2870 but need to be sure.

kernel.log shows ar9170.  The page he references speaks of the same chipset and lists the DWA-160 as needing updated drivers to work properly.

Output of lsusb:
Bus 001 Device 005: ID 07d1:3a09 D-Link System DWA-160 Xtreme N Dual Band USB Adapter(rev.A2) [Atheros AR9001U-(2)NG]

I have a weird (possibly related) issue:
My card was recognized right away and will let me enter my WPA2 password for my network, then shows me connected.  However, I am not able to get to any web pages.  The log file shows the following:
```
Dec  7 08:41:20 ubuntu-server kernel: [ 5650.286460] phy0: writing reg 0x1c36f0 (val 0x2400) failed
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.285867] usb 1-1.1: no command feedback received (-110).
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.285876] ar9170 cmd: 08 01 00 00 f0 36 1c 00 00 24 00 00              .....6...$..
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.285886] Pid: 2240, comm: phy0 Tainted: P            2.6.35-23-generic #41-Ubuntu
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.285891] Call Trace:
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.285904]  [<ffffffff812c4103>] ? print_hex_dump_bytes+0x33/0x40
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.285917]  [<ffffffffa0dabf9c>] ar9170_usb_exec_cmd+0x20c/0x270 [ar9170usb]
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.285929]  [<ffffffffa0daf41f>] ar9170_write_reg+0x4f/0xb0 [ar9170usb]
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.285941]  [<ffffffffa0db01af>] ar9170_set_slot_time+0x4f/0x60 [ar9170usb]
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.285951]  [<ffffffffa0dad518>] ar9170_op_config+0x68/0xe0 [ar9170usb]
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.285972]  [<ffffffffa0d569d2>] ieee80211_hw_config+0xc2/0x120 [mac80211]
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.285994]  [<ffffffffa0d5b917>] ieee80211_scan_work+0x267/0x340 [mac80211]
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.286016]  [<ffffffffa0d5b6b0>] ? ieee80211_scan_work+0x0/0x340 [mac80211]
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.286025]  [<ffffffff8107a775>] run_workqueue+0xc5/0x1a0
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.286033]  [<ffffffff8107a8f3>] worker_thread+0xa3/0x110
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.286041]  [<ffffffff8107f620>] ? autoremove_wake_function+0x0/0x40
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.286050]  [<ffffffff8107a850>] ? worker_thread+0x0/0x110
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.286057]  [<ffffffff8107f0c6>] kthread+0x96/0xa0
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.286065]  [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.286073]  [<ffffffff8107f030>] ? kthread+0x0/0xa0
Dec  7 08:41:21 ubuntu-server kernel: [ 5651.286081]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
```

I will be attempting the driver update from jamk's post, and will report back.

---

### Post by xubuntu84 on 2010-12-07
I am running into several issues with attempting to follow the link's instructions.

First off: you have to use a newer compat-wireless version (2.6.35-1) instead of the 2.6.32 that is referenced if you are using a newer kernel (ie an up to date Meerkat is 2.6.35.-23ish).

Second: While doing the make install, the entire list of wireless modules said it couldn't be found.  The sequence goes something like this:
```
make install
Your old wireless subsystem modules were left intact:
...
Your old bluetooth subsystem modules were left intact:
...

make -C /lib/modules/2.6.35-23-generic/build M=/home/benmctee/Programs/compat-wireless-2.6.35-1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  Building modules, stage 2.
  MODPOST 97 modules
WARNING: "__tracepoint_iwm_tx_wifi_cmd" [/home/benmctee/Programs/compat-wireless-2.6.35-1/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko] undefined!
WARNING: "__tracepoint_iwm_tx_packets" [/home/benmctee/Programs/compat-wireless-2.6.35-1/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko] undefined!
WARNING: "__tracepoint_iwm_rx_packet" [/home/benmctee/Programs/compat-wireless-2.6.35-1/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko] undefined!
WARNING: "__tracepoint_iwm_rx_ticket" [/home/benmctee/Programs/compat-wireless-2.6.35-1/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko] undefined!
WARNING: "__tracepoint_iwm_rx_nonwifi_cmd" [/home/benmctee/Programs/compat-wireless-2.6.35-1/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko] undefined!
WARNING: "__tracepoint_iwm_rx_wifi_cmd" [/home/benmctee/Programs/compat-wireless-2.6.35-1/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko] undefined!
WARNING: "__tracepoint_iwm_tx_nonwifi_cmd" [/home/benmctee/Programs/compat-wireless-2.6.35-1/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko] undefined!
WARNING: "__tracepoint_iwlwifi_dev_rx" [/home/benmctee/Programs/compat-wireless-2.6.35-1/drivers/net/wireless/iwlwifi/iwlcore.ko] undefined!
WARNING: "__tracepoint_iwlwifi_dev_ioread32" [/home/benmctee/Programs/compat-wireless-2.6.35-1/drivers/net/wireless/iwlwifi/iwlcore.ko] undefined!
WARNING: "__tracepoint_iwlwifi_dev_iowrite32" [/home/benmctee/Programs/compat-wireless-2.6.35-1/drivers/net/wireless/iwlwifi/iwlcore.ko] undefined!
WARNING: "__tracepoint_iwlwifi_dev_iowrite8" [/home/benmctee/Programs/compat-wireless-2.6.35-1/drivers/net/wireless/iwlwifi/iwlcore.ko] undefined!
WARNING: "__tracepoint_iwlwifi_dev_ucode_wrap_event" [/home/benmctee/Programs/compat-wireless-2.6.35-1/drivers/net/wireless/iwlwifi/iwlcore.ko] undefined!
WARNING: "__tracepoint_iwlwifi_dev_hcmd" [/home/benmctee/Programs/compat-wireless-2.6.35-1/drivers/net/wireless/iwlwifi/iwlcore.ko] undefined!
WARNING: "__tracepoint_iwlwifi_dev_ucode_event" [/home/benmctee/Programs/compat-wireless-2.6.35-1/drivers/net/wireless/iwlwifi/iwlcore.ko] undefined!
WARNING: "__tracepoint_iwlwifi_dev_ucode_error" [/home/benmctee/Programs/compat-wireless-2.6.35-1/drivers/net/wireless/iwlwifi/iwlcore.ko] undefined!
WARNING: "__tracepoint_iwlwifi_dev_ucode_cont_event" [/home/benmctee/Programs/compat-wireless-2.6.35-1/drivers/net/wireless/iwlwifi/iwlcore.ko] undefined!
WARNING: "__tracepoint_iwlwifi_dev_tx" [/home/benmctee/Programs/compat-wireless-2.6.35-1/drivers/net/wireless/iwlwifi/iwlcore.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make -C /lib/modules/2.6.35-23-generic/build M=/home/benmctee/Programs/compat-wireless-2.6.35-1 "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'

INSTALL /home/benmctee/Programs/compat-wireless-2.6.35-1/compat/compat.ko

...


DEPMOD  2.6.35-23-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
Updating Ubuntu's initramfs for 2.6.31-wl under /boot/ ...
grep: /boot/config-2.6.31-wl: No such file or directory
WARNING: missing /lib/modules/2.6.31-wl
Device driver support needs thus be built-in linux image!
WARNING: Couldn't open directory /lib/modules/2.6.31-wl: No such file or directory
FATAL: Could not open /lib/modules/2.6.31-wl/modules.dep.temp for writing: No such file or directory
FATAL: Could not load /lib/modules/2.6.31-wl/modules.dep: No such file or directory
...

Will now run update-grub to ensure grub will find the new initramfs ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
depmod will prefer updates/ over kernel/ -- OK!
WARNING: Module /lib/modules/2.6.35-23-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko ignored, due to loop
WARNING: Loop detected: /lib/modules/2.6.35-23-generic/updates/drivers/net/wireless/iwlwifi/iwlcore.ko which needs iwlcore.ko again!
WARNING: Module /lib/modules/2.6.35-23-generic/updates/drivers/net/wireless/iwlwifi/iwlcore.ko ignored, due to loop
WARNING: Module /lib/modules/2.6.35-23-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko ignored, due to loop

Currently detected wireless subsystem modules:
...

Now run:

sudo make unload to unload both wireless and bluetooth modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

And then load the wireless or bluetooth module you need. If unsure reboot.
Alternatively use sudo make load/wlload/btload to load modules

```

I ran make unload, then make load wlload.

Now my wireless is not available as even an option on the menu bar.  I plan to restart and troubleshoot.  If you can tell by my make install output as to what to do, please let us know.

---

### Post by xubuntu84 on 2010-12-07
After a restart, still no luck.  Any ideas?

---

### Post by TBABill on 2010-12-07
[http://linuxwireless.org/en/users/Drivers/ar9170](http://linuxwireless.org/en/users/Drivers/ar9170)

---

### Post by g41m on 2011-04-24
I had problems with usb stick D-Link DWA-160 A2 (ar9170) and ubuntu 10.10 and 11.04. Ubuntu loaded two drivers ar9170usb and carl9170.

What i did was blacklisting ar9170usb in /etc/modprobe.d/blacklist.conf and after that i put carl9170 firmware to directory /lib/firmware/

[http://www.kernel.org/pub/linux/kernel/people/chr/carl9170/fw/1.9.2/carl9170-1.fw]("http://www.kernel.org/pub/linux/kernel/people/chr/carl9170/fw/1.9.2/carl9170-1.fw")

Afrer reboot ubuntu used carl9170 and my usb wlan stick started to work correctly.

---

### Post by two4two on 2011-05-26
In my Ubuntu Studio 10.04 (Lucid) my DWA-160 A2 was included in the kernel as AR9170usb.  It worked out of the box, except it's not very stable.  Periodically it freezes.  When it does so, the access light is stuck on in the USB stick.  It seems as though maybe the driver is "looping".  If I unplug it and replug it it almost always recovers, but it's a pain to have to always do that.  Does the carl9170 have this problem?

---

### Post by nbound on 2011-06-17
it usually autorecovers, ive found though that torrents will cause my connection to hang after a short while. and even cause my router to restart.

edit: ive installed compat-wireless recently and torrenting is much improved!

---

### Post by two4two on 2011-06-21
OK, where do I get the latest carl9170 driver?  I followed some links to compat-wireless and it ended up installing an updated kernel package (Ubuntu Studio 10.4 LTS preempt kernel) and it has the same AR9170USB driver.  I go to the linux-wireless page and it says to install from the test git.  I need better instruction than that.  Anyone have some actual instructions how to disable the old ar9170usb driver and replace with the carl9170 driver?  I have the carl9170 firmware binary, now I need to put it in the right place and install the driver. This is Ubuntu Studio 10.4 LTS.

---

### Post by narcoticfresh on 2011-07-02
It seems this has been "resolved" in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/540827](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/540827) as workaround on Natty..

I just did (i have a d-link dwa160 usb adapter):
rmmod ar9170usb
create a file /etc/modprobe.d/blacklist-local.conf with the content "blacklist ar9170usb"
unplug und re-plug the adapter..

then issue
lsmod | grep ar91
to get sure ar9170usb isn't loaded anymore..

then it worked much more stable after this.. no need for wireless-compat or anything on Natty..

i hope this helps someone..

note: if rmmod complains - first unplug the adapter, then rmmod. if ar9170usb keeps loading, just try to reboot ;)

---

### Post by chili555 on 2011-07-02
Just to clarify, the Natty kernel contains *_both_*:```
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ar9170/[COLOR="Red"]ar9170usb[/COLOR].ko
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/carl9170/[COLOR="Red"]carl9170[/COLOR].ko
```ar9170usb is unstable and disconnects, according to various bug reports and carl9170 is stable. Therefor, as narcoticfresh correctly suggests, blacklist ar9170usb and let carl9170 do the work. 

His method is perfectly valid, but you may also simply add:```
blacklist ar9170usb
``` to /etc/modprobe.d/blacklist.conf.

Thanks for a good find, narcoticfresh.

---

### Post by two4two on 2011-07-08
OK, I have Ubuntu Studio 10.4 LTS, 2.6.32-21.32-preempt.  I didn't like the driver that came with it for my DWA-160 A2 (ar9170usb), so I downloaded compat-wireless from their site.  I got compat-wireless-3.0-rc4-1.  I went thru some research and did the install as per the instructions.  I blacklisted the old driver.  Put the firmware into the firmware directory.  I used carl9170-1.fw (dated: Monday, January 10, 2011, 9:01:42 AM).  It works but disconnects immediately.  I have a file where I put the terminal log from the install and the kernel log of the boot-up where it tries to connect.  I made it a .zip file because of size limit.  Anyone can read and comprehend this?  I need some help with this to get it working.  Thanks all you learned people.

---

### Post by chili555 on 2011-07-08
I am studying your logs. Your version of compat-wireless implies you are running kernel 3.0-rc4. I am sure you are aware that an rc has the possibility of errors or instability.

EDIT:> Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-preemptI wonder if you'd have better luck with a different version of compat-wireless.

EDIT2: I see you have two wireless cards. Are you trying to connect both at once? Is Network Manager alive and running here? I am quite confident that NM will shut down one in preference to the other; poor carl, I assume.

---

### Post by two4two on 2011-07-08
Thanks so much for looking at the logs.  I'm not trying to run both devices at the same time.  I have an old D-link DWL-122 (prism chipset) that worked in an earlier version of Ubuntu, and I tried plugging it in in order to at least get online to do research and download anything to fix the other driver.  Interesting that the prism stick didn't work either and had the very same symptom of seeing the network, associating, and immediately dis-associating.  I don't really care about that device, but it might be useful to know it fails too, because it may be an indicator of a broader problem.  OK, any suggestions on the best version of compat-wireless that has the carl9170 driver and will work on my kernel?  I assume that all I need to do is per their README and "make uninstall", and then install the different version of compat?

---

### Post by chili555 on 2011-07-08
> I have an old D-link DWL-122 (prism chipset)Ahem!> [ 2438.419377] [COLOR="Red"]ath[/COLOR]: EEPROM regdomain: 0x3aIs it actually an Atheros card or do you have *three* cards? In order to get poor carl to work, we ought to blacklist the one(s) that we don't want and evaluate carl's performance afterwards. How about giving me a zipped log with:```
lsmod
```

*Is* NM running?> I assume that all I need to do is per their README and "make uninstall", and then install the different version of compat? Not yet. Let's clear the non-working modules first.

---

### Post by two4two on 2011-07-08
Nope.  Not 3 adapters.  Only the DWA-160 A2 and the DWL-122 prism stick.  I only stuck that DWL-122 in for one boot-up to try to get to the internet but it didn't work either.  There's a wired LAN on this mobo but I do believe I've disabled it in the BIOS.  There was the old ar9170usb driver that's blacklisted.  But here's the lsmod zip file.

---

### Post by chili555 on 2011-07-08
There are no conflicting modules loaded, as far as I can see. As well, my apologies, the module *ath* is required by carl9170. There are far more warnings in your compile then what I got when I compiled the daily version just now. I suggest you do the 'sudo make uninstall' as you previously suggested and then download here to your desktop: [http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball](http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball)

Right click and select Extract Here. Now in a terminal, do:```
cd Desktop/compat
```Press Tab and the rest will fill in; I assume it's compat-wireless-2011-07-08 or similar. If not, post back and we'll sort it out. Next:```
./scripts/driver-select carl9170
make
sudo make install
```Now unload the old non-working version:```
sudo rmmod -f carl9170
```And load the good one:```
sudo modprobe carl9170
```Verify the module installed correctly:```
modinfo carl9170
```The correct, new version is:```
filename:       /lib/modules/2.6.whatever/[COLOR="Red"]updates[/COLOR]/drivers/net/wireless/ath/carl9170/carl9170.ko
alias:          arusb_lnx
alias:          ar9170usb
firmware:       carl9170-1.fw
description:    Atheros AR9170 802.11n USB wireless
license:        GPL
author:         Christian Lamparter <chunkeey@googlemail.com>
author:         Johannes Berg <johannes@sipsolutions.net>
[COLOR="Red"]version:        1:1.9.2[/COLOR]
<snip>

```

---

### Post by two4two on 2011-07-08
OK, I did all that.  It didn't get installed exactly as the docs say it should.  I have the extracted file in my downloads directory and I installed it from there.  But it doesn't work.  I'm attaching a zip file that has: the install log; the kernel log on reboot, and the lsmod after re-boot.  Should I have downloaded a different firmware?  I'm using the same one from the previous install.  And there's a message in the kernel log that says it couldn't find a compatible firmware descriptor.  Thanks for your help.

---

### Post by chili555 on 2011-07-08
> dad@Dad-Stubuntu:~/Downloads/compat-wireless-2011-07-07$ modinfo carl1970
ERROR: modinfo: could not find module carl[COLOR="Red"]1970[/COLOR]Let's see:```
modinfo carl9170
```My compilation shows: > $ modinfo carl9170
filename:       /lib/modules/2.6.38-8-generic/updates/drivers/net/wireless/ath/carl9170/carl9170.ko
alias:          arusb_lnx
alias:          ar9170usb
firmware:       [COLOR="Red"]carl9170-1.fw[/COLOR]
Does it exist?```
$ ls -al /lib/firmware | grep carl
-rw-r--r--  1 root root   12548 2011-04-20 15:27 carl9170-1.fw
```Is it the same version and size? Please try:```
sudo modprobe carl9170
dmesg | tail -n10
```Thanks.

---

### Post by two4two on 2011-07-08
Probably it's my firmware is the wrong stuff.  Where do I get the proper firmware for the compat-wireless version you suggested for me?  See attached file.

---

### Post by chili555 on 2011-07-08
If you have a wired ethernet connection, you can do:```
sudo apt-get install --reinstall linux-firmware
```Check the size again and see if it's -rw-r--r--  1 root root   [COLOR="Red"]12548[/COLOR] 2011-04-20 15:27 carl9170-1.fw. If that doesn't do it, I'll zip mine and send it.

What does lil carl do or not do?

---

### Post by two4two on 2011-07-08
I have my wired lan disabled in the BIOS.  I'm not near a wired outlet.  If you could please zip and send that'd be convenient, but will your firmware from your Natty work in my Lucid?

---

### Post by chili555 on 2011-07-08
> **two4two said:**
> I have my wired lan disabled in the BIOS.  I'm not near a wired outlet.  If you could please zip and send that'd be convenient, but will your firmware from your Natty work in my Lucid?I don't know. I suspect the only way to find out it try it. Rename your firmware so as to save it in case we need it:```
cd /lib/firmware/
sudo mv carl9170-1.fw carl9170-1.bak
```Then right-click and extract my attachment and move it over:```
cd
cd Desktop
sudo mv carl9170-1.fw /lib/firmware
sudo reboot
```Anything new to report?

---

### Post by two4two on 2011-07-08
OK, still no luck.  The firmware is newer, but still not the same level as the driver.  And also, after the replace, the owner is not root; I am the owner.  Could this be the problem now?  See attached file.  I'm logging off for the night and I'll pick it up again tomorrow.  Thanks so much for your help.  :)

---

### Post by chili555 on 2011-07-09
Here is what is said about firmware in the log you sent previously:> Jul  7 22:46:41 Dad-Stubuntu kernel: [ 2438.057425] usbcore: registered new interface driver carl9170

Jul  7 22:46:41 Dad-Stubuntu kernel: [ 2438.076018] usb 1-8: driver   API: 1.9.2 2011-01-22 [1-1]

Jul  7 22:46:41 Dad-Stubuntu kernel: [ 2438.076028] usb 1-8: firmware API: 1.9.0 2010-10-12

Jul  7 22:46:41 Dad-Stubuntu kernel: [ 2438.419377] ath: EEPROM regdomain: 0x3a

Jul  7 22:46:41 Dad-Stubuntu kernel: [ 2438.419384] ath: EEPROM indicates we should expect a direct regpair map

Jul  7 22:46:41 Dad-Stubuntu kernel: [ 2438.419391] ath: Country alpha2 being used: CA

Jul  7 22:46:41 Dad-Stubuntu kernel: [ 2438.419395] ath: Regpair used: 0x3aIt looks pretty happy! It goes on to connect and a few moments later, disassociate. 

This bothers me:> Jul  7 22:46:40 Dad-Stubuntu kernel: [ 2437.690365] Compat-wireless backport release: compat-wireless-v3.0-rc4-1

Jul  7 22:46:40 Dad-Stubuntu kernel: [ 2437.690374] Backport based on linux-2.6-allstable.git v[COLOR="Red"]3.0-rc4[/COLOR]That makes me wonder if the older, seemingly incompatible compat-wireless version is somehow still around. I suggest you try to uninstall it again and re-install the daily build version from a ***freshly extracted*** file. 

I'm starting to not like carl...

---

### Post by two4two on 2011-07-12
After trying many different versions of compat-wireless I finally found the answer.  I simply disabled the ipv6 setting in the configuration.  So, I am using Chilli's fw level and wireless compat-wireless-2.6.39-rc6-1.  It works!  carl9170 working now. :)  Thanks chilli for all you help and hard work.  I am a newbie and you made it all do-able for me.  :)

---

### Post by chili555 on 2011-07-12
Awesome! Now I like carl a lot. The best part, aside from your wireless working, is that you've helped some searchers.

---

### Post by two4two on 2011-07-12
I've helped someone?  How did I do that?  Do you mean the ipv6 thing?  That was the last part.  It was getting the right level and firmware combo that I simply could not get and get it all installed.  So thanks for showing me how to do those things. We all rely on more experienced people like you to help us get things done.  :)

---

### Post by chili555 on 2011-07-13
Well, I think you helped not only with the IPv6 setting, but looking around for the best compat-wireless package and, probably, a bit of perseverance. You might also use Thread Tools at the top to Mark Solved.

---

### Post by two4two on 2011-07-13
Since it's not originally my thread, I don't have the option to mark as resolved, but does everyone agree this thread is resolved?  Can the owner mark it?

---

