---
title: "Ubuntu 11.04 not displaying any wireless networks"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by Integral1 on 2011-10-06
I just installed Ubuntu 11.04 on my new Lenovo v570 laptop and I can't seem to get my wireless card to work properly (I am typing this by connecting via ethernet cable).  

My wireless card is:  

intel centrino wireless n wimax 6150

Really need help on this situation from an expert Linux user.  I really want to use Ubuntu, but it is almost useless to me if I can't get connected to local wireless networks.

---

### Post by Integral1 on 2011-10-06
here is the list from the rfkill list all command when I am not connected to the internet.  

theory@ubuntu:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
theory@ubuntu:~$

---

### Post by choochus on 2011-10-22
Have you had any luck with this? I just installed 11.04 on my Asus laptop which uses the intel centrino wireless n wimax 6150 but it's not working.

I can see access points, but can't connect to anything. When I click on a connection it takes forever to configure the card, then says it's authenticating, then just goes back to disabled.

Here's my rfkill list all:

0: asus-wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: asus-wimax: WiMAX
        Soft blocked: yes
        Hard blocked: no
2: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

---

