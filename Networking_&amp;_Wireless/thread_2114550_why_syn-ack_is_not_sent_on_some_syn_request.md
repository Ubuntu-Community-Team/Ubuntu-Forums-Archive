---
title: "why syn-ack is not sent on some syn request"
date: 2013-02-10
forum: Networking &amp; Wireless
---

### Post by xiao2ge on 2013-02-10
Folks, Happy Chinese New Year!!
 
Although I am not a linux/ubuntu newbie, but once a while I still run into situations that I feel like I am one. I hope this forum can help me to solve this problem.
 
The problem is my ubuntu server (10.6.194.200 on port 50004) sends tcp syn-ack in respond to one tcp syn request (from 10.6.194.10) but not the other (from 10.6.194.35).
 
Can someone help me to understand why?
 
below is the tcpdump summary:
 
08:26:16.837558 IP 10.6.194.10.36726 > 10.6.194.200.50004: Flags [S], seq 1054246829, win 14600, options [mss 1460,sackOK,TS val 1158853290 ecr 0,nop,wscale 7], length 0
08:26:16.837573 IP 10.6.194.200.50004 > 10.6.194.10.36726: Flags [S.], seq 2574113174, ack 1054246830, win 14600, options [mss 1460,nop,nop,sackOK], length 0
08:26:16.838329 IP 10.6.194.10.36726 > 10.6.194.200.50004: Flags [.], ack 1, win 14600, length 0
08:26:20.337263 IP 10.6.195.35.15264 > 10.6.194.200.50004: Flags [S], seq 2953761099, win 5840, options [mss 1460,nop,nop,sackOK,nop,wscale 7], length 0
08:26:23.337957 IP 10.6.195.35.15264 > 10.6.194.200.50004: Flags [S], seq 2953761099, win 5840, options [mss 1460,nop,nop,sackOK,nop,wscale 7], length 0
08:26:29.337135 IP 10.6.195.35.15264 > 10.6.194.200.50004: Flags [S], seq 2953761099, win 5840, options [mss 1460,nop,nop,sackOK,nop,wscale 7], length 0
08:26:45.478501 IP 10.6.194.10.36726 > 10.6.194.200.50004: Flags [F.], seq 1, ack 1, win 14600, length 0
08:26:45.478588 IP 10.6.194.200.50004 > 10.6.194.10.36726: Flags [.], ack 2, win 14600, length 0
08:26:45.979060 IP 10.6.194.200.50004 > 10.6.194.10.36726: Flags [F.], seq 1, ack 2, win 14600, length 0
08:26:45.979426 IP 10.6.194.10.36726 > 10.6.194.200.50004: Flags [.], ack 2, win 14600, length 0
 
Any answer or analysis is appretiated.

---

### Post by Doug S on 2013-02-10
Is 10.6.195.35 being blocked by some iptables rule or other deny rule at 10.6.194.200?
Is 10.6.[COLOR=red]195[/COLOR].XXX considered to be some other subnet than 10.6.[COLOR=red]194[/COLOR].XXX that 10.6.194.200 doesn't like?
I notice some different options in the two sources of SYN requests, but I didn't look deeper to understand if it matters or not.
 
Oh,... By the way, Welcome to Ubuntu forums.

---

### Post by xiao2ge on 2013-02-11
Doug, thanks for your reply, and thanks for pointing out my typo on 10.6.194.35 (should be 10.6.195.35) in my previous message.
 
It does seem like my server has some preference treatment based on its own interfaces to the incoming tcp syn request.
 
My server has two NIC interfaces:
eth4 on the 10.6.194.0 subnet with 2 IPs 10.6.194.11 and 10.6.194.200.
eth3 on the 10.6.195.0 subnet with 1 IP 10.6.195.13.
 
Before I brough up the eth3 interface (10.6.195.13) the eth4 answers the tcp syn request from 10.6.195.35, regardless which IP between 10.6.194.11 or 10.6.194.200. But after I brought up the eth3 interface, the eth4 stopped responding to the tcp sync from 10.6.195.35. However, the eth3 interface with 10.6.195.13 will answer, if the tcp syn request is pointed to it.
 
See the below tcpdump where the first entry tcp syn is pointed to 10.6.194.11 and got no answer, while the starting from second entry the same tcp syn is pointed to 10.6.195.13 and it is answered.
 
11:46:08.056653 IP 10.6.195.35.12232 > 10.6.194.11.50004: Flags [S], seq 3763925109, win 5840, options [mss 1460,nop,nop,sackOK,nop,wscale 7], length 0
11:46:10.929473 IP 10.6.195.35.12233 > 10.6.195.13.50004: Flags [S], seq 3762190368, win 5840, options [mss 1460,nop,nop,sackOK,nop,wscale 7], length 0
11:46:10.929487 IP 10.6.195.13.50004 > 10.6.195.35.12233: Flags [S.], seq 214507397, ack 3762190369, win 14600, options [mss 1460,nop,nop,sackOK], length 0
11:46:10.930597 IP 10.6.195.35.12233 > 10.6.195.13.50004: Flags [.], ack 1, win 5840, length 0
11:46:10.930953 IP 10.6.195.35.12233 > 10.6.195.13.50004: Flags [P.], seq 1:18, ack 1, win 5840, length 17
11:46:10.930960 IP 10.6.195.13.50004 > 10.6.195.35.12233: Flags [.], ack 18, win 14600, length 0

This solution solved my problem for the application. It also gives some explaination/solution to the misterious tcp syn/syn-ack behavior.
 
But as to how to configure the NICs properly so that any IP on the multi-NIC system will answer tcp syn, I still don't have an answer yet.

---

### Post by Doug S on 2013-02-11
I will have to defer to others to help you.
 
I would never apply two IP addresses to one NIC card.
 
You will also have to create routes between the two sub-nets and maybe bridge them somehow. Anyway, I am not familiar with such things as I haven't had to do them for myself.

---

