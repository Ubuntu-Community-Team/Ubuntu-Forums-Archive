---
title: "Transferring Large Files Between 2 Computers"
date: 2012-11-19
forum: Networking &amp; Wireless
---

### Post by StuFranks on 2012-11-19
Hey,
I have recently built a pc which is running Ubuntu 12.10 and I want to transfer all my music to it. My music is currently on a laptop running WIndows 7. 

What is the best way to transfer the songs from the laptop to the pc?

How would I go about setting up a shared folder on the Ubuntu system which can be seen from the Win 7 laptop?

Cheers,
Stu

---

### Post by vahnx on 2012-11-19
On your Ubuntu system, open the terminal and **sudo apt-get install system-config-samba** then open it in System Tools > Administration. You can use the + button in this program to easily add a share and make it visible and writable with the checkboxes and browse to the folder you wish to share. You can also use the Access tab and make it accessible by everyone (always works for me). Then with Windows I find it's easiest to open up any folder and in the top address bar, type the IP of the Ubuntu system preceding with \\ and you should see your share listed. You can then just copy and paste into it.

[IMG]http://img825.imageshack.us/img825/1640/59133962.png[/IMG]

[IMG]http://img819.imageshack.us/img819/3044/72298552.png[/IMG]

---

### Post by dannyboy79 on 2012-11-19
as a side note, you may want to copy chunks at a time instead of all at once in case you have a power failure or some other weird situation.

I have not used samba within 12.10 but in 10.04.4 I had to make sure that ubuntu was in the same workgroup name as my windows computer which was either mshome or workgroup by default in windows. If the workgroup isn't the same, you won't be able to "browse the network" and see the windows machine or vice versa.

---

### Post by vahnx on 2012-11-19
Ah yes, also make sure you're on the same workgroup in Ubuntu. 

In /etc/samba/smb.conf make sure you have

[B][global]
workgroup = WORKGROUP #or whatever your workgroup is
name resolve order = bcast host[/B]

---

### Post by wojox on 2012-11-19
My favourite [WinSCP: Free SFTP, SCP and FTP client for Windows]("http://winscp.net/eng/index.php")

---

