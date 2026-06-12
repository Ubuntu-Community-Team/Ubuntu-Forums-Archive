---
title: "remote folder/file access please help"
date: 2013-03-14
forum: Networking &amp; Wireless
---

### Post by keefer2k4 on 2013-03-14
Hello, I have a windows xp computer that i use to store pdf files. I use it as a network drive and I do all my daily work on a windows 7 machine and save to the windows xp computer. They are connected through a linksys wrt120n router. I have dsl service. I also have a dell d430 with ubuntu 12.04 on it. I want to be able to access and edit those files when I am on the dell d430 on the road. I would love to make this simple and possibly free. I would love if it just acted as a network folder I can access it on the laptop and then save the file when I am done to the network drive on the windows xp machine. The xp machine is constantly connected to the internet.

Please any help would be greatly appreciated

Thank you, Keith

---

### Post by matt_symes on 2013-03-16
Hi

There are a number of options you can use.

You can set up a VPN.

Install an ssh server on the windows box and use sshfs on the ubuntu box.

You can use a vnc (with ssh !!) client on Ubuntu and server on the XP box. This will give you remote desktop.

You could SCP, SFTP or rsync the file from the xp box, make your changes and copy it back.

What ever you do, make sure your setup is secure ! You will need to open some ports on your router as well and this will make the xp box vulnerable to attacks on the open port.

Do you want a GUI or are you happy with CLI ?

It'll be interesting to see what others think as well.

Kind regards

---

### Post by kevdog on 2013-03-16
I just read your setup -- your server is your windows machine and your client is your windows /ubuntu machine -- it would be easier if it were the other way around.  Command line methods are probably your best alternative.  For my individual windows machine I usually use the cygwin/openssh implementation since its setup the same way as on a linux machine.  There are other alternatives however to cygwin/openssh they may be a little bit easier to setup.  

I've recently become very enamored to mounting remote ssh directories using sshfs.  There is a remote sshfs client for windows known as DokanFFS that is able to remotely mount linux openssh shares, however your situation is the exact opposite.  You want to mount ssh shares (served on windows) to your linux/windows box.  Short of mounting the shares (which just gives you the ability to drop and drag files from a file manager back and forth), you could just use utilities which are mostly command line based such as sftp,rsync,scp (which all use ssh as a backend) as mentioned above.  WinSCP is a great windows sftp client that requires putty as a backend for managing the authentication process.  

Thinking out load I'm not sure of other remote file system solutions for your situation -- cifs (samba), nfs won't work.  Reverse ssh tunneling isn't going to help.  ssfs would work in the reverse situation.  

I'm not sure if installing lets say Ubuntu or other distro in a VM environment would give you access to your files either.

---

