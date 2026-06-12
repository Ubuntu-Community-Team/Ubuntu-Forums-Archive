---
title: "Port forwarding behind Linksys router"
date: 2011-10-05
forum: Networking &amp; Wireless
---

### Post by knof on 2011-10-05
I have Linksys router. Behind this router i have 2 machines, running on Ubuntu 11.04. 1. is a server machine on local IP 192.168.1.125 and is running Apache server on por 80.
Port 80 forwarding is done on Linksys. Works fine.
 
On the same machine on port 2000 i have citadel server running. So, if i want to connect to my web server to see web site i type into browser [http://mydomain](http://mydomain). If i want connect to citadel server wich run on port 2000 i wrote [http://mydomain:2000](http://mydomain:2000)
 
Now i want to run citadel server on another local machine on port 2000, IP 192.168.1.126 (i have DHCP on Linksys), but don't want to redirect with Linksys. I want to redirect with a 1. Ubuntu server. 
 
Suggestions? Iptables, ufw, firestarter, virtualhost?
Do i need 2nd ethernet device?
 
I need this solution wery fast,

---

### Post by jonobr on 2011-10-05
Im guessing Iptables, and Im thinking pre-routing on the current machine using something like this (assuming your using tcp and eth0)

```
iptables -t nat -A PREROUTING -p tcp  -i eth0 --dport 2000 \
-j DNAT --to 192.168.1.126:2000
```


I recall playing around with this before and am kicking myself I didnt make note of it.

---

### Post by knof on 2011-10-06
Did not work. :( I think this is wery close, but not exact....
I need some fine tuning on this one.
 
Any other suggestions?

---

### Post by Dangertux on 2011-10-06
Try something with iptables along these lines it's the same thing just a single addition.

```

iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 2000 -j DNAT --to 192.168.1.126:2000
iptables -A FORWARD -p tcp -i eth0 -d 192.168.1.126 --dport 2000 -j ACCEPT

```

should fix it

---

### Post by jonobr on 2011-10-06
Thanks Dangertux,

iptables aint my strong pointpoint, but its nice to know I wasnt WAY off the reservation ;-)

---

### Post by knof on 2011-10-06
I tried with this settings above, but still got no luck. Without this lines i get connection to port 2000 on local machine. When i add this two lines into file i get nothing. Browser say's that "cannot display this site" like when server is not online.
I think, that problem is, that i have: 1. Linksys router (DHCP), and then on this router connected both machines with assigned IP's from router wich are: 1. 192.168.1.125 and 2. 192.168.1.126.
I'm wondering if it's possible to forward or reverseproxy this assigned local IP-port to another IP-port, with only one eth0 network card on 1. machine, from wich i want to forward?

---

### Post by jonobr on 2011-10-06
interesting,

Im guessing your packet from the router to host A is forwarded to host B, the response is sent back to host A which doesn't know what to do with it and the browser times out. I think that makes sense.

Before looking at that , i would verify the initial forward is working
Running tcpdumo to view the initial forward would be a good idea.

maybe   something like

```
 tcpdump -v -i eth0 port 2000 dst 192.168.1.126
```

If you see a packet from this filter when connecting, you know the forward is working.


I think you need another set of rules for the return response
The response would have to identify that the source port being used is 2000, running a wireshark may show the exact thing to trigger the iptables mapping
Im guessing 2000 will be the source port? Assuming 1.1 is the router




```

iptables -t nat -A PREROUTING -p tcp -i eth0 --sport 2000 -j DNAT --to 192.168.1.1
iptables -A FORWARD -p tcp -i eth0 -d 192.168.1.1 --dport 2000 -j ACCEPT

```

Again, the above is a guess, recommend that you review the traces to refine the iptables statement

---

### Post by Doug S on 2011-10-06
I suspect that in a single NIC card system, it doesn't know what do to with packets that would otherwise hit this rule:```
sudo iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 2000 -j DNAT --to 192.168.1.126:2000
```The interesting thing is that no error is given when the command is entered (at least on my test system, which is an older system (6.06)). I also get an error when I try to observe the nat table, because it isn't there. (I'll see about force loading the forwarding module).
jonobr: on my test system, I looked with tcpdump and I don't see the packets being sent on. I'll keep looking at it, just thought I would give an intermediate update.
 
knof: what do you get for this:```
cat /proc/sys/net/ipv4/ip_forward
```(I get 0, and I cann't seem to set it to 1)

---

### Post by knof on 2011-10-06
I also get 0.
 
And for: "tcpdump -v -i eth0 dst port 2000" , i get "mystaticproviderIP_and_domainname4259 > 192.168.1.125.cisco-sccp: flags [S], ck sum 0xb918correct), seq 1557754031, win 65535, options [mss 1460,nop,nop,sackOK], length 0"
 
Maybe firewall block those ports?
Maybe i need to setup iptables on destination (2.) server too?

---

### Post by jonobr on 2011-10-06
tcpdump results seems to show the packet getting to the first machine (125) but not being forward on,
If iptables were changing the packet,
you would mostly likely see a second packet to 126 with dst port 2000

try 

```
iptables -L -v
``` see if it shows anything of interest being seen by iptables

---

### Post by knof on 2011-10-06
Nop, no activity at all for port 2000, not for 192.168.1.125 or 192.168.1.126.

---

### Post by jonobr on 2011-10-06
odd,

packets are arriving given the line 

[QUOTE]tcpdump -v -i eth0 dst port 2000" , i get "mystaticproviderIP_and_domainname4259 > 192.168.1.125.cisco-sccp: flags [S], ck sum 0xb918correct), seq 1557754031, win 65535, options [mss 1460,nop,nop,sackOK], length 0"[/QOUTE]

Makes me think either the iptables is not working or the rules arent defined.

Do you have other rules already in there that may be cuasing this trouble?

Did you take a look at your current set of rules to see if there are any conflicts?

---

### Post by Doug S on 2011-10-06
Evidently, what Knof is trying to do can be done. [Here is one good reference I found]("http://www.linuxquestions.org/questions/linux-networking-3/iptables-forwarding-with-one-nic-80009/").
To try to mirror what Knof is trying to do, I am trying to forward port 80 requests to my test computer at 192.168.111.140 to my main server at 192.168.111.1. I get the same results as Knof, i.e. a browser gets the web pages from the test machine without the added iptables rules and nothing happens with them. As I mentioned earlier, with tcpdump, I see the packets coming in, but they don't get sent back out. You won't see them with "iptables -L -v" because they are in the nat table. On my system, I also can not see them with "iptables -t nat -L -v", because my system doesn't seem to think I have a nat table. However, I can see the packets with "sudo iptables-save -c":
```
*nat
:PREROUTING ACCEPT [6337:2346901]
:POSTROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
[18:912] -A PREROUTING -i eth0 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.111.1:80
COMMIT
```
So, you can see that 18 packets travsered the rule. Now, I wouldn't expect things to work until I can get /proc/sys/net/ipv4/ip_forward to be 1, which I haven't yet been able to do on my old old test machine.

---

### Post by Dangertux on 2011-10-06
> **Doug S said:**
> Evidently, what Knof is trying to do can be done. [Here is one good reference I found]("http://www.linuxquestions.org/questions/linux-networking-3/iptables-forwarding-with-one-nic-80009/").
To try to mirror what Knof is trying to do, I am trying to forward port 80 requests to my test computer at 192.168.111.140 to my main server at 192.168.111.1. I get the same results as Knof, i.e. a browser gets the web pages from the test machine without the added iptables rules and nothing happens with them. As I mentioned earlier, with tcpdump, I see the packets coming in, but they don't get sent back out. You won't see them with "iptables -L -v" because they are in the nat table. On my system, I also can not see them with "iptables -t nat -L -v", because my system doesn't seem to think I have a nat table. However, I can see the packets with "sudo iptables-save -c":
```
*nat
:PREROUTING ACCEPT [6337:2346901]
:POSTROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
[18:912] -A PREROUTING -i eth0 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.111.1:80
COMMIT
```So, you can see that 18 packets travsered the rule. Now, I wouldn't expect things to work until I can get /proc/sys/net/ipv4/ip_forward to be 1, which I haven't yet been able to do on my old old test machine.

For the ip_forward to be 1 have you tried adding the following to your firewall script

```

echo 1 > /proc/sys/net/ipv4/ip_forward

```

Hope that helps, but yes, you can DNAT with one interface, it's just not normal to do so :-/

---

### Post by Doug S on 2011-10-07
Dangertux: Yes, thanks. For a few reasons, laziness being the main one, I was trying to do it maunally. Even editing sysctl.conf and restarting the computer didn't work.
 
I did get the packets to forward properly, but then things got confused with the return path, as jonobr had suggested might occur. I pretty much copied the solution from the example in the link I gave previously, then things seem to work as expected and I can see the packets moving around as expected with tcpdump. The, rather commentless, file for my test system is:```

#
echo Enabling forwarding...
echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -P INPUT ACCEPT
iptables -F INPUT
iptables -P OUTPUT ACCEPT
iptables -F OUTPUT
iptables -P FORWARD ACCEPT
iptables -F FORWARD
iptables -t nat -F
iptables -X
iptables -Z
iptables -t nat -Z
iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 80 -j DNAT --to 192.168.111.1:80
iptables -A FORWARD -p tcp -i eth0 -d 192.168.111.1 --dport 80 -j ACCEPT
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 192.168.111.140
```

---

### Post by jonobr on 2011-10-07
> For a few reasons, laziness being the main one,


We are brothers from a different mother, you could be describing me in that quote :P

---

### Post by knof on 2011-10-08
I tried everything described above. No sucsses. I don't now what to do else. 
I know, that this solution is just about to work...
 
Maybe is another solution with virtualhost and proxyreverse....

---

### Post by Doug S on 2011-10-08
Well that is interesting. Did you get any errors when you loaded your iptables? Was /proc/sys/net/ipv4/ip_forward actually 1 after being set? With tcpdump , could you see the packets going out to 192.168.1.126 now. but not coming back? Can you trace packet paths through your iptbales with the packet counters?
My test computer is turned off now, but I still have the files and such to continue to try to help. I suppose this is an obvious statement, but this should work for you.
I would like to clarify something from your original post. For this statement:```
Now i want to run citadel server on another local machine on port 2000, IP 192.168.1.126 
```
Did you mean:```
Now i want to run [COLOR=red]the[/COLOR] citadel server on another local machine on port 2000, IP 192.168.1.126
```
In which case this solution should work for you. Or did you mean:```
Now i want to run [COLOR=red]anothe[/COLOR]r citadel server on [COLOR=black]another[/COLOR] local machine on port 2000, IP 192.168.1.126
```
In which case this solution will not work, as it will re-direct all traffic (if we can get it to work).

---

### Post by Doug S on 2011-10-09
About: /proc/sys/net/ipv4/ip_forward: The other day when I said:> Even editing sysctl.conf and restarting the computer didn't workWell, umm... It might have helped if I had edited the sysctl.conf file on the correct computer... I only noticed last night when I went to restore the file, that I had edited the file on the wrong computer. (Duh!)
Since I started my test computer again, I took an example tcpdump.
Command:```
sudo tcpdump -i eth0 -n -nn -tttt >zxzx.txt
```
I manually edited out the unrelated packets 
Legend:
Doug 192.168.111.140.80 = knof 192.168.1.125.2000 = computers with additional iptables rules.
Doug 192.168.111.1.80 = knof 192.168.1.126.2000
Doug 192.168.111.100 = browsing computer
(are we confused yet?)
Observe the packets both being forwarded and returned via 192.168.111.140:
> 2011-10-08 13:00:36.684078 IP 192.168.111.100.32463 > 192.168.111.140.80: S 1803411263:1803411263(0) win 8192 <mss 1460,nop,wscale 2,nop,nop,sackOK>
2011-10-08 13:00:36.689748 IP 192.168.111.140.32463 > 192.168.111.1.80: S 1803411263:1803411263(0) win 8192 <mss 1460,nop,wscale 2,nop,nop,sackOK>
2011-10-08 13:00:36.689899 IP 192.168.111.1.80 > 192.168.111.140.32463: S 3865980205:3865980205(0) ack 1803411264 win 5840 <mss 1460,nop,nop,sackOK,nop,wscale 7>
2011-10-08 13:00:36.690096 IP 192.168.111.140.80 > 192.168.111.100.32463: S 3865980205:3865980205(0) ack 1803411264 win 5840 <mss 1460,nop,nop,sackOK,nop,wscale 7>
2011-10-08 13:00:36.691279 IP 192.168.111.100.32463 > 192.168.111.140.80: . ack 1 win 16425
2011-10-08 13:00:36.691362 IP 192.168.111.140.32463 > 192.168.111.1.80: . ack 1 win 16425
2011-10-08 13:00:36.699385 IP 192.168.111.100.32463 > 192.168.111.140.80: P 1:369(368) ack 1 win 16425
2011-10-08 13:00:36.699461 IP 192.168.111.140.32463 > 192.168.111.1.80: P 1:369(368) ack 1 win 16425
2011-10-08 13:00:36.699642 IP 192.168.111.1.80 > 192.168.111.140.32463: . ack 369 win 54
2011-10-08 13:00:36.699707 IP 192.168.111.140.80 > 192.168.111.100.32463: . ack 369 win 54
2011-10-08 13:00:36.703009 IP 192.168.111.1.80 > 192.168.111.140.32463: P 1:288(287) ack 369 win 54
2011-10-08 13:00:36.703084 IP 192.168.111.140.80 > 192.168.111.100.32463: P 1:288(287) ack 369 win 54(Note: I am not sure how to prevent the little face icon substitution)

---

### Post by knof on 2011-10-12
Sorry for delay...long workdays...
 
I'm running the citadel server on both machines on the same port 2000. I think, that running citadel servers on both machines is not a problem. I must just specify, which one i want to forward out to web. 
Originaly, i want to run the citadel server on 2. machine on IP 192.168.1.126, that i mean in 1. post. 1. machine is used just for redirection.
 
I'm not confused, yet ;), but just to clarify: 
I need to setup iptables on both machines or just on the 1. one?
Is $IPT = iptables in file where i configure iptables?
In which file do i have write and save iptables configuratin? Now i'm using file in /etc/firestarter/user-post.  OS is Ubuntu 11.04.
 
Hopin that's not too much...huh?

---

### Post by Doug S on 2011-10-12
> I need to setup iptables on both machines or just on the 1. one?
You just need the special redirection rules on the number 1 machine (192.168.1.125)
> Is $IPT = iptables in file where i configure iptables?
I am not sure I understand the question, but yes many people use a name declaration in the script. However, I would have expected something like:
> IPT=/sbin/iptables
for the declaration, and then something like:
> $IPT -P FORWARD DROP
when it is being used. But like I said, maybe I don't understand the question.
> In which file do i have write and save iptables configuratin? Now i'm using file in /etc/firestarter/user-post. OS is Ubuntu 11.04.
Sorry, I had the impression from this thread that you were pretty good at adding iptables rules and such. I have never used firestarter, actually never used any iptables front end program of any sort. I have always written iptables rule scripts directly. Hopefully some other forum reader can help with how to add the rules I listed above with the other firestarter stuff that you already have. If you want to do it in iptables, I can try to help further.

---

### Post by knof on 2011-10-13
I have used iptables in many cases, for block specific IP or accept specific IP. And it allways work fine. I just type into /etc/firestarter/user-post file iptables statements and it works. And i allways tested those statements. If i delete this statements, server behave like before. For example: 
$IPT -I INPUT -s 192.168.1.126 -j DROP   statement for blocking IP 192.168.1.126.
But now, when i see, that nothing help to get this redirection, i'm wondering what to ....i'm doing wrong.
I also use VirtualHost file for serving requests for specific domains from different directories. This is not problem. Just this redirection....

---

### Post by Doug S on 2011-10-13
O.K. I understand.
Is there a file called "/etc/firestarter/user-pre". If yes, try putting the rules there.
Perhaps it is time to take a look at your entire iptables. With the rules in place and after trying it a few times, post the output for these commands (on 192.168.1.125):
```
 
sudo iptables -v -x -n -L
sudo iptables -t nat -v -x -n -L
sudo iptables-save -c

```

---

