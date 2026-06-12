---
title: "Giving acces to start openVPN to other users than admin and sudo use"
date: 2012-07-06
forum: Networking &amp; Wireless
---

### Post by sources on 2012-07-06
Now if i want to log into my openVPN or install it i have to use "sudo /etc/init.d/openpvpn start"

But if i do this with another user than the adminuser i installed openVPN with, it only says i need root previligies and that this will be reported, blablabla...

Is this(I read it in a sticky topic) mayb a "sollusion to the problem:

**"Graphical sudo**

 You should **never** use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on *Kubuntu*) to run such programs.  gksudo  sets HOME=~root, and copies .Xauthority to a tmp directory.  This  prevents files in your home directory becoming owned by Root.  (AFAICT,  this is all that's special about the environment of the started process  with gksudo vs. sudo). 
Examples: 
gksudo gedit /etc/fstabor 
kdesudo kate /etc/X11/xorg.conf
[LIST]
[*]To run the graphical configuration utilities, simply launch the application via the Administration menu.
[*]gksudo and kdesudo simply link to the commands gksu and kdesu [SIZE=3]**"**[/SIZE]
[/LIST]




Is this maybe a way to go to fix this problem or doesnt that help at all? And if you wonder i installed vpn with sudo apt-get install openvpn, and moved the files etc..


and started it with sudo /etc/init.d/openvpn and then the password, and auth. key..


But after a while i wanted more security and opened a new user without admin rights, but now i cant use openvpn.. (And after ubuntu 10.04 i havent been able to get openVPN to work with network manager like before.. (Before i could install it, enable/disable it like a regular network connection, now it wont appear at all.. Why is that?


Thanks for your answers and time! :)

---

### Post by Kirk Schnable on 2012-07-11
Try this. (replace "username" with your username)

Use "visudo" to edit your sudoers file.  Add this line to give your non-admin user the privileges to run OpenVPN as root (and nothing else).

> *username* ALL= NOPASSWD: /usr/sbin/openvpn

I think this is what you want.  Try it, and if not, let us know...

Kirk

---

### Post by SeijiSensei on 2012-07-11
Usually OpenVPN starts at boot via the script /etc/init.d/openvpn.  Is there a reason why this won't work for you?

---

