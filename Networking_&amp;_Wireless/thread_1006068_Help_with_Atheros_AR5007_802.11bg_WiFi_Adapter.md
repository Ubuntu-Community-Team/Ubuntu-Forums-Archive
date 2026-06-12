---
title: "Help with Atheros AR5007 802.11b/g WiFi Adapter"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by CrimsnDragn on 2008-12-08
Ok, so I've seen a couple threads that kinda addresses Atheros AR5007 802.11b/g WiFi Adapter and how ubuntu doesn't recognize it...? I kinda googled stuff on it and found a instruction that was labeled as for people with "no previous linux networking experience"...but I could not follow along it at all. maybe I'm doing something wrong, I read the help provided in ubuntu about how to kinda use their terminal thing, which is completely bizzare concept to me, having used windows all my life. the jargons used completely baffles me as well, took me like 20min to understand what opening a terminal shell in a folder meant, and 20more to figure out how to actually do it. I'm getting very frustrated, and I would greatly appreciate if any of you vets out there could give me a hand and explain how to do this in a simpler manner. I tried the way they showed, and I got errors in the middle for some reason...Thanks!!!

BTW this is the thing i was referring to that i was using: [http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)

---

### Post by PhoenixMaster00 on 2008-12-08
Im afraid its the only way as far as i no. Were exactly did you get stuck?

---

### Post by CrimsnDragn on 2008-12-08
well, first i opened a terminal in the MadWifi or whatever with cd /media/disk/MadWifi (btw I'm saving it in the right place right? in my C: or whatever?)

i tried their 2 lines of ifconfigure and it said there was nothing found, because all i have is eth0 or something...

then i tried the next set of code, and it goes warning: there's old stuff found you should delete it blah blah blah...so i was like r, for remove, the thing comes up again, and i typed r againn, and then...idk..i think it removed it...displayed whole bunch of stuff. 

the next 'make', when i typed it in, it kinda looked like it was installing something, for like a mintue, there were stuff scrolling through and that was kinda cool, but the last 5lines were errors...

i can barely understand their tutorial, so i'm really confused right now. any help would be appreciated :D

---

### Post by PhoenixMaster00 on 2008-12-09
> **CrimsnDragn said:**
> well, first i opened a terminal in the MadWifi or whatever with cd /media/disk/MadWifi (btw I'm saving it in the right place right? in my C: or whatever?)

i tried their 2 lines of ifconfigure and it said there was nothing found, because all i have is eth0 or something...

then i tried the next set of code, and it goes warning: there's old stuff found you should delete it blah blah blah...so i was like r, for remove, the thing comes up again, and i typed r againn, and then...idk..i think it removed it...displayed whole bunch of stuff. 

the next 'make', when i typed it in, it kinda looked like it was installing something, for like a mintue, there were stuff scrolling through and that was kinda cool, but the last 5lines were errors...

i can barely understand their tutorial, so i'm really confused right now. any help would be appreciated :D

Try this that i found. it was for Ubuntu 8.04 but should work for Ubuntu 8.10.
[B]
Preparing your system
[/B]
Open the terminal and just copy and paste the instructions (not all at once though)

sudo apt-get install build-essential

wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

make

sudo make install

sudo modprobe ath_pci

sudo reboot

---

### Post by CrimsnDragn on 2008-12-09
I saw that instruction actually. unfortunately, they changed that file. if you open it now, all you see is a notepad telling you to go to the MadWifi website...is there anyway you can upload your copy of it, if you have it? also I don't get how in the command it directs to a website, even though i cna't get go any websites because i'm trying to setup my wireless connection.

---

### Post by CrimsnDragn on 2008-12-11
I realized i had the new version of ubuntu...intrepid something...I don't know if that makes a difference, i thought ar5007 was to be supported on this new one :( also i've heard people using this other program besides madwifi...? I'm really new at this, so any help would be awesome >.<

---

