---
title: "File sharing over NON-tcp/ip networks"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by Ulysses_ on 2009-07-11
Hi. I would like to set up a file server that does not use tcp/ip at all. Only some other protocol. What protocol can be used instead of tcp/ip?    The reason I want to do this is what is known as protocol isolation: if the server only speaks a non-tcp/ip protocol, it is much harder to hack into from other computers in the LAN. These computers are connected to the internet for web browsing, and can therefore get penetrated.    1. What is the most secure non-tcp/ip protocol for protocol isolation? Ie the hardest to penetrate?    2. What protocol should be used above this for the file sharing? NFS? Samba? Ftp? Other?

---

### Post by jonobr on 2009-07-11
This doesn't make a lot of sense to me and maybe its becuase Ive never heard of protocol isolation like this before.

The protocols you mention, like ftp and so on use the IP stack on your machine which is layer 3 of the OSI model.
The only other alternatives at layer 3 would be something like IPX (not really in use anymore) or more commonly something like IPsec.

TCP  is used on layer four , the transport layer.
 other options instead are UDP, which is what tftp bootp and other connectionless applications would use.
At layer 4 there are other transport protocols like sctp which uses the reliability of TCP with the speed of TCP and was developed by the IETF ,PPTP and other secure protocols

So there are they options instead of using TCP/IP. however, Im not sure if theres a branch of the networking topic I have missed regarding protocol isolation. which is possible

---

### Post by ktrnka on 2009-07-12
Well the network sharing protocols you just listed all use TCP/IP. I think I understand what you mean though. I prefer to use only ssh. It is real easy and completely encrypted (both the initial connection and the file transfer). You can use scp/sftp/sshfs to transfer files. This would also allow you to only monitor one port number (your ssh port) sshguard, fail2ban and the like will prevent those script kiddie attacks from being effective. The other option would to setup a VPN with openvpn. SSH is simple secure and effective.

I do know about limiting allowing only specific protocols but what you are suggesting is security through obscurity which is just plain moronic. All I'd have to do is sniff/monitor your network traffic with wireshark or etthercap and easily identify which protocol you are using. You'll be fine sticking with TCP/IP using ssh/sftp and using STRONG passwords.

Good Luck!

---

### Post by jonobr on 2009-07-12
+1 on the use of ssh/sftp and strong passwords

---

### Post by Ulysses_ on 2009-07-12
> **jonobr said:**
> The protocols you mention, like ftp and so on use the IP stack on your machine which is layer 3 of the OSI model.  Thanks, I am aware of this, part 2. is "What protocol should be used _above this_ for the file sharing"  > The only other alternatives at layer 3 would be something like IPX (not really in use anymore) or more commonly something like IPsec  Any more information on IPsec and how to install it?  > other options instead are UDP, which is what tftp bootp and other connectionless applications would use.  Would that be more secure than acknowledged tcp/ip?  Remember, it is protocol isolation we aim at here.  > PPTP and other secure protocols  This one sounds promising.  Is it designed specifically for security?  > Im not sure if theres a branch of the networking topic I have missed regarding protocol isolation. which is possible  One recommended protocol for this is netbeui in windows, but it is not available on linux any more (used to be 10 years ago). Maybe tcp/ip properly set up is better than protocol isolation, but can we please not consider tcp/ip in this discussion.  As the title says, this is about non-tcp/ip protocols.  Is it possible to do the same thing as **laplink file-sharing** but do it through ethernet cards instead of serial ports?

---

### Post by Ulysses_ on 2009-07-12
> **ktrnka said:**
> I prefer to use only ssh. It is real easy and completely encrypted (both the initial connection and the file transfer). You can use scp/sftp/sshfs to transfer files. This would also allow you to only monitor one port number (your ssh port) sshguard, fail2ban and the like will prevent those script kiddie attacks from being effective.    Sounds cool.  I would like to find instructions how linux can be set up to only expose one port.  It seems difficult to guarantee that.    > All I'd have to do is sniff/monitor your network traffic with wireshark or etthercap and easily identify which protocol you are using.    And once you find it's some obscure protocol that there are no hacking tools for, what are you going to do about it?  Reverse engineer the entire protocol?  Little used hardware and software like apple macs are considered the toughest to hack into by the FBI because nobody bothers to develop hacking tools for - too much effort for two few possible target computers.  Below is one example of protocol isolation.  Can something analogous be done in ubuntu (but with a file server instead of a database server and a web browsing pc instead of the web server)?   [http://www.rudebadmood.com/winmac/200007/0015.html](http://www.rudebadmood.com/winmac/200007/0015.html)

---

### Post by superprash2003 on 2009-07-12
> Sounds cool. I would like to find instructions how linux can be set up to only expose one port. It seems difficult to guarantee that.
you could use firestarter or gufw to open 1 particular port in ubuntu and block the rest

---

### Post by jonobr on 2009-07-12
Hello


Just quick follow up to some of the questions you ask.


IPSec is a encryption and authentication protocol which is for securiing each IP packet.

Protocols such as PPTP L2Tp are tunneling mechanism to create a tunnel between endpoints to create a vpn.



Cheers

---

### Post by Ulysses_ on 2009-07-14
If anyone is interested, here's how it can be done. Appletalk replaces tcp/ip in the local network as follows:   1. On windows computers you install pc maclan (choose "Disable encrypted logins" under menu Configure-Server information).    2. On linux computers you apt-get the netatalk package, edit the file /etc/netatalk/atalkd.conf adding one line that says "eth0" without the quotes, and reboot for the automagic configuration to occur.    The windows computers can then see the linux home directories, but not the other way round (there simply isn't any linux tool for reaching appletalk file shares in windows which is probably a good thing).  This means you have to remember to copy any new files from linux to windows, if you use a liveCD for the linux box - you cannot mount windows file shares.

