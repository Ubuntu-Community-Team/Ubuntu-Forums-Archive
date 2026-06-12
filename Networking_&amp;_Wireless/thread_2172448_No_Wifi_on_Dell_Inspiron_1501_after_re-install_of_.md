---
title: "No Wifi on Dell Inspiron 1501 after re-install of dual boot Ubuntu 12.04"
date: 2013-09-05
forum: Networking &amp; Wireless
---

### Post by ljmartz on 2013-09-05
I am new to Ubuntu having installed Ubuntu 12.04 dual boot on my Dell Inspiron 1501 a year ago.  Had to re-install because dependencies were broken beyond repair.  At first install, I was unable to access wireless networks.  Was able to restore connection using

```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
and
```
sudo apt-get install --reinstall linux-firmware-nonfree
```

Tried those commands after re-install and still no wireless connection.

Results of

```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```

are attached to this post.

Any help to get me re-connected to my wifi is greatly appreciated

---

### Post by ljmartz on 2013-09-05
I did discover that my Broadcom driver was not activated, however, after selecting 'activate,' about half way through the process of downloading and installing the process killed my LAN connection to my laptop and would not complete.

---

### Post by chili555 on 2013-09-05
> b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not foundThere is the whole problem. Please obtain a termporary wired ethernet connection and do:```
sudo apt-get install --reinstall linux-firmware-nonfree
```Please note and post here any errors. Now unload and reload the driver:```
sudo modprobe -r b43 && sudo modprobe b43
```Any improvement?

---

### Post by ljmartz on 2013-10-14
Sorry it has taken so long to respond to this post.  Life intervened after the first post and this is the first time I had time to get back to this.

> 
[COLOR=#000000]Code:
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source[/COLOR]
[COLOR=#000000]and[/COLOR]
[COLOR=#000000]Code:[/COLOR]
sudo apt-get install --reinstall linux-firmware-nonfree[COLOR=#222222][/COLOR] 

Already ran above code in Terminal prior to posting in forum for help.  Neither fixed the problem.

The other problem that I have is any attempt to run any type of code having to do with either wifi or LAN connections or any process that even connects to the LAN (like unloading and downloading the driver), immediately kills my Ethernet LAN connection and the only way to reconnect is to re-boot.

---

### Post by chili555 on 2013-10-14
I suggest you reboot with the ethernet detached and see if it works. If not, run and post again:```
dmesg | grep b43
```

---

### Post by ljmartz on 2013-10-14
Rebooting w/o ethernet attached does at least bring up the "WiFi" light.  Under network connections, showing no WiFi networks available.

The STA Broadcom driver is showing that it is not activated in the additional drivers section of System Settings.  Any attempt to activate the driver causes the laptop to immediately disconnect from the ethernet connection.

Cannot post the results of

```
dmesg | grep b43
```

As any attempt to connect to the internet via the ethernet connection causes the computer to disconnect from the connection.  If there is any way to download the driver on the windows side and load it on to a USB key and then load the driver on the Ubuntu side, that might fix the problem.

---

### Post by chili555 on 2013-10-14
> The STA Broadcom driver is showing that it is not activated in the additional drivers section of System Settings. Any attempt to activate the driver causes the laptop to immediately disconnect from the ethernet connection.We would very much like for you to *NOT* activate the STA driver as it is, as you have seen, wrong not only for your wireless but also, remarkably, wrong for your ethernet. Please do not activate it again. Again, please do:```
sudo apt-get remove --purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```After it is done, reboot. Is your ethernet working? Can you then do:```
sudo apt-get install --reinstall linux-firmware-nonfree 
```If not, please run:```
dmesg > ljmartz.txt
```Find the file ljmartz.txt in your user directory and transfer it on a USB key or similar and transfer it to another computer and post it here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/) Please give us the link in your reply.

---

### Post by ljmartz on 2013-10-15
```
sudo apt-get remove --purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```

Returns:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by chili555 on 2013-10-15
> **ljmartz said:**
> ```
sudo apt-get remove --purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```

Returns:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?That usually means that some other application like Software Center or Synaptic is opened and running. Close it out and try again.

---

### Post by ljmartz on 2013-10-15
Fresh boot, nothing open but terminal, not plugged into ethernet

```
sudo apt-get remove --purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```

Still returns

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

---

### Post by chili555 on 2013-10-15
I suggest you do:```
sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock
```And then:```
sudo fuser -cuk /var/cache/apt/archives/lock; sudo rm -f /var/cache/apt/archives/lock
```And finally:```
sudo apt-get remove --purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```Reboot.```
sudo apt-get install --reinstall linux-firmware-nonfree
```

---

### Post by ljmartz on 2013-10-15
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock[/FONT][/COLOR]
```

Caused laptop to lockup.  Do I hard boot and try again?

---

### Post by chili555 on 2013-10-15
> **ljmartz said:**
> ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock[/FONT][/COLOR]
```

Caused laptop to lockup.  Do I hard boot and try again?Yes. If it still locks up,then reboot and try only:```
sudo rm -f /var/lib/dpkg/lock
sudo rm -f /var/cache/apt/archives/lock
```I am starting to suspect much bigger problems here than just wireless.

---

### Post by ljmartz on 2013-10-15
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock[/FONT][/COLOR]
```

Continued to cause lock up.

