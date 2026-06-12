---
title: "Network directory automatic mounting"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by Thyago Lopes on 2009-02-25
Hello all,

I'm from Brazil and, for that reason, I have loads of files and directories with names containing characters that aren't available in the English language. In my computer I face no problems because Ubuntu deals very well with that, but, when I try to smbmount a directory from my other computer, these characters aren't read correctly, I find a coding problem.

The funny thing, though, is that when I go to smb://<other_pc_ip> it shows the names perfectly.

So, what I'd like to ask is if anyone knows how Ubuntu mounts these directories automatically so that I could do the same and maybe find a way to mount it always automatically.

I'm using Ubuntu 8.10 and accessing my lan through a Wireless connection. The system LOCALE is set to PT_BR. Oh, and the other computer runs a Windows XP.

Thanks for any help.

---

### Post by Iowan on 2009-02-25
[This]("http://ubuntuforums.org/showthread.php?t=288534") is my favorite Samba-mounting How-To, but I don't know (pardon my ignorance) if utf8 will work for you. Dunno if [this]("http://ubuntuforums.org/showthread.php?&t=283131") one on FSTAB will be helpful.

---

### Post by Thyago Lopes on 2009-02-25
Thanks a lot Iowan, it was exactly what I was looking for, solved my problem.

---

