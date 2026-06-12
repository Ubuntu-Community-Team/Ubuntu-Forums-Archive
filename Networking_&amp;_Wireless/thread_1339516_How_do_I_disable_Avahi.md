---
title: "How do I disable Avahi??"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by aeh on 2009-11-27
I have U 9.10 as well as U studio 9,10. Both display a message on startup that says something to the effect of 'localhost...  network discovery service is disabled'  
How do I disable it permanently?
TIA

A

---

### Post by Iowan on 2009-11-27
I thought I'd seen it under the System>Preferences>Startup Applications... but it's not there on this Jaunty laptop.

---

### Post by sisco311 on 2009-11-27
> **aeh said:**
> I have U 9.10 as well as U studio 9,10. Both display a message on startup that says something to the effect of 'localhost...  network discovery service is disabled'  
How do I disable it permanently?
TIA

A

Edit the /etc/init/avahi-daemon.conf file to something like this:
```
# avahi-daemon - mDNS/DNS-SD daemon
#
# The Avahi daemon provides mDNS/DNS-SD discovery support (Bonjour/Zeroconf)
# allowing applications to discover services on the network.

description	"mDNS/DNS-SD daemon"

start on (**never**
          and filesystem
	  and started dbus)
stop on stopping dbus
...

```

---

### Post by Riniker on 2009-11-28
I tried editing /etc/init/avahi-daemon.conf as suggested, but still get that irritating "network discovery service is disabled" pop-up every time that I login.

The avahi-daemon would appear to be really stubborn! I have even tried deleting /usr/sbin/avahi-daemon, and still get the pop-up.

---

### Post by Iowan on 2009-11-28
Check **ps -ef | avahi** to see if avahi is still running.

---

### Post by wojox on 2009-11-28
Disable:

```
sudo update-rc.d -f avahi-daemon remove
```

Enable:

```
sudo update-rc.d avahi-daemon defaults
```

---

### Post by aeh on 2009-11-28
Thanx but the problem is still unsolved....

---

### Post by wojox on 2009-11-28
Since there is no System > Administration > Services, you could download Boot-up Manager and see if you can stop it through there.

---

### Post by sisco311 on 2009-11-28
> **wojox said:**
> Disable:

```
sudo update-rc.d -f avahi-daemon remove
```

Enable:

```
sudo update-rc.d avahi-daemon defaults
```

> **wojox said:**
> Since there is no System > Administration > Services, you could download Boot-up Manager and see if you can stop it through there.

update-rc.d and bum installs/removes System-V style init scripts. In karmic, avahi-daemon is started/stopped by an Upstart job. So you cannot use update-rc.d and bum to disable the daemon.

_______________________________________________________________

It looks like avahi-daemon is also started when the network connection is established (/etc/network/if-up.d/avahi-daemon).   

To disable it, you must edit the file /etc/default/avahi-daemon as root:

```
gksu gedit /etc/default/avahi-daemon
```

and add this line:
```
AVAHI_DAEMON_DETECT_LOCAL=0
```

---

### Post by Riniker on 2009-12-05
Thanx. Changing **AVAHI_DAEMON_DETECT_LOCAL=1** to **AVAHI_DAEMON_DETECT_LOCAL=0** in /etc/default/avahi-daemon has got rid of the irritating pop-up.

---

### Post by geohei on 2009-12-13
> **sisco311 said:**
> ...
To disable it, you must edit the file /etc/default/avahi-daemon as root:

```
gksu gedit /etc/default/avahi-daemon
```

and add this line:
```
AVAHI_DAEMON_DETECT_LOCAL=0
```
I'm using Ubuntu 9.10.
I have a strange network problem ... not sure whether avahi is involved or not, nevertheless, I'd like to give it a try.

So I tried to kill the 2 avahi tasks, which are shown by "ps -ef". No success.

I have no /etc/default/avahi-daemon file. Is this normal?
Creating the file and adding AVAHI_DAEMON_DETECT_LOCAL=0 didn't make the job either. After a restart, both avahi tasks were still there!

Also, I don't have System/Administration/Services. Is this normal?

All weird ?!?!

Any help would be appreciated.

Thanks,

---

### Post by mardev on 2009-12-29
So, does this really disable **Avahi **or just stop it from removing a security threat?

---

### Post by rccarter on 2010-03-01
What worked for me was the following:

```
sudo vi /etc/avahi/avahi-daemon.conf
```

I then changed:

```
use-ipv4=yes
```

To:

```
use-ipv4=no
```

I then ran:

```
sudo /etc/init.d/avahi-daemon restart
```

Current status:

```
service avahi-daemon status
avahi-daemon stop/waiting
```

---

### Post by graylion on 2010-03-15
simply uninstall it. it's going to complain about being dependency for libnss-mdns, so uninstall that as well.

---

### Post by Poizhan on 2010-04-01
```
sudo apt-get remove avahi-daemon
```

Enter your password, and accept the changes. No more annoying popup!

---

### Post by sonicb00m on 2010-05-01
been driving me nuts for years!

---

### Post by tgerbert on 2012-02-23
If you want to disable an Upstart job, e.g. avahi, the better way is to create a **/etc/init/*<service name>*.override** file (in this case, **/etc/init/avahi-daemon.override**), the contents of that file being a single line with the word **manual** - that tells Upstart to *only* ever start that service as a result of a manual request by you, and never to start it automatically.

I didn't notice the date, hopefully I didn't resurrect an ancient thread. ;)

---

### Post by bab1 on 2012-02-23
> **tgerbert said:**
> If you want to disable an Upstart job, e.g. avahi, the better way is to create a **/etc/init/*<service name>*.override** file (in this case, **/etc/init/avahi-daemon.override**), the contents of that file being a single line with the word **manual** - that tells Upstart to *only* ever start that service as a result of a manual request by you, and never to start it automatically.

I didn't notice the date, hopefully I didn't resurrect an ancient thread. ;)

But of course... you did resurrect it.  :-(

Edit: Upstart was not a big deal back when this thread was started.

---

### Post by overdrank on 2012-02-23
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

