---
title: "RT2860sta no wifi after resume from sleep"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by Metteke on 2010-10-13
When my akoya mini E1210 with UNR10.10 resumes after sleep my wifi searches forever and then cuts out. When I do iwconfig the card  seems normal for about a minute and then I do iwconfig again it gives gives no id.
Reboot and bang, everything perfect.
Did make new driver from latest ralink driver, as explained by Sven ,but nu change. Also blacklisted the rt2800 and rt2x00.

Seems that after sleep the wifi card driver is not loaded.
Worked like a charm in 9.10 and in 10.4 (upgrade from 9.10).
After update to 10.10, it went wrong.

extra: when I do sudo ifconfig ra0 up I get the message "SIOCSIFFLAGS: Operation not permitted"
Also, after hibernation, no luck...

in dmesg found that the mailbox keeps MCU active, and rt2860 could not be initialised.:

> maarten-laptop kernel: [ 1902.168454] ERROR!!! NICInitializeAdapter failed, Status[=0x00000001]
maarten-laptop kernel: [ 1902.168788] ERROR!!! H2M_MAILBOX still hold by MCU. command fail
maarten-laptop kernel: [ 1902.174003] !!! rt28xx Initialized fail !!!

When Evolution Mail is not used, everything is ok. I know this message is not related to mail, but it helps for a while. After longer period of sleep, same problem again. Firmware problem?

---

### Post by Metteke on 2010-10-13
no one?

---

### Post by toker_tok on 2010-10-15
I have exactly the same issue. If I put the computer to sleep, when it wakes up on battery power, it does not connect. I guess this is one difference.  My  wireless does not connect on battery power, but as soon as I plug in it connects. In fact, if I unplug it when everything is up, within a minute or so it will loose  connection, but then when I replug it connects. Very frustrating. I think it is a kernel issue(not that I know much). Before the upgrade to maverick i had 2.6.32.25 and if I run it with that it still works. But with maverick the new kernel is 2.6.35.22 and that is the problem. I also tried the dailies from kernel:ppa, it is the same. The problem is 2.6.32.25 works fine wrt to w ireless, but once in a while it freezes...very unpleasant....I hope someone can fix this because it was great with lucid. I wish I did not upgrade or there was a way to downgrade.

---

### Post by toker_tok on 2010-10-15
i just did the one thing that I did not try. Installed the firmware. It seems to have worked. I actually am using the original ubuntu driver and not the the ralink one(i tried with that too but there was problems still) but the firmware update part seemed to have helped. 
[http://ubuntuforums.org/showthread.php?t=1573039](http://ubuntuforums.org/showthread.php?t=1573039)

---

### Post by fiepel on 2010-10-18
I have the same issue.

I tried the proprietary ralink driver which reconnects after a suspend, but crashes my desktop regularly.

I also tried the solution of using the ubuntu driver with the latest ralink firmware, but this also crashes my desktop from time to time.

At the moment I do not have a working solution for Ubuntu 10.10.
Ubuntu 10.04 worked fine with the january release of the ralink drivers (including resume).

The only way to get 10.10 wireless up after a resume (apart from a full reboot) is to bring wlan0 down (sudo ifconfig wlan0 down), remove the driver (sudo rmmod rt2860sta), install the driver (sudo modprobe rt2860sta) and then send my laptop to sleep and wake up again (restarting the network service does not suffice for some reason).

I am on a Medion Akoya E1210.

Philippe

---

### Post by fiepel on 2010-10-18
Doing a "modinfo rt2860sta" tells me that the Ubuntu module is using two firmware files: rt3090.bin and rt2860.bin. Ralink only supplies a firmware for rt2860. 

So what did you do with the rt3090.bin file? Just use the Ubuntu one?

---

### Post by toker_tok on 2010-10-18
the freezing issue can be completely a separate one. Check this thread:
[http://ubuntuforums.org/showthread.php?t=1595196](http://ubuntuforums.org/showthread.php?t=1595196)
there are other people suffering from freezes on the battery. maverick upgrade turned out to be very unpleasant. My wireless is still working fine though after the firmware trick.

---

### Post by tlaurent on 2010-12-19
I had the same problem and followed the steps given here ([http://www.twentyways.com/2010/11/19/fixing-wireless-issues-with-asus-eeepc-1000he-running-ubuntu-10-10/](http://www.twentyways.com/2010/11/19/fixing-wireless-issues-with-asus-eeepc-1000he-running-ubuntu-10-10/)) and that solved it.
For information, I'm running Ubuntu 10.10 on eeePC 901.

---

