---
title: "Restarting NetworkManager"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by stderr on 2008-12-30
Under 'typical' linux scenarios, one would normally restart networking with

```
sudo /etc/init.d/networking restart
```

However, since NetworkManager seems to take over *everything*, it seems that that script is none too useful. Even ifup/ifdown seem to be struggling under NM.

I found references online to scripts under /etc/dbus-1/event.d/ (no's 25 and 26). However, having just upgraded to Ibex, I find that 25 has been removed, and 26 only exists by way of a backup copy.

Funnily enough, I only then discovered /etc/init.d/NetworkManager. However, it doesn't work, and reading through the script has made me even more confused.

```
PIDFILE=/var/run/$NAME.pid
```

(where NAME has been defined as NetworkManager)

Now, Network Manager is running ('ps aux | grep nm' gives nm-applet, nm-system-settings and nmbd), but there is no PID file at the above location.

The script is small and simple; all it does is use start-stop-daemon to start or stop the daemon /usr/sbin/NetworkManager.

Looking at the modified date, and the fact that I just upgraded to Ibex on this box today, I reckon /etc/init.d/NetworkManager is an old script which perhaps should have been removed.

So, after all this, I'm still left with my original question ;) - aside from manually hacking up a command using start-stop-daemon or even something like killall, how do we restart NetworkManager in the style of /etc/init.d/networking?

TIA

---

### Post by lensman3 on 2008-12-30
I don't thing NetworkManager is ready for prime time yet! 

I went into all the /etc/rc#.d/'s and deleted all the soft links to for S??NetworkManager for the SYS5 start sequence.  That way when my system starts it won't start the daemons.  NetworkManger kept taking me offline.  There didn't seem to be a reasonable "keep-alive" time.  It would even unmount my eth0 driver.

I like using ifup/ifdown.  The only trouble (and it is a big problem) is that when my machine starts, I have to manually start the network. (I have a home network with a Linux firewall).  I boot to runlevel three, no GUI. Then logon and then start X11 with "startx".  If the network isn't running. it takes a long time to get X11 to start.  I then <CNTL>-<ALT>-<BKSPACE> to kill X11 and start my network, which then starts and stays started.

Sorry I don't have a "real" solution.  I think this was something that wasn't broken, and somebody has now broke (sic) it.

---

### Post by stderr on 2008-12-30
> **lensman3 said:**
> I don't thing NetworkManager is ready for prime time yet! 

I went into all the /etc/rc#.d/'s and deleted all the soft links to for S??NetworkManager for the SYS5 start sequence.  That way when my system starts it won't start the daemons.  NetworkManger kept taking me offline.  There didn't seem to be a reasonable "keep-alive" time.  It would even unmount my eth0 driver.

I like using ifup/ifdown.  The only trouble (and it is a big problem) is that when my machine starts, I have to manually start the network. (I have a home network with a Linux firewall).  I boot to runlevel three, no GUI. Then logon and then start X11 with "startx".  If the network isn't running. it takes a long time to get X11 to start.  I then <CNTL>-<ALT>-<BKSPACE> to kill X11 and start my network, which then starts and stays started.

Sorry I don't have a "real" solution.  I think this was something that wasn't broken, and somebody has now broke (sic) it.

Ah, this wasn't what I wanted to hear! :-k Your problems appear to be worse than mine. I must admit I've been hoping for some time now that I've just overlooked some really obvious NetworkManager scripts, features, ... anything. Because, indeed, it doesn't seem like it's release-ready, or even close. 

How it can interface so poorly with existing Linux tools, I don't know. It seems to go against the grain of what Linux is all about.

I think that unless someone else has some magic words of wisdom, I'll follow your tack and revert to good ol' /etc/network/interfaces and the like, even though it is a little annoying for switching secured wireless networks and suchlike. 

I suppose removing it from "Startup Programs" under System->Prefs->Session would do the trick.

At least when we're dealing with simple config files and nice init.d scripts, any complications introduced by removing network manager can be relatively simply patched up with a couple of bash scripts. In fact, now that I'm thinking about it, ditching NM seems like a sure-fire solution here :D

---

### Post by bab1 on 2008-12-30
See if this article helps: 
[http://www.arachnoid.com/linux/NetworkManager/index.html]("http://www.arachnoid.com/linux/NetworkManager/index.html")

---

### Post by stderr on 2008-12-30
> **bab1 said:**
> See if this article helps: 
[http://www.arachnoid.com/linux/NetworkManager/index.html]("http://www.arachnoid.com/linux/NetworkManager/index.html")

Brilliant; many thanks :D

edit: That was useful, I hadn't considered using gconf to configure it.

---

### Post by bab1 on 2008-12-30
> That was useful, I hadn't considered using gconf to configure it.

Be aware that NM has changed with the last release of Ubuntu (8.10).  NM 0.70 is what you are using in Intrepid.  

You might want to peruse the NM forum at:

[http://mail.gnome.org/archives/networkmanager-list/]("http://mail.gnome.org/archives/networkmanager-list/")

---

### Post by stderr on 2008-12-31
Cheers bab1, that'll come in handy when I get into this in a couple of days. Since NM is bound to stick around for a while, I figure I may as well attempt to make it more controllable instead of just ditching it.

I'll post anything useful I come up with.

Cheers

---

### Post by bab1 on 2008-12-31
@ stderr,

Good luck with NM.  I believe NM is something that can be enhanced by a good coder.  The use of DBUS and HAL means that we are working with some standardized interfaces.

I don't program in the appropriate language, but I do have 20 odd years as a Solaris/Linux Systems Administrator.

See my further thoughts on NM at: 
[http://ubuntuforums.org/showthread.php?p=6469022#post6469022]("http://ubuntuforums.org/showthread.php?p=6469022#post6469022")

I'm looking forward to your comments and ideas.

---

### Post by stderr on 2009-01-02
Thanks bab1. The reservation you raised in that other post regarding moving from the 'everything is a file' philosophy is where my dislike eminates from; however, I'm prepared to give this a go. After all, with the number of DBus errors I see all the time, the time expenditure surely must pay off in the future.

That said, the DBus API rather reminds me of GTK; which isn't much of a compliment :) Heck, this may take a while... but check back, I won't forget about this mini project until I've got my DBus /etc/init.d/networking solution operating :D

---

### Post by zika on 2009-01-02
You can revert to good and old /etc/network/interfaces. take a look at the [http://ubuntuforums.org/showpost.php?p=6404146&postcount=2](http://ubuntuforums.org/showpost.php?p=6404146&postcount=2) and [http://ubuntuforums.org/showpost.php?p=6479041&postcount=22](http://ubuntuforums.org/showpost.php?p=6479041&postcount=22).

---

### Post by bab1 on 2009-01-02
> **stderr said:**
> Thanks bab1. The reservation you raised in that other post regarding moving from the 'everything is a file' philosophy is where my dislike eminates from;

I understand completely.  The familiar is...er...familiar. :-)  On the other hand, NM is distro agnostic by the virtue of not relying on the traditional whatever.conf file

>  however, I'm prepared to give this a go. After all, with the number of DBus errors I see all the time, the time expenditure surely must pay off in the future.

I think a user controlled NM type applet with roaming features that can be turned of and on would be great.  I'm sure somewhere in all the threads on this forum, roaming with NM has been discussed.  Just a thought; I wonder if that is an facet of NM to look at.
> 

That said, the DBus API rather reminds me of GTK; which isn't much of a compliment :) Heck, this may take a while... but check back, I won't forget about this mini project until I've got my DBus /etc/init.d/networking solution operating :D

Keep us all in the loop.  I think a practical applet is a great idea.  Maybe the upstream folks (Ubuntu or Gnome) will be interested.

---

