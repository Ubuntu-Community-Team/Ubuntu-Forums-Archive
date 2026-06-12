---
title: "Intel 5100 Wireless running at 1mbs"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by waapwoop1 on 2009-05-19
Hi,

In windows my Intel 5100 card connects to the g wireless point at 28mbs+  I seem to be getting an initial connection speed of 11mbs and it goes down to 1mbs after.

I am running Jaunty 9.04. 

I have read this thread  [http://ubuntuforums.org/showthread.php?t=1032617](http://ubuntuforums.org/showthread.php?t=1032617)

and done this:- sudo apt-get install linux-backports-modules-jaunty
 which didn't help

I also found the intel driver at [http://intellinuxwireless.org/](http://intellinuxwireless.org/)  I installed the driver, even though it was already in my /lib/firmware folder.

So I am now stuck. How can i get this working like it does in windows?

Phil

---

### Post by waapwoop1 on 2009-05-19
Download "iwlwifi-5000-ucode-5.4.A.11.tar.gz" from "http://intellinuxwireless.org/?n=Downloads". 
Unzip it to a folder, and copy the "iwlwifi-5000-1.ucode" file to "/lib/firmware" 
And then reboot the machine 

That sets the IWL5100AGN driver.


I also did the above.....

---

### Post by waapwoop1 on 2009-05-20
Ok, I have fixed this up a little.

So I have tried on a new router, wireless N.

In Windows I can get 300mbs which is awesome. the thing is with the 5100 it defaults to G and in the windows settings you can change it to N also. This helped me get wireless N.

In Ubuntu I get G speeds, 54mbs.... There are no settings like in windows to change it to N. Anyone know how to do this, or am i stuck with G speeds when i use ubuntu?

---

### Post by waapwoop1 on 2009-05-21
does Ubuntu work with N networks?

---

### Post by waapwoop1 on 2009-05-24
I can get 300mbs per scond with windows 7 and xp. sometimes i get 48mbs in ubuntu..


I guess noone cares anyway.

---

### Post by waapwoop1 on 2009-06-24
anyone know about this yet?

---

### Post by japher on 2009-11-18
I'm using Jaunty, Intel WiFi Link 5100, Netgear DG834N router. I'm also only getting the G speeds, not N speeds :(

Has there been any new developments in the last 6 months? I'd love to have this card working at N speeds in Ubuntu! :)

---

