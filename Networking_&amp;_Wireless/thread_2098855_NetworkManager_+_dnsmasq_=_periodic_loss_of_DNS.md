---
title: "NetworkManager + dnsmasq = periodic loss of DNS"
date: 2012-12-27
forum: Networking &amp; Wireless
---

### Post by mtreece on 2012-12-27
Greetings,

System information:
```
$ uname -a && cat /etc/*release
Linux pixel 3.6.10-030610-generic #201212101650 SMP Mon Dec 10 21:51:40 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
NAME="Ubuntu"
VERSION="12.04.1 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.1 LTS)"
VERSION_ID="12.04"
```

I've been having trouble recently with my network in that, at "random" times, I will lose DNS lookup capability (and thus, a slew of other resulting problems).

When this happens, I usually noticed it via web-browsing, but since I wanted to capture precise times this would occur, I wrote a simple cronjob to (every minute) run a DNS lookup of 'google.com' and log whenever DNS would fail.

Excerpt from log:
> Thu Dec 27 18:54:11 EST 2012 - DNS lookup failed of "google.com".
Thu Dec 27 18:55:11 EST 2012 - DNS lookup failed of "google.com".
Thu Dec 27 18:56:11 EST 2012 - DNS lookup failed of "google.com".
Thu Dec 27 18:57:11 EST 2012 - DNS lookup failed of "google.com".
Thu Dec 27 18:58:11 EST 2012 - DNS lookup failed of "google.com".
Thu Dec 27 18:59:11 EST 2012 - DNS lookup failed of "google.com".
Thu Dec 27 19:00:11 EST 2012 - DNS lookup failed of "google.com".
Thu Dec 27 19:01:11 EST 2012 - DNS lookup failed of "google.com".
Thu Dec 27 19:02:11 EST 2012 - DNS lookup failed of "google.com".
Thu Dec 27 19:03:11 EST 2012 - DNS lookup failed of "google.com".
Thu Dec 27 19:04:11 EST 2012 - DNS lookup failed of "google.com".
Thu Dec 27 19:05:11 EST 2012 - DNS lookup failed of "google.com".
Thu Dec 27 19:06:11 EST 2012 - DNS lookup failed of "google.com".
Thu Dec 27 19:07:11 EST 2012 - DNS lookup failed of "google.com".
Thu Dec 27 19:08:11 EST 2012 - DNS lookup failed of "google.com".
Thu Dec 27 19:09:11 EST 2012 - DNS lookup failed of "google.com".
Thu Dec 27 19:10:11 EST 2012 - DNS lookup failed of "google.com".
Thu Dec 27 19:25:11 EST 2012 - DNS lookup failed of "google.com".
Thu Dec 27 19:26:11 EST 2012 - DNS lookup failed of "google.com".

The only two ways to "fix" this error, that I've found so far, are to either:

[LIST=1]
[*]restart the computer
[*]open Network Manager (via gnome 3 panel) and disable / re-enable my wired connection. Or, if the click+point way failed (as it mysteriously did for me once), execute: ```
$ gnome-control-center network
```
[/LIST]

After getting a glimpse of when the DNS problems started, I started looking through my logs and I think I've found what the cause is:

```
$ grep 'dnsmasq.* FAILED' /var/log/syslog -C 5 | tail -n 36
--
Dec 27 19:10:38 pixel dnsmasq[18312]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Dec 27 19:10:38 pixel dnsmasq[18312]: using nameserver 192.168.1.254#53
Dec 27 19:10:38 pixel NetworkManager[1179]: <info> DNS: starting dnsmasq...
Dec 27 19:10:38 pixel NetworkManager[1179]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Dec 27 19:10:38 pixel dnsmasq[18315]: failed to create listening socket for 127.0.0.1: Address already in use
Dec 27 19:10:38 pixel dnsmasq[18315]: FAILED to start up
Dec 27 19:10:38 pixel NetworkManager[1179]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Dec 27 19:10:38 pixel NetworkManager[1179]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv6 routing and DNS.
Dec 27 19:10:38 pixel NetworkManager[1179]: <warn> dnsmasq exited with error: Network access problem (address in use; permissions; etc) (2)
Dec 27 19:10:38 pixel NetworkManager[1179]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Dec 27 19:10:38 pixel dnsmasq[18312]: exiting on receipt of SIGTERM
--
Dec 27 19:24:55 pixel dnsmasq[19029]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Dec 27 19:24:55 pixel dnsmasq[19029]: using nameserver 192.168.1.254#53
Dec 27 19:24:55 pixel NetworkManager[1179]: <info> DNS: starting dnsmasq...
Dec 27 19:24:55 pixel NetworkManager[1179]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Dec 27 19:24:55 pixel dnsmasq[19032]: failed to create listening socket for 127.0.0.1: Address already in use
Dec 27 19:24:55 pixel dnsmasq[19032]: FAILED to start up
Dec 27 19:24:55 pixel dnsmasq[19029]: exiting on receipt of SIGTERM
Dec 27 19:24:55 pixel NetworkManager[1179]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Dec 27 19:24:55 pixel NetworkManager[1179]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv6 routing and DNS.
Dec 27 19:24:55 pixel NetworkManager[1179]: <warn> dnsmasq exited with error: Network access problem (address in use; permissions; etc) (2)
Dec 27 19:24:55 pixel NetworkManager[1179]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
--
Dec 27 19:36:13 pixel NetworkManager[1179]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Dec 27 19:36:13 pixel NetworkManager[1179]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Dec 27 19:36:13 pixel NetworkManager[1179]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv6 routing and DNS.
Dec 27 19:36:36 pixel NetworkManager[1179]: <info> DNS: starting dnsmasq...
Dec 27 19:36:36 pixel dnsmasq[19790]: failed to create listening socket for 127.0.0.1: Address already in use
Dec 27 19:36:36 pixel dnsmasq[19790]: FAILED to start up
Dec 27 19:36:36 pixel NetworkManager[1179]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Dec 27 19:36:36 pixel dnsmasq[19725]: exiting on receipt of SIGTERM
Dec 27 19:36:36 pixel NetworkManager[1179]: <info> DNS: starting dnsmasq...
Dec 27 19:36:36 pixel dnsmasq[19793]: started, version 2.59 cache disabled
Dec 27 19:36:36 pixel dnsmasq[19793]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
```

