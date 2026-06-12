---
title: "Can not longer access Win 7 shares (password prompt)"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by mordanda on 2010-12-19
Everything was working well between my Windows 7 shares and all three of my Ubuntu machines.  I just replaced my buggy belkin router with a Netgear one and now none of the Ubuntu machines can open my windows box through Nautilus. All three (one 10.04, 2 10.10) can see the Windows box but when I click on it I get the never ending password prompts.

My Mac can access the Windows 7 machine fine, and all three Ubuntu boxes can access the shares with CIFS/autofs.  I just can't browse the available shares using Places->Network.

I'm lead to believe something on Win 7 reset when I changed the router but after two days I'm at a loss as to what it could be.

Any ideas?

P.S. Windows Live Sign-In Assistant is not installed.

---

### Post by garvinrick4 on 2010-12-19
Check the Windows workgroup in 7 and make sure you have everything right and it
is using a password to login. A couple of versions of Ubuntu this happened in a Alpha or
beta but not in a while and all mine are working in Windows workgroup with 7 and vista
and 6 installs of Ubuntu and fedora 14. Look into the Windows install.

---

### Post by mordanda on 2010-12-19
Actually I don't want it to prompt for the password.  The Win 7 box and the ubuntu systems are in the same workgroup and I used to be able to see the available shares on the win 7 box and nautilus wouldn't prompt for authentication.  Even if I didn't mind being authenticated my username and password are not accepted.

What confuses me is my autofs mounts still work.  It's only when I attempt to browse the shares that the prompt appears and does not accept any credentials. Password protected sharing on win 7 is turned off.  What else should I check?

---

### Post by silverbullet763 on 2011-01-01
Have you recently updated to Windows Live Essentials 2011? The previous version allowed Live Sign-In to be removed the new one does not as far as I can tell. The only way to remove the sign in on the new version is to remove the Live applications. I believe Microsoft required this update recently. Live Sign-In is no longer listed in Programs and Features. This may be why you think it is uninstalled. I had this same issue on my linux machine and found that removing Essentials solved the problem.

Appears to be a known issue: [http://aspiregemstone.blogspot.com/2010/10/windows-essentials-2011-breaks-samba.html](http://aspiregemstone.blogspot.com/2010/10/windows-essentials-2011-breaks-samba.html)

The above article also shows that Live Sign-In can be disabled via Services in Windows 7.

---

