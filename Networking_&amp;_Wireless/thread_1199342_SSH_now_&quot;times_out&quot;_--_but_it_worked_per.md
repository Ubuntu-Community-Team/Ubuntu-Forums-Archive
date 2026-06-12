---
title: "SSH now &quot;times out&quot; -- but it worked perfectly yesterday"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by jespes on 2009-06-28
Hi,
noob here. I have a basic SSH server running on a 9.04 machine. It  has worked perfectly for quite a long time. But today it says "operation timed out" every time I attempt to access it. 

The only thing i can think of is: Today I installed a bunch of updates that showed up in the update manager...

Any suggestions on how to troubleshoot? I've tried the obvious things (rebooted the machine; doublechecked that that my DynDNS is updating properly; restarted SSH; checked router to be sure port forwarding was still on).

Any ideas welcome! many thanks.
jp

---

### Post by Boondoklife on 2009-06-28
> **jespes said:**
> Hi,
noob here. I have a basic SSH server running on a 9.04 machine. It  has worked perfectly for quite a long time. But today it says "operation timed out" every time I attempt to access it. 

The only thing i can think of is: Today I installed a bunch of updates that showed up in the update manager...

Any suggestions on how to troubleshoot? I've tried the obvious things (rebooted the machine; doublechecked that that my DynDNS is updating properly; restarted SSH; checked router to be sure port forwarding was still on).

Any ideas welcome! many thanks.
jp

Have you tried to connect to it from the local network? how about from the machine itself (localhost)?

---

### Post by jespes on 2009-06-28
Thanks for the suggestion. I just tried "ssh localhost" and got: "connect to host localhost port 22: Connection refused"

That seems strange -- because i've got SSH set up to use a much higher port, not 22. Does that offer a clue? I've also checked sshd_config and it is still set up to listen to my non-standard port.

---

### Post by Boondoklife on 2009-06-28
try specifying the port  '-p ###'

---

### Post by jespes on 2009-06-28
Ah, thanks. 

Okay i did "ssh localhost -p ###" and got this (where ### is the actual port number of course):

[B]The authenticity of host '[localhost]:### ([127.0.0.1]###)' can't
be established.
RSA key fingerprint is ((long number here)).
Are you sure you want to continue connecting (yes/no)?[/B]

I said "yes" and got this:

[B]Warning: Permanently added '[localhost]:### (RSA) to the list of
known hosts. Write failed: Broken pipe.[/B]

---

### Post by Boondoklife on 2009-06-29
> **jespes said:**
> Ah, thanks. 

Okay i did "ssh localhost -p ###" and got this (where ### is the actual port number of course):

[B]The authenticity of host '[localhost]:### ([127.0.0.1]###)' can't
be established.
RSA key fingerprint is ((long number here)).
Are you sure you want to continue connecting (yes/no)?[/B]

I said "yes" and got this:

[B]Warning: Permanently added '[localhost]:### (RSA) to the list of
known hosts. Write failed: Broken pipe.[/B]

This is interesting and can be found in other forums online but with no solution, try using verbose mode 'ssh -v hostname' to track down more info.

---

### Post by kevdog on 2009-06-29
I thought the syntax was something like:

ssh -p 22 localhost

---

### Post by Boondoklife on 2009-06-29
> **kevdog said:**
> I thought the syntax was something like:

ssh -p 22 localhost


Either way will work, the command is smart enough to know what you want.

---

### Post by jespes on 2009-07-07
thanks to all for your help. i figured out the problem: somehow, my ubuntu machine's internal (local) IP address got changed!

i have no idea why, or how, that happened. i didnt even think that was possible. doesn't your router assign local IP addresss (eg, 10.0.1.XX) then just stick with them? 

anyhoo.  i updated the port forwarding on my router to reflect the machine's new local IP address, and now ssh is working again.  what a pain that was.

thanks again for weighing in on this strange problem.

---