As you can see, in each instance, NetworkManager (for whatever reason, it keeps updating very frequently?) will SIGTERM the old dnsmasq then try to spawn a new one. However, when my problem occurs, dnsmasq is delayed in exiting, thus keeping the socket alive, thus preventing the new dnsmasq from acquiring it ... and so the new dnsmasq dies, and moments later, so does the old dnsmasq.

Anyone else think this could be a bug?

I can't really say what new changes I've done to my system, since this is a new computer, and I've done a LOT of work to it, but nothing network related.

I found on [this forum post]("http://ubuntuforums.org/showthread.php?t=1968061") that a user can disable dnsmasq; I'm tempted to try that if I can't solve my problem otherwise, but I figured I'd post this here to see if anyone has any suggestions / ideas / similar experiences.


Thank you!

~mtreece

---

### Post by ZippyUbu on 2012-12-27
Hi, 

```
Dec 27 19:10:38 pixel dnsmasq[18315]: failed to create listening socket for 127.0.0.1: Address already in use
Dec 27 19:10:38 pixel dnsmasq[18315]: FAILED to start up
```You could try this: [post]("http://sokratisg.net/2012/03/31/ubuntu-precise-12-04-get-rid-of-nms-dnsmasq-and-setup-your-own/")

Although you may not have upgraded, you could try anyway...

--
Zu

---

### Post by mtreece on 2012-12-27
> **ZippyUbu said:**
> Hi, 

```
Dec 27 19:10:38 pixel dnsmasq[18315]: failed to create listening socket for 127.0.0.1: Address already in use
Dec 27 19:10:38 pixel dnsmasq[18315]: FAILED to start up
```You could try this: [post]("http://sokratisg.net/2012/03/31/ubuntu-precise-12-04-get-rid-of-nms-dnsmasq-and-setup-your-own/")

Although you may not have upgraded, you could try anyway...

--
Zu

Zu,

Thanks for the tip :). That solution seems similar to a few other things I've read, but it seems to just be a workaround by making dnsmasq NetworkManager-independent?

Is this the best route to go?

I'm also wondering if this is something others have experienced: if the problem is a race-condition of sorts with dnsmasq being SIGTERM'ed just in time for a new instance, this aught to be a bigger issue than just what I'm seeing.

---

### Post by ZippyUbu on 2012-12-29
I've read quite a few posts that people are running independently; some people would say that's the only way to go. Myself, I'm partial to running things as designed but that's not always possible ;)

You do have the option of removing Network Manager altogether and using dnsmasq but like you stated earlier you also have the option to disable dnsmasq.

> I'm also wondering if this is something others have experienced: if the  problem is a race-condition of sorts with dnsmasq being SIGTERM'ed just  in time for a new instance, this aught to be a bigger issue than just  what I'm seeing. Agreed, you can check to see if there are any related bugs although I had quick look and didn't see any related - 

[https://bugs.launchpad.net/ubuntu/+source/dnsmasq](https://bugs.launchpad.net/ubuntu/+source/dnsmasq)
[https://bugs.launchpad.net/ubuntu/+source/network-manager](https://bugs.launchpad.net/ubuntu/+source/network-manager) 

You may want to try both options above to see which suits your environment better.

---

### Post by praseodym on 2012-12-29
Uncomment "dns=dnsmasq" in the file /etc/NetworkManager/NetworkManager.conf. Maybe uninstalling the package "resolvconf". Rebbot after that.

---

### Post by jdthood on 2013-01-04
This is interesting. Please *do* file a bug report against the dnsmasq package in Launchpad.

Also do try commenting out "dns=dnsmasq" in /etc/NetworkManager/NetworkManager.conf and confirm that that cures the problem.

Do not uninstall resolvconf.

---

### Post by CharlesA on 2013-01-04
The only reason to uninstall resolvconf is if you want to configure your DNS settings yourself.

Of course, you could just use resolvconf to configure them for you.

So basically, comment out the dns=dnsmasq line and then restart network manager and see what happens.

---

### Post by jdthood on 2013-01-04
> **CharlesA said:**
> The only reason to uninstall resolvconf is if you want to configure your DNS settings yourself.

Even if you want to configure DNS settings by hand it is better to leave resolvconf installed. The reason is that when resolvconf is installed, most other packages refrain from overwriting /etc/resolv.conf. To edit /etc/resolv.conf by hand when resolvconf is installed, simply remove the symbolic link at /etc/resolv.conf and put your own static file there.

---

