---
title: "Setting up a Wireless Router in 8.04"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by gustoflow on 2009-02-22
I've been through all the trouble of getting wireless cards to work, but I've got a Belkin 54 G wireless router and it works out of the box. However, I need some type of encryption, since a neighbor was killing my bandwidth with god knows what.

I have a F5D7234-4 (model number) and haven't been able to find anything specific or current as to using it in Ubuntu 8.04 64-bit.

Does anyone know of any links to something useful??? Or is there something simple that I'm missing?

Thanks,
Erik

---

### Post by Hobgoblin on 2009-02-22
Your operating system is irrelevant when setting up your router.

Just point your web browser at the setup page, enter the user and password (assuming your neighbour hasn't changed these to stop you shutting him out) and set things up through the web interface.

This is best done from a wired connection, as soon as you change the wireless security you'll lose the wireless connection.

---

### Post by Hobgoblin on 2009-02-22
Since you posted the model number I've downloaded the [manual](http://cache-www.belkin.com/support/dl/man_f5d7234-4_v3000_pm01110-a_g.pdf).

Turn to page 25

Go to [http://192.168.2.1](http://192.168.2.1)

Click login.  If you have not changed the password then leave that blank.  Click submit.

Page 49 has details of securing your network.  I suggest you also change the SSID and the password for the router login page.

---

### Post by SurferGTO on 2009-03-21
hey i attempted to do this (WEP Passphrase) and now I can not connect using WICD and I can log into 192.168.2.1. If i do can get onto the home page but if i attempt to edit any of the seetings I get a page displaying this message:

Duplicate Administrator
This device is managed by 192.168.2.3 currently!!

If i try to open that address i get a page not found error message. It worked no problem before I attempted to change the security settings.

---

### Post by cptrohn on 2009-03-21
> **SurferGTO said:**
> hey i attempted to do this (WEP Passphrase) and now I can not connect using WICD and I can log into 192.168.2.1. If i do can get onto the home page but if i attempt to edit any of the seetings I get a page displaying this message:

Duplicate Administrator
This device is managed by 192.168.2.3 currently!!

If i try to open that address i get a page not found error message. It worked no problem before I attempted to change the security settings.

I have the same router and just went through the same setup, You are supposed to enter 192.168.2.3 into your web browser as the URL, then click onto security and it will pretty much guide you through the set up from there... I wouldn't set up your security as WEP though, it's too easy to beat... I set mine up with WPA...

I can't remember every detail of it, but Belkin had a great tutorial video for it on their support website.

---

### Post by 03taxi on 2009-03-21
Wireless security 101:

hide SSID (makes your router "invisible")
use WPA2 if possible, else use WPA, never ever use WEP
put MAC address of all wifi nic's that are allowed access into the router (MAC filter)

paranoia ??? setup a radius server

---

### Post by helgman on 2009-03-22
> **03taxi said:**
> hide SSID (makes your router "invisible")
...
put MAC address of all wifi nic's that are allowed access into the router (MAC filter)

These two are only stops people from "stumblin'" into your network - if some one WANTS access, these won't help at all. Why? MAC-address and SSID are used when communicating, so the attacker could grab these out of the air ...

I'm not telling you not to use them, just pointing out there limitations.

Regards,
Helgman

---

### Post by SurferGTO on 2009-03-31
I enable WPA2/WPA Passphrase in the router, and edit WICD settings to use encryption and i enter the password, however if i try to connect with encryption enabled it never connects. am i forgetting to do something? I have to go wired, remove the passphrase (go unsecured) and disable encryption in WICD to get wireless back

---

### Post by SurferGTO on 2009-03-31
aaand now I cant connect wired into the router at all. only directly into the modem...

---

### Post by SurferGTO on 2009-03-31
bump

---

### Post by SurferGTO on 2009-04-02
no one can help me out here? Theres no way to externally reset the router and I cant log into it wired or wireless for some reason in order to change the security preferences

---

### Post by helgman on 2009-04-02
Not sure exactly what router you are using but most of them have a rest button that will let you go back to factory default. According to one of the manuals on this page ([http://web.belkin.com/support/download/downloaddetails.asp?download=994&lang=1](http://web.belkin.com/support/download/downloaddetails.asp?download=994&lang=1)), so does the Blekin G Wireless "F5D7230-4" - are you sure there is no reset button?

Regards,
Helgman

---

### Post by kilgore9 on 2009-04-03
Hey Surfer,

I'm having the same problem, and have a thread going on it as well which you can follow, in case I find the answer.  I am trying to connect using Network Manager, so its atleast nice to know that it won't help me switching to wicd.  One step I can push aside.  Thanks!

---

### Post by kilgore9 on 2009-04-04
Ignore my last post....I installed wicd and my problem was solved.  Basically, I also had to configure my router with my username and password from my ISP.  I also got rid of the WEP key and changed to WPA.  The router should confirm that it is connected to the web.  Then with wicd it was as simple as adding the WPA key.  This was the step that always failed with Network Manager.

---

### Post by SurferGTO on 2009-04-08
Thats all I do! I set it up in the router to use WPA and I open up WICD and put the key in there but the damned thing just wont connect. and no theres def no reset button that I can find unless the thing requires some amount of disassembly to get to it

---

### Post by kilgore9 on 2009-04-08
In my router, the reset function is under management, and then in the place where you can set your router settings back to factory settings.  There is a reset button.  There also should be one on the router itself, like a pinhole...you can press it with a paperclip...

---

