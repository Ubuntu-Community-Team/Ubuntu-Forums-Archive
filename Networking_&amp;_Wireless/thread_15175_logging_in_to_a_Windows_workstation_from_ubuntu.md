---
title: "logging in to a Windows workstation from ubuntu"
date: 2005-02-12
forum: Networking &amp; Wireless
---

### Post by sharkzf6 on 2005-02-12
OK, I'm no networking guru; I think I'm one of those people who know enough about networking to be dangerous. Here's my situation. I have a home network, which uses a D-Link router as a DHCP server and access point to my cable modem (Internet gateway). When I try to access a shared folder on a Windows workstation from an ubuntu workstation or vise versa, I get prompted for a user name and password. I figure it's looking for the same user name and password I use to login to my various workstations so I type that in. It rejects the data and prefixes the user name with the name of the computer. I leave it alone, retype the password and, of course, it still rejects it. So what am I doing wrong? I don’t have any trouble at all going from Windows workstation to Windows workstation even if it asks for a username and password. It accepts the input and goes directly to the shared folder on whatever workstation I’m accessing. Same thing if I go from Linux workstation to Linux workstation, it accepts the input and goes to the shared folder. Thanks for any help.

---

### Post by hndrcks on 2005-02-12
OK first make sure:

1. In network config on Linux PC that windows networking is enabled and the workgroup is set to the same as the XP PC.

2. Open network place and browse, make sure you can see XP PC.

If you have gotten that far, open network place again

type CTRL-L

in box, type in 

smb://windowscomputername/sharename 

(insert computer / share name as required)

That should get you to a login pass domain prompt. Enter the windows login info.

Currently gnome has 'issues' with browsing certain types of windows network shares; but specifying the share directly should work.

---

### Post by sharkzf6 on 2005-02-12
[QUOTE=hndrcks]OK first make sure:

1. In network config on Linux PC that windows networking is enabled and the workgroup is set to the same as the XP PC.

2. Open network place and browse, make sure you can see XP PC.

If you have gotten that far, open network place again

type CTRL-L

in box, type in 

smb://windowscomputername/sharename 

(insert computer / share name as required)

That should get you to a login pass domain prompt. Enter the windows login info.

Currently gnome has 'issues' with browsing certain types of windows network shares; but specifying the share directly should work.[/QUOTE]
 Thanks for the info. That worked but actually, all I have to do is not type in a username and password, just say OK at that dialogue box and it goes to the folder....go figure....

---

### Post by sharkzf6 on 2005-02-12
all I have to do now is figure out how to mark folders as shared on my Warty distro, my Hoary has a menu item but Warty does not...

---

### Post by sharkzf6 on 2005-02-12
Ahh crap, I still have a problem. I can get from linux to windows but not from windows to linux, still asks for a user name and password and prefixes with computer name which keeps it from connecting...damn!

---

### Post by JayCnrs on 2005-02-12
[QUOTE=sharkzf6]Ahh crap, I still have a problem. I can get from linux to windows but not from windows to linux, still asks for a user name and password and prefixes with computer name which keeps it from connecting...damn![/QUOTE]
 Go to Computer-->System Configuration-->Networking, then click the General tab, put a check in Windows networking and put the workgroup. If you can't put a check in Windows networking you will need to install Samba through Synaptic.

Now you will want to go to a terminal type **sudo smbpasswd (then put in your username), **give yourself a password, the password and username should match a user on your Ubuntu system and a user on Windows, to make it easy set the password to your windows password, if you don't have a Windows password then type at a terminal **sudo smbpasswd -n (username)** Then you need to go to **/etc/samba** then use a text editor to add this line right below Workgroup=(windows workgroup), **null passwords = yes** in smb.conf then save the file.

HTH :)

---

### Post by sharkzf6 on 2005-02-12
[QUOTE=JayCnrs]Go to Computer-->System Configuration-->Networking, then click the General tab, put a check in Windows networking and put the workgroup. If you can't put a check in Windows networking you will need to install Samba through Synaptic.

Now you will want to go to a terminal type **sudo smbpasswd (then put in your username), **give yourself a password, the password and username should match a user on your Ubuntu system and a user on Windows, to make it easy set the password to your windows password, if you don't have a Windows password then type at a terminal **sudo smbpasswd -n (username)** Then you need to go to **/etc/samba** then use a text editor to add this line right below Workgroup=(windows workgroup), **null passwords = yes** in smb.conf then save the file.

HTH :)[/QUOTE]
Cool, thanks. What about setting folders to be shared on Warty? Thanks again.

---

### Post by shuflie on 2005-02-12
A quick google for SMB share came up with this on the first page.

[http://linux.ucla.edu/pipermail/linux/2000-May/003362.html](http://linux.ucla.edu/pipermail/linux/2000-May/003362.html)

EDIT: just to make it clearer, "If you installed SMB support on your linux box then all there is to do is edit /etc/smb.conf.  The file has many comments explaining different settings, but you really should just read the documentation. It can be found under
/usr/doc/samba-*/"

---

### Post by sharkzf6 on 2005-02-13
[QUOTE=shuflie]A quick google for SMB share came up with this on the first page.

[http://linux.ucla.edu/pipermail/linux/2000-May/003362.html](http://linux.ucla.edu/pipermail/linux/2000-May/003362.html)

EDIT: just to make it clearer, "If you installed SMB support on your linux box then all there is to do is edit /etc/smb.conf.  The file has many comments explaining different settings, but you really should just read the documentation. It can be found under
/usr/doc/samba-*/"[/QUOTE]
Thanks again. :D

---

