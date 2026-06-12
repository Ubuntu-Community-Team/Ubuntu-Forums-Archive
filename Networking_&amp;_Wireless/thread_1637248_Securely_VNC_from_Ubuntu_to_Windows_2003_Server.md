---
title: "Securely VNC from Ubuntu to Windows 2003 Server"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by Anquietas on 2010-12-04
Hello, a little advanced problem here, not for newbies ! :)

I have 5 servers at my workplace: 3 Linux Boxes and 2 Windows Server 2003s ... so far so good...

I don't have to mention the fact that I can nicely connect to ssh on all the 3 linux servers, securely, do my work, etc... it's all perfect. Linux rulz over Windows billion times :)

The problem comes when I want to remotely connect to the Windows Servers.

I understand that RDP (Remote Desktop protocol), the proprietary tool of Windows has encrypted connections, however it starts a separate session. I do NOT want that... I want the same screen as if I were sitting in front of it. (like a VNC).
For this, I've installed UltraVNC for Windows on both the Windows Servers...

I can easy vnc to these with Vinagre (the ubuntu vnc client) to UltraVNC Servers... still, no problems, everything is OK except one thing: I want encryption ! Secure channel.
Vinagre and UltraVNC do not provide (or I don't know to provide security)

I can easely solve this with a VPN connection but I don't want to install vpn there for 2 windows servers...

My problem is... do you know a secure way what I can use to connect from my home Ubuntu Desktop Laptop VNC Client (Vinagre) to the Windows 2003 Servers from my office ?...
(something that has to do with SSH Tunneling but I didn't quite understand it very well, only that I am suposed to have SSH on the Servers which I don't have because it's a Windows Server)...

Please advice :)
RDP or VNC Secured or some solution that I can connect to the existing Desktops of those W2K3 Servers securely from my Ubuntu Desktop.

---

### Post by CharlesA on 2010-12-04
Huh?

You can always RDP to the administrator account on the Win Server box and it'll act just like you have "logged in locally"

I don't use VNC for Windows machines I can connect to with RDP unless there is a specific reason for using VNC.

Quick and dirty way to connect securely:

1) SSH to linux box and create a tunnel to the Windows box
2) Connect to Windows box using localhost:someport

---

### Post by Anquietas on 2010-12-04
Yea, well...

1. I've tried the RDP, it prompts me with a new Logon Screen and if I want to log in, it opens a new Desktop Session, I want the old screen, the one with a program running.
RDP does not act as a VNC... it opens new sessions (remote, of course, but new ones not existing ones)

2. Can you please detail me the steps ?... what linux box ? my laptop ?... or.. which commands, etc.. please if you could just detail me the steps please... what must I do ?...

---

### Post by CharlesA on 2010-12-04
> **Anquietas said:**
> 
1. I've tried the RDP, it prompts me with a new Logon Screen and if I want to log in, it opens a new Desktop Session, I want the old screen, the one with a program running.
RDP does not act as a VNC... it opens new sessions (remote, of course, but new ones not existing ones)

Are you logging off of the RPD session or are you just closing the window?

If you just close the Window, the session and all running programs will still be running. If you logout, you close all running programs and end that session.

> **Anquietas said:**
> 
2. Can you please detail me the steps ?... what linux box ? my laptop ?... or.. which commands, etc.. please if you could just detail me the steps please... what must I do ?... 

You'd SSH to one of the linux servers nad run a command like this:

```
ssh -L 4001:serveripaddress:3389 user@host
```

Then connect to localhost:4001

---

### Post by Anquietas on 2010-12-04
Thank you ! That worked perfectly :)

I still don't quite understand how does the VNC Server on the other side encrypt the information or how does the ssh do the encryption but I trust there is a safe mechanism.

---

### Post by CharlesA on 2010-12-04
Anything transmitted over SSH is encrypted end-to-end. VNC is still unencrypted, but it's being transmitted via an encrypted medium.

Does that make sense?

---

### Post by Anquietas on 2010-12-04
Yes but I discovered something else...

The SSH Server MUST be on the SAME server with the VNC ... for the encryption to work.

that means something like:
ssh -L 5900:localhost:5900 SSH_SERVER
(and SSH_SERVER = localhost:5900 (the vnc server))

this is not the case with me.

I have:

ssh -L 5900:REMOTE_VNC_SERVER:5900 localhost
(as I was using localhost (own ssh on ubuntu to encrypt))
(but with this method, it encrypts only between the ssh client and ssh server)... the SSH Server establishes a remote connection with the VNC Server which looses the encryption because the remote vnc server doesn't handle encryption...

I don't know if I make any sense... but this is usefull only if the VNC Server and SSH Server are on the Same Physicall Machine so that it is FULL Encryption.

For this to work properly I would need a SSH Server on that Windows 2003 Machine to be able to use:
ssh -L 5900:localhost:5900 WIN2003SERVER (with ssh support)...

I hope I make sense :))

---

### Post by CharlesA on 2010-12-04
The point of an SSH tunnel is to have an encrypted link over an insecure network like the internet. If the traffic is going over the internet, it's encrypted.

---

### Post by Anquietas on 2010-12-04
It's encrypted if the SSH Server is on the same machine as the VNC Server.

If not, the encryption is only between the SSH Client and the SSH Server. Anything outside this, is unencrypted.

[http://www.bitvise.com/files/port-forwarding-2.gif](http://www.bitvise.com/files/port-forwarding-2.gif)

For full 100 % procent encryption, the viewer and ssh client must be on the same machine, and the ssh server and vnc server also on the same machine.
Anything outside these, become unencrypted.

I think I will go with RDP perhaps. Thanks for your support.

---

### Post by CharlesA on 2010-12-04
That's correct.

Do you normally encrypt traffic in your local network?

---

### Post by Anquietas on 2010-12-04
No, I do not encrypt traffic in my LAN, but when I'm at home and I want to access remotely those Windows Servers,... the route is via the Internet... and I need encryption :)

---

### Post by CharlesA on 2010-12-04
If you are using SSH, it's already encrypted when it goes over the internet.

---

### Post by Anquietas on 2010-12-05
Only if the SSH Server resides on the same machine as the VNC Server. If not, all the traffic between the SSH Server and the VNC Server is UNencrypted, only the traffic between SSH Server and SSH Client is encrypted.

All things are clear.
Let's close this topic.

---

