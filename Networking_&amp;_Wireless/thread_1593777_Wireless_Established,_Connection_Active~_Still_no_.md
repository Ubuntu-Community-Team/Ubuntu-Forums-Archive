---
title: "Wireless Established, Connection Active~ Still no internet, Compaq Presario c500"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by Rasa1111 on 2010-10-11
Hey all, 

 My first 'issue' with 10.10, 
and it's not on my computer, but on a friends. 

  I am only here for a short time, so Im trying to figure this out as soon as possible. 

  I had to install/activate the Broadcom STA wireless driver,
> These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware....

in order to get the wireless connection to 'come alive", 
and now my wireless connection is established, 
but can still access no website or anything else that requires a connection. :confused:

 What is going on?

 Honestly, I don't have much experience with wireless, 
and the other laptops Ive installed Ubuntu on, they connect to wireless without any fuss, or proprietary drivers activated.

 So this is my first real issue with it, 
and I tried a few different things before i even got this far. lol

 I really thought I had "figured it out", 
and said to myself.. "huh, damn, easier than I thought!" lol

 Then I came to open chromium, and I have no access to internet. 

ethernet works fine [what Im on now], 

but, if i unplug ethernet, and allow wireless to connect ~
it seems to connect just like normal, but the internet goes out.
While wireless connection still established. :(

 Is there any enlightenment for a wireless n00b? :confused:

 Thanks for any help 
tis much appreciated. <3

---

### Post by Rasa1111 on 2010-10-11
as you can see~
connection active, 100%
 [IMG]http://ubuntuforums.org/attachment.php?attachmentid=172005&stc=1&d=1286839109[/IMG]

 But get "this webpage is not available"
and no actual connection..:confused:

 the other laptop in the house is connected just fine.

---

### Post by Rasa1111 on 2010-10-12
anybody home? 

  I brought the laptop home with me to try and figure out, 
but still nada.. 

wireless connection still established,
but no internet unless I plug in my ethernet cable. 

 anyone else, anyone at all experienced this?

---

### Post by gismo93 on 2010-10-12
Gonna bump this thread, hoping for some replies.

---

### Post by irv on 2010-10-12
I know how frustrating it is when you are having problems with a piece of hardware like wifi cards. I had some issues like this awhile back, and finial when back to the version before, and everything worked. Take for example: I have a laptop hooked up on the sound system at the church, and I have to run Ubuntu 9.04 on it because of hardware issues. 
I know it is nice if the newest and greatest works, but sometimes it just doesn't on all older hardware.
One thing you can try if you have a different wifi card is to install it and try it. It just might be the card. If you know what card you are using post it. Maybe other out here are using the same card and can help with other suggestions.

---

### Post by irv on 2010-10-12
I just thought of another thing. Just wondering if you can see other computer on your network. Just get the ip address of one of them and then at the command prompt just type 
> ping [the ip address of the other computer] 
What this will tell you if you can ping it, your network is working, but your gateway to the Internet is not. So it could be a port issue. But I am not sure where it could be changed.

---

### Post by acotte on 2010-10-13
> **Rasa1111 said:**
> 

  I had to install/activate the Broadcom STA wireless driver,
...

in order to get the wireless connection to 'come alive", 
and now my wireless connection is established, 
but can still access no website or anything else that requires a connection. :confused: <3

Yesterday I have reinstalled Meerkat from the official iso (before I was with a RC version).  And now Ubuntu propose two differents drivers for the Broadcom, the second one works and now I can surf from my new DELL Vostro 1220.  BUT now I'm unable to connect my bluetooth mouse.

So I suggest to install from the official release iso.

Good luck

---

### Post by roktiw on 2010-10-15
Got the same problem. ifconfig, iwconfig, dhclient - everything looked fine for wireless, but internet worked only via ethernet. I could even ping every domain and still i was unable to get http connection with wifi.

What was the problem?

I got upgrade from 10.04 to 10.10 and everything was fine. Got wireless connection working, etc. I did the *apt-get dist upgrade* and problem with "wireless established, but no internet connection" started. I ignored the fact that my *Firestarter* was not configurated (what *apt-get* told me) after dist-upgrade. After uninstalling Firestarter everything worked fine.

My advice: **Check your firewall settings**.

---

### Post by Rasa1111 on 2010-10-31
> **roktiw said:**
> Got the same problem. ifconfig, iwconfig, dhclient - everything looked fine for wireless, but internet worked only via ethernet. I could even ping every domain and still i was unable to get http connection with wifi.

What was the problem?

I got upgrade from 10.04 to 10.10 and everything was fine. Got wireless connection working, etc. I did the *apt-get dist upgrade* and problem with "wireless established, but no internet connection" started. I ignored the fact that my *Firestarter* was not configurated (what *apt-get* told me) after dist-upgrade. After uninstalling Firestarter everything worked fine.

My advice: **Check your firewall settings**.

 hey mate, firewall checked, turned it off..
 and still nada.. 

Wireless is active, but no access. 

 Im on 10.04 now, and still the same thing. ..

 anyone got any other ideas?

---

