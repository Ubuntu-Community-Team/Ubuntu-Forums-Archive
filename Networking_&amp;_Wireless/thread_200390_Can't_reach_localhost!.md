---
title: "Can't reach localhost?!?"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by Luke771 on 2006-06-20
I wanted to explore the network I'm connected to using Cheops-ng, but when I typed 127.0.0.1 in the "Connect to Agent" dialog, I got ```
I could not connect with the Specified IP agent at: 127.0.0.1
``` (with that capitalization).
I disabled ICMP filtering in Firestarter but nothing changed.
So I tried the older version of Cheops (0.61) and that worked fine.
Then I tried launching Cheops-ng  from a terminal window so I could see the output: Typing 127.0.0.1 in  "Connect to Agent" it was:```
ERROR: File event.c, Line 727 (ipv4_agent): Unable to connect to ipv4 agent '127.0.0.1' (Connection refused)
ERROR: File gui-viewspace.c, Line 158 (start_ipv4_agent): Unable to connect to local agent

```
How is it possible that I can't connect to my localhost? Must be some loopback problem (just guessing) I must have missed something quite obvious but I can't figure out what it is, only thing I know is that I used to run Cheops-ng on Breezy and it worked, so I guess the problem must be in my network settings. 

I have some small problems with web surfing too: sometimes it's too slow, sometimes it takes several minutes to load a page, and sometimes I click the firefox panel icon, "starting firefox.." shows up in the windows list... and then it disappears. 
When that happens I have to log out and in again for the browser to launch; trying to launch Opera instead won't work: "starting Opera..." in the windows list, and then disappears, just like Firefox (and Mozilla suite too).

Anybody knows what's that all about?
Can those problems be related to each other?
I do I fix that?
And *what* is the problem(s) anyway?

I'm on a fiber 10M/sec network, at least that's what the ISP says, I actually get 1 M/sec some times little more, oftes even less that that. I am behind a ISP NAT with no access to the NAT box.

My system is an old Duron 1600 with 512 Ram, the Ethernet card is a 10MB/s Via Rhine.

---

### Post by gerbman on 2006-06-20
[QUOTE=Luke771]I wanted to explore the network I'm connected to using Cheops-ng, but when I typed 127.0.0.1 in the "Connect to Agent" dialog, I got ```
I could not connect with the Specified IP agent at: 127.0.0.1
``` (with that capitalization).[/QUOTE]Check your loopback interface ("lo") with "ifconfig". The interface should have an inet address of 127.0.0.1. If it doesn't, reconfigure it with```
sudo ifdown lo
sudo ifup lo
```and check it again with "ifconfig".

---

### Post by Luke771 on 2006-10-30
I didn't remember about posting theis thread; the problem was that I didn't know that you have to launch cheops-agent before you can use cheops-ng.
In a terminal window, run the command line ```
sudo cheops-agent
``` if you want to see the output of the apps used by cheops-ng.
If you don't care about the aoutput, you can run ```
sudo cheops-agent &
``` and, once it's running, hit enter to make it go back to prompt, the close the terminal winow with ```
exit
```.
Closing the terminal in other way than that will make cheops-agen crash.

Once cheops-agent is running, you can start cheops-ng and type 127.0.0.1 in the 'agent' field of the 'connect to agent' window

---

### Post by Luke771 on 2007-01-19
(edit) 
double post by mistake. sorry.

---

### Post by Luke771 on 2007-01-19
What was I thinking?
You don't want to run cheops-agent as a daemon, first of all because you may want to see what cheops-ng is doing, what app is it using, the output, etc: you see all that stuff in the terminal.
Second of all, you will have to close cheops-agent, once you're done with chops-ng, and having an open terminal makes the exiting much easier.

---

