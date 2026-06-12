---
title: "Cant see all computers on network...."
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by ginnie6 on 2009-01-28
We have 5 computers on the home network..2 are vista, 1 xp, and 2 ubuntu 8.04.

The vista computers can see each, other One ubuntu laptop sees the xp computer and itself, and the other ubuntu computer sees the windows network but no computers. I need for the ubuntu laptop to see the vista computers to be able to use the printer. I had this set up and working on Hardy but since the upgrade to Intrepid I can't remember how to get it to work.

Thanks!

---

### Post by Cope57 on 2009-01-28
Samba

---

### Post by ginnie6 on 2009-01-28
> **Cope57 said:**
> Samba

its installed,,,,,,,

---

### Post by ddubois on 2009-01-28
I'm having the same problem as original poster.

Let me preface by saying that I do not regularly use linux, and have no experience administering it, so I am not familiar with the techniques one might use for debugging samba issues, nor even where it's configuration files are located.

I'm a new owner of a Neuros Link, which is a pre-built ubuntu box configured with hardware/software optimized for watching streamed internet video on my television.  I would also like to use it as a network media streamer of video content stored in shared folders on my windows PC, which it ostensibly should be able to do out of the box.  So I'm only interested in samba client, not server.

To elaborate on my problem:

If I go to Network Neighborhood -> Microsoft Windows Networks on a PC on my LAN, I see "MSHOME" and "WORKGROUP".  Under the former, I see the machines "POKER" and "LEFT", and under the latter I see "PCH-A110", and underneath those, I see the folders I've shared.  Meanwhile, if I go to Network -> Microsoft Windows Networks on my Neuros Link using Computer - File Browser, I see "MSHOME" and  "WORKGROUP" (usually... sometimes it times out with an error, but a second try usually comes back with the correct information instantly).  But I see no computers and no shared directories under either windows network.  Clicking Refresh a few times has no effect.

What steps should I take to isolate, identify, and correct samba issues like this?

---

### Post by Alex22 on 2009-01-29
I will focus on the **ginnie6** post, coz you wrote too much, **ddubois**. ;)
I hope it will help ya too.

1) Firstably, Ginnie, what do you mean by: **"computer can't see another computer"**? 

a) that ping doesn't return.
b) that one comp can't access shared folders at another comp.

If a, then do the following:

On Linux machines:
```
ifconfig
```
Check the eth0 part. Things like: inet addr, Mask, Bcast.

On windoza machines:
Very similiarly, but the command is:
```
ipconfig
```
And the interface name is i don't remember, LAN or sth.

AND IN ALL LINUX AND WINDOWS MACHINES:
Address should be different on every machine, but varying only on the last part (it's simplified what i'm saying).
Mask and Bcast should be the same.

---

### Post by sysadmn62 on 2009-01-29
> **ddubois said:**
> I'm having the same problem as original poster.

Let me preface by saying that I do not regularly use linux, and have no experience administering it, so I am not familiar with the techniques one might use for debugging samba issues, nor even where it's configuration files are located.

I'm a new owner of a Neuros Link, which is a pre-built ubuntu box configured with hardware/software optimized for watching streamed internet video on my television.  I would also like to use it as a network media streamer of video content stored in shared folders on my windows PC, which it ostensibly should be able to do out of the box.  So I'm only interested in samba client, not server.

To elaborate on my problem:

If I go to Network Neighborhood -> Microsoft Windows Networks on a PC on my LAN, I see "MSHOME" and "WORKGROUP".  Under the former, I see the machines "POKER" and "LEFT", and under the latter I see "PCH-A110", and underneath those, I see the folders I've shared.  Meanwhile, if I go to Network -> Microsoft Windows Networks on my Neuros Link using Computer - File Browser, I see "MSHOME" and  "WORKGROUP" (usually... sometimes it times out with an error, but a second try usually comes back with the correct information instantly).  But I see no computers and no shared directories under either windows network.  Clicking Refresh a few times has no effect.

What steps should I take to isolate, identify, and correct samba issues like this?


Well, if it were me, I'd change all computers to use the same domain - either MSHOME or WORKGROUP.  Which one (if either) is the Neuros using?   Unless you're doing it on purpose, why complicate things?

Once that is done, it might be any of a number of problems.  It might be easier to step through the installation instructions (or this: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)) to make sure you don't have a typo or skipped step.

---

### Post by ddubois on 2009-01-30
The popcorn hour was using WORKGROUP by default, but it's offline now and irrelevant.  I got the Neuros because the PCH-A110 was nothing but trouble.  The point was, the Neuros can definately see the windows networks.  It can also ping them, and be pinged by them, FYI.

I've read this post: [http://ubuntuforums.org/showthread.php?t=190542](http://ubuntuforums.org/showthread.php?t=190542) , but I don't think this FireStarter firewall is running on my machine.  Is it possible I am running some other firewall on the Linux device I don't know about?  How might I check from my windows boxes?

In any case, I have some more information that should make the solution obvious to someone, but I don't know how to proceed.

When I "smbclient //LEFT/htdocs", I get "timeout connecting to 24.28.193.9:445".  I don't know what the heck 24.28.193.9 is, but it sure ain't my LEFT machine; that's 192.168.2.2.  When I "smbclient //LEFT/htdocs -I 192.168.2.2", I am able to connect, then successfully "ls" and see the files on that share.

Is there some sort of /etc/hosts file for NetBios names where I can map LEFT to 192.168.2.2 and POKER to 192.168.2.3?  Sure, it would be nice if the Linux box did broadcasts or whatever and dynamically grabbed the needed IPs in the formal manner, but a quick hack to a config file will suit my purposes just fine.

I'll try the [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) link now, maybe that will answer the questions I've posed.

---

### Post by dmizer on 2009-01-30
Are you using OpenDNS?

---

### Post by ddubois on 2009-01-30
> **dmizer said:**
> Are you using OpenDNS?
I don't think so.  Using the GUI network configuraiton tool, I just gave myself a static IP address, and configured my DNS server to be 192.168.2.1 (my gateway), just as I do with my windows boxes.  My gateway/router just uses whatever DNS server my ISP told me to use.

---

### Post by ddubois on 2009-01-30
Well, I feel both silly and confused. I added
192.168.2.2 LEFT
192.168.2.3 POKER
to my /etc/hosts file, and now both smbclient and the file browser work just fine.  I assumed NetBIOS names would be discovered and tracked separately (WinS?) than normal DNS hostnames, but I guess not.  Maybe there's something in my Neuros' configuration that is telling it to look for DNS first before WinS, or perhaps to look exclusively at DNS and not WinS, but since it works, I don't really need to figure it out.

---

### Post by BigBangTheory on 2009-08-13
Thanks buddy!
It worked for me too, editing /etc/hosts file . . and then typing smb://IP_addresses_of the computers_in_network 
in nautilus (launched using this command)

 ```
dbus-launch nautilus --no-desktop --browser
```

---

