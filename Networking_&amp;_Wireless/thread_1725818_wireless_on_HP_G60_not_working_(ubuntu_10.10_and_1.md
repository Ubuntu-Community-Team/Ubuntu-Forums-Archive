---
title: "wireless on HP G60 not working (ubuntu 10.10 and 11.04)"
date: 2011-04-10
forum: Networking &amp; Wireless
---

### Post by MistyMountainHop on 2011-04-10
I installed 10.10 on my machine some 2 weeks ago. Since the time I installed it, my wireless hasn't been working. In the HP G60 range of laptops, there's a button (not a switch) to switch the wi-fi card on and off. During boot, my laptop recognizes that my wifi is off (the wifi button is red). However, it changes to blue when it presents my login screen. It doesn't go back to red even upon me pressing it. 
Also, in the 10.10 desktop environment, it doesn't give me an option to enable my wifi because it's all blanked out. I tried upgrading to 11.04 yesterday hoping this would fix it, but unfortunately it hasn't! 
Is this a problem with my wifi card or with some messed up configuration settings somewhere?

---

### Post by MistyMountainHop on 2011-04-10
This is the output of the iwconfig and rfkill list commands I ran a few minutes back (if it helps)

bala@bg-hp60-linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
bala@bg-hp60-linux:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
bala@bg-hp60-linux:~$

---

### Post by MistyMountainHop on 2011-04-10
posting it again because of smiley related issues in the previous post.


bala@bg-hp60-linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
bala@bg-hp60-linux:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
bala@bg-hp60-linux:~$

---

### Post by mcmann on 2011-09-08
Hello, I have the same problem, the driver is the problem. But you can make it work. I have to type this in at every boot-up, but it makes my wifi work...
sudo rfkill unblock wifi

You can then toggle on or off the wifi.  Cheers!   Mcmann

---

### Post by praseodym on 2011-09-08
Hi mcmann,

you can write the line

```
rfkill unblock all
```

(sudo not neccessary) [COLOR="Red"]before[/COLOR] the phrase "exit 0" into the file **[B]/etc/rc.local**[/B]

---

### Post by jonathonparker on 2011-10-18
> **praseodym said:**
> Hi mcmann,

you can write the line

```
rfkill unblock all
```

(sudo not neccessary) [COLOR="Red"]before[/COLOR] the phrase "exit 0" into the file **[B]/etc/rc.local**[/B]

How do I edit that file, to insert that line. I am new to linux. It says access denied when i try to save it.

---

### Post by praseodym on 2011-10-19
With

```
gksudo gedit /etc/rc.local
```

---

