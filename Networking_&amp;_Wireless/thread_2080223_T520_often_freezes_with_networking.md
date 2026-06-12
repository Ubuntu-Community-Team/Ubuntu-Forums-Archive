---
title: "T520 often freezes with networking"
date: 2012-11-03
forum: Networking &amp; Wireless
---

### Post by YustAnotherLinuxFriend on 2012-11-03
Hy everybody,

i am using a lenovo T520 (4243) with a intel 6250 chip for networking. I didnt installed any third party drivers, i am using
only the intel HD. After a while sometimes a hour ths system freezes completely. No reaktion on ping etc. I could work over
several hours when networking is disabled, because no (W)LAN
is connected. Thats why i suppose that it has something to do with networking. Currently i am useing Mint13, but i have had the same
problem with 12.04 I already google many keywords but i have no
idea how to fix this.

Many Thanks in advance.

Dietmar

---

### Post by chili555 on 2012-11-03
Probably the best place to start is to look at syslog after it freezes:```
sudo cat /var/log/syslog | grep -e iwl -e etwork | tail -n25
```It will produce 25 lines of output so you can pick out the ones that seem significant.

If there is little output, substitute syslog.1.```
sudo cat /var/log/syslog.1 | grep -e iwl -e etwork | tail -n25
```> After a while sometimes a hour ths system freezes completely. No reaktion on ping etc. Do you mean the whole computer freezes or just the wireless?

---

### Post by YustAnotherLinuxFriend on 2012-11-04
So i had just a freezing event. The system freezes completely. No networking or any keyboard combination i know is acepted.

I am not hundred percent shure when the freeze happend, there is only a time gap at:

Nov  4 19:06:00 t520 udev-configure-printer:...
Nov  4 19:06:11 t520 mdm[1582]: pam_ecryptfs:...

I uploaded the syslog... but i dont find any error or strange messages. I disabled bluetooth and WLAN with switch at the notebook. I imagine that the freezing has not been so often.
Is there a kind of Log-Level which has to be increased?

Best Regards

Dietmar

---

### Post by chili555 on 2012-11-04
> I am not hundred percent shure when the freeze happend, there is only a time gap at:

Nov 4 19:06:00 t520 udev-configure-printer:...
Nov 4 [COLOR="Red"]19:06:11[/COLOR] t520 mdm[1582]: pam_ecryptfs:...
I don't think so, because there is plenty of activity after that, including Network Manager connecting your wired ethernet.> Nov  4 19:06:31 t520 NetworkManager[839]: <info> Activation (eth0) Beginning IP6 addrconf.
Nov  4 19:06:31 t520 NetworkManager[839]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Nov  4 19:06:31 t520 NetworkManager[839]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Nov  4 19:06:31 t520 dhclient: Listening on LPF/eth0/f0:de:f1:77:7b:6e
Nov  4 19:06:31 t520 dhclient: Sending on   LPF/eth0/f0:de:f1:77:7b:6e
Nov  4 19:06:31 t520 dhclient: Sending on   Socket/fallback
Nov  4 19:06:31 t520 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov  4 19:06:32 t520 dhclient: DHCPREQUEST of 192.168.1.114 on eth0 to 255.255.255.255 port 67
Nov  4 19:06:32 t520 dhclient: DHCPOFFER of 192.168.1.114 from 192.168.1.1
Nov  4 19:06:32 t520 dhclient: DHCPACK of 192.168.1.114 from 192.168.1.1
Nov  4 [COLOR="Red"]19:06:32[/COLOR] t520 dhclient: bound to 192.168.1.114 -- renewal in 353344 seconds.
etc., etc.I see this:> [drm:pch_irq_handler] *ERROR* PCH poison interruptBut it seems to be harmless. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1031630](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1031630)> It's simply a matter of us complaining about an interrupt with new (but harmless) meaning.I also see this:> Nov  4 18:01:47 t520 kernel: [20580.294463] watchdog: only one watchdog can use /dev/watchdog.
Nov  4 18:01:47 t520 kernel: [20580.294465] watchdog: error registering /dev/watchdog (err=-16).
Nov  4 18:01:47 t520 kernel: [20580.294466] mei: unable to register watchdog device.I think it's also harmless, but you can read about a fix here: [http://ubuntuforums.org/showthread.php?t=1970325](http://ubuntuforums.org/showthread.php?t=1970325)

