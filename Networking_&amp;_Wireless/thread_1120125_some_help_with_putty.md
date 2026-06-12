---
title: "some help with putty"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2009-04-08
i am trying to set up putty to tunnel my vnc port 5900 through ssh port22.

I look up a bunch of different guides on line, but they say conflicting things, and I'm not sure how to set it up.




I have a work PC(10.10.10.60 local ip) behind a firewall. that is the tightvnc server.

I think i set port forwarding right, I can see port 5900, but 22 says like no service. I'm using a port checker websites. 

The ip is set to a dyndns.com account, so i think the website goes in the host spot. 

the vnc viewer is an ubuntu laptop at home. the local ip varies so do i type "local" or "localhost" in the tunnel tab?

some guides say i should set source to 5900, destination to 5901.
some say source 22 destination 5900.

i'm confused there.

---

### Post by wlraider70 on 2009-04-10
Can anyone help me  Putty  Please.

---

### Post by Kulgan on 2009-04-10
Let me get this straight. Your setup looks something like this:


Home Ubuntu laptop --- router w/ firewall --- internet --- router with firewall --- work computer

Or are the work computer and laptop on the same network (ie, both in your home)?

---

### Post by doas777 on 2009-04-10
I'm working on old memory, but if I recall, you don't actually terminate your tunnel at port 22. Putty knows that the connection is running  via ssh and will come in via 22. you want to set your tunnel from the a upper range port on your home system (mabey 4545), and the process waiting on the server for your connnection. 

that way the tunnel runs from localhost:4545 to server:5900

then when you connect with vnc, use localhost:4545, and it will be forwarded to server:5900

---

### Post by wlraider70 on 2009-04-10
Home Ubuntu laptop --- router w/ firewall (a cheap linksys wireless router) --- internet --- server with firewall (a sonicwall with LOTS of settings) --- work computer


yes

---

### Post by Kulgan on 2009-04-10
And I'm assuming that you have access to port forwarding on this Sonic Wall, or at least have set yourself up as the virtual server for SSH. If so, you don't need to tunnel at all. You just run the VNC server on whatever port you are a virtual server for on the SonicWall side of things - 22 - and run vncviewer <sonicwall's external IP>::22 (yes, that's two colons) to connect from your home ubuntu machine. 

Don't need putty at all, unless it was purely intended as an encryption layer.

---

### Post by wlraider70 on 2009-04-11
The reason for putty is simply for encryption. I was told BBC on 5900 is not secure and I deffinatly need security. I'm open to other encyrptions. 

I can set the sonic wall as I need. 
 
I'm not familar with a virtual server.

---

### Post by Kulgan on 2009-04-11
In that case you were right in the first place and it's a tunnel you need. My apologies for saying otherwise. 

This is what you need:
[http://members.shaw.ca/nicholas.fong/vnc/](http://members.shaw.ca/nicholas.fong/vnc/)

At least for the work side of things. You also need to play with ssh on the home side. In that doc they use putty in both cases. In linux, you do the same thing (making the other "end" of the tunnel) by logging in to the ssh server slightly differently:

```

ssh -C -D 5900 user@remotehost 

```

-D <port> locks <port> on your *local* machine to the tunnel user@remotehost. So any traffic directed to port (in this case 5900) on your machine will be sent to remotehost. 

-C compresses the data sent over the tunnel. I haven't tried that myself with SSH, but it should be an advantage (afaik). Not needed though.

<port> can be whatever you want it to be. The only difference it makes is that when you connect with vncviewer, you run localhost::<port>. 

This is all assuming that you are able to SSH into your work computer from home.

You will, of course, not need to do any port forwarding on your home router as this is only required when dealing with unrequested traffic.

---

### Post by wlraider70 on 2009-04-19
Kulgan, can you clarify one thing for me. That guide you linked to is very helpful, but it says to install cygwin and use that to install openssh on the host box.

I guess i was under the impression that i could use putty on the host to put the port 22 traffic back to port 5900 or the VNC. IS that not the case?

---

### Post by Kulgan on 2009-04-19
As far as I know, putty is a client only, isn't it?

We need something on the other side of the ssh tunnel to transform it back into a VNC connection. This is also the reason you have to enable loopback connections in the tightVNC server. 

You don't actually need putty at all, seeing as you're using Ubuntu on the client side ;)

---

### Post by ktrnka on 2009-04-19
Let's assume you don't have access to your firewall @ work. If you don't have access you will need a place you can ssh to. If you leave your laptop on @ home, forward port 22 to your laptop's IP address. 

What you will need to next is setup a reverse ssh tunnel from your work (a tunnel out).

(Work computer is Windows I'm assuming)
If we are going to use a vnc server use 5900 if Windows Remote Desktop use 3389

From work computer in Putty:

Fill out the Session section with your HOME dyndns name.

Then navigate to:

Connection>SSH> Select Tunnels

(Make sure you have disabled vnc-server service from your laptop if you use a destination port of 5900)

source port will be 5905 

You may use any port number you like but it must match the port number used by your vnc server.

Destination will look like this:    localhost:5900 (default VNC port number)


Make sure the "Remote" radio button is selected. 

Click Add

Then click OPEN

Login via ssh as normal. (side-note - make sure to use TcpKeepAlive setting in your sshd_config to make sure the session doesn't automatically close before you get home)


Once you get home to your laptop, you will need to open up a vnc client ( I use tsclient - it's in the repos. You will also need to install xtightvncviewer for vnc support in tsclient)

Where it asks for Computer: 

Put localhost:5905

This will connect to port 5905 on your ubuntu laptop and then tunnel that back through ssh all the way back to your work and connect to port 5900 @ your work. 


Now if you want to use Windows Remote Desktop instead, just change all the port numbers to 3389.

---

### Post by ktrnka on 2009-04-19
If you have a 3rd party where you can ssh to that allows binding of port numbers you would just change putty's session to connect to the 3rd party location (example ssh.server.com) and from your ubuntu laptop you would execute a local bind by bringing up a command line and execute:

```
ssh -L 5905:localhost:5905 sshuser@ssh.server.com 
```

Then just enter the same information into your Terminal Server Client as I had stated in my previous reply.


so the ssh tunnel would look like  WORK:5900:tunnelto:5905 -> thirdpartySSHserver <- Ubuntulaptop:5905:tunnelto:5905

---

### Post by ktrnka on 2009-04-19
For future reference:

```
ssh -L localportnumber:RemotecomputertoconnectTO:RemotePortnumber [email]sshuser@ssh.server.com[/email]
```

---

