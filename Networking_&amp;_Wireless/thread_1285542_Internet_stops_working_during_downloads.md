---
title: "Internet stops working during downloads"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by GAdamp on 2009-10-07
I'm a noob to Ubuntu, got it yesterday, and I've been having way to many problems. My main problem is that whenever I start a download, after a little bit (30s-2m), my wireless internet suddenly stops working, and I need to stop the download to get it working again. This has made updating very annoying, and downloading large files almost impossible. Can anyone help me solve this problem.

Specs:
Qosmio X305-Q701 Laptop
Linksys WRT150N Wireless Router
64-Bit Ubuntu 9.04
I believe my Wireless Networking Card is from Atheros

Please remember I am a linux noob. Also, I do not have this problem in Windows, or when just casually browsing.

Thanks in Advance

---

### Post by GAdamp on 2009-10-08
Bump. Please help, or I'll have to uninstall Ubuntu and go back to Windows.

---

### Post by GAdamp on 2009-10-09
Bump. I need help, I cannot use Ubuntu because of this.

---

### Post by mclavey on 2009-10-09
sudo apt-get install linux-backports-modules-jaunty

---

### Post by GAdamp on 2009-10-09
Installed it, did nothing to help the problem.

---

### Post by OrangeVixen on 2009-10-09
I don't use wireless myself, but it sounds like a timeout problem. If you are downloading and browsing or doing human internet stuff, does the same disconnection occures? Does the entire internet connection get disconnected or just the download connection/socket?

---

### Post by Marvin123 on 2009-10-09
I have the same problem and it appears that whether an application is accessing the network or a 'person' is all network activity stops then starts up again after a random amount of time without any human input in my case. The download just begin again or the browser comes to life again. Very frustrating for a newbie to ubuntu...

---

### Post by GAdamp on 2009-10-10
What happens is that when I am in a download, after some time, I no longer have internet accesss. It appears that I am still connected, but I only get access back after cancelling the download. I don't get the problem when just browsing the web or using forums like now.

---

### Post by ztomic on 2009-10-10
I've noticed this problem for the past few distributions of Ubuntu. I've seen bug reports. I've duplicated this behavior on different computers with different applications and different distributions and at different locations; That covers hardware, software and internet and makes it really difficult to file a bug report. But I suspect it has something to do with the Kernel. A good example of what happens is this: When updating the system, The download progress bar stops in the middle of a file for several minutes. Restarting the update will continue where it left off. Another example is in Firefox: Downloads stall but can be restarted in the Downloads dialog box by pressing pause and then resume.

I also know that this is happening to a lot of people and nobody seems to know what the problem is.

---

### Post by ubuwatson on 2009-10-10
Yep, having the same problem.  I was using 9.04 for months and then after some system updates my wireless started acting funny (in fact I have been having some system slow downs as well).

I could be on the net and though I was still connected, internet would stop working.  I would have to disconnect from my wireless network and then reconnect again to get it to work.

I am using the Intel 4965AGN Wireless card in my HP Laptop.

I reinstalled Ubuntu from scratch again, but after the system updates I begin experiencing problems.  I am using Windows 7 right now, but would rather use and support Ubuntu.  This is disappointing to me because 9.04 works brilliantly until the system updates are installed which indicates that their is a bug in the updates.

---

### Post by GAdamp on 2009-10-10
That's a shame that the problem isn't currently solvable. This is the only thing besides games that is stopping me from using ubuntu.

---

### Post by ztomic on 2009-10-11
> **GAdamp said:**
> That's a shame that the problem isn't currently solvable. This is the only thing besides games that is stopping me from using ubuntu.
Well, I'm doing some experimenting. I found some info about MTU. What I did on my system is set up my router to use an MTU of 1462 instead of the default 1492. Then i set my network card on my Ubuntu box to do the same. I'm on a fresh install of Ubuntu 8.10 and I'm doing updates right now. So far everything is going great. It would be nice if other users with a similar problem could tell me whether this works for them.

---

### Post by GAdamp on 2009-10-12
> **ztomic said:**
> Well, I'm doing some experimenting. I found some info about MTU. What I did on my system is set up my router to use an MTU of 1462 instead of the default 1492. Then i set my network card on my Ubuntu box to do the same. I'm on a fresh install of Ubuntu 8.10 and I'm doing updates right now. So far everything is going great. It would be nice if other users with a similar problem could tell me whether this works for them.

Please remember I am a Linux noob, and I'm also dual-booting with Vista, if that matters. Can you explain a little better?

---

