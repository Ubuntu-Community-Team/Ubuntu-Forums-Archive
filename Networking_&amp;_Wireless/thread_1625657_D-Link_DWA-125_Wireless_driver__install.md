---
title: "D-Link DWA-125 Wireless driver  install"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by hodad on 2010-11-19
I've been through countless pages over the past two days, and have tried many different paths, so please have patience with my request. I've gone thru all of the posts on this problem, but the problem is that each one leads to a dead end at some point in the coding, and I can't figure out how to proceed.  The Wireless Networking help page is a good start, but no help because it is not specific enough when the problem diverges from the text.

I've downloaded the latest Ralink driver, and unpacked it OK.   I modified the Makefile and Config.mak as near as I can tell.  I then run "sudo make", and it runs, but with error messages.  I "grep" (which I assume means search) for RT2870.*, but nothing happens (no listing).  When I do "iwconfig", I get "eth0 - no wireless extensions". lsusb shows that the D-Link device is recognized on the usb port.

Under the GUI  - Admin - Netowrk Tools- Devices, I show "looback interface" and "Ehternet Interface", but no wireless.  I "added" wireless on that page to no avail.

Any help on how to get thru this would be greatly appreciated!   Will check back tonight or tommorrow morning, as I have to work on my car today :-(

---

### Post by chili555 on 2010-11-19
With a little fiddling, the native rt2870sta driver should support your device. First, we need to know the usb.id. Please post the part of *lsusb* that relates to your device.

---

### Post by hodad on 2010-11-19
*********:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 07d1:3c16 D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2010-11-19
Here is your device:> Bus 001 Device 003: ID 07d1:3c16 D-Link System Please remove the device and amend these files to reflect your usb.id:```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c16", RUN+="/sbin/modprobe -qba rt2870sta"
```Proofread twice, save and close gedit.```
sudo gedit /etc/modprobe.d/network_drivers.conf

```Add one long line:```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "07d1 3c16" > /sys/bus/usb/drivers/rt2870/new_id
```Proofread twice, save and close gedit. Re-insert the device and run:```
iwconfig
```Do you now have a wireless interface? Can you click the Network Manager icon and connect?

---

### Post by hodad on 2010-11-19
REsults:

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by chili555 on 2010-11-19
Let's have a look at:```
sudo modprobe rt2870sta 
dmesg | grep -i rt2
```Thanks.

---

### Post by hodad on 2010-11-19
desktop:~$ sudo modprobe rt2870sta
[sudo] password for dave: 
desktop:~$ dmesg | grep -i rt2
[   10.929131] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   10.932922] usbcore: registered new interface driver rt2870

---

### Post by chili555 on 2010-11-19
> [ [COLOR="Red"]10.932922[/COLOR]] usbcore: registered new interface driver rt2870Wow! That's very early in the boot process, suggesting it was loaded before we started writing files. I hope it's not the defective version you couldn't properly compile. Please post:```
lsmod | grep -e rt2 -e rt3
modinfo rt2870sta | grep version
```Could you please try a reboot before you run these tests?

---

### Post by hodad on 2010-11-19
Rebooted, then result:
desktop:~$ lsmod | grep -e rt2 -e rt3
rt2870sta             525366  0 
desktop:~$ modinfo rt2870sta | grep version
version:        2.0.1.0
srcversion:     169A56F8E0E6AA9C2B2FD02
vermagic:       2.6.32-25-generic SMP mod_unload modversions

---

### Post by chili555 on 2010-11-20
Dr. Chili snaps on his latex gloves; it's time to do a full diagnostic work-up. We are going to create a zip document that I and others can examine to find out why this won't spring to life. In a terminal, please do:```
dmesg > hodad.txt
ifconfig >> hodad.txt
lsmod >> hodad.txt
ls /etc/Wireless/RT2870STA/ >> hodad.txt
ls /lib/firmware | grep -i rt2 >> hodad.txt
zip hodad.zip hodad.txt
```You will find a file in your home directory called hodad.zip. Please attach it to your reply using the little paperclip above the reply box.

---

### Post by hodad on 2010-11-20
Not sure if it got thru, her it is again:

---

### Post by hodad on 2010-11-20
I sent  the zip file, but don't see it in the "queue", so let me know if it didn't go thru...

---

### Post by chili555 on 2010-11-20
The dmesg part didn't work. Please delete the hodad.txt and hodad.zip files, detach the ethernet cable, wait 60 seconds and run all this again. Post back and I'll be waiting.

So far, it looks just perfect. It's my favorite problem, it looks just perfect, except it doesn't work...

---

### Post by hodad on 2010-11-20
Here it is...

---

### Post by chili555 on 2010-11-20
Still no dmesg. Please try:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```Thanks.

---

### Post by hodad on 2010-11-20
attached...

---

### Post by chili555 on 2010-11-20
I see two issues:> [    0.662716] ACPI Error (psargs-0359): [ECEN] Namespace lookup failure, AE_NOT_FOUND
[    0.662721] ACPI Error (psparse-0537): Method parse/execution failed [\] (Node ffffffff81a0b040), AE_NOT_FOUND
[    0.662800] ACPI Error (dswload-0781): [PRID] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.662803] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20090903/psloop-230)
[    0.662807] ACPI Error (psparse-0537): Method parse/execution failed [\] (Node ffffffff81a0b040), AE_ALREADY_EXISTS
[    0.662810] ACPI: Marking method \___ as Serialized because of AE_ALREADY_EXISTS errorThis seems to be the subject of a known bug: [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/551654](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/551654)

I am not sure it has anything to do with initializing your USB device, but it is suspect. I notice there is an ACPI driver loaded for your laptop and I winder if it is misbehaving. Please do:```
sudo rmmod -f rt2870sta
sudo rmmod asus_atk0110
sudo modprobe rt2870sta
iwconfig
```Any improvement?

I also see:> [   10.869746] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   10.869748]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   10.869749]  (Note that use of the override may cause unknown side effects.)I believe this is trivial; almost no desktop computers (i.e. not servers) need ECC.

I also suggest you double-check the wording in the files we created.

---

### Post by hodad on 2010-11-20
Results of first part:

desktop:~$ sudo rmmod -f rt2870sta
[sudo] password for dave: 
dave@girls-desktop:~$ sudo rmmod asus_atk0110
dave@girls-desktop:~$ sudo modprobe rt2870sta
dave@girls-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

