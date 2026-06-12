---
title: "Mapping a network drive ? How ?"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by Drood on 2009-01-27
Hi .So basically im trying to add a network drive to my computer for school. I am connected to the school network (resnet) and with windows  vista all I had to do was use the "map network drive" thing and enter the passwords and folder. Now with ubuntu im thinking I have to go to the " connect to server thing" I did but im not sure what to put where. I know I sound really stupid but I seriously don't know how to do this in ubuntu.The farthest I got to was : connect to server - > windows share .

This were the instructions for windows :
   1.  Open My Computer.
   2. On the left hand side of the window is a section called Other Places.
          * Right click on My Network Places.
          * Choose Map Network Drive.
   3. For the drive letter, choose T (to map the department T-Drive)
   4. In the Folder text box, type \\itksrv1\progs
   5. Be sure Reconnect at Logon is checked.
   6. Click on Connect using a different user name.
   7. In the popup window enter adilstu\(your drive assignment) - For example you might type adilstu\itk1779999 (depending on the exact drive assignment you were given).
   8. Use the password assigned to your drive not your ULID password.
   9. Click OK then Finish.
  10. Choose the drive letter H (to map your assigned H-Drive)
  11. In the Folder text box, type \\itksrv5\(your drive assignment)
  12. Repeat steps 5-9 above.

This are the ones for MAC, if it helps..

These instructions are for Mac OS X 10.4 and 10.5. To map network drives to an ITK network share, do the following:

   1. On the Finder menu bar, click Go > Connect to Server....
   2. The Connect to Server window will appear.
   3. In the box labeled Server Address:, type one of the following network paths (based on the network share you would like to access).
          * smb://itksrv5/yourULID
          * smb://itksrv1/progs
   4. Click Connect.
   5. Enter your ITK user name and ITK password when prompted to do so.

The network share you connected to will automatically open.

    * On Mac OS X 10.4, the network share will appear on your desktop.
    * On Mac OS X 10.5, network shares do not automatically appear on the desktop. To show connected shares on the desktop, refer to 1375: Network drives do not appear on the desktop in Mac OS X 10.5.


Thanks in advance for your help, let me know if you need anything.

---

### Post by Drood on 2009-01-27
I tried to apply this to my situation (since they are similar ) but for some reason It wont work, it says it cant find the drive.

[http://ubuntuforums.org/showthread.php?t=1004850](http://ubuntuforums.org/showthread.php?t=1004850)

---

### Post by Another Monkey on 2009-01-27
If you have smblcient installed just open Nautilus (that's the file/network browser in Gnome) and in the address:
```
smb://name-of-server/name-of-share
```
then hit enter.  If you have Samba (and your firewall!) correctly set up, then this should work (Ubuntu will automatically mount it).

Pretty much like the Mac instructions to be honest.

Although, you might want to read a bit about "Samba" and how to use it.

---

### Post by Drood on 2009-01-27
Thanks for your prompt reply, I just got connected to it using the connect to server thing. It worked, just had to try different things, now is there any way of placing a shortcut in my desktop to have it there permanently everytime I turn on the PC ?

---

### Post by Another Monkey on 2009-01-27
There probably is, but I have never tried to do it.

Maybe a URL?

---

### Post by Drood on 2009-01-27
/bump I read something about adding it to a fstab or something like that. But I do not know what exactly to add to it. Can someone make the line for me. Just tell me what info you need, server ? domain name? user/ pass

---

### Post by Drood on 2009-01-31
Solved. Ubuntu wiki had it.

---

