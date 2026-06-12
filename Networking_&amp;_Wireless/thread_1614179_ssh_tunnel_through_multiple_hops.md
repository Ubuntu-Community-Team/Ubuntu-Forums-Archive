---
title: "ssh tunnel through multiple hops"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by manco1911 on 2010-11-05
Hi guys, i recently solved (thanks to the forum :P) the filter at school, where i only have the port 80 open. 

I did a SOCKS proxy with the following comand:
#ssh -D 8080 -p 80 [email]user@homeserver.com[/email] 

Done, works 10+. 

Now the issue im having, is that i have to accomplish the same results, but throug multiple hops. 
That would be:
Univ:socks 8080 --> ssh port 80 --> host1.com -->  ssh port 9999 --> homeserver.com


What i have tried:

#ssh -t -D 8080 -p 80 [email]user1@host1.com[/email] ssh -t -D 8080 -p 9999 [email]user@homeserver.com[/email]

no luck.

#ssh -t -p 80 [email]user1@host1.com[/email] ssh -t -D 8080 -p 9999 [email]user@homeserver.com[/email]

no luck.


Hope to get some kind of solution for this.. 
Thanks in advance guys !

---

### Post by sedawk on 2010-11-05
I think option -D does some magic you only want to run
once in your "chain".

Also make sure to check where you want to run ssh.
I see no reason for "-p 9999". You can always use
the same port, e.g. "80".

I think "-D" is only needed for the last connection
in the chain. For all the previous connections you
can use simple "forwarding without the magic of -D".

Untested:
#ssh -t -L8080:homeserver.com.8080 -p 80 [email]user1@host1.com[/email] ssh -t -D 8080 -p 80 [email]user@homeserver.com[/email]

This should connect local port 8080 to port 8080 on host1.com
and the second ssh command then does "-D magic" on port 8080
between host1.com and homeserver.com

BTW: You might be interested in OpenVPN and how to set up
a Point-2-Point tunnel (with, or without some ssh-hops
in between). Might give you more flexibility than the above
solution...

---

### Post by manco1911 on 2010-11-05
@sedawk
Thanks 4 the quick response. 
First of all, i use the -p 9999 for not misleading the explanation. 
I'll continue with that line if its ok to you. 

So, i tested your line:
 
#ssh -t -L8080:homeserver.com:8080 -p 80 user1@host1.com ssh -t -D 8080 -p 9999 user@homeserver.com

It seems to work.. thow on the browser i get "..too long to respond". 
And on the comand line i get this output:

user@homeserver:~$ channel 3: open failed: connect failed: Connection timed out
channel 4: open failed: connect failed: Connection timed out
channel 5: open failed: connect failed: Connection timed out
channel 3: open failed: connect failed: Connection timed out
channel 4: open failed: connect failed: Connection timed out
channel 3: open failed: connect failed: Connection timed out
channel 3: open failed: connect failed: Connection timed out
channel 3: open failed: connect failed: Connection timed out
channel 4: open failed: connect failed: Connection timed out

So, i get a ssh tunnel to my homeserver. But it seems not to work the -D Socks connection ?

---

