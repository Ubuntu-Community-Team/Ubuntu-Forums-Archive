---
title: "Problems while using ubuntu 12.04 to connect to the network"
date: 2012-05-04
forum: Networking &amp; Wireless
---

### Post by NightKnight on 2012-05-04
Hello, everybody, I've got this problem for a few days, and it drives me crazy!!!

I used Acer 4741g, and I updated my pc from 11.10 to 12.04 three days ago, then I found that its' hard for me to surf the internet. 

When i use Chromium, it will tell me the webpage is not available, because of dns lookup failed,
for the firefox, it tell me server not found.
Even when i used apt to update or download softwares, it tells me that "Something wicked happened resolving 'deb.opera.com:http' (-5 - No address associated with hostname)". 

I tried to set the dns server address manualy, but still not work.
Of course, the network is ok, the 11.10 works well, and my friends' Windows works well too.

anybody can help me? appreciated for any suggestions...:confused:

---

### Post by NightKnight on 2012-05-04
hello? anybody here? any suggestions?

---

### Post by Mike V on 2012-05-05
Anyone?

I'm having the same problem, I run Maverick and Arch on the same machine I'm running Precise and I do not have any problem whatsoever.

I tried as suggested in this thread:
[http://ubuntuforums.org/showthread.php?t=1968061](http://ubuntuforums.org/showthread.php?t=1968061)

But nothing happened, the problem is still the same, after that I changed the DNS in:

/etc/dhcp/dhclient.conf

But doesn't work either.

Any help would be very much appreciated.

---

### Post by Nakadomarin on 2012-05-05
Sorry, I guess disregard this, as I somehow overlooked the link that suggests that one of the posters already tried this.  It DID however seem to work for me, although I actually tried it after following this link:

[http://ubuntuforums.org/showthread.php?t=1971969](http://ubuntuforums.org/showthread.php?t=1971969)

Again, apologies...



> Hi there,

So, I'm by no means a linux expert, have no idea what half the daemons are doing in the background, but I'm reasonably intelligent and wasted most of my morning trying to fix my own (recently upgraded) installation of Ubuntu 12.04 and THINK that I've got a fix, although somebody who knows what he/she is talking about might better explain what it is that this "fixes".  Over the past couple days, I noticed the same bizarre spotty network access and assumed it had to do with either Comcast sucking or my internet being throttled, neither of which wound up being the case after talking to customer service.  Anyhow, after much wasted time, and observing that my connection wasn't actually dropping, as once I started downloading the ISO for Ubuntu 12.04 (was pretty close to just bailing and reinstalling from scratch), the connection and speed were fine.  This got me wondering if the issue was DNS.  If you start Googling that, I think other folks are having similar issues...

Anyhow, long story short, I think the issue is something called "dnsmasq", which apparently is new to 12.04.  There's some discussion of it here, although I'm still not sure I really understand what it's doing:

[http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/]("http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/")

If you disable this as described in that link, ie:

```
sudo nano /etc/NetworkManager/NetworkManager.conf
```

Comment the line:

dns=dnsmasq

to 

#dns=dnsmasq

Save (Ctrl-O).  Close (Ctrl-X).

```
sudo restart network-manager
```

After doing that, Chromium is happy again.  Again, I should warn you that I don't really understand what the implication of disabling "dnsmasq" is, but maybe some moderator or administrator can see whether that shines any light on the issue?  Hopefully this resolves your problem as it did mine.

---

### Post by NightKnight on 2012-05-06
:lolflag:Thanks very much, i'll try it later, and then tell you whether it works.

---

### Post by Orion8 on 2012-07-11
Thanks, Nakadomarin!  This worked great for me.  I've not had any wireless problems but my wired connection was giving me fits since upgrading.

---

### Post by mattsvensson on 2012-07-13
I had connectivity issues as well and was able to finally narrow it down (with help from other forums) to adding the below entries to the below two files. Looks like Ubuntu was trying to resolve the DNS servers and having DNS resolution issues doing so (ironic, no?).

Entries to add - these are Comcast DNS servers:
nameserver 75.75.75.75
nameserver 75.75.76.76

Files to add it to:
/etc/resolv.conf
/etc/resolvconf/resolv.conf.d/head

Before there was just:
nameserver 127.0.0.1
search hsd1.ga.comcast.net

---

### Post by gtsfer on 2013-02-17
_**Fix for Network Issues in 12.04 LTS**_
This absolutely WORKS!  And makes sense too.  I just installed Ubuntu  12.04 on an old Toshiba Satellite after upgrading memory and hard disk.    I had the exact same issues with internet dropping out intermittently.    Wireless worked FINE.   Hard wired internet was a pain in the butt,  in and out.

I tried maybe 3 other "fixes" to no avail.  Investigating your posted  links and it made good sense.  This definitely is the fix and it appears  to be clean and affect nothing else.    **Comment Out dnsmasq in Networkmanager.conf**

This belongs in release notes / post install patches or something.   Thank you!  I'm reproducing these instructions below.

[U][B]Instructions to Comment Out dnsmasq
[/B][/U][FONT=Arial, sans-serif][SIZE=2]$ sudo nano /etc/NetworkManager/NetworkManager.conf[/SIZE][/FONT]
  [FONT=Arial, sans-serif][SIZE=2]Comment the line: 	dns=dnsmasq		to	#dns=dnsmasq
Save (Ctrl-O). Close (Ctrl-X).[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]$ sudo restart network-manager[/SIZE][/FONT]
 
That's it!   Done.    I was immediately able to connect and stay online without any issues.

---

### Post by jdthood on 2013-02-17
> **mattsvensson said:**
> These are Comcast DNS servers:
nameserver 75.75.75.75
nameserver 75.75.76.76

Files to add it to:
/etc/resolv.conf
/etc/resolvconf/resolv.conf.d/head

Before there was just:
nameserver 127.0.0.1
search hsd1.ga.comcast.net

You solved the problem, but not in the right way. Adding "nameserver" lines to /etc/resolvconf/resolv.conf.d/head does ensure that those lines end up in /etc/resolv.conf but this is not what you want if you connect to another network, for example.

The problem was almost certainly that the forwarding nameserver dnsmasq, which listens at 127.0.0.1, was either incorrectly configured or was malfunctioning as reported in bug #1003842. The correct way to solve that would have been to fix the dnsmasq configuration or to disable dnsmasq. Probably it would have sufficed to edit /etc/NetworkManager/NetworkManager.conf and comment out the line "dns=dnsmasq" (so that it looked like: "#dns=dnsmasq") and restart network-manager.


> **gtsfer said:**
> This absolutely WORKS!

Likewise in your case.

---

