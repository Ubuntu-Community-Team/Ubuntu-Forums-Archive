---
title: "Help! Need help setting up internet(wired)"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by BaasHans on 2009-04-10
Hello, I just joined solely to try and get my internet connected. Currently booted into WinXp. I used that basic help thing that came with linux on the top taskbar-like thing. After using sudo pppoeconf I am still where I was at start(Internetless). If only I can get the internet to connect I can look for the rest of the stuff I need on the net.
Back to the sudo pppoeconf. It did nothing after scanning the 2 devices. Can't remember the exact message, coz i have to reboot just to post this, and I don't know how to take a screenshot in linux yet. In the meanwhile I have scoured through a couple of the network pages and most are regarding wireless.
Please tell me what I am doing wrong, because I also tried using the Network Manager.
I entered my username and password in the dsl connection and it just times out - it seems - and then defaults back to "Wired Connection 1". I also noticed that when I am connected to the ethernet network with the default connection thing or with my own connection that I set up, I can't access my router.
Help will be appreciated severely.
Sorry if this has been posted somewhere before, but I was not feeling up to browsing through 1200+ pages of network related stuff.
If you need any sort of feedback like images or stuff from "terminal" just tell me how to get it to you.
BTW it's Ubuntu 8.10 amd6

---

### Post by jdackle on 2009-04-10
Hi BaasHans,

What are the two devices (modems/routers?) you mention? Please state brand and model (if you can get the info, firmware revision number too).
Some hardware needs some tweaking in order to run on Linux...

Hints:

To take screenshots: Applications -> Accesories -> Screen Capture (or some similar term, mine is in Portuguese... ;D )

To save the output of some command to a text-file:
```
$ command arguments-if-any **>textfile.txt**
``` (the ">" character redirects the output to the specified file)

Also, have a look at [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
It's more specific to wireless, yes, but has important tips on how to get infos on your networks (wired or wireless) too.

---

### Post by brayden13 on 2009-04-10
So do you have a router or something like that? My memory is bad as I haven't used XP in a very long time but if you can get the MAC address for that router or whatever then all you should need to do is just go to System -> Preferences -> Network Connections. Then go to Wired tab, then click "Add". After that name it something you will remember and copy the MAC address exactly as it appears.

---

### Post by BaasHans on 2009-04-10
Jdackle >
Ok This is the exact router i am using. [http://www.sizwebroadband.co.za/content/billion-800vgt-firewall-adsl2-router](http://www.sizwebroadband.co.za/content/billion-800vgt-firewall-adsl2-router)
I am also using the firmware that is available on the link on that page on the left hand.
Ok the 2 devices it scanned i think was Pan0 and aut0.
I take it aut0 refers to my network card. I took pan0 to refer to my router, but I guess it's something else.
brayden13 >
I am currently at work, and have no way of accessing the router where I am now.
All>
Ok one thing that might help you understand what I am trying to achieve is:
I'm currently at work. I made an internet connection that connects through the router although my work is already using their own username and password on their router.
I want to create a similar connection on linux to ensure i can just change it minor-ly so i can use it at home.
And BTW Thanks for responding so swiftly :)

---

### Post by jdackle on 2009-04-10
Nope, don't know that router, sorry.
However, now that you've posted what it is, someone else familiar with that machine may be able to help you. ;)

Posting the infos asked by the thread I already mentioned, questions 1, 3 (iwconfig NOT necessary), 4, 5, 6, 8, 9 and 10, should help others more knowledgeable to help you.
Question 6 (*$ sudo lshw -C network* should give you the list of networks you have installed.

---

