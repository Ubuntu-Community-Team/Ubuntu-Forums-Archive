---
title: "File sharing between two Ubuntu 9.1 computers"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by jwager0408 on 2010-03-10
I have two desktop computers on the same home network and I am unable to share files between the two.  Both have access to the network.  One is able to file and printer share using SAMBA and a windows 7 laptop.  The other machine is unable to either do file sharing via Samba or SSL file sharing between the two Ubuntu machines.  Trouble shooting help would be great, thanks.

John

---

### Post by sedawk on 2010-03-10
Which of your machines is the file server and which is the print server?

On Ubuntu there is a command line tool "smbclient" that is similar to ftp and can be used to debug the problem.

On windows there is something like "net" and it can be used with something like "net show" to show samba servers or shares or printers on other machines (the servers).

---

### Post by jwager0408 on 2010-03-10
sedawk, I failed to qualify that the two desktops are running Ubuntu 9.10 and I would like to have both of them acting as servers to share both files and printers and I would like both to be able to access files and printers on the other Ubuntu based machine.  Accessing the Windows 7 laptop is gravy as my long term goal is to have all systems on the home network running Ubuntu.  Thanks for the suggestion of "smbclient", I will see if it can help.

---

### Post by Iowan on 2010-03-10
> **jwager0408 said:**
> The other machine is unable to either do file sharing via Samba or [COLOR="Red"]SSL[/COLOR] file sharing between the two Ubuntu machines. SSH? I presume you installed samba's server package and the SSH server on both machines?

---

### Post by jwager0408 on 2010-03-10
SSH and Samba server is installed on both machines

---

### Post by jwager0408 on 2010-03-12
All, problem solved.  Reviewed the config files and made the required changes.  Now onto the SAMBA settings.

---

### Post by Iowan on 2010-03-12
GOOD luck ! :p

---

### Post by aboud on 2010-03-15
> **jwager0408 said:**
> All, problem solved.  Reviewed the config files and made the required changes.  Now onto the SAMBA settings.

what config file, how did you access the file afterward ?

file sharing between Ubuntus and xp worked with me but now they just can't see each other, ubuntu is pinging ubuntu and windows but sharing is not working. usully when facing such problem i restared samba but now this not helping .

---

