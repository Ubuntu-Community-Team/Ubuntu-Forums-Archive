---
title: "How do I set up a Remote Desktop?"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by xouns on 2009-09-03
I have tried this many times, but have never gotten it to work, so I thought I'd ask the community.

At my parents home I have a computer running Jaunty. At the university I have windows XP Profesional computers at my disposal (user level, not admin, running FF and RDP). What I want is to try and connect with my computer at home while I am at the university.

I know my share of Ubuntu commands, and I'm quite adept using Windows, however, I have never been able to make a remote connection, also due to my lack of networking skills. Could somebody please step by step explain what I need to do with both computers iot connect remotly to my computer at home?

thanks in advance

---

### Post by stefangr1 on 2009-09-03
There are several things you have to configure.

Step (1)
First is your Ubuntu desktop.

On the main panel, go to System -> Preferences -> Remote Desktop

Here you enable "allow other users to view" and "allow other users to control" your desktop. Also enable "require the user to enter a password" (and choose the a password).

Step (2)
The safest way to use a remote desktop from the outside is trough a secure ssh connection.

Install openssh-server:
sudo apt-get install openssh-server

Step (3)
On your hardware internet router, you have to assign a static ip-address to your ubuntu pc and configure port forwarding. How this works depends on your router, have a look in the manual if you don't know how it works.

You have to forward port 22 to your ubuntu pc.

Step (4)
The programs you need to log in on your pc from an outside windows computer are putty and realvnc-viewer (the executable without installer).

You start putty, enter your ip-address, go to the ssh-tab -> tunnels, type:
Source port: 5900
Destination: 10.0.0.5:5900 (where 10.0.0.5 is the internal ip address you assigned to your ubuntu computer in your router)

Click "Add", "Open" and login to your machine with your normal ubuntu password.

Now you start vncviewer, and enter: localhost:5900
Here, you login with the password you specified in the Ubuntu remote desktop options.

---

### Post by Bucky Ball on 2009-09-03
Nice, but the only way I could get things working was to switch off DHCP server and static IP address in the router and set the static IP for the Ubuntu local machine with System->Admin->Network. This would depend entirely on your router. I have a couple of D-Links.

Also, I think you can use DNS rather than IPs but I prefer the static IP security.

---

### Post by xouns on 2009-09-03
Wow, thanks so much, I'll get started with this as soon as I'll get home (can't wait).

---

### Post by xouns on 2009-09-04
One more question, how big a deal would network-managers make if they see I'm using these programs? Anyone any idea?

---

### Post by superprash2003 on 2009-09-04
it doesnt consume much.. you should be fine!!

---

