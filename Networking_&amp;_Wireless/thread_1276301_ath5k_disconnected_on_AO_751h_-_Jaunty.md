---
title: "ath5k disconnected on AO 751h - Jaunty"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by crgutierrez on 2009-09-26
"crgutierrez@crgutierrez-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:23:8B:D1:71:9C

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             196.40.3.9
    DNS:             196.40.3.8


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected:confused::confused::confused:
  Default:           no
  HW Address:        00:25:56:13:84:9E

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points "

......and I cannot get it to run after trying quite a few workarounds available

---

### Post by danstoner on 2009-10-01
I also have this problem.  I do know that wireless works with Fedora 11 on this hardware.  I have not had a chance to compare Fedora 11 with Ubuntu to see what they do differently.

I believe I tried all of the workarounds listed here:

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)


Specifically, the following did **not** solve my issue:

```
modprobe -r ath5k acer_wmi; modprobe ath5k
```The hardware toggle switch does not cause the wifi light to come on and wireless does not work.


Will try to submit bug report later tonight but if you are reading this and having this problem, please consider submitting your own bug report.  It would be great to squash this bug before 9.10 is released.

---

### Post by cubiclegangsta on 2009-10-22
Greetings gentlemen, I also have the ao751h.

I ***had*** a similar problem, but was able to resolve it

I am using ubuntu 9.04 jaunty (lpia)

I found this link through another forum thread here (but can't remember which):
[B]
[http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)[/B]

It was written for intrepid ibex (8.10), but here's what I did for jaunty:

Step 1 : Go to the Terminal(Applications->Accessories->Terminal) and type sudo apt-get install linux-backports-modules-jaunty
Step 2 : Now , go to System->Administration->Hardware Drivers
Step 3 : Now you should see the atheros driver listed there** (NOTE: I have "Support for 5xxx series of Atheros 802.11 Wireless LAN cards".This is the one you want).**
Step 4 : Select the driver and click on ENABLE or ACTIVATE

It didn't work for me (yet), so I moved on to the next step:

Step 1 : Go to the Terminal(Applications->Accessories->Terminal) and type gksudo gedit /etc/modprobe.d/blacklist
Step 2 : Now add the following 2 lines to it

blacklist ath_hal
blacklist ath_pci

Step 3 : Save the file and close the terminal
Step 4 : Reboot your PC and you should hopefully have your atheros card working fine in ubuntu 

Now I have working wifi (fingers crossed).

Like I say, I do not know if that is the same issue that you are experiencing, but it is all I can contribute.

Good luck,

CG

---

### Post by crgutierrez on 2009-10-29
GRACIAS!!!!

But I only get the alternate madwifi driver to activate.........

---

### Post by drpjkurian on 2009-11-01
> **crgutierrez said:**
> GRACIAS!!!!

But I only get the alternate madwifi driver to activate.........

Hi
Please visit my thread
[http://ubuntuforums.org/showthread.php?t=1240781](http://ubuntuforums.org/showthread.php?t=1240781)

Best of luck
Dr Kurian

---

### Post by drpjkurian on 2009-11-01
> **crgutierrez said:**
> GRACIAS!!!!

But I only get the alternate madwifi driver to activate.........

Hi
Are you still in Gutsy???
UPGRADE

---

### Post by crgutierrez on 2009-11-09
I works! it works it works it works!!!!!!
But it stops working after a kernel upgrade (from 15 to 16 I think)
Gonna try again.
Best of thanks Dr. Kurian!!!!

---

