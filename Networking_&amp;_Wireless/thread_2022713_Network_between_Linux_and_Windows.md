---
title: "Network between Linux and Windows"
date: 2012-07-11
forum: Networking &amp; Wireless
---

### Post by Jordan Queiroz on 2012-07-11
Hi guys.
I'm trying to navigate in my windows network through my linux PC, but it's getting hard. Whenever I open Nautilus, it's possible to see the Windows network, but everytime that I try to access the folders, the computer requests a user, domain and a password.
I enter my Ubuntu's usermane, window's homegroup and my Ubuntu's password. but it doesn't work.

How can I access the window's network?
Do I need to configure something on Samba?

thank you =)

---

### Post by Kopkins on 2012-07-11
Could it be requesting the windows user/password?

I'm fairly unfamiliar with samba/windows networking, but I always thought you had to enter an external username/password to access network stuff. 

Best of luck,
Kopkins

---

### Post by Jordan Queiroz on 2012-07-11
I also have tried the windows' password and user, but it also has not worked

---

### Post by papibe on 2012-07-11
Hi Jordan Queiroz.

It is asking for the Window's username and password.

Sometimes it is  required to enter the username in this format:
```
WORKGROUP\username
```
change 'WORKGROUP' for your actual workgroup name.

Let us know how it goes.
Regards.

---

### Post by Jordan Queiroz on 2012-07-11
Unfortunatelly, I got the same error =(

There are some windows' folders that I can access through linux (folders that I've shared before), but I can't see and access linux folder's through Windows(even the shared folders on linux).
On linux, I just can see and access the window's folder if it is already shared, otherwise, I can see the folder, but I can't access it (because of the request of user, domain and password) =(

what do I do now?

---

### Post by Kirk Schnable on 2012-07-11
The domain might not be WORKGROUP.  It might be COMPUTERNAME where COMPUTERNAME is the name of the Windows computer you are connecting to.  

The credentials you type should definitely be for the Windows computer you're connecting to, not the Ubuntu computer you're connecting from.

Make sure the Windows user who you're logging in as has permissions to access the share.

Kirk

---

