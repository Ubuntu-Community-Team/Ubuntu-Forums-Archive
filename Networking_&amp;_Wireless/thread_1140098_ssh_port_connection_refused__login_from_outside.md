---
title: "ssh port connection refused / login from outside"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by jamescoleman on 2009-04-27
Hey!

I'm having a problem with logging in to the computer in the basement using ssh. 
It's using ubuntu server 9.04.
I've opened the port, restarted, closed, opened again, and restarted the computer.
I can ssh into my laptop using putty and then when I try to ssh into the basement computer using my laptop, I get this message: "ssh: connection to host 192.168.1.65 
port 22: connection refused" I get the same message when using putty to directly connect to the computer in the basement. I can ssh from the basement computer to my laptop and my desktop computer when I'm running linux. 

I can't even scan the ports using nmap on the computer in the basement. When I did scan the ports on the loopback interface on the computer in the basement, I see the ports 22,53,80, and 5300 open. These are the ones that I want open but I don't know why 53 is open nor do I want it open. Could it be that the domain service is messing things up? If so, how can I shut it down?

I tried to make new ssh keys, delete the texts in the known hosts file in the ssh directory, and I removed the whole file. I thought a new file would have been made and it hasn't been made. Could it be that the computer in the basement is on a different domain? 

Maybe my network layout will help. The basement computer is directly connected to the dsl 2wire router. I have a 2924 switch connected to that router. The switch is in my room where I have my laptop and desktop. 


Now for the login from outside. I've opened the ssh port on the dsl router but I can't login. Maybe I'm doing it wrong. I type "ssh xxx.xxx.xxx.xxx" but nothing happens. Then I type "ssh [EMAIL="user@xxx.xxx.xxx.xxx"]user@xxx.xxx.xxx.xxx[/EMAIL]" and nothing still happens. The x equal the numbers of the outside ip address. I thought the router would direct the traffic to the computer because the router has me set the port only to one computer. 


I've been looking for information on both of these posts for a while but still can't be pointed in the correct direction.

---

### Post by rharriso on 2009-04-27
This may seem a like a simple suggestion but maybe you should see if you ssh support on your server is configured correctly or is running, maybe save your self some routing table trouble.

If you believe the problem is with your routing, you should check out the `route` command

[PHP]
route -n //see the routing table with numerical ip addresses
[/PHP]

there are a couple more command route add and route del if your feeling adventurous, check out the man pages. But I would doubt you would need to do either of these things.

---

### Post by jamescoleman on 2009-04-27
I've checked it out and it just shows 192.168.1.0 and 169.254.1.0.
I tried to add new ip addresses but it didn't work out so well.

---

### Post by bwilhiteforex on 2009-04-27
I'm not sure I'm understanding something...you are not able to ssh to the computer from behind the firewall, correct?

can you ping the computer?
ping -c 4 192.168.1.65

(And that is the correct ip right?)

---

### Post by jamescoleman on 2009-04-27
Correct. I get the responses back from the ping.

---

### Post by bwilhiteforex on 2009-04-27
ok, here's what I would do for starters:

1) Close any open ports on your router/firewall
2) change your sshd_config to enable logging in with only a password (also disable key authentication and any other very restrictive options you may  have)
3) sudo /etc/init.d/ssh restart (and make sure no errors occur there)
4) try to login using username@192.168.1.65
5) if that works, now switch back to your key authentication and then re-open your ports on your firewall/router

I'm no expert on ssh, but I've done this setup plenty of times, so I imagine we can figure this out.  I also have some good tutorial links if you'd like them.

---

### Post by jamescoleman on 2009-04-27
It still didn't work.... 
Maybe I need to reinstall the OS??? I know that sounds dumb but
nothing is working out for me. I can't even see the website on 
the computer in the basement.

---

