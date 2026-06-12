---
title: "Broadcom 4315: No wireless after upgrading to Pangolin 12.04"
date: 2012-09-04
forum: Networking &amp; Wireless
---

### Post by PerplexedPangolin on 2012-09-04
Thank you to anyone who can  help.

I searched for a resolution in this forum for my specific driver, but didn't find one, and following the advice of numerous others who had this problem has failed to help, so far.

I have a Dell Inspiron laptop 32-bit and upgraded Ubuntu to Pangolin 12.04, suddenly I have no wireless.  I have a Broadcom STA driver, but when I try to activate it under "Additional Drivers" I get:

"Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

When I go to settings/wireless it says, "Firmware Missing"

Following instructions from Chili555 in a thread very similar to my situation, I opened a terminal window and entered:

lspci -nn | grep 0280

This is what I got:

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

I don't see a solution for "4315" on this forum, yet.  Here is the thread I'm talking about, that's similar to my situation:

[http://ubuntuforums.org/showthread.php?t=1967515&highlight=jockey](http://ubuntuforums.org/showthread.php?t=1967515&highlight=jockey)

I sincerely appreciate anyone who can help, please keep it simple as I'm not as much of a techie as you all, thank you!

---

### Post by chili555 on 2012-09-06
With a temporary ethernet connection, please do:```
sudo apt-get install --reinstall bcmwl-kernel-source
```After it's done, do:
```
sudo modprobe wl
```If there is no error or warning, your wireless should be working.

---

### Post by PerplexedPangolin on 2012-09-07
Thank you for responding Chili555, I get error messages running the codes you recommended:

1. Here is what I get after running the first command:

(Reading database ... 562647 files and directories currently installed.)
Removing pdvdlinux ...
No value set for `/desktop/gnome/powerdvd/default_list'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd'
No value to set for key: `/desktop/gnome/volume_manager/autoplay_dvd'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd_command'
rm: cannot remove `/usr/share/app-install/desktop/pdvdlinux.desktop': No such file or directory
rm: cannot remove `/usr/share/app-install/icons/pdvdlinux.xpm': No such file or directory
/var/lib/dpkg/info/pdvdlinux.postrm: 27: /var/lib/dpkg/info/pdvdlinux.postrm: update-app-install: not found
dpkg: error processing pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 pdvdlinux
E: Sub-process /usr/bin/dpkg returned an error code (1)

2. And here's what I get when I enter the second command:

FATAL: Module wl not found.

When I upgraded to Ubuntu 12.04, I received an error message that Flash and pdvdlinux had not been installed, followed by successful installation of Flash; however pdvdlinux could not be installed, and when I use the Update Manager now, this is what I get:

[http://ubuntuforums.org/showthread.php?t=2053256](http://ubuntuforums.org/showthread.php?t=2053256)

Now I see pdvdlinux is showing up in the error message when I run the codes you recommended to get the wireless up?

Thanks so much for your help!

---

### Post by chili555 on 2012-09-07
I think you have to get your pdvdlinux problems solved first. I am not experienced with this package, but I'd probably remove it altogether:```
sudo apt-get remove --purge pdvdlinux
sudo apt-get update
```Then see if you can then successfully install bcmwl-kernel-source.

---

### Post by PerplexedPangolin on 2012-09-07
Another error message when I tried to remove pdvdlinux, this is what happens when I enter the first code:

Removing pdvdlinux ...
No value set for `/desktop/gnome/powerdvd/default_list'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd'
No value to set for key: `/desktop/gnome/volume_manager/autoplay_dvd'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd_command'
rm: cannot remove `/usr/share/app-install/desktop/pdvdlinux.desktop': No such file or directory
rm: cannot remove `/usr/share/app-install/icons/pdvdlinux.xpm': No such file or directory
/var/lib/dpkg/info/pdvdlinux.postrm: 27: /var/lib/dpkg/info/pdvdlinux.postrm: update-app-install: not found
dpkg: error processing pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 pdvdlinux
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by PerplexedPangolin on 2012-09-07
I fixed the problem with pdvdlinux:

sudo gedit /var/lib/dpkg/info/pdvdlinux.postrm

# Comment out the last three lines & save

sudo gedit /var/lib/dpkg/info/pdvdlinux.postinst

# Comment out the last three lines of this also & save

sudo dpkg -P --force-all pdvdlinux

sudo apt-get update

sudo apt-get upgrade

That took care of it... now I'm running the scripts you gave to fix the wireless and I'll post the resutls.

---

### Post by PerplexedPangolin on 2012-09-07
Here's what happens when I run the following codes:

sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
I don't get any error messages, however the wireless isn't restored, in fact it has disappeared under Settings/Network completely; however under "Additional Drivers" it now says the Broadcom STA Driver is active, but not currently in use on this system (it was inactive before).

I rebooted, that didn't help, but at least the update manager works again (after clearing pdvdlinux, above).

When I run the second line of the code, nothing seems to happen, is that expected?  Any ideas?  Thanks again...

---

### Post by chili555 on 2012-09-07
Let's look for any error messages:```
sudo modprobe wl
dmesg | grep wl
```Thanks.

---

### Post by PerplexedPangolin on 2012-09-07
There was nothing from the first code, but after the second code I got this:

[  143.757765] wl: module license 'MIXED/Proprietary' taints kernel.

I hope we're getting warmer ;)

---

### Post by chili555 on 2012-09-07
I think we are very warm. There are two opinions about how to get this little jewel working:> Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315]I think we know bccmwl-kernel-source is the wrong one. With the ethernet hooked up:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -r wl
sudo apt-get install linux-firmware-nonfree
```Reboot and let us hear a good report.

---

### Post by PerplexedPangolin on 2012-09-07
Wow, it worked!  When I ran the second line I got:

FATAL: Module wl not found.

I ran the third line anyway, rebooted and I've got wireless again... thank so much, Chili555!

Under additional drivers, it says the Broadcom STA driver is not active... I'm going to leave that alone, lol

---

### Post by chili555 on 2012-09-07
> rebooted and I've got wireless again... thank so much, Chili555!Glad it's working! Please use thread tools at the top to mark Solved.

Have fun!

---

### Post by christopher035 on 2012-09-09
> **chili555 said:**
> I think we are very warm. There are two opinions about how to get this little jewel working:I think we know bccmwl-kernel-source is the wrong one. With the ethernet hooked up:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -r wl
sudo apt-get install linux-firmware-nonfree
```Reboot and let us hear a good report.

This worked perfectly for my Dell 5150 wireless problem in Lubuntu 12.04. Thanks!

---

