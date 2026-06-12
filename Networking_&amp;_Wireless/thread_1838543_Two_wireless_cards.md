---
title: "Two wireless cards"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by mattygg on 2011-09-03
Hi all,
 
I have had a look through this forum but havent been ale to find an answer so any elp would be appreciated.
 
I have a netbook with a build in wireless card (wlan0) and i also have an external wireless adapter (wlan1). My plan is to connect to a network via the wlan1 card and use the wlan0 to create an access point.
 
I have managed to create an access point for wlan0. However, the wlan1 card only seems to connect to this point and wont let me connect to any other networks. When i try disconnecting the wlan1 card the wlan0 card also disconnects.
 
I am using the standard network manager which comes with ubunut
 
Does anyone have any advice for me, or any programs they would recommend which may help.
 
I am doing this as my wlan0 card range isnt big enough to connect to the network, whereas the wlan1 card is.
 
Thanks in advance
 
Matt

---

### Post by northd_tech on 2011-09-03
Hi,

You might **possibly** be trying to overcomplicate things a bit, but let's determine what kind of hardware you have first- can you post the results of these terminal commands here:

```
sudo lshw -C network
lsmod
ifconfig
iwconfig
nm-tool
lsusb
lspci -vvnn | egrep 'net|etwork|ireless'
```

---

### Post by mattygg on 2011-09-03
Im not at home at the moment so im unable to post the results.
 
My wlan0 card is the one which comes with the N-150 Samsung netbook i think its a RTL8192E.
 
The wlan1 card is a AWUS036H if that helps.
 
Matt

---

### Post by northd_tech on 2011-09-03
Hi,

From what I remember- Samsung, N150, and Realtek 8192E sound vaguely familiar- once you are certain that you have a Realtek 8192E wireless, would you do me a favor and email "Kidman" at Realtek to see if there is a **newer** Linux driver than the one found here?  (I've done it personally at least 5+ times and waited for a response- and Realtek is D**N quick if "Kidman" isn't on vacation from my experience).

[COLOR=#000000]Wireless LAN ICs [/COLOR]email:   [EMAIL="wlanfae@realtek.com"]wlanfae@realtek.com[/EMAIL]
[http://www.realtek.com/contact/contentView.aspx?Langid=1&PNid=1&PFid=4&Level=2](http://www.realtek.com/contact/contentView.aspx?Langid=1&PNid=1&PFid=4&Level=2)

See my post #44 on the following thread if you do confirm that you do INDEED have a Realtek (81[SIZE=3]**92[COLOR=Red]E[/COLOR]**[/SIZE]) - because that last letter makes a HUGE difference.

**Re: Realtek RTL8192E, Wireless not working**
[http://www.realtek.com/contact/contentView.aspx?Langid=1&PNid=1&PFid=4&Level=2](http://www.realtek.com/contact/contentView.aspx?Langid=1&PNid=1&PFid=4&Level=2)

P.S.  Can you send "Kidman" links to **this** thread, and also to these tagged threads here (in a Linux/Ubuntu context)?:

Realtek [Linux/Ubuntu] 8192E threads:
[http://ubuntuforums.org/tags.php?tag=realtek+8192e](http://ubuntuforums.org/tags.php?tag=realtek+8192e)

[http://ubuntuforums.org/showthread.php?p=11216155#post11216155](http://ubuntuforums.org/showthread.php?p=11216155#post11216155)

---

