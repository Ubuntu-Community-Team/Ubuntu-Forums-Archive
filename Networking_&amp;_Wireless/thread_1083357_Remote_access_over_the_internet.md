---
title: "Remote access over the internet"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by eekfonky on 2009-02-28
Is it possible to access another ubuntu machine over the internet? With Windows XP you can use MSN Messenger and it's simple. I am in Australia and need to access a colleagues computer in France. I cannot ask him to do complicated port forwarding. Is there a simple way under ubuntu? surely it can't be that hard...is it?

---

### Post by cybergalvez on 2009-02-28
> **eekfonky said:**
> Is it possible to access another ubuntu machine over the internet? With Windows XP you can use MSN Messenger and it's simple. I am in Australia and need to access a colleagues computer in France. I cannot ask him to do complicated port forwarding. Is there a simple way under ubuntu? surely it can't be that hard...is it?

yes its simple, but what exactly do you want to do? chat? pidgin will connect to any of the chat servers, remote control, a little more difficult and depends on what the computers are running, linux, you can use NX, or vnc, is he is running windows he can use the built in RDP server (Its been a long time but I think its under system properties>remote) or he can install vnc, if he's on a mac he can use vnc.

---

### Post by eekfonky on 2009-03-01
ubuntu to ubuntu over the internet. Can it be done easily without port forwarding etc. is there an application? Please help

---

### Post by cybergalvez on 2009-03-03
the simplist way would be to just use the built-in remote desktop (vnc).  On his end he will have to turn on system>Preferences>Remote Desktop  The dialogs are pretty strieght forward, however port 5900 will have to be reachable from his computer.  If he knows of a prot that will already forward to his computer then you can change the prot that remote desktop uses via the advanced tab.  Sorry I'm not sure how you would tunnel this through any of the P2P programs that get around routers and the such.

Take a look at:
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
[https://launchpad.net/remote-help-assistant](https://launchpad.net/remote-help-assistant)

---

### Post by eekfonky on 2009-03-05
Thanks, but is there anything where I can simply login to my friends ubuntu machine?

---

### Post by cybergalvez on 2009-03-06
> **eekfonky said:**
> Thanks, but is there anything where I can simply login to my friends ubuntu machine?

the best I have found, if you just want to log into his machine, with your own account, ie not remote control, but rather you get your own desktop is to have him install NX, thats what I use to admin alot of the machines I have to deal with.  They have deb packages and are very simple to install.  

[http://www.nomachine.com/](http://www.nomachine.com/)

if its the later remote control that your after then vnc is what you want like I mentioned in a post above

---

### Post by eekfonky on 2009-03-06
I only need to admin the machine, so I can log in as my friend and do what's necessay then Nomachine sounds like something I can use. I'll try it next week when i get the chance.

I'kk let you know how I get on, thank you

---

### Post by cybergalvez on 2009-03-08
sounds good, thats exactly what I user nomahcine for on my kids machine, I log in and do that admin stuff, apply patches and stuff like that, she does not have admin right.  So I can log in regardless if she is on or not

---

### Post by eekfonky on 2009-03-09
Ok it gives me 3 files to download.

Do I need to download it as well as my colleague in France?
Which file(s) do I download?

---

### Post by cybergalvez on 2009-03-10
> **eekfonky said:**
> Ok it gives me 3 files to download.

Do I need to download it as well as my colleague in France?
Which file(s) do I download?

On both machines you need to have sshd installed and running,
on your machine you need the client,
on your friends he needs all three, client, node and server

---

### Post by eekfonky on 2009-03-11
Can you point me to an idiots guide to set it all up, I'm new to this sort of thing? Also how do I uninstall if I need to?

---

### Post by bgiannes on 2009-03-11
take a look at [http://www.webmin.com/](http://www.webmin.com/)

but this tool will give the admin total control over the remote server.

the other option is using SSH, and forward the ports you need.  The XP end would use a program called putty.  Or a program called SCP which is a file manager program that uses the SSH tunnel

howto's

ssh server on the ubuntu server and a bit of Putty SCP
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by eekfonky on 2009-03-12
Ok trying to use Google's Gitso. I have all the dependencies installed, as does my friend in France. However when I follow the instructions it just sits looking at me. Can anyone point me to a forum to help? Surely a simple remote over the internet can't be that hard for the mighty ubuntu?

---

### Post by cybergalvez on 2009-03-15
> **eekfonky said:**
> Ok trying to use Google's Gitso. I have all the dependencies installed, as does my friend in France. However when I follow the instructions it just sits looking at me. Can anyone point me to a forum to help? Surely a simple remote over the internet can't be that hard for the mighty ubuntu?

its not as long as you can actually see the other machine.

1) make sure you can ssh to his machine
```
ssh user@machinenameURL_or_ip
```

2) if you can't then the host computer either does not have sshd running or he is behind a firewall and the ssh port is not being forwarded to his computer properly.  This has to be fixed first.  if you can ssh then NX should just connect without issue

---