Ran 
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo rm -f /var/lib/dpkg/lock
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo rm -f /var/cache/apt/archives/lock[/FONT][/COLOR]
```

Both ran without issue.  No data returned.

---

### Post by chili555 on 2013-10-15
> **ljmartz said:**
> 

Both ran without issue.  No data returned.Good! So now how about all the remainder?

---

### Post by ljmartz on 2013-10-15
Do I skip

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock[/FONT][/COLOR]
```

and start with ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo fuser -cuk /var/cache/apt/archives/lock; sudo rm -f /var/cache/apt/archives/lock[/FONT][/COLOR]
```

Or do I do the complete list of code starting with

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock[/FONT][/COLOR]
```

---

### Post by chili555 on 2013-10-15
If the* rm* commands ran without issue, you are ready for:```
sudo apt-get remove --purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```

Reboot.

```
sudo apt-get install --reinstall linux-firmware-nonfree


```

---

### Post by ljmartz on 2013-10-15
Results of
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get remove --purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source[/FONT][/COLOR]
```
Returned:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

---

### Post by chili555 on 2013-10-15
> you must manually run 'sudo dpkg --configure -a' to correct the problem.I suggest you do exactly that.

---

### Post by ljmartz on 2013-10-15
Ran
```
[[COLOR=#000000]*sudo dpkg --configure -a*[/COLOR]/CODE]

Final output shows:
[CODE]DKMS: install completed.
```

Do I now re-boot and run
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install --reinstall linux-firmware-nonfree[/FONT][/COLOR]
```

---

### Post by chili555 on 2013-10-15
If you already removed the bcmwl gang, then yes.

---

### Post by ljmartz on 2013-10-16
[ATTACH]246990[/ATTACH]Complete output from 
```
*sudo dpkg --configure -a*
```
is attached.  Not completely sure that > [COLOR=#000000]bcmwl gang[/COLOR] was removed, but to the best of my understanding reading the output it was.  Would covet your confirmation.

---

### Post by chili555 on 2013-10-16
We see this:> Loading new bcmwl-6.20.155.1+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-52-generic-pae
Building for architecture i686
Building initial module for 3.2.0-52-generic-pae
Done.It looks like part of the configure -a process was to *fix* the bcmwl-kernel-source installation which is incorrect for your device!! Let's try again:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```If you'd like, feel free to show us the results if you have any doubts or questions.

---

### Post by ljmartz on 2013-10-16
Running 
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get remove --purge bcmwl-kernel-source[/FONT][/COLOR]
```

Returns 
```
[COLOR=#000000][FONT=Ubuntu Mono]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.[/FONT][/COLOR]
```

Running 

```
s[COLOR=#000000]*udo dpkg --configure -a*[/COLOR]
```

Returns the same output as before.  One thing I have noticed is that when ```
s[COLOR=#000000]*udo dpkg --configure -a*[/COLOR]
``` completes, I do not get the root directory prompt in the terminal.  The output ends w/ "[COLOR=#000000][FONT=Ubuntu Mono]DKMS: install completed." and then goes to a blinking cursor.[/FONT][/COLOR]

---

### Post by ljmartz on 2013-10-16
Just for kicks and giggles, I re-booted.  Then ran```
[COLOR=#000000][FONT=Ubuntu Mono][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get remove --purge bcmwl-kernel-source[/FONT][/COLOR] [/FONT][/COLOR]
``` It returned  
```
[COLOR=#000000][FONT=Ubuntu Mono]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.[/FONT][/COLOR]
```

Ran ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg --configure -a[/FONT][/COLOR]
```

All same output EXCEPT final line of output reads
```
Segmentation fault
```



I think that your previous assessment that I have a larger problem than just wifi is correct.  Instead of plugging the crack in the dam, I'd like to fix the problem that is causing the crack.  Any help in how to assess my larger problem and fix it is greatly appreciated.

---

### Post by chili555 on 2013-10-17
> **ljmartz said:**
> I think that your previous assessment that I have a larger problem than just wifi is correct.  Instead of plugging the crack in the dam, I'd like to fix the problem that is causing the crack.  Any help in how to assess my larger problem and fix it is greatly appreciated.Of course, the scorched earth approach, reformat and reinstall, cures all ills. Otherwise, you might gain some insight from the message logs after a reboot:```
dmesg > ljmartz2.txt
```Find the text file in your user directory and copy and paste it here and give us the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by ljmartz on 2013-10-30
> [COLOR=#000000]Of course, the scorched earth approach, reformat and reinstall, cures all ills. Otherwise, you might gain some insight from the message logs after a reboot:[/COLOR]
Since I've just done what I thought was the scorched earth approach and ended up with a mess, would it be possible for you to point me to a complete list of steps to take to re-install on a dual boot machine?

---

### Post by chili555 on 2013-10-30
I actually think it's as easy as booting the live DVD and selecting 'something else' and replacing Ubuntu with Ubuntu, leaving your Windows dual-boot in place. However, I don't dual-boot and so I am not an authority to ask. I suggest you ask here: [http://ubuntuforums.org/forumdisplay.php?f=331]("http://ubuntuforums.org/forumdisplay.php?f=331")

---

### Post by ljmartz on 2013-11-01
Used scorched earth and reinstalled.  Took two tries as the first time I installed updates, things got ugly again.  Second install was a success.  Did not activate Broadcom driver. Ran
```
sudo apt-get install linux-firmware-nonfree
```

Unplugged Ethernet, re-booted and low and behold, wifi is back.  Thanks for your help

---

### Post by chili555 on 2013-11-01
Awesome! Glad it's working. Have fun!

---

