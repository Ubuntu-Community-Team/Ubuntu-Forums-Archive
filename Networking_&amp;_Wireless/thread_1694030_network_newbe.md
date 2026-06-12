---
title: "network newbe"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by yeldarbs1 on 2011-02-23
i just switched from open suse kde and like ubuntu 10.10 but im having trouble navigating around my network we have a mixed wired and wireless net work with a combo of 8 terms or computers and my problem is on my linux machine in networks i show windows share and next to that i show my machine, when i click on windows share which i presume is the same as samba shares, i show mshome and workgroupe. when i click on mshome  which is our combined network it shows all but my machine. question one, how dow i get my machine over from workgroupe to mshome. question two, in mshome when i click on one of our other computers i can access all the shared files and apps, but when i click on any other machine i get  -sorry cannot mount (computer) couldnot recieve shares from server. if we goto one question at a time would be real helpful. thanks a newbe in need of help.:(

---

### Post by headvampyre@hotmail.co.uk on 2011-02-23
Hi, basically you want to join the mshome workgroup? your question is a little unclear, but ill take it step by step.
Firstly, make sure samba is installed, do this by going to Applications > terminal:

sudo apt-get install samba samba-common samba-common-bin smbclient smbfs libpam-smbpass

When you type your password in it might appear that its not typing, dont worry, it is.
Now, type:

sudo gedit /etc/samba/smb.conf

Find where it says:
workgroup = workgroup

Change it to this:

workgroup = mshome

Go to file > save.
Now go back to terminal and type:

sudo service smbd restart
sudo service nmbd restart

you should now be in the mshome workgroup :)

---

### Post by yeldarbs1 on 2011-02-23
when i type in sudo gedit/etc/samba/smb.conf it says command not found, also after samba installed it didnot ask for my password.

---

### Post by gdawg on 2011-02-23
Follow gedit with a space. sudo gedit /etc/samba/smb.conf

---

### Post by rpaar63 on 2011-02-24
Thank you, I was searching how to do the very same thing. It now works just like i wanted.

---

### Post by yeldarbs1 on 2011-02-27
ok that part works fine now thank you, now with the other problem-- in the list of terminals and other parameters on my network only one works when i click to open it the others come up with failed to retrieve share list from server"i cant find any difference in the way they are shared. thanks again for the help.

---

