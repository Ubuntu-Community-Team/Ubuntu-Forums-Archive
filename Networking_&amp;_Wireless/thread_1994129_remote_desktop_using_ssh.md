---
title: "remote desktop using ssh"
date: 2012-06-02
forum: Networking &amp; Wireless
---

### Post by hurtstotalktoyou on 2012-06-02
Hi guys.

So I successfully set up a secure ssh connection using public/private keys and passcode and all that.  But all I know how to do is access my server from the client's terminal (i.e. text-only).  If possible, I'd like full graphical access to my server desktop.

I got the impression from Google searches that it is possible to use the Remote Desktop feature (I think it's called vino/vinagre) through ssh.  But all the tutorials I found were way over my head.

Can anyone point me in the direction of an easy-to-understand tutorial?  Or maybe just tell me what to do here in this thread?

Any help would be much appreciated.  Thanks, guys.

---

### Post by TheFu on 2012-06-02
ssh can setup the tunnel, but it doesn't do the GUI part.
To have GUI access, you need a server program running on the remote machine and a client program running on your desktop/laptop.

You can use VNC, NX, or some new-fangled GUI.  NX includes ssh so a separate ssh tunnel isn't needed. The FreeNX server is harder to setup. NX is much more efficient than any other GUI desktop I've seen anywhere. An NX client is required.

For VNC over ssh tunnels, google found this how-to: [http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html](http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html)

There are VNC clients for almost every OS, but be certain that you ALWAYS tunnel VNC traffic if the internet is involved. **VNC is not secure and needed ssh or a VPN.**

---

### Post by ajgreeny on 2012-06-02
You could simply use x-forwarding when in an ssh session by using the command ```
ssh -X user@IPaddress
``` From the client you can then run the graphical applications that are on the server machine.  Not quite a remote desktop, but still useful.

---

### Post by TheFu on 2012-06-03
> **hurtstotalktoyou said:**
> Can anyone point me in the direction of an easy-to-understand tutorial?  Or maybe just tell me what to do here in this thread?

Any help would be much appreciated.  Thanks, guys.

This isn't a tutorial, [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) but it does try to explain the different ways to have a remote desktop or remote GUI.  With that, you can google the specific solution you'd like to try using the generic terms. Something like these:
* ssh tunnel vnc setup
* nx server setup
* remote x/windows

The response about using "ssh -X" is actually what I use on LAN connections, but over a WAN, it is painfully slow. That is an understatement, but if you have the bandwidth - it is really, really easy.

---

### Post by hurtstotalktoyou on 2012-06-03
Okay, thanks for the suggestions guys.  I'll check them out.

---

