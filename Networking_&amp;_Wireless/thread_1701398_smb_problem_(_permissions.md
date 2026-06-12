---
title: "smb problem ( permissions"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by yeldarbs1 on 2011-03-06
i have windows machines running on my lan and one linux machine running ubuntu 10.10 i can see my linux machine on all windows machines but cannot connect to it. it says it cannot find network path or i may have permission. when i try to change permissions on my linux machine when i try to save it, it says ¨changing the attributes of files is not supported with protocol smb.¨ how do i change the permmisions or  connect my linux machine on my lan?

---

### Post by headvampyre@hotmail.co.uk on 2011-03-06
Dont change any permissions via SMB through nautilus, its not designed for windows networks, just change them by running nautilus as root (ALT+F2 > gksu nautilus /). Also - have you checked your smb.conf?

---

### Post by topcat7736 on 2011-03-07
Hi yeldarbs1!

(The following assumes you're using a router for your network connections).

The following  should replace the default smb.conf file which comes with Ubuntu. Once  you do it, you will be able to network with other Ubuntu, Windows XP and  Windows 7 computers without a problem. Plus, you can directly access  printers attached to those computers using the standard drivers provided  with Ubuntu via the Samba share.

Before saving this smb file, change WORKGROUP to the name of your  windows workgroup, (IE MSHOME) and change GATEWAY to the unique network  name of the computer you are using.

```

[global] 
workgroup = WORKGROUP
netbios name = GATEWAY
name resolve order = bcast host lmhosts wins
map to guest = Bad User
os level = 33
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False 

```Linux is a rather difficult operating system to setup and use. On   another forum, venzkep provided me with a link to Mr. Swerdna's site   where I found the solution to networking my machines. Through   experimentation, I found that the above replacement Samba file allows   you to access other machines on your network and access printers   attached to them without needing to do have anything else in the Samba   file. Indeed, I can access a HP printer attached to a Windows 7 computer   without a problem although the HP driver site says it can't be done.   While Samba offers a huge amount of options, the above replacement is   all one needs to do any desired networking.

Here is the link to Mr. Swerdna's site but first try using only the one   above. (The printer items Mr. Swerdna includes weren't needed).

[http://www.swerdna.org/index.html](http://www.swerdna.org/index.html)

To edit your smb file,

1) Load the terminal
2) Type sudo gedit /etc/samba/smb.conf
3) enter your authenticate password
    your smb.conf file will now be open on the screen
4) Left click "File" and then "Save As"
    Change the name to smb.conf.master and press enter
    You will now be editing the smb.conf.master file
5) Left click "File" and then "Close"
6) Left click "File" and then "Open"
7) Left click smb.conf and left click "Open"
8. Left click "Edit" and then left click "Select All"
    When the Samba file is highlighted, put your cursor on it and right click "delete"
9) Highlight and copy the new file I posted for you
10) Left click somewhere on the now blank page
      right click and select "paste"
11) With the new Samba file on the screen, 
      Left click "File" and then "Save"
12) Left click "File" and then "Quit"
13) Back at the terminal, type "exit" and then enter or return

Re-boot your machine to effect the new Samba file.

After the machine re-boots, go to "Places" and left click "Home Folders"
Right click on "Public" and select "sharing options"
Tell it to share the file and it will say some things need to be   installed. Allow it to install the items and you should then be able to   share any of your files with other machines on your network.

Al

---

### Post by yeldarbs1 on 2011-03-08
> **headvampyre@hotmail.co.uk said:**
> Dont change any permissions via SMB through nautilus, its not designed for windows networks, just change them by running nautilus as root (ALT+F2 > gksu nautilus /). Also - have you checked your smb.conf? thanks for the help this seems to help:D:D

---

### Post by yeldarbs1 on 2011-03-08
> **topcat7736 said:**
> Hi yeldarbs1!

(The following assumes you're using a router for your network connections).

The following  should replace the default smb.conf file which comes with Ubuntu. Once  you do it, you will be able to network with other Ubuntu, Windows XP and  Windows 7 computers without a problem. Plus, you can directly access  printers attached to those computers using the standard drivers provided  with Ubuntu via the Samba share.

Before saving this smb file, change WORKGROUP to the name of your  windows workgroup, (IE MSHOME) and change GATEWAY to the unique network  name of the computer you are using.

```

[global] 
workgroup = WORKGROUP
netbios name = GATEWAY
name resolve order = bcast host lmhosts wins
map to guest = Bad User
os level = 33
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False 

```Linux is a rather difficult operating system to setup and use. On   another forum, venzkep provided me with a link to Mr. Swerdna's site   where I found the solution to networking my machines. Through   experimentation, I found that the above replacement Samba file allows   you to access other machines on your network and access printers   attached to them without needing to do have anything else in the Samba   file. Indeed, I can access a HP printer attached to a Windows 7 computer   without a problem although the HP driver site says it can't be done.   While Samba offers a huge amount of options, the above replacement is   all one needs to do any desired networking.

Here is the link to Mr. Swerdna's site but first try using only the one   above. (The printer items Mr. Swerdna includes weren't needed).

[http://www.swerdna.org/index.html](http://www.swerdna.org/index.html)

To edit your smb file,

1) Load the terminal
2) Type sudo gedit /etc/samba/smb.conf
3) enter your authenticate password
    your smb.conf file will now be open on the screen
4) Left click "File" and then "Save As"
    Change the name to smb.conf.master and press enter
    You will now be editing the smb.conf.master file
5) Left click "File" and then "Close"
6) Left click "File" and then "Open"
7) Left click smb.conf and left click "Open"
8. Left click "Edit" and then left click "Select All"
    When the Samba file is highlighted, put your cursor on it and right click "delete"
9) Highlight and copy the new file I posted for you
10) Left click somewhere on the now blank page
      right click and select "paste"
11) With the new Samba file on the screen, 
      Left click "File" and then "Save"
12) Left click "File" and then "Quit"
13) Back at the terminal, type "exit" and then enter or return

Re-boot your machine to effect the new Samba file.

After the machine re-boots, go to "Places" and left click "Home Folders"
Right click on "Public" and select "sharing options"
Tell it to share the file and it will say some things need to be   installed. Allow it to install the items and you should then be able to   share any of your files with other machines on your network.

Al thanks for helping i think ill try swerdnas help file also. thank you again i appreciate it.

---

