---
title: "SSH help"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by mad_max0204 on 2009-02-25
Hi

in the past few days I've gained the need to control one of my home computers from work. I googled a bit and installed SSH (sudo apt-get install ssh-server) and it works. I opened port in my router and I can connect from windows pc to it using putty.
Now my question is how can I get more security (those keys are a bit unclear to me) so its not that easy to connect to my computer and how can I after ssh connect control my desktop (I can do almost everything from ssh console but there are some things I cant so I need this).
Any help/guides/articles/links are welcome.


Thanks

---

### Post by Iowan on 2009-02-25
[This]("https://help.ubuntu.com/community/SSH_VPN") might be what you're looking for.

---

### Post by issih on 2009-02-25
Hmmn, things to consider.

!) Use deny hosts, so that any IP trying to log in and getting the wrong password a few times is blocked.

2) Use a non standard port (i.e. not port 22) to make it harder for people with malicious intent to find your server.

3) Enable the built in remote desktop, or just run a vncserver of your choice

4) Forward the port over the ssh tunnel and then connect a vnc client to the local port you forwarded on to.

Thats about all I can think of for now..

Hope that helps

---

### Post by mad_max0204 on 2009-02-25
Thanks for the guide but I'm trying to connect from Windows computer.

Putty gets me into my computer but I cant get vnc clients to connect.

How can I raise security so people cant connect to my ssh so easy ?
Are there any ways of using keys or something ?


EDIT: 
@issih
Basically I changed the port, enabled builtin remote desktop.
Problem is that VNC clients cant connect.
They ask me for pass, I type in pass from remote desktop properties but it fails to connect.
Maybe its because I generated those id_rsa and id_rsa.pub keys ?
Dunno :(


Thanks

---

### Post by mad_max0204 on 2009-02-25
Okay

I managed to secure acess to be keybased.

Now my next problem is that when I connect with putty I cant connect with VNC.

---

### Post by x1101 on 2009-02-25
What you will want to do is create an ssh tunnel, and use vnc over that ssh tunnel. [HERE]("http://members.shaw.ca/nicholas.fong/vnc/") is a howto on that.

---

### Post by mad_max0204 on 2009-02-25
I created that SSH tunnel and I even got ultraVNC to ask me for password but when I entered, it said that I dont have a DSMP plugin selected (which I do).
With tightVNC it just gives and error that it cant connect.

I dont know whats the problem.

---

### Post by issih on 2009-02-26
Hmmn, I'm at a bit of a loss at this point.

check whether the vncsoftware works if you try and use it just within your home lan.

After that make doubley sure that your tunnels are working, and that you are connecting to the local windows machine with the vncserver, i.e. connect to localhost 5900 or whatever port you forwarded onto.

Other than just debugging every step I'm stuck, as that should work as far as I know.

Sorry about that

---

### Post by mad_max0204 on 2009-02-26
Hm, it seems that I cant even connect from my own computer to my remote desktop server on it (vino should be the default ubuntu one).
How can I debug that in order to fix it ?

Or maybe I should switch to one of the NX programs ?

---

### Post by issih on 2009-02-26
Curious, first of all try disabling the password (just to make it as simple as possible) and then try connecting with the remote desktop viewer.

The local remote desktop should just show up in the list and you can click on it to view it, all a bit circular I know but it does work after a fashion.

---

### Post by mad_max0204 on 2009-02-26
I cant connect to it even without a password. I'm trying from computer with Ubuntu.
I cant even see it. Seems that something is wrong with vnc server.

EDIT:
I just did /usr/lib/vino/vino-server and it works now.
I gotta make it start on startup somehow.

EDIT2:
I think I'll have to install VNC or some NX server. This ubuntus one is lame.

---

