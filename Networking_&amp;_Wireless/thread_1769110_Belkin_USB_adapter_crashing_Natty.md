---
title: "Belkin USB adapter crashing Natty"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by meggiedude on 2011-05-27
[FONT=Arial]Hi there,

I have rebuilt an oldish PC for my son with Natty on it. 
I want to use an old Belkin F5D6050 usb adapter to get him on tinternet.

When I first plugged it in it ws not recognised.

I googled this and that to find a fix and loaded  ndisgtk (he ndiswrapper GUI tool).
I then ran that pointing to the .INF file on the Belkin Windows driver CD.
This seemed to load OK.

However when I plug my adapter in now it crashes Ubuntu.
Blank screen of death and lots of text.

Any Help appreciated.[/FONT]

---

### Post by chili555 on 2011-05-27
The two most frequent reasons for crashes in ndiswrapper that I have seen are the .inf is not the XP driver or a native Ubuntu driver is trying to load and interfers. Let's magically determine what's going on *without* plugging the device in. Please open Applications > Accessories > Terminal and run and post:```
ndiswrapper -[COLOR="Red"]l[/COLOR]
dmesg | grep ndis
sudo cat /var/log/syslog | grep ndis | tail -n20
```That's a lower-case L for 'list.' The pipe symbol | is on the right side of my US keyboard on the same key with \.

Here is a snip from *man ndiswrapper-1.9*:> ndiswrapper is two parts: user space tool that is used to install  Windows  XP drivers and kernel module to load the **Windows XP** drivers. Both are called ndiswrapper.

---

### Post by meggiedude on 2011-05-28
> **chili555 said:**
> The two most frequent reasons for crashes in ndiswrapper that I have seen are the .inf is not the XP driver or a native Ubuntu driver is trying to load and interfers. Let's magically determine what's going on *without* plugging the device in. Please open Applications > Accessories > Terminal and run and post:```
ndiswrapper -[COLOR=Red]l[/COLOR]
dmesg | grep ndis
sudo cat /var/log/syslog | grep ndis | tail -n20
```That's a lower-case L for 'list.' The pipe symbol | is on the right side of my US keyboard on the same key with \.

Here is a snip from *man ndiswrapper-1.9*:
Thanks for the  advice.

From a clean boot this is what we get

[COLOR=Blue]> simon@Hark-JR:~$ ndiswrapper -l
netvusbr : driver installed
simon@Hark-JR:~$ dmesg|grep ndis
simon@Hark-JR:~$ sudo cat/var/log/syslog|grep ndis|tail -n20
[sudo] password for simon: 
May 27 20:50:38 Hark-JR kernel: [   21.864682] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
May 27 20:50:39 Hark-JR kernel: [   22.421551] ndiswrapper: driver netvusbr (Belkin,11/01/2001,1.1.2.34) loaded
May 27 20:53:33 Hark-JR kernel: [  196.832064] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat usb_storage uas radeon snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_seq_midi ttm snd_rawmidi drm_kms_helper binfmt_misc snd_seq_midi_event ppdev snd_seq snd_timer drm ndiswrapper(+) snd_seq_device snd joydev i2c_algo_bit serio_raw soundcore ns558 parport_pc gameport snd_page_alloc shpchp sis_agp i2c_sis96x lp parport hid_sunplus hid_belkin usbhid hid sis900 floppy
May 27 20:56:42 Hark-JR kernel: [   17.900895] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
May 27 20:56:43 Hark-JR kernel: [   18.487746] ndiswrapper: driver netvusbr (Belkin,11/01/2001,1.1.2.34) loaded
May 27 20:56:44 Hark-JR kernel: [   19.547595] ndiswrapper (wrap_reset_port:1093): locking failed: -16
May 27 20:59:02 Hark-JR kernel: [   72.828536] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
May 27 20:59:02 Hark-JR kernel: [   73.268440] ndiswrapper: driver netvusbr (Belkin,11/01/2001,1.1.2.34) loaded
May 27 20:59:04 Hark-JR kernel: [   74.300090] ndiswrapper (wrap_reset_port:1093): locking failed: -16
May 27 20:59:07 Hark-JR kernel: [   77.616018] ndiswrapper (wrap_reset_port:1093): locking failed: -16
May 27 20:59:07 Hark-JR kernel: [   77.623216] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
May 27 20:59:07 Hark-JR kernel: [   77.623226] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
May 27 20:59:07 Hark-JR kernel: [   77.623244] ndiswrapper (mp_halt:262): device f40a5440 is not initialized - not halting
May 27 20:59:07 Hark-JR kernel: [   77.623248] ndiswrapper: device eth%d removed
May 27 20:59:07 Hark-JR kernel: [   77.623287] ndiswrapper: probe of 2-2:1.0 failed with error -22
May 27 20:59:07 Hark-JR kernel: [   77.623936] last sysfs file: /sys/bus/pci/drivers/ndiswrapper/uevent
May 27 20:59:07 Hark-JR kernel: [   77.624112] Modules linked in: ndiswrapper(+) snd_intel8x0 radeon snd_ac97_codec ac97_bus snd_pcm snd_seq_midi binfmt_misc snd_rawmidi ttm ppdev drm_kms_helper snd_seq_midi_event snd_seq drm snd_timer snd_seq_device snd joydev i2c_algo_bit serio_raw soundcore ns558 parport_pc shpchp i2c_sis96x gameport sis_agp snd_page_alloc lp parport hid_sunplus hid_belkin usbhid hid floppy sis900
May 27 20:59:07 Hark-JR kernel: [   77.627138]  [<f8308322>] ? ntdriver_thread+0x62/0xa0 [ndiswrapper]
May 27 20:59:07 Hark-JR kernel: [   77.627138]  [<f83082c0>] ? ntdriver_thread+0x0/0xa0 [ndiswrapper]
May 27 20:59:07 Hark-JR kernel: [   77.660838] usbcore: registered new interface driver ndiswrapper[/COLOR]

