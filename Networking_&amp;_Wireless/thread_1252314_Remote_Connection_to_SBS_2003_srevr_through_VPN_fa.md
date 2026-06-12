---
title: "Remote Connection to SBS 2003 srevr through VPN fails"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by yodawise on 2009-08-28
Background:
I am new to ubuntu and to this forum. Please pardon my ignorance and lack of knowledge. I am familiar with UNIX and some Linux distros. I am not a sys admin. I am learning Ubuntu to be able to migrate a tiny MS SBS2003/Vista operation  to Ubuntu/Vista and ultimately all Ubuntu.

I have installed Ubuntu 9.04 on a 2nd hard drive on a home PC to dual boot with Vista. RDC from Vista to remote SBS2003 works fine.  

Here goes my current road block..

I am struggling to connect to a remote SBS2003 server which is behind a Syslink router.
After reading a few on line pages about how to configure a VPN client, I have been able to run vpnc, though it dumps these messages:
> .: 7: Can't open /usr/share/sendmail/dynamic
run-parts: /etc/resolvconf/update-libc.d/sendmail exited with return code 2
run-parts: /etc/resolvconf/update.d/libc exited with return code 1
VPNC started in background (pid: 5354)...ping to the router IP fails
> 5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4004mstsclient  for RDP and RDPv5 fails as follows:

> ** (tsclient:7266): WARNING **: 
Autoselected keyboard map en-us
ERROR: channel_register
WARNING: Initializing sound-support failed!
ERROR:SBS2003_server: unable to connecttsclient for VNC protocol fails as follows:
> ** (tsclient:7975): WARNING **: 
vncviewer: ConnectToTcpAddr: connect: No route to host

Unable to connect to VNC serverThe SBS 2003 is listening to ports 3389 and 1723.

I will appreciate a step by step guide to remote connect to SBS2003. Here are some questions, which show that detailed instructions are desperately needed to configure VPN/remote connection.

1. Do I need to do port forwarding in the router? If yes, why does it work for Vista and not Ubuntu?
2. Do I need to specify the IPsec gateway IP listed in the Cisco pcf file in /etc/hosts?
3. Do I need to list the SBS 2003 in /etc/hosts? If yes, what IP address?
4. What protocol should I specify for the tsclient? If VNC, the protocol file field  becomes enabled. Trying to browse for a protocol file opens a window with the title "Choose and RDP file to open". Where do I get an RDP file from?

Any help will be appreciate. Thanks in advance!

---

### Post by yodawise on 2009-08-31
Any volunteer to help me , please ?

---

### Post by yodawise on 2009-09-08
I was able to solve the problem as follows:

1.  I used kvpcn to import the Cisco pcf file and was able to connect to the router.

2. I used rdesktop give the local IP address for the server:

   ```
rdesktop 192.168.1.2
```

---

