---
title: "configuring network connections on bootup"
date: 2006-04-08
forum: Networking &amp; Wireless
---

### Post by bearcat on 2006-04-08
N00bie question for y'all...

The problem is that during the bootup process, the "configuring network connections" step is *painfully* slow; it takes about two to three minutes to move on to the next bootup step. And the later clock synchronization step fails. 

However, once I'm finally fully booted, I have no trouble whatsoever getting online. 

So, basically, I can reluctantly live with a slow bootup process if I have to, but I'd really like to speed it up if possible. Is there anything I can do to make the network connections configure faster?

If you need further information from my config files or whatever, I can post it...but I'm too much of a n00b to know what to post until I'm asked :confused:

---

### Post by 5-HT on 2006-04-08
Is it the 'configuring network connectoins', or the clock syncronization step that is taking so long? 
There are lots of posts about the clock synchronization strep either failling or taking a long time.

As long as everything's working when you're booted but the step fails on boot, a quick and easy way would be to just press ctrl + c during the step that's failing.

There is a way to remove steps from the boot process, but it's quite more involved than a ctrl + c. If you want, there should be at least a couple threads describing how to do so, and a quick search should get you the answer.

HTH

---

### Post by jml on 2006-04-09
The delay i boot caused by trying to establish network connections for things that have no current connection can be partially fixed by deactivating the network connections that are not needed.  For example, if you mainly use a wireless connection for your computer, make sure that the wired connection, usually eth0 is deactivated.  If you don't routinely have your computer connected to wireless, then deactivate that one.  Its not an elegant solution, but it will speed up the boot process.

Joe

---

### Post by bearcat on 2006-04-11
The time synchronization just fails, but it does so quickly; it's the "configuring network connections" step that takes forever. I'll try the ctrl-C next time I boot up.

I'm on a DSL connection, not a wireless one...but to do anything in that regard, I don't even know what file I'd need to edit or how.

---

### Post by echo $USER on 2006-04-11
Could you post what is in your /etc/network/interfaces file?  The answer might be in there.

---

### Post by DaOg75 on 2006-04-11
i had this problem and solved it by editing my interfaces file in /etc/network directory. 
Before it was:  
"mapping hotplug
	script grep
	map eth0

iface eth0 inet dhcp"
and after editing:
"mapping hotplug
	script grep
	map eth0

#iface eth0 inet dhcp"
i hope this helps and please forgive if i am posting this wrong as i am a newbie to linux and ubuntu. many thanks to all who post here as its helped me out a lot making the transition from windows.

---

