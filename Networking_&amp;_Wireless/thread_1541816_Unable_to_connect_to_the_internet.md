---
title: "Unable to connect to the internet"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by XXXTURBO6 on 2010-07-29
First of all I want to let everyone know that I am very new to this system so I need to be walked thru carefully step by step...
 
I downloaded **Ubutu 10.04**
 
My lap top is a **Compaq model # HSTNN-C17C**
 
Router brand is **LinkSys model# WRT54G V8**
 
I have a **Broadcom 4311 wireless card** in this machine.
 
I have hooked up an ethernet cable from the back of my "Linksys" to my lap top and still no luck.
 
I have now been doing search's for hours and recently just entered this in the Terminal;
 
Entered: **[iwconfig]**
 
 
Results: 
 
**[COLOR=blue]lo:[/COLOR]** [COLOR=red]No wireless extentions[/COLOR]
 
**[COLOR=blue]eth0:[/COLOR]** [COLOR=red]No wireless extensions[/COLOR]
 
**[COLOR=blue]wlan0:[/COLOR]** [COLOR=red]IEEE 802.11bg ESSID: off/any[/COLOR]
[COLOR=red]Mode: managed Access Point: Not-Associated Tx-Power=0dbm[/COLOR]
[COLOR=red]retry long limit:7, RTS: off, Fragment: off , Power Management: off[/COLOR]

---

### Post by Naitsirhc Hsem on 2010-07-29
for ethernet try 
```
sudo ifconfig eth0 up
sudo dhclient

```

---

### Post by XXXTURBO6 on 2010-07-29
> **Naitsirhc Hsem said:**
> for ethernet try 
```
sudo ifconfig eth0 up
sudo dhclient

``` BOTH come as:  [COLOR=red][sudo] password for scot[/COLOR]

---

### Post by linux18 on 2010-07-29
> **XXXTURBO6 said:**
> BOTH come as:  [COLOR=red][sudo] password for scot[/COLOR]
they are supposed to, your bringing up the wired interface just type the password and your all set. one question, is your wifi encrypted?

---

### Post by XXXTURBO6 on 2010-07-29
> **linux18 said:**
> they are supposed to, your bringing up the wired interface just type the password and your all set. one question, is your wifi encrypted? The WIFI button on my lap top used to light up blue when it was enabled before and ever since I up loaded the Ubuntu on my lap top and done a restart it will not work!  
 
When I press it Nothing happens, Before it would come on and light up blue..
 
This whole ordeal with this thing not recognizing ANY connection is driving me batty...
 
I need to make at least some progress on this or I will just can this computer and go back to Windows... I never thought this was going to be like this from the start....

---

### Post by XXXTURBO6 on 2010-07-29
> **linux18 said:**
> they are supposed to, your bringing up the wired interface just type the password and your all set. one question, is your wifi encrypted? Okay I entered [sudo ifconfig eth0 up]  and then my password and it says " Command not found"

---