desktop:~$

---

### Post by hodad on 2010-11-20
Second part:

Do you want me to repeat steps from the beginning of this thread? No problem trying it if you think it would help...

---

### Post by hodad on 2010-11-20
Went ahead and cracked open a linux book I have on the shelf that explains kernal issues, so I'm getting a better feel for what you're up to, so at least I can follow what's going on.    Looks like we removed the previously installed driver "module", and are ready to re-install (?). I also went thru the syntax of the lines added to the files we created at the start of this thread, and they were correct...

---

### Post by chili555 on 2010-11-20
Nope. We modified the driver module to recognize the usb.id for your device. Google tells us that rt2870sta is appropriate for your device: [http://wiki.debian.org/rt2870sta](http://wiki.debian.org/rt2870sta)> --- snip ---
USB: 07D1:3C0F D-Link System AirPlus G DWL-G122 Wireless Adapter(rev.E) [Ralink RT2870]
USB: 07D1:3C11 D-Link System DWA-160 Xtreme N Dual Band USB Adapter(rev.B) [Ralink RT2870]
USB: [COLOR="Red"]07D1:3C16 D-Link System DWA-125[/COLOR] Wireless N 150 Adapter(rev.A2) [Ralink RT2870]
USB: 07D1:3C17 D-Link System (Device name unknown)
--- snip --However, the module in Ubuntu 10.10 and earlier does not recognize the usb.id:```
chili@LAPTOP60:~$ modinfo rt2870sta | grep -i 3c16
chili@LAPTOP60:~$ 
```When there is no output, that means the file does *not* contain the text. Therefor, we wrote two files to try to force the driver to recognize the usb.id. We know it works from several other instances: [http://ubuntuforums.org/showthread.php?t=1434630](http://ubuntuforums.org/showthread.php?t=1434630)

I am frankly scratchin' my old gray beard trying to figure this one out.

May I see:```
cat /etc/modules
```If rt2870sta is in there, please remove it and reboot. Please give me a good report.

---

### Post by hodad on 2010-11-20
Result:

desktop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

---

### Post by hodad on 2010-11-22
Should I start from the beginning again, and, if so, what thread should I follow and where in that thread do you suggest I begin?  I might have missed a step, or made a mistake somewhere...

---

### Post by chili555 on 2010-11-22
Please let us see:```
cat /etc/udev/rules.d/network_drivers.rules
cat /etc/modprobe.d/network_drivers.conf
```Thanks.

---

### Post by hodad on 2010-11-22
Results:

desktop:~$ cat /etc/udev/rules.d/network_drivers.rules
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c16", RUN+="/sbin/modprobe -qba rt2870sta"
dave@girls-desktop:~$ cat /etc/modprobe.d/network_drivers.conf
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "07d1 3c16" > /sys/bus/usb/drivers/rt2870/new_id

---

### Post by chili555 on 2010-11-22
Please open:```
sudo tail -f /var/log/messages
```Leave the terminal open as you remove the device from the USB slot, count to twenty and reinsert it. New messages should appear in the terminal. Please post them.

The files you created look perfect.

---

### Post by hodad on 2010-11-22
thE FIRST TIME i PLUGGED IT BACK IN, DIDN'T GET A RESPONSE, SO i UNPLUGGED/PLGGED AGAIN, AND THEN IT RECOGNIZED IT.

RESULT:

desktop:~$ sudo tail -f /var/log/messages
[sudo] password for dave: 
Nov 22 08:52:34 girls-desktop kernel: [    9.491721] type=1505 audit(1290441154.692:8):  operation="profile_replace" pid=899 name="/usr/lib/connman/scripts/dhclient-script"
Nov 22 08:52:34 girls-desktop kernel: [    9.493908] type=1505 audit(1290441154.692:9):  operation="profile_load" pid=900 name="/usr/bin/evince"
Nov 22 08:52:34 girls-desktop kernel: [    9.496434] type=1505 audit(1290441154.692:10):  operation="profile_load" pid=900 name="/usr/bin/evince-previewer"
Nov 22 08:52:34 girls-desktop kernel: [    9.498029] type=1505 audit(1290441154.692:11):  operation="profile_load" pid=900 name="/usr/bin/evince-thumbnailer"
Nov 22 08:52:34 girls-desktop kernel: [    9.540381] r8169: eth0: link up
Nov 22 08:52:34 girls-desktop kernel: [    9.540388] r8169: eth0: link up
Nov 22 08:52:36 girls-desktop kernel: [   11.751463] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov 22 08:52:41 girls-desktop pulseaudio[1230]: ratelimit.c: 5 events suppressed
Nov 22 08:54:12 girls-desktop pulseaudio[1470]: ratelimit.c: 16 events suppressed
Nov 22 09:07:19 girls-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="854" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Nov 22 09:37:07 girls-desktop kernel: [ 2686.594525] usb 1-2: USB disconnect, address 2
Nov 22 09:37:37 girls-desktop kernel: [ 2717.500075] usb 1-3: new high speed USB device using ehci_hcd and address 3
Nov 22 09:37:38 girls-desktop kernel: [ 2717.667911] usb 1-3: configuration #1 chosen from 1 choice
Nov 22 09:37:56 girls-desktop kernel: [ 2735.581476] usb 1-3: USB disconnect, address 3
Nov 22 09:38:09 girls-desktop kernel: [ 2749.050926] usb 1-3: new high speed USB device using ehci_hcd and address 4
Nov 22 09:38:09 girls-desktop kernel: [ 2749.217954] usb 1-3: configuration #1 chosen from 1 choice
q

---

### Post by hodad on 2010-11-22
Assuming we're starting from scratch, how do I download the proper driver (since I don't want to re-use what I had before, which I downloaded from D-Link website)?

---

### Post by hodad on 2010-11-22
I've been looking thru all of the threads and links all morning, and they all pick up after the driver has been downloaded and installed.  I want to start out right by getting the proper driver, but I'm "gun shy" at this point (at 4 days and counting).  I guess I'll go back to the D-Link site again...

---

### Post by hodad on 2010-11-22
Downloaded the 2010_0709_RT2870_Linux_STA_v2.4.0.1.tar.bz2 file from Ralink, and extracted it.  I assume that I do "sudo make", and then "sudo make-install" now, so that's what I'll try...

---

### Post by chili555 on 2010-11-22
If you are running the latest kernel version, 2.6.35-22, I believe, the latest Ralink version should work perfectly. Make sure you have build-essential and linux-headers-generic installed.

Read and follow the instructions in the README.

Post back and let us know how you get along.

---

### Post by hodad on 2010-11-22
Downloaded and unpacked.

rEAD THRU INSTRUCTIONS (readme STA) and it says:
3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.

Don't know what they're talking about (?).  I had already ru "make", so do I have to backup somehow?

---

### Post by chili555 on 2010-11-22
You can skip all that. How about this:> ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	  Also, check in usb_main_dev.c to see if your device appears: 07d1:3c16. If not, we can add it.

If you make these changes, start clean:```
make clean
make
sudo make install
```

---

### Post by hodad on 2010-11-22
Also not sure what to do with this instruction:

6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

I went to the subdirectory /os/linux, but saw no "/sbin/insmod rt2870sta.o".  I tyed it in anyway, and it gave an error message.

---

### Post by hodad on 2010-11-22
In answer to post #33, I already checked that when I downloaded a few days ago, and it was already done; but I'll double -check now...

---

### Post by chili555 on 2010-11-22
> **hodad said:**
> Also not sure what to do with this instruction:

6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

I went to the subdirectory /os/linux, but saw no "/sbin/insmod rt2870sta.o".  I tyed it in anyway, and it gave an error message.Skip it. Our friend Network Manager will do it for us.

---

### Post by chili555 on 2010-11-22
> **hodad said:**
> In answer to post #33, I already checked that when I downloaded a few days ago, and it was already done; but I'll double -check now...Including usb_main_dev.c ??

---

### Post by hodad on 2010-11-22
You were right (of course), had to change "N" to "y" in the two lines.

Looked in the usb dev main.c file and it had:
if (dev->descriptor.idVendor == 0x07D1)
    	{
		if (dev->descriptor.idProduct == 0x3C0F)

I will go ahead and do the instructions for compiling now...

---

### Post by hodad on 2010-11-22
Did the "make" etc lines.  What now?

---

### Post by chili555 on 2010-11-22
Reboot, detach the ethernet cable and tell us you are connected!

---

### Post by hodad on 2010-11-22
Nope...

I unhooked the ehternet, and rebooted... still no lights a flashin'   I then did lsusb and the device is still listed as 07d1:3c16, tho.

---

### Post by chili555 on 2010-11-22
Please do:```
sudo modprobe rt2870sta
dmesg | grep rt2
```Thanks.

---

### Post by hodad on 2010-11-22
Result:

desktop:~$ sudo modprobe rt2870sta
[sudo] password for dave: 
desktop:~$ dmesg | grep rt2
[   11.939745] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   11.943760] usbcore: registered new interface driver rt2870
desktop:~$

---

### Post by chili555 on 2010-11-22
I don't think we're any further ahead than we were with the native driver. Please let me see:```
modinfo rt2870sta | grep -e 3C16 -e version
```Are you quite sure the device is not faulty?

---

### Post by chili555 on 2010-11-22
> **hodad said:**
> You were right (of course), had to change "N" to "y" in the two lines.

Looked in the usb dev main.c file and it had:
if (dev->descriptor.idVendor == 0x07D1)
    	{
		if (dev->descriptor.idProduct == 0x[COLOR="Red"]3C0F[/COLOR])

I will go ahead and do the instructions for compiling now...Isn't your device 3C16?

---

### Post by hodad on 2010-11-22
Does the fact that "grep" doesn't find anything mean something?

---

### Post by hodad on 2010-11-22
Oops, missed your earlier post


Yes, it's 3c16

---

### Post by hodad on 2010-11-22
Also, yes the device is good I think.  WE were using it for several months on the girl's pc before I upgraded their motherboard last week.  Also, it's picking it up on the usb port, so I assume it's good (?)

---

### Post by hodad on 2010-11-22
Now you've got me wondering...

Could it still pick up the vendor:product id if it was bad?   Haven't seen it flash it's light even once on the new pc; so maybe something burned it out.

Another idea - could the usb port simply not be recognized as a comm port?  I still get "no woreless extensions" when I do iwconfig...

---

### Post by hodad on 2010-11-22
Sorry, getting ahead of myself

Result:

desktop:~$ modinfo rt2870sta | grep -e 3C16 -e version
version:        2.0.1.0
srcversion:     169A56F8E0E6AA9C2B2FD02
vermagic:       2.6.32-25-generic SMP mod_unload modversions

---

### Post by hodad on 2010-11-22
Just noticed something:

My kernal is 2.4, and the last statement mentioned 2.6, can that be an issue?

---

### Post by hodad on 2010-11-22
Sorry, my bad, I have kernal ver. 2.6.35-25

---

### Post by asvravi on 2010-11-22
I had the same wireless adapter. Got it working in under 5 minutes by copying over the driver files from the CD that came with it, and using ndiswrapper and ndisgtk.

---

### Post by hodad on 2010-11-22
I just had a revelation...

I truly appreciate all you have done for me in the past 5 days, but...

5 days of troubleshooting is enough for me.

I think I'll use the boot method on this thing (as in, crush it with my...)

Is there another wireless card of which you are aware that will work for people who don't have much luck getting things to work in Ubuntu?  THe hardware compatability list just doesn't work (I checked it before buying this thing, and it recommended Ralink-based products).

---

### Post by chili555 on 2010-11-22
> **hodad said:**
> Sorry, my bad, I have kernal ver. 2.6.35-25I don't think so:> desktop:~$ modinfo rt2870sta | grep -e 3C16 -e version
version: 2.0.1.0
srcversion: 169A56F8E0E6AA9C2B2FD02
vermagic: 2.6.[COLOR="Red"]32[/COLOR]-25-generic SMP mod_unload modversionsI don't think your install went well. This says your version is 2.0.1.0. However, you downloaded:> Downloaded the 2010_0709_RT2870_Linux_STA_v[COLOR="Red"]2.4.0.1[/COLOR].tar.bz2 file from RalinkLet's backtrack.```
cd Desktop/RalinkDirectory
```Substitute the actual location you downloaded and extracted the file. Navigate to the location of the usb_main_dev.c file:```
cd wherever/whatever
gedit usb_main_dev.c
```It should have a list of usb.ids. Add one to the list:```
{USB_DEVICE(0x07D1,0x3C16)}, /* Dlink 125 */
```It should follow the format already in the file; please correct it, or ask, if I have mis-typed. Proofread, save and close gedit. Now do:```
cd Desktop/RalinkDirectory
```Substitute the actual location you downloaded and extracted the file. Do:```
make clean
make
sudo make install
```Note any errors and report them.```
sudo rmmod -f rt2870sta
sudo modprobe rt2870sta
modinfo rt2870sta | grep version
```Is the version 2.4.0.1? Any blinking??

---

### Post by chili555 on 2010-11-22
> **hodad said:**
> I just had a revelation...

I truly appreciate all you have done for me in the past 5 days, but...

5 days of troubleshooting is enough for me.

I think I'll use the boot method on this thing (as in, crush it with my...)

Is there another wireless card of which you are aware that will work for people who don't have much luck getting things to work in Ubuntu?  THe hardware compatability list just doesn't work (I checked it before buying this thing, and it recommended Ralink-based products).Not so fast! Please try my post just above.

---

### Post by hodad on 2010-11-22
Sorry, but I can't find the right place to insert the id in the usb_main_dev.c file.  There are hundreds of lines of code, and I can't find anything about usb id's.

---

### Post by chili555 on 2010-11-22
Downloading now, brb.

---

### Post by chili555 on 2010-11-22
Oops! It's rtusb_dev_id.c. It's in the directory called common. Please see attached. Proofread carefully before you press save and close gedit.

---

### Post by hodad on 2010-11-22
Modified the file, and then compiled. No blinking, unfortunately (but will reboot while awaiting your reply)

Result (partial):

desktop:~/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1$ sudo make install
make -C /home/dave/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/dave/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/dave/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.32-25-generic
make[1]: Leaving directory `/home/dave/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux'
dave@girls-desktop:~/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1$ sudo rmmod -f rt2870sta
dave@girls-desktop:~/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1$ sudo modprobe rt2870sta
dave@girls-desktop:~/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1$ sudo modprobe rt2870sta
dave@girls-desktop:~/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1$ modinfo rt2870sta | grep version
version:        2.0.1.0
srcversion:     169A56F8E0E6AA9C2B2FD02
vermagic:       2.6.32-25-generic SMP mod_unload modversions

---

### Post by chili555 on 2010-11-22
I couldn't even get past 'make' without errors. Are you sure it built OK for you?> make[2]: *** [/home/chili/hodad/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/chili/hodad/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2


---

### Post by hodad on 2010-11-22
I had the same errors, but then I did "sudo" make, and ,as I recall, I lost the errors (as I recall, but I unfortunatley wiped "terminal" when I rebooted a few minutes ago).

---

### Post by chili555 on 2010-11-22
> **hodad said:**
> I had the same errors, but then I did "sudo" make, and ,as I recall, I lost the errors (as I recall, but I unfortunatley wiped "terminal" when I rebooted a few minutes ago).Try again.```
cd Desktop/2010whatever
sudo su
make clean
make 
make install
exit
```Any errors?

---

### Post by hodad on 2010-11-22
I didn't get the errors you mentioned previously, but there were about 30 or so "warnings"

---

### Post by hodad on 2010-11-22
THis couldn't be a hardware related problem, could it?  I have an AMD processor and an Asus motherboard.  Maybe the USB port just isn't communicating (in other words, could the ralink driver not support AMD processors for some reason?)

---

### Post by chili555 on 2010-11-22
So now what does this tell us:```
modinfo rt2870sta | grep version
```I am reaching for my tanto...

---

### Post by hodad on 2010-11-22
REsult:

desktop:~/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1$ modinfo rt2870sta | grep version
version:        2.0.1.0
srcversion:     169A56F8E0E6AA9C2B2FD02
vermagic:       2.6.32-25-generic SMP mod_unload modversions

---

### Post by chili555 on 2010-11-22
> **hodad said:**
> THis couldn't be a hardware related problem, could it?  I have an AMD processor and an Asus motherboard.  Maybe the USB port just isn't communicating (in other words, could the ralink driver not support AMD processors for some reason?)Let's check:```
sudo lsusb -vv
```Errors or warnings? It should produce lots of juicy data and no funny business.

---

### Post by hodad on 2010-11-22
I'm reaching for my credit card...

---

### Post by hodad on 2010-11-22
Result:

  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc016 M-UV69a/HP M-UV96 Optical Wheel Mouse
  bcdDevice            3.40
  iManufacturer           1 Logitech
  iProduct                2 Optical USB Mouse
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.32-25-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:13.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        2 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0303 lowspeed power enable connect
   Port 3: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.32-25-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:12.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        2 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.32-25-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:12.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        2 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 002: ID 07d1:3c16 D-Link System 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x07d1 D-Link System
  idProduct          0x3c16 
  bcdDevice            1.01
  iManufacturer           1 Ralink
  iProduct                2 11n Adapter
  iSerial                 3 1.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           67
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              450mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           7
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.32-25-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:13.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0503 highspeed power enable connect
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.32-25-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:12.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

---

### Post by chili555 on 2010-11-22
It all looks pretty normal, actually. I wonder if we have method #1 fighting method #2. Please do:```
sudo mv /etc/udev/rules.d/network_drivers.rules /etc/udev/rules.d/network_drivers.rules.bak
sudo mv /etc/modprobe.d/network_drivers.conf /etc/modprobe.d/network_drivers.conf.bak
```Reboot and report, please.

---

### Post by hodad on 2010-11-22
Looks like the usb port recognizes this little devil, because it retrieves all ofthe mfr's data.   Could it be some function other than the driver that's blocking communications to/from the little bugger?

---

### Post by hodad on 2010-11-22
...unplugged ethernet cable, powered down and up:

zero/zilch/nada!

back on ethernet now.

---

### Post by hodad on 2010-11-22
DOing some reading on the Ubuntu manual:

I looked into the modprobe.conf file and it's empty.   Shouldn't this file contain a reference to the driver?

---

### Post by chili555 on 2010-11-22
If the device properly reports its usb.id and the driver grabs it, it's unnecessary. Sometimes the system gets lazy and it's needed. Check with:```
lsmod | grep rt2
dmesg | grep rt2
```

---

### Post by hodad on 2010-11-22
Result:

desktop:~$ lsmod | grep rt2
rt2870sta             525366  0 
dave@girls-desktop:~$ dmesg | grep rt2
[ 2181.921478] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 2181.933186] usbcore: registered new interface driver rt2870


The boss (wife) and kids just got home, so will be checking out for a while.  I'll look for any responses or ideas later this evening.  Thanks for your help so far, I know it's been a pain...

---

### Post by punck on 2010-11-23
Hi, guys! I have the same problem.

I hope you can figure this out.

Good luck!

---

### Post by hodad on 2010-11-23
Stay tuned!

---

### Post by hodad on 2010-11-23
Question: Could there be some other parameter in one of those ".c" files (in /common or elsewhere) that bind the device to the usb port?  The little bugger is returning data to the port, so we know it's alive and communicating in both directions (I think; unless that info is coming from the driver???).  But it doesn't get any "com" related commands (assuming my theory is correct).

However, I did try taking the device to another pc, and it didn't even register when I plugged it into a usb port (so maybe it is dead?).

---

### Post by chili555 on 2010-11-23
> However, I did try taking the device to another pc, and it didn't even register when I plugged it into a usb port (so maybe it is dead?).Windows or Linux? If it doesn't ever register in any computer, even Windows ("New hardware found") then I think it is deceased.

---

### Post by hodad on 2010-11-23
It was another linux box.  I just tried it again.  This time, I plugged the bugger into the usb port, and powered up the pc. I kept my eye on the bugger through the boot up process, and didn't see lights a flashin'. 

However, I then brought up the system log, and unplugged, plugged in - system log saw it happen.  THen I ran lsusb, which showed D-Link 07d1:3c16 on usb-004.  Doesn't this mean that the bugger is at least sending it's ID?  Which, of course, means it's at least SOMEWHAT alive?

---

### Post by chili555 on 2010-11-23
It means exactly that, but the driver never gets beyond loading. You can load any driver you want but it doesn't mean it drives the device. Here is the last part of my /var/log/messages when I modprobed rt2870sta:> Nov 23 11:28:13 LAPTOP60 kernel: [182885.596191] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
Nov 23 11:28:13 LAPTOP60 kernel: [182885.603574] rtusb init --->
Nov 23 11:28:13 LAPTOP60 kernel: [182885.604417] usbcore: registered new interface driver rt2870Not really any different from yours. I don't own the device; in fact, there is nothing at all plugged in to my USB port at the moment!

I am mystified as to why you compiled version 2.4.0.1 and your version still shows as:> desktop:~/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1$ modinfo rt2870sta | grep version
version: [COLOR="Red"]2.0.1.0[/COLOR]
srcversion: 169A56F8E0E6AA9C2B2FD02
vermagic: 2.6.32-25-generic SMP mod_unload modversionsI am very seldom bamboozled, but this may be my day!

---

### Post by hodad on 2010-11-23
Should I try starting from scratch, or should I try downloading the tarball from the same source as you?  THe file I downloaded was from the Ralink site, and is named

 2010_0709_RT2870_Linux_STA_STA_v2.4.0.1.tar.bz2  628.6 KB

Maybe there some parameters that I didn't customize after decompressing?

---

### Post by chili555 on 2010-11-23
> make[2]: *** [/home/chili/hodad/[COLOR="Red"]2010_0709_RT2870_Linux_STA_v2.4.0.1[/COLOR]/os/linux/../../common/cmm_mac_usb.o] Error 1That's exactly the one I used. I have to be out for a while, to have a tall one at lunch. I'll be back later.

---

### Post by hodad on 2010-11-23
Thanks, and I hope she's satisfying!  (Ooops1, I didn't really say that - erase)

I'll check back...

---

### Post by infiniah on 2010-11-23
Why don't you just use ndiswrapper, I find it quick and easy.

---

### Post by hodad on 2010-11-23
I suppose that I could, but whenever is see references to ndiswrapper, I see another several hundred pages of instructions  to follow in my future.  I may be forced to, however.  Also, I have an AMD machine, and it seems I need to modify the procedure for ndiswrapper even more (according to one guide).

---

### Post by chili555 on 2010-11-23
Is yours a 64-bit install? Do you have the x64 version .inf and .sys files? On the install disc that came with the device?

---

### Post by hodad on 2010-11-23
I installed edubuntu 10.04 AMD-64 (DOWNLOADED FRO THE UBUNTU DOWNLOAD SITE)

---

### Post by hodad on 2010-11-23
lOOKING BACK THRU THE STEPS, i NOTICED IN POST #60 THE FOLLOWING:

desktop:~/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1$ sudo make install
make -C /home/dave/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/dave/Downloads

Could it be that it never created an updated driver because of the "cannot create directory" line, and kept an older driver version?  I'm greasping at straws...

---

### Post by chili555 on 2010-11-23
> Could it be that it never created an updated driver because of the "cannot create directory" line, and kept an older driver version? I'm greasping at straws...No; that's entirely normal. The Makefile says to create a directory, but it already exists, so it goes into the existing directory and places a file, in this case RT2870STA.dat. It all looks maddeningly normal.

---

### Post by hodad on 2010-11-23
SO do I start again with another download/unpack/modify files/compile ( because of the ver. anomoly)?

---

### Post by chili555 on 2010-11-23
Please see PM.

---

### Post by hodad on 2010-11-23
Sorry, dont know what you mean by PM?

---

### Post by hodad on 2010-11-23
"Previous Message"

Well, I guess that means time to give it the boot.

Thanks for your help - It's been a long and frustrating road.  I'll buy another card and try again.  I started writing up the procedures for future reference.  I can send them along if you think it would be of any help in the future...

---

### Post by chili555 on 2010-11-23
No!!! Stop. Private Messages at the upper right, right below **Welcome, hodad.**

---

### Post by hodad on 2010-11-23
I think I just sent you a reply; first time try. Let me know if it didn't go.

---

### Post by chili555 on 2010-11-24
We got the compiled version to work by making one change in the Makefile. This may only apply to hadad's kernel, 2.6.33-25. We changed:```
ifeq ($(PLATFORM),PC)
# Linux 2.6
LINUX_SRC = /lib/modules/$(shell uname -r)/build
# Linux 2.4 Change to your local setting
#LINUX_SRC = /usr/src/linux-2.4
LINUX_SRC_MODULE = [COLOR="Red"]/lib/modules/$(shell uname -r)/kernel/drivers/net/wireless/[/COLOR]
CROSS_COMPILE = 
endif
```To:```
ifeq ($(PLATFORM),PC)
# Linux 2.6
LINUX_SRC = /lib/modules/$(shell uname -r)/build
# Linux 2.4 Change to your local setting
#LINUX_SRC = /usr/src/linux-2.4
LINUX_SRC_MODULE = [COLOR="Red"]/lib/modules/$(shell uname -r)/kernel/drivers/staging/rt2870/[/COLOR]
CROSS_COMPILE = 
endif/
```Then it compiled and installed correctly on his system. He removed and reinserted the device and it started blinking. A wireless interface, ra0 is now found in *iwconfig*. We are having trouble getting it to scan and have Network Manager take control.

hodad, please reboot the machine and run:```
iwconfig > hodad.txt
dmesg >> hodad.txt
sudo cat /var/log/syslog | grep -i rt2 >> hodad.txt
lsmod >> hodad.txt
zip hodad.zip hodad.txt
```Attach the zip file to your reply. Thanks.

---

### Post by hodad on 2010-11-24
... and here it is.  Note that when I ran iwconfig, ra0 was listed (but didn't echo for some reason):

(see attachment)

---

### Post by hodad on 2010-11-24
I looked at syslog, and it was almost empty,  attached is updated systog text after I unplugged/plugged it in.

---

### Post by hodad on 2010-11-24
I looked at syslog, and it was almost empty,  attached is updated systog text after I unplugged/plugged it in.

---

### Post by chili555 on 2010-11-24
> iwconfig > hodad.txt
dmesg >> hodad.txt
sudo cat /var/log/syslog | grep -i rt2 >> hodad.txt
lsmod >> hodad.txt
zip hodad.zip hodad.txtI got about 1/10th of what is expected. Please run the commands one right after the other, in order and be cautious about the > sign (meaning *add* the text to a file), and the >> sign (meaning *append* the text to the previous file.) You should end up with a giant text file and a much smaller zip file. I want the zip.

---

### Post by hodad on 2010-11-24
Not sure what happened, but here's the result:

---

### Post by chili555 on 2010-11-24
I notice this:> [ 1073.019399] rtusb_disconnect: unregister usbnet usb-0000:00:13.2-1
[ 1073.019407] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=ra0!
[ 1073.029274] [COLOR="Red"]CMDTHREAD_RESET_BULK_IN: Cannot do bulk in because flags[/COLOR](0x30080102) on !When I google the highlighted part, I see:

[http://www.spinics.net/lists/linux-usb/msg37744.html](http://www.spinics.net/lists/linux-usb/msg37744.html)> Even that probably won't help, since overcurrent is a hardware problem.  
Evidently the ralink device wants to draw more power than the mobile 
device is capable of providing. [https://bugs.archlinux.org/task/20159](https://bugs.archlinux.org/task/20159)> hardware was broken, sorry for the noise. I have checked with other computers and OSes and the same problem happens.
I don't know whether 'broken hardware' means the device itself or the USB port. Some information is here, from your lsusb -vv:> Bus 002 Device 002: ID 07d1:3c16 D-Link System
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 2.00
bDeviceClass 0 (Defined at Interface level)
bDeviceSubClass 0
bDeviceProtocol 0
bMaxPacketSize0 64
idVendor 0x07d1 D-Link System
idProduct 0x3c16
bcdDevice 1.01
iManufacturer 1 Ralink
iProduct 2 11n Adapter
iSerial 3 1.0
--- snip ---
(Bus Powered)
[COLOR="Red"]MaxPower 450mA[/COLOR]
Interface Descriptor:
--- snip ---I don't know quite what that means. Does the device spring to life in another computer? Do other USB devices, mice, etc., work perfectly in the same USB port?

---

### Post by hodad on 2010-11-24
A few snippets of info:

Fist of all, I opened the door on the "Pidgin" coop.

2.  THe USB prt is OK (mounted is on adjacent one), but I changed ports anyway.

3. I just rebooted the pc (as it froze for some reason) and I notice the following change - the bugger started to flash with data (instead of the usual regular rhythmic flashing) for a while, and the network manager icon was trying to connect (ethernet cable still hooked up).  Now the wireless NM icon is gone, and it's back to ethernet (I guess it gave up trying), and the bugger is flashing regularly again.

4.  I agree that the power issue is puzzling - 0dBm is equiv to 1 mw; but I think even 1 mw should be OK as the router is only 5 feet away.  I tried to force power level up yesterday to no avail - turns out that all available iwconfig commands are not available depending on the driver (rt2870 in this case) according to one source I read.

5. I've been going thru the Ubuntu wireless networking troubleshooting guide, and am trying to force a connection at this point.  Will let you knoww if I get any promising results...

---

### Post by hodad on 2010-11-24
Tried scanning ra0 using another tool I found in a thread with an interesting result:


desktop:~$ sudo nmap -sS 192.168.0.1

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-11-24 10:12 MST
Interesting ports on 192.168.0.1:
Not shown: 997 closed ports
PORT     STATE SERVICE
80/tcp   open  http
4444/tcp open  krb524
8099/tcp open  unknown
MAC Address: 00:1E:58:E8:F5:DB (D-Link)

Nmap done: 1 IP address (1 host up) scanned in 1.05 seconds

 By scanning the IP of the router (192.168.0.1), it seems to have found the D-Link router!  I looked up the MAC address on the router, and it matches the above (unless 192:168:0:1 maps to the MAC address shown, and it just LOOKS like I found it?)!

BTW, my daughter just took over my other pc for homework, so I'm down to one pc...

---

### Post by hodad on 2010-11-24
Ooops!

Desregard - I had the ethernet cable plugged in - thought I was only on ra0.

---

### Post by hodad on 2010-11-24
One more observation:

When I try to start the wireless device using the network manager icon, the device flashes irregularly for a moment.  It appears that TX data is thus traversing the device. Perhaps the transmitter is turned off, however. THe regular flashing continues during this time.

---

### Post by hodad on 2010-11-24
Just got back - sorry, I was thinking 3pm our time - oops!

---

### Post by chili555 on 2010-11-24
> I opened the door on the "Pidgin" coop....and then you closed it?

---

### Post by hodad on 2010-11-24
I'm here, but can't get the pidgin up to answer you (your off line?)

---

### Post by hodad on 2010-11-25
Some Syslog messages that showed up when I plug in the device are attached.  Also, found this link referring to a bug resulting in one of the error listings in the attached:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/638791](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/638791)

Not sure if it'll help...

Hope you're having a good Thanksgiving!!!

---

### Post by chili555 on 2010-11-25
How about unplugging the wired ethernet, count to twenty and repeat the test. Name it plugin2 this time.

Wish the family Happy Thanksgiving from Grandpa and Mrs. Chili!

---

### Post by hodad on 2010-11-26
Just fired up the pc with the DWA-125, and the network manager icon was gone.  I need to get it back before carrying on (I'm on the other pc).  Will report back with results of "syslog test" when I restore network function...

---

### Post by bkratz on 2010-11-26
Been following this thread for a long time, until Dr Chili returns you might try the following (sometimes it works, but no harm)


Right click on the top panel-click add to panel-select notification area -click add

---

### Post by hodad on 2010-11-26
Thanks for the advice, I got it working by unplugging the DWA-125 and rebooting - network and NM icon came back (go figure!). Attached is file with results of unplugging eth0, waiting, unplugging dwa-125, waiting, then replugging dwa-125..

---

### Post by chili555 on 2010-11-26
Please do:```
cat /etc/Wireless/RT2870STA/RT2870STA.dat
```Post this portion:> AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=If your WPA key is in there, obscure it with ****.

When you do:```
sudo iwlist ra0 scan
```What are the WPA details?>  IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSKOr is it otherwise?

---

### Post by hodad on 2010-11-26
Firstly, got your IM, but couldn't respond, says you're offline.

Results:
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=

*************

desktop:~$ sudo iwlist ra0 scan
[sudo] password for dave: 
ra0       Interface doesn't support scanning.

---

### Post by chili555 on 2010-11-26
> **hodad said:**
> Firstly, got your IM, but couldn't respond, says you're offline.

Results:
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=

*************

desktop:~$ sudo iwlist ra0 scan
[sudo] password for dave: 
ra0       Interface doesn't support scanning.I thought you modified that according to the README? No? Wanna try again?

---

### Post by hodad on 2010-11-26
Your pidgins keep flying in , but my messages keep going out, error mssage saying "not logged in"..  I'll fiddle with it...

---

### Post by hodad on 2010-11-26
REsults attached

---

### Post by hodad on 2010-11-26
Results attached...

---

### Post by hodad on 2010-11-26
syslog and data files attached. I'm going to lunch...

---

### Post by hodad on 2010-11-26
and the data file (didn't see it attached previous message)...

---

### Post by chili555 on 2010-11-26
I think there is a better way. Hold on a few...

---

### Post by chili555 on 2010-11-26
Please open a terminal and do:```
cd Downloads/Extract/2010_0709_RT2870_Linux_STA_v2.4.0.1
sudo make uninstall
```Now go here: [http://www.ralink.com.tw/support.php?s=2](http://www.ralink.com.tw/support.php?s=2)

Download this: RT8070/RT3070/RT3370 USB

In your Downloads directory, create a new folder called Extract2. Drag and drop the file you downloaded there. Back to the terminal:```
cd ~/Downloads/Extract2
tar xjvf 2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO.bz2
cd 2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO
```
Make the changes to os/linux/config/mk as before.
```
sudo su
rmmod -f rt2870sta
echo "blacklist rt2870sta" >> /etc/modprobe.d/blacklist.conf
make
make install
modprobe rt3370sta
iwconfig
iwlist ra0 scan
exit
```Any improvement?

---

### Post by hodad on 2010-11-26
Yes - for the first time scan returns something:

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@girls-desktop:/home/dave/Downloads/Extract2/2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO# iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: 00:1E:58:E8:F5:DB
                    Protocol:802.11b/g/n
                    ESSID:"axmey"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-33 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s
****************

Ping still results in "Network is Unreachable", though.

---

### Post by hodad on 2010-11-26
This message coming to you through the "little bugger"!

After compiling the new module, and copying their canned version of RT2870STA.dat, I made a few changes and DISABLED the encryption on both ends.  It came right up after that w/o ethernet cable.  Now that it's working, I'll reinstate encryption (as soon as I figure out the right settings in the .dat file).

I'll then review/update my installation instructions and send them along.

---

### Post by chili555 on 2010-11-26
Awesome! I am glad it's finally working. Thanks for sticking with it. When you turn the computer over to the girls, tell them Uncle Chili hopes they have fun and stay safe!

---

### Post by hodad on 2010-11-26
This message travelling through the little bugger  (w ethernet cable disconnected)!

Recompiled per your instructions, then copied their "canned" dat file, with necessary changes, and disabled encryption on both ends temporarily.

Can't get working in encrypted mode under any combination of settings in the dat file.  WIll try to implement thru NM GUI.

---

### Post by hodad on 2010-11-27
Many thanks to Chili for the many days he spent helping me resolve the problems with the DWA-125!


Seems to me that the README file supplied by Ralink as part of the download could be a bit more accurate and detailed, as many of the settings in the RT2870STA.dat file were incomplete (anyone from Ralink listening? - well, probably not)

Still having an issue with encryption, but I'll post that separately, I guess.  Hope to send along a summary of what made it work, to save people the heartache we went thru...

---

### Post by punck on 2010-11-29
Great news! I'll hope for your summary.

Congratulations, Chili.

Cya

---

### Post by hodad on 2010-11-29
Still doing research so that I can summarize the steps we took.  I will post when the document is finished.

Q for Chili - How did you decide to try the 3370 Ralink driver our of the list of available drivers at  [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)  ?  I looked at the page, and the readme's aren't very easy to decipher (they're more like programmer's notes).  The DWA-125 uses the Ralink rt2870 chipset, so how did you decide to try the 3370 (which worked right away!)?

---

### Post by chili555 on 2010-11-29
I decided to try it because many of the threads I Googled up referred to the 3070 driver. While the 3070 and the 2870 are very similar and have been merged in the stock built-in driver: > modinfo /lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    [COLOR="Red"]RT2870/RT3070[/COLOR] Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       rt3070.bin
firmware:       rt2870.bin
etc., etc.
I wondered if there were significant differences that might solve your issue. I also looked at the dev_id.c file and saw that your usb.id was explicitly listed with no editing required. So it seems that Ralink, the author of the driver and the manufacturer of your device thinks 3070 is correct for your device.

The proof was that your device started and runs just fine using this driver.

Please remember that, when a new linux-image, or kernel, comes along, you will need to build the module against the new kernel using the steps above, with an addition:```
[COLOR="Red"]make clean[/COLOR]
make
make install
```

---

### Post by hodad on 2010-11-29
Again, Many THanks Chili!

ANyway, it's nice to know that I'll be able to go thru the whole procedure once again when and if I upgrade the kernal!!!!

You can best believe, I'll be sticking with this kernal for a good while!!!

But seriously, I think I understand what's going on now, whereas when we first started out, I didn't have a clue!!!

I am still working on the guidelines for this driver install, and will post when done.  I'd like to give folks a general guideline of what we did, in hopes it might save others the troubles I encountered.

Besides, I'll be turning right around in a day or two and configuring my son's computer for wireless using a different wireless card, so it may be useful for that as well.

BTW, still no joy on the encryption problem, but I think were close (see the other thread "Router encryption settings 10.04".  When we resolve that, I'll enter in the guidelines.

---

### Post by hodad on 2010-11-29
Going thru the postings to edit my installation instructions. I have the following questions:

In the network_driver.rules and network_drivers.conf files, we added the long lines of instructions, i.e.:

install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "07d1 3c16" > /sys/bus/usb/drivers/rt2870/new_id

I would have thought it would change to:

install rt3370sta /sbin/modprobe --ignore-install rt3370sta $CMDLINE_OPTS; /bin/echo "07d1 3c16" > /sys/bus/usb/drivers/rt3370/new_id

to reflect the rt3370 driver?

Also, I noticed that the config.mk file for the new rt3370 driver also refers to the rt2870 numerous times, so I assume that they don't want us to make the name changes, am I right?

Just a bit confused - were using the rt3370 driver, but the compilation process still refers to rt2870 (?). Is there any easy explanation?

---

### Post by chili555 on 2010-11-29
I thought we moved those out of the way; i.e. to '.bak' so they wouldn't affect the compiled version. See post #71 here. If you did that properly, the command to edit or see these files should yield 'no such file or directory.'

[http://ubuntuforums.org/showthread.php?t=1625657&page=8](http://ubuntuforums.org/showthread.php?t=1625657&page=8)

---

### Post by hodad on 2010-11-29
Does that mean that we don't want to use those files at all (because we moved them out of the way)?  I ask because they seem to be common in other threads on the DWA-125 problem.

---

### Post by chili555 on 2010-11-29
> Does that mean that we don't want to use those files at all (because we moved them out of the way)?Yes.

They are common in other DWA-125 threads where the native rt2870sta driver is tricked into recognizing the usb.id and working. We tried that in your case and it did *not* work. It does no good and possibly does harm to mix two methods, one of which, in your case doesn't work.

---

### Post by hodad on 2010-11-29
Thanks, that makes sense.

Per PM, here's the attachment...

---

### Post by hodad on 2010-12-02
After 2 weeks of trying I give up.  I will string an ethernet cable, as the ethernet connection seems to always be reliable.  I wrote a summary in hopes of helping others thru the process, but I'm told it has too many mistakes, so wont post it.  Hopefully others that have the DWA-125 will have better luck.

---

### Post by hodad on 2010-12-02
One last post: 

I wanted to thank Chili for all of the time he put into helping me out.  Not his fault it didnt work, and I'm sure he would be able to get it working in 5 minutes if he were sitting at my pc!  

Perhaps a clean reinstall of the operating system would have worked.  But the main reason I decided to "cut bait" is that I'm concerned that the device would just decide to stop working some day, and I'd have to go thru the whole process again (for instance, if my daughter plugged in her MP3 player, and something got hosed).

Best to all!

---

### Post by alistair1946 on 2011-05-01
Wanted to say a big THANKYOU to chili555 for a very informative walk through this remedial action in dealing with the D-Link DWA125 wifi setup in Ubuntu 10.10 (Maverick Meercat).
As a result of your steps as set out in thread # 1625657 in helping hodad I have resolved my connectivity issues and am now wirelessly connected to the NET using a D-Link DWA125 dongle and sending you this reply via Ubuntu.
I am an old newbe from down under and really appreciate your input. Keep up the great work!!!!!
Cheers Al :smile:
"Quake City"

---

### Post by jeopardise on 2011-05-05
> **chili555 said:**
> Please open a terminal and do:```
cd Downloads/Extract/2010_0709_RT2870_Linux_STA_v2.4.0.1
sudo make uninstall
```Now go here: [http://www.ralink.com.tw/support.php?s=2](http://www.ralink.com.tw/support.php?s=2)

Download this: RT8070/RT3070/RT3370 USB

In your Downloads directory, create a new folder called Extract2. Drag and drop the file you downloaded there. Back to the terminal:```
cd ~/Downloads/Extract2
tar xjvf 2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO.bz2
cd 2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO
```Make the changes to os/linux/config/mk as before.
```
sudo su
rmmod -f rt2870sta
echo "blacklist rt2870sta" >> /etc/modprobe.d/blacklist.conf
make
make install
modprobe rt3370sta
iwconfig
iwlist ra0 scan
exit
```Any improvement?


I am a new use in Ubuntu. I has been using Ubuntu 11.04 and DWA-125 seems to work. However, because of bugs (may related to OpenGL, power management, strange memory issues), I choose to more stable 10.10. But I am surprised that my DWA-125 doesn't blink. I temporarily borrow Aztech WL552USB from my brother to connect to the internet.

It seems that Mr Chilli has stated a solution for our problem. I've gone through page one until the current page. I think I could start from post #126 as referral.

However there is already an update for the driver at Ralink website for RT3070. Can I use it?

Let me try it first :guitar:

---

### Post by chili555 on 2011-05-06
> However there is already an update for the driver at Ralink website for RT3070. Can I use it?

Let me try it firstPost back if you need further assistance.

---

### Post by Script Warlock on 2011-07-11
working in Ubuntu 11.04 just plug and play

lsusb:
Bus 001 Device 005: ID 07d1:3c16 D-Link System

---

