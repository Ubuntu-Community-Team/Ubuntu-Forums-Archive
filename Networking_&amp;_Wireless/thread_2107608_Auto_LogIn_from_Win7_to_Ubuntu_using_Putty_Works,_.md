---
title: "Auto LogIn from Win7 to Ubuntu using Putty Works, but how do I add commands?"
date: 2013-01-22
forum: Networking &amp; Wireless
---

### Post by Carlo Jongen on 2013-01-22
Hi,
 
I've Installed C:\putty.exe
I made a C:\Login.bat file in Win7 containing the next text:
```
putty -ssh [EMAIL="client_name@client_IP"]client_name@client_IP[/EMAIL] -pw client_password
```
 
When I run the Login.bat it opens up a Putty window and I'm connected to the target computer running Ubuntu. In this Putty window I can execute some commands. For example:
```
sudo shutdown now
```
After entering the password the Target PC shutsdown.
 
My question is, how can I add this command in the *.bat file so it can automate this process? 
 
 
--------------------------------------------------------------------------------------------------
Freelance 3D animation at [www.c3d.be]("http://www.c3d.be/")

---

### Post by mlentink on 2013-01-22
You can't.

Your batchfile is a list of commands executed in windows. It starts up a terminal in Ubuntu and passes your login-credentials to the ubuntu login program. Ubuntu knows nothing about windows, or whatever commands were entered there, it only knows about commands you enter into Ubuntu. 
You could, however write up a small 'batch-file' (which we call a 'shell-script') to do what you want to shut down ubuntu. But then again, Windows knows nothing about the commands you give Ubuntu.

Hope this clarifies this a bit for you.

---

### Post by Carlo Jongen on 2013-01-22
Thanks... But I'm new at Ubuntu and I'm not much of a script writer... So forgive my ignorance in my next question:
Do I need a script inside Ubuntu to run these commands? Or can a script in Windows pass the commands trought to putty and then excecute them? This is not clear to me...

---

### Post by Cheesemill on 2013-01-22
You can use plink (part of putty) to run remote commands.

```
plink -ssh client_name@client_IP -pw client_password sudo shutdown now -r
```

You probably want to configure sudo on the target machine so that you aren't prompted for a password for the shutdown command. This is done by editing the /etc/sudoers file using the visudo command...

[https://help.ubuntu.com/community/Sudoers#Shutting_Down_From_The_Console_Without_A_Password](https://help.ubuntu.com/community/Sudoers#Shutting_Down_From_The_Console_Without_A_Password)

---

