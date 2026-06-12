---
title: "cannot connect to libary wifi bu can connect to any other"
date: 2013-04-12
forum: Networking &amp; Wireless
---

### Post by MasterJimmy on 2013-04-12
ok, this is a little complicated but not badly. i use ubuntu 12.04 64 bit LTS on my main rig ( a nice Gateway laptop) which i have no issues with otherthan the screen is broken so i have to tote my flatscreen monitor with me to the library which even though its only 19 inches and packs up easy its just a botherto do so. i have a dell latitude D610 that i had a 32 bit 12.04 LTS install on that would connect to my phone wifi and the bookstore and mcdonalds etc with no problem but wont connect to the library wifi which was the point because having a fully functional screen i could just pack up and go there for my big DL's and then transfer the files etc to my main rig. i have tried knoppix 7.0.4, mint 14 "nadia", windows XP Black, and currently i have fedora 17 installed on my dell rig. the issue with the various distros (and the "special" XP remix) is that they wont even connect to my phone wifi. they all detect the wifi but wont connect to it. i have a coupleof live dvds with multiple distro's i know are safe and stable having gotten them from linux user magazine. im also going to try fuduntu 12.4 , netrunner 12.12 , ghostBSD 2.5 , and mintKDE 14 to see if i have better results. so, to sumarize the issues im asking about are that my distro's will detect but not connect to my phone wifi, except for my 32 bit ubuntu 12.04 on the dell which will connect to every wifi network EXCEPT for the library.

---

### Post by Cheesehead on 2013-04-14
You seem to be making this more complicated than it needs to be.
You could simply replace the broken screen. Replacement screens for many models are fairly cheap and simple to install yourself.
You could also try connecting using the command line to see if you get a successful result, or perhaps an error message.
You could also tell us at what point in the attempted connection the process fails, or even merely what symptoms seem to be. AP too weak? AP association? DHCP request? Connection-then-immediate-disconnect?
You could also tell us how your phone wi-fi is configured. Open? WEP? MAC filtered?

Having already tried four distros/OSs with (apparently) the same results, what factors lead you to rule out hardware or signal strength? Based on your description, that's where I would look first before wandering through a forest of LiveDVDs.

---

### Post by MasterJimmy on 2013-04-14
i got fuduntu installed on my secondary rig and its connecting fine. eventually i am going to get the screen fixed on my main rig. i posted this thread because i dont know how to use the terminal for command execution and was hoping someone could tell me how or where to find out. i have a third box, a sony vaio which just needs a new power connector and im getting that fixed in the next few weeks. the dell rig is going to be the one i experiment on mostly once i get a newer HDD for it to stand up against the constant system installations and analysis i will be putting it through. ok the symptoms i was experiencing were consistent no matter what OS i tried up to now on this rig : i would see the network in the available network list and when i tried to connect to it it would keep asking me for the password even after i made sure it was entered correctly. when it did connect it would stay conected for a few minutes then disconnect and would not reconnect without rerstarting the computer and even then it might not connect. signal strength was at full especially since i had the phone next to the computer and the gauge even read full strength so i know its not a signal issue. the reason why i am so concerned with getting various distros to work is because i am working on various home automation projects, assistive technology, and a few just plain fun things  to bring to market and im trying to find one that will give the best overall user experience. its hard to actually put into words what i am judging by but its just one of those things i will know when i see it. so far Ubuntu is the only distro i seem to have no real issues with other than my dell rig will connect to every wifi network on earth EXCEPT for the local library wifi which is the one i WANT it to connect to. on my main rig i have absolutely no problems running ubuntu but there are aspects other distros i like, such as Kubuntu's overall interface minus a few specific details and one detail of this distro and that aspect of another etc. so far fuduntu comes the closest to what i want out of the box though. when i have the occasional connection issue (mostly disconnecting) it seems to be solved by turning my phones wifi off then back on though. once i have the time and the extra rig to really play around with like i want to i will post a list of what i want from each system and see what i can do about getting it put together.

---

### Post by MasterJimmy on 2013-04-14
one other thing i seem to experience is a smaller set of weird issues which shouldnt happen at all and that i can not for the life of me explain and which i cannot duplicate under any circumstances. the latest is that i would put the live dvd into my main rig but it wouldnt launch the live environment and it would go straight into my native OS. this went on for about a half hour then started working fine. i tried to launch the live os on my dell rig and it would hang up part way through and just stop. then it just as mysteriously loads properly after the third attempt. not trying to multi topic the thread but thought it worth mentioning

---

### Post by Cheesehead on 2013-04-14
> **MasterJimmy said:**
> i dont know how to use the terminal for command execution and was hoping someone could tell me how or where to find out.

See [http://askubuntu.com/questions/142336/how-do-i-connect-to-available-networks-from-the-command-line](http://askubuntu.com/questions/142336/how-do-i-connect-to-available-networks-from-the-command-line) for a good discussion and lots of good links.


> **MasterJimmy said:**
> i would see the network in the available network list and when i tried to connect to it it would keep asking me for the password even after i made sure it was entered correctly. when it did connect it would stay conected for a few minutes then disconnect and would not reconnect without rerstarting the computer

See ubuntuforums.org/showthread.php?t=1888681 (Page 2) for several possibilities, how to tell if your situation is similar, and how they fixed it.
Also [http://ubuntuforums.org/showthread.php?t=1458905](http://ubuntuforums.org/showthread.php?t=1458905)
We can help you more if you post the relevant entries from /var/log/syslog showing a connection and then a disconnection. Log entries havbe time codes - simply note the times at which you connect and disconnect, and paste that section here.


> **MasterJimmy said:**
>  it seems to be solved by turning my phones wifi off then back on though.

That suggests a problem with your phone's software instead of (or in addition to) your laptop....

---

### Post by MasterJimmy on 2013-04-20
i ended up installing the 32 bit 12.10 ubuntu onto the dell rig and have no problems connecting to any wifi network so far, although i havent had a chance to take it to the library yet to test it out on that network. so far it looks like the only distro that works for me out of the box without a bunch of system tweaks and mods is ubuntu so i will probably be sticking with it for everything. with all of the symptomology and etc i have seen so far it looks like its an OS issue rather than a network issue, specifically being the combination of hardware (my dell d610) and the various OS's

---

### Post by MasterJimmy on 2013-04-24
ok so the latest news is that every time i tried to launch an app through the dashboard i would have this total freeze and the only way to get it unstuck was to restart. so i finally dug out my old 10.04 LTS ubuntu and got my secondary rig up and running with that and am in the process of upgrading to 12.04.2 . Before you ask about the massive number of installations etc i always end up going through this repeated installation tango several times and then suddenly have a fully functional installation. happens on every rig ive run so far and usually the third or fourth install is the one.

---

### Post by MasterJimmy on 2013-04-30
im running a 32 bit 12.04.2LTS ubuntu on a dell D610. i can get it o connect toprety much any wifi netorki can find EXCEPT for the library wifi. my main rig is a 64 bit 12.04LTS on a NEW95 gateway laptop hich connects tothe library wifi perfectlywell but the screen is busted and its  not convienient to bring my 19 inch flatscreen monitor with me. im getting the sceen fixed on my main rig so i can use it atthe library again but im setting up[ the dellrig for myfiancee's mother and i need it to connect for her. HELP PLEASE!!!!!

---

### Post by Iowan on 2013-04-30
Threads merged.

---

