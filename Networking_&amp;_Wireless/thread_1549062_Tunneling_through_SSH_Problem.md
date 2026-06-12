---
title: "Tunneling through SSH Problem"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by djbushido on 2010-08-09
Okay, I'm having a problem trying to tunnel a VNC connection through my computer. Basically what's happening is that I can initiate the connection on SSH, but I have to open another port through the router to connect to the VNC server.
So far as I can tell, what happens is that the traffic is tunneled through SSH, but still goes to a separate port on the router, which then forwards it to the computer. And I would prefer to not have to open a separate port. Is there a way to tunnel the traffic through the same port as well? Or is there a secure vnc the way there is a secure ftp?
Anyway, all help would be appreciated, thank you!

EDIT: To try and explain the network model a bit better:
The ssh client is forwarding the vnc requests through the tunnel, but they end up at the router at port 5900, not the end server at port 5900. Thus, I would have to forward port 5900 as well. Does that make any more sense?

---

### Post by YesWeCan on 2010-08-09
client ---> router ----> server

You must configure the router to forward all port 22 traffic to the server. Then you have to use SSH on the client to "port-forward" the server's port 5900 to a port on the client, via the router.

ssh -p 22 -L 12345:localhost:5900 router_ip

This command makes the server's port 5900 appear at the client's port 12345. You can tell Vinagre or another vnc viewer to connect to localhost:12345. The -p sets the SSH port to use. This is redundant in this case because SSH defaults to 22. You need to tell SSH to connect to the router's external address; the router then passes the connection to the server and relays the replies back again.

Note that all communication between client and server is done using port 22 only. The SSH port forward (aka SSH tunnel) simulates a port 5900 to port 12345 connection. But it is all done using port 22.

Make sure the server is configured to export the desktop on port 5900.

---

### Post by djbushido on 2010-08-09
So if I understand correctly, the "end of the tunnel" is at the actual client, not at the ip address used to connect to. I'll try again, and see what happens.

EDIT: Tried again, and I'm still getting tightVNC saying that the connection got closed.
It should also be noted that I'm using putty, not ssh

EDITEDIT: I can connect locally, so the problem is definitely either in the way I am setting up the tunnel, or in the router. There is no firewall on the actual computer.

---

### Post by YesWeCan on 2010-08-09
You are running Vino (remote desktop) on the server, right?
When you say you can connect locally, you mean you are viewing your server's desktop on its own desktop? Sounds like a recursive challenge. How does that work?
You are using Putty on the client...so it's a Windows client and you are using tightVNC. Should be fine. I do this myself on Win7.

The command I posted works: I just tried it to get a remote desktop from a Ubuntu server 2500 miles away. I am running tightvncserver on the server so I can have multiple desktops without having to be logged in at the server console.

---

### Post by YesWeCan on 2010-08-09
Interesting. I get the same "connection closed" as you do when I try this using Windows 7.
Using Ubuntu as a client it works fine.
Using Windows over a VPN it works fine.

I think this is something to do with Windows security. Tightvnc reports that the connection is established before the connection closed dialog appears. I'll see if I can fix it.

---

### Post by YesWeCan on 2010-08-09
Ok it now works. At least using tightvncserver and server port 5901. I wasn't using the correct entries in putty the first time.

In Putty, you have to put the router's IP in the Session section and port 22. In SSH Tunnels section, you need to put 12345 (or whatever you choose) in source and localhost:5900 in destination, then add. Then click Open.

In Tightvnc you need to put localhost:12345. You should then be asked for a vnc password.

---

### Post by djbushido on 2010-08-09
Okay, yeah, the last post fixed it. I'm surprised though, that's not how I would have expected the port syntax to work. Do you need the same syntax for the "ssh" command, or use the syntax on the first you posted?
Anyway, here is how my network is set up:
Windows 7 client (putty) -> OpenSSH (Ubuntu) -> x11VNC (Ubuntu)
Anyway, it is working now, thank you so much!
Also it is not the windows security, I double checked and the firewall was on during all of this.

EDIT: I forgot to say thank you. Thanks!

---

### Post by YesWeCan on 2010-08-09
\\:D/ 
The ssh syntax always confuses me. I did try my post #2 command from Ubuntu and it worked.
FYI I use a permanent OpenVPN tunnel between my client and the server. VPN is like a direct LAN cable connection except better because it is encrypted. And it is bomb-proof. So I don't have to faff about with Putty and ssh tunnels each time. I just tell tightvnc the virtual ip address and the port of the server. Check it out.

---

