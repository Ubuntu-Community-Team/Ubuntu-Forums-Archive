---
title: "Does anybody use FreeNX?"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by harisund on 2006-07-04
Hello

I followed the instructions on [https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX) . However, there is no real information on how to start the FreeNX server aside from merely the installation. 

So I added the required repository and did a "sudo apt-get install freenx" and it installed something. From what I understand FreeNX uses SSH, and SSH server is running fine on port 22, no problems there. 

I really don't know what to do beyond that. I just assumed FreeNX was installed fine and running. So I head over to my Windows box, install the client, and connect to the server (on the same subnet, no firewalls / router). The nomachine NXClient connects to my server, and then nothing happens. 

Is nothing supposed to happen? Or am I supposed to get a GUI screen or something like that? Am I forgetting something? A ps ax listing on the server doesn't really reveal anything with 'nx' on them, and "sudo nxserver --start" just returns some errors. 

Trust me, if I can get NX server on Linux and client on Windows running, I will edit the wiki page to have appropriate instructions. :)

---

### Post by steven43126 on 2006-07-05
Hmm, as for ubuntu specific instructios i can't help you 'yet' ;)
NX dosent really run as a service it's launched from an SSH connection.
Check your logs after an attempted connection see whats there. Make sure
SSH is running and you can connect to that alright. 

Ta Steve.

---

### Post by rvergara on 2006-07-05
Harisund,

I use Freenx on a daily basis to connect from a windows XP client to my Ubuntu 5.10 box. I do this remotely over the internet.

In your process running listing, there should be several "nx" processes once you are connected, namely:

nxagent
nxserver
nxnode (one or more)

However these processes do not run unless you are connected, so my assumption is that you are not actually connected. In order to debug we would need more info.

1. Are you using Ubuntu 5.10? it seems you do from your forum profile. If you do I assume you are using Gnome as a desktop.
2. What desktop did you set up in the general tab of the nomachine client, it should be gnome
3. Did you set up a key or used the default?
4. is your Ubuntu box behind a NAT device?, did you port forward port 22?
5. can you review your nx session log (NXWin.log)? you will find it in the following path: \Documents and Settings\(what ever username you use in XP).....\.nx\temp

---

### Post by harisund on 2006-07-11
rvergara, thanks a ton for your support .. seriously it is people like you who direct newbies in the right direction. 

Anyway, somebody on IRC told me that freenx from Seveas' repository is version 1.5 and consequently I will need client version also 1.5 on Windows (I had client version 2 on Windows.) 

Anyway, your post just taught me a lot on how to go about remotely debugging problems.. I am sure to use it while I go about my work as the system admin of the dorms in my university :)

---

### Post by harisund on 2006-07-11
I have a couple of questions. 

1. Often when I nx into my Ubuntu machine, the gnome panel and the bottom windows list panel doesn't show up. Any ideas? 

2. Can I use it to connect to anything other than Gnome, KDE or CDE? I am thinking fluxbox and XFCE here. I would prefer them to Gnome (yeah, the old takes-up-too-much-system-resources-eye-candy thing). Will NX work over these two too?

---

### Post by harisund on 2006-07-11
Going over /etc/nxserver/node.conf this is what I understand. 

The command gnome-session (/usr/bin/gnome-session) starts a gnome session. A dpkg --search reveals it is from a package called gnome-session. 

The command kdestart (/usr/bin/kdestart) starts a kde session. A dpkg --search reveals it is from a package called ksmserver. 

Now what command starts a xfce session? Fluxbox?

---

