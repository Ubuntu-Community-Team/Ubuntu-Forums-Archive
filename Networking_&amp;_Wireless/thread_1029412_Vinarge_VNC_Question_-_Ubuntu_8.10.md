---
title: "Vinarge VNC Question - Ubuntu 8.10"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by umechanism on 2009-01-03
I have two computers both of which are running Ubuntu 8.10 and are connected by wired connections to a Linksys router.  I can not see either computer from the other computer but I want to be able to use VNC to control computer #1 by using computer #2.

So far, I have done the following:

(1)  Assigned static IP addresses to both computers.
(2)  Enabled remote desktop viewing under System>Preferences>Remote Desktop

Questions I have:
(1)  Do these two computers need to be in the same "Workgroup" as common on Windows networks?  If so, where do I set this?
(2)  When I try to use Vinarge to connect from Machine #2 to Machine #1 I get an error telling me that port 5900 is closed.  Why?

Thank you for the help.

Mike

---

### Post by edkmho on 2009-01-04
I have the exact problem and still could not find a solution to it. Can anyone help, please. 

I have just started using linux 2 months ago. Please help.

Thanks.

---

### Post by edkmho on 2009-01-04
umechanism,

I have sort of find out why you are getting the connection closed messsage. I have experiment with various selection in the setting up the remote desktop, if you unchecked the "Only allow local connections" the message will not appear and you will be able to connect. 

Though it is working now, but i wanted the connection to only allow local connections, how can i achieve that? Please help anyone.

---

### Post by umechanism on 2009-01-04
> **edkmho said:**
> I have the exact problem and still could not find a solution to it. Can anyone help, please. 

I have just started using linux 2 months ago. Please help.

Thanks.

Edkmho,

I have found that UltraVNC works very, very well on Vista to Vista or Vista to XP connections.  I have not had a chance to try UltraVNC client/server on Linux but the website does indicate that the client side can run within a Java environment on Linux machines.  I am not sure if the UltraVNC server will run on Linux machines but there are VNC servers that will.  Perhaps you could use the UltraVNC client on your linux machine and another type of VNC server on the host machine.  I believe "TightVNC" has server/client solutions for Linux.

Also, you can use Ubuntu 8.10 to control a Windows XP Pro machine via Remote Desktop.  I did not believe this would work but it does.  Just open a terminal on your Linux machine and, assuming the XP Pro machine is on your LAN and configured to accept incoming connections, type this:

```
rdesktop 192.168.1.105
(assumes that 192.168.1.105 is the IP of your machine)
```

You will see a small window open with full desktop access to your XP Pro machine.  If you would like a full screen instead, then type:
```
rdesktop -f 192.168.2.105
```
where the "-f" means "full screen".

It is funny that I can not get Vinarge to do the same thing on the XP Pro machine as "rdesktop -f" does but I decided not to fight it any longer and just accept it as fact.

I hope this helps you.

---

### Post by umechanism on 2009-01-04
> **edkmho said:**
> umechanism,

I have sort of find out why you are getting the connection closed messsage. I have experiment with various selection in the setting up the remote desktop, if you unchecked the "Only allow local connections" the message will not appear and you will be able to connect. 

Though it is working now, but i wanted the connection to only allow local connections, how can i achieve that? Please help anyone.

I will check this setting.  Hopefully, that is my problem.  I'm in Vista now and must reboot to check.

Thank you for the help!

---

### Post by umechanism on 2009-01-04
I just checked and both computers were set to allow local connections only.  I unchecked these (allowing all connections) but I still get an error that says:

"Connection to host 192.168.1.109:5900 was closed".

Any ideas?

---

### Post by umechanism on 2009-01-06
Anyone?

I'm still having issues getting my two Ubuntu 8.10 computers to communicate over the network.  Both computers are dual-booting with Windows and both, when in Windows, communicate over the network without issues.  I just can't get Ubuntu to do the same and I prefer to use Ubuntu 100% of the time but I must get this network issue resolved.

All help is greatly appreciated and will be shared with others.

Thanks!

---

### Post by AWittyUserName on 2009-02-06
> **edkmho said:**
> umechanism,

I have sort of find out why you are getting the connection closed messsage. I have experiment with various selection in the setting up the remote desktop, if you unchecked the "Only allow local connections" the message will not appear and you will be able to connect. 

Though it is working now, but i wanted the connection to only allow local connections, how can i achieve that? Please help anyone.

Unchecking the local network option resolved this for me.  Thanks for doing the research.

Now that I think a bit harder about it, both machines are behind a gateway router, anyway.  So I'm not sure this feature makes any difference in my situation.

---

