---
title: "Connection to Windows Network Printer"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by Clarke49 on 2010-03-15
Hello Everyone,
For starters, i am COMPLETELY new to Ubuntu. I am a windows user..*shutter*
 
To give you a quick idea of my experience, i'm good with databases and am working on my programming (usually VBA) i would say i'm an advanced begginer if there is such a thing. As for networks, i can set up a home network and access a router, i can do some of the most basic things but that's probably it.
 
My problem:
I have just recently installed Ubuntu 9.04 onto a windows machine. The machine has a dual harddirve setup. So one harddrive is dedicated to Ubuntu, the other to windows.
 
Everything installed peachy, and the computer can actually access the internet and update.
 
My problem right now, is printing. Or accessing the network at all. I have a Windows Vista laptop and a Windows XP Pro on a home network going through a D-Link wireless router The Ubuntu Machine is wired.
When i go to my network, i can see the MS home network and even go as far as to see the machines on the network. When i try to access them, i get an error saying that it can't mount the device.
 
Also, when i try to add a printer (which is my goal here) I go to the printer set up and follow the basic directions, but when I select "browse" to find the printer on the network, the printer manager window just closes. The printer is connected to the wired XP Pro machine. Can anyone give me some insight or assistance.
Did i provide enough info?

---

### Post by dannyboy0416 on 2010-03-22
I'm having almost the exact same problem the only difference that I'm using Karmic.  I hope it doesn't take to much longer than a week to resolve this.

---

### Post by suseendran.rengabashyam on 2010-03-22
Hi,

Try the following steps in your Ubuntu Machine

1) Go to System->Administration->Printing

2) Click On New->Network Printer->Windows Printer via SAMBA

3) Mention the IP Address of your Windows Machine with the printer share name in the ```
smb://
``` box, for example 192.168.1.1 is my Windows machine IP address and HPLaser is my printer share name then I would enter ```
192.168.1.1/HPLaser
```

4) You can also click on 'Verify' to check whether the printer is reachable.

5) Click on 'Forward' to proceed further.

Hope this helps.

---

### Post by Clarke49 on 2010-03-22
I actually tried this on the weekend. I had to set my XP machine to be a static IP first. (so that i didn't loose the connection the next time the machine was turned on)
But it did work. (I was actually just coming on here to respond to my own post to let everyone know i found solution.)
 
Your assistance is much appreciated though! Thank you for your time.

---

### Post by dannyboy0416 on 2010-03-23
Thank you so much for your help but I have a new problem now and am completely new to Ubuntu and linux in general.  Basically I'm trying to connect to a Brother HL-2040 printer connected to a windows xp machine now following your steps I was able to get the share but now all it does is process.  I was able to verify it and what not but its still not printing.  In addition the only printer available was a HL-2060.  Any further advice would be greatly appreciated because this is pretty much the last thing that I want to conquer before seriously considering going 100% linux/Ubuntu.  Thanks in advance.

---

### Post by dannyboy0416 on 2010-03-23
Nevermind got it working, thanks again for the help.

---

