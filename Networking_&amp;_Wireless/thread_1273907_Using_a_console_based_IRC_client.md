---
title: "Using a console based IRC client"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by Jaraxle on 2009-09-23
I installed ircii and the pork irc client. However I can't figure out how to get a server list and connect to a server. I've searched and can't find anything that has helped.

I like the look and feel of these programs and would rather learn to use these instead of a GUI client. Unfortunately, I only have experience using mIRC on Windows.

So how do I connect to channels? I only know how to start and exit the program.

---

### Post by etnlIcarus on 2009-09-23
In a terminal, type```
man ircii
```for instructions on how to use ircii.

And for the record, almost everything you install on *nix will come with a, "manpage", or manual page. You can find it by typing "man", followed by the name of the package/application.

---

### Post by Jaraxle on 2009-09-23
Ok, I managed to get a bit further but most of the servers are searching my system for something called identd and then refusing the connection, saying I need to have identd installed.

I looked for it in Synaptic and it seems to be some kind of daemon or protocol server. I'd like to know more about what it does before I install it. Do I really need it?

---

### Post by etnlIcarus on 2009-09-23
I'm not real well versed with ircii. Upon starting it up, it looks as if it's trying to connect to a server listed in a file that isn't properly configured.

Once it fails, I just type:

```
/SERVER irc.freenode.org

/JOIN #ubuntu
```

And I get into the #ubuntu channel on freenode without a hitch.

Sorry I can't be of more help, I prefer graphical clients.

---

### Post by The Tronyx on 2009-09-23
I would recommend doing sudo apt-get install irssi.  Once installed, run irssi via command line.  When the irssi window appears, do /server irc.freenode.net.  Once connected, go have fun.

---

### Post by andrew.46 on 2009-09-24
Hi Jaraxle,

It is a little unusual to see people looking for console based irc clients, everybody seems to be settling for X-Chat and the like which I will admit to cordially loathing :). Can I second the comments by Tronyx and also advise the use of irssi? I have written a guide that makes it all a bit easier:

[Howto] Setup irssi and join #ubuntu on Freenode
[http://ubuntuforums.org/showthread.php?t=1010780](http://ubuntuforums.org/showthread.php?t=1010780)

and I attach a screenshot of irssi in action to hopefully tempt you a little :).

Andrew

---

### Post by scorp123 on 2009-09-24
> **Jaraxle said:**
> most of the servers are searching my system for something called identd and then refusing the connection, saying I need to have identd installed ...  I'd like to know more about what it does before I install it.  And why didn't you simply look it up?
Go to:
[http://www.wikipedia.org/](http://www.wikipedia.org/)

Type "identd" into the search field ... voila, done. ;)

> **Jaraxle said:**
> Do I really need it? those server admins most certainly think so :D

---

