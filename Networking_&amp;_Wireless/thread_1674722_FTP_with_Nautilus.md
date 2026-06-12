---
title: "FTP with Nautilus"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by theone964 on 2011-01-24
I recently bought a Netgear N600 (WNDR3400) it has a USB port on it. I hooked up a 1TB External HDD to it and it places nice on my LAN but remotely its been giving me grief. It uses Netgear's Readyshare to share any USB Drive connected to it

Just for clarification when i say <externalipaddress> i mean the one that isnt  192.168.x.x

While on LAN this works
Nautilus=smb://<externalipaddress> 
or Places>Network>Windows Network>Workgroup>Readyshare
Firefox= ftp://<externalipaddress>
             ftp://<externalipaddress>/shares
             http://<externalipaddress>/shares
             smb://<externalipaddress> if i have no password set

Now when i got to work and access it remotely
Nautilus= smb wont work and connect to server wont work
Firefox= Everything works fine as above.

I really want to use Nautilus to access my share because by clicking on a .avi or .flv or .iso and using open with VLC Media Player, the file opens up straight away and begins playing/streaming. If I use firefox (even though I set VLC as the default now) to open the file via ftp, http, or smb it downloads first and then plays it. I dont want to wait for a 4GB ISO to download i just wanna watch it when i click on it.

The things that are giving me grief or making me wonder are that the smb:// works when im on the same network as the 1TB but not when i'm remote, even though i use an external ip address to connect to the smb share. And the other is that no matter how i try to connect to the external using Places>Connect to Server> FTP (with login) it just keeps giving an error message.

---

### Post by penquin on 2011-05-10
I don't know if this is what you are looking for but. I  went to connect to server. It popped up a window then I clicked on server type I choose windows share. I then used server number from the routerlogin (XX.XXX.XX.XXX/share but remove the word share). Don't forget bookmark it so you can do it again.

---

