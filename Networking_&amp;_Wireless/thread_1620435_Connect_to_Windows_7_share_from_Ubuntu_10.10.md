---
title: "Connect to Windows 7 share from Ubuntu 10.10"
date: 2010-11-13
forum: Networking &amp; Wireless
---

### Post by Vikstar on 2010-11-13
How does one connect to a Windows 7 share from Ubuntu 10.10? I switched from Windows 7 to Ubuntu 10.10 while my wife still uses Windows 7. I'm trying to connect to a share on her computer from mine. I've done the steps shown here: [http://www.liberiangeek.net/2010/09/quickly-access-windows-shares-ubuntu-10-10-maverick-meerkat/]("http://www.liberiangeek.net/2010/09/quickly-access-windows-shares-ubuntu-10-10-maverick-meerkat/").

Tried with password protected sharing, tried it without, with a password on her account, without. Nothing works. Every time it tries to connect the dialog box with "Password required for share" shows up (even when password protection is turned off!) and all combinations of using a password or not do not work, the dialog box just keeps popping up.

Does anyone have a working solution on how to connect to a Windows 7 machine from Ubuntu 10.10?

---

### Post by baldy4eva on 2010-11-13
Quite a bit of info in this thread... [http://ubuntuforums.org/showthread.php?t=1604180](http://ubuntuforums.org/showthread.php?t=1604180) helped me out loads :D

---

### Post by baldy4eva on 2010-11-13
Forgot to say, the bit about Windows Live Sign In Assistant on page 2 or 3 seemed to have been the main issue

---

### Post by Vikstar on 2010-11-13
> **baldy4eva said:**
> Forgot to say, the bit about Windows Live Sign In Assistant on page 2 or 3 seemed to have been the main issue

Windows Live Sign-in Assistant was one of the first things I checked before posting. I've never installed it intentionally and I can't find it under W7's "Uninstall Programs", so I don't have it unless it's hidden away somewhere within the W7 configuration abyss.

Adding the IP to hosts didn't work either. My workgroup is already called WORKGROUP. nmap shows 139 and 445 open likewise. It's funny, because I can see her computer with the server icon inside the Nautilus "Network" link, and there is also a "Windows Network" where I can navigate through "Workgroup" to get to her computer as well, just can't get in.

---

### Post by rickatnight11 on 2010-12-14
I have the same issue.  Thanks for the tip about Windows Live Sign-In.  That fixed the issue with one of my Windows 7 machines.  There's still another without the Windows Live Sign-In software installed.  When I run the **smbclient** command to the now-working machine it gives the list of shares, but using it on the non-working machine gives me this:

rickatnight11@Fuzzalien:~$ smbclient -L Fuzzdump -U Rick%##########
session setup failed: SUCCESS - 0

Any other suggestions?

---

