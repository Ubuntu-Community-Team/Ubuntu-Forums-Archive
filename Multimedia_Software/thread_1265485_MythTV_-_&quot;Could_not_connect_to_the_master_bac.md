---
title: "MythTV - &quot;Could not connect to the master backend server&quot;"
date: 2009-09-13
forum: Multimedia Software
---

### Post by badger_fruit on 2009-09-13
Hello all
A brand new Ubuntu user here; I am familiar with linux as I have used opensuse for a few years now.
My problem is with the running of MythTV front-end from a "remote" machine.

My setup is:-

BGRSVR-V - MythTV Backend hosted on Ubuntu 8.10, IP address is 10.0.0.5
BGRMEDIA01 - MythTV Frontend running on Suse 11.0; IP address is 10.0.0.100.

If I sit at BGRSVR-V, then I can run the front-end and watch Live TV.
If I sit at BGRMEDIA01, then I always get the message:-

"[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]**[B]could** **not** **connect** **to** the **master** **backend** **server**[/B][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]"

I configured the backend server to use the IP 10.0.0.5 (as opposed to 127.0.0.1 or DNS name BGRSVR-V). I have also gone into mysql and GRANT ALL ON *.* to 'mymythuser'@'10.0.0.100' IDENTIFIED BY ('password') ... to ensure the remote PC has access to the MySQL server & databases.  I have repeated the GRANT statement for all the BGRMEDIA computers (3).

Have I missed something? Why do I get this message on all my clients?
Please help, I am going out of my mind with this!!!

Thank you for reading, I hope with your help, to be able to solve this.
badger

---

### Post by badger_fruit on 2009-09-14
Just FYI this is now resolved; a GRANT ALL ON mythconverg.* to 'user'@'10.0.0%' ... has allowed all users on my LAN to access, MythTV is now working, hoorah!

---

