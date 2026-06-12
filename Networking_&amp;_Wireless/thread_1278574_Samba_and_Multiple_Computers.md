---
title: "Samba and Multiple Computers"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by leveliv on 2009-09-29
I am just looking for a quick solution to:

Getting Samba to share the same folder to more than one computer. I have one folder on my linux box for Music and Video etc. Running 9.04 

It is able to be seen on one computer with no problems at all, It shares the folder /Media/Samba/ plus a printer to my Windows 7 Computer. 

However I have a Windows XP computer that I would like to see it being shared to. The computer shows up in My Network Places but the folder doesn't.  

The way I have the win 7 computer set up is I went into Network Connections and changted the WINS setting to the ip of the server then enabled Netbios over TC/IP. then it just worked after that. 



The Windows XP Computer is on the same Workgroup and also has the same TC/IP Settings on it's LAN connection. 


Would I be able to Add a new Samba user then just connect to the Server with those credentials?

---

### Post by mattkoehn on 2009-09-29
Are you getting the popup in XP that asks for credentials?

Does anything change if you browse directly to the share by going to explorer or the run box and putting in \\computername\sharename ?

---

