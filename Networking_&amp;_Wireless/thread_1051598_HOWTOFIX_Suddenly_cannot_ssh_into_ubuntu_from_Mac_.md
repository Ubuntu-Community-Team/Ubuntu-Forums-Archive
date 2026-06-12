---
title: "HOWTOFIX: Suddenly cannot ssh into ubuntu from Mac OS X"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by Defrector on 2009-01-26
If you are getting long pauses when trying to ssh from your mac (OS X) to your ubuntu machine by IP (username@xxx.xxx.xxx.xxx), especially when you could have sworn you were able to a few months ago, and you've tried the following:

* Mess with the MTU of your LAN, dropping it to 576 or up to 1500
* Cleared your ssh keys and rebuilt them
* Bypassed switches, routers, etc between your client and your server
* Used the -vvv flag on your client's ssh command

... and you're still getting messages which look like this when the -vvv option is on:
> 
debug1: An invalid name was supplied
Cannot determine realm for numeric host address

and/or this...

> debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
Write failed: Broken pipe

First, **DO NOT DOWNGRADE YOUR CONNECTION TO VERSION 1.** It technically will work but it is vulnerable.

Try this:

As sudo on your mac, edit your /etc/hosts file and add the IP of the server and give it a name, such as:
```
XXX.XXX.XXX.XXX    my-ubuntu-server
```

Save and exit, then re-try to SSH.

-thanks to this article for the hint:
[http://macnewbie.wordpress.com/2006/08/30/slow-ssh-connections-on-mac-os-x/](http://macnewbie.wordpress.com/2006/08/30/slow-ssh-connections-on-mac-os-x/)

Why this problem could happen:
Probably a bug on the mac side.

---