---

### Post by jonobr on 2009-07-14
AFAIK Appletalk has been dropped by apple in favour of TCP/IP.

It was a proprietary standard by apple.

When I say it was dropped, if you look at the website, they use the word 'deprecated"

If your bored, below is the free dictionaries definition of deprecate,
which in reality means it has not only be superseded , but that it should be avoided.,

Also, good on you for sharing your info!

> Usage Note:  Deprecate originally meant "to pray in order to ward off something, ward off by prayer." Perhaps because the occasion of such prayers was invariably one of dread, the word developed the more general meaning of disapproval, as in this quotation from Frederick Douglass, "Those who profess to favor freedom, yet deprecate agitation, are men who want crops without plowing up the ground." From here it was a small step to add the meaning "to make little of, disparage," what was once the proper meaning of depreciate. This meaning of depreciate appears to have been overwhelmed by the word's use in the world of finances, where it means "to diminish (or cause to diminish) in price or value." In similar fashion, the "disparage" sense of deprecate may be driving out the word's other uses. In our 2002 survey, only 50 percent of the Usage Panel accepted deprecate when it meant "to express disapproval of" in the sentence He advocates a well-designed program of behavior modification and deprecates the early use of medication to address behavioral problems. Moreover, a similar example in the same survey elicited the same split in opinions among Panelists: He acknowledged that some students had been wronged by the board's handling of the matter and deprecated the board's decision to intervene. It seems clear, then, that the Panel has very mixed feelings about the use of deprecate to mean "disapprove of." But a great majority of Panelists accept deprecate when used to mean "make little of, disparage." Fully 78 percent accepted the example He deprecated his own contribution to the success of the project, claiming that others had done just as much. It may be that the widespread use of the word in the compound adjective self-deprecating has helped bolster this use of the verb.

---

### Post by martinbaselier on 2009-07-14
Correct me if I'm wrong, but as far as I know, appletalk has no encryption, I don't thin you can even set passwords. It was intended to be implemented as a simple network protocol. So for security reasons, you use the most insecure protocol you can find, so open indeed, that it picks a random address and it broadcasts its address on the network, to check if no other computer has chosen the same address. It just makes no sense at all.

It's true that it's unlikely that anyone would think of it at first. If they'd be sniffing your network though, they would know it as soon as the first computer is turned on and probably before that. 

Why don't you just use the secure option? Use ufw or some graphical tool to close all the ports except the one you'd want to use. Use data encryption to prevent your data being easily read and use strong passwords.

Excuse me for being so harsh on you, but I just don't get it.

---

### Post by Ulysses_ on 2009-07-14
> **martinbaselier said:**
> Correct me if I'm wrong, but as far as I know, appletalk has no encryption, I don't thin you can even set passwords. It was intended to be implemented as a simple network protocol. So for security reasons, you use the most insecure protocol you can find, so open indeed, that it picks a random address and it broadcasts its address on the network, to check if no other computer has chosen the same address. It just makes no sense at all.

It's true that it's unlikely that anyone would think of it at first. If they'd be sniffing your network though, they would know it as soon as the first computer is turned on and probably before that. 

Why don't you just use the secure option? Use ufw or some graphical tool to close all the ports except the one you'd want to use. Use data encryption to prevent your data being easily read and use strong passwords.

Excuse me for being so harsh on you, but I just don't get it.

 It's ok, just remember that I expect the linux box to get hacked so any encryption in the linux-windows link is irrelevant, the hacker can type what I type and see what I can see, that's ok.  I don't want to hide the windows server's shared files.  Let the hacker see them if they can.  What I want to prevent is the hacker from owning the server too.  How would you go about penetrating the server in order to own it, not just read the apple-shared files?

---

### Post by martinbaselier on 2009-07-14
Just did a quick google search: you should be able to access the files with afps-ng from a linux machine.
For somebody to own the server, you would need to have openssh-server installed. 
If you don't there's no way to gain control over the machine.

---

### Post by Ulysses_ on 2009-07-14
> **martinbaselier said:**
> Just did a quick google search: you should be able to access the files with afps-ng from a linux machine.  Thanks, I'll try that. Should save a lot of effort copying files across.  > For somebody to own the server, you would need to have openssh-server installed. 
If you don't there's no way to gain control over the machine.  I definitely don't have openssh-server installed.  Remains to be seen how available any appletalk exploits are to typical hackers.  Pc maclan is not identical to the mac's appletalk client, so it should not have the same holes! This may be an extremely secure setup.

---

### Post by martinbaselier on 2009-07-14
> Pc maclan is not identical to the mac's appletalk client, so it should not have the same holes
The protocol doesn't have any holes. Because holes imply there's some solid part, like a wall or a fence. ;)

[Here's the wiki article.](http://en.wikipedia.org/wiki/Appletalk)

Anyway, if it's just a local pc, you have very little chance of a hacker breaking into it.

---

### Post by Ulysses_ on 2009-07-14
Any security holes like buffer overflows and integer overflows are a fault of PC Maclan, not the protocol.  The OS X implementation of the protocol has just 3 known faults, according to the site below, but no faults at all are known for the pc maclan implementation.  [http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-4269](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-4269) [http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-4267](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-4267) [http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-4268](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-4268)

---

### Post by martinbaselier on 2009-07-14
I wasn't talking about faults in the implementation. I just meant: When you don't have a lock on your door, nobody can pick the lock.

---

