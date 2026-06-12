---
title: "Wireless is disabled"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by bharesc on 2010-09-10
I updated from Ubuntu 9 to 10 some while ago and can no longer connect to the internet via wireless. The computer is a Medion 96290 with a USB wireless card. Running "lsusb" gives: -

bobharesceugh@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 003: ID 064e:a100 Suyin Corp. Acer OrbiCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bobharesceugh@ubuntu:~$ 

Running "ndiswrapper -l" gives: -

obharesceugh@ubuntu:~$   ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save.1, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8187b : driver installed
    device (0BDA:8189) present (alternate driver: rtl8187)
bobharesceugh@ubuntu:~$ 

This tells me a driver is installed but it may not be the correct one. I copied this driver from the Windows driver file.

Network Manager shows "Wireless Network" greyed out and "wireless is disabled".

WICD shows net8187b as the installed driver and that the hardware is present. 

There is a wireless switch on the keyboard which it was not necessary to use in Ubuntu 9 and is inoperative in Ubuntu 10.

I have searched through and applied many suggestions without success and have posted this problem on a couple of forums, again without success.

Can anyone help solve this issue?

Bob

---

### Post by skrap on 2010-09-10
I want to preface this post with a comment.  I have been using Ubuntu since Gutsy on the same laptop with no wireless problems and when I upgraded to 10.04 I cannot connect wireless.  I have been an advocate of Ubuntu since I started using it some six years ago.  I am finding it hard to accept this and I think the developers of 10.04 should be embarrassed about this set back.

I have been searching the boards and working on this problem for about 10 hours and it is very frustrating to have Upgraded my software and created a wireless problem I didn't have before.

I have a Toshiba Satellite with a Realtek 8139 Ethernet board.  It connects flawlessly when I hard wire it.  The "Enable Wireless" is grayed out and is inoperable.  I have read about the ndiswrapper and this may be a work around but the question is why do I have to do a work around in the first place.  As I said the wireless worked fine with Intrepid.

I have the same problem as Bob with the same symptoms.  Pretty sure this is a Kernel problem and all I see is fixes that want me to work around and load drivers etc....  Please help restore my faith in Ubuntu.

Skrap

---

### Post by xX(TFM)Xx on 2010-09-10
ive been lookin at this one too... glad its just a temp 10.4 issue as the last notebook i had was an acer with all sorts of issues this aint so bad this a couple posts on the forum and a couple links u should all check out with the realtek stupid A$$ wireless issue.  ill post that up n please let me know what works on yers as the sat l455d is the only laptop i have and not easy to get a hard lan here n there as i travel so if it works let me know so i dun waste my time... i shoulda used karmic koala i take it lol

---

### Post by xX(TFM)Xx on 2010-09-10
couple other similars

[http://ubuntuforums.org/showthread.php?t=1267961&highlight=toshiba+satellite+wireless](http://ubuntuforums.org/showthread.php?t=1267961&highlight=toshiba+satellite+wireless)

[http://ubuntuforums.org/showthread.php?t=1560645&highlight=toshiba+satellite+wireless](http://ubuntuforums.org/showthread.php?t=1560645&highlight=toshiba+satellite+wireless)

try this solution too below

[FONT=arial][SIZE=2][COLOR=black][FONT=arial][SIZE=2][COLOR=black][FONT=Arial, Helvetica, sans-serif][http://ubuntuforums.org/showpost.php?p=9009017&postcount=26](http://ubuntuforums.org/showpost.php?p=9009017&postcount=26)[/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

hope it helps n again lemme know if its good news

---

### Post by ch13fy on 2010-09-10
I always use wicd for wireless ):P

---

### Post by skrap on 2010-09-11
Problem Solved - went back to intrepid everything is working again.
Not the laptop or the Realtek controller. Ubuntu 10.04 is the problem.  Disappointment abounds.

---

### Post by bharesc on 2010-09-11
Thanks for your responses. Emailed Realtek for driver; awaiting response.
Bob

---

