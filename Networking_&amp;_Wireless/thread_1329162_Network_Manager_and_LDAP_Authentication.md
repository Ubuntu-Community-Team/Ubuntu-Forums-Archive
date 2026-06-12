---
title: "Network Manager and LDAP Authentication"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by jlsheehan on 2009-11-17
Does anyone know how to make Karmic Network Manager and LDAP authentication work well together?

The problem is I have set up a nice LDAP authentication network but GDM can't authenticate because Network Manager does not bring up the interface until after login.

I can put the settings in /etc/network/interfaces directly but then Network Manager will no longer control the interface or give any indication of its status...

Any insight much appreciated.

Jeff

---

### Post by larseko on 2009-11-30
I'm another network administrator wondering about this...

---

### Post by jlsheehan on 2009-11-30
I have done a little more research, I think that network connections made "Available to all users" should be started during boot.

I will try this out and post back.

Jeff

---

### Post by jlsheehan on 2009-12-05
I tried it out and creating a connection that is "Available to all users" is definitely the way to go.

This connection is started at boot time and you can do LDAP auth.

Jeff

---

### Post by larseko on 2009-12-07
Thanks. Unfortunately, the networkmanager is no longer able to authenticate (thru policykit) while I have ldap set up anyway, so I'm not able to test it without removing every ldap configuration at the moment. But I was pretty sure this didn't work, as I've tried it in previous versions of ubuntu. If it works now, that's great.

A thread about my authentication issues which I have to resolv...:

[http://ubuntuforums.org/showthread.php?t=1341871](http://ubuntuforums.org/showthread.php?t=1341871)

---

### Post by larseko on 2009-12-09
Strange, my wireless connections that are set to be "available to all users" aren't brought up during boot. 

jlsheehan: The connection you made was a wireless one, right?

---

### Post by larseko on 2009-12-09
Well, actually, it works. I was perhaps just too quick, trying to logon before the network connection had settled. 

However, as a sysadmin, there's a slight problem with the network manager approach: by default, it let's the users fiddle with their network settings. This could be an advantage in some circumstances, for instance when the user has moved the PC while logged on, and lost connection. The disadvantage is obvious: the users are able to screw up their profile's network setting.

So... how do you ensure that any changes to the network by the user aren't saved? If they have access to write at all... Since the terminals are set up with NFS home directories and LDAP authentication, I don't want them to accidentally change network.

---

