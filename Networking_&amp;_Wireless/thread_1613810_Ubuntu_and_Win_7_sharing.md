---
title: "Ubuntu and Win 7 sharing"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by andysom25 on 2010-11-04
Hello I am running Ubuntu Desktop 10.10
yes I am a noob I apologize in advance, all I simply want to do is be able to access shared files on my laptop from my ubuntu desktop, I have disabled password protected sharing in windows and for some reason I cannot connect to the laptop, although from the laptop I can still few shared files on ubuntu...
help?

---

### Post by andysom25 on 2010-11-04
bump.... this is driving me insane anyone please help if possible I will love you all forever!

---

### Post by dforthman on 2010-11-05
Is the folder you want to share set up correctly? Correct permissions set?

Go to the folder's properties and click the Sharing tab.
In Group or user names, hit Advanced Sharing.
Be sure it is set to "Share" and choose "Permissions"
If "Everyone" is not listed, click "Add" type "Everyone" and hit "OK". 
Assign Everyone full control. Hit OK. and close the sharing window.
Move to the Security tab (if listed) and click Edit.
Click 'Add' and add Everyone to the list of users.

If you want to be quick and dirty, assign "Full Control" to the Everyone user. If you want to limit what "Everyone" can do, choose the lowest permissions needed.

Hit "Ok" and try accessing the windows share again.

---

### Post by dforthman on 2010-11-05
If it's a default install, shouldn't Samba be installed by default?

I have a fresh install, and below is a list of shares on one of my Windows 7 computers at work.

---

### Post by andysom25 on 2010-11-05
alright see now I can one of the vista desktops but still my windows 7 laptop refuses me access and ask for password after I turn off password protection every time, advice? any more info you guys need let me know?

---

### Post by dforthman on 2010-11-05
Was the Vista machine giving problems before? 
What did you do to make the share work like you want?
Did you duplicate this on the Windows 7 machine or set up permissions on the shared folder?

---

### Post by dforthman on 2010-11-05
Posted twice, sorry.

---

### Post by andysom25 on 2010-11-05
alright so actually no the vista computer never gave me problems I didn't have to change anything on there and I have double triple checked the permissions on the windows 7 laptop

---

