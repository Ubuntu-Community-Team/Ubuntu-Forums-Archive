---
title: "VNC port issues"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by Tsquad on 2010-01-09
Hello, im having some problems trying to have multipul pc's at my house being VNC servers. I have one thats running ubuntu 8.10 and it has its own ip and its own port of 5900, the usual vnc port number. That is my server. Then i have my main pc that has its own ip as well and its own port number of 5901. After some research i found that the port numbers start at 5900 and go up by one for vnc. So my main issue is how do i tell my vnc client to look at a port other than the standard 5900?

Iv been googling trying to figure out how to configure vnc to look to a different port but i have not found anything helpful.

---

### Post by changingstate on 2010-01-09
When using the vinagre VNC client aka 'Remote Desktop Viewer', the box for selecting which host to connect to accepts an argument in the form <host>:<port>

So, on my network, I've got a machine called fighter running a VNC server on port 5901, I just pop in : fighter:5901 , then click connect.

---

### Post by Tsquad on 2010-01-11
ok, so i just put my ip::5901 and the connection failed. I know thats the right way but im guessing i have something else wrong. the funny thing is that when i put it back on port 5900 and i dont type in the ::5900 part, it connects no problem. this is all for accessing these computers from outside my network like from work or a friends house.

---

### Post by changingstate on 2010-01-11
Have a read through this example.

I'm using tightvncserver ( See : [https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers) ) and vinagre ( See : [https://help.ubuntu.com/community/VNC/Clients](https://help.ubuntu.com/community/VNC/Clients) ). 

To start everything up, I ssh into the server ( fighter ). First, su up to root, with :

```
sudo -i
```Then I execute tightvncserver with :

```
tightvncserver -nolisten tcp :1
```[FONT=Arial]This [/FONT]starts the server listening for connections on port 5901. If I wanted a VNC server on port 5902, I'd execute :

```
tightvncserver -nolisten tcp :1 -rfbport 5902
```[FONT=Verdana]
[/FONT] [FONT=Verdana]Lets assume you want the do the second. With the server configured, I then start vinagre on the client, click connect and type into the dialog box :
[/FONT]
```
fighter:5902
```NOTE THE SINGLE COLON. It requests my password, I go in and do my funky thing. After I'm bored of asking for shoes on heads, I decide to shut down the VNC server on fighter, by disconnecting vinagre, sshing back into fighter and executing ( as root ) :

```
tightvncserver -kill :1
```[FONT=Verdana]
Then I log out of fighter. See how that example works, for you.[/FONT]

---

### Post by pricetech on 2010-01-11
BEFORE you open ports in your router and expose your internal network to the outside world, look at the security issues involved with VNC of any flavor.  I don't have any links to post, but if you'll search for VNC, SSH, and Security, you should find a lot of information.

Unless you're "married" to the idea of using VNC, I'd recommend NX from nomachine.com.  Install the client, node, server for Linux and the client for winders.  NX runs over SSH, so it's secure already.  You can change the port easy enough to accommodate forwarding to more than one internal IP.  I have the steps outlined if you want them.

---

