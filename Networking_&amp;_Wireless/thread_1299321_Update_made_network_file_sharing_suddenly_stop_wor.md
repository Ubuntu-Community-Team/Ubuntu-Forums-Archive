---
title: "Update made network file sharing suddenly stop working"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by andrewkirk on 2009-10-23
Dear Ubuntu community

I have four computers on my home network, all dual boot WinXP and Ubuntu. While I have had various problems with XP accessing file shares, any computer running Ubuntu has always been able to see shares on all the others (whether they're booted into Ubuntu or XP), via the Places menu amongst other techniques.

Suddenly, last Tuesday 20 Oct, all the computers stopped being able to access network shares, one after another. Reviewing this odd plague, I realised that for each of them, the problem started on the first Ubuntu reboot after loading the Ubuntu updates released that day. Now none of them can access shares on other network computers, although a computer running Windows can see the shares on the Ubuntu computers. ie it appears the Samba servers are working OK but something in the updates has corrupted the Samba clients.

When I try to access shares on other computers, I first get the message "you can stop this operation by clicking cancel" and then, after a long pause: "unable to mount location - failed to retrieve share list from server". 

Unfortunately there appears to be no way to 'roll back' the updates that caused the problem, and I can't even find out what they were, as the packages don't seem to be in /var/cache/apt/archives.

As the computers are all different hardware, BIOS etc, it is hard to imagine that the problem is machine specific. Most of the Ubuntu installations are entirely generic, without customisation. I would imagine that this problem must have come up with many other people at the same time, after doing the update.

Ubuntu version is 9.04. The network is connected via a Netgear router with both wired and wireless connections. The Netgear also acts as an internet gateway and the computers have no problem seeing the internet, just seeing each others' files.

I have found that I can access network shares by typing the IP address of the server PC into Nautilus' address bar. It gives an error message 
	Could not display "smb://192.168.0.6/".
	Error: DBus error
	org.freedesktop.DBus.Error.InvalidArgs: Mountpoint
	Already registered
	Pleaseselect another viewer and try again
however it then goes ahead and shows the share list anyway, and allows me access.

However, this solution is not satisfactory and having to manage this messy workaround would surely be sufficient to drive all the users in my family, who have finally, gradually been won over to Ubuntu, straight back to Windows. 

If anybody can help getting the 'Places' function to work again I would be very grateful.

---

### Post by Cybie257 on 2009-10-23
First off, let me start by saying, that you should have updated one computer, tested, and then continued with the rest if successful. Sorry, just something I had to say as an IT person. :)

What you can try to do is to connect to the shares by using PLACES->Connect to Server->Service Type->Windows Share and enter the appropriate information. 

This has always worked for me when the other way hasn't, due to broken updates. Linux is changing on a daily basis and things will break when updating, just as they will begin to work again on a future update. Best practice is to NOT update unless it is found to be necessary. Come with the old saying, "Don't fix what isn't broken". 

Hope the suggestion to connect works out. 

-Cybie

---

