---
title: "Access denied in samba to windows 7 PC"
date: 2010-12-25
forum: Networking &amp; Wireless
---

### Post by LocoMan on 2010-12-25
Ok, here goes.

I had 10.04 set up in my computer so that I had two folders in home, they connected to folders in a windows 7 computer by adding the following to the fstab file:

```
//10.0.0.80/Movies /home/loco/Videos/Movies   cifs  username=guest,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

//10.0.0.80/Anime /home/loco/Videos/Anime   cifs  username=guest,iocharset=utf8,file_mode=0777,dir_mode=0777
```

When I upgraded to 10.10, both folders are empty, and if I try to manually navigate to the folders by going to network - Samba Shares - Workgroup - locoman-pc, it either asks me for a login and password (I've tried "guest" as login and no password, and the login and password of all windows accounts), and keeps asking me over and over or just tells me access denied.

I'm guessing it's something that was changed with the upgrade to 10.10 since the windows 7 computer is the same and I didn't change anything there, but I have no idea how to even begin to troubleshoot it.

---

### Post by LocoMan on 2010-12-26
I usually don't like to do this but... bump

---

### Post by Boondoklife on 2010-12-26
what is the out of:
smbclient -L 10.0.0.80 -U guest

---

### Post by LocoMan on 2010-12-28
This is the result:

```
Enter guest's password: 
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows 7 Ultimate 7600] Server=[Windows 7 Ultimate 6.1]

        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 10.0.0.80 failed (Called name not present)
session request to 10 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

```

---

### Post by LocoMan on 2010-12-29
eeer... bump?

---

### Post by PatchesTheCaveman on 2010-12-29
Do you have Windows Live Essentials installed on the Windows 7 PC?  The Windows Live Sign-In Assistant portion of that software makes a small change to the way Windows 7 communicates over SMB that breaks the version of Samba included with Ubuntu.

While the Samba team has fixed the official version, Canonical has not yet released an updated version for Ubuntu.  In the meantime, you can get it working again by uninstalling the Windows Live Sign-In Assistant.

Incidentally, Windows Live Essentials will sometimes install via Windows Update so it could have installed without your knowledge.

---

### Post by LocoMan on 2010-12-29
> **PatchesTheCaveman said:**
> Do you have Windows Live Essentials installed on the Windows 7 PC?  The Windows Live Sign-In Assistant portion of that software makes a small change to the way Windows 7 communicates over SMB that breaks the version of Samba included with Ubuntu.

While the Samba team has fixed the official version, Canonical has not yet released an updated version for Ubuntu.  In the meantime, you can get it working again by uninstalling the Windows Live Sign-In Assistant.

Incidentally, Windows Live Essentials will sometimes install via Windows Update so it could have installed without your knowledge. THANK YOU!!!

That was it. I didn't have windows live sign-in assistant listed, but I did have windows live essentials (only messenger installed), removing it fixed the problem. I had only installed it because I was fixing my wife's computer's webcam (with messenger) and needed another one on the network to try it out. Personally I much prefer to use pidgin or some other multi IM program (the very few times I use IM, that is, I prefer IRC)

---

### Post by PatchesTheCaveman on 2010-12-29
You're welcome!

):P

Thank you for verifying that you can't uninstall the Sign-In Assistant separately from Windows Live Essentials.  Some other posters had left me with the impression that this was possible.

---

