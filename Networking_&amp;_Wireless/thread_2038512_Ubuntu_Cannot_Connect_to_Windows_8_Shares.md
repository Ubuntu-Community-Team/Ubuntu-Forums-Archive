---
title: "Ubuntu Cannot Connect to Windows 8 Shares?"
date: 2012-08-06
forum: Networking &amp; Wireless
---

### Post by josiahrulez on 2012-08-06
Hey All,

So my download box is running Ubuntu 11.04 and i have recently upgraded my Main Gaming PC and Fileserver to Windows 8. 

But now my download box cannot access shares on either Windows 8 PC, but it can still access shares on Windows 7 PCs. 

I have tried to update by
sudo apt-get update
sudo apt-get upgrade

But hasn't fixed my issue.

---

### Post by josiahrulez on 2012-08-07
Anyone with a similar issue with Ubuntu and windows 8?

---

### Post by ambsace on 2012-10-02
> **josiahrulez said:**
> Hey All,

So my download box is running Ubuntu 11.04 and i have recently upgraded my Main Gaming PC and Fileserver to Windows 8. 

But now my download box cannot access shares on either Windows 8 PC, but it can still access shares on Windows 7 PCs. 

I have tried to update by
sudo apt-get update
sudo apt-get upgrade

But hasn't fixed my issue.

Hi there,

I did a clean install of Windows 8 on a home PC, and ran into the same problems as you have.  

One of the things that I did during the install was sign in with a Microsoft account (e.g., [email]XYZ@live.com[/email]).

I was able to get Ubuntu (well, Lubuntu 12.04) to access my Win8 shares by going to the 

[INDENT]"Settings Charm" > "Change PC Settings" > "Users" > "Switch to local account"[/INDENT]

This prompted me to create a new account which would then work when attempting to connect via Samba.

Hope that works.

---

