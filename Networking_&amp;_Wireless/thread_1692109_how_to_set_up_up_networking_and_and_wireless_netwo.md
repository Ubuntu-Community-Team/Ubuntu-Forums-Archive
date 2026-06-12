---
title: "how to set up up networking and and wireless networking in ubuntu 10.04"
date: 2011-02-20
forum: Networking &amp; Wireless
---

### Post by chitragurung on 2011-02-20
I just installed UBUNTU 10.04 in my dell inspiron machine mini 10. It is fresh installation. Before it was 8.04.  After installation, network not working, wireless internet also not working, internet not working. How can I fix it ?
 
Network card is Broad com corportaion.

---

### Post by topcat7736 on 2011-02-20
Hi chitragurung!

Try replacing your smb.conf file with the following one. (Save the original as smb.conf.master before doing the change). 

Change the name WORKGROUP to the name of your workgroup, the name GATEWAY to the name of your computer and, after saving the file, re-boot and you should be able to connect to networks without a problem.

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
```Hope this helps you out.

Al

---

### Post by chitragurung on 2011-02-21
How to edit it ?
 
When I do gedit smb.conf it open empty

---

### Post by topcat7736 on 2011-02-21
Linux is a rather difficult operating system to setup and use. On another forum, venzkep provided me with a link to Mr. Swerdna's site where I found the solution to networking my machines. Through experimentation, I found that the above replacement Samba file allows you to access other machines on your network and access printers attached to them without needing to do have anything else in the Samba file. Indeed, I can access a HP printer attached to a Windows 7 computer without a problem although the HP driver site says it can't be done. While Samba offers a huge amount of options, the above replacement is all one needs to do any desired networking.

Here is the link to Mr. Swerdna's site but first try using only the one above. (The printer items Mr. Swerdna includes weren't needed).

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
8) Left click "Edit" and then left click "Select All"
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
Tell it to share the file and it will say some things need to be installed. Allow it to install the items and you should then be able to share any of your files with other machines on your network.

Al

---

### Post by chitragurung on 2011-02-21
Finally it works using various methods. But I have got problem to re-store evolution back files.

---

