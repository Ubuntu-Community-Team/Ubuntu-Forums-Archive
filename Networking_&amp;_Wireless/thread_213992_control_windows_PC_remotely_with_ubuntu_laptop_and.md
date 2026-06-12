---
title: "control windows PC remotely with ubuntu laptop and VNC?"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by yellowband on 2006-07-12
Hi

i read that VNC works on both windows and linux. I have tightVNC installed on my windows box and i want to control it with VNC on my ubuntu laptop on the home network. is this even possible?

i have tried to type, in the terminal, vncviewer. Then it asks for the ip address of the computer i want to control. i then enter 192.169.1.100.  And then it just hangs and nothing happens. 

is this correct? something seems wrong with this.  What if i was outside of my network? i wouldnt' enter 192.168.1.100, that wouldn't work would it?

thanks for any help.

---

### Post by MrHorus on 2006-07-12
> **yellowband said:**
> 
i read that VNC works on both windows and linux. I have tightVNC installed on my windows box and i want to control it with VNC on my ubuntu laptop on the home network. is this even possible?

Yes - it works perfectly and I myself have done it several times, both with Linux-Windows and with Windows-Linux.

> i have tried to type, in the terminal, vncviewer. Then it asks for the ip address of the computer i want to control. i then enter 192.169.1.100.  And then it just hangs and nothing happens.

Are you running a VNC server?
If not, install one on your Windows box and set up a password and port to run on and ensure that any firewalls are configured to allow traffic on that port.

Then it shuld be a case of launching the vncclient on your Linux machine and supplying the IP and password. 

> What if i was outside of my network? i wouldnt' enter 192.168.1.100, that wouldn't work would it?

That's correct. The 192.168.x.x IP block is non-routeable, which means that it is not accessable on the global Internet and is reserved for private networks that anyone can use.

You would need a real IP address to access the machine across the Internet.

---

