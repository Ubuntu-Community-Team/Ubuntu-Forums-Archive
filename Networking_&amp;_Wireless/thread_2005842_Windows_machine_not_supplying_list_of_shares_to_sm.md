---
title: "Windows machine not supplying list of shares to smb"
date: 2012-06-18
forum: Networking &amp; Wireless
---

### Post by mainmeister on 2012-06-18
I cannot see my windows shares from my ubuntu machine but I can see my ubuntu from my windows machines.

```
mainmeister@AcerLaptop:~$ smbtree
Enter mainmeister's password: 
MAINMEISTER
	\\DESKTOP        		Dell
	\\ACERLAPTOP     		AcerLaptop
		\\ACERLAPTOP\Public         	
		\\ACERLAPTOP\print$         	Printer Drivers
		\\ACERLAPTOP\myshare        	description
		\\ACERLAPTOP\IPC$           	IPC Service (AcerLaptop)

```

The DELL is the windows machine and the ACERLAPTOP is the ubuntu machine. As you can see they are both a member of the MAINMEISTER group. I've created the same two users on windows and ubuntu with the same passwords.

My question is, where do I go from here. Why is my windows machine not providing the list of shares?

---

