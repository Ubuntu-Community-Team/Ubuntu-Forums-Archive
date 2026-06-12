---
title: "iptables"
date: 2006-01-24
forum: Networking &amp; Wireless
---

### Post by odin on 2006-01-24
I would like to allow only 2 machines in a network to use ftp but I cant find the way.

I've tried all possible options to do this but obviously the right one.The thing is that if ftp is allowed for 2 of them(as I though) the rest can also use that port.I really have tried but I need to allow ftp traffic from machine A to machine B and the opposite blocking this traffic to rest of the world.

Anyone can help??

Thank's in advance

PD:I cant use firestater or anything like that cause this is for a kind of application I'm doing that works with several bash scripts.

---

### Post by mpvano on 2006-01-24
You're a bit confused.

A firewall cannot control traffic between OTHER computers in a network, It only controls the behaviour of YOUR computer. You cannot prevent other computers from using FTP to talk to things other than the computers you install your firewall on.

If you are trying to prevent YOUR SPECIFIED TWO COMPUTERS from being ACCESSED BY FTP by ANY COMPUTER BUT EACH OTHER, you can do this, but EACH of them needs to be using a correctly configured  iptables that allows FTP connections only from the other.

In addition, you probalby won't be able to do this type of filtering unless each machine has a static address, since the filter rule will need to be based upon IP address.

It sounds like you're a little fuzzy on how IP networks operate, so I suspect you won't be able to get this working yourself, since creating custom filter rules definitely requires a good understanding of what's going on in your network.

Perhaps you can achieve your goals by simply disabling anonymous access to each of your ftp servers? That way machines that you don't want using FTP won't be able to log in unless they have an account. If you don't know how to control access to your FTP servers, you shouldn't be running them as they are dangerous. Read the man pages and other documentation for your server and for your server's configuration files for detailed information about how to control access to them.

Better yet, is there any reason you can't use secure shell for transfers? You can then use shell commands directly on the peer machine, or do ftp like transfers with sftp or scp.

SSH offers all kinds of powerful ways to control access, the best of which is to disallow logins from machines that don't have known keys installed on the target machines. You can also control access by host and by account name easily. Again read the man pages and documentation to learn how to set this up.

Once you have ssh security working properly, you can also use the powerful rsync directory synchronization and backup program without having to install an rsync server on either machine. Again, refer to the man pages and documentation for rsync for more information. It's a powerful system and easy to use over ssh transport.

hope this points you in the right direction

Mario

---

### Post by odin on 2006-01-24
Well I should have given more details about the situation but still I might be wrong...

The thing is that I'm using an machine with ubuntu installed as a wireless access point.Besides I made an application to configure that access point.My starting point is that I believe all traffic in the wireless network is "traveling" through the access point so that is why I think it may be possible to allow ftp traffic only  between 2 specific machines adding some rules in the access point (I say ftp but it could be any other kind of traffic) since all traffic should be "routed" through the access point.

As I said I might be wrong but now you may understand why I think this can be possible.

But thank's for the fast answer and hope that after this explanation we can find a way of solving this if possible.

thank's in advance

---

### Post by mpvano on 2006-01-24
Whether you're actually routing through ubuntu or only through the wireless access point software is the question.

You are correct, in general, wireless hosts using managed mode talk to each other through the wireless access point, but the wireless access point is usually implemented inside the host adapter itself. Those messages never usually enter the machine hosting the adapter.

There are some wireless access point packages for linux that replace the access point management functionality by software running in the linux box, but even when they do, that traffic doesn't usually go through the normal linux networking protocols stack unless it's actually directed to the machine itself.

If your machines are all on the same IP subnet, then it's most likely that the protocol stacks in linux never see the packets.

I suspect that if you're using a specialized host access package to simulate a wireless access point using something like the "hostap" driver system, then the software that manages your access point could theoretically filter packets for you, but I have no idea what software you are using to do that, and I really don't know much about such packages or what options they offer.

Since you are using the linux box as the gateway for your wireless hosts, you CAN, however use it to firewall access from OUTSIDE the wireless part of your network to and from machines on the wireless lan.

I'm still not sure if this is any help to you, but at least I think we're talking about the same thing....

Mario

---

