---
title: "Is it possible to forward desktop via X11/SSH"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by umechanism on 2009-01-21
I am running Ubuntu 8.10 with Openssh server installed.  I can use Putty to connect to it either locally or outside my LAN via the internet.  It works great.

I took a step further today and installed Xming on my Windows XP computer - the same computer that I can connect via Putty/SSH to my Linux machine at home.  Everything seems to be working correctly.  Once Xming is running I connect with Putty and specify X11 forwarding.  Once connected, I can type "firefox" and Firefox will launch.

All of that is good but I was wondering if there is a way to forward the entire Ubuntu desktop via X11 so that I can just point and click on icons instead of typing commands like "firefox"?  I want to do this securely and encrypted (ssh).  I once was able to get the "kicker" panel going but I can't get that now.

Any ideas?

Thanks!

---

### Post by croto on 2009-01-21
the easiest way is using VNC. You need to run the server in the remote computer, and the viewer on the local machine (I don't know Ubuntu, but it may have it installed by default, it may be under some more "descriptive" name, as Desktop sharing, or something like that, try the forum). It can be tunneled through ssh, and you don't need X11 installed in the client computer. It's a lot faster that exporting X11 windows directly, because VNC connections are compressed.

---

### Post by umechanism on 2009-01-21
Thank you for the reply.

I can connect to my remote machine, the one running Ubuntu, using VNC but how do I connect with VNC via SSH?  I'll be using a Windows XP computer as the VNC client connecting to the VNC server on the Linux machine.  Is there an option to connect with VNC-SSH?

---

### Post by croto on 2009-01-21
That's not hard. First, let's assume for the sake of the explanation that you have the VNC server running on linux host A, and the client running on linux host B (I know that the client is on windows, but let me ignore it for a second). 

First, you need to create an ssh tunnel between hosts A and B. The easiest way is connecting by ssh from host B to host A, telling ssh to create the tunnel. Imagine the server is running on screen "n" ("n" could be 0, 1, 2, etc.). That means the server is listening on port 5900+n in host A. That's the destination socket (ip+port) we need to create the tunnel to. The local socket will be on a port that we choose, let's say 5903.

The command on linux to create the tunnel is
```

hostB$ ssh -L5903:127.0.0.1:5900 user@hostA

```

This commands does to things. 1) Connects to hostA as it normally would. 2) Creates the ssh tunnel. Let me try to explain again what the -L switch is doing. The format is -Llocalport:destinationmachine:destinationport.
After the tunnel is created, there's a service listening on port localport on the machine where the ssh command was issued. Then whatever connection to that port will be forwarded to hostA (because that's where we ssh'd to). Then from there, the connection will be forwarded to destinationmachine port destinationport. In our example, that is localhost (127.0.0.1), but FROM THE POINT OF VIEW OF hostA!, that means that in the end, the connection will go to the port on hostA where vncserver is listening. destinationhost DOES NOT have to be localhost, you can send the connection anywhere you want, making the tunnel work as a proxy (in this way you could for example, bypass firewalls).

Anyway, the final step. You are ready now to connect the vnc client. Where should you tell the client to connect? Well, the ssh tunnel is expecting connections on port 5903, and it is listening in hostB. So from hostB, you tell vncviewer to connect to 127.0.0.1:3 
Why localhost again? Remember that this localhost is from the point of view of hostB, which is where vnc tunnel is waiting connections. Why 3? because we are listening on port 5903. 

Now, you are using windows on hostB. No problem. Putty can do ssh tunnels too. In the connection screen you'll see something like "ssh tunneling" or "ssh forwarding". Hopefully with my explanations you'll be able to figure out how to fill out the input box. If not, I'll be here for a while.

---