Cheers

MD

---

### Post by chili555 on 2011-05-28
We're closer but not quite there. May I see:```
ls /etc/ndiswrapper
```Can you please tell me the exact model and version number of your Belkin? Do you recall if you loaded both an .inf file as well as a .sys file?

---

### Post by meggiedude on 2011-05-28
> **chili555 said:**
> We're closer but not quite there. May I see:```
ls /etc/ndiswrapper
```Can you please tell me the exact model and version number of your Belkin? Do you recall if you loaded both an .inf file as well as a .sys file?

Lo again Chili, Thanks for your help here.
The adapter is a Belkin F5D6050.
I've aways ever used it on a windows system before with WEP security. This time I will be linking it to a WPA network. I don't know if that males a difference or not. This adapter was bought before the WPA standard was commonly used.

I used the ndisgk uility which I believe frontends ndiswrapper.
This only asked for the .INF file, which I supplied from the orig driver CD.

ls -algR of /etc/ndiswrapper gives:

> [COLOR=Blue]/etc/ndiswrapper:
total 20
drwxr-xr-x   3 root  4096 2011-05-27 20:43 .
drwxr-xr-x 134 root 12288 2011-05-28 20:41 ..
drwxr-xr-x   2 root  4096 2011-05-27 20:43 netvusbr

/etc/ndiswrapper/netvusbr:
total 92
drwxr-xr-x 2 root  4096 2011-05-27 20:43 .
drwxr-xr-x 3 root  4096 2011-05-27 20:43 ..
-rw-r--r-- 1 root   594 2011-05-27 20:43 0D5C:A002.F.conf
-rw-r--r-- 1 root  8241 2011-05-27 20:43 netvusbr.inf
-rw-r--r-- 1 root 69632 2011-05-27 20:43 vnetusbr.sys[/COLOR]So it looks like it created the .sys from the .INF file??

Cheers

MD

---

### Post by chili555 on 2011-05-28
Ahh! That's what I wanted!> -rw-r--r-- 1 root 594 2011-05-27 20:43 [COLOR="Red"]0D5C:A002[/COLOR].F.confThat's the usb.id for your device which is claimed by a native driver with the odd, convoluted name *at76c50x-usb*. It may be that it's trying to load and conflicting with your ndiswrapper install. It probably didn't drive your device out of the box because of missing firmware, a condition that Dr. Chili can easily cure. Let's try to fix the conflict by blacklisting the native driver. Please do:```
sudo su
echo "blacklist at76c50x-usb" >> /etc/modprobe.d/blacklist.conf
exit
```Next we need to be sure you have the XP .inf file and not ME, 95, 7 or something else. You can find out by reading the .inf file:```
less /etc/ndiswrapper/netvusbr/netvusbr.inf
```It ought to make clear reference to XP or to 2000/XP. The 'less' command allows you to scroll back and forth with the arrow keys. Is it XP?> So it looks like it created the .sys from the .INF file??ndiswrapper ingeniously grabs the .sys file if it needs it without human intervention. Crazy, eh?> This time I will be linking it to a WPA network. I don't know if that males a difference or not. This adapter was bought before the WPA standard was commonly used.Your adapter probably supports WPA but we'll check once we have it running correctly.```
sudo iwlist wlan0 auth
```If it does WPA, it will tell you something like:> wlan0     Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMPAfter you do the blacklist and determine that you have the XP .inf file, reboot and insert the device and see if it black-screens.

---

### Post by meggiedude on 2011-05-30
> **chili555 said:**
> Ahh! That's what I wanted!That's the usb.id for your device which is claimed by a native driver with the odd, convoluted name *at76c50x-usb*. It may be that it's trying to load and conflicting with your ndiswrapper install. It probably didn't drive your device out of the box because of missing firmware, a condition that Dr. Chili can easily cure. Let's try to fix the conflict by blacklisting the native driver. Please do:```
sudo su
echo "blacklist at76c50x-usb" >> /etc/modprobe.d/blacklist.conf
exit
```Next we need to be sure you have the XP .inf file and not ME, 95, 7 or something else. You can find out by reading the .inf file:```
less /etc/ndiswrapper/netvusbr/netvusbr.inf
```It ought to make clear reference to XP or to 2000/XP. The 'less' command allows you to scroll back and forth with the arrow keys. Is it XP?ndiswrapper ingeniously grabs the .sys file if it needs it without human intervention. Crazy, eh?Your adapter probably supports WPA but we'll check once we have it running correctly.```
sudo iwlist wlan0 auth
```If it does WPA, it will tell you something like:After you do the blacklist and determine that you have the XP .inf file, reboot and insert the device and see if it black-screens.

Hi again Doc Chili,

Bad news I'm afraid. Blacklisted that device driver to the blacklist.conf file (and confirmed it appended the file OK)
Rebooting still causes he same behavior unfortunately :( 

BTW, The netvusbr.inf file is the XP one by the looks of things.

Is the at76c50x-usb driver the right one to blacklist or should I try another??
Also is there any way I can post the right error msg to this forum so you can see where its all going wrong?

Cheers

MD

---

### Post by chili555 on 2011-05-30
> Is the at76c50x-usb driver the right one to blacklist or should I try another??It is correct. Drivers have alias files so they recognize and drive one and only one device, although there are a very few exceptions. That is, devices that are claimed by two drivers and blacklisting is required.

at76c50x-usb is correct for your device:```
$ modinfo at76c50x-usb | grep A002
alias:          usb:v[COLOR="Red"]0D5C[/COLOR]p[COLOR="Red"]A002[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```> Also is there any way I can post the right error msg to this forum so you can see where its all going wrong?Can you copy and paste it into a text document and save it to a USB key so we can see it? Can you take a camera phone picture of it and post it here? Can you take a screenshot (Applications > Accessories > Take Screenshot)? Can you just write it down?

Another avenue to consider is to remove ndiswrapper and get the native driver and firmware going.

---

### Post by meggiedude on 2011-05-30
> **chili555 said:**
> It is correct. Drivers have alias files so they recognize and drive one and only one device, although there are a very few exceptions. That is, devices that are claimed by two drivers and blacklisting is required.

at76c50x-usb is correct for your device:```
$ modinfo at76c50x-usb | grep A002
alias:          usb:v[COLOR="Red"]0D5C[/COLOR]p[COLOR="Red"]A002[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```Can you copy and paste it into a text document and save it to a USB key so we can see it? Can you take a camera phone picture of it and post it here? Can you take a screenshot (Applications > Accessories > Take Screenshot)? Can you just write it down?

Another avenue to consider is to remove ndiswrapper and get the native driver and firmware going.

As requested - here is a digi pic for you:

[IMG]http://farm4.static.flickr.com/3062/5777675155_a2bd843f6f_b.jpg[/IMG]

This is the black screen text almost immediately after inserting the usb lead connected to the belkin unit.

Cheers,

MD

---

