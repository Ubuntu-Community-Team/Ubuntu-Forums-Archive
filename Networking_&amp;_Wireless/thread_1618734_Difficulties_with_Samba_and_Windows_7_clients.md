---
title: "Difficulties with Samba and Windows 7 clients"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by deusexcalibur on 2010-11-11
I set up a home server running Ubuntu Server 10.10, but I've been running into problems with Samba.

I want anyone in my home network to be able to browse folders and print.

I can get the media share folder viewable by setting security = share and setting the proper permissions for the /share directory. No problem there. The real headache is printing.

I managed to get it working by installing drivers manually on the Windows client side. I just install the HP Universal PS Printing drivers on my end when it prompts for a driver. The Ubuntu machine is using HPLIP with a DeskJet 4180. The problem started when I realized that I could simply upload the drivers to the server to share. At first I had a bit of hassle, but I created a root account for SMB, set security to user, and set the write list to root for [print$]. The drivers were uploaded. 

I started running into another problem after this. On my laptop I started getting messages how I couldn't connect to the printer. I tried to log back in on my desktop and the server kept denying me access even using the SMB root account. I could enter the server without even logging in on my laptop despite the fact the password wasn't stored. Security = share solved this but it is still unsettling.

I thought I had to add an account with the same login name as my Windows user so I did sudo smbpasswd -a blake, (Windows account is Blake) but this did not work either. 

So now I am stuck where I cannot add the printer on the laptop (it can also log right in to the server without entering a pass with security = user) and my desktop cannot connect at all. (login refused with both root and blake) I'm not sure what to try from here. I'd appreciate any help!

EDIT: This brings about another question: How do users in Samba work? The more I read the more I get confused. Is it case sensitive? For myself do I need to have a blake (or Blake if case sensitive) account in ubuntu, samba, and windows? (All with matching passwords too?)

---

### Post by mastapat11 on 2010-11-11
1st) you don't **Need** the same account in ubuntu, samba, and windows, but it helps in saving you/end user confusion (and personally i'm lazy to remember multiple passwds)

2nd) u **Should** add an account with the same login name as ur linux account not win. so the cmd line should read: ```
sudo smbpasswd -a "*ubuntu username*"
``` ```
sudo smbpasswd -e "*ubuntu username*"
```  Then ```
sudo smbpasswd "*ubuntu username*"
``` and enter ur ubuntu password twice.


3rd) i would stick with 'security = user'. I *"think"* that's more secure. restart samba ```
sudo restart smbd
```

4th) what ver of Win are you using? whichever, remove the stored passwd to ur linux samba svr.  Now try to connect to the server.

PS. do you have a firewall on the server? if so, u need to allow samba thru.

---

### Post by deusexcalibur on 2010-11-11
Thanks for that info, it solved the login difficulties.

The printer problem still remains unfortunately. I noticed that the printer driver files ended up in the W32X86 folder instead of the x64 like it should have. That may explain why my desktop which already has the driver files in the Windows driver directory works and the laptop doesn't. I also had an error message come up when I first uploaded the drivers after I hit "apply."

Is there a way to de-register printer drivers in Samba? It seems like it doesn't work well with Windows 7. I should've been able to upload the drivers as user "blake" since I am an lpadmin.

EDIT: Fixed the other PC not being able to install the print$ drivers, I had to add the user to the allowed user in CUPS.

---

