---
title: "[SOLVED] RCN digital upgrade broke my firewire capture setup"
date: 2008-12-13
forum: Mythbuntu
---

### Post by lokimon on 2008-12-13
RCN in new york city upgraded their system to an all-digital one on december 10th.  they gave me a lot of warning, so i was expecting to potentially lose my mythtv setup for a little while (and depending on the types of changes, perhaps for good.)  i knew that my two happague x50 tuner cards were no longer going to work (they are analog only) and that the firewire connection could be screwed up by the change.

when i first checked on my setup on the 10th, i found that my morning news had failed to record (as expected) but i was able to see some channels on livetv, although the numbers were skewed.

i reported the issue on the schedules direct website, and soon received an email telling me to try an alternate lineup they had just added.

for some reason, i thought that it would be a good idea to delete the X50 pci cards from the list of tuners, as i didn't want the scheduler to try to use them to record any shows.  unfortunately the only way to delete capture cards is to delete them all. (why is that?)  i figured that it would be trivial to re-setup the firewire capture, after deleting them all.

that was a big mistake.

i wrote down all the settings (dct-6200, broadcast, 200mbps) but i did notice that there was a GUID listed, although i didn't write it down.)  when i re-setup the card, i was able to re-enter everything, no GUID showed up however, and i went ahead and added the new cable listing, added the channels in step 3 and 4, ran mythfilldatabase, and tried to watch live tv.

it wouldn't work.  didn't change screens even.  i rebooted everything (unpluged the cable box for 30 seconds, let it fully boot and then booted my mythbacked.)  no dice.

as far as troubleshooting, so far i have:

•power cycled everything numerous times
•tried both firewire ports on the box
•deleted all capture cards/lineups and started from scratch
•made sure to have the cable box set to a known good channel

i have read these threads/sites:

[https://help.ubuntu.com/community/MythTV_Firewire](https://help.ubuntu.com/community/MythTV_Firewire)
[https://help.ubuntu.com/community/MythTV_Firewire/scanfw](https://help.ubuntu.com/community/MythTV_Firewire/scanfw)
[http://ubuntuforums.org/showthread.php?p=6350515](http://ubuntuforums.org/showthread.php?p=6350515)
[http://ubuntuforums.org/showthread.php?t=1006814&highlight=firewire](http://ubuntuforums.org/showthread.php?t=1006814&highlight=firewire)

i have gathered what i feel may be the best clues as to what the issue is:

RCN probably upgraded the firmware on my cable box during the digital upgrade.  this has caused issues for others, but my issue seems different yet related.

i have checked the encryption status for the channels i am trying to use, and none of them are encrypted or copy protected.

when i log into mythweb, and check the backend status, i do not see ANY tuner cards listed.

in mythtv-setup, there is no GUID listed for the firewire card.

i get this message in the mythtv-backend.log: 

```
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
```

output from firewire_tester:

```
lokke@media:~$ sudo firewire_tester -b -P 0 -n 1
Action: Test broadcast 1 times, node 1, channel 62
Broadcast: Testing...Success, 26 packets
```


please let me know what other information i can gather, to help fix this, to me it seems that the tuner not showing up in mythweb is at the root of this, but i'm not sure.

---

### Post by volkswagner on 2008-12-14
> for some reason, i thought that it would be a good idea to delete the X50 pci cards from the list of tuners, as i didn't want the scheduler to try to use them to record any shows. unfortunately the only way to delete capture cards is to delete them all. (why is that?) i figured that it would be trivial to re-setup the firewire capture, after deleting them all.

You need a keyboard attached.  When a tuner is selected, pressing "d" on the keyboard deletes the selected tuner.  I only found this via the forum not in any documentation.

Can you get repeat success on broadcast.  Try 5 or ten times.

```
sudo ./firewire_tester -b -P 0 -n 1 -r 5
```

```
sudo ./firewire_tester -b -P 0 -n 1 -r 10
```

What is the output of 

```
plugreport
```

---

### Post by lokimon on 2008-12-14
> **volkswagner said:**
> You need a keyboard attached.  When a tuner is selected, pressing "d" on the keyboard deletes the selected tuner.  I only found this via the forum not in any documentation.

d'oh!  i should have tried that anyway!

> Can you get repeat success on broadcast.  Try 5 or ten times.

```
sudo ./firewire_tester -b -P 0 -n 1 -r 5
```

```
sudo ./firewire_tester -b -P 0 -n 1 -r 10
```

lokke@media:~$ sudo firewire_tester -b -P 0 -n 1 -r 10
Action: Test broadcast 10 times, node 1, channel 62
Broadcast: Testing...Success, 44 packets
Broadcast: Testing...Success, 43 packets
Broadcast: Testing...Success, 111 packets
Broadcast: Testing...Success, 98 packets
Broadcast: Testing...Success, 62 packets
Broadcast: Testing...Success, 86 packets
Broadcast: Testing...Success, 25 packets
Broadcast: Testing...Success, 64 packets
Broadcast: Testing...Success, 82 packets
Broadcast: Testing...Success, 45 packets
lokke@media:~$

> What is the output of 

```
plugreport
```

lokke@media:~$ plugreport
Host Adapter 0
==============

Node 0 GUID 0x000000000010002e
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

Node 1 GUID 0x00152ffffeda459a
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=0
	channel=62, data_rate=1, overhead_id=0, payload=376
iMPR n_plugs=0, data_rate=2

lokke@media:~$

---

### Post by volkswagner on 2008-12-14
I don't know why plugreport finds the GUID but mythbackend does not.  

Hopefully someone with more knowledge will chime in.

Maybe a database issue holding on to the old information, and not letting the new box id.

Perhaps you can try a database repair.

Sorry I am not much of a help.

---

### Post by lokimon on 2008-12-15
> **volkswagner said:**
> I don't know why plugreport finds the GUID but mythbackend does not.  

Hopefully someone with more knowledge will chime in.

Maybe a database issue holding on to the old information, and not letting the new box id.

Perhaps you can try a database repair.

Sorry I am not much of a help.

just to update (and bump the thread in case someone can solve this)

database repairs didn't fix the issue.

since i keep my recordings on another drive, i backed up the database and re-installed mythbuntu from scratch, but the firewire box still isn't showing up as a tuner.

this is really bizarre,  i really hope someone can help with this issue.

---

### Post by dmfrey on 2008-12-15
I also use RCN firewire capture, but in the Lehigh Valley (Allentown, PA) and recently had an issue with it.  Originally, i thought it was related to a power outage, but now, I am not so sure.

Do you have a /dev/raw1394 device created for you?  I recently had an issue where the device was not getting created for me on boot up.

My issue cleaned itself up, but one thing i did, besides recycling all of the boxes involved, was to unplug it from the power supply.  I am really not sure what fixed the issue, it just started working again.

---

### Post by lokimon on 2008-12-17
well, everything seems to be fixed now.

i can't explain how it was fixed.  i did install the latest updates, and rebooted many times and reset the cable box many times, as well as completely re-installing mythbuntu twice (at least i know how to backup/restore my database now.)

once i got the cable box recognized, (once the GUID showed up, so did the cable box, FYI) i still had some freezing playing back HD content, until i changed the CPU setting from "CPU++" to "Normal" not sure if upping the ram to 4GB from 2GB would help with that as well, but i plan to up the ram anyway.

as of this morning, i was still getting some wrong channels, but i'm cleaning up my listings and hoping that will solve that issue.  at least the firewire stuff is working well.

will post another message when the whole thing is working perfectly, because i hope someone else can benefit from my troubleshooting, even though after all this i have no idea which step solved the issue.

---

