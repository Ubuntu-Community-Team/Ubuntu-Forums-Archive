---
title: "driver isnt running"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by kenyard on 2011-09-03
Ok my issue at the moment is i updated to kernel 3 in the hopes i wouldnt have to use my laptop on one cpu for wireless
Now i cannot activate my wireless on this. grand i go to deactivate the soft block on my wireless, and bam, it puts in a hard block

> kenny@ubuntu:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
kenny@ubuntu:~$ rfkill unblock all
kenny@ubuntu:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
I have no idea why. i looked at my drivers

> kenny@ubuntu:~$ lsmod
Module                  Size  Used by
wl                   2642531  0 [permanent]
brcmsmac              578254  0 my wireless card is 
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
so BOTH of these should be working. but neither is used by the controller.
I just installed the wl module there now to see if i could get it going with that but no luck.
anyone got any suggestions?
my guess is the drivers arent being used by my card or arent compatible or something...
I didnt run the lsmod before thehard block came into place so maybe they were being used before.
there arent any solutions i can find anywhere to this
p.s the brcmsmac module is just a renamed version of the brcm80211 from kernel 2.6.xx which worked for me previous even. so i have no idea why its not working here

also other things that may be wanted
> kenny@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


and when i try to enable the wlan0 with e.g airmon it says
Interface    Chipset        Driver

wlan0        Unknown     brcmsmac - [phy0]SIOCSIFFLAGS: Operation not possible due to RF-kill

problem is i need rfkill to enable it i believe no? or can i just get rid of it or what?

---

