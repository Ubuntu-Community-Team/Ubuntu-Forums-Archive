---
title: "ssh tunnel/port forwarding help"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by flyingsliverfin on 2011-07-28
I don't understand the concept of ssh port forwarding and tunneling.
I was going to set up a remote desktop (vnc) connection to my grandmother's laptop that we'll give her soon so if something goes wrong i can fix it from here (she lives on the other side of the world). However, i've read using vnc plain over the internet isn't secure, and that i can secure it by running it through an ssh tunnel.

That's what i've understood so far. However, from there on i get confused.

I'd have to run both an ssh server AND a vnc server on her laptop?
So what i'd have to do is ssh into her computer, and then while logged on on her computer, somehow open a vnc connection back from the remote server to the local computer? Then i'd go back to my local computer and open a port where the vnc connection is waiting?

All seems a bit obscure/complicated to me... sorry


From the concept, it would seem like i should be able to tunnel all the regular network traffic from the local computer to the remote one through ssh?

---

### Post by msandoy on 2011-07-28
I have to say, you are not afraid of jumping in with both feet. Setting up VNC with SSH tunnel and installing the computer on the other side of the world for support.

To make your life easier, please install a program called Teamviewer on both your computer and your grandmothers computer. It is safe, easy to use, free to use, does not need any particular ports open and it does not run in the background waiting for connections unless you start it up. 

You can find it here: [http://www.teamviewer.com/en/index.aspx](http://www.teamviewer.com/en/index.aspx)

I have used it many times, and it works wonders.

---

### Post by msandoy on 2011-07-28
In order to use your VNC SSH sollution, you would have to have both ssh server and VNC server running on your grandmothers computer. The VNC server should preferably listen to a port witch is NOT open to the internet. But you will need SSH server to have an open port. When starting a tunnel, what you practically do is, open a SSH connection without a terminal, and dedicating a port of your choice on your local computer to be talking directly to another port of your choice on the remote computer.

---

### Post by flyingsliverfin on 2011-07-31
> **msandoy said:**
> I have to say, you are not afraid of jumping in with both feet.  thanks! :)

i thought it might be a good way to start understanding all the networking stuff

when you say 'open a port that isn't open to the internet', how is that possible? I thought ports were pretty much holes in a wall that you can open selectively (im a visual thinker :) )

i was looking at the command i'd have to use:
```
ssh user@server -L local_port:service:remote_port
```
this means that im using ssh to make a connection, which tells the server to open and send the service from the 'remote_port' to the 'local_port'... if that's right then im finally getting it! 
I wonder why they arranged it that way, to me it would make far more sense to do service:remote_port:local_port (as in send the remote service from that remote port to this local port)

---

### Post by doas777 on 2011-07-31
> **flyingsliverfin said:**
> thanks! :)

i thought it might be a good way to start understanding all the networking stuff


when you say 'open a port that isn't open to the internet', how is that possible? I thought ports were pretty much holes in a wall that you can open selectively (im a visual thinker :) )

well, first an important distinction: on the Server, YOU do not open a port, a server application does.
on the Firewall, a port is as you describe, just a whole in the wall.

for your server site (your grandma's place) to make a service accessible, you must have:
1) a server service running on the port
2) the firewalls in play must allow traffic to that port, from whatever sender is designated

to check the state of your service, on the server, run 
```
sudo netstat -ntlup
```and make sure that your port is listed as listening on 0.0.0.0/0. 

then make sure your server firewall allows connections on that port:
```
sudo ufw status
```and make sure that your port is allowed or the firewall is inactive.

then make sure the port is allowed by your router. see instructions for your 
make/model of router here: [http://portforward.com/](http://portforward.com/)

to test, from the server, go to [www.canyouseeme.org]("http://www.canyouseeme.org") and see if it can see your ssh service. alternately you can use zenmap/nmap or telnet to check which ports are open to your network.

if you've done those things, your ssh should work fine.

as for VNC, I would really recommend you try [FreeNX]("https://help.ubuntu.com/community/FreeNX") instead. its easier to get running. the only thing it doesn't do, is allow you to interact with the desktop session (it logs you into your own session). 
otherwise here are instructions for tunneling vnc traffic over ssh from windows clients (skip to step 3):
[http://ubuntuswitch.wordpress.com/2007/07/01/securely-remote-control-your-ubuntu-via-putty-from-a-windows-host-vncssh/](http://ubuntuswitch.wordpress.com/2007/07/01/securely-remote-control-your-ubuntu-via-putty-from-a-windows-host-vncssh/)

on ubuntu clients, use these instructions for connecting (easier than tunneling via putty):
[http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/](http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/)

On the serverside (the laptop in question) you need both ssh and vnc (Remote desktop) running. 
SSH should be accessible from the internet, but VNC should NOT be. Make sure you have Remote desktop uPNP settings disabled, and set it up for access only from the lan.

On the client computer, you need both an ssh client, and a vncviewer. for ubuntu both of these are built in, but on windows you use PuTTY, and any vncviewer you like. TightVNC and RealVNC are both quite popular.

to connect, first you use putty to connect to the servers ssh per the instructions in the link above.
this creates a "tunnel" between a port on your local computer (5900), and a port on the remote server (also 5900). any traffic you send into the port on your end, gets sent to the port on the server, so we just need to send vncviewers traffic to the local port to send it through the tunnel to the server. 

to do that, point your vncviewer to 127.0.0.1 (by default, to port 5900). the vncviewer will send the traffic to localhost:5900, and it will be sent through the tunnel, to be received by server:5900. the server replies through the tunnel, and vncviewer gets the response. 

[]("http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/")

---

