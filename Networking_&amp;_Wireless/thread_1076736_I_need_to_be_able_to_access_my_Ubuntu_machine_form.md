---
title: "I need to be able to access my Ubuntu machine form my XP machine."
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by joegra on 2009-02-21
I need to be able to access my Ubuntu machine form my XP machine. All help greatfully received.

I am running Ubuntu 8.10 and XP Professional 64 bit on the other machine.

---

### Post by oubaas on 2009-02-21
I did this 5 mins ago.;)
Setup the ubuntu folders you want to access as shared. 
(and/or windows folders too), on ubuntu do system->administration->sharing.
Connect machines with cross-over ethernet cable, or patch cables and a router/switch.
Set IP addresses on each machine, (eg 192.168.0.1 /255.255.255.0 for winbox and 192.168.0.2 /255.255.255.0 for uxbox, if you have direct cable).
test by pinging the other from either side (start->run-> ping 192.168.0.2 on windows) or (ubuntu system->admin->network tools has a ping tab)
Right click My Computer->map network drive->, select a drive letter you are not already using from the DRIVE pull-down, and then select browse from beside the FOLDER pulldown,and you should be able to navigate to the ubuntu folder under the 'Microsoft Windows Network'
Hope this helps

---

### Post by joegra on 2009-02-22
Thanks oobaas, I'll give it a go

---

### Post by superprash2003 on 2009-02-22
are you talking about remote control or file sharing?

---

### Post by Reiger on 2009-02-22
If you want remote control of the Ubuntu Box from the XP box, I'd recommend downloading & installing Putty on the XP box and OpenSSH (sudo apt-get install ssh) on the Ubuntu box. Then you should be able to log onto your Ubuntu box using accountname@ip-address with your passwd as passwd. (Alternatively you can set up more elaborate encryption with Putty too.)

If you want to combine that with remote file management (up/download grep and what not) I'd recommend installing WinSCP on the XP box as well; it can work together with Putty to give you a Filemanger fronten to SSH.

---

### Post by joegra on 2009-02-22
Superprash2003: File Sharing.

Reiger: Thanks I'll give that a shot.

The help that oobaas offered didn't work, for me.

---

### Post by superprash2003 on 2009-02-25
you would need to setup samba for this.. [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html)

---

