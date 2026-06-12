---
title: "Help needed on wired connection to WRH54G w/ Lucid Lynx"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by trebuntu101 on 2010-06-25
hi guys,

i have already checked previous posts regarding a similar concern and had actually tried the suggested troubleshooting steps there; most had been about MTU settings which seem to have worked.

my case however still fail to get resolved w/ these outlined steps (i.e. fiddlin' w/ the MTU settings and pinging my router from time to time)

i am currently running ubuntu 10.04 on my PC w/ a Duron processor, ECS motherboard w/ built-in LAN, 512MB of RAM, and 50GB OS partition.  the installation went relatively well considering that i'm a linux noob.

i have made a similar install on an officemate's netbook (dell) and she's had not problems connecting to the internet both through the office WLAN and her mobile DSL dongle.:KS

i am right now using my netbook that's running win7 (argh!) connecting wirelessly to the same router without issues.

my PC has really got me frustrated :confused: and i could really use some help.  thanks!

trebs

---

### Post by Iowan on 2010-06-25
Is the problem with connecting to the router, or with  getting web pages to load? Does the machine get an IP address (**ifconfig -a** from a terminal)? Can you ping the router? Can you ping internet by IP address (74.125.95.105)?

---

### Post by trebuntu101 on 2010-06-25
whoa!  i dunno what happened but i just left my netbook and PC connected to the router lastnight.  wasn't gettin' anywhere tryin' to troubleshoot the lucid PC but as i got up a few minutes ago and tried pinging the router again, i was finally able to connect!:popcorn:

what i'm worried though is if this is gonna be a permanent thing of if i'd have to go through the same experience again soon as i do a reboot.

last night i had no problems pinging the router and i was getting the same IP address that's assigned to me right now by my router.  i was unable to ping the internet until this morning after trying the address you suggested.  maybe it's what got me connected.

the first time i tried connected after doing my install, i was only able to bring up google and do searches with google, but no other pages would load up.  they'd only go up to around 50% on the status bar then just stay blank.  soon as i started troubleshootin' w/ MTU though, i totally lost internet connection.

went to 1472, 1464, 1300, 1492, back to 1500 automatic, then back to 1472 right before hittin' the sack.

in any case, thank you very much, sir!:p

for now, i'm updating the PC and will be monitoring my connection.  will keep you guys posted should anything unnatural turn up.:p

again, thank you very much, sir!  i'm looking forward to an awesome ubuntu experience...mabuhay from the Philippines!

trebs

---

### Post by Iowan on 2010-06-25
Probably a good idea to give it a couple of days before you mark the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")...  ;)

---

### Post by trebuntu101 on 2010-06-26
aye, chief!  will certainly do that.  thanks again for the assist!:KS

---

