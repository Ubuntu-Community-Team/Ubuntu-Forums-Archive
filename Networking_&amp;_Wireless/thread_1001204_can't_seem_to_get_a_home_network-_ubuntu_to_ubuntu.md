---
title: "can't seem to get a home network- ubuntu to ubuntu"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by pikaia on 2008-12-03
I know there are a million threads about home networks, almost all deal with interacting with windows based systems, however I'm trying to get my Ubuntu Desktop and my Ubuntu laptop to see each other and am about to go crazy.  I want my laptop to be able to use the network printer (connected to desktop) and would like to set up a few shared folders.  But nothing is working...  I have Samba and CUPS installed on both, and am very frustrated.  

Anyway, I have both machines on, and try to Add New printer on the Laptop.  Nothing shows up under any of the network options (CUPS, IPP, Samba, etc).  If I go to the Samba setup I can see myself (laptop 1) and my other (windows laptop) but when I try to log in to my current machine (laptop 1) I get a password prompt.  I enter my password and then it just keeps looping, asking for password, asking for password...etc.  If I go into the Desktop (Hardy) and look under the Network in the Nautilus menu, I can see the Laptop 1, but again, can't log in.  On the Desktop, when I try to make folders 'Shared' it tells me that the Windows Network Sharing Service is not installed.  I click Install and nothing happens.  If I then click "Create Share" I get: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

So my question is how exactly can I set up this network so that all my machines can view each other and share (minimally) the printer.  My windows laptop is fine.  It was able to see the printer no problem, but my Ubuntu machines are being troublesome.  

I've seen the links and have scrolled through a ton of them.  At this point I fear I need the 'Mentally Challenged' HOW TO.  I've been using linux for over a year (several dozen distros) and this is up there for most frustrating.  Mostly because I feel like the biggest newb because I'm really lost, and PCLinuxOS had it configured with about 3 mouse clicks.

Thanks for any help.

---

### Post by IQRules on 2008-12-03
Can you do Firefox browsing, connect to network (wireless)?
If so try, [http://localhost:631/](http://localhost:631/)

---

### Post by pikaia on 2008-12-03
Thanks for the comment.  I can connect to my Wireless Router just fine.  And I actually just now found a check box on my Desktop that made my Laptop see the Printer.  But I still can't get the file sharing to work.  I've made files available on my Laptop but they aren't showing up on my Desktop, and I can't make anything 'Shared' on the Desktop because of the Windows Network Sharing issue listed in my previous post; ie I click 'Sharing Options' after Right Clicking a folder and I get a pop up saying "Sharing Service is Not Installed, I click Install Service and then nothing (apparently) happens.  I then click Create Share in the File Manager (Folder Sharing Pop Up) and then get the error at the bottom of the pop up saying "'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing."

I'd love to be able to share folders across my network, so if anyone can help, I'd be greatly appreciated.

Thanks.

---

### Post by pikaia on 2008-12-04
Ok.  It definitely seems to be mostly on the Desktop side of things.  First of all Hardy (running on Desktop) seems much more difficult to do this than Feisty (laptop).  As I mentioned before, whenever I click to share the file, I get prompted to install sharing service; I put in my password and it seems that it tries to open synaptic, but then crashes.  Or closes or something.  And again, nothing.  Just the error message I listed above.

Can anyone help?

---

### Post by superprash2003 on 2008-12-04
ok i think you have a problem with your samba setup.. the most common reason why you keep getting the password box up again and again is because you havent created a samba user.. Try setting up samba again , unless your samba is running perfectly it would be difficult to setup network printer using samba.. this guide should help , note the part where you create a samba user [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by dE_logics on 2009-04-18
Did that guide help anyone?

I'm trying to share ubuntu and windows.

---

### Post by ulfj on 2009-04-18
Yes it did thank you superprash2003 I asked this earlier but didn't make myself clear to what I was wanted to do I guess.I'm going to try this shortly.

---

