---
title: "DVBSky T680C on Mythbuntu 14.04 Trusty"
date: 2015-01-10
forum: Mythbuntu
---

### Post by Henk Poley on 2015-01-10
How to make it work. Download the firmware and driver from: [http://www.dvbsky.net/Support_linux.html](http://www.dvbsky.net/Support_linux.html)

The [FONT=Lucida Console]build_dvbc_x64.sh[/FONT] script changes the driver so it only shows supports DVB-C. This makes it DVB-C work in MythTV.

```
mkdir dvbsky
cd dvbsky

wget http://www.dvbsky.net/download/linux/dvbsky-firmware.tar.gz
sudo apt-get install unp && unp dvbsky-firmware.tar.gz
cd dvbsky-firmware
sudo ./copy-firmware.sh
cd ..

wget http://www.dvbsky.net/download/linux/media_build-bst-14-141106.tar.gz
unp media_build-bst-14-141106.tar.gz
cd media_build-bst-14
./build_dvbc_x64.sh
sudo make install 
sudo reboot
```

Had contact with 'stuartm' on #mythtv irc. He'll look at adding a C vs. T/T2 selector in MythTV 0.28

---
**old post**

I'm pretty sure I should be able to get this to work. So I'm merely documenting my travels here, so someone else solves it quicker.

I've installed the [FONT=lucida console]linux-generic-lts-utopic[/FONT] 3.16 kernel. Nvidia VDPAU (h.264) still works, but HDMI audio doesn't (for me). This is not enough to get the card to work. There's no [FONT=lucida console]/dev/dvb/*[/FONT] created. I don't want to run a full custom kernel, so I follow the advice over at the [DVBSky Linux driver page]("http://www.dvbsky.net/Support_linux.html"). Which means I downloaded and built the latest 'upstream' Linux drivers  as described at: [http://git.linuxtv.org/cgit.cgi/media_build.git/about/](http://git.linuxtv.org/cgit.cgi/media_build.git/about/)

```
sudo apt-get update
sudo apt-get install linux-generic-lts-utopic
sudo reboot
```

Then follow: [http://git.linuxtv.org/cgit.cgi/media_build.git/about/](http://git.linuxtv.org/cgit.cgi/media_build.git/about/)

After a reboot DVB-T works. But I didn't test that. I need DVB-C. So next I try install the firmware:

```
mkdir dvbsky
cd dvbsky
wget http://www.dvbsky.net/download/linux/dvbsky-firmware.tar.gz
sudo apt-get install unp && unp dvbsky-firmware.tar.gz
cd dvbsky-firmware
sudo ./copy-firmware.sh
```

This still doesn't make DVB-C work. Next I build the DVBSky drivers for dvb-c:
```
mkdir dvbsky
cd dvbsky
wget http://www.dvbsky.net/download/linux/media_build-bst-14-141106.tar.gz
sudo apt-get install unp && unp media_build-bst-14-141106.tar.gz
cd media_build-bst-14
./build_dvbc_x64.sh
sudo make install 
sudo reboot
```

**This works :)**

Basically they hide the fact that driver supports DVB-T and T2, so MythTV will only see the DVB-C support. I hope this is fixed in MythTV 0.28.

```
--- ./v4l/sit2_mod.dvb	2014-07-25 17:12:50.000000000 +0200
+++ ./v4l/sit2_mod.dvbc	2014-07-27 10:34:18.000000000 +0200
@@ -34,8 +34,8 @@
 }
 
 static const struct dvb_frontend_ops sit2_ops = {
-	.delsys = { SYS_DVBT, SYS_DVBT2, SYS_DVBC_ANNEX_A },
-	/*.delsys = { SYS_DVBC_ANNEX_A },*/
+	/*.delsys = { SYS_DVBT, SYS_DVBT2, SYS_DVBC_ANNEX_A },*/
+	.delsys = { SYS_DVBC_ANNEX_A },
 	/* default: DVB-T/T2 */
 	.info = {
 		.name = "Sit2 DVB-T2/C",
```

But audio doesn't work over nvidia HDMI with the 3.16 kernel :-/

Next I'll try the regular trusty kernel (3.13) and rebuild everything for that.

```
sudo apt-get remove linux-headers-3.16.0-28 linux-headers-3.16.0-28-generic linux-image-3.16.0-28-generic linux-image-extra-3.16.0-28-generic
```

Note that media_build-bst-13-140619.tar.gz for Linux 3.13 does not seem to support the DVBSky T680C. And even though the website says the 'bst-14' is not for 3.13, it still builds and works for our purpose.

You *might* be able to set the default driver to DVB-C with `[FONT=Lucida Console]dvb-fe-tool[/FONT]` before mythtv-backend has started.
```
apt-get install dvb-fe-tool
dvb-fe-tool -d DVBC/ANNEX_A -a 0
```

This would mean you could use either the upstream [media_build.git](http://git.linuxtv.org/cgit.cgi/media_build.git/about/) or [FONT=lucida console]linux-generic-lts-utopic[/FONT] 3.16 kernel, without any extra compilation. You will need to find a way to run it at boot time before mythtv-backend starts.

---

### Post by maliufkan on 2015-01-18
Great post! This helped me fixing my problem.

I want to receive DVB-T2 channels with the DVBSky T680C on Ubuntu 14.04.1
I went through each step of the installation guide very carefully ([http://www.dvbsky.net/download/doc/Linux_driver_installation_Guide](http://www.dvbsky.net/download/doc/Linux_driver_installation_Guide)), but at the end I got the problem with the missing */dev/dvb *directory.

I fixed the problem with these steps:

```
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/media/
```
Instead of the recommended *media_build-bst-13-140619.tar.gz* drivers for my kernel version, I downloaded the next available package of a higher kernel version:
*media_build-bst-14-141106.tar.gz*
Again I went through each step of the installation guide, but with the new package.
After running the *make* command, I got this error: > "Can't locate Proc/ProcessTable.pm"
So I installed processtable:
```
sudo apt-get install libproc-processtable-perl
```
After that I deleted the compiled files, ran *make* again and proceeded with the installation guide steps.

Finally the */dev/dvb/adaptor0* is available and watching DVB-T2 is possbile. Notice: I did not test the HD channels, only SD.

---

