---
title: "bcm43xg sees ap, but will not connect"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by carolinason on 2009-09-08
running a broadcom chipset wireless card wmp300n in ubuntu 9.04, i installed the broadcom sta driver. card is up and running

[COLOR="Green"]$ iwlist scan[/COLOR] - sees the ap [COLOR="Gray"]EDIT**** So now i add this info to iwconfig, right - WRONG read on *****EDIT[/COLOR]
[COLOR="Green"]$ iwconfig eth1 essid "essid name" channel 1 mode Managed ap "Mac Address"[/COLOR] error = 
[COLOR="Red"]Error for wireless request "Set AP Address" (8B14) :
    SET failed on device eth1 ; Device or resource busy.[/COLOR]

[COLOR="Green"]$ iwconfig eth1 essid "essid name" channel 1 mode Managed[/COLOR] - will assign eth1 to the ap [COLOR="Gray"]EDIT**** This did not happen and was part of the problem ******EDIT[/COLOR]

[COLOR="Green"]$ dhclient eth1[/COLOR] - times out

this card connects to the ap with 9.10 alpha 5, but only during a live cd session, a list of ap's is presented and i choose the correct ap and it will connect AWESOME, HOWEVER if i install 9.10 onto the pc, i'm not prompted for anything not even to install a proprietary driver, if i add the sta driver 9.10 has same issue as with 9.04, the card is up and running, sees available ap's, but will not get an ip with dhclient or wifi-radar, which lists ap's as well.

i used to run ndiswrapper a while back and had success, but if my card sees the ap, it seems that i am almost there, i just cannot get an ip address? 

any help getting this working in 9.04 would be appreciated. this card has no problem in windows or a live cd session of 9.10, but i prefer to run 9.04 at this time/ please help so i don't have to run windows!

---

### Post by carolinason on 2009-09-09
i see

---

### Post by carolinason on 2009-09-09
ndiswrapper is doing the same thing

i wonder since there is no encryption key on the ap if that has something to do with it. how frustrating.

---

### Post by carolinason on 2009-09-10
Here is the fix.

Don't add the ap [COLOR="Gray"]EDIT*** in the cli ***EDIT[/COLOR], use the network manager to add the wireless connection. i used 
[COLOR="Green"]$ sudo ifconfig [/COLOR]
to get my wireless card's mac address and 
[COLOR="Green"]$ sudo iwlist scan[/COLOR]
to get the name of the ap.

go to system->preferences->network connections. click the wireless tab. click the add button and enter the ap name in the ssid field and your wireless card's mac address in mac address field.

bam! this worked for me, sorry none of the thousands of ubuntu heads could figure this out.

---

### Post by mechsin on 2009-10-10
I am having problems getting my card to show up its a netgear WN311B but has the same chip set.  BCM43XG (14E4:4329). I was just wondering are you 32 bit or 64 bit.

---

### Post by carolinason on 2009-12-03
32 bit. Sorry so late. I fixed some issues on my wireless, by disabling ipv6.

---

