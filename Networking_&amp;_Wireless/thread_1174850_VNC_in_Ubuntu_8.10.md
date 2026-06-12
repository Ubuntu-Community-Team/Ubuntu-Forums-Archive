---
title: "VNC in Ubuntu 8.10"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by Rastus302 on 2009-05-31
Hi,
I have a server with a static IP address running ubuntu 8.10 that I would like to VNC into from the local network only.
 
I have allowed Remote connections under System > Preferences > Remote Desktop
 
but when I try to logon using VNC Viewer for Windows from a local XP Box, I cannot connect. I get the message "unable to connect to host Connection refused (10061).
 
There are several tutorials out there but most seem to be old and it seems like I am probably missing something simple.
 
Can anyone point me to a troubleshooting guide for VNC on 8.10 or suggest what may be the problem. Thanks.

---

### Post by RedSingularity on 2009-05-31
Have you installed the VNC client on the computers you want to connect to?

---

### Post by Rastus302 on 2009-06-01
No, I have not
I was under the (perhaps mistaken) impression that allowing RDC access on the ubuntu machine would allow another machine to VNC into it.
 
Is there other software that I need to install?

---

### Post by strife242 on 2009-06-01
No, you don't need any other software than the VNC viewer.

When you connect to the server, do you see anything on the servers screen?

I forgot to turn off the "ask for permission" checkbox first time I set it up which lead me to be refused (since nobody was at the server to accept my attempt).

---

### Post by superprash2003 on 2009-06-01
do you run firestarter or ufw or anything similar?? are you able to ping the machine?

---

### Post by Rastus302 on 2009-06-02
[INDENT]"When you connect to the server, do you see anything on the servers screen?"
[/INDENT]
No, it does not allow me to connect, I get the message "unable to connect to host Connection refused (10061).

the "ask for permission" button is off and I have it set to require password authentication.

[INDENT]do you run firestarter or ufw or anything similar?? are you able to ping the machine?

[/INDENT]Not that I know of.  I can RDC FROM the ubuntu box to a windows machine without problems.  I have not yet tried to ping the ubuntu server from the windows box but I will today and I'll let you know.
Thanks

---

### Post by Rastus302 on 2009-06-03
More Info

Yes, I can ping the machine at 192.168.10.9 no problem.

But when I try to connect with open VNC standalone viewer I get the same error message : (10061).  I never see the screen of the ubuntu machine.

I tried with Tight VNC standalone app and got "failed to connect to server". Again, never got to see the screen.

I have not specified a port and there is no firewall between the boxes on this network. 

BTW, just to be sure I hadn't messed anything up, I did a clean ubuntu install and rechecked again.  No Joy.

I don't need to install something additional like tightVNCServer do I?

Suggestions on what to check or try next?

---

### Post by superprash2003 on 2009-06-04
post output of **sudo iptables -L **from the ubuntu machine

---

### Post by Rastus302 on 2009-06-04
OK here is the output of sudo iptables -L:

	 	 Chain INPUT (policy ACCEPT)  
 target     prot opt source               destination          
 

 Chain FORWARD (policy ACCEPT)  
 target     prot opt source               destination          
 

 Chain OUTPUT (policy ACCEPT)  
 target     prot opt source               destination   
 
I await further instructions. (insert hopeful looking smilie here)
Thanks

---

### Post by Rastus302 on 2009-06-04
OK,
Even more info

I have another ubuntu machine running on the local network so I tried

vinagre host:0 and got

"connection to host host:5900 was closed"

again, pinging to the host is no problem but VNC into it gets a closed connection message.

Clearly, it seems like I am missing some configuration detail on the ubuntu server.
But What?

---

### Post by Rastus302 on 2009-06-04
There is Joy in Mudville.

I found the answer here

[http://ubuntuforums.org/showthread.php?t=927440&highlight=vnc+troubleshooting](http://ubuntuforums.org/showthread.php?t=927440&highlight=vnc+troubleshooting)

it has to do with the checkbox to just allow local network connections.  uncheck it and life is good.

Thanks Guys.

---

### Post by frunze on 2009-06-04
I had the same problem. Seems like default vnc is having problems. I resolved it by installing **x11vnc** using synaptic package manager. Since that time it worked flawlessly.
The only problem I had is when you restart the machine you had to go and start x11vnc manually. May be there was a way to make it automatic... It was long time ago.

---

