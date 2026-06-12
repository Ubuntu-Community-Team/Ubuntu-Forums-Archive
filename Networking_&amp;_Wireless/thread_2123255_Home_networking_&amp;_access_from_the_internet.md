---
title: "Home networking &amp; access from the internet"
date: 2013-03-07
forum: Networking &amp; Wireless
---

### Post by nick7076 on 2013-03-07
Not sure if an Ubuntu specific forum is the right place to ask but I'm going to ask anyway!

How do I get 5 machines connected so I can access any file from any other machine and have control of any machine from the internet?


Machine 1 is XP and has VNC server installed along with dyndns client for static ip addressing. I can access this machine from the internet via VNC client. It runs one specific program that 3 or 4 people need access to, has firewall and virus protection. Nothing else will be installed on or connected to this machine.

Machine 2 is Puppy 5.3.1 It is an old Pentium 4 1.6 with 750MB Ram. It will have a printer and various USB external drives connected. Puppy is the only OS I have been able to get to run and install, having tried just about everything that came on a magazine disk for the last 2 years!

Machine 3 is XP It exists to run Microsoft Money. All I require is remote turn on if possible, and access.

Machine 4 is an Elonex Netbook with Puppy 5.3.1 Again anything else won't install due to screen resolution and driver issues. This I take to work when travelling and will use to access the home network and keep on top of jobs.

Machine 5 is my main laptop, core2 2.0Ghz 2Gb Ram running Ubuntu 12.04 and XP on a second partition. I use 12.04 for 99.9% of everything I do. All I need now is to be able to access everything at home when away.

The 2 XP and Puppy desktops are online via an Ethernet switch. A spare connection is used for the laptop instead of wifi. My router is the standard BT infinity broadband box with the necessary port forwarding for VNC.

---

### Post by ing.tani on 2013-03-08
Have you try TeamViewer?
For puppy ypu can find it here: [http://puppylinux.org/wikka/TeamViewer](http://puppylinux.org/wikka/TeamViewer)

---

### Post by TheFu on 2013-03-08
There are thousands of solutions.
I would setup 1 box with internet connectivity and a VPN, then use that to jump to any other machine from the outside world.

As to sharing files across all the machines, use CIFS/Samba on the LAN, but never, never, never use it over the internet.  For that, use scp/ssh/sftp.

I don't have much experience with puppy because I think the run-as-root-always method used is terribly broken.

I would strongly encourage you to centralize all the file storage - this makes all sorts of other things easier too. There are lots of cheap NAS solutions from $30+ available.

BTW, using VNC without a VPN is not secure. Be afraid - very afraid.

---

