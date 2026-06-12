---
title: "Broadcom BCM4313 802.11b/g/n Wireless Card Not Connecting To Network"
date: 2013-07-01
forum: Networking &amp; Wireless
---

### Post by jeffro97 on 2013-07-01
So, I upgraded to Ubuntu a few months ago, but in the installation, it tried and failed to connect to my network, then when the installation finished, and my computer came mback up from rebooting, it wouldn't connect. I tried the help manual, but that didn't do me any good. I looked into Software Sources: Additional Drivers, and it said its being used with an alternate driver. Could anyone else help me with my problem?

---

### Post by Charlotte18 on 2013-07-01
Can you be more specific about the problem? For example, do you see your wireless SSID in Ubuntu but cannot connect? Or is the wireless card not working at all?

---

### Post by jeffro97 on 2013-07-01
It shows the SSID, and I can attempt to connect to it, but it never will connect to the network. The card seems to be working otherwise, but for some reason, i can't get it to connect.

I ran ```
nm-tool
``` and this is what I got.

[TABLE="width: 500"]
[TR]
[TD]Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        00:26:82:DF:F1:5F

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


[/TD]
[/TR]
[/TABLE]

---

### Post by varunendra on 2013-07-03
Hello jeffro97,

Please follow the "Wireless Script" link in my signature and post back the results as asked in the linked post.

---

### Post by jeffro97 on 2013-07-03
[ATTACH]244373[/ATTACH]

Did it.

---

### Post by varunendra on 2013-07-03
The driver you currently have in use is known to have issues with this particular card that you have (BCM4313). For some, the older version of this driver (wl) works, for others the native brcmsmac works better.

Regardless of the driver in use, there are a few common suggestions to improve your connectivity -

[INDENT]1) Turn the power management off on the wireless interface -
```
sudo iwconfig eth1 power off
```

2) Change the encryption type in your router from WEP to WPA2-PSK (AES)[/INDENT]

Try these first and see if you can connect. Although given this combination's reputation I doubt if it is going to help, but is worth a try. If it still can't connect, please try removing the current proprietary driver and use the native one instead -
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
sudo modprobe -v brcmsmac
```

If this doesn't help either, run the wireless_script again and post back the new report.

There is another tested workaround that has worked for many, but I want to try the native one first : [http://ubuntuforums.org/showthread.php?t=2140640&p=12629619#post12629619](http://ubuntuforums.org/showthread.php?t=2140640&p=12629619#post12629619)

---

### Post by jeffro97 on 2013-07-04
I can't change my WEP to WPA cause I don't have the power to do that (parents wouldn't allow it), but when I ran the second option, I shut it down afterwards (I was heading out, then upon booting up later, it connected me via the internal card to my network. THANK YOU!

[ATTACH]244409[/ATTACH]

Here's the file if you still wanna look at it.

Now, I'd mark it solved, but I can't find the prefix box to change it to [Solved].

---

### Post by varunendra on 2013-07-04
> **jeffro97 said:**
> but when I ran the second option, I shut it down afterwards (I was heading out, then upon booting up later, it connected me via the internal card to my network. THANK YOU!

You're welcome ! :)

But please confirm - which second option? "sudo iwconfig eth1 power off" ?

Because you don't seem to have removed the wl driver yet (or you ran the script BEFORE removing it). Doesn't matter as long as it works, but will help us to offer better help next time, as well as searchers looking for help. :)

---

### Post by jeffro97 on 2013-07-10
I ran the ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -v brcmsmac[/FONT][/COLOR]
``` then rebooted, tried logging on, and it connected.

---

