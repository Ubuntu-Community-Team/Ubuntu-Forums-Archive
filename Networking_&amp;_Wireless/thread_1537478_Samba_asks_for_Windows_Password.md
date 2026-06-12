---
title: "Samba asks for Windows Password"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by davidkazuhiro on 2010-07-23
I'm using Ubuntu 9.10 and trying to install a printer over the network which is plugged into a Windows 7 machine.

I can see the workgroup fine and the computer fine on the network, but when I try to double-click on the computer (both via the nautilus and the printer setup route), it asks me for a username, workgroup and password.

I tried the account's username and password and username "Guest" with no password but neither worked. The weird thing is that when I booted my machine into Windows XP and tried to install the same printer, it never asked me for a username and password and installed just fine.

Why is Samba/Ubuntu asking me for the Windows 7 password when Windows XP didn't need it?

---

### Post by Morbius1 on 2010-07-23
Do you have "Windows Live Sign-In Assistant" installed on the Win7 machine?

[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)

You might want to consider uninstalling it.

---

### Post by Unterseeboot_234 on 2010-07-23
I have spent 2 days on this. There is a huge amount of mis-information out there to google and try. Even the Information Article from Microsoft is wrong, they leave out steps. The Microsoft Forums do not care. XP even has a problem with Win7.

Out of all the "recipes", "howtos", forums, you name it, there might be bandaid fixes for certain hardware configurations of networks. I get limited access, wired DNS-router, using the current Samba on the Ubuntu end. HomeNetwork on the Winny7 end; a user profile without a password. That user has a library and a shared printer in user/public.

[Ubuntu menu]> Places -> Network (dbl-click) Windows Network <icon>. Is the 'magic sesame" that shows <WORKGROUP icon> dbl-click <COMPUTER-A icon> then all the folder... BUT you can only look at contents inside of /Public. The connection is bookmarked. That bookmark will be the only chance to tunnel back into Win7 files. Going back through Nautilus-Network hangs.

Any ip addressing, any NetBios (human label), any Windows Share, any password, Guest, UbuntuName etc... that all has to be done in the samba config file. You will waste **FOREVER AND A DAY** trying to do it that way.

If anybody can actually help you with the password feature, bring it on. I want to hear about it. The Ubuntu staff cannot connect Win7 network accounts.

==============
Excuse, but the Windows Live Assistant removal makes no difference. That may have been a great hack 4 or 5 months ago, but with the current releases of Win7 vs. Samba, removing Live Assistant is an exercise in aggravation.

---

### Post by davidkazuhiro on 2010-07-23
Thanks Morbius1 for the link to the [Microsoft thread]("http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527"). According to David Konrad on that thread, it's a bug in Samba which doesn't anticipate the extra layer of authentication imposed by the Windows Live Sign-In Assistant.

It appears on the [Samba bug tracker]("https://bugzilla.samba.org/show_bug.cgi?id=7577") that the bug has been fixed, but it's probably going to take a while before the patch makes it into the Ubuntu distro.

I'll see if I can convince the owner of the Windows 7 machine to uninstall the Windows Live Sign-In Assistant, and I'll confirm on here whether that worked or not.

--
Thanks Unterseeboot_234 for sharing, I've been going through the same frustration for the past month. It's nice to finally look like this issue is going to get resolved. Hopefully we'll both be happy by the end of today.

---

### Post by Morbius1 on 2010-07-23
> **davidkazuhiro said:**
> I'll see if I can convince the owner of the Windows 7 machine to uninstall the Windows Live Sign-In Assistant, and I'll confirm on here whether that worked or not.
You know it never even occurred to me that it wasn't your Win7 box.  :)

---

### Post by Unterseeboot_234 on 2010-07-25
I was able to network over a hard-wired DNS / internet home network. Win7 on one box, Ubuntu 9.10 on another. It works, the difficulty is seeing the user as the gateway. 

The Win7 user is joined to a named WorkGroup. 
The user has the option to share an asset visible to the named workgroup -- asset being library or hardware.
The user can then grant access privileges to visitors.

On the Ubuntu end, you must manually edit the Samba config file. The only change you need to do is match the Win7 Workgroup name. Save the file, reboot or shutdown / restart Samba. 

Win7 has a a clean interface, but it is web-page like. Be sure to look for the buttons that commit options before navigating off the page that represents a dialog box, e.g. the Win7 dialogs have a different feel.

here is the site that helped ...

**[http://www.7tutorials.com/how-change-workgroup-windows-7]("http://www.7tutorials.com/how-change-workgroup-windows-7")**

Note this is using Samba that is joined to a Workgroup. I have yet to get 'domain' or 'share' to work. Indeed, Win7 forbids volumes, e.g. > C:\


Much mis-information out there on the web. In fact, suspect any network advice that is more than 4 months older than this post.

Good luck.

---

