---
title: "PC Not showing up on LAN"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by mjc7373 on 2010-06-12
Hi all, I need help with my home network. I have a desktop PC running Ubuntu 10.4 connected via network cable to my DSL Modem, and a Windows XP laptop I connect via wireless. 

I decided to set up Samba shares so my laptop could access files on the Ubuntu PC. I edited the smb.conf file with the (as far as I can tell) proper parameters for sharing. I added the Samba users and added the shared directories. When I looked at "My Network Places" I could not see any shares, nor any trace of my Ubuntu PC. Since my desktop is dual-boot, I decided to boot into Windows 7 to see if I could share it's folders, but that also failed. 

That was when I noticed something else odd. When I went to my router's configuration page, where all PCs connected to the LAN should have been listed, but only my laptop was there. My desktop PC was not showing up at all, and this was true weather I was booted into Ubuntu or Windows. 

Wondering if the modem was somehow to blame, I decided to use Putty to try to access my Ubuntu PC from the laptop via ssh, and it worked! 
So ssh, yes... Samba, Windows file sharing and detection by the DSL modem, no. Any ideas? Thanks so much!


Here are my relevant smb.conf enteries:

   workgroup = WORKGROUP
   server string = Samba Server
   netbios name = SERVER-DESKTOP

;   comment = Home Directories
    browseable = yes
    writable = yes

[Music]
browseable = yes
path = /home/me/Music
guest = ok

---