Frankly, I don't see a freeze and, more importantly, any issue with networking.

Is this syslog or syslog.1? I'll be happy to look at the other.

---

### Post by YustAnotherLinuxFriend on 2013-02-05
Hey, i just want to double check if someone has already found a solution for this problem.
I already updated the newes Bios Firmware, and installed Blumblebee, which i dont really
under stand, and furhtermore it dont offers me a external dvi monitor. But i think i dont
use it correctly.
The freese still happening sometimes, especially when working with a browser.
Is there a possibility to encrease the log-level with rotating files or something similar?

Best Regards,

Dietmar

---

### Post by HughR on 2013-02-05
> **YustAnotherLinuxFriend said:**
>  After a while sometimes a hour ths system freezes completely. No reaktion on ping etc. I could work over
several hours when networking is disabled, because no (W)LAN
is connected.

What do you mean by freezing?  Is the only cure a reboot, or does the system come back after a pause?

I'm trying to debug a t520 freezing on another continent.  This one locks up hard: no video activity, ALT SYSRQ doesn't work, no response to pings.  The cure is a reboot.

The lockup seems to be associated with playing something with Flash or playing a local video file with totem.  So it isn't (just?) networking.  I wonder if it is a screen-saver event: usually you don't touch the keyboard for long stretches when streaming or watching.

The computer has the nVidia Optimus video but we've selected Intel-only.  We haven't tried bumblebee.  I seem to remember telling the BIOS to disable the nVidia stuff.

