---
title: "Nokia on bluetooth"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by LaptopU on 2009-03-15
I can connect to my Nokia 6630 with no problem, but when I click to browse the directory is empty.  I've done lots of research and it appears there's a known problem as many Nokia phones have two FTP servers and the default server Ubuntu connects to is the wrong one.

Part of the fix is upgrading the Obex backend to 0.4.3, but I've downloaded source code and tried to compile with absolutely no joy.  How on earth can I get the latest version of Obex backend onto Intrepid?  Any help is appreciated, TIA.

---

### Post by inobe on 2009-03-15
tried with my samsung m520 and razr prior to the samsung...... basically they are locked which makes it all the more difficult.

though i found that if ftp is enabled it allows me to choose from the sd or in phone !

in phone was useless to say the least' however via sd only certain folders i could view content' but was unable to drag and drop.....

file transfer seemed to work' but that wasn't what i wanted, for that i could just plug the sd card in and do the same.

some stuff i found, i don't know if it will lead to anything great.

[https://help.ubuntu.com/community/PortableDevices/Nokia](https://help.ubuntu.com/community/PortableDevices/Nokia)

old and new' bug report' scroll down

edit: looks promising [http://www.ubuntugeek.com/blueman-bluetooth-manager-for-ubuntu.html#more-960](http://www.ubuntugeek.com/blueman-bluetooth-manager-for-ubuntu.html#more-960)

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by LaptopU on 2009-03-18
Inobe - that is absolutely PERFECT, I am delighted after not being able to browse my Nokia 6630 *ever* before on Ubuntu, Blueman has just done it in about one minute.  I'm over the moon, thank you!

---

### Post by inobe on 2009-03-18
that's great LaptopU :)




enjoy

---

### Post by LaptopU on 2009-03-18
Update - Unfortunately it hasn't really worked though.

Small file transfers - under 10kb, no problem.

Larger files - even 100k - won't transfer.  Blueman isn't reporting a problem, but if I double-click an image for instance, I get the message -

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Any ideas please?

---

### Post by inobe on 2009-03-18
i found this' i will look threw it



[http://www.google.com/search?q=DBus+error+org.freedesktop.DBus.Error.NoReply%3A&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=DBus+error+org.freedesktop.DBus.Error.NoReply%3A&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by LaptopU on 2009-03-18
Thanks, I've been looking through it all myself for the past couple of hours too with no joy.  Oddly enough someone on the Blueman forums says they cannot download any files from the Nokia 6630 phone, so I think it may be a bug, but they haven't said much more than that.

Seems just a bit too unusual that I can download very tiny files but nothing large, if I couldn't connect at all that would be a different story.  In the meantime because of what I've read up on and the problem itself, I've logged it as a bug on Blueman.

I think I could really use Obex 0.4 though at some point.  (Edit - it's next month Jaunty comes out - that has Obex 0.4, may be the answer to my prayers?!!)

---

### Post by inobe on 2009-03-18
yes' i just added the ppg key and i will do some experimenting from my samsung m520, check back for the results.

---

### Post by inobe on 2009-03-18
alrighty' i have clicked send file, i am sending an mp4 video pretty large.

prior i tried to drag and drop' as always my service provider did something to block that..... so i won't even go there .

it seems that the transfer succeeded' i just need to found it

if i could drag to the folder i could test that' i cannot......

send file works

---

