---
title: "script for netowk mangement"
date: 2013-05-05
forum: Networking &amp; Wireless
---

### Post by tomrip on 2013-05-05
im tryign to make a script to run ping, tace a network path to a target, remotely access a machine in a secure manner and allow you to look up the ip address of a domain name. i have no idea where to start.

---

### Post by Cheesemill on 2013-05-05
```
man ping
man traceroute
man ssh
man host
```
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

That should be a good start for you :)

---

### Post by tomrip on 2013-05-05
thanks for the replay. i am confused by what it means to write a script that does all this. Would someone just run this script and see results, or do they have to enter something? This is the entire text
For this problem you will need to design a script for network management. This script would be a tool that a network admin may have on a server or two to simplify work. It should follow good design principles.

The script should be able to accomplish the following tasks

[LIST]
[*]Run ping with a limited number (4-8) of packets
[*]Trace a network path to a target
[*]Remotely access a machine in a secure manner
[*]Allow you to look up the IP address of a domain name
[/LIST]
Im sorry for the silly questions, but i really dont know linux enough to know wht his means lol

---

### Post by sandyd on 2013-05-05
In Linux, scripts are run through a command line interpreter (shell). In Ubuntu, the default shell is bash.

If you wanted to run a bunch of commands, you would put them each on their own line in a file, and get bash to run it

Heres a good guide on how to do that -> [http://tldp.org/LDP/abs/html/sha-bang.html](http://tldp.org/LDP/abs/html/sha-bang.html)

---

### Post by wildmanne39 on 2013-05-05
Closed because homework is not a supported topic on the forum!

---

