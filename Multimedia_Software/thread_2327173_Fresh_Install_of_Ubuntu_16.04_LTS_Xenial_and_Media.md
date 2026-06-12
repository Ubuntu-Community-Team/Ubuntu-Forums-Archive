---
title: "Fresh Install of Ubuntu 16.04 LTS Xenial and Mediatomb"
date: 2016-06-08
forum: Multimedia Software
---

### Post by wt9bind2 on 2016-06-08
Hello, I have been running Mediatomb on my old Ubuntu 12.04 headless server for a very long time, however my trusty old HP Microserver died a slow and painful death so I had a spare Dell T320 laying around and I have installed 16.04 LTS and migrated all of my data over.
Now my beloved Mediatomb is misbehaving on the new server.
If I do a sudo service mediatomb status, I see that it is running and I can get to it at: [http://localhost:49153]("http://localhost:49153/") no problem. However When I go to my uPNP device(s) such as my PS3 and WD Live TV's, Mediatomb is not there.
So, I head back to the server and type:
sudo mediatomb and bingo, it is running, can still get to the web page and can now see it on my PS3 and WD's, however this isn't so good as I want the service to be running and not have to manually invoke it.
So, I kill the service and run it as my root user by just typing meidatomb and I get this:
```
daniel@BINSVR2:~$ mediatomb
MediaTomb UPnP Server version 0.12.2 - http://mediatomb.cc/

===============================================================================
Copyright 2005-2010 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2016-06-07 08:23:26    INFO: Loading configuration from: /home/daniel/.mediatomb/config.xml
2016-06-07 08:23:26    INFO: Checking configuration...
2016-06-07 08:23:26    INFO: Setting filesystem import charset to UTF-8
2016-06-07 08:23:26    INFO: Setting metadata import charset to UTF-8
2016-06-07 08:23:26    INFO: Setting playlist charset to UTF-8
2016-06-07 08:23:26 WARNING: You enabled the YouTube feature, which allows you
                             to watch YouTube videos on your UPnP device!
                             Please check http://www.youtube.com/t/terms
                             By using this feature you may be violating YouTube
                             service terms and conditions!

2016-06-07 08:23:26    INFO: Configuration check succeeded. 
2016-06-07 08:23:26   ERROR: Error while accessing sqlite database file (/home/daniel/.mediatomb/mediatomb.db): Permission denied
```

So I go and do a ls -l on the .mediatomb folder:
```
daniel@BINSVR2:~/.mediatomb$ ls -l
total 32
-rw-r--r-- 1 root root  5317 Jun  3 18:50 config.xml
-rw-r--r-- 1 root root 18432 Jun  7 08:22 mediatomb.db -rw-r--r-- 1 root root   128 Jun  7 08:22 mediatomb.html
```

And it does't look right, so I chmod 777 so it looks like this:
```
-rwxrwxrwx 1 root root    5317 Jun  3 18:50 config.xml
-rwxrwxrwx 1 root root 5826560 Jun  7 19:44 mediatomb.db
-rwxrwxrwx 1 root root  247160 Jun  7 19:44 mediatomb.db-journal
-rwxrwxrwx 1 root root     128 Jun  7 19:05 mediatomb.html
```

Great! Now when i type "mediatomb" I get no more permission denied errors

However, If the service starts, I can get to the web page but nothing shows on my devices still. If I kill the service and manually start it with "mediatomb" I can see the web page and media tomb on my devices, however I don't want to have to manually run it.

Does anybody have any ideas?

Cheers!

---

### Post by papibe on 2016-08-19
Hi wt9bind2.

Same problem here. It seems the new default is to serve music locally (weird).

Get your NIC name with this command:
```
ip link
```
and then change the line in your /etc/default/mediatomb:
```
MT_INTERFACE="eth1"
```
where eht1 is your actual network card.

Let us know how it goes.
Regards.

---

### Post by h-julien on 2016-09-21
> **papibe said:**
> Hi wt9bind2.

Same problem here. It seems the new default is to serve music locally (weird).

Get your NIC name with this command:
```
ip link
```
and then change the line in your /etc/default/mediatomb:
```
MT_INTERFACE="eth1"
```
where eht1 is your actual network card.

Let us know how it goes.
Regards.

Hello,

I tried doing that and it still doesn't work for me.  Anywhere else I should have a look at?  When I install mediatomb on Ubuntu 14, no problem, works perfectly.

Thanks!

H

---

### Post by jofamer2 on 2016-11-03
Hello,

I also experienced the same issue and was able to resolve it taking cues from previous post. The only gap with the instructions in previous post is it doesn't guide in identifying the correct network interface to which mediatomb server should be binding to.

I followed below steps.

ifconfig 

(This lists out all the network interfaces configured on my system. From the list I identified the network interface name that secured a valid IP address from DHCP service of my router. Given I'm connecting to network via wifi, I know this has to be wireless network interface. This has to be the interface to which mediatomb should bind to). On my machine this is 'wlp2s0'

Modify /etc/default/mediatomb and change the line as below
MT_INTERFACE="wlp2s0"

Restart mediatomb service.

This fixed my problem.

---

