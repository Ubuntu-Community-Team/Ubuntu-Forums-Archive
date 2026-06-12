---
title: "SAMBA and Windows 7 Shares"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by stevedude on 2009-12-01
Hi all,

Thanks for taking the time to read and respond. My issues are related to SAMBA. I have run Samba with Hardy and Jaunty with Win XP on separate systems -- No problems. I ran Jaunty with Vista on separate systems with no issues either. I decided to do a fresh install of Karmic on my machine and Windows 7 on the kids machine. For the life of me, I cannot get this to work at all. I just receive a "Unable to Mount Location" error.

Shareable folders have been setup in Windows 7 Home Edition and a homegroup.
Samba workgroup name was changed from the default to the name of my workgroup under Globals section of smb.conf and the workgroup name within Windows 7 matches so that all match.

That is all I ever had to do in my previous experiences for shares between systems to work.

The kids Windows 7 PC has our printer installed on their computer. Another thing I noticed is that when I try to set-up a network printer on my Karmic system, I do not see a choice for Windows/Samba under the network printer choices.

In summary: Cannot share files/folder in Karmic and Windows 7, Cannot install a network printer, and lastly, when I try to make a folder shareable in Nautilus, the icon shows I made a shareable folder, but after a restart, the folders have to be re-shared, the icon disappears.

Help is appreciated.

---

### Post by Dougie187 on 2009-12-01
I can't help you too much, because I don't have anything with windows 7 on it. But, have you read this?

[http://www.tomshardware.com/forum/75-63-windows-samba-issue](http://www.tomshardware.com/forum/75-63-windows-samba-issue)

In the comments a few users say they have it working.

---

### Post by stevedude on 2009-12-01
Thanks Dougie187,

I've scoured the Internet for hours and I did read that post. If you have Windows 7 Home Edition and not Pro or Ultimate (like me), there is no "Lan Manager" entries to change within the Windows 7 registry for the Home Edition.

Thanks for sharing, but that does not appear to be the answer for my situation. 

Interesting to note that a responder within the link you sent stated Windows 7 intentionally breaks Samba --  Wonder if that is true?

Back to square one if anyone can help - - -thanks!

---

### Post by stevedude on 2009-12-03
OK, I was able to apparently confirm that Microsoft Windows 7 does not have the accessibility for SAMBA to work with the Windows 7 HOME PREMIUM Edition.

I found a good article at [http://www.linuxplanet.com/linuxplanet/tutorials/6911/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6911/1/)

I am running Ubuntu Karmic on my desktop and I have another desktop and laptop I want to get SAMBA to work with.  The one desktop has Windows 7 Home Premium Edition, the laptop employs Windows 7 Ultimate Edition.

I can connect to the Windows 7 Ultimate Edition on the laptop from my Ubuntu Desktop with no problems, confirming the apparent Home Premium Edition issue. I cannot connect to the Home Premium Edition at all. Still receive the "Unable to Mount Location" error.

So far any Windows Registry Hacks I've read do not work for the Home Premium Edition. So unless any of you know of a work-around, I'll have to wait for SAMBA to correct the issue on a future release because I doubt Microsoft will.

[As a side note, those of you with Win 7 Home Premium trying to work with SAMBA should make your voice heard to Microsoft. This is unacceptable, I am writing them right now!: [http://mymfe.microsoft.com/Windows%20%207/Feedback.aspx?formID=195&UrlReferrer=](http://mymfe.microsoft.com/Windows%20%207/Feedback.aspx?formID=195&UrlReferrer=) ]

---

