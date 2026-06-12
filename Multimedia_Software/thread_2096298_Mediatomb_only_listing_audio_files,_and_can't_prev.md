---
title: "Mediatomb only listing audio files, and can't prevent it from autostarting"
date: 2012-12-19
forum: Multimedia Software
---

### Post by Nixblicker on 2012-12-19
Hi everybody,

I have to confess that the title is a bit misleading. 

Actually these two problems occur on two completely different setups. I'll come to this.

The reason I posted here is, that after installing mediatomb on my my 12.04 notebook, I can't prevent it from autostarting the daemon on every system restart.

I merely wanted to start MT manually from the console, if i want to stream something to my beamer. But it happens that always there is an instance of it loaded already, what confuses the the whole thing and is a unnecessary complication.

I found that there is an option in /etc/default/mediatomb that is presumably exactly created for guys like me.

```
# Set whether the daemon should be started. Set this value to anything
# but 'yes' to enable the daemon
NO_START="yes"

```

So I stated "yes" to prevent it from starting - but guess what. After every reboot, the daemon is there until it is shut down manually.

Does anyone have a similar problem and might point me to the right direction? Any other suggestions in this?

The second issue is more a general thing - I have MT also installed on my mipsel based Asus wl500w network router device as the latest static optware version from [http://mediatomb.cc/pages/download#optware](http://mediatomb.cc/pages/download#optware). 
After the fiddling with sqlite and such it seemed to work. But wait - it does only display my audio files in the tree I gave the ui to search for media. There it also only displays an Audio subfolder in "Database", no Video listing at all. 
Files I wished it would find are regular avi and such. Nothing special.

What the heck - tried googling, but nobody ever seems to have had this problem. Cannot find anything unusual also in the default config.xml that would make it exclude something. 

Is there such an option that would let me exclude some type of media - and where would I find it, if it does?
Any ideas/suggestions someone?

Would be highly appreciated!

Cheers,
Nix

---

