---
title: "connecting to a windows network"
date: 2005-12-15
forum: Networking &amp; Wireless
---

### Post by ernie on 2005-12-15
in one of my school classes i am messing aronund with ubuntu and i want to connect it so that i can see my folders and things on the windows network servers how do i do it

---

### Post by wylfing on 2005-12-15
Open a terminal and type:
```
sudo apt-get install samba samba-common
```
Then you need to set yourself up to be part of a Windows workgroup. Probably the easiest way to do that is editing a file called smb.conf. To do that, run this command from a terminal:
```
sudo gedit /etc/samba/smb.conf
```
Find the line that says "workgroup =" and change the value to something appropriate. Save the file. Now type this in the terminal:
```
sudo /etc/init.d/samba restart
```
Now you should be able to browse to shares on the Windows server by going to Places > Network Servers.

---

### Post by MetalMusicAddict on 2005-12-15
What exactly does **samba-common** do? Also, since Hoary I havnt been able to brows shares without inputting a username and password for every box on my network. In Warty if it was in my workgroup I could browse it no problem.

---

### Post by davidsrsb on 2005-12-16
You don't need to run the samba server to connect to Windows shares.
Just install samba for smbmnt and smbumount and the smb4k package.

The samba server presents windows shares on your Linux pc to Windows machines.

---

### Post by Gurgeh on 2005-12-16
Alternatively, u could just use the "Connect to ...." in the system menu if you know the IP address (and remember to set the drop down box to Windows share).

---

### Post by Moezzie on 2005-12-17
i've got the same problems as described earlier. And followed  your little "tut" but there is a big issure: It dont lets me log in at those loginwindows. I write my username and password but 1 second after i clicked ok the same window pops up gain. If i just close it the just comes a msg telling me that i cant se the contets of the workgroup.

what can i do about this?

---

