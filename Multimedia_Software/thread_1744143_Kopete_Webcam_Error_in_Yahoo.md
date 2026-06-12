---
title: "Kopete Webcam Error in Yahoo"
date: 2011-04-30
forum: Multimedia Software
---

### Post by ibrahim52 on 2011-04-30
UBUNTU - A Beautiful Invention. Installed 11.04 and i am totally switched from WINDOWS to UBUNTU now but unfortunately the webcam issue in KOPETE which is not working for me, i am able to see the preview of my cam in CONFIGURE but whenever i try to send or recieve the webcam it says JASPER CONVERSION PROGRAM ERROR or something similar i tried install the jasper and everything related to it but it is still not working, any workaround ?

---

### Post by frefactory on 2011-04-30
I've got the same problem. I even added the path to JasPer in the environment-path but it just does not work. The problem can be replicated every single time I reinstall 11.04 and it happens on different machines as well.

I hope there will be a workaround or patch soon.

---

### Post by ibrahim52 on 2011-04-30
But still, were you able to solve the existing issue or it is still the same for you ?

---

### Post by TinyFoot on 2011-04-30
you just have tu run this in the terminal. works for me. i tested it just now.

*sudo apt-get install jasper libjasper-java libjasper-runtime libjasper-dev libjasper1*

please post the results.

---

### Post by ibrahim52 on 2011-04-30
Did that but unfortunately it didn't worked instead when i reboot the laptop it had reset all the settings and i had to put all the settings includes, hostname ,username , wifi password.

---

### Post by ibrahim52 on 2011-04-30
unable to find the jasper image conversion program error


Same error again and again and again, tried reinstalling it for three times. I am tired totally

---

### Post by frefactory on 2011-05-03
I haven't been able to solve the problem either. 

I installed all necessary packages. Except the "jasper" package that is used for Ext2/3 and has nothing to do with the jpeg-2000 libraries. That is why you needed to reconfigure the entire settings upon reboot. 

I manually changed /etc/environment to include jasper in the path. It still complains that jasper cannot be found. 

This remains a mystery. One possible workaround might be to install a previous kopete version and see what happens.

---

### Post by ibrahim52 on 2011-05-03
yeah but did it worked for you ?

---

### Post by frefactory on 2011-05-04
No, it still does not work. Somehow I hope we're not the only two with the problem.

---

### Post by ibrahim52 on 2011-05-04
Nop we aren't but i am wondering if it is there any alternative for KOPETE, tried GYACHI :p it is HORRIBLE it shows the previous deleted contacts from address book of yahoo which are useless

---

### Post by frefactory on 2011-05-10
I have found a solution. I took the kopete package from the 10.10 repository. installed it, and thus overwriting the newer version. It works flawlessly for me now.

Try this : 

Make sure you have kopete and libjasper-runtime installed already in 11.04

if not : **sudo apt-get install kopete libjasper-runtime**
then proceed to do this : 

surf to [http://packages.ubuntu.com/maverick/i386/kopete/download](http://packages.ubuntu.com/maverick/i386/kopete/download)

and download the **kopete_4.5.1-0ubuntu2.2_i386.deb** package from security.ubuntu.com/ubuntu (just click the link)

now go into terminal and go to the place where the .deb package is downloaded (probably home/yourprofile/Downloads)

then do : **sudo dpkg -i kopete_4.5.1-0ubuntu2.2_i386.deb**
this replaces the 11.04 faulty kopete with the version from 10.10

now get the dependencies 

**sudo apt-get install libkutils4 libkprintutils4**

Additionally, prevent kopete from being updated if this is bothering you. go to **synaptic package manager**. search for kopete. highlight the installed **kopete **package. go to the **package menu **and **LOCK VERSION**. If somewhere in the (near) future there will be a corrected version available in 11.04, just remove the version lock and update it. 



You're about ready to launch kopete and enjoy the yahoo webcam viewing.


cheers!

---

### Post by ibrahim52 on 2011-05-10
i don't know if you found the solution or was your own DISCOVERY but i must say that you just made a HISTORY here by solving this ISSUE , you are THE HERO . THANKS a load or for 1000 times even if i keep thanking you it would be less. THANKS A LOADDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD

---

### Post by ibrahim52 on 2011-05-10
and guess what you made me save my points in forums like EXPERTS EXCHANGE where this TOPIC is still exists and UNRESOLVED.

---

### Post by frefactory on 2011-05-10
> **ibrahim52 said:**
> i don't know if you found the solution or was your own DISCOVERY but i must say that you just made a HISTORY here by solving this ISSUE , you are THE HERO . THANKS a load or for 1000 times even if i keep thanking you it would be less. THANKS A LOADDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD

I had the idea a few days ago to roll back the main kopete package to the previous version and keep it versionlocked. Today I had a few spare minutes and gave it a try during lunchbreak. I love it when a plan works out. :-)
I hope that others will benefit from this solution as well. If not, we've got our own private thread in the forum. lol.

Anyway, happy webcamming!

---

### Post by iclestu on 2011-06-02
hey guys,

couldnt find a bug report for the issue with the latest version of kopete not finding jasper so filed one here:

[https://bugs.launchpad.net/ubuntu/+source/kopete/+bug/792126](https://bugs.launchpad.net/ubuntu/+source/kopete/+bug/792126)

click on the button to let em know it affects other people to try and get em working on a fix to make latest version work....

---

### Post by billz68 on 2011-07-15
Thanks for this information.  I was trying to get it to work last night for the first time (I've been using Skype, which works flawlessly in Ubunbu) and couldn't for the life of me get it to work.  i found a rollback link on another site and tried it, but nothing happened at all when I clicked the "Invite to view webcam" link.  It may have something to do with the fact that my messages weren't going out either (that has happened before.  It seems to be a sporadic bug in Kopete).  So I went back to the new version and was able to send and receive messages, but no Webcam.  I will try the more comprehensive solution here tonight and hopefully it will work.

---

