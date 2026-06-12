---
title: "SSH / SFTP connect onto my Ubuntu machine"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by lucasart on 2010-04-03
Hello everyone,

(I am using Ubuntu 9.10 64bit)

I would like to share some of my folders with other people. And it would have to work from Linux/Windows/Mac OS X machines. I spent some time looking at forums and figured out that:
- Setting up an FTP and making it "visible" on the internet is ridiculously complicated
- Using Samba looks simple in these silly tutorial. But all they do is connect from their home PC to the same PC running Windows on a VM: this makes the problem trivial because the name of my computer makes no sense outside my local network, and there's no router/firewall to go through.
- Besides, I want to keep things simply and understand what exactly I am doing. So I figured an SSH connection and SFTP to allow external users to access my files using FileZilla or HummingBird for example, would be the best solution.

Here's my understanding of how an SSH connection should work, but I'm really a newbie so any help/comment is appreciated:

1/ I need to configure the ufw firewall on my Ubuntu machine to allow TCP connections via port 22: is that correct ? Or am I missing something. I don't want to simply disable my firewall, and also I want to understand what is happening.

2/ Now the door is open, and let's say that my computer is lucas-desktop, and has an account called guest with a password. Let's say I am now an external Windows user and I open FileZilla, and enter: host = lucas-desktop, username = guest, password = (...), port = 22. I imagine it will not work, if only because they cannot possibly figure out what lucas-desktop is from the outside.
- Would it work by using my IP adress ?
- now IP adress is not constant, and logging in with an IP adress in is not very "user friendly". Is there a better way to identify my machine ?

3/ So SFTP would be possible if I get to fix 2/. And would SSH connection via a client like Putty work too ? That would be really cool too.

Thank you

---

### Post by Martje_001 on 2010-04-03
Hi lucasart,

You should really try Dropbox (see my signature): it's a very simple application which allows sharing files and storing them in a cloud (if you decide to sign up, please use my link, thanks! ;)).

The problem you're facing is probably the fact you're behind a NAT. This means your modem/router is blocking all attempts to access your computer, from outside your network. Read this: [http://en.wikipedia.org/wiki/Port_forwarding](http://en.wikipedia.org/wiki/Port_forwarding) .

---

### Post by Bachstelze on 2010-04-03
1. Correct.

2. If you have a dynamic IP address, you can use services like [http://www.no-ip.org](http://www.no-ip.org) to get a name that will always resolve to your address.

3. Yes. Both SFTP and SSH connections are handled by the same daemon (sshd), so if one works, the other works too.

---

### Post by Martje_001 on 2010-04-03
To answer your questions step by step:

1. Depends on your configuration. If you have configured UFW in such a manner all connections from outside your computer are blocked, then: yes. However; the default configuration of Ubuntu doesn't do this: it simply hasn't got any applications listening. As soon as you set up an application listening on (for example) port 22, this port will be opened up.

2. You're correct here. In combination with port forwarding it should be possible to access your machine with your IP from the outside. What ^Bachstelze^ said.

3. Sftp actually has nothing to do with FTP. The name is a bit misleading, it's purely SSH.

---

### Post by lucasart on 2010-04-03
Many thanks to both of you. I understand now.
But unfortunately my router does block all incoming connections ;( I really found nothing to get rid of that stupid "feature", although it was interesting information to read the wikipedia page.

---

### Post by Martje_001 on 2010-04-04
Most routers support port forwarding. Have you tried visiting the web interface of yours?

[IMG]http://dl.dropbox.com/u/1106740/Screenshot-Connection%20Information.png[/IMG]

For example, my address is: [http://192.168.178.1/](http://192.168.178.1/)

---

### Post by lucasart on 2010-04-05
Thanks. Actually it wasn't port forwarding: my internet provider put a built in firewall in their own stupid system. So even with ufw disabled, it's as though it was enabled already and blocking all (incoming & unsollicited) connections.

---

