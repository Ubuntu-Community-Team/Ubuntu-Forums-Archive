---
title: "networking passwords"
date: 2011-07-22
forum: Networking &amp; Wireless
---

### Post by cmdace on 2011-07-22
I have a server running ubuntu 10.04.  Running it because everything after that sucks.
I have it running sick beard just fine with a back up program.  My problem is that it is
head less with no keyboard or mouse.  When I boot it up it does everything just fine.  
If I need to remote into the desktop or access any shared files, I have to attach a
keyboard and monitor and type in the password.  Then I can get into remote desktop and 
the file from anouther computer.  The other computer accessing it is an ubuntu machine running
xbmc and a couple of windows machines, both vista and win7.
Is there any way to get rid of the password log in on the machine.  Its anouying to have to 
jump on it to get things working everytime I boot it up.
Thanks

---

### Post by kaspar_silas on 2011-07-22
Eh? 

So you are saying you have a server that has computers you can only access from it. But it's a pain physically going to the server, right?

Firstly is the server actually connected to an external network. If a computer isn't connected to a wider network there is normally a good reason. 

Assuming this is not the case if you have the server password you can just ssh or vnc onto the server or install a internet based connection (try googling teamviewer).

---

### Post by spiky001 on 2011-07-22
Is it something to do with the screen saver if so just disable screen saver, although as mentioned in previous post you should be able to ssh or use vnc. With vnc there is an option to set so you can configure network to accept connections without the need for passord

---

### Post by cmdace on 2011-07-22
I would absolutly love to vnc into the pc, but I have to got to the server and type in the password.  I do have team viewer but I should not have to type any password in just to view files on it. SSH does not  unlock the server, and no screen saver on it.  Yes it is connected to a network and works great.  The only problem I have is the fact that to get into the server, you have to unlock it by typing a password into the server it self.

---

### Post by doas777 on 2011-07-22
is this a desktop server or a regular gui-less server install?

what app is asking you for a password that you must supply?

I run a headless desktop server, and I use FreeNX for remote access. it does not require you to have logged into a desktop the way ubuntu remote desktop does, so you can remotely log into a desktop session and start things with "startup applications".

you should attempt to have everything you need client access to to run as a service, that way you don't have to login interactively before stuff becomes accessible.

the core question is what kinds of services are you running and how are you launching them?

---

### Post by capscrew on 2011-07-22
> **cmdace said:**
> I have a server running ubuntu 10.04.  Running it because everything after that sucks.
I have it running sick beard just fine with a back up program.  My problem is that it is
head less with no keyboard or mouse.  When I boot it up it does everything just fine.  
If I need to remote into the desktop or access any shared files, I have to attach a
keyboard and monitor and type in the password.  Then I can get into remote desktop and 
the file from anouther computer.  The other computer accessing it is an ubuntu machine running
xbmc and a couple of windows machines, both vista and win7.
Is there any way to get rid of the password log in on the machine.  Its anouying to have to 
jump on it to get things working everytime I boot it up.
Thanks


Do you mean you have to log in to the server before you can ssh or vnc to it.  Without logging in can you ping this server?  Maybe the interface is not up.

---

### Post by LemursDontExist on 2011-07-22
A little more detail would be really helpful here for figuring out what's going on.  If the VNC server were running, then it shouldn't be necessary to enter any passwords physically on the machine to log in - so, I'm guessing the problem is that the VNC server isn't running.

If that's the case, there are a few possible solutions.  The simplest would simply be to enable [auto-login]("https://help.ubuntu.com/community/AutoLogin") on the server.

A more elegant solution would be to configure the VNC server to [run at boot time]("http://www.abdevelopment.ca/blog/start-vnc-server-ubuntu-boot").

Note that both of these approaches are potentially problematic from a security point of view.  I would strongly encourage you to [route your connections through ssh]("https://help.ubuntu.com/community/VNC#SSH port-forwarding") for security, and prohibit any non local connections.

---

### Post by doas777 on 2011-07-22
> **LemursDontExist said:**
> 
Note that both of these approaches are potentially problematic from a security point of view.  I would strongly encourage you to [route your connections through ssh]("https://help.ubuntu.com/community/VNC#SSH%20port-forwarding") for security, and prohibit any non local connections.

Agreed. thats why I always recommend [FreeNX/NeatX]("https://help.ubuntu.com/community/FreeNX"). its ssh based, fast, and rather reliable. clients for most major OSes.

---

### Post by cmdace on 2011-07-22
Sorry this is really starting to get to me.
To answer your questions this is a regular server with gui installed, hence the reason i can remote into it.    No apps are asking for passwords on the client pc.  When I first boot up the server, then go to any client pc, if I attemt to open a file. On the client pc  thru network to a file that is on the server, I cannot open the file.  If I then go to the server a password box pops up and asks for a password.  Not a log in, and not a wake from screen saver or power saver mode.  The same happens for vnc.  Im using remote desktop on the server and vnc to access it.  I figured the built in remote desktop would work fine without installing tight vnc or freeNX.   If i fire up vnc it asks for the ip address, and this opens a password box on the server i must type in a password for remote desktop to work.    I have tried to disable the pass word but then I cant get access at all.

The server is auto log on, and yes I can ping it and I can access any web based applications just fine.   Untill I try to access a file.

---

### Post by doas777 on 2011-07-22
ok, that helps a lot.
it is likely either somthing in Startup Applications that uses gksu, or its the keyring password.

What does the password box say specifically? somthing about a keyring password?

---

### Post by kaspar_silas on 2011-07-23
Just a quick check but I take it you have checked you have the correct permissions on the files you are trying to view?

---

