---
title: "Tenda W541U V2.0 Wireless USB Adapter / Ralink RT2070 How To"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by lesnoland on 2009-10-08
Hi,

After some time of searching, switching between sadness and happiness and pulling my hair out I finally got my Tenda W541U V2.0 a.k.a. Tenda 54M Mini, a.k.a. Ralink RT2070L working.

I wrote this tutorial because I googled and I found nothing, nobody seems to know how to do it or is not willing to share his method. I even emailed Tenda support and they said their hardware is not working on Linux but it seems it actually does.

Note: There are many CHEAP usb adapters that are based on this Ralink chipset, the best way to see if yours is using it is to do a lsusb, and check for 148f:2070 at ID.

**Hardware**:
Tenda W541U V2.0 Wireless USB Adapter ( Ralink RT2070L Chipset)

Bus 001 Device 003: ID 148f:2070 Ralink Technology, Corp.

**Driver**:
RT3070USB(RT307x) [http://www.sendspace.com/file/xfk1tg](http://www.sendspace.com/file/xfk1tg)

**Host**:
Linux mercury 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux

Ubuntu 9.04 \n \l

**Tutorial**:

1. Download the RT3070USB driver from Ralink. (link is listed above).
2. Unpack it.

```

$sudo su
#tar jxvf 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2
```

3. Navigate to os/linux and add the following line to usb_main_dev.c

```
#cd 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux
#pico usb_main_dev.c
...
add:
        {USB_DEVICE(0x148F,0x2070)}, /* Ralink 2070L */
under #ifdef RT3070
...

```
4. Compile the module. 

```
#cd ../..;make
```

5. Install the module.

```
#make install
```

6. Copy the .DAT file to /etc/Wireless. (the install script should do it but just in case). Also copy the rt2870.bin file to /lib/firmware. (just in case).

```
#mkdir -p /etc/Wireless/RT2870STA
#cp RT2870STA.dat /etc/Wireless/RT2870STA/
#apt-get install tofrodos
#dos2unix /etc/Wireless/RT2870STA/RT2870STA.dat
#chmod +x /etc/Wireless/RT2870STA/RT2870STA.dat

#cp common/rt2870.bin /lib/firmware/

```
7. Start the module.

```
#modprobe rt3070sta
```

8. Test to see if it works.

```
#ifconfig ra0 inet 192.168.0.33 up

#iwconfig ra0
```

9. Configure the card.

For step 9, you can find numerous tutorials, the configuration is exactly the same as for the rt2870 chipset.

**UPDATE:** Linux Kernel >= 2.6.31 / Ubuntu Karmic Koala 9.10 compile patch!
Ok, after speaking with another person and installing Ubuntu 9.10 on my other box I noticed this driver will not compile on my brand new 2.6.31-14-generic kernel.

The error I received (and probably many people do when attempting to compile most ralink drivers under 2.6.31 because this kernel replaced the old net_device structure with a new one called net_device_ops) was: 

```

  CC [M]  /root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.o
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevAttach&#8217;:
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1510: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1511: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1512: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1513: error: &#8216;struct net_device&#8217; has no member named &#8216;do_ioctl&#8217;
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1519: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1553: error: &#8216;struct net_device&#8217; has no member named &#8216;validate_addr&#8217;
make[2]: *** [/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/root/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [LINUX] Error 2
```

After some deep searching I found this rt3070-2.6.31-compile.patch (a part of rt3070-kmod Fedora 11 package) on lists.rpmfusion.org/pipermail/rpmfusion-commits/2009-August/006214.html. Once you apply it, it will compile just fine.

I have attached it to this post, just:

```
$gunzip rt3070-2.6.31-compile.patch.gz

$patch -p0 < rt3070-2.6.31-compile.patch

patching file 2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp_os.h
patching file 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c
patching file 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_main_dev.c

$cd 2009_0525_RT3070_Linux_STA_v2.1.1.0/

$make

```

Also make sure that rt2800usb, rt2x00usb and rt2x00lib are blacklisted as they now recognize this device (under Ubuntu 9.10) but the device will not function properly (no scan results). 

```
$sudo pico /etc/modprobe.d/blacklist.conf

add the following lines:
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
close and save.

$sudo rmmod rt2x00usb (just in case)
$sudo rmmod rt2x00lib (just in case)
$sudo rmmod rt2800usb (just in case)
```

Good luck.

**Update 2**: If when you are trying to load the module you receive the following (on Karmic):

```
$sudo modprobe rt3070sta
$dmesg
815108.907620] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.
```

And your device is NOT detected, copy the rt3070sta.ko file in the staging directory like this:

```
$cd os/linux
$sudo cp ./rtk3070sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/rt3070/
$sudo rmmod rt3070sta
$sudo modprobe rt3070sta
```

**Update 3**:
For some reason the common/rtusb_io.c file contains a very annoying line that will fill your dmesg with empty lines cointaining only #. In order to fix this "bug":

```
$nano common/rtusb_io.c
replace:
DBGPRINT(RT_DEBUG_OFF, ("#\n"));
with:
//DBGPRINT(RT_DEBUG_OFF, ("#\n"));
$sudo make clean && make && make install
```

Also I noticed Ralink "updated" the driver "directory" as the driver itself still wont compile on 2.6.30 >= kernels, and from a first impression it is the exact same driver. A quick fix would be to do the following, after you download the and extract driver archive:

```
$mv 2009_1106_RT3070_Linux_STA_V2.1.1.0 2009_0525_RT3070_Linux_STA_v2.1.1.0
```

That is because the rt3070-2.6.31-compile patch is designed to search for that directory in particular.

**Security Update**:
For those using this driver with wpasupplicant you should know about this bug which could affect your system:

[http://bugzilla.kernel.org/show_bug.cgi?id=14591](http://bugzilla.kernel.org/show_bug.cgi?id=14591)

A quick fix for it is to: 

```
$cd os/linux
$nano sta_ioctl.c
replace
struct iw_mlme *pMlme = (struct iw_mlme *)wrqu->data.pointer;
with
struct iw_mlme *pMlme;
and
struct iw_pmksa *pPmksa = (struct iw_pmksa *)wrqu->data.pointer;
with
struct iw_pmksa *pPmksa;
$sudo make clean && make && make install

```
The only disadvantage is that the driver will lack SIOCSIWPMKSA and SIOCSIWMLME functions. However I managed to connect to the AP (WPA,WEP) just fine w/out these two.

**Update**: Ralink kept changing the driver version, so I added a link to 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2. Also I tried to compile the driver with the patch applied on 2.6.32-22-generic-pae (Lucid) and it worked.

---

### Post by DingoStar on 2009-10-13
This is fantastic lesnoland. I almost gave up on installing Ubuntu on my daughter's PC because of this damn rt2070 chip! Your instructions are spot on.
I would like to add a couple of tips to anyone who uses WPA security. 
Before compiling the driver, make the following changes in os/linux/config.mk:
HAS_WPA_SUPPLICANT=[COLOR=Red]y[/COLOR]
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR=Red]y[/COLOR]
Also, if you are using WICD, ensure that WPA Suppliant Driver is wext.
Finally, if you are running lesnoland's instructions in Ubuntu, type sudo at the start of each command as you will need to run them as root.

---

### Post by thanh2050 on 2009-10-14
How to set rt2070 to mode Master ?

---

### Post by lesnoland on 2009-10-19
> **thanh2050 said:**
> How to set rt2070 to mode Master ?

I dont think that is possible with this driver, and I am unaware of another drivers existance for Linux.

However, I managed to provide Internet to my notebook by setting the notebooks wireless card to Master and connecting the USB Adapter to the AP. At first it felt kind of weird because the "router" was connecting to the "client" and not the other way around, but I encountered no problems.

---

### Post by lwhitmore on 2009-10-23
Thank you so much for this .. you're a life saver :)

---

### Post by Ylon on 2009-10-29
I can confirm (with patch) for Ubuntu Karmic Koala with a "0df6:003e Sitecom Europe B.V."

:popcorn::KS

---

### Post by mumuwoyou on 2009-10-30
[SIZE=4]In Ubuntu 9.10 (10.29)
I type:modprobe rt3070sta
then:lsmod
but I didn't found "rt3070sta",the 3070 didn't load.can you please tell me why?[/SIZE]

---

### Post by mumuwoyou on 2009-10-31
[SIZE=4]I modprobe rt2800usb ,it can find the wireless Adapter, can find wireless network,but  through the connecting  I can't explore www. if I rmmod rt2800usb and modprobe rt3070sta,lsmod , I can't find rt3070sta,reboot,also. please help me.thanks ![/SIZE]

---

### Post by Zoey.Marie on 2009-10-31
I'm using an Azio usb wireless adapter with the rt3070 chipset, and this little tutorial (with the patch on the end) finally got my wireless card working in 9.10

I thought I was doomed.

THANK YOU!!!!

---

### Post by forumboy on 2009-11-01
Thank you very much. With your instruction, my 0411:015d MelCo., Inc. (Buffalo WLI-UC-GN 802.11n USB-WiFi adapter) is working fine under Ubuntu 9.10 now.

---

### Post by john.jarvis on 2009-11-01
Thank you so much!  I can confirm that, after following your instructions, my Edimax EW-7711UAn Wireless nLite USB adapter (serial: 00:1f:1f:38:fc:1b) is at least working intermittently under 9.10 too.

---

### Post by anoncsaddict on 2009-11-06
> **forumboy said:**
> Thank you very much. With your instruction, my 0411:015d MelCo., Inc. (Buffalo WLI-UC-GN 802.11n USB-WiFi adapter) is working fine under Ubuntu 9.10 now.

Did you make any changes to the instructions as posted?  I tried to do everything mentioned including the patch but am still unable to use the Buffalo WLI-UC-GN adapter. rt3070 will show up in my lsmod, but when I try to connect I get "no such device"

---

### Post by hernanp on 2009-11-08
I follow the steps and now my wireless connection is working OK, but I have a new problem : the pptp client connection is not working, after checking all other stuff the only thing left is the patched driver (I suppose...)
I'm running Ubuntu 9.10
iptables ACCEPT all traffic (in and out)
I'm trying to establish a pptp connecting from the ubuntu machine TO a windows server over the Intenet but GRE protocol is NOT comming IN (as tcpdump shows), pptp keep sending GRE and finish with "LCP: timeout sending Config-Requests" error.
Before upgrating ubuntu (from 9.04) and patching the driver pptp is working corretly
Using Windows XP as a client running in the same machine the connection is working correctly

Can anyone figure out if the patch may cause the problem?
Thanks.

---

### Post by lesnoland on 2009-11-09
> **anoncsaddict said:**
> Did you make any changes to the instructions as posted?  I tried to do everything mentioned including the patch but am still unable to use the Buffalo WLI-UC-GN adapter. rt3070 will show up in my lsmod, but when I try to connect I get "no such device"

You need to replace:
        {USB_DEVICE(0x148F,0x2070)}, /* Ralink 2070L */
With:
        {USB_DEVICE(0x0411,0x015d)}, /* Melco Inc */

This way your device will be detected. If thats not the problem, let us know.

---

### Post by lesnoland on 2009-11-09
> **mumuwoyou said:**
> [SIZE=4]I modprobe rt2800usb ,it can find the wireless Adapter, can find wireless network,but  through the connecting  I can't explore www. if I rmmod rt2800usb and modprobe rt3070sta,lsmod , I can't find rt3070sta,reboot,also. please help me.thanks ![/SIZE]

Maybe the module did not install correctly, try to insert it like this(after removing and blacklisting the other modules):

```
$cd os/linux
$sudo insmod ./rt3070sta.ko
$dmesg
```

And check the output for some kind of error.

Note: rt2800usb will recognize the device, still when you try to scan for networks it will not work.

---

### Post by hernanp on 2009-11-09
> **hernanp said:**
> I follow the steps and now my wireless connection is working OK, but I have a new problem : the pptp client connection is not working, after checking all other stuff the only thing left is the patched driver (I suppose...)
I'm running Ubuntu 9.10
iptables ACCEPT all traffic (in and out)
I'm trying to establish a pptp connecting from the ubuntu machine TO a windows server over the Intenet but GRE protocol is NOT comming IN (as tcpdump shows), pptp keep sending GRE and finish with "LCP: timeout sending Config-Requests" error.
Before upgrating ubuntu (from 9.04) and patching the driver pptp is working corretly
Using Windows XP as a client running in the same machine the connection is working correctly

Can anyone figure out if the patch may cause the problem?
Thanks.
Forget it, I deleted the passwords in the keyring and problem solved. It seems that network-manager cannot retrieve the password for the user name configured and send it to pppd generating GRE traffic only out. The same tcpdump can be obtained calling pppd from command line using a user name that not exists in chap-secrets....

---

### Post by mvs1207 on 2009-11-09
> **lesnoland said:**
> You need to replace:
        {USB_DEVICE(0x148F,0x2070)}, /* Ralink 2070L */
With:
        {USB_DEVICE(0x0411,0x015d)}, /* Melco Inc */

This way your device will be detected. If thats not the problem, let us know.

Did that.  But still no luck here on 9.10.  ifconfig -a shows eth0, lo and vboxnet0.  dmesg shows the following
> 
[  865.744034] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.
[  865.755443] rtusb init --->
[  865.755511] usbcore: registered new interface driver rt2870


Any pointers?

---

### Post by ReneVYL on 2009-11-10
I, too, appear to have problems with WLI-UC-GN: investigating ...


EDIT: it would seem that rt3070sta.ko is not loaded automatically when my WLI-UC-GN is plugged in. If, on the other hand, it is manually insmod'd, things seem to work, at least some of the time. More later ...

---

### Post by lesnoland on 2009-11-10
> **VMUKKAMALA said:**
> Did that.  But still no luck here on 9.10.  ifconfig -a shows eth0, lo and vboxnet0.  dmesg shows the following


Any pointers?

Try this: 

```
$cd os/linux
$sudo cp rt3070sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/rt3070/
$sudo rmmod rt3070sta.ko
$sudo modporbe rt3070sta.ko
```

---

### Post by lesnoland on 2009-11-10
> **ReneVYL said:**
> I, too, appear to have problems with WLI-UC-GN: investigating ...


EDIT: it would seem that rt3070sta.ko is not loaded automatically when my WLI-UC-GN is plugged in. If, on the other hand, it is manually insmod'd, things seem to work, at least some of the time. More later ...

This should fix the problem if your "staging" module is loaded:

```
$cd os/linux
$sudo cp ./rtk3070sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/rt3070/
$sudo rmmod rt3070sta
$sudo modprobe rt3070sta
```

If no module is loaded when you plug in the device then you could add it to be loaded at startup. But my guess is that the rt3070sta.ko file is not in the right location.

---

### Post by ReneVYL on 2009-11-10
> **lesnoland said:**
> This should fix the problem if your "staging" module is loaded:

```
$cd os/linux
$sudo cp ./rtk3070sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/
$sudo rmmod rt3070sta
$sudo modprobe rt3070sta
```If no module is loaded when you plug in the device then you could add it to be loaded at startup. But my guess is that the rt3070sta.ko file is not in the right location.

It turns out that this was pretty much exactly what was wrong.

/lib/modules/`uname -r`/kernel/drivers/staging/rt3070/ contained an rt3070sta.ko, but it was different from the one I built. Copying rt3070sta.ko into <the staging path you mentioned>/rt3070/ works better, at least. Early indications seems to be that I need to do "sudo modprobe rt3070sta" by hand, though ... 

Thanks a bunch!


EDIT: the early indications were wrong; lesnoland's fix is 100%.

---

### Post by mvs1207 on 2009-11-10
> **lesnoland said:**
> Try this: 

```
$cd os/linux
$sudo cp rt3070sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/rt3070/
$sudo rmmod rt3070sta.ko
$sudo modporbe rt3070sta.ko
```

You are right.  Thanks to your instructions, my wireless works now.  Now.. I need to get Network Manager applet to play nice with my usb wireless adapter.

---

### Post by Jonah11 on 2009-11-20
> **VMUKKAMALA said:**
> You are right.  Thanks to your instructions, my wireless works now.  Now.. I need to get Network Manager applet to play nice with my usb wireless adapter.

It's not working for me.  I also have a WLI-UC-GN, and have followed every step/update in this thread, including the suggestions that were made to you.  I get...

linux# modprobe rt3070sta.ko
FATAL: Module rt3070sta.ko not found.

Also, I get:

linux# ifconfig ra0 inet 192.168.0.33 up
SIOCSIFADDR: No such device
ra0: ERROR while getting interface flags: No such device
ra0: ERROR while getting interface flags: No such device

What can I do?

Thanks,
Jonah

---

### Post by lesnoland on 2009-11-20
> **Jonah11 said:**
> 

What can I do?

Thanks,
Jonah

You can start by trying to insmod ./rt3070sta.ko driver from os/linux, as stated above. 

Also if you get some kind of error while compiling, installing, following the instructions tell us about it.

Also post more info about your computer such as the following:

```
$uname -a; cat /etc/issue; ls -la /lib/modules
```

---

### Post by Jonah11 on 2009-11-20
> **lesnoland said:**
> You can start by trying to insmod ./rt3070sta.ko driver from os/linux, as stated above. 
Thanks.  I tried that, and insmod ran without error.  However, I still get the same errors as in my latter post when I run modprobe and ifconfig.

> Also if you get some kind of error while compiling, installing, following the instructions tell us about it.I did not see any errors while compiling, but it's possible I missed something.  Should I recompile and post the terminal output?

> Also post more info about your computer such as the following:



```
$uname -a; cat /etc/issue; ls -la /lib/modules
```I am running an acer aspire revo with the latest ubuntu installed.
```

Linux boxee-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
Ubuntu 9.10 \n \l

total 20
drwxr-xr-x  3 root root  4096 2009-10-28 15:57 .
drwxr-xr-x 18 root root 12288 2009-11-17 20:41 ..
drwxr-xr-x  5 root root  4096 2009-11-20 00:43 2.6.31-14-generic


```Please let me know if you need any further info.

Thanks,
Jonah

---

### Post by Jonah11 on 2009-11-21
Anyone else have any hints for me?  Thanks!

---

### Post by flhtguy on 2009-11-23
I did the following as the instructions suggested $sudo pico /etc/modprobe.d/blacklist.conf  add the following lines: blacklist rt2x00usb blacklist rt2x00lib blacklist rt2800usb close and save.  $sudo rmmod rt2x00usb (just in case) $sudo rmmod rt2x00lib (just in case) $sudo rmmod rt2800usb (just in case)  And the dongle did not light up. I removed the above lines from /etc/modprobe.d/blacklist.conf and the dongle does light up but when doing a "dmesg" the following message is displayed at the end:  Disabling channel 2467 MHz on phy3 due to Country IE [  269.353614] cfg80211: Disabling channel 2472 MHz on phy3 due to Country IE [  269.353619] cfg80211: Disabling channel 2484 MHz on phy3 due to Country IE [  269.354736] phy3: Selected rate control algorithm 'minstrel' [  269.356326] Registered led device: rt2800usb-phy3::radio [  269.356364] Registered led device: rt2800usb-phy3::assoc [  269.356401] Registered led device: rt2800usb-phy3::quality [  269.427095] rt2800usb 1-1:1.0: firmware: requesting rt2870.bin [  269.681281] ADDRCONF(NETDEV_UP): wlan1: link is not ready  Any Ideas?  Thanks for the great instructions, by the way.

---

### Post by Fruitbeard on 2009-11-25
Hi There,

Has anyone got a copy of

2009_0525_RT3070_Linux_STA_v2.1.1.0.tar.bz2

The ralinktech site (link on first post) appears only to have some newer drivers 

2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2

which when following these instructions, gives an error (during the UPDATE1 section of the post) on patching :

patching file 2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp_os.h
patching file 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c
Hunk #1 FAILED at 1506.
Hunk #2 FAILED at 1545.
2 out of 2 hunks FAILED -- saving rejects to file 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c.rej
patching file 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_main_dev.c
Hunk #1 succeeded at 513 (offset 9 lines).
Hunk #2 succeeded at 544 (offset 9 lines).
Hunk #3 succeeded at 557 (offset 9 lines).

If someone could post the v.2.1.1.0 version of these drivers I'd be most grateful.

Many Thanks.

---

### Post by darkod on 2009-12-04
> **Fruitbeard said:**
> Hi There,

Has anyone got a copy of

2009_0525_RT3070_Linux_STA_v2.1.1.0.tar.bz2

The ralinktech site (link on first post) appears only to have some newer drivers 

2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2

which when following these instructions, gives an error (during the UPDATE1 section of the post) on patching :

patching file 2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp_os.h
patching file 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c
Hunk #1 FAILED at 1506.
Hunk #2 FAILED at 1545.
2 out of 2 hunks FAILED -- saving rejects to file 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c.rej
patching file 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_main_dev.c
Hunk #1 succeeded at 513 (offset 9 lines).
Hunk #2 succeeded at 544 (offset 9 lines).
Hunk #3 succeeded at 557 (offset 9 lines).

If someone could post the v.2.1.1.0 version of these drivers I'd be most grateful.

Many Thanks.

Exactly the same happened to me just now with 2009_1110 driver from Ralink. Any ideas for us?

PS. Before finding this thread I compiled 2009_1110 without this patch but it doesn't seem to work. Also in Connection Information in NetworkManager for driver it shows "usb" not RT3070 or RT2870. Any ideas please? I really got stuck with this. Ihave Tenda W311U which is 150Mb USB N adapter it seems with RT3070 (lsusb is giving 148e:3070).

PPS. Also, I don't know if it matters, someone might know but in the /etc/Wireless folder there was RT3070STA folder created during my compiling but the file inside is named RT2870STA.dat have no idea why and whether that's good or bad.

---

### Post by darkod on 2009-12-04
@Fruitbeard
In case you're still looking for solution, it seems I managed to get this going.
First of all, sudo lsusb is reporting 148F:3070 Ralink which means RT3070 chip and not RT2870 but since the patch for RT3070 driver was giving me the same error like yours, I decided to give RT2870 driver a shot. I'm attaching the exact driver I used and the exact patch. On the Ralink website they still offer the same driver for RT2870, the 2009_0820 anyway so you can get it there too.

1. Before compiling, edit the /os/linux/config.mk file and change wpa supplicant options from 'n' to 'y' (yes) if you want to use WPA. Put the patch file inside the 2009_0820 folder that will be created when you extract the driver. It has to be there or it won't work. Execute the patch with:

patch -p1 < patchname

2. Open /etc/modprobe.d/blacklist.conf and blacklist 2x00usb, 2x00lib and 2800usb as per the instructions in the first post here.

3. Open /etc/modules and add
rt2870sta

4. Open /etc/rc.local and add
# hack for wireless
ifconfig ra0 up
pkill NetworkManager

That's it. Reboot and see if it works. I hope I didn't forget anything.

---

### Post by noppie on 2009-12-06
os/linux/config.mk


where do i find this file

thank you

---

### Post by darkod on 2009-12-06
After you unpack the downloaded driver file (it's compressed), it will create folder starting with 2009_0820 blabla (or other number depending on which driver, that number is a date). Inside that folder you will find folder "os" and inside "linux".

So what it's said /os/linux/config.mk

It is meant relevant to the position when you are in the 2009_0820 etc folder.

---

### Post by jcorcione on 2009-12-22
PLEASE forgive me if I have put this post in the wrong area.  Any information would b most helpful as i plan on installing this on several more pc's in my home.  LOVE this software!!

I am sorry to beat a dead horse here.  But I have read almost every single post.  I have followed the directions on unpacking and installing the ralinktech drivers and such (at least i hope i have) and getting no joy on connecting or the system to recognize the usb adapter.

I started by installing Ubuntu on my daughters pc its a dell.  I was fed up with Windows XP Pro on here machine and it getting viruses all the time so I obliterated the XP o/s and went with linux ubuntu.  Love the software but being so spoiled and babied by XP i have lost much of my CLI skills and cannot get the usb adapter to work.

SO following the instructions as stated in the original post, this is where I am at.

After all the instructions and installing the necessary drivers and such I see that in network connections properties that the IP Address is a 10.x.x.x.  I see activity on the adapter (lights flashing) and i feel i have entered all the necessary wep sec info using the GUI part of UBUNTU as well as the ip address 192.168.x.x information but cannot connect to the internet.  Do I have to go into the terminal and setup the ip address and and dns info there?  I can't seem to find out which network interface i have referring to ra0 vs wlan0 etc... Please can someone help me?

Thanks

---

### Post by opt1k on 2009-12-22
confirmed working with EDUP USB stick. ebay $3.00 stick;  new.

**jcorcione**: maybe this is your problem? >>>

To get this working with the nm-applet aka network manager applet I found that you need to do the following before compile.

nano -w os/linux/config.mk

change the WPA lines from n to y

#ifdef WPA_SUPPLICANT_SUPPORT
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y
#endif // WPA_SUPPLICANT_SUPPORT //

#ifdef NATIVE_WPA_SUPPLICANT_SUPPORT
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
#endif // NATIVE_WPA_SUPPLICANT_SUPPORT //

EDIT:
There is a new release of this driver on the site that does not need patching with 9.10 to be able to compile. you still need to edit config.mk for wpa.

2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2

---

### Post by bx2gp1 on 2009-12-23
hi,
i downloaded the new driver version of tenda w541u which is 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2
and also the 	rt3070-2.6.31-compile.patch.gz file
but every time i type #tar jxvf 2009_1110_RT3070_Linux_STA_v2.1.2.0.bz2
it says "no such file or directory", i placed it in drive D with out any folder. what seems to be the problem? i cant proceed to the next instruction. anyway i typed sudo su and placed my password at the beginning of the code..

---

### Post by opt1k on 2009-12-23
> **bx2gp1 said:**
> hi,
i downloaded the new driver version of tenda w541u which is 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2
and also the 	rt3070-2.6.31-compile.patch.gz file
but every time i type #tar jxvf 2009_1110_RT3070_Linux_STA_v2.1.2.0.bz2
it says "no such file or directory", i placed it in drive D with out any folder. what seems to be the problem? i cant proceed to the next instruction. anyway i typed sudo su and placed my password at the beginning of the code..

i dont know your level of expertise with the system so dont take this reply the wrong way. 

confirm you are in the correct directory and typing the file name correctly.

without more information it appears you need to mount your windows drive containing the files and copy the .bz2 off of it to a working directory in your home folder.

the very basic terminal commands if you dont know them are

ls list files
cd change directory
mv move
cp copy
pwd print working directory
nano terminal based text editor
cat print the contents of file to screen

---

### Post by opt1k on 2009-12-23
recompiling on RT kernel. please advise...

/root/rt2070/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c: In function &#8216;RtmpRaDevCtrlInit&#8217;:
/root/rt2070/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3709: error: implicit declaration of function &#8216;init_MUTEX&#8217;
/root/rt2070/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3710: warning: passing argument 2 of &#8216;os_alloc_mem&#8217; from incompatible pointer type
/root/rt2070/2009_1110_RT3070_Linux_STA_v2.1.2.0/include/rtmp.h:5704: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;UCHAR *&#8217;
make[2]: *** [/root/rt2070/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o] Error 1
make[1]: *** [_module_/root/rt2070/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-9-rt'

---

### Post by bx2gp1 on 2009-12-23
> **opt1k said:**
> i dont know your level of expertise with the system so dont take this reply the wrong way. 

confirm you are in the correct directory and typing the file name correctly.

without more information it appears you need to mount your windows drive containing the files and copy the .bz2 off of it to a working directory in your home folder.

the very basic terminal commands if you dont know them are

ls list files
cd change directory
mv move
cp copy
pwd print working directory
nano terminal based text editor
cat print the contents of file to screen

i did copy the bz2 file in the download folder (inside the home folder) and also in the home folder(beside the download folder) but same error occurs, "no such file or directory"

when i type lsusb, 1 of the line says "ralink network usb 2.0"(or something like that, i dont remember the exact words) and i also blacklisted the 3 rt's namely rt2x00usb, rt2x00lib and rt2800usb so they wont be read like what the instructions sed.

btw, i am typing the codes in bush(shell)
i also try typing inside the CTRL+ALT+F1 console but noting changes.

---

### Post by opt1k on 2009-12-23
> **bx2gp1 said:**
> i did copy the bz2 file in the download folder (inside the home folder) and also in the home folder(beside the download folder) but same error occurs, "no such file or directory"

when i type lsusb, 1 of the line says "ralink network usb 2.0"(or something like that, i dont remember the exact words) and i also blacklisted the 3 rt's namely rt2x00usb, rt2x00lib and rt2800usb so they wont be read like what the instructions sed.

btw, i am typing the codes in bush(shell)
i also try typing inside the CTRL+ALT+F1 console but noting changes.


could your error be a simple as removing the "#" from what you are typing 

tar jxvf 2009_1110_RT3070_Linux_STA_v2.1.2.0.bz2
or just try 

tar jxvf *bz2

---

### Post by bx2gp1 on 2009-12-23
ok i will try and inform u the outcome

---

### Post by bx2gp1 on 2009-12-23
everything works fine but the ifconfig inet dont work,
and i try to manage a connection but no wireless option,
only wired and dsl are available

---

### Post by sanjib on 2009-12-23
I am also trying to use WLI-UC-GN wireless. After referring to this thread and some trial and error I could get the blue light blinking on the USB dongle. However still not able to connect to the network using wireless. 

The following is the output of iwconfig for ra0
ra0       Link encap:Ethernet  HWaddr 00:24:a5:23:0a:8e  
          inet6 addr: fe80::224:a5ff:fe23:a8e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3723 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6826 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1145621 (1.1 MB)  TX bytes:571344 (571.3 KB)

ra0:avahi Link encap:Ethernet  HWaddr 00:24:a5:23:0a:8e  
          inet addr:169.254.5.198  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1


When I check System->Preferences->Network connections, it has successfully determined the ESSID for Wireless connection. Do I need to input the Key?

---

### Post by rozeni on 2009-12-24
I am trying to make WLI-UC-GN work.  I followed the instructions and was able to get to the point where "iwconfig ra0" displays the following information

Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

However, there is no ra0 connection in the network manager?  I am not sure where ESSID in the above excerpt came from.  I've tried various configuration commands but nothing seems to work.  Where do I go from here?

Thanks

---

### Post by jcorcione on 2009-12-24
> **opt1k said:**
> confirmed working with EDUP USB stick. ebay $3.00 stick;  new.

**jcorcione**: maybe this is your problem? >>>

To get this working with the nm-applet aka network manager applet I found that you need to do the following before compile.

nano -w os/linux/config.mk

change the WPA lines from n to y

#ifdef WPA_SUPPLICANT_SUPPORT
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y
#endif // WPA_SUPPLICANT_SUPPORT //

#ifdef NATIVE_WPA_SUPPLICANT_SUPPORT
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
#endif // NATIVE_WPA_SUPPLICANT_SUPPORT //

EDIT:
There is a new release of this driver on the site that does not need patching with 9.10 to be able to compile. you still need to edit config.mk for wpa.

2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2

Thanks for your response.  I tried this and did not see this file in the directories.  I have also checked that the .dat file for the 2870/3070 usb adapter is there.  I don't even see the ra0 adapter when i run ifconfig or iwconfig.  Tried to install the driver via synaptic application.  NO JOY.  i will continue to work on this.  let me know if you have any more suggestions.:confused:

---

### Post by Ramunas on 2010-01-05
I'm getting this, when I'm trying to apply the patch for 9.10 kernel:
```
ramunas@ramunas-desktop:~/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0$ patch -p0 < rt3070-2.6.31-compile.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -rupN 2009_0525_RT3070_Linux_STA_v2.1.1.0.old/include/rtmp_os.h 2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp_os.h
|--- 2009_0525_RT3070_Linux_STA_v2.1.1.0.old/include/rtmp_os.h	2009-05-20 23:33:56.000000000 -0400
|+++ 2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp_os.h	2009-08-04 00:00:46.000000000 -0400
--------------------------
File to patch:
```
Any ideas?


**Sorry for stupid post, solved, did that in the wrong dir.**

---

### Post by exo_ist on 2010-01-27
Hi,
I have this problem too...
HELP PLS ;)
> **Ramunas said:**
> I'm getting this, when I'm trying to apply the patch for 9.10 kernel:
```
ramunas@ramunas-desktop:~/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0$ patch -p0 < rt3070-2.6.31-compile.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -rupN 2009_0525_RT3070_Linux_STA_v2.1.1.0.old/include/rtmp_os.h 2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp_os.h
|--- 2009_0525_RT3070_Linux_STA_v2.1.1.0.old/include/rtmp_os.h	2009-05-20 23:33:56.000000000 -0400
|+++ 2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp_os.h	2009-08-04 00:00:46.000000000 -0400
--------------------------
File to patch:
```
Any ideas?


**Sorry for stupid post, solved, did that in the wrong dir.**

---

### Post by dablus on 2010-02-01
lesnoland - Thanks for writing this up!


Yesterday - I followed the procedure found the first post of [http://ubuntuforums.org/showthread.php?p=8071728](http://ubuntuforums.org/showthread.php?p=8071728), with a few minor differences (some from details found in subsequent posts in the thread).


Here is the modified the procedure that worked for me using the information found here and using Ubuntu 9.10 with a Zonet ZEW2508 usb wifi adapter with chipset Ralink RT2070:


1. Download the RT3070USB(RT307x) driver from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2).

(As I write this, the current version of the driver is named: 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2).


2. Unpack it - and change directory into the new directory:

```

$ sudo tar jxvf 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2

$ cd 2009_1110_RT3070_Linux_STA_v2.1.2.0
...

```3. Add the following line to usb_main_dev.c:

```

$sudo vi os/linux/usb_main_dev.c
...

add:
        {USB_DEVICE(0x148F,0x2070)}, /* Ralink 2070 */
under #ifdef RT3070
...

```4. Modify rtusb_io.c to eliminate printing of blank lines with only # in dmesg file:

```

$ sudo vi common/rtusb_io.c
...

replace all occurences of:
DBGPRINT(RT_DEBUG_OFF, ("#\n"));
with:
**[COLOR=red]//[/COLOR]**DBGPRINT(RT_DEBUG_OFF, ("#\n"));
...

```5. Modify config.mk to include wpasupplicant support in the driver:

```

$sudo vi os/linux/config.mk
...

replace:
HAS_WPA_SUPPLICANT=n
with:
HAS_WPA_SUPPLICANT=**[COLOR=red]y[/COLOR]**
...

replace:
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
with:
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**[COLOR=red]y[/COLOR]**
...

```6. Modify sta_ioctl.c to fix wpasupplicant security bug (see: [http://bugzilla.kernel.org/show_bug.cgi?id=14591](http://bugzilla.kernel.org/show_bug.cgi?id=14591) for bug details):

```

$ sudo vi os/linux/sta_ioctl.c
...

replace:
struct iw_mlme *pMlme = (struct iw_mlme *)wrqu->data.pointer;
with:
struct iw_mlme *pMlme;
...

and replace:
struct iw_pmksa *pPmksa = (struct iw_pmksa *)wrqu->data.pointer;
with:
struct iw_pmksa *pPmksa;
...

```7. Compile the module:

```

$ sudu make
...

```8. Install the module:

```

$ sudu make install
...

```9. Copy the RT2870STA.dat file to /etc/Wireless , and copy the rt2870.bin file to /lib/firmware :

```

$ sudo mkdir -p /etc/Wireless/RT2870STA
$ sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/
$ sudo apt-get install tofrodos
$ sudo dos2unix /etc/Wireless/RT2870STA/RT2870STA.dat
$ sudo chmod +x /etc/Wireless/RT2870STA/RT2870STA.dat
...

$ sudo cp common/rt2870.bin /lib/firmware/
...

```11. Start the module.

```

$ sudo modprobe rt3070sta
...

```12. Test to see if it works.

```

$ sudo ifconfig ra0 up
$ sudo iwconfig ra0
...

```12b. If when you are trying to load the module (in step 11) you receive the following (on Karmic):

```

$ dmesg
815108.907620] rt3070sta: module is from the staging directory,
the quality is unknown, you have been warned.
...

```And - if your device is NOT detected (in step 12), copy the rt3070sta.ko file in the staging directory like this:

```

$ sudo cp os/linux/rtk3070sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/rt3070/
$ sudo rmmod rt3070sta
$ sudo modprobe rt3070sta
...

```13. Add the rt3070sta module to the list of modules to be loaded at boot time:

```

$ sudo vi /etc/modules
...

add:
rt3070sta
...

```14. Configure the card.

I found the HOWTO found at: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834) to be very complete, and managed to get my Zonet ZEW2508 usb wifi adapter configured and working for me.


NOTES:

I did NOT need to apply the rt3070-2.6.31-compile.patch file to patch the files found in the unpacked 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2 file.

I did NOT need to modify /etc/modprobe.d/blacklist.conf to get the rt3070sta module to run properly.

I did NOT need to modify /etc/rc.local to get ra0 to start up automatically at boot time.

Others may or may not need to complete the steps I skipped here: [http://ubuntuforums.org/showthread.php?t=1285828](http://ubuntuforums.org/showthread.php?t=1285828) (read earlier posts in this thread for additional details).


Hopefully, I managed to write this up without introducing some new errors...


Thanks again!


Addendum:

To update my routing tables, now that I have two network interfaces - configured by dhcp - able to reach non-local network, I used this modification to the /etc/network/interfaces file:

```

$ sudo vi /etc/network/interfaces
...

add:
auto eth0
iface eth0 inet dhcp
post-up ip route delete default dev eth0
...

```This addition to the interfaces file deletes the default route added by dhcp for eth0.

When the other network interface (in my case, ra0) is configured by dhcp - a default route is automatically added to the main routing table, allowing non-local networks to be reached.

A comparable change could be made for ra0 (rather than eth0), if I wanted eth0 to handle traffic destined for non-local networks.

---

### Post by bx2gp1 on 2010-02-01
hi, i have finished installing the driver and blacklisting the 3 rt's according to the guide, but everytime i type modprobe rt3070sta nothing happens, i even tried rebooting my unit but still the same, i cant use my w541u to scan for any available accespoint (which i can connect using windows), i check the iwconfig and the ra0 was rt2870, what seems to be the problem?

---

### Post by esunix on 2010-02-16
Hi,

Firstly I would like to thank all of you that are so supportant to each other.
As not findning the soulution for my problem I registered here.

Secondly,
I followed the steps and managed to get 0411:015d MelCo., Inc. (Buffalo WLI-UC-GN 802.11n USB-WiFi adapter)  work on my BackTrack 4. The system finds the interfaces and everything and the USBcard blinks. But whenever I try to connect to an accespoint I press connect.. and it just stays there.. and later it gets disconnected. After that, the network interface dissapears.. but can be seen from iwconfig.. but I cannot see it from Wicid manager.
Anyone know the solution for this ? 
I tried to do a clean new reinstall of this but still get to that same issue.
Appreciate for help.

---

### Post by Anubis on 2010-02-18
[http://www.linuxquestions.org/questions/linux-networking-3/ralink-chipset-works-in-ubuntu-jaunty-not-karmic-beta-761949/](http://www.linuxquestions.org/questions/linux-networking-3/ralink-chipset-works-in-ubuntu-jaunty-not-karmic-beta-761949/)

blacklist rt2800usb
blacklist rt2870sta

That is all I did. All of this compiling of modules is silly when all is required is to add two lines to the modules blacklist.

---

### Post by esunix on 2010-02-18
> **Anubis said:**
> [http://www.linuxquestions.org/questions/linux-networking-3/ralink-chipset-works-in-ubuntu-jaunty-not-karmic-beta-761949/](http://www.linuxquestions.org/questions/linux-networking-3/ralink-chipset-works-in-ubuntu-jaunty-not-karmic-beta-761949/)

blacklist rt2800usb
blacklist rt2870sta

That is all I did. All of this compiling of modules is silly when all is required is to add two lines to the modules blacklist.

Thanks for the reply,

I tried that out.. but it seems to not help :(
Any other suggests ?

When I type dmesg i get the result
```
Bulk In Failed. Status = -32, BIIdx=0x0, BIRIdx=0x0, actual_length= 0x0
```

---

### Post by clipement on 2010-02-18
hi darko,

I have downloaded both patch and the driver and tried to install it but i am having troubles with those steps you provided.

how do you Execute the patch with:

patch -p1 < patchname ? I do not understand how its done.

also I've tried changing 2. Open /etc/modprobe.d/blacklist.conf and blacklist 2x00usb, 2x00lib and 2800usb as per the instructions in the first post here.

3. Open /etc/modules and add
rt2870sta

4. Open /etc/rc.local and add
# hack for wireless
ifconfig ra0 up
pkill NetworkManager


it wouldn't let me save?!


I am new to Linux as you could probably tell.  really would appreciate your help!

---

### Post by clipement on 2010-02-18
could anyone tell me whats up with the code? I dont get where you input the code and how to read it. is it just copy and paste?

---

### Post by Rothstei on 2010-02-21
Well, this has got me as close as I've gotten so far. Thanks!

I'm using the Buffalo WLI-UC-GN, and have modified the USB ID as suggested. Install works, and modprobe seems to be effective.

ifconfig actually worked once; I saw ra0 come up with no speed. I rebooted to see if it would improve, and I lost it again. I've now uninstalled and reinstalled a couple of times, using the patch and not using the patch, trying to copy rt3070sta.ko manually, and not, and messing with the file and directory names in /etc/Wireless, but to no avail. When I do ifconfig, it thinks for a minute, and then:

SIOCSIFFLAGS: Operation not permitted
SIOCSIFFLAGS: Operation not permitted

that's it.

I've tried every other suggestion in the thread, as well as the variations here [http://ubuntuforums.org/showthread.php?t=960642](http://ubuntuforums.org/showthread.php?t=960642)
because I thought I had read that for the Buffalo WKI-UC-GN, rt2870sta was the driver I wanted, but when I saw all the folks having success with rt3070sta, I started trying that instead. I've definitely gotten further over here.

Any ideas on the SIOCSIFFLAGS? I haven't found a good description of what that means, other than that others have run into it with ra0 driver troubles as well.

Thanks again to Lensoland and others--I really appreciate the clearly written tutorials. Makes this a lot easier to learn, and understand what I'm doing!

Adam

---

### Post by esunix on 2010-02-22
> **Rothstei said:**
> Well, this has got me as close as I've gotten so far. Thanks!

I'm using the Buffalo WLI-UC-GN, and have modified the USB ID as suggested. Install works, and modprobe seems to be effective.

ifconfig actually worked once; I saw ra0 come up with no speed. I rebooted to see if it would improve, and I lost it again. I've now uninstalled and reinstalled a couple of times, using the patch and not using the patch, trying to copy rt3070sta.ko manually, and not, and messing with the file and directory names in /etc/Wireless, but to no avail. When I do ifconfig, it thinks for a minute, and then:

SIOCSIFFLAGS: Operation not permitted
SIOCSIFFLAGS: Operation not permitted

that's it.

I've tried every other suggestion in the thread, as well as the variations here [http://ubuntuforums.org/showthread.php?t=960642](http://ubuntuforums.org/showthread.php?t=960642)
because I thought I had read that for the Buffalo WKI-UC-GN, rt2870sta was the driver I wanted, but when I saw all the folks having success with rt3070sta, I started trying that instead. I've definitely gotten further over here.

Any ideas on the SIOCSIFFLAGS? I haven't found a good description of what that means, other than that others have run into it with ra0 driver troubles as well.

Thanks again to Lensoland and others--I really appreciate the clearly written tutorials. Makes this a lot easier to learn, and understand what I'm doing!

Adam

did you try with

```
insmod ./rt3070sta.ko
``` ?

---

### Post by rhycel on 2010-03-05
Hi, I hope this topic is not dead.

I`ve downloaded the new driver (RT3070_LinuxSTA_V2.3.0.1_20100208.tar.bz2) and got stuck with this:

add:
        {USB_DEVICE(0x148F,0x2070)}, /* Ralink 2070L */
under #ifdef RT3070
...

Can`t find where to insert it since there seems to be no #ifdef RT3070 line in usb_main_dev.c

---

### Post by flash63 on 2010-03-06
> **rhycel said:**
> Hi, I hope this topic is not dead.

I`ve downloaded the new driver (RT3070_LinuxSTA_V2.3.0.1_20100208.tar.bz2) and got stuck with this:

Can`t find where to insert it since there seems to be no #ifdef RT3070 line in usb_main_dev.c

Hello,
take a look at **~/RT3070_LinuxSTA_V2.3.0.1_20100208/common/rtusb_dev_id.c**

and don't forget the **~/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/config.mk**

---

### Post by rhycel on 2010-03-06
Thanks a lot, will start compiling and hopefully get this device detected.

---

### Post by Joemomma69 on 2010-03-10
Just wanted to say thanks to lesnoland and dablus for the write ups! My Buffalo WLI-UC-GN adapter is working now using the 2.1.2.0 driver.

Note: The latest on Ralink's site is 2.3.0.1. I could not get this version to work. It kept throwing "Unknown Symbols" errors when trying to insmod the compiled driver. Maybe someone smarter than me can figure that out ... 

Googling a copy of 2.1.2.0 and following the steps dablus posted works like a champ!

Thanks,
Joe

---

### Post by Phandmar on 2010-03-15
> **Joemomma69 said:**
> Just wanted to say thanks to lesnoland and dablus for the write ups! My Buffalo WLI-UC-GN adapter is working now using the 2.1.2.0 driver.

Note: The latest on Ralink's site is 2.3.0.1. I could not get this version to work. It kept throwing "Unknown Symbols" errors when trying to insmod the compiled driver. Maybe someone smarter than me can figure that out ... 

Googling a copy of 2.1.2.0 and following the steps dablus posted works like a champ!

Thanks,
Joe


Joe, can you tell me where you found a copy of the older version? - my googling skills are obviously not up to it. I've had the same issue with version 2.3.0.1

Thanks

---

### Post by keroro on 2010-03-21
I found 2.1.1.0 here:
[http://www.opendrivers.com/driver/292758/ralink-rt3070usb(rt307x)-driver-2.1.1.0-linux-free-download.html](http://www.opendrivers.com/driver/292758/ralink-rt3070usb(rt307x)-driver-2.1.1.0-linux-free-download.html)

You have to use the backup server since the driver is not available on Ralink's site anymore.

---

### Post by e-San on 2010-03-23
Hi! 

I still can not get it to work...

```
san@eeepc:/media/linux/Ralink/2009_0525_RT3070_Linux_STA_v2.1.1.0 (3)$ make
make -C tools
make[1]: Wej&#347;cie do katalogu `/media/linux/Ralink/2009_0525_RT3070_Linux_STA_v2.1.1.0 (3)/tools'
gcc -g bin2h.c -o bin2h
make[1]: Opuszczenie katalogu `/media/linux/Ralink/2009_0525_RT3070_Linux_STA_v2.1.1.0 (3)/tools'
/media/linux/Ralink/2009_0525_RT3070_Linux_STA_v2.1.1.0 (3)/tools/bin2h
/bin/sh: Syntax error: word unexpected (expecting ")")
make: *** [build_tools] B&#322;&#261;d 2
```

Tried to compile RT3070_LinuxSTA_V2.3.0.1_20100208:

```
san@eeepc:/media/linux/Ralink/RT3070_LinuxSTA_V2.3.0.1_20100208$ sudo modprobe rt3070sta
FATAL: Error inserting rt3070sta (/lib/modules/2.6.32.2-eeepc-0v9.6.4/kernel/drivers/net/wireless/rt3070sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

dmesg:
```
[  851.421139] rt3070sta: Unknown symbol usb_alloc_urb
[  851.421395] rt3070sta: Unknown symbol usb_free_urb
[  851.423256] rt3070sta: Unknown symbol usb_register_driver
[  851.423833] rt3070sta: Unknown symbol usb_put_dev
[  851.426084] rt3070sta: Unknown symbol usb_get_dev
[  851.426541] rt3070sta: Unknown symbol usb_submit_urb
[  851.431217] rt3070sta: Unknown symbol usb_control_msg
[  851.432002] rt3070sta: Unknown symbol usb_deregister
[  851.434649] rt3070sta: Unknown symbol usb_kill_urb
[  851.434838] rt3070sta: Unknown symbol usb_buffer_free
[  851.436870] rt3070sta: Unknown symbol usb_buffer_alloc
```

```
san@eeepc:/media/linux/Ralink/RT3070_LinuxSTA_V2.3.0.1_20100208$ lsusb
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp.
```

EDIT!
lesnoland, you have got my very thanks!

according to your touturial i tried to edit kernel source:

since:```
linux-2.6.33.1/drivers/staging/rt2870$ cat usb_main_dev.c
#include "../rt2860/usb_main_dev.c"
```

lets go to linux-2.6.33.1/drivers/staging/rt2860 and edit usb_main_dev.c.
find something like this:
```
#ifdef RT3070
        
        {USB_DEVICE(0x148F, 0x3070)},   /* Ralink 3070 */
```

and make it like this:
```
#ifdef RT3070
        {USB_DEVICE(0x148F, 0x2070)},   /* e-San.info */
        {USB_DEVICE(0x148F, 0x3070)},   /* Ralink 3070 */
```

as You can see 'USB_DEVICE(0x148F, 0x2070)', specialy '148f' and '2070' are my device's id. Once again thanks to lesnoland!

```
san@eeepc:/media/linux$ lsusb
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp.
```

This CAN BE way to make run other 'CHEAP usb wifi's'.

We can go now for our new kernel.
Disable every rt* modules (specially rt2x00usb, rt2800usb, rt2x00lib etc.)
Go to Staging section and enable (in my case - as a module) rt2870/rt3070.
Do what you want to do more, compile it and enjoy!

```
san@eeepc:/media/linux$ lsmod
Module                  Size  Used by
uvcvideo               44395  0 
usb_storage            29202  5 
rt2870sta             336932  1 
ehci_hcd               26634  0 
usbcore                91415  4 uvcvideo,usb_storage,rt2870sta,ehci_hcd
sg                     12912  0 
eeepc_laptop            9914  0 
sparse_keymap           1695  1 eeepc_laptop
rfkill                  6652  2 eeepc_laptop

```

There are some disadvantages, but it does work:

```
wlan0     Ralink STA  ESSID:"Ratamahatta"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:02:72:5C:91:7F   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=97/100  Signal level:-65 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
Link quality is stronger than my built in wlan with two antenas - i can not belive in that...

---

### Post by archie888 on 2010-03-25
Hi, I tried this procedure, but there is a new driver from Ralink with a different version number. I did not see any reference to the line #ifdef RT3070 where the extra line needs to be inserted into usb_main_dev.c.

I entered the extra line anyway, and proceeded to compile. 

It appears to compile, but I do not see the RT3070STA.Dat file which generates an installer error in the make install step.

Please let me know if anyone has worked out how to use the latest Ralink Driver with this procedure ([http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)) ([RT3070USB(RT307x)]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekF5THpJMEwyUnZkMjVzYjJGa09UQTVOemcyT0RjMU1DNWllakk5UFQxU1ZETXdOekJmVEdsdWRYaFRWRUZmVmpJdU15NHdMakZmTWpBeE1EQXlNRGd1ZEdGeUM%3D")                     02/08/2010                     2.3.0.1)

Regards Archie888

---

### Post by roadwarriormark on 2010-03-25
First off, big thanks to lesnoland and others who have resolved most of my issues.

I have the ralink 2070 working to the point where it can detect the names of nearby wireless access points from Network Settings->ra0 Properties->Network Name (down arrow)

However, when I try to connect using DHCP and WPA at that point I get: Network, disconnected - you are now offline

I have set the supplicants to y for WPA for both the kernel and the network manager as described in earlier posts, and the ESSID, password and security is correct for the access point as it works with those from another machine, and I double checked them.

One thing I did not do so far is implement this suggestion, as I wasn't clear that it was a necessity, and just a security issue: (Maybe this could be the issue?)
6. Modify sta_ioctl.c to fix wpasupplicant security bug (see: [http://bugzilla.kernel.org/show_bug.cgi?id=14591](http://bugzilla.kernel.org/show_bug.cgi?id=14591) for bug details):
 
Another oddity is that in the top right tray for the network connection icon, it shows the wired network in bold, but does not show wireless network at all.  Wired network works fine for unplugging and replugging the cable, and to test the wireless I unplug the cable first.

I failed previously at getting this device working with ndiswrapper, so I went to native compilation and it seems like I am almost there except for this last hurdle.  So close...

If anyone has any ideas of what I can try, it would be greatly appreciated!

Thanks,

Mark

---

### Post by johnflux on 2010-03-26
Hi all,

  I'm am trying to get a fix put into the linux kernel.  If this is successful, the RT2070 should work out of the box in Ubuntu 10.04.  But I need your help!

  If you have RT2070 or the Buffalo WLI-UC-GN usb-wifi device:

  Please, install  the kernel at:   [http://people.canonical.com/~smb/lp441990/](http://people.canonical.com/~smb/lp441990/)

Specifically, do:

  wget [http://people.canonical.com/~smb/lp441990/linux-headers-2.6.32-17-generic_2.6.32-17.26+lp441990v1_i386.deb](http://people.canonical.com/~smb/lp441990/linux-headers-2.6.32-17-generic_2.6.32-17.26+lp441990v1_i386.deb) [http://people.canonical.com/~smb/lp441990/linux-headers-2.6.32-17_2.6.32-17.26+lp441990v1_all.deb](http://people.canonical.com/~smb/lp441990/linux-headers-2.6.32-17_2.6.32-17.26+lp441990v1_all.deb) [http://people.canonical.com/~smb/lp441990/linux-image-2.6.32-17-generic_2.6.32-17.26+lp441990v1_i386.deb](http://people.canonical.com/~smb/lp441990/linux-image-2.6.32-17-generic_2.6.32-17.26+lp441990v1_i386.deb)
  sudo dpkg -i linux-image-2.6.32-17-generic_2.6.32-17.26+lp441990v1_i386.deb linux-headers-2.6.32-17_2.6.32-17.26+lp441990v1_all.deb linux-headers-2.6.32-17-generic_2.6.32-17.26+lp441990v1_i386.deb


  And then tell me if your hardware works.

  I CANNOT GET THIS FIX UPSTREAM IF NOONE TESTS IT AND TELLS ME!


JohnFlux

---

### Post by johnflux on 2010-03-26
.. just in case it's not obvious, sorry, you need to reboot after doing the two instructions that I said, and then boot with that new kernel 2.6.32-17.  The device should then just work - you should have a ra0 in iwconfig, and the device should show up in networkmanager.

---

### Post by e-San on 2010-03-26
archie888, 
cp RT2870STA.Dat to RT3070STA.Dat - it is only config file. I belive it is beacose of buggy drivers. unlucky.

i tried to way you do, but it had not worked. anyway i found place and way how to add our id, but i do not remember where and how it was. find something like '3070', there should be something like 
{0xID1, 0xID2} name.
once again: it did not make it.

johnflux, sorry but i wont use any of preconfigured kernels. my configuration is special for my eeepc made with hours of testing.

you can send me kernel source and say what should i change in my config. i'll then test it.

---

### Post by johnflux on 2010-03-26
It's just the stock ubuntu lucid kernel, with the USB_DEVICE  line added.

---

### Post by e-San on 2010-03-26
Ok, i installed it.
It won't work, it won't boot. It halts on 
'mounted root fs
can not mount /dev/pts and something else
cant mount rootfs'
???

anyway if your patch is:
```
#ifdef RT3070
        {USB_DEVICE(0x148F, 0x2070)},   /* e-San.info */
        {USB_DEVICE(0x148F, 0x3070)},   /* Ralink 3070 */
```
only - it must work.

archie888, why dont you try to compile your own kernel?
it can take not much your time (but compileing does)
 - download kernel source (kernel.org)
 - extract it
 - copy your kernel config from /boot to .config into your kernel source
 - make oldconfig (standard answeres to everything new)
 - make xconfig - find staging in devices and enable rt3070 as module
 - save
 - apply my patch
 - make -j2
 - sudo make install modules_install
 - add your new kernel to your grub/lilo menu.

---

### Post by johnflux on 2010-03-26
> **e-San said:**
> Ok, i installed it.
It won't work, it won't boot. It halts on 
'mounted root fs
can not mount /dev/pts and something else
cant mount rootfs'
???


I don't know.  Is this on the EEPC?  Does the ubuntu kernel normally work?
> **e-San said:**
> 
anyway if your patch is:
```
#ifdef RT3070
        {USB_DEVICE(0x148F, 0x2070)},   /* e-San.info */
        {USB_DEVICE(0x148F, 0x3070)},   /* Ralink 3070 */
```only - it must work.


Yeah but I can't see that anyone has actually tried it, with the staging driver in the ubuntu kernel.  Everyone is off downloading the awful driver from ralink etc.  And you're telling people to use the stock linus kernel, which isn't helping things :P :)

---

### Post by nhandler on 2010-03-26
> **johnflux said:**
> Hi all,

  I'm am trying to get a fix put into the linux kernel.  If this is successful, the RT2070 should work out of the box in Ubuntu 10.04.  But I need your help!

  If you have RT2070 or the Buffalo WLI-UC-GN usb-wifi device:

  Please, install  the kernel at:   [http://people.canonical.com/~smb/lp441990/](http://people.canonical.com/~smb/lp441990/)

Specifically, do:

  wget [http://people.canonical.com/~smb/lp441990/linux-headers-2.6.32-17-generic_2.6.32-17.26+lp441990v1_i386.deb](http://people.canonical.com/~smb/lp441990/linux-headers-2.6.32-17-generic_2.6.32-17.26+lp441990v1_i386.deb) [http://people.canonical.com/~smb/lp441990/linux-headers-2.6.32-17_2.6.32-17.26+lp441990v1_all.deb](http://people.canonical.com/~smb/lp441990/linux-headers-2.6.32-17_2.6.32-17.26+lp441990v1_all.deb) [http://people.canonical.com/~smb/lp441990/linux-image-2.6.32-17-generic_2.6.32-17.26+lp441990v1_i386.deb](http://people.canonical.com/~smb/lp441990/linux-image-2.6.32-17-generic_2.6.32-17.26+lp441990v1_i386.deb)
  sudo dpkg -i linux-image-2.6.32-17-generic_2.6.32-17.26+lp441990v1_i386.deb linux-headers-2.6.32-17_2.6.32-17.26+lp441990v1_all.deb linux-headers-2.6.32-17-generic_2.6.32-17.26+lp441990v1_i386.deb


  And then tell me if your hardware works.

  I CANNOT GET THIS FIX UPSTREAM IF NOONE TESTS IT AND TELLS ME!


JohnFlux

These instructions worked for me ([http://www.buffalotech.com/products/wireless/client-adapters/nfiniti-wireless-n-ultra-compact-usb-20-adapter-wli-uc-gn/](http://www.buffalotech.com/products/wireless/client-adapters/nfiniti-wireless-n-ultra-compact-usb-20-adapter-wli-uc-gn/))

---

### Post by e-San on 2010-03-26
Yes, it is eeepc.
 Well i do not use ubuntu kernel, only mine. I installed 9.10 about month ago and it was working. 
Few days ago i moved everything to other hdd (ssd btw.) but it does find all my partitions with no problem.
I had not modified too much this os, so i can not find the reason why...

I tried this modification (i added patch for 'empty dmesg lines', will see if this helps - i made this after test if first modiffication helps) and it does definetly works. ;)

Meybe some usb-over-the-net? i belive there is something like that...

edit. i put information about this modification on rc2x00's team forum, meybe they will add this to drivers source.

edit2.

Hi, once again.
There is something more. there is another one small issue:

```
san@eeepc:~$ dmesg | tail
(...)
[22660.020103] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 402
[22780.020084] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 402
[22900.020078] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 267
[23020.022529] ===>rt_ioctl_giwscan. 2(2) BSS returned, san@eeepc:~$ dmesg | tail
(...)
[22660.020103] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 402
[22780.020084] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 402
[22900.020078] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 267
[23020.022529] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 267
[23140.017530] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 267
[23260.013949] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 508
[23380.014579] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 571
[23500.020122] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 571
data->length = 267
[23140.017530] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 267
[23260.013949] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 508
[23380.014579] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 571
[23500.020122] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 571
```

In my case - every two minutes.
but there is solution:

1. Once again, lets go to linux-2.6.33.1/drivers/staging/rt2860
2. nano sta_ioctl.c
3. find and comment
```
/*      DBGPRINT(RT_DEBUG_ERROR,        #e-San.info
                 ("===>rt_ioctl_giwscan. %d(%d) BSS returned, data->length = %d\n",
                  i, pAdapter->ScanTab.BssNr, data->length)); */
```
4. save (ctr + o)
5. compile and enjoy!

ad.1 if you compiled it with bug, remove linux-2.6.33.1/drivers/staging/rt2870/sta_ioctl.o before compileing.
ad.2 for further reserch, source: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/356807](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/356807)

---

### Post by roadwarriormark on 2010-03-28
In a previous post I wrote:

> **roadwarriormark said:**
> 
One thing I did not do so far is implement this suggestion, as I wasn't clear that it was a necessity, and just a security issue: (Maybe this could be the issue?)
6. Modify sta_ioctl.c to fix wpasupplicant security bug (see: [http://bugzilla.kernel.org/show_bug.cgi?id=14591](http://bugzilla.kernel.org/show_bug.cgi?id=14591) for bug details):
 

I didn't hear from anyone, so I put this bug fix in, but as I expected it wasn't the issue.

I would really appreciate any pointer I can get about getting the last bit of functionality working.  Specifically, it can detect the wireless network names... yay!  But then it can't connect to them.

I have no idea where to find these tutorials which were mentioned: For step 9, you can find numerous tutorials, the configuration is exactly the same as for the rt2870 chipset.

Thanks,

Mark

EDIT:

I re-read all the posts and did all the steps bit by bit again and this one helped:
sudo cp ./rtk3070sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/rt3070/

It got the latest compile in there.

I also found one which helped me get NetworkManager recognizing the wireless device and managing it, and now wireless is working!

It involved editing /etc/NetworkManager/nm-system-settings.conf 

Thanks to all!

There still seems to be some slowness and intermittent failures though, and some odd messages in the /var/log/messages file so that's my next hurdle...

Mar 30 08:52:31 compaq-desktop kernel: [ 2987.648527] ===>rt_ioctl_giwscan. 18(18) BSS returned, data->length = 2540
Mar 30 08:52:31 compaq-desktop kernel: [ 2987.659925] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
Mar 30 08:52:42 compaq-desktop kernel: [ 2998.851657] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
Mar 30 08:53:17 compaq-desktop kernel: [ 3033.976023] ===>rt_ioctl_giwscan. 18(18) BSS returned, data->length = 2540
Mar 30 08:53:17 compaq-desktop kernel: [ 3033.985177] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)

---

### Post by LooseCanon on 2010-03-29
Thanks so much for devoting a thread to this!

My adapter is a Tenda W311U. The chipset is Ralink 3070, and I'm usingthe current driver from the Ralink site (3070 2.3.0.1). I just tried using the patch and was told that "hunks" were failing. I've learned a lot about terminal in the last three days, but I'm very stuck here.

Does anyone have any ideas for me?

---

### Post by e-San on 2010-03-29
lsusb and what does not work?

---

### Post by mike909 on 2010-04-04
> **johnflux said:**
> 
  I CANNOT GET THIS FIX UPSTREAM IF NOONE TESTS IT AND TELLS ME!
JohnFlux

John,
Using the Buffalo WLI Nfinniti (Ralink chip) your updated kernel packages for amd64 made it work out-of-the-box. There is something worth mentioning though, my on-board wireless ( Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)) would stop being able to associate after approx. 2 hours of continuous use. Sorry, can't give more details than that, but it doesn't happen on 2.6.31-20, and it happned twice on that later kernel. I also can't tell you if it happens with the Buffalo card, as I  am returning it now that I realized it only does 802.11N in 2.4Ghz (it doesn't have a 5Ghz radio). Great work on getting those Ralink chips to work.

---

### Post by johnflux on 2010-04-04
Thanks Mike.

This means Ubuntu 10.04 will ship with support for the Buffalo card :)
Unfortunately nobody tested with RT2070, so I can't get that fix in :-/

---

### Post by rshakin on 2010-04-06
John, it looks like your most recent kernel patch will enable the chipset, and it will connect to a unsecured network when using the buffalo wli-uc-gn card. But it will not connect to a WPA enabled router, it will just time out and try again when you use the network management application. I've downloaded the most current kernel image that you've provided with the built in support.  Any ideas why it would do that. Also in your latest patch to the kernel the annoying "#" mark every 5 sec is still there. It's also there for the lucid release of the patch, so it's now upstream. 

rshakin@newline:~$ cat /proc/version
Linux version 2.6.32-17-generic (root@magrathea) (gcc version 4.4.3 (Ubuntu 4.4.3-3ubuntu3) ) #26+lp441990v1 SMP Thu Mar 25 14:20:15 UTC 2010


Bus 001 Device 004: ID 0411:015d MelCo., Inc.

---

### Post by roadwarriormark on 2010-04-07
trying to delete... where's the button? =P

---

### Post by roadwarriormark on 2010-04-07
I have been using this solution successfully with WPA, but I tried it with WEP and it fails.

I don't think I need to disable the WPA stuff I enabled for it to work with WEP as well.

Did anyone else have issues getting this working with WEP?

Mark

---

### Post by rshakin on 2010-04-08
I can't even get it to work with WPA, how did you get it to work with WPA and what card do you actually have.

---

### Post by roadwarriormark on 2010-04-08
> **rshakin said:**
> I can't even get it to work with WPA, how did you get it to work with WPA and what card do you actually have.

It's an EDUP Ralink Wireless 2070 on USB.

The way I got it to work was by following the instructions in this thread exactly, and not deviating.  Sometimes the hints came from posts later on in the thread from other folks.  I wrote down a log of what I tried as I did it, and can post it if you want, but basically it just always came back to reading the steps in this thread and doing them as suggested.

Unfortunately, nobody has posted any clues as to why WEP might be having issues yet.

My thanks again to the posters in this thread.

---

### Post by roadwarriormark on 2010-04-13
> **rshakin said:**
>  it will connect to a unsecured network 

I can connect successfully to WPA, but am having problems connecting via WEP and also connecting to an unsecured network.

When I try to connect to a network, it does not give me the option to choose no security, only between WEP and WPA.  This occurs at: System->administration->network->network settings->wireless connections->properties->ra0, when you click off the roaming checkbox.

Any help greatly appreciated.

Mark

---

### Post by LooseCanon on 2010-04-14
> **e-San said:**
> lsusb and what does not work?

Sorry I asked for help and then dropped off the planet. I got really busy and had to put my wireless troubles on hold. Here's my lsusb:

Bus 002 Device 002: ID 148f:3070 Ralink Technology, Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The first one is obviously the wirless adapter. It's a Tenda device, I know the hardware is fine because it works on my Windows XP installation. I've tried a lot of the fixes on this thread, and the adapter recognizes the correct network names, but it won't connect--so could it be a problem with WPA supplicant?

---

### Post by e-San on 2010-04-14
Have you tried my solution? [http://ubuntuforums.org/showpost.php?p=9013478&postcount=62](http://ubuntuforums.org/showpost.php?p=9013478&postcount=62)
It is the same device by ID.

Remember to disable non-staging modules for ralink wifi devices.

Give us your lsmod too.

EDIT. my mystake!
there is your ID included in kernel source. forget it.
show us your lsmod, if you have loaded wrong modules - it will not work - propably.
since it is not same device as mine, sorry, i can not give you sure answer.

---

### Post by LooseCanon on 2010-04-14
> **e-San said:**
> show us your lsmod, if you have loaded wrong modules - it will not work - propably.
since it is not same device as mine, sorry, i can not give you sure answer.

Here's my lsmod:

   Module                  Size  Used by
  
  nls_iso8859_1           5280  1 
  
  nls_cp437               6976  1 
  
  vfat                   13184  1 
  
  fat                    59832  1 vfat
  
  binfmt_misc            10220  1 
  
  snd_hda_codec_intelhdmi    14880  1 
  
  snd_hda_codec_realtek   277860  1 
  
  snd_hda_intel          31880  4 
  
  snd_hda_codec          87584  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
  
  iptable_filter          3872  0 
  
  ip_tables              21200  1 iptable_filter
  
  snd_hwdep               9352  1 snd_hda_codec
  
  snd_pcm_oss            44704  0 
  
  snd_mixer_oss          18976  1 snd_pcm_oss
  
  snd_pcm                93160  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
  
  snd_seq_dummy           3460  0 
  
  snd_seq_oss            33440  0 
  
  snd_seq_midi            8192  0 
  
  snd_rawmidi            27360  1 snd_seq_midi
  
  ppdev                   8232  0 
  
  lp                     11908  0 
  
  snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
  
  x_tables               25832  1 ip_tables
  
  parport                40528  2 ppdev,lp
  
  snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
  
  ndiswrapper           245248  0 
  
  snd_timer              26992  2 snd_pcm,snd_seq
  
  snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
  
  snd                    77096  20 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
  
  soundcore               9088  1 snd
  
  snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
  
  usbhid                 43968  0 
  
  ohci1394               33780  0 
  
  usb_storage            65952  1 
  
  ieee1394              100896  1 ohci1394
  
  floppy                 65192  0 
  
  r8169                  38884  0 
  
  mii                     6368  1 r8169
  
  intel_agp              32816  0 
  

If there's something wrong in here, can let me know what I need to do? I was pretty familiar with the fixes on this thread a 2 weeks ago, but since I've been busy and haven't' touched it, I don't remember everything I did. I'm really new at this.

---

### Post by keroro on 2010-04-16
It worked all so nicely.
I changed into the os/linux directory and then /sbin/insmod rt3070sta.ko and it worked.
Then I made a big mistake. Since months I booted XP and made the WLAN stick work. When I came back to Kubuntu (after 5 mins in XP i surely missed it) I had no more access to internet. When I did the commands I mentioned before, I always got a short message that the WLAN is now active. This message does not pop up anymore. No connection possible. I tried to re-install but no success.
It seems like something has been written on the WLAN stick by XP and now Linux can not recognize or load anymore.
If anybody has any idea how to get it work again I would be happy.
Thanks

---

### Post by e-San on 2010-04-17
LooseCanon,
first of all.  put your lsmod into 'code' or i won't answer your next question.
try to compile kernel (or try package on few post erlier) with staging support with modules for ralink. disable all ralink usb wifi devices too.

kerero,
it is not possible - there is no such memory to be written by windows.
is this pcie or usb device? does windows recognize it and is it usable?

---

### Post by LooseCanon on 2010-04-17
> **e-San said:**
> LooseCanon,
first of all.  put your lsmod into 'code' or i won't answer your next question.
try to compile kernel (or try package on few post erlier) with staging support with modules for ralink. disable all ralink usb wifi devices too.

If by 'code' you mean with columns properly formatted, sorry about that. I didn't notice that it was de-formatted last time. And actually, I'm trying now, but when I preview the post it takes all the spaces/indents away and makes a mess of the columns. How can I make the forum software comply?

Your instructions are confusing me, though. I thought I was trying to *enable* my usb ralink wifi device, not *disable* it.
I also don't know what actions are necessary to compile it with staging support for ralink modules, but if you mean the fixes from a few pages ago, I can try those (or try them again, if they're the ones I've already tried).

Thanks so much for your willingness to help!

---

### Post by keroro on 2010-04-18
> **e-San said:**
> LooseCanon,
it is not possible - there is no such memory to be written by windows.
is this pcie or usb device? does windows recognize it and is it usable?

It is a USB device. It is usable under windows. I just think it is strange that it worked perfectly under Linux until I made it work under XP. So  thought something has been changed on the stick or the WLAN station during the install procedure under Windows. I don't care if it works under XP. I need it to work under Linux.

---

### Post by keroro on 2010-04-19
Sorry for double post.
I did the whole installation procedure described in this thread again.
Also I decided to pull the power plug from the WLAN-station (it is not mine).
Now I can see the networks again. But somehow it seems that I can not get an IP address. I see the name of the networks the strength of the signals and all. But as soon as I want to connect, the manager just tells me 'activating' but then breaks up after a minute.

-----------------------------------------------------------------------

Problem solved:
I use KDE. When I click on the icon in the bar, the WLAN manager offers me the available networks. So I clicked the one I usually used. I checked the settings and everything looked OK. Anyway it did not work.
I deleted my standard connection and made a new one. All settings same. Now it works.

---

### Post by LooseCanon on 2010-04-20
I just saw that Ralink has a new version of the driver up for the 3070 chipset, posted April 12th 2010. The Read Me file on their site claims that it supports Linux Kernel 2.6.31. I'm trying it now without any of the revisions or patches to see if it works. I'll keep you updated.

Edit: No joy. Even after completing all the edits with the new driver, the adapter still doesn't work.

---

### Post by jcorcione on 2010-04-22
Is there not a SIMPLE instruction set to install this driver on Ubuntu Desk top?  This is getting quite frustrating.  I DO NOT want to go back to a windows OS.. and i would like my daughter to learn linux.. :confused:   I don't even see the usb adapter recognized in the gui on the ubuntu desk top.

---

### Post by LooseCanon on 2010-04-23
> **johnflux said:**
> Hi all,

  I'm am trying to get a fix put into the linux kernel.  If this is successful, the RT2070 should work out of the box in Ubuntu 10.04.  But I need your help!

  If you have RT2070 or the Buffalo WLI-UC-GN usb-wifi device:

  Please, install  the kernel at:   [http://people.canonical.com/~smb/lp441990/]("http://people.canonical.com/%7Esmb/lp441990/")

Specifically, do:

  wget [http://people.canonical.com/~smb/lp441990/linux-headers-2.6.32-17-generic_2.6.32-17.26+lp441990v1_i386.deb]("http://people.canonical.com/%7Esmb/lp441990/linux-headers-2.6.32-17-generic_2.6.32-17.26+lp441990v1_i386.deb") [http://people.canonical.com/~smb/lp441990/linux-headers-2.6.32-17_2.6.32-17.26+lp441990v1_all.deb]("http://people.canonical.com/%7Esmb/lp441990/linux-headers-2.6.32-17_2.6.32-17.26+lp441990v1_all.deb") [http://people.canonical.com/~smb/lp441990/linux-image-2.6.32-17-generic_2.6.32-17.26+lp441990v1_i386.deb]("http://people.canonical.com/%7Esmb/lp441990/linux-image-2.6.32-17-generic_2.6.32-17.26+lp441990v1_i386.deb")
  sudo dpkg -i linux-image-2.6.32-17-generic_2.6.32-17.26+lp441990v1_i386.deb linux-headers-2.6.32-17_2.6.32-17.26+lp441990v1_all.deb linux-headers-2.6.32-17-generic_2.6.32-17.26+lp441990v1_i386.deb


  And then tell me if your hardware works.

  I CANNOT GET THIS FIX UPSTREAM IF NOONE TESTS IT AND TELLS ME!


JohnFlux

I just tried this and upon doing the dpkg line, it informed me that the package architecture (i386) did not match my system (amd64). But my CPU is an Intel chip. Is this kernel for a 32-bit architecture? Because I do have Karmic 64-bit installed...

Edit:
Final (and strange) update. In connecting to download JohnFlux's kernel, I updated Karmic for the first time since installing it, and either John's kernel or a new one from the update showed up in my grub. I loaded that, modprobed rt2800usb, and my Tenda adapter (Ralink 3070 chipset) works (miraculously). Perhaps if (when I booted Ubuntu for the first time) I had known enough to manually modprobe that driver, it would have worked. Who knows? Thanks everyone for your help!

---

### Post by max62840 on 2010-05-05
HI,

First of all, sorry for my english, but it is well known that french people are very poor in other language !!! :lolflag:

I bought a wifi key : evo-w542usb and it seems that it's based on the rt2070 chipset.
It is detect but i have no scan results. Let's see the results of different command :

```
max@max-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
``````
max@max-laptop:~$ lsusb
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp.
``````
max@max-laptop:~$ lspci -nn | grep -i net
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
``````
max@max-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:81:29:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.12 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:27 memory:f6488000-f6488fff ioport:30f8(size=8) memory:f6489c00-f6489cff memory:f6489800-f648980f
  *-network
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:1a:73:8d:04:3e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f6000000-f6003fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:1d:1a:07:55:97
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn
``````
max@max-laptop:~$ lsmod
Module                  Size  Used by
michael_mic             1732  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
arc4                    1153  2 
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
mac80211              204922  2 rt2x00usb,rt2x00lib
snd_hda_codec_conexant    22577  1 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              126485  2 rt2x00lib,mac80211
lib80211_crypt_tkip     7596  0 
snd                    54148  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
usblp                  10481  0 
nvidia               9932176  40 
usbhid                 36110  0 
hid                    67032  1 usbhid
crc_ccitt               1339  1 rt2800usb
uvcvideo               56990  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
sdhci_pci               5470  0 
ricoh_mmc               2923  0 
sdhci                  15462  1 sdhci_pci
led_class               2864  2 rt2x00lib,sdhci
agpgart                31724  1 nvidia
vga16fb                11385  1 
vgastate                8961  1 vga16fb
i2c_nforce2             5199  0 
wl                   1959598  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
k8temp                  3024  0 
psmouse                63245  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
ahci                   32008  3 
pata_amd                8766  0 
forcedeth              49556  0
``````
max@max-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:199
          Rx invalid nwid:0  invalid crypt:27  invalid misc:0

wlan1     IEEE 802.11bgn  ESSID:"Livebox-3442"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=7 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
``````
max@max-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:81:29:3f  
          inet adr:192.168.1.12  Bcast:192.168.1.255  Masque:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:1176 erreurs:0 :0 overruns:0 frame:0
          TX packets:1151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1092190 (1.0 MB) Octets transmis:136726 (136.7 KB)
          Interruption:27 Adresse de base:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:8d:04:3e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:2599 erreurs:0 :0 overruns:0 frame:169
          TX packets:2437 errors:10 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:2459758 (2.4 MB) Octets transmis:329868 (329.8 KB)
          Interruption:19 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:11418 erreurs:0 :0 overruns:0 frame:0
          TX packets:11418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:3373510 (3.3 MB) Octets transmis:3373510 (3.3 MB)

wlan1     Link encap:Ethernet  HWaddr 00:1d:1a:07:55:97  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
``````
max@max-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

wlan1     No scan results
``````
max@max-laptop:~$ uname -r -m 
2.6.32-21-generic i686
``````
max@max-laptop:~$ cat  /etc/network/interfaces
auto lo
iface lo inet loopback
``````
max@max-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             disconnected
  Default:           no
  HW Address:        00:1D:1A:07:55:97

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:1B:24:81:29:3F

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             80.10.246.130
    DNS:             81.253.149.10


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        00:1A:73:8D:04:3E

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Livebox-3442:    Infra, 00:03:C9:7C:4D:86, Freq 2432 MHz, Rate 0 Mb/s, Strength 80 WPA
    NEUF_10C4:       Infra, 00:17:33:19:10:C5, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA
    Neuf WiFi:       Infra, 00:17:33:1F:D9:C8, Freq 2462 MHz, Rate 54 Mb/s, Strength 40
    Livebox-e5ba:    Infra, 00:16:41:CD:C8:EF, Freq 2457 MHz, Rate 54 Mb/s, Strength 80 WEP
    Livebox-3A68:    Infra, 00:1E:4C:20:FD:52, Freq 2412 MHz, Rate 0 Mb/s, Strength 60 WPA
    NEUF_D9C0:       Infra, 00:17:33:1F:D9:C1, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA
    Livebox-DD10:    Infra, 00:1E:4C:96:F1:16, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA
```I use Ubuntu 10.04. I don't know if there is an issue for my trouble ! Can you help me please ?

Thx a lot,

Max

---

### Post by medeea on 2010-05-09
Max, you receive no scan results because that is what you get when using rt2800usb driver, they have added support for it, but not fully supported. by following the instructions on first post, i think you can get it to work.

also make sure you blacklist the following modules: rt2800usb, rt2x00usb, rt2x00lib.

---

### Post by max62840 on 2010-05-09
I've already tried to compile the ralink driver as explain in first post, but it didn't work. The key was detect but when I tried to activate it I had this kind of response (I don't remenber exactly): 

SCSIOFLAGS : Operation not permitted. 

Whereas I used 'sudo ....'

So no results for me.

---

### Post by medeea on 2010-05-09
well, if you want to get it to work, follow the steps again, and post detailed instructions on what errors you get. this is the only way i believe we can help you.

---

### Post by max62840 on 2010-05-09
Well I've restart the installation from the beginning. 
I had to replace dos2unix by fromdos at step 6 and now it's ok. 

But I have a poor bitrate : 0.50Mbs when I make a test on [http://www.speedtest.net]("http://www.speedtest.net/")
Whereas I have a 20Mbs subscription !!

---

### Post by NX3 on 2010-06-06
The Tenda W541U v2 doesn't work out of the box on 10.04.

I have followed the instructions from the first post but I fail at step 3 as below. I find no reference in the file to RT3070 or any similar line so don't know where to put the line. 

It would be much simplier if Ralink chipset wifi deviced worked out of the box.

"
#cd 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux
#pico usb_main_dev.c
...
add:
        {USB_DEVICE(0x148F,0x2070)}, /* Ralink 2070L */
under #ifdef RT3070
...

---

### Post by lesnoland on 2010-06-07
I think you are trying to modify a different version of the drivers, as Ralink keeps updating them. Please check in the first pages, I think there is a link there to the original driver this tutorial was designed to work with.

Regards.

Update: Here is a link to the original driver:

[http://www.sendspace.com/file/xfk1tg](http://www.sendspace.com/file/xfk1tg)

> **NX3 said:**
> The Tenda W541U v2 doesn't work out of the box on 10.04.

I have followed the instructions from the first post but I fail at step 3 as below. I find no reference in the file to RT3070 or any similar line so don't know where to put the line. 

It would be much simplier if Ralink chipset wifi deviced worked out of the box.

"
#cd 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux
#pico usb_main_dev.c
...
add:
        {USB_DEVICE(0x148F,0x2070)}, /* Ralink 2070L */
under #ifdef RT3070
...

---

### Post by auditguy on 2010-06-09
It just worked! I downloaded all three files (kernel image and headers) and installed. A re-boot with the modified 2.6.32-17 kernel and my wireless came alive.

Thank you for providing this to the community.

---

### Post by thomaswp on 2010-06-26
Hmmm. :confused: I have tried the instructions in the first post but the make fails.  Initially this was because gcc was not installed but now I get:

```
make *** /lib/modules/2.6.32-22-generic/build: No such file or directory. Stop.
```

I am running a new install of xubuntu 10.04 on an IBM R31 with 256MB RAM as a hobby project, so not that urgent, but I am confused by this.  I figured it might be because I need the kernel source and downloaded that but no build directory appeared.

I am also confused by the patch.  When do I run the patch code? (assuming I can get the **make** and **make install**to work).

---

### Post by lesnoland on 2010-06-26
you need to install the kernel headers (the kernel source is not required): 

```
apt-get install build-essential kernel-headers-$(uname -r)
```

if it still does not work, try to find some info about building a kernel module, you can easily find it on google.

you run the patch code after you unpack the archive.

> **thomaswp said:**
> Hmmm. :confused: I have tried the instructions in the first post but the make fails.  Initially this was because gcc was not installed but now I get:

```
make *** /lib/modules/2.6.32-22-generic/build: No such file or directory. Stop.
```

I am running a new install of xubuntu 10.04 on an IBM R31 with 256MB RAM as a hobby project, so not that urgent, but I am confused by this.  I figured it might be because I need the kernel source and downloaded that but no build directory appeared.

I am also confused by the patch.  When do I run the patch code? (assuming I can get the **make** and **make install**to work).

---

### Post by Jeff_USA on 2010-07-09
Hi.
After compiling four different Ralink drivers (kernel modules)  I was able to get 2 of them fully working with my Ralink 2070 wifi. I am using kernel  2.6.32.  None of Ralinks drivers had the correct usb IDs I needed (148F:2070) this had to be added. Blacklisting of rt2800usb was also required. The two drivers that worked were:

1) 2009_0525_RT3070_Linux_STA_v2.1.1.0 : This driver is no longer available from Ralink. This driver  is well documented in this thread the, "rt3070-2.6.31-compile.patch" still worked with the 2.6.32 kernel.

2)  DPO_RT3070_LinuxSTA_V2.3.0.2_20100412 : This is a later driver available from Ralink This compiled for me with no errors without patching.  just A) Make clean-- to clean up the junk, B) add your USB ID into   "/commom/rtusb_dev_id.c"  and C) Make -- compile the driver. The rt3070sta.ko is built into the /os/linux directory.

I also tried 2 RT2870  drivers but was not able to get them fully working with the 2070 hardware.
Keep having fun
Jeff

---

### Post by hulmeman on 2010-08-23
I've successfully installed the latest ralink driver (DPO_RT3070_LinuxSTA_V2.3.0.4_20100604) on kernel 2.6.34, but I'm getting this error with 2.6.35:

> 
CC [M]  /usr/src/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_mac_usb.o
/usr/src/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_mac_usb.c: In function &#9632;NICInitTransmit&#9632;:
/usr/src/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_mac_usb.c:917: error: implicit declaration of function
&#9632;usb_buffer_alloc&#9632;
/usr/src/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_mac_usb.c:917: warning: cast to pointer from integer of different size
/usr/src/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_mac_usb.c:1004: warning: cast to pointer from integer of different size
/usr/src/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_mac_usb.c:1022: warning: cast to pointer from integer of different size
/usr/src/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_mac_usb.c:1039: warning: cast to pointer from integer of different size
/usr/src/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_mac_usb.c:1055: warning: cast to pointer from integer of different size
/usr/src/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_mac_usb.c:1078: error: implicit declaration of function &#9632;usb_buffer_free&#9632;
make[2]: *** [/usr/src/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/usr/src/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.35-gentoo-r2'
make: *** [LINUX] Error 2


Any ideas?

---

### Post by Amazing-q3 on 2010-08-27
i have the same trouble with 2.6.35 kernel (.
please post here if someone solve this problem.

---

### Post by VolatileMember on 2010-08-28
It seems that they renamed usb_buffer_alloc and usb_buffer_free in 2.6.35 into usb_alloc_coherent and usb_free_coherent. Attached is a patch which fixes the compile errors. Let me know if the driver works for you now!

(driver version: DPO_RT3070_LinuxSTA_V2.3.0.4_20100604)

---

### Post by Amazing-q3 on 2010-09-02
it works. thank you.

---

### Post by Strunz on 2010-09-11
> **VolatileMember said:**
> It seems that they renamed usb_buffer_alloc and usb_buffer_free in 2.6.35 into usb_alloc_coherent and usb_free_coherent. Attached is a patch which fixes the compile errors. Let me know if the driver works for you now!

(driver version: DPO_RT3070_LinuxSTA_V2.3.0.4_20100604)

Hello,

can you please tell me how to patch this diff-file???
I`m only a newbie:-(

Regards
Strunz

---

### Post by VolatileMember on 2010-09-11
cd DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/
patch -p1 -i /path/to/patch

does it work?

---

### Post by sheekeebut on 2010-09-16
> **VolatileMember said:**
> cd DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/
patch -p1 -i /path/to/patch

does it work?

It works, but I can't find any networks.

The patch compiles fine for me. I was having the same compile errors as hulmeman when I switched to the 2.6.35 kernel on my Arch installation. I don't have anything else other than my Hardy install, and with its 2.6.24-27 kernel, I have nothing to compare to.

Now the module is fine, but I haven't been able to get the adapter, with the module installed, to work.

*ifconfig* shows my ra0 interface, but no ip.
Can't connect through my wicd, because wicd can't find any networks at all. Very Strange.

*iwconfig* showed that it I didn't even have a default configuration.
Realized that the *make install* of the drivers didn't copy an RT2870sta.dat file to my /etc/Wireless/RT3070STA because it was not able to find it in the source folder.
I thought maybe it was the missing file that didn't allow me to use the device.

I tried copying the RT2870sta.dat file from the one functioning on my Hardy installation, same permissions and all.
*iwconfig* showed me a default configuration, but wicd still couldn't find any networks.

Realized that the drivers had created the RT2870sta.dat file in the source folder after all, and the *make install* error meant to say that it was looking in the wrong folder to copy the source RT2870sta.dat file from. Ugh, this is tough for those who learn code simply from making all the corrections to get this driver to work.

Copied the above file to the /etc/Wireless/RT3070STA/ *as well as* /etc/Wireless/RT2870STA/ , as all of you know that sometimes you have to rename that folder for this driver to work. But again, no detected networks.

Now I have a feeling I didn't build a good driver. I doubt wicd has anything to do with this problem, because *ifconfig* shows that the ra0 interface is not sending any packets whatsoever. Any other options?

Any ideas?

---

### Post by hulmeman on 2010-09-28
> **sheekeebut said:**
> It works, but I can't find any networks.

The patch compiles fine for me. I was having the same compile errors as hulmeman when I switched to the 2.6.35 kernel on my Arch installation. I don't have anything else other than my Hardy install, and with its 2.6.24-27 kernel, I have nothing to compare to.

Now the module is fine, but I haven't been able to get the adapter, with the module installed, to work.

*ifconfig* shows my ra0 interface, but no ip.
Can't connect through my wicd, because wicd can't find any networks at all. Very Strange.

*iwconfig* showed that it I didn't even have a default configuration.
Realized that the *make install* of the drivers didn't copy an RT2870sta.dat file to my /etc/Wireless/RT3070STA because it was not able to find it in the source folder.
I thought maybe it was the missing file that didn't allow me to use the device.

I tried copying the RT2870sta.dat file from the one functioning on my Hardy installation, same permissions and all.
*iwconfig* showed me a default configuration, but wicd still couldn't find any networks.

Realized that the drivers had created the RT2870sta.dat file in the source folder after all, and the *make install* error meant to say that it was looking in the wrong folder to copy the source RT2870sta.dat file from. Ugh, this is tough for those who learn code simply from making all the corrections to get this driver to work.

Copied the above file to the /etc/Wireless/RT3070STA/ *as well as* /etc/Wireless/RT2870STA/ , as all of you know that sometimes you have to rename that folder for this driver to work. But again, no detected networks.

Now I have a feeling I didn't build a good driver. I doubt wicd has anything to do with this problem, because *ifconfig* shows that the ra0 interface is not sending any packets whatsoever. Any other options?

Any ideas?

Did you rename the file in '/etc/Wireless/RT3070STA/' to RT3070sta.dat?

---

### Post by hulmeman on 2010-09-28
> **VolatileMember said:**
> It seems that they renamed usb_buffer_alloc and usb_buffer_free in 2.6.35 into usb_alloc_coherent and usb_free_coherent. Attached is a patch which fixes the compile errors. Let me know if the driver works for you now!

(driver version: DPO_RT3070_LinuxSTA_V2.3.0.4_20100604)

Works fine Vol, Thanks very much.

---

### Post by jackpipe on 2010-10-02
I know this is listed as solved, but has anyone got this driver working in AP mode?

Looking at the latest driver release notes, it has item #9

> 9. Fix mgmt ring full issue: It happened only in big-endian platform and quickly switch the network type between Infra and Adhoc mode.

Also the driver readme itself seems to be from the 2870 driver, but says:

> This driver implements basic IEEE802.11. Infrastructure and adhoc mode with open or shared or WPA-PSK or WPA2-PSK authentication method. NONE, WEP, TKIP and AES encryption.

Also the ibeini project are using this driver, I think they need more than just client mode, monitor and injection perhaps?

Looking in the driver code there are references to infrastructure mode too, but is this all just refering to client modes ?

Has anyone got it working?

---

### Post by DracoFlameus on 2010-10-15
Noob here. Thanks for the instructions in your first post! I have a problem though :(

When I enter
```
$patch -p0 < rt3070-2.6.31-compile.patch
```

I get the following errors:

```
patching file 2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp_os.h
Hunk #1 FAILED at 53.
Hunk #2 FAILED at 63.
2 out of 2 hunks FAILED -- saving rejects to file 2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp_os.h.rej
patching file 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c
Hunk #1 FAILED at 1506.
Hunk #2 FAILED at 1544.
2 out of 2 hunks FAILED -- saving rejects to file 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c.rej
patching file 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_main_dev.c
Hunk #1 FAILED at 504.
Hunk #2 FAILED at 520.
Hunk #3 FAILED at 531.
3 out of 3 hunks FAILED -- saving rejects to file 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_main_dev.c.rej

```

I'm working with Ubuntu 10.10.

**EDIT**: Nevermind, I'm at least one step further and got the driver installed. Still not working although I confirmed that it's the correct one. Well, I'll keep looking for instructions. Seems there are a lot of problems with this chip and it needs alot of luck to get it working.

---

### Post by cumulonix on 2010-11-05
Noob here, on 10.10 (Maverick Meerkat).

lsusb detects my device.
When I enter
```
$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
...
Bus 002 Device 005: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter

```

I downloaded the latest drivers from Ralink. They seem to be a different one : DPO_RT3370_LinuxSTA_V2.4.0.1_20100831, compared to the ones being discussed here. I followed the instructions on that, but I am unable to compile.
...DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/os/linux/../../common/crypt_md5.o] Error 1
there seems to be multiple errors with DPO_RT3370_LinuxSTA_V2.4.0.1_20100831/common/crypt_md5.c

After pulling my hair out, I decided to use an older driver from 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2
I went ahead and followed dablus's suggestions on [feb 1st in this thread.]("http://ubuntuforums.org/showthread.php?t=1285828&page=5").
In step 7 of his instructions, I get multiple compile time errors:
.../wifi_old_2/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
.../wifi_old_2/os/linux/../../os/linux/rt_linux.c:1510: error: ‘struct net_device’ has no member named ‘open’

Can someone point me to a complete solution for the RT2070 chipset for 10.10?

---

### Post by hernanp on 2010-11-05
I think maverick already include drivers for 2070...

---

### Post by mbonet on 2010-11-14
I can confirm that rt2070 chipset is not working in 10.10 (Maverick) by default. 

Even Ralink published a new driver [Linux STA 2.4.0.1]("http://www.ralinktech.com/download.php?t=U0wyRnpjMlYwY3k4eU1ERXdMekEzTHpBNUwyUnZkMjVzYjJGa05ETTVOalU0TXpVeU5pNWllakk5UFQweU1ERXdYekEzTURsZlVsUXlPRGN3WDB4cGJuVjRYMU5VUVY5Mk1pNDBMakF1TVM1MFlYST1D") (Jul 10) is still not working. :( I patched the code for 2.6.35-22. Because the latest patch you posted is for 2.6.35-1 and source is slightly different. 

([DracoFlameus]("http://ubuntuforums.org/member.php?u=262003") I bet this is your issue you are trying to apply an incorrect patch.)

In my case everything is installed properly but interface is not showing up.

```
modprobe rt2870sta
dmesg | tail
```This is what I get:
```
rtusb init --->
usbcore: registered new interface driver rt2870
```But if:
```
ifconfig
```I get:
```
eth0 ...
lo ...
```ra0 interface is missing! :(

All the steps are done ... blacklisted everything, make && make install, etc... But still not working, any clue?

---

### Post by ellynx on 2010-11-21
I have the same setup as mbonet, and probably the same issue :) have not yet come that far. Any solutions?

Though my D-Link dwa-140 worked occasionally when running livecd, I wonder what's the name  of the driver in use. Could be nice to just get it up long enough to run some apt-getting because I think I have to download the header file to compile the driver (RT2870) properly, and now I don't have internet on my stationary.

---

### Post by pesarak on 2010-11-29
2010-11-29
beginers guide.

Step by Step Guide to :  ;)
Install Wireless LAN USB Adapter Driver RT 2070
on Ubuntu 10.10 Maverick Meerkat

my system:
ubuntu 10.10
TP-Link TL-WN321G V4 ($lsusb -> Ralink 2070)


i try to compile and install latest RT2870 driver from vendor site
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
but when installed device was not detected by system
ifconfig and iwconfig do not show ra0 that expected.
i get error if i try "$ ifconfig ra0"
ra0: error fetching interface information: Device not found
"$ dmesg |grep rt" show that
driver rt2870 failed to start with error -1


finally i found this tutorial    :P
[http://ubuntuforums.org/showthread.php?t=1285828](http://ubuntuforums.org/showthread.php?t=1285828)
i decide to install an old version of driver RT3070
for my RT2070.(that is not available on vendor site)
im do it with some additioal detail because of new
kernel in ubuntu 10.10 rather to 9.10 in this taturial.
and finally all things are ok and my device work out
of box.this old driver also support monitor mode.
thanks to lesnoland.:KS   :p   :P


i follow these step most of them are same as main tutorial
[http://ubuntuforums.org/showthread.php?t=1285828](http://ubuntuforums.org/showthread.php?t=1285828)
but some more step in compiling added to support ubuntu 10.10
(enter command in terminal with sudo before if you get error related 
to permition/operation not permitted/...)


1)download driver RT3070USB(RT307x) from
[http://www.sendspace.com/file/xfk1tg](http://www.sendspace.com/file/xfk1tg)
or
[http://ubuntuforums.org/attachment.php?attachmentid=194546&d=1307534414](http://ubuntuforums.org/attachment.php?attachmentid=194546&d=1307534414)
or

[http://www.4shared.com/file/q24_oKm9/2009_0525_RT3070_Linux_STA_v21.html](http://www.4shared.com/file/q24_oKm9/2009_0525_RT3070_Linux_STA_v21.html)


2)connect device and check WLAN USB hardware ID to be 2070/3070/2870 or other
$lsusb 
  see something like this: ralink 148f:2070
  see WLAN USB hardware ID and disconnect it from usb

3)extract archive file in step 1 by any archive manager or use this code
$sudo su
#tar jxvf 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2

4)ADD Device ID to c++
file located 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/usb_main_dev.c
under section #ifdef RT3070 using any text editor

{USB_DEVICE(0x148F,0x2070)}, /*your comment Ralink 2070 */

you can add your own USB wireless hardware ID by changing 148f and 2070
to any other number get from step 2.

-----------------------------------
5)this step added for ubuntu 10.10 to compile without errors of
"error: implicit declaration of function â&#8364;&#732;usb_buffer_freeâ&#8364;&#8482;"
"error: implicit declaration of function â&#8364;&#732;usb_buffer_allocâ&#8364;&#8482;"
during compile. if you have other version of ubuntu except 10.10
just skip this step then if you see such error during 'make' go back
and do it.
open this file using text editor:
2009_0525_RT3070_Linux_STA_v2.1.1.0/include/iface/rtmp_usb.h
replace all instances of usb_buffer_alloc with usb_alloc_coherent
and all instances of usb_buffer_free with usb_free_coherent 
save and close
this error is because of functions that have been renamed in new kernel
you can read more info at:
[http://lkml.org/lkml/2010/4/30/111](http://lkml.org/lkml/2010/4/30/111).
[http://xlcwu.wordpress.com/2010/07/09/build-rt3070-kernel-module-on-ubuntu-10-04-lucid-lynx/](http://xlcwu.wordpress.com/2010/07/09/build-rt3070-kernel-module-on-ubuntu-10-04-lucid-lynx/)
--------------------------------------

--------------------------------------
6)this step is for WPA support
you can skip this step but your driver will not support WPA Security
and gnome network manager probebly does not show your device
it is recommended to do it:

open README_STA_USB and follow section 3 in this file or simply
In os/linux/config.mk 
set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
save and close.
--------------------------------------

--------------------------------------
7)this section is for prevent errors of
"error: â&#8364;&#732;struct net_deviceâ&#8364;&#8482; has no member named â&#8364;&#732;openâ&#8364;&#8482;"
...
"â&#8364;&#732;struct net_deviceâ&#8364;&#8482; has no member named â&#8364;&#732;validate_addrâ&#8364;&#8482;"
during compile. you can skip this step and if you during make have
got this error go back and do it.

download Patch file from Attachment:
[http://ubuntuforums.org/attachment.php?attachmentid=132572&d=1256080042](http://ubuntuforums.org/attachment.php?attachmentid=132572&d=1256080042)
at the end of post:
[http://ubuntuforums.org/showthread.php?t=1285828](http://ubuntuforums.org/showthread.php?t=1285828)

or from
[http://www.4shared.com/file/XwZgLx-Y/rt3070-2631-compilepatch.html](http://www.4shared.com/file/XwZgLx-Y/rt3070-2631-compilepatch.html)

paste to same folder as you paste driver in step 1
run this code
$gunzip rt3070-2.6.31-compile.patch.gz

$patch -p0 < rt3070-2.6.31-compile.patch

you will see
patching file 2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp_os.h
patching file 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c
patching file 2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_main_dev.c

----------------------------------

8 )disable previous RT2870 driver to ensure that your driver work
open window in root permition
$gksudo nautilus
go to /etc/modprobe.d/blacklist.conf
open file with text editor and add these line to bottom:
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
close and save.
run these command to disable this driver
$sudo rmmod rt2x00usb
$sudo rmmod rt2x00lib
$sudo rmmod rt2800usb


9)Compile source code

run this to go to driver folder:
$cd 2009_0525_RT3070_Linux_STA_v2.1.1.0/
run this to compile files:
$sudo make

wait untill complete.

/*-------
default ubuntu 10.10 have c++ compiler in default and sufficient for
compiling above driver but if you have not and 'make' not work in
your system you can get it by this step:
$sudo apt-get install build-essential fakeroot dpkg-dev
$sudo apt-get install linux-headers-$(uname -r)
---------*/


10)Install the driver
$sudo make install



11)some manual file copying
Copy the .DAT file to /etc/Wireless. using following code.(the install script should do it but just in case).
Also copy the rt2870.bin file to /lib/firmware.
(command meaning : mkdir=make directory; cp=copy ) ;)

$sudo mkdir -p /etc/Wireless/RT2870STA
$sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/
$sudo apt-get install tofrodos
$sudo apt-get install dos2unix
$sudo dos2unix /etc/Wireless/RT2870STA/RT2870STA.dat
$sudo chmod +x /etc/Wireless/RT2870STA/RT2870STA.dat
$sudo cp common/rt2870.bin /lib/firmware/


12)Start the module !!!
$sudo modprobe rt3070sta

/*-------------
this is not problem in ubuntu 10.10 but if
network manager does not show your WLAN device or
If when you are trying to load the module you receive the following (on Karmic):
$sudo modprobe rt3070sta
$dmesg | grep rt3
815108.907620] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned
And your device is NOT detected,
do the following :

copy the rt3070sta.ko file in the staging directory like this:

$cd os/linux
$sudo cp ./rt3070sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/rt3070/
$sudo rmmod rt3070sta
$sudo modprobe rt3070sta

thanks to marshaf (post #125) (i edit a mistake) :
-------------*/


13)Test to see if it works.
Connect your WLAN USB Dongle and then

$ifconfig
$iwconfig

note that try both command not just one.
if you see ra0 by one of them then all ok!

/*-----------------
if ra0 not detected you have a long way ahead
you can try:
$dmesg | grep rt    => to see is driver loaded
$sudo rmmod rt3070sta => to disable driver
$sudo modprobe rt3070sta => to enable again
$lsusb   => to list all usb device
$modinfo rt3070sta   => to display module info
$lsmod  => to list module
unplug all usb
try another usb port
ensure that your Device ID is supported by this Driver
see README_STA_usb in 2009_0525_RT3070_Linux_STA_v2.1.1.0
search the exact error you get in google
....
*/------------------



14) Configure the card.
you can find numerous tutorials, the configuration is exactly the same as for the rt2870 chipset.
you can also see README_STA_usb in 2009_0525_RT3070_Linux_STA_v2.1.1.0
you can try 'network manager'(in notification area of ubuntu panel ,see wireless network)
you can also try other GUI tools like WICD

--------------------------

15) if you want monitor WLAN traffic passively using aircrack-ng
   you must set your card in monitor mode and also edit sensitivity
   (in my system when the card is in monitor mode , no traffic captured unless
    i edit sensitivity by changing register value in real time at another terminal)

sudo ifconfig ra0 up          ---> put WLAN up
sudo airmon-ng start ra0      ---> put WLAN up 
iwconfig ra0                  ---> show network card status
sudo iwconfig ra0 mode monitor ---> put your card in monitor mode
sudo airodump-ng ra0    ---> sniff traffic passively
sudo wireshark          ---> run wireshark in root permition ,select ra0 to sniff traffic passively

EDIT Sensitivity :
(only if no traffic detected do this)
open another terminal and change register value while sniffing:
iwpriv ra0 bbp         ----> show register value for ra0
iwpriv ra0 bbp 4=0     ----> set register R04 value=0  (in my system this is work but you may edit other registers to get work)

-------------------------



//END!
thanks to lesnoland for excellent tutorial:
Tenda W541U V2.0 Wireless USB Adapter / Ralink RT2070 How To
[http://ubuntuforums.org/showthread.php?t=1285828](http://ubuntuforums.org/showthread.php?t=1285828)

---

### Post by naja on 2010-11-29
THANK YOU VERY MUCH !!!

i bought an alfa usb adapter with rt3070 chipset. the stock driver rt2870sta couldnt find the most powerfull signal from accesspoint, which i find a bit wierd, i had to install windows to be able to get connected :cry. i tried to install the newset driver from ralink, but as you said they changed few things. I was able to install it, but networkmanager wont find it, wpa_supplicant nag about it. I was able to list every accesspoint but the topping on the ice  was that I needed TTLS PAP protocols, which none of the other GUI tools allow to connect to /tryed tweaking wicd, wifi-radar crashed/. but now you freed me. at last no more aero interface for me.

Thank you again !!!

---

### Post by telecoda on 2010-12-11
Thanks for this, I used your instructions to compile and install another driver from Ralink for an old wireless USB dongle using RT2770.

Had to edit the usb_buffer_alloc and usb_buffer_free references as suggested to compile, then happy days.

---

### Post by biji on 2010-12-14
Thank you..... it worked hahahha
the most important part is, adding my device id to source:

#Bus 002 Device 014: ID 148f:2070 Ralink Technology, Corp. 

Using latest driver is easier for 10.04, see attachment

grep -rni 0x148F source_path
and add this:
...
        {USB_DEVICE(0x148F,0x2070)}, 
...

---

### Post by marshaf on 2011-01-04
> **pesarak said:**
> 2010-11-29
beginers guide.

Step by Step Guide to :  ;)
Install Wireless LAN USB Adapter Driver RT 2070
on Ubuntu 10.10 Maverick Meerkat
...
Thanks a lot. My TP Link TL WN321G now works!!

But in step 12 of your guide.
sudo cp ./rt**k**3070sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/rt3070/
should be 
sudo cp ./rt3070sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/rt3070/

---

### Post by bdargan on 2011-01-09
Great Post!! 

I had to follow all the patches to get it working on MSI wind 123 (internal wifi is stuffed) and I had an asus usb n13 handy.

only thing I needed to do was to change the patch command as I had a more recent driver to patch.

patch -p1 < patch-file

---

### Post by qingdan on 2011-01-14
Thanks very much!

---

### Post by megavolt500 on 2011-01-22
Oh well. I suppose I'm STILL having problems.
I am a total newbie, running Ubuntu 10.10 (upgraded). I am trying to get my TP-Link wn321g ver4 working.
I followed the directions (which are great - thanks) but I have some problems.
First of all, when I tried to blacklist those three drivers (rt2x00usb ...etc), I was told that they don't exist. So I continued.
All was going well until I tried installing. I then got this:

make -C /home/boss/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/boss/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/boss/2009_0525_RT3070_Linux_STA_v2.1.1.0/RT2870STA.dat /etc/Wireless/RT3070STA/.
install -d /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3070sta.ko /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/
install: cannot stat `rt3070sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/boss/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux'
make: *** [install] Error 2

I did the manual file copying, but when I got to:
sudo cp ./rtk3070sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/rt3070/

I got:
cp: cannot stat `./rtk3070sta.ko': No such file or directory

When I tried to start the module I got:
FATAL: Module rt3070sta not found

I've been trying to install this for over a week, with no success. Can someone PLEASE help me?
Thanks

---

### Post by woodrow667 on 2011-01-22
megavolt500, check this thread out and _[COLOR=red]DO NOT[/COLOR]_ do anything it says until you contact chili. I am a total nooby so I don't know if this will work for you. He got mine working starting at post number 70.
[http://ubuntuforums.org/showthread.php?t=1670201&highlight=ralink+rt2070&page=7](http://ubuntuforums.org/showthread.php?t=1670201&highlight=ralink+rt2070&page=7)

---

### Post by lesnoland on 2011-01-28
By the things you pasted the build seems to have not worked out ok. Please paste in more detail what output you got after executing the "make" command. I think you got some errors when doing "make", and you ignored them and did "make install".



> **megavolt500 said:**
> Oh well. I suppose I'm STILL having problems.
I am a total newbie, running Ubuntu 10.10 (upgraded). I am trying to get my TP-Link wn321g ver4 working.
I followed the directions (which are great - thanks) but I have some problems.
First of all, when I tried to blacklist those three drivers (rt2x00usb ...etc), I was told that they don't exist. So I continued.
All was going well until I tried installing. I then got this:

make -C /home/boss/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/boss/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/boss/2009_0525_RT3070_Linux_STA_v2.1.1.0/RT2870STA.dat /etc/Wireless/RT3070STA/.
install -d /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3070sta.ko /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/
install: cannot stat `rt3070sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/boss/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux'
make: *** [install] Error 2

I did the manual file copying, but when I got to:
sudo cp ./rtk3070sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/rt3070/

I got:
cp: cannot stat `./rtk3070sta.ko': No such file or directory

When I tried to start the module I got:
FATAL: Module rt3070sta not found

I've been trying to install this for over a week, with no success. Can someone PLEASE help me?
Thanks

---

### Post by megavolt500 on 2011-01-30
In the end I installed compat-wirelessdrivers and started using a new version rt2800usb, which works well.
****

---

### Post by rajthandi27 on 2011-02-13
Hi there,

I am new to linux and i don't know how to apply the patch, i mean which dir i should save the patch file, when ever i try to apply it, i got the following message

can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -rupN 2009_0525_RT3070_Linux_STA_v2.1.1.0.old/include/rtmp_os.h 2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp_os.h
|--- 2009_0525_RT3070_Linux_STA_v2.1.1.0.old/include/rtmp_os.h	2009-05-20 23:33:56.000000000 -0400
|+++ 2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp_os.h	2009-08-04 00:00:46.000000000 -0400
--------------------------
File to patch:

please HELP!

---

### Post by sheekeebut on 2011-02-19
> **hulmeman said:**
> Did you rename the file in '/etc/Wireless/RT3070STA/' to RT3070sta.dat?

I can't believe I've left this thing open for so long...

Yeah, I tried renaming the file. Works great! Thanks! [Solved] for me

---

### Post by SOULTE on 2011-04-25
Hello there;

I just tried to compile and install RT3070 driver for my new TP-Link WN321G v4 card in Ubuntu 10.10 according to the instructions in the 13th page by "pesarak". I got the error *"error: â€˜struct net_deviceâ€™ has no member named â€˜openâ€™" "* and as it's mentioned in the instruction I tried to apply the patch "rt3070-2.6.31-compile.patch" and unfortunately I got another error; :(

```
patch unexpectedly ends in middle of line
patch: **** Only garbage was found in the patch input.
```

what's wrong with that? Only garbage found in the input! What does that means exactly? :confused:

PS: Is this driver compatible and enough for air cracking or...?

---

### Post by pesarak on 2011-06-08
> **SOULTE said:**
> 
PS: Is this driver compatible and enough for air cracking or...?

this driver support monitor mode and thus air cracking
i sniff packet on air with this driver.
but some minor problem with channel selection (it capture all channel even when you select only one of them!
, that is solved with change sensivitity , but in general
 im not happy with "TL WN321G V4" for air-cracking)

you need "aircrack-ng_1.0~rc1-2_i386.deb" in ubuntu 10.10

---

### Post by pesarak on 2011-06-08
Edit Sensitivity 

(in RT2070/RT3070 driver TL-wn321g v4)

use following code to change sensitivity of 
sniffing packet on air when set in monitor mode:

1)
iwpriv ra0 bbp
2)
iwpriv ra0 bbp 4=0

line 1 show all registers value that use by driver
every register have special functionality

line 2 change register R4 to zero that is change sensitivity
in my system.
you can change for example R0 to R20 in real-time while sniffing 
and see result to find a proper register you want.


/*
i add driver and patch to attachment again for mirror link
*/

---

### Post by Xtazy on 2011-07-05
Does anyone please know if this solution would work for other distros ?

---

### Post by thaitang on 2011-11-23
hi gang,

I have a Tenda W311U and in Ubu10.10 it has always showed a connection to a local wireless hub I can connect to fine on my laptop and surf.

So although there a connect is made in NetManager and I am assigned an IP addy I cannot surf any web sites nor ping anything. Like I said the local wireless service works fine for Ubu10.04 on my laptop using its builtin wireless, so there is no problem there.

I did run thru all of the steps pesarak provides on pg13, and although everything ran fine, nothing looks or acts differently: I connect on boot-up or whenever dongle is plugged in or wireless enabled in NetManager, but I cannot surf any pages.

Any ideas? All the steps pesarak lists worked fine without error once I made the necessary changes in the files mentioned for 10.10.

cheers,
tt

---

### Post by universeroc on 2012-01-17
With reading all these above you wrote, I have done make && make install, and patch it. 
Then I modprobe rt3070sta, nothing output in console.
Then I ifconfig I got this more info in attachment.

I did not ifconfig ra0 192.168.1.111 up as I got error msg:

SIOCSIFADDR: No such device
ra0: ERROR while getting interface flags: No such device
ra0: ERROR while getting interface flags: No such device

So I don't know whether I have installed this driver successfully and if not how to do next.

Please help me, thanke you so much in advanced.


If you could make a deb package for W541U v2.0 to make this easy so much appreciated to you.

If you help me make it, I would do my best to it. As I like this you help others and others would help you, we could improve together. This is according to Open Source philosophy.

---

### Post by iliachou on 2012-04-10
> 
It seems that  they renamed usb_buffer_alloc and usb_buffer_free in 2.6.35 into  usb_alloc_coherent and usb_free_coherent. Attached is a patch which  fixes the compile errors. Let me know if the driver works for you now!
[DPO_RT3070_LinuxSTA_V2.3.0.4_20100604.compile_fix_2.6.35-1.patch.txt]("http://ubuntuforums.org/attachment.php?attachmentid=167767&d=1283038248") (2.1 KB, 307 views

Hello guys, help me please. 
I have the same trouble but I try to install this driver 2010_0709_RT2870_Linux_STA_v2.4.0.1 and get the same errors. Probably this patch would suit me, but I don't know how I can edit it to my version.

My kernel version is
3.0.0-12-generic and I don\t know why this probs are available here. 
> 
/home/ilya/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:78:3: error: implicit declaration of function &#8216;usb_buffer_free&#8217; [-Werror=implicit-function-declaration]

---

### Post by WebGraf on 2013-01-13
This is does not work on 3.5.0-21-generic.

---

### Post by Agent24 on 2013-01-14
> **WebGraf said:**
> This is does not work on 3.5.0-21-generic.

What doesn't work? The adapter or the fixes in this thread?

---

