---
title: "Printer sharing problem"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by coolkid5 on 2010-12-26
Hi, I'm having a problem with network printing.  Previously, I had my printer hooked up to computer running Windows XP, and I had it set up so that the printer was shared across the network.
Recently, I replaced the Windows XP machine with a Windows 7 machine and now I've been trying to get the network printing working again but I'm having problems.  Here's what I tried to do when setting it up:
I went on the windows computer and set it to share the printer. Then, on my Ubuntu 10.10 computer, I went to System->Administration->Printing and tried to add the printer.  I went to add the "Windows Printer via SAMBA" as I had done when I had set up network printing before, and I browsed for the Windows computer which is in the domain "WORKGROUP."  However, when I go to access the right computer, a dialogue pops up saying "You must log in to access [computer-name]."  It asks for my Username, Domain, and Password, which I filled in using my Ubuntu username and password (with Domain set to WORKGROUP) but when I hit OK it says "Not authorized: The password may be incorrect."  So... I'm wondering is there some permissions thing I need to edit on my windows computer to that this will work.  I don't recall having this problem before, but it was a while ago.

Thanks!

---

### Post by drdos2006 on 2010-12-26
Windows 7 does not have Internet Printing Protocol installed, XP does. Microsoft have issued a patch but I could not get it work. Google on Windows 7, Internet Printing and see what comes back for you.

regards

---

### Post by coolkid5 on 2010-12-26
Actually, I think my problem is more general than just printing.  I cannot access any shared files on the Windows 7 computer.  Whenever I try to, the dialogue box asking for my username and password comes up.

I now realize that others are having the same exact problem:
[http://ubuntuforums.org/showthread.php?t=1653257]("http://ubuntuforums.org/showthread.php?t=1653257")
[http://ubuntuforums.org/showthread.php?t=1653143]("http://ubuntuforums.org/showthread.php?t=1653143")

Does someone know anything more about this issue? Is it a bug? Is it not possible to access Windows 7 shared folders?

---

### Post by garvinrick4 on 2010-12-26
#Must have windows machine using username and password to login to Windows. Cannot
use auto login. 
# Re-check your workgroup set-up and that all your items printer, C; drive, media and such are shared.
# Your problem is at the username and password right now and is a Windows setup thing.
# I have 6 linux installs a 7 and a Vista and Ubuntu comes out of box set to see Windows workgroup,
   It is a windows problem for sure in your setup. 
# if I install Ubuntu on a test partition I keep it is already set to see Windows workgroup, as simple as that.

---

### Post by garvinrick4 on 2010-12-26
At one time it was a bug back in 9.10 in a Alpha or a Beta but I have not heard nor
seen of the bug since it was fixed. I would go bug checking in launchpad if you are 
certain you have Windows workgroup set up right.  Upper right of the page launchpad.net
Good luck and keep at it you will find the problem.

---

