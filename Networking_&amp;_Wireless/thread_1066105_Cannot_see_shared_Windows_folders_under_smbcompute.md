---
title: "Cannot see shared Windows folders under smb://computer-name/"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by SteveDee on 2009-02-10
I can view the contents of Windows shared folders by specifying the shared folder name in Nautilus. Example:-
 
 smb://computer-name/steve

But I can't see a list of shared folders on a Windows computer when I use:-
 
smb://computer-name/

Windows pc can access shared directories & files on both of my Intrepid computers.

I think this is a common problem. Anyone know the solution to this?

---

### Post by jonobr on 2009-02-10
Take a look :-)


[http://ubuntuforums.org/showthread.php?t=1042030]("http://ubuntuforums.org/showthread.php?t=1042030")

---

### Post by SteveDee on 2009-02-11
> **jonobr said:**
> Take a look :-)


[http://ubuntuforums.org/showthread.php?t=1042030]("http://ubuntuforums.org/showthread.php?t=1042030")

Thanks for the link to this thread.

Although at least one person in the other thread suggests that this worked with an earlier version of 'buntu, I think the issues lie with Windows security.

From my work with DCOM I know that the Microsoft user Group "everyone" = "anyone" for WinNT & 2k. But security was tightened up with the introduction of WinXP such that "everyone" now means everyone with recognised credentials. So in order to access a Windows share on an XP machine you need a recognised Username & password.

A couple of checks led me to focus on the Windows end:-
1) running pyNeighborhood and scanning the Windows host always failed to find shared folders.
2) Running LnNeighborhood in Puppy Linux also failed to find/display shared folders. (Puppy Linux is a great distro to run from a memory stick when you want to diagnose problems).

I spent a pleasant evening with the Windows Firewall down, while adjusting various security settings until I found some kind of answer.

What reliably works for me (on both 'buntu & Puppy) is setting Windows for Simple File Sharing (from Windows Explorer > Tools > Folder Options > View > "Use Simple File Sharing")

However, I've chosen to keep Simple File Sharing disabled, and have simply created bookmarks in Nautilus for the handful of Windows folders I need access to.

Thanks again for your input.

---

### Post by jonobr on 2009-02-11
> I spent a pleasant evening with the Windows Firewall

LOL :guitar:

---

