---
title: "Specific Hauwei E220 3G Modem problems"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by ZALinuxDude on 2009-11-10
Hi All I have searched back wards and forwards for a little help with my specific problem, so if this has been answered please direct me to where the answer can be found, please bare in mind that my command prompt skills are still pretty limited despite my previous experience with ubuntu...(spent most of my time on windoze at work) any way my problem is (known issue with server 9.10) that i cannot use my 3G modem to connect to the web but last night after finishing my very first install of Karmic Koala i connected my modem and nothing happened, as i am now working purely with command line i'm not sure what to be looking for nor am i sure of the exact steps to install this modem and there after how to use it, can some one please explain to me (baring in mind my skill level being limited) what i should do to firstly get the OS to recognise/install/mount the modem and then to explain what the commands are to actually dial out and connect to the internet so that i can download valuable updates and extra's that i need

Your patience and guidance would be appreciated
Many thanks

---

### Post by pdc on 2009-11-11
we have an E220 modem; it just configured up straightaway on 9.10;

does this page help you

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

go to the section 

> Create a Mobile Broadband connection

follow each step carefully; do what each step says

you should be able to configure a connection; and then connect;

---

### Post by ZALinuxDude on 2009-11-11
yeah busy with this fix its just a bit difficult when you are only able to use command line (can't download a gui because no internet)

But any way yeah thanks alot for you suggestion i hope i can come right, its just getting frustrating that i can't even update my ubuntu now for almost a week and its still unchanged since installing it from ISO

---

### Post by pdc on 2009-11-11
don't you just hate it when it's all hard to do;

what happens if you:

turn the Ubuntu computer on;
plug in your 220 modem;
when loaded, right-click on network manager; (top line);
select "edit connections"
select mobile broadband; select "Add":
select country: select your network: accept; close box;
now left-click on network manager; click on what you have just set up: what happens?

---

### Post by ZALinuxDude on 2009-11-12
Sorry dude but you giving me directions using a front end, I don't have a front end because i can't download one i'm having to do everything via command, but don't worry i sorted it out, i used the very same "fix"

---

### Post by veryoldcrow on 2009-11-14
I am impressed that you found a command line solution!

if you get time, could you share the basic steps?

Cheers
stumped veryoldcrow

---

### Post by ZALinuxDude on 2009-11-16
I ended up re-installing the OS with my offices network connection and downloaded the frontend and carried on with the same fix, it was the only thing i could do to come right (was stuck in a catch 22 situation)

---