There are old reports that might or might not be relevant [http://askubuntu.com/questions/53341/complete-freeze-on-a-thinkpad-t520]("http://askubuntu.com/questions/53341/complete-freeze-on-a-thinkpad-t520"), [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/773508]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/773508"), [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/728101]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/728101")

---

### Post by YustAnotherLinuxFriend on 2013-02-24
Sorry for my late answer, but i have to check, why i didnt get an email. So Blumblebee is no solution, i am having still the problem. Even with lan and wlan. I am not sure, but i already read from other users with the same problem useing windows. I am useing the 90W adapter hmm. In the /var/log/syslog and syslog.1 i cant see anything strange. Is there a possibility to increase the loglevel for network activities?

---

### Post by chili555 on 2013-02-24
> Is there a possibility to increase the loglevel for network activities?None that I'm familiar with. There are many more logs kept than syslog and dmesg:```
chili@Think410:~$ ls /var/log
alternatives.log    ConsoleKit      kern.log.1          syslog.2.gz
alternatives.log.1  cups            kern.log.2.gz       syslog.3.gz
apport.log          dist-upgrade    kern.log.3.gz       syslog.4.gz
apport.log.1        dmesg           kern.log.4.gz       syslog.5.gz
apport.log.2.gz     dmesg.0         lastlog             syslog.6.gz
apport.log.3.gz     dmesg.1.gz      lightdm             syslog.7.gz
apt                 dmesg.2.gz      mail.err            udev
auth.log            dmesg.3.gz      mail.log            ufw.log
auth.log.1          dmesg.4.gz      news                unattended-upgrades
auth.log.2.gz       dpkg.log        pm-powersave.log    upstart
auth.log.3.gz       dpkg.log.1      pm-powersave.log.1  wtmp
auth.log.4.gz       faillog         pm-suspend.log      wtmp.1
boot                fontconfig.log  pm-suspend.log.1    Xorg.0.log
boot.log            fsck            samba               Xorg.0.log.old
bootstrap.log       hp              speech-dispatcher
btmp                installer       syslog
btmp.1              kern.log        syslog.1
```After a freeze, you might check the suspicious logs; in my estimation, dmesg, dmesg.1, syslog, syslog.1, kern.log, kern.log.1 and the two Xorg logs. 

If there is any warning or triggers that a freeze is imminent, you could also run:```
top
```See what activity is eating all your CPU cycles. Here is a sample from my machine. As you can see, my 'top' processes are firefox and xorg.

---

### Post by HughR on 2013-02-24
> **YustAnotherLinuxFriend said:**
> Sorry for my late answer, but i have to check, why i didnt get an email. So Blumblebee is no solution, i am having still the problem. Even with lan and wlan. I am not sure, but i already read from other users with the same problem useing windows. I am useing the 90W adapter hmm. In the /var/log/syslog and syslog.1 i cant see anything strange. Is there a possibility to increase the loglevel for network activities?

I'm a little confused.  Let me ask again: is this a permenant-until-reboot freeze, or a freeze-for-for-some-time and then things are OK?

I assumed that you meant permanent-until-reboot.  But in that case, the logs will have a hole where things are not recorded.  Of course they are still the best you can get.

---

### Post by HughR on 2013-02-24
More info about the problem with our t520.  We don't know if our problem is the same as YustAnotherLinuxFriend's.

We've tried to duplicate this on Windows.  One reason is that our warranty was about to run out and Lenovo isn't likely to deal with a Linux freezing issue that cannot be duplicated in Windows.  Well, we cannot seem to duplicate it in Windows.  Trying the same tasks that do freeze Linux.

The machine does not seem to be overheating when it locks up.

In the BIOS, you can choose which video system to enable: integrated graphics (Intel HD 3000), discrete graphics (nVidia), or nVidia Optimus (switch to the nVidia chip on demand).  We're experimenting with these choices.  I'm not sure what we've been using up until now, but I'm suggesting that experiments be limited to the first two choices, reducing the number of variables.  The drivers for the first two choices are quite different and so should have different bugs.  I don't think that we've loaded the proprietary nVidia drivers.

I don't think that our problem is network-related since it can be provoked by watching a video from an external USB drive.

I'm wondering if it is related to screen-saving.  I've requested an experiment to test this theory (watch a video, but hit a shift key every few minutes) but I haven't heard the results.

---

### Post by YustAnotherLinuxFriend on 2013-03-20
So when the machine freezes it freezes completely, means even if you  looked a video, the sound is in an endless loop, with a signal length of  ~10 or 100 milli seconds. There is nothing which could be done anymore,  no remote ssh login etc.
I am not sure if it happens on Win7 probably i shoud try this, but my dislike is bigger.
I dont think it is screen saving related, because it happens often while browsing and working, just while moving the mouse. 
I think it is network related because i could work for hours while traveling on rails without umts etc. I disabled network.

Many Thanks four Your Help.

Dietmar

---

### Post by HughR on 2013-03-20
> **YustAnotherLinuxFriend said:**
> So when the machine freezes it freezes completely, means even if you  looked a video, the sound is in an endless loop, with a signal length of  ~10 or 100 milli seconds. There is nothing which could be done anymore,  no remote ssh login etc.
Thanks for that information.  I assume that alt-sysrq stuff doesn't work either.
> 
I am not sure if it happens on Win7 probably i shoud try this, but my dislike is bigger.
It would be a useful datapoint.  As I said, we don't get crashes under Windows so far (we ONLY use it for this testing).
> 
I dont think it is screen saving related, because it happens often while browsing and working, just while moving the mouse.
Oh well, it was a nice theory.

Have you tried browsing with Adobe Flash disabled?  This is a longshot, but our problem seems to be related to video and/or streaming (I'm not 100% sure since I'm remotely debugging this).
>  
I think it is network related because i could work for hours while traveling on rails without umts etc. I disabled network.

Could this be power supply related?  When you are working for hours on rails, are you running off battery?  Anything else different in that situation?

What voltage is your power supply plugged into?  Our t520 is plugged into 220V.  We haven't had a problem with 120V power, but then we were not doing the same things that caused problems.

---

