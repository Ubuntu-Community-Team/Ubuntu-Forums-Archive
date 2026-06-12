---
title: "Wireless adapter not working after wlan.conf update"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by dnlarsen on 2011-01-19
I am very new to Linux, so hopefully there is a simple answer to this question. I updated  Ubuntu to 10.04 after which I noticed the wireless indicator lights on my HP laptop were continually flashing between blue and orange and network performance seemed slow. I did some searching and found and implemented the following change to stop the flashing:


[LIST=1]
[*]gksudo gedit /etc/modprobe.d/wlan.conf
[*]Copy and paste the below line:
  options iwlcore led_mode=1
[/LIST]
Since making this change the wireless connection is shut off and I can;t get it to work at all. I first tried simply to remove the change to get back wher I was, but I can;t do that. Can sopmebopdy toell me at least how to get rid of this wlan,conf file ( it was created by the above command) so I can start over?

Coincidentally since making this change my Windows Vista OS fails to start because of errors attributed to a software or hardware change, of which there were none other than the Ubuntu wlan.conf change. . It may be unrelated but I am suspicious of the coincidence. I am running Vista and Ubuntu in a dual boot configuration and all ha run very well until I did the Ubuntu wlan.conf change.

I am now attempting a complete recovery of my Vista system, since it seems irreparably broken. Again coincidence or not?

Help!

---

### Post by grahammechanical on 2011-01-19
First of all, the file you created in Ubuntu did not and could not make changes to the software in Vista. Second, it is very unlikely if not impossible for the creation of that file to change the hardware on your machine.

Have you considered that there could be a fault with the switch on the keyboard that switches the wireless adapter on and off?

Perhaps it is making and breaking the connection repeatedly. This will prevent wireless from working in Ubuntu and may cause enough confusion for Vista to get into a panic.

This is just a thought.

Regards.

---

### Post by dnlarsen on 2011-01-19
I agree that a change to Ubuntu should not affect either hardware or software on a different OS. But I just did a full recovery on my Vista system, it is up and running and the wireless adapter is on solid blue and working fine. The adapter worked just fine with my previous versions of Ubuntu as well, 9.04 and 9.10.

BTW when I did the recovery it apparently blew the dual booter away because my laptop will only boot Vista now. I went ahead and repartitioned the drive and eliminate Ubuntu for now, but I am still very curious about what happened and how I could remove the wlan.conf file I created that seemed to start the wireless problems  with Ubuntu at least. I still have Ubuntu on a desktop computer so I hope somebody comes up with an answer for future reference.

Bottom line, when I reverted to a working version of Vista, problems went away. Very strange.

---

