---
title: "Ubuntu 10.10 can't use network printer"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by beeser on 2011-04-30
Hello,

I'm running Ubuntu 10.10 on a Dell Inspiron 1545, and have an HP CP1215 laserprinter that I'm using as a network printer by connecting it to the USB port on a Belkin Play N600 router (model F7D8301).  The printer works fine from the Macs on the network with Belkin Router Management installed, but I'm unable to get the Ubuntu/Dell to see the printer.  When I plug the printer directly into the Dell with the USB cable, I can print, so I know the driver is correctly installed.  Is there a way Ubuntu can print through the router?  Does the Dell/Ubuntu need Belkin Router Management installed, and, if so, how?

Thanks!

---

### Post by beeser on 2011-05-29
So, no ideas on this one?

(aka "bump")

---

### Post by silvertuna on 2011-07-29
I have the same question.  Have you found an answer?

---

### Post by Daug on 2011-08-31
Same problem here..

When I go to System>Administration>Printing>Add, the "New Printer" dialog box pops up, appears to be searching, but never sees the network connected (Epson) printer.

Funny thing is, in the past, I've been able to connect to the printer and even print occasionally, but the Ubuntu laptop always loses its connection to the printer. Does this maybe have something to do with DHCP?

In any case, now Ubuntu will not even see the network printer.. please help!

Thanks

---

### Post by northd_tech on 2011-09-01
> **Daug said:**
> Same problem here..

When I go to System>Administration>Printing>Add, the "New Printer" dialog box pops up, appears to be searching, but never sees the network connected (Epson) printer.

Funny thing is, in the past, I've been able to connect to the printer and even print occasionally, but the Ubuntu laptop always loses its connection to the printer. Does this maybe have something to do with DHCP?

In any case, now Ubuntu will not even see the network printer.. please help!

Thanks

How is your Epson connected to the network?  Ethernet cable? Wireless? USB?  

Is it connected to a Windows machine?  (In this case you would need to enable Print Sharing under Windows and set up a Samba client on your Ubuntu machine to "see" any Windows Networking printers (or directories).  )

Also, it might matter what model of Epson you are working with (and it might be worth downloading the manual and/or Quick Setup Guide(s) from their website for that model if you don't already have a paper manual).

It is possible that you just need to install, enable, and/or restart the Ubuntu CUPS daemon, too:

[https://help.ubuntu.com/8.04/serverguide/C/cups.html](https://help.ubuntu.com/8.04/serverguide/C/cups.html)

---

### Post by Daug on 2011-09-07
thanks northd--

my epson is connected to my wireless router via ethernet, and has its own wifi. my ubuntu laptop is on wifi.

as i said, i have been able to connect in the past, and print, but i think what happens is maybe a router channel switches, or the printer gets assigned a new ip from the router, and ubuntu loses its connection to the printer. perhaps i should try to assign the printer a static ip, and turn off auto-channel while i'm at it (i haven't logged into my router in years; i'll have to remember how).

also, i'll try restarting CUPS. thanks =)

---

### Post by TBABill on 2011-09-07
beeser, when you go through the add printer process, are you selecting "find network printer"? I have an HP C309A that is wireless on my network. To find it I select find network printer and the system seems to hang for up to a minute, but it's actually searching. I can't click anything or change my selection, but eventually it pops up with my printer ID and prompts to add the driver. Have you already taken those steps? I have seen others who try to input all the info about their printer manually, but the automatic method works well often.

---

