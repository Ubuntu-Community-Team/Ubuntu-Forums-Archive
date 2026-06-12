---
title: "networking wondering if it is imposable"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by klein de usa on 2008-12-08
hi
i have a home network set up, i use hughes.net for internet and the hughes box acts as an dhcp server. everything works fine i even have two computers networked wirelessly , i would like to share folders over the same network is it possible?

i have installed samba and gone through the setup and i can see the other computers on the network, even the wireless computers. 

i have shared one folder on two of the computers but when i click on the icon for the computer it thinks about it and then just leaves me with a blank page.

what am i doing wrong, or is it i can't share files across the same network as my internet?

---

### Post by crucial123 on 2008-12-08
I am having the same problem. 
My setup is a Vista box from which I can see (and access)shares from both a Ubuntu Intrepid desktop box and a Ubuntu Intrepid laptop...
I can see the network and shares from one ubuntu machine to the other but get an empty folder when I try to access anything on the vista box from either ubuntu machine.

I have gone through these instuctions:" [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently) "   Paying particular attention to the "cifs, user perms" part of the instructions as I am under the impression that smbfs doesn't work with vista.

a one way network is sort of like living on a one way dead end street. help.

---

### Post by jmoorse on 2008-12-08
Vista uses a different security method by default in communication with network filesystems.

Please give the following instructions a shot on the Vista box:

1. Start > Run > `secpol.msc` (this will open local security policy editor)
2. Go to Local Policies > Security options
3. Double click on "Network Security: LAN Manager authentication level"
4. Change to "LM and NTLM – use NTLMV2 session security if negotiated"

Reboot and give it a shot!

---

