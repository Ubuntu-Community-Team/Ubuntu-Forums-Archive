---
title: "FAQ not found: WinXP -&gt; Ubuntu Networking"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by nomomikeysoft on 2011-02-23
I successfully have a dual boot Ubuntu 10.10 / Windows XP system on 1 hard drive.  Samba has been installed within Ubuntu.

I have connected a 2nd computer to my router which is only running Windows XP.

Both computers are on MSHOME network.  

Here are the issues I am facing:

1) I can from WinXP to WinXP "paste" files to the other computer in the shared documents folder -- great.  However, from Ubuntu to WinXP -- I can see the WinXP file system, copy from it to Ubuntu BUT I cannot PASTE files from Ubuntu to WinXP over the network (we're just talking about Shared Documents folder here).

2) On the WinXP only computer, I can NEVER see the Ubuntu computer in network -- however, if I load (dual-boot) in WinXP, they can see each other perfectly; and the pasting works fine to the shared documents folder (thats fine with me, as long as I can paste files somewhere).

So... in Ubuntu, I can see/access the WinXP machine.  I can cut/copy files from the WinXP and save them to Ubuntu machine.  I cannot, however, paste any files from Ubuntu to the WinXP machine.

Additionally, from the WinXP machine, I can NEVER see the Ubuntu machine via network.

* How can I make the Ubuntu machine visible to my generic windows network so the WinXP only machine can see Ubuntu?  Is it because I use ext3 file system and windows cannot recognize it?

* How can I paste files from Ubuntu onto the WinXP machine in Shared Documents folder?  Must they come from a NTSF partition and not from a ext3?

Again, WinXP -> WinXP things work fine.

Thanks for your time.

---

### Post by Jack Smith on 2011-02-23
windows hates linux, and linux dislikes NTFS.  as is, windows will NOT read ext file systems and is probably causing the problem.  both operating systems can read the fat32 filesystem, however i don't think you can install ubuntu to a fat32 partition, i would suggest using a seperate fat32 partition as a go between for transfering files.  this may work, but no gaurantees as i am not an expert.

---

