---
title: "Home Network woes"
date: 2005-01-15
forum: Networking &amp; Wireless
---

### Post by philip41 on 2005-01-15
Just setup today my 2nd pc,  i can now access my windows xp pro pc from Ubuntu, but when i want to access the Ubuntu pc from windows i cannot.
Ubuntu shows up on the windows pc but when i click to access it a box appears asking me for a user name and password.
I enter them both( user & password for Ubuntu ) click ok and the box just returns.

I guess i am doing some thing wrong but what.

Any help much appreciated.

---

### Post by az on 2005-01-15
Ubuntu comes with all ports closed by default.  This means that there is nothing listening.  This is for safety reasons.  If you install something that listens on a port, you are presumed to know what you are doing.

You need to install the samba package.  You will then be able to access your Ubuntu system from windows.

"You do not need the 'samba' package installed in order to print to Windows
printers, or access file shares on Windows systems.  The only reason to install
it is to provide those services FROM Ubuntu TO Windows systems."

---

### Post by HankB on 2005-01-16
I just went through the same thing. You'll need samba installed to begin with and then you have to configure it. (I suppose you're at least part way along with that if Windows sees your Ubuntu host on network.) On a lot of things I can just go through the config file and get things set and be working, but SAMBA took me a bit more.

I recall that the last thing I did to get it working (printer and file sharing from Ubuntu to a Win2000 client) was to enable users and add their SAMBA passwords. I don't think that SAMBA can authenticate against the Linux password database because Linux and Windows use different ways to encrypt passwords. (try "smbpasswd -e <user>")

I saw a post about an Ubuntu SAMBA information page and you can also install samba-doc for more info.

HTH,
hank

---

### Post by philip41 on 2005-01-16
[QUOTE=azz]Ubuntu comes with all ports closed by default.  This means that there is nothing listening.  This is for safety reasons.  If you install something that listens on a port, you are presumed to know what you are doing.

You need to install the samba package.  You will then be able to access your Ubuntu system from windows.[/quote]

I have Samba installed ( maybe i should have said that) but still no joy, How do i open ports.

> 
"You do not need the 'samba' package installed in order to print to Windows
printers, or access file shares on Windows systems.  The only reason to install
it is to provide those services FROM Ubuntu TO Windows systems."

I see thanks.

---

### Post by philip41 on 2005-01-16
[QUOTE=HankB]I just went through the same thing. You'll need samba installed to begin with and then you have to configure it. (I suppose you're at least part way along with that if Windows sees your Ubuntu host on network.) On a lot of things I can just go through the config file and get things set and be working, but SAMBA took me a bit more.

I recall that the last thing I did to get it working (printer and file sharing from Ubuntu to a Win2000 client) was to enable users and add their SAMBA passwords. I don't think that SAMBA can authenticate against the Linux password database because Linux and Windows use different ways to encrypt passwords. (try "smbpasswd -e <user>")

I saw a post about an Ubuntu SAMBA information page and you can also install samba-doc for more info.

HTH,
hank[/QUOTE]

Thanks Hank, looking into that now.

---

### Post by philip41 on 2005-01-16
A happy ending, i can now move my files to and fro.
I just had to edit the SMB.conf .

---

### Post by jetpeach on 2005-08-11
is their a way to edit this or configure samba using a GUI?  I really don't like having to find, edit random text files, and then test (to make sure I configured it correctly) something just to configure it.  I know, maybe I should learn to expect this from linux... but a simple application that runs in Gnome that allows easy configuration of the Samba settings would be much nicer for me (and millions of other Windows converts, I think too.)
Any program I should get from the repositories?
Thanks,
jet

---

### Post by Dave In Sidney on 2005-08-13
SWAT is the traditional GUI for SAMBA configuration. Not sure if it's installed by default on your system, but if not, you should be able to get it from SAMBA.

---

### Post by Buffalo Soldier on 2005-08-13
[QUOTE=jetpeach]is their a way to edit this or configure samba using a GUI?  I really don't like having to find, edit random text files, and then test (to make sure I configured it correctly) something just to configure it.  I know, maybe I should learn to expect this from linux... but a simple application that runs in Gnome that allows easy configuration of the Samba settings would be much nicer for me (and millions of other Windows converts, I think too.)
Any program I should get from the repositories?
Thanks,
jet[/QUOTE]Using Hoary. I'm not sure if it's the same in Warthy. System -> Administration -> Shared Folders.

---

