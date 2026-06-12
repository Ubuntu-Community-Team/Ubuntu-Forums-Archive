---
title: "Likewise &quot;open ports to DC&quot;"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2009-06-23
So i've seen LOTS of posts about using Likewise.  

but the error i have is about these ports... see below.


I open the ports from the AD server to this linux box. They are open. It is possible i opened them worng, but i dont think so. the firewall is a sonicwall 190. The Linux box is hard wired to the main switch and it already has an internal ip of 10.10.10.xx    
So I open the ports as LAN to LAN. 

Any ideas




.......
luke@vaio:~$ sudo domainjoin-cli join LPCC.LOCAL.COM Administrator
[sudo] password for luke: 
Joining to AD Domain:   LPCC.LOCAL.COM
With Computer DNS Name: vaio.LPCC.LOCAL.COM


Error: Manual configuration required [code 0x00080043]

The configuration stage 'open ports to DC' cannot be completed automatically.
Please manually perform the following steps and rerun the domain join:

Some required ports on the domain controller could not be contacted. Please
update your firewall settings to ensure that the following ports are open to
'LPCC.LOCAL.COM':
    88  UDP
    389 UDP
    464 UDP
    123 UDP
    88 TCP
    389 TCP
    445 TCP
    464 TCP
luke@vaio:~$

---

### Post by wlraider70 on 2009-06-24
I can ping the server, is there a way that i can ping a specific port?

---

### Post by nofear1056 on 2009-06-30
Bump, as I am having the same problem/error message when trying to join a domain.

---

### Post by wlraider70 on 2009-07-06
so i turns out that sharepoint is broken on my server. 
Could that be the issue.
That going to be my assumption till i fix sharepoint.

---

### Post by vap0rtranz on 2009-07-07
Your test was in the wrong direction.  The DC responds to client via ephemeral ports.  The client opens the ports listed in the error, so your firewall/port checking should be done from client to server.  See [http://www.likewise.com/resources/documentation_library/manuals/lwe/likewise-enterprise-guide.html#OpenOutboundPorts](http://www.likewise.com/resources/documentation_library/manuals/lwe/likewise-enterprise-guide.html#OpenOutboundPorts)

Justin

---

### Post by wlraider70 on 2009-07-09
I have hope.

My linux box when i use port checker is saying that many of these ports are closed.

How do i open ports?

---

