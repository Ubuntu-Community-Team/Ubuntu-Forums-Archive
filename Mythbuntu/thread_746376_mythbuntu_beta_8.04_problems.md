---
title: "mythbuntu beta 8.04 problems"
date: 2008-04-05
forum: Mythbuntu
---

### Post by jimp180 on 2008-04-05
I just installed the beta using the alternate install cd, I used this because I have a software raid that I wanted set up when I got Mythbuntu installed as this is where my recordings dir is located. 
the first thing I notice is that it doesn't make the default login as mythtv with the frontend starting automatically so I have to login with my user name then start the frontend manually. How do I change to the auto login for the frontend? 
also I am having problems with it locking up, most prominent when I try to watch live tv from my Hdhr tuner. at first I thought this was due to the channel that it was defaulted to not really being there so it couldn't get a lock. Last night however I went in the back end and changed the default to a channel I know is good, I watched live TV for a couple minutes at this time but then the audio started to crack and pop and the video started to get digital splotches in it then it just locked up. when it does this I can't use any controls and even the network is messed up because I can't remote in to reboot, the machine can't be found. (ssh or vnc) so I have to hard boot the thing. 
Is the weather fubared in this release again? I get the funky looking ? in my weather plugin again, I know it was working on the 7.10 release. that weather setup sucks too, I can't understand why I have to enter  the city for each screen but there must be a reason they changed that I guess. 
any help would be appreciated, I may just try to install off the live cd and just add the software raid manually after I install and see if the live cd install is better.

---

### Post by jimp180 on 2008-04-05
ok I see bluetooth is no longer going to be supported at the command line in 8,o4 either without jumping through hoops. sometimes progress for mamby pamby windoze users is detrimental to the cause, I would think that while maybe kubuntu and whatever they call it with gnome might need the gui version of bluetooth, mythbuntu should have the hidd program because I don't see any reason to have a desktop for a mythtv box. maybe a section should be put in the MCC for the bluetooth gui thing. 

root@mythbuntu:~# hidd --search
-bash: hidd: command not found

---

### Post by laga on 2008-04-05
For bluetooth: Install bluez-utils?

---

### Post by jimp180 on 2008-04-05
> **laga said:**
> For bluetooth: Install bluez-utils?

yes I have installed bluez-utils but as for the version that installs with 8.04 it doesn't contain hidd, hence I get

root@mythbuntu:~# hidd --search
-bash: hidd: command not found

but now I have dumped 8.04 because I couldn't use it locking up like it was anyway, I thought I would get my bluetooth keyboard to work in 7.10. 7.10 does install hidd with bluez-utils but even with that when I try to do hidd --search it finds my keyboard and tries to connect but when I type my key into the keyboard no window pops up for me to type it into ubuntu. do I have to install another desktop besides xfce just to get this bluetooth passkey window?

---

### Post by superm1 on 2008-04-05
> **jimp180 said:**
> yes I have installed bluez-utils but as for the version that installs with 8.04 it doesn't contain hidd, hence I get

root@mythbuntu:~# hidd --search
-bash: hidd: command not found

but now I have dumped 8.04 because I couldn't use it locking up like it was anyway, I thought I would get my bluetooth keyboard to work in 7.10. 7.10 does install hidd with bluez-utils but even with that when I try to do hidd --search it finds my keyboard and tries to connect but when I type my key into the keyboard no window pops up for me to type it into ubuntu. do I have to install another desktop besides xfce just to get this bluetooth passkey window?
Bluetooth is done a lot different in 8.04.  You don't use hidd.

Open up the bluetooth applet, and pair in that.  It just "works" then upon system start.

```
bluetooth-properties
```

---

