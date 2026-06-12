---
title: "Firewall - IPtables"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by Harshall on 2013-01-20
Hi, 

Not sure if this is the correct place for this.. 

I am performing some tests on ubuntu 12.04 using netkit, netcat and IP tables.
 
my current setup is as follows:

4 Netkit machines:

A - Sending a text document only containing the letter "H" (Using Netcat)
B - Receiving the text document (Using Netcat)
C - TCP dump capture 
D - Firewall - (Custom IP table rules)

I  am trying to block the file transfer going from machine A to machine B  if the file contains the string "H", I am using the following commands:

iptables -A INPUT -m --string --algo bm --string "H" -j DROP
iptables -A OUTPUT -m --string --algo bm --string "H" -j DROP
iptables -A FORWARD -m --string --algo bm --string "H" -j DROP

But this does not seem to be doing anything at the moment, I would expect the file transfer to fail but its not...

Can someone please advice what I am doing wrong?, is this the right way to check the contents of a text file?

Kind Regards,
Harsh

---

### Post by howefield on 2013-01-20
Thread moved to the "*Networking & Wireless*"*[]("http://ubuntuforums.org/forumdisplay.php?f=336") *forum.

---

### Post by greg_ory on 2013-01-20
I was not aware that this is actually possible but I might found something what could help as it seems that is not possible by default(Don't take me for granted on that)

[http://www.symantec.com/connect/articles/iptables-linux-firewall-packet-string-matching-support](http://www.symantec.com/connect/articles/iptables-linux-firewall-packet-string-matching-support)

-Greg

---

### Post by Doug S on 2013-01-20
@ greg_ory : It is true that the string module did not used to be available in default systems. One had to re-compile the kernel for it to be available. However, that is no longer the case (I think). The article you linked to is pretty old.
 
@ Harshall : I think the syntax you listed is not correct, and you should have seen iptables complain when you tried to load those rules. I think it should be:```
iptables -A INPUT -m string --algo bm --string "H" -j DROP
```At least, that is what I needed to get the rule to load on my test computer (with sudo prefix, of course). Also, the command seems to be working for me.
 
I do not understand why you would be running the iptables rules set on computer "D". Shouldn't it be running on computer "B"? Shouldn't tcpdump also be running on computer "B". I don't understand why you even have computers "C" and "D" for this test.

---

### Post by Harshall on 2013-01-21
> **Doug S said:**
> @ greg_ory : It is true that the string module did not used to be available in default systems. One had to re-compile the kernel for it to be available. However, that is no longer the case (I think). The article you linked to is pretty old.
 
@ Harshall : I think the syntax you listed is not correct, and you should have seen iptables complain when you tried to load those rules. I think it should be:```
iptables -A INPUT -m string --algo bm --string "H" -j DROP
```At least, that is what I needed to get the rule to load on my test computer (with sudo prefix, of course). Also, the command seems to be working for me.
 
I do not understand why you would be running the iptables rules set on computer "D". Shouldn't it be running on computer "B"? Shouldn't tcpdump also be running on computer "B". I don't understand why you even have computers "C" and "D" for this test.
Hi Doug,

Thanks for replying.

Yeah sorry the syntax I wrote was wrong.

Below are the rules that I have entered and are accepted:

iptables -A INPUT -p tcp -m string --string "H" --algo bm -j DROP
iptables -A OUTPUT -p tcp -m string --string "H" --algo bm -j DROP
iptables -A FORWARD -p tcp -m string --string "H" --algo bm -j DROP

I am not using physical machines, I am using netkit which creates a virtual environment so the reason I have 4 virtual machines are:

[B]Machine A:  This is used to send the text document using "netcat", specific command: cat test1 | nc 192.168.1.2 1234 -q 10

The above command "cat's" the content of "test1" which only contains letter "H" and "pipes" it to IP "192.168.1.2" listening on port "1234" 

[/B] IP: 192.168.1.1
Gateway: 192.168.1.100

[B]Machine B: This is used to listen on port 1234 for the file, specific command: nc -l -p 1234 > file1

The above command listens for traffic on port 1234 and creates a text file named "file1" with the received content.

[/B]IP: 192.168.1.2
Gateway: 192.168.1.100

[B]Machine C: TCP dump capture, specific command: tcpdump -i eth0 -w test

[/B]IP: 192.168.1.3
Gateway: 192.168.1.100

[B]Machine D: Firewall - Implementing IPtable rules

[/B]IP: 192.168.1.100

All of the virtual machines are connected on **eth0**

Is the above setup that I have incorrect? I am really confused as the rules are being accepted but the file is still getting transferred.

My current version of iptables is: iptables v1.4.1.1

How did you get this test working? were you able to block the file transfer?

P.S What I am trying to do is possible right? lol been trying it for few days not getting anywhere :(

Hope you can point me to the right direction.

Thank you.
Harshal

---

### Post by Doug S on 2013-01-21
By the way, I forgot to notice that yesterday was your first posting, and to say welcome to Ubuntu forums.
 
I think the problem with your test is that the packets do not have to flow through or involve computer "D" at all. Even though computer "D" is your gateway computer for the 192.168.1.0 sub-net, it doesn't have to be involved with traffic between two computers ("A" and "B" in this case) on the local sub-net. I am not familiar with netkit, but I assume it has implemented a virtual switch for the local sub-net.
 
In the senario you described, I think you need the iptables rule to reside in Computer "B". I also think you only need one rule on the INPUT chain.> How did you get this test working? were you able to block the file transfer?I added the one rule to the INPUT chain of my test computer. The computer is normally a headless server that I communicate with via ssh. Of course, with such a simple trigger string in the rule, my ssh session became unstable and died. I thought that was good enough for my test.
 
O.K. so re-testing just now: I made a longer string to prevent false triggering of the rule. On my "s15" computer, I did:```
sudo iptables -A INPUT -m string --algo bm --string "HzDxFvGb" -j DROP
```On another computer on the same local sub-net I entered:```
doug@doug-64:~$ [COLOR=red]wget http://s15.smythies.com/HzDxFvGb[/COLOR]
--2013-01-21 07:32:10--  http://s15.smythies.com/HzDxFvGb
Resolving s15.smythies.com (s15.smythies.com)... 192.168.111.112
Connecting to s15.smythies.com (s15.smythies.com)|192.168.111.112|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.
... many more tries deleted ...
--2013-01-21 07:36:06--  (try:10)  http://s15.smythies.com/HzDxFvGb
Connecting to s15.smythies.com (s15.smythies.com)|192.168.111.112|:80... connected.
HTTP request sent, awaiting response... ^C

```And on the "s15" computer, I observed the packet counters:```
doug@s15:~$ [COLOR=red]sudo iptables -v -x -n -L[/COLOR]
Chain INPUT (policy ACCEPT 213 packets, 17021 bytes)
    pkts      bytes target     prot opt in     out     source               destination
      [COLOR=red]90[/COLOR]    15840 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            STRING match  "HzDxFvGb" ALGO name bm TO 65535
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
Chain OUTPUT (policy ACCEPT 156 packets, 22598 bytes)
    pkts      bytes target     prot opt in     out     source               destination

```And, for completeness, an example of a non-blocked wget of a nonexistent file:```
doug@doug-64:~$ [COLOR=red]wget http://s15.smythies.com/bla[/COLOR]
--2013-01-21 07:42:13--  http://s15.smythies.com/bla
Resolving s15.smythies.com (s15.smythies.com)... 192.168.111.112
Connecting to s15.smythies.com (s15.smythies.com)|192.168.111.112|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-01-21 07:42:13 ERROR 404: Not Found.

```Hope this helps.

---

### Post by Harshall on 2013-01-21
Hi Doug,

Thanks for the welcome!

Yeah I was applying the rules in the wrong place...lol

The 2nd test that you did where you made a longer string.. **"HzDxFvGb" **did you receive the file with the letters **"HG" **removed? so did you receive [B]"zDxFvGb"?
[/B]
As I tried the same thing but the file received is empty.

I also noticed if the letters are "hg" (lower case) then the file will still be allowed through.

Do you think I may have to use the **"u32"** module and not the string module? for this to work?

Thanks!

---

### Post by Doug S on 2013-01-21
> The 2nd test that you did where you made a longer string.. **"HzDxFvGb" **did you receive the file with the letters **"HG" **removed? so did you receive **"zDxFvGb"?**
Sorry, I don't understand the question. I only expect packets with the exact string pattern to be dropped, nothing more, nothing less.> I also noticed if the letters are "hg" (lower case) then the file will still be allowed through.
Yes, I expect the string pattern match to be case sensitive. Using my previous example:```
doug@doug-64:~$ wget http://s15.smythies.com/[COLOR=red]h[/COLOR]zDxFvGb
--2013-01-21 14:29:40--  http://s15.smythies.com/hzDxFvGb
Resolving s15.smythies.com (s15.smythies.com)... 192.168.111.112
Connecting to s15.smythies.com (s15.smythies.com)|192.168.111.112|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-01-21 14:29:40 ERROR 404: Not Found.
```Meaning there was no dropped packets and the wget request got through and a file not found error was returned, as expected.> Do you think I may have to use the **"u32"** module and not the string module? for this to work?Well, I don't know what you are actually trying to do for real, not for tests, so it is hard to comment. However, if your trigger bytes are at known offsets in the packets then certainly the u32 method would be a better way to go, requiring less compute power than a string search of the entire packet.

---

### Post by Harshall on 2013-01-22
Hi,

Sorry to confuse you..

I have changed the rule from DROP to ACCEPT:

[B]iptables -A INPUT -m string --string "HG" --algo bm -j ACCEPT

[/B]Now I am trying to block everything else except the string **"HG"  **by using the following rules:

[B]iptables -A INPUT -m string --string "HG" --algo bm -j ACCEPT
iptables -A INPUT -m string --string ! "HG" --algo bm -j DROP [/B]

After applying those rules, I am unable to send anything to the machine...I also tried 

[B]iptables -A INPUT -p tcp --dport 1234 -m string --string "HG" --algo bm -j ACCEPT
iptables -A INPUT -p tcp --dport 1234 -m string --string ! "HG" --algo bm -j DROP [/B]
This again did not work...all the rules are being accepted without throwing any errors.

Not sure where I am going wrong..

---

### Post by Doug S on 2013-01-22
I think you need to keep in mind that it takes several packets, not all of which are payload packets, containing "HG", to make a complete TCP session. Since you are dropping all packets, except the actual payload packet, yes it doesn't work. Example:```
doug@s15:~/temp1$ [COLOR=red]sudo tcpdump -n -nn -tttt -i eth0 port 1234[/COLOR]
[sudo] password for doug:
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
2013-01-22 14:09:19.289532 IP 192.168.111.1.56512 > 192.168.111.112.1234: Flags [S], seq 1765651562, win 14600, options [mss 1460,sackOK,TS val 734334971 ecr 0,nop,wscale 6], length 0 [COLOR=red]<<< Open a TCP session, "SYN" packet[/COLOR]
2013-01-22 14:09:19.289686 IP 192.168.111.112.1234 > 192.168.111.1.56512: Flags [S.], seq 2367102133, ack 1765651563, win 14480, options [mss 1460,sackOK,TS val 91151194 ecr 734334971,nop,wscale 7], length 0 [COLOR=red]<<< O.K. SYN ACK packet[/COLOR]
2013-01-22 14:09:19.289796 IP 192.168.111.1.56512 > 192.168.111.112.1234: Flags [.], ack 1, win 229, options [nop,nop,TS val 734334971 ecr 91151194], length 0
2013-01-22 14:09:19.289880 IP 192.168.111.1.56512 > 192.168.111.112.1234: Flags [P.], seq 1:4, ack 1, win 229, options [nop,nop,TS val 734334971 ecr 91151194], length 3  [COLOR=red]<<< Actual payload packet[/COLOR]
2013-01-22 14:09:19.289900 IP 192.168.111.112.1234 > 192.168.111.1.56512: Flags [.], ack 4, win 114, options [nop,nop,TS val 91151194 ecr 734334971], length 0
2013-01-22 14:09:[COLOR=red]29.[/COLOR]290281 IP 192.168.111.1.56512 > 192.168.111.112.1234: Flags [F.], seq 4, ack 1, win 229, options [nop,nop,TS val 734337471 ecr 91151194], length 0 [COLOR=red]<<< The terminate request, after the 10 second delay[/COLOR]
2013-01-22 14:09:29.290372 IP 192.168.111.112.1234 > 192.168.111.1.56512: Flags [F.], seq 1, ack 5, win 114, options [nop,nop,TS val 91153694 ecr 734337471], length 0 [COLOR=red]<<< O.K. [/COLOR]
2013-01-22 14:09:29.290503 IP 192.168.111.1.56512 > 192.168.111.112.1234: Flags [.], ack 2, win 229, options [nop,nop,TS val 734337471 ecr 91153694], length 0
```

---

### Post by Harshall on 2013-01-25
> **Doug S said:**
> I think you need to keep in mind that it takes several packets, not all of which are payload packets, containing "HG", to make a complete TCP session. Since you are dropping all packets, except the actual payload packet, yes it doesn't work. Example:```
doug@s15:~/temp1$ [COLOR=red]sudo tcpdump -n -nn -tttt -i eth0 port 1234[/COLOR]
[sudo] password for doug:
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
2013-01-22 14:09:19.289532 IP 192.168.111.1.56512 > 192.168.111.112.1234: Flags [S], seq 1765651562, win 14600, options [mss 1460,sackOK,TS val 734334971 ecr 0,nop,wscale 6], length 0 [COLOR=red]<<< Open a TCP session, "SYN" packet[/COLOR]
2013-01-22 14:09:19.289686 IP 192.168.111.112.1234 > 192.168.111.1.56512: Flags [S.], seq 2367102133, ack 1765651563, win 14480, options [mss 1460,sackOK,TS val 91151194 ecr 734334971,nop,wscale 7], length 0 [COLOR=red]<<< O.K. SYN ACK packet[/COLOR]
2013-01-22 14:09:19.289796 IP 192.168.111.1.56512 > 192.168.111.112.1234: Flags [.], ack 1, win 229, options [nop,nop,TS val 734334971 ecr 91151194], length 0
2013-01-22 14:09:19.289880 IP 192.168.111.1.56512 > 192.168.111.112.1234: Flags [P.], seq 1:4, ack 1, win 229, options [nop,nop,TS val 734334971 ecr 91151194], length 3  [COLOR=red]<<< Actual payload packet[/COLOR]
2013-01-22 14:09:19.289900 IP 192.168.111.112.1234 > 192.168.111.1.56512: Flags [.], ack 4, win 114, options [nop,nop,TS val 91151194 ecr 734334971], length 0
2013-01-22 14:09:[COLOR=red]29.[/COLOR]290281 IP 192.168.111.1.56512 > 192.168.111.112.1234: Flags [F.], seq 4, ack 1, win 229, options [nop,nop,TS val 734337471 ecr 91151194], length 0 [COLOR=red]<<< The terminate request, after the 10 second delay[/COLOR]
2013-01-22 14:09:29.290372 IP 192.168.111.112.1234 > 192.168.111.1.56512: Flags [F.], seq 1, ack 5, win 114, options [nop,nop,TS val 91153694 ecr 734337471], length 0 [COLOR=red]<<< O.K. [/COLOR]
2013-01-22 14:09:29.290503 IP 192.168.111.1.56512 > 192.168.111.112.1234: Flags [.], ack 2, win 229, options [nop,nop,TS val 734337471 ecr 91153694], length 0
```

Hi,

Thank you, yep thats right, I tried the test with UDP and it works without a problem.

Is their a way to get this working using TCP?

Thanks

---

### Post by Doug S on 2013-01-25
> Is their a way to get this working using TCP?
I don't know. I assume the example of this thread is somehow simplified from what you are really wanting to do. Perhaps explain the real case.

---

### Post by Harshall on 2013-02-22
> **Doug S said:**
> I don't know. I assume the example of this thread is somehow simplified from what you are really wanting to do. Perhaps explain the real case.


Sorry for not replying, been away from this for a while.

My main objective is to write a TCP chat server and to be able to authenticate the connection using IPTABLES string module. Trying to create a covert authentication channel.

I am currently trying this at a very low level using netcat to see if it's possible. 

For e.g. if the message contains the "Secret message" then the connection can be authenticated.

I have managed to fix the problem, I was facing earlier by changing the rule a little:

iptables -A INPUT -m string --string ! "123" --algo bm -m state --state ESTABLISHED -j DROP

This drops all packets if the packets do not contain the "secret string"..

The problem that I am currently facing is that I cannot get a continuous chat going using netcat.

I tried to create a simple chat server using netcat:

**MACHINE A:  **nc 192.168.1.2 1234  
**MACHINE B: **nc -l -p 1234 **(This is where the IPTABLES string rule is applied)**

**123 **is the secret string.

Test 1: if machine A sends **123** to machine B, then machine B receives the string **123 **and it can send only one message back, if it send more than 1 then the other messages are stuck in a queue and machine A will not receive them until, machine A type the secret string **123..**.

Test 2: if machine B sends a message to machine Afirst then machine A does not receive the message until machine A types **123** 

Test 3: if machine A sends something which is not the "secret string" for e.g **321 **Machine B does not receive this as expected... but then if machine A then sends **123 **this time which is the secret string, the message still does not go through to Machine B.

I think when the rule is not matched, the connection is being dropped altogether

Cannot figure out a way around this, hope you can suggest some ideas.

Thanks

---

### Post by Doug S on 2013-02-24
Thanks for the description of what you are really trying to do.
I do not think you can make this work with TCP protocol.
You should study TCP protocol details. [One reference]("http://en.wikipedia.org/wiki/Transmission_Control_Protocol").

---

### Post by Harshall on 2013-02-25
Thanks for the reply, are you sure this is not possible? as it is partially working, I think I may need conditional IP table rules which would say if the "Secret string" is been found then do the following, e.g. keep the connection open for 10 minutes or so.

Do you think something like this would work or are you confident that this is not possible?

---

### Post by Doug S on 2013-02-25
> **Harshall said:**
> Thanks for the reply, are you sure this is not possible? as it is partially working, I think I may need conditional IP table rules which would say if the "Secret string" is been found then do the following, e.g. keep the connection open for 10 minutes or so.
 
Do you think something like this would work or are you confident that this is not possible?I am not 100% sure, no. However, I do not think it could utlimately be done at the packet level and with iptables. The issue is at the next level up where the payload stream is being re-contructed. Read the reference I gave in my last post, and other references you can find on the TCP/IP protocol subject, to understand better.

---

### Post by Harshall on 2013-02-27
Hi,

Thanks a lot for replying, really appreciate your suggestions. got another question hope you don't mind.

Is it possible to have a itpable rule to remember the ipaddress of the machine and keep it saved for a certain amount of time?

I am now creating user defined chain -  which can be seen as being similar to if statements in c.

# iptables -N stringmatch

iptables -A INPUT -m state --state ! "xyz" --algo bm -m state --state

---

### Post by Harshall on 2013-02-27
Hi,

Thanks a lot for replying, really appreciate your suggestions. got another question hope you don't mind.

Is it possible to have a itpable rule to remember the ipaddress of the machine and keep it saved for a certain amount of time?

I am now creating user defined chain -  which can be seen as being similar to if statements in c.

# iptables -N STRING-MATCH

# iptables -A INPUT -m state --state "xyz" --algo bm -m state --state ESTABLISHED -j STRING-MATCH

So if the above rule matches it will use the -j switch to go to the stringmatch chain.

I can then accept the packet if it contains the ip address (which I can define, as shown below)

# iptables -A STRING-MATCH -s 192.168.1.1 -j ACCEPT

I was wondering if there is anything within iptable rules that will actually remember the ip address once the rule matches and stores it for 10 - 5 mins for example?

is that possible?

I could not find anything in regards to saving the incoming ip address.

Thanks,
Harshall

---

### Post by Doug S on 2013-02-27
Hi Harshall,
 
Maybe you could use the "recent" module to achieve what you want. Something like this (I didn't check the syntax, or test it):```
iptables -A INPUT -m recent --update --hitcount 1 --seconds 600 --name STRING-MATCH -j ACCEPT
iptables -A INPUT -m state --state "xyz" --algo bm -m state --state ESTABLISHED -m recent --set --name STRING-MATCH -j ACCEPT
``` Once the secret password string has been supplied then all packets are accepted with a 10 minute timeout. You might prefer to narrow it down some by requiring ESTABLISHED state for that line also, it is up to you.

---

### Post by Harshall on 2013-03-01
Hi Doug,

I have the following rules in place now.

Drop all rules first:

# iptables -A INPUT -j DROP
# iptables -A OUTPUT -j DROP
# iptables -A FORWARD -j DROP

Creating a custom chain:

# iptables -N STRING-MATCH

Jumping to the chain:

# iptables -A INPUT -j STRING-MATCH 

Using the recent match module:

# iptables -A INPUT -m recent --update --hitcount 1 --seconds 120 --name STRING-MATCH -j ACCEPT
# iptables -A INPUT -m state --state "xyz" --algo bm -m state --state ESTABLISHED -m recent --set --name STRING-MATCH -j ACCEPT

I  have been trying to test this using netcat, but no packets are going  through. I have been reading up on this module and in theory this module  seems like it has the options which can help me do what I need, but i'm  not sure if i'm testing this correctly.

just for testing purposes I changed the connection time from 10 mins to 2 mins.

I assume only way I will know it's working is that if the string "xyz" goes through to the other machine.

Thanks,
Harshall

---

### Post by Doug S on 2013-03-01
Harshall,

STRING-MATCH is the name of the list of ip addresses that "recent" will keep, not the name of a chain. Delete the chain declaration and the jump to it.
Also you need to complete two way communications for TCP IP to work, even if there is no payload packets going out. Change your OUTPUT default DROP to ACCEPT.

---

### Post by Harshall on 2013-03-03
[FONT=arial]Hi Doug,

I tried the following rules:
[B]
# iptables -P INPUT DROP
# iptables -P OUTPUT ACCEPT
# iptables -P FORWARD DROP

# iptables -A INPUT -m recent --update --hitcount 1 --seconds 120 --name STRING-MATCH -j ACCEPT
#  iptables -A INPUT -m string --string "xyz" --algo bm -m state --state  ESTABLISHED -m recent --set --name STRING-MATCH -j ACCEPT[/B]

after applying the following rules no packets are going through, the input policy is dropping the packets.
I looked at /proc/net/ipt_recent/STRING-MATCH but the file is also empty.

I  captured the traffic without any rules and started a conversation using  netcat listener and server, before the packet goes through it does syn,  syn ack, ack as expected then it does a PSH (contains the payload)  after the initial handshake it only does PSH, ACK and ACK.

Can i input the rules to say accept the following flags.. something similar to the example shown below?
[/FONT]
[FONT=arial]# Initial stage of the tcp connection SYN/ACK handshake

[B] iptables -A INPUT -p tcp --tcp-flags SYN,ACK NONE -m recent --name STRING-MATCH --set -j ACCEPT
[/B][/FONT][FONT=arial][B]iptables -A INPUT -p tcp --tcp-flags SYN,ACK  ACK -m recent --name STRING-MATCH --set -j ACCEPT 
[/B][/FONT][FONT=arial]
# Middle stage of tcp connection where data transportation takes place.

[B] iptables -A INPUT -p tcp --tcp-flags PSH,ACK NONE -m recent --name STRING-MATCH --update -j ACCEPT
iptables -A INPUT -p tcp --tcp-flags ACK, PSH NONE -m recent --name STRING-MATCH --update -j ACCEPT


[/B][/FONT]

---

### Post by Harshall on 2013-03-04
Just a quick update, I changed the rule to allow everything just to see if the rules are being hit or not.

below is the verbose output:


 pkts bytes target     prot opt in     out     source               destination         
   20  1088 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           recent: UPDATE seconds: 30 hit_count: 1 name: STRING-MATCH side: source 
    1    56 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           STRING match "xyz" ALGO name bm TO 65535 state ESTABLISHED recent: SET name: STRING-MATCH side: source 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 21 packets, 1129 bytes)
 pkts bytes target     prot opt in     out     source               destination   

Above you can see that the rule is being matched and the packets are being accepted based on the rule, I changed the seconds to 30, but after 30 seconds the packets are not being dropped.

Harshal

---

