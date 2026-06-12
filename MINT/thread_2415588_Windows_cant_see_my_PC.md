---
title: "Windows cant see my PC"
date: 2019-03-28
forum: MINT
---

### Post by daninozz on 2019-03-28
Hi all,

So im new to linux i know that ive posted under Ubuntu and my OS is actually Linux Mint but im under the impression Mint is based on Ubuntu.

anyway my question is I am trying to get my windows 10 machine to communicate with my Linux Mint machine, unfortunately due to my troubleshooting I cant seem to find the resolution.

I originally wanted to connect to my network drive which is under a workgroup so I went into the samba config file and changed the default workgroup to MSHOME which is the name of the current workgroup im trying to connect to.

after having no luck i decided to try a different approach just by creating a folder on linux and sharing that folder, unfortunately this doesnt seem to work either.

below is my troubleshooting.

- Installed Samba configured the file by changing workgroup name to mine.

- created a sharing folder into linux mint. followed this tutorial to do so.

- Enabled SMB for both client and server on my windows 10 PC

- Turned my Windows Firewall off completely.

- Reboted both machines

- Tested the communication between both machines and able to ping without any issue.

I have exhausted all my troubleshooting in getting this issue to be resolved.

Any suggestions greatly appreciated.

Cheers

---

### Post by coffeecat on 2019-03-28
*Thread moved to **Mint** subforum*.

---

### Post by Rubi1200 on 2019-04-01
Hi and welcome to the forums :-)

This link is somewhat outdated but might start pointing you in the right direction:
[https://forums.linuxmint.com/viewtopic.php?f=42&t=88146&start=0](https://forums.linuxmint.com/viewtopic.php?f=42&t=88146&start=0)

Good luck!

---

### Post by drpeppercan on 2019-04-01
I just got my Linux Mint Tessa connected to my Windows 10 pc with [Gigolo]("https://www.maketecheasier.com/manage-remote-filesystems-with-gigolo/").
So far I have only used it to access shared Windows folders.
Check this [tutorial here]("https://www.unixmen.com/how-to-access-remote-linux-and-windows-shares-with-gigolo/").

[IMG]https://s24255.pcdn.co/wp-content/uploads/2013/07/Gigolo_010.png[/IMG]

---

