---
title: "netatalk and avahi-daemon problems - services not advertising"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by fr33loder on 2010-05-13
Hi all!

I have recently installed netatalk and avahi-daemon on my lucid server but, much to my chagrin, I have to run

```

restart avahi-daemon

```every time I boot to get the service to advertise.

both avahi-daemon and netatalk have been added to the appropriate runlevels...

I'm stumped by this...any thoughts?

---

### Post by arkham on 2010-05-13
I got avahi/netatalk to play nice following the instructions here:

[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/")

If you scroll down to the 5th section regarding getting avahi to advertise services you should be set.

A

---

### Post by fr33loder on 2010-05-13
> **arkham said:**
> I got avahi/netatalk to play nice following the instructions here:

[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

If you scroll down to the 5th section regarding getting avahi to advertise services you should be set.

A

Hi - thanks for the reply!

This is exactly the instructions I followed to get the beastie set up - and still got this problem...

painful...

---

### Post by creamers on 2010-05-16
Just add the mdns from the guide and and install netatalk from the package manager. That is what I have done on both of my computers and it works better thn you can believe

---

### Post by peap on 2010-05-21
Check your syslog after boot. Does avahi report as follows?
```
Month XX XX:XX:XX host avahi: Avahi detected that your currently configured local DNS server serves
Month XX XX:XX:XX host avahi: a domain .local. This is inherently incompatible with Avahi and thus
Month XX XX:XX:XX host avahi: Avahi disabled itself. If you want to use Avahi in this network, please
Month XX XX:XX:XX host avahi: contact your administrator and convince him to use a different DNS domain,
Month XX XX:XX:XX host avahi: since .local should be used exclusively for Zeroconf technology.
Month XX XX:XX:XX host avahi: For more information, see http://avahi.org/wiki/AvahiAndUnicastDotLocal
```
Some ISP's are doing some funny business with the .local domain that causes avahi-daemon not to start at boot. If everything works after you've started it manually you can safely create: ```
/etc/default/avahi-daemon
``` and add the line: ```
AVAHI_DAEMON_DETECT_LOCAL=0
``` This will skip the .local domain check at boot that might cause your problem and avahi-daemon will start as it should.

---

### Post by fr33loder on 2010-05-22
Hi folks...

thanks for the ideas, tried them, but still not working.  the syslog at boot contains the following for avahi-daemon - no sign of any error I can identify:

```

May 23 08:43:07 gandalf avahi-daemon[949]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.53.
May 23 08:43:07 gandalf avahi-daemon[949]: New relevant interface eth1.IPv4 for mDNS.
May 23 08:43:07 gandalf avahi-daemon[949]: Registering new address record for 192.168.0.53 on eth1.IPv4.
May 23 08:43:07 gandalf avahi-daemon[949]: Withdrawing address record for 192.168.0.53 on eth1.
May 23 08:43:07 gandalf avahi-daemon[949]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.53.
May 23 08:43:07 gandalf avahi-daemon[949]: Interface eth1.IPv4 no longer relevant for mDNS.
May 23 08:43:07 gandalf avahi-daemon[949]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.53.
May 23 08:43:07 gandalf avahi-daemon[949]: New relevant interface eth1.IPv4 for mDNS.
May 23 08:43:07 gandalf avahi-daemon[949]: Registering new address record for 192.168.0.53 on eth1.IPv4.

```but when I run the 'restart' command, I get this in the syslog:

```

May 23 08:44:49 gandalf avahi-daemon[1550]: Found user 'avahi' (UID 107) and group 'avahi' (GID 118).
May 23 08:44:49 gandalf avahi-daemon[1550]: Successfully dropped root privileges.
May 23 08:44:49 gandalf avahi-daemon[1550]: avahi-daemon 0.6.25 starting up.
May 23 08:44:49 gandalf avahi-daemon[1550]: Successfully called chroot().
May 23 08:44:49 gandalf avahi-daemon[1550]: Successfully dropped remaining capabilities.
May 23 08:44:49 gandalf avahi-daemon[1550]: Loading service file /services/afpd.service.
May 23 08:44:49 gandalf avahi-daemon[1550]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.53.
May 23 08:44:49 gandalf avahi-daemon[1550]: New relevant interface eth1.IPv4 for mDNS.
May 23 08:44:49 gandalf avahi-daemon[1550]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.52.
May 23 08:44:49 gandalf avahi-daemon[1550]: New relevant interface eth0.IPv4 for mDNS.
May 23 08:44:49 gandalf avahi-daemon[1550]: Network interface enumeration completed.
May 23 08:44:49 gandalf avahi-daemon[1550]: Registering new address record for xxxx::xxx:xxxx:xxxx:xxxx on eth1.*.
May 23 08:44:49 gandalf avahi-daemon[1550]: Registering new address record for 192.168.0.53 on eth1.IPv4.
May 23 08:44:49 gandalf avahi-daemon[1550]: Registering new address record for xxxx::xxx:xxxx:xxxx:xxxx on eth0.*.
May 23 08:44:49 gandalf avahi-daemon[1550]: Registering new address record for 192.168.0.52 on eth0.IPv4.
May 23 08:44:49 gandalf avahi-daemon[1550]: Registering HINFO record with values 'X86_64'/'LINUX'.
May 23 08:44:50 gandalf avahi-daemon[1550]: Server startup complete. Host name is gandalf.local. Local service cookie is 121355744.
May 23 08:44:50 gandalf avahi-daemon[1550]: Service "gandalf AFP" (/services/afpd.service) successfully established.

```As you can see, the restart shows a lot of reference to the services files, service estblishment, etc. which don't appear in the startup...

does this raise any new thoughts?

Thanks all

Tim

---

### Post by fr33loder on 2010-05-30
I'm always loathe to bump a thread...but this is still giving me hell...

---

### Post by Matt.Sleepy on 2010-06-08
I have the exact same problem, logs also don't show an error.

i'm using 10.04 x64.

---

### Post by setlursh on 2010-06-25
I'm having the same problem. For me, it began when I started sharing via samba as well. A reply to comment #616 [here]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/") seems to indicate that the problem exists because netatalk is being started after avahi-daemon. I still haven't been able to figure out how to change the service start order, since avahi-daemon seems to now be an upstart job, and does not have symlinks in the rc*.d directories.

---

### Post by fr33loder on 2010-06-29
Well, after much trial and tribulation, I seem to have resolved the problem (touch wood).

I performed a clean install of netatalk (v.2.1-2_amd64) and avahi from the debian testing repository (A list of these can be found at [http://packages.debian.org/squeeze/amd64/netatalk/download](http://packages.debian.org/squeeze/amd64/netatalk/download)) - This obviously also required the upgrading of a number of dependencies also - one which caused me particular issue was libgcrypt11 - but this is also available from the deb testing repository - you will get a few warnings during the process due to unverified packages...didn't seem to cause me a problem...yet.

I also had to remove a number of spaces between the fields in the AppleVolumes.default file, so that there was only a single 'tab' separating path->share name->options, etc

When I have a bit of time, I will try to document the process I followed in resolving this issue.

Thanks for all your suggestions an assistance!!

---

### Post by SanDiegoSeahawk on 2010-08-28
> **setlursh said:**
> I'm having the same problem. For me, it began when I started sharing via samba as well. A reply to comment #616 [here]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/") seems to indicate that the problem exists because netatalk is being started after avahi-daemon. I still haven't been able to figure out how to change the service start order, since avahi-daemon seems to now be an upstart job, and does not have symlinks in the rc*.d directories.

Were you ever able to figure this out?  Seems odd that controlling the timing of UpStart jobs is such an obscure subject but I can't find anything about it.  

My syslog clearly shows avahi-daemon starting before afpd/netatalk which requires me to restart avahi-daemon to get it right.

Any late news on this?

---

### Post by wch on 2010-08-31
> **SanDiegoSeahawk said:**
> Were you ever able to figure this out?  Seems odd that controlling the timing of UpStart jobs is such an obscure subject but I can't find anything about it.  

My syslog clearly shows avahi-daemon starting before afpd/netatalk which requires me to restart avahi-daemon to get it right.

Any late news on this?

For what it's worth, I have this problem too, and I've filed a bug. No solution yet, though.
[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/624043](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/624043)

---

### Post by SanDiegoSeahawk on 2010-08-31
> **wch said:**
> For what it's worth, I have this problem too, and I've filed a bug. No solution yet, though.
[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/624043](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/624043)

I think there are a couple of issues at work here.  I don't always see avahi start before netatalk/afpd, sometimes it's reversed.  To me this reflects the problem of not being able to synchronize the starting of the two daemons.

The other issue is that I think avahi-daemon is just having problems launching.  When the problem occurs, the system logs only have about 3 lines for avahi.  When it launches correctly there are more like 10-15 lines of output in the system logs.

For the heck of it, I added a call to: /sbin/restart avahi-daemon in rc.local.  This only seems to address the problem some times which tells me there is something amiss with avahi-daemon during startup.

Thanks for filing the bug.  Hopefully it gets fixed.

---

### Post by Return Privacy on 2010-09-06
Hi fr33loder,
I am having the exact same problem that you did. On 10.04, I downloaded and installed netatalk, and the avahi daemon and installed them. I just followed the prompts. Then I set it all up to share a folder on the network with afp. The strange part is that I can manually log in to the Ubuntu afp share from my iMac, by going to "go to server" and typing in the ip 10.0.1.3, and putting in the ubuntu username and pw, and it logs in fine. But avahi is not broadcasting at all? I even try to issue the $ sudo /etc/init.d/avahi-daemon restart or $ sudo service avahi-daemon restart, but it won't broadcast even when I restart it? Like I said, netatalk is working because I can log into the afp share from my iMac on the network with no problems, but the afp share isn't being advertised with avahi at all. I checked in the syslog and it says this: (only the last few lines)

Sep  6 19:25:09 ubuntu10-desktop afpd[1630]: server_child[1] 1703 done
Sep  6 19:25:09 ubuntu10-desktop afpd[1696]: Setting uid/gid to 0/0
Sep  6 19:25:21 ubuntu10-desktop afpd[1705]: ASIP session:548(4) from 10.0.1.2:62331(7)
Sep  6 19:25:21 ubuntu10-desktop afpd[1630]: server_child[1] 1705 done
Sep  6 19:25:21 ubuntu10-desktop afpd[1696]: Setting uid/gid to 0/0
Sep  6 19:26:03 ubuntu10-desktop afpd[1706]: ASIP session:548(4) from 10.0.1.2:62334(7)
Sep  6 19:26:03 ubuntu10-desktop afpd[1630]: server_child[1] 1706 done
Sep  6 19:26:03 ubuntu10-desktop afpd[1696]: Setting uid/gid to 0/0
Sep  6 19:26:05 ubuntu10-desktop afpd[1696]: Setting uid/gid to 0/0
Sep  6 19:26:05 ubuntu10-desktop afpd[1696]: ipc_write: command: 2, pid: 1696, msglen: 24
Sep  6 19:26:05 ubuntu10-desktop afpd[1630]: ipc_read: command: 2, pid: 1696, len: 24
Sep  6 19:26:05 ubuntu10-desktop afpd[1630]: Setting clientid (len 16) for 1696, boottime 4C76E90C
Sep  6 19:26:05 ubuntu10-desktop afpd[1630]: ipc_get_session: len: 24, idlen 16, time 4c76e90c
Sep  6 19:26:08 ubuntu10-desktop afpd[1707]: ASIP session:548(4) from 10.0.1.2:62336(7)
Sep  6 19:26:08 ubuntu10-desktop afpd[1630]: server_child[1] 1707 done

---

### Post by michael_j_w on 2010-10-25
This issue is causing grief here. full details posted at [https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/624043?comments=all](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/624043?comments=all)

But the short of it is avahi-daemon fails to advertise apple filesharing after a reboot but works perfectly after manually restarting the service. no issues with local domains here. please post a solution.

Thanks!

---

### Post by alejandro.mc on 2011-10-04
The problem is created apparently by your ISP.

Workaround proposed in launchpad:

edit with gedit the following file:



/etc/default/avahi-daemon



Change

"AVAHI_DAEMON_DETECT_LOCAL=1"

to

"AVAHI_DAEMON_DETECT_LOCAL=0"



Save and close, restart. 

This was proposed by someone in launchpad, I'm to lazy to look it up, there are many bug reports associated with avahi .local failure to load automatically (actually it loads and then it's closed automatically releasing a message.. something like that..)

Cheers..

Alejandro
Buenos Aires
Argentina

---

### Post by peap on 2012-09-04
I've had this problem for a while and I haven't been able to fix it properly either. I did however, apply a dirty fix.


To **/etc/rc.local** i added: ```
sh /path/to/bash/script.sh
```

script.sh:
```
#!/bin/bash

# Dirty but woking solution to make avahi/netatalk announce properly

service avahi-daemon stop
service netatalk stop
service netatalk start
service avahi-daemon start

```

Not pretty but atleast my shares works and are announced properly on startup/reboot.

---

