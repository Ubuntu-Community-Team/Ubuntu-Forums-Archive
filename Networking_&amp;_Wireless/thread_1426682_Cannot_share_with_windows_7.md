---
title: "Cannot share with windows 7"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by dr83 on 2010-03-10
Hello every one

i have recently installed ubuntu on my old pc

i wanted to share my PC with my laptop running windows 7
i have a wireless connection and the file sharing in windows is managed by network magic

but till now i m not able to share folder with windows 7
my Ubuntu pc can see the laptop folder but is not able to mount it
and my windows 7 cannot detect ubuntu at all

i recently saw a post about windows live id assistant(and to uninstall it) but i think that its not installed on my laptop can any one help please !!!!!!????

---

### Post by johnson.d on 2010-03-11
1) You can try mounting the Windows share in Ubuntu by entering the following command:

$ sudo mount -t cifs //<ip-address of Windows machine>/<share-name>/ /<mount-point>/ -o user=<user-id>

The output of the command can be used to troubleshoot further.

2) As your Windows machine doesn't detect you Ubuntu machine, You can directly enter the ip-address of the Ubuntu machine in the address tab of the Windows explorer as the following:

\\<ip-address of the Ubuntu machine>

---

### Post by dmizer on 2010-03-11
Please see the 6th link in my sig. There is a section specifically related to Windows 7.

---

### Post by rik666 on 2010-03-11
I had this problem sharing from Ubuntu to vista. you should be able to create a UNC path either way as long as you're sharing out the folders you want to access. I would advise checking your share settings on the win7 machine, once you know they're alright try mounting the win7 drive. I solved the error once the relevant access was granted through sharing on the windows machine.

---

