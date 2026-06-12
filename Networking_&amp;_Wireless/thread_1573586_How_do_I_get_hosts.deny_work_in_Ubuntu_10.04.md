---
title: "How do I get hosts.deny work in Ubuntu 10.04"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by foamcarver on 2010-09-12
I have read the man files on hosts (deny/allow) and think I understand how they are supposed to work but reality has proven me wrong.

My simple test case was to add "ALL: ALL " to the end of hosts.deny which I though should make the Internet not work.  I can still look up hosts fine so apparently I don't understand these files or Ubuntu is ignoring them.

This is my hosts.deny file
```
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.
#
# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID
ALL: ALL
```
my hosts.allow
```
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
```
and hosts
```
127.0.0.1	localhost
127.0.1.1	10-04-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
hosts.deny is the only file I have edited (so far)

Any help with why this is not denying my connection to the internet is appreciated.  Once I understand this I will delve into more useful filtering but at the moment I want to keep it simple as possible (make my network useless).

I have young children and want to limit them to a very few web sights.  Thought the hosts files looked like an easy way to do this but so far its not working.

---

### Post by gzarkadas on 2010-09-13
These files work only with services that either:

-- have been linked against the libwrap library during compilation of their sources
-- are spawned from the inetd (Ubuntu uses as default the openbsd inetd) superserver, using tcpd to exec them inside the configuration file /etc/inetd.conf

The situation is that most services that are usually enabled by default in Ubuntu do not use either inetd and/or libwrap. For example Apache does not (neither can in the newer versions).

In addition, the purpose of those files is to control / disallow _incoming_ connections. You want to control / dissalow _outgoing_ connections. To do what you want, have a look at [http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/). Also, if you are interested in other aspects of control, you can have a look at [this recent thread]("http://ubuntuforums.org/showthread.php?t=1572443").

[U]Relevant Files:
[/U]/etc/inetd.conf
/etc/init.d/openbsd-inetd
/etc/hosts.allow
/etc/hosts.deny
[U]Relevant Links:
[/U]```

man hosts_access
man hosts_options
man tcpd

```
[http://en.wikipedia.org/wiki/TCP_Wrapper](http://en.wikipedia.org/wiki/TCP_Wrapper)
[http://www.comptechdoc.org/os/linux/usersguide/linux_uginetd.html](http://www.comptechdoc.org/os/linux/usersguide/linux_uginetd.html)
[http://rute.2038bug.com/node32.html.gz](http://rute.2038bug.com/node32.html.gz)
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) (Look the Firewall section)

---

### Post by foamcarver on 2010-09-13
Thanks,

Sounds like I am boarding up the wrong door.  (Incoming instead of Outgoing)

I'll read through the links you included this evening (after work).  I have skimmed one of them before but thought I could avoid figuring out and setting up a proxy (guess not).

Thanks Again

---

### Post by gzarkadas on 2010-09-13
Well, you can set a default deny policy in the firewall for outgoing connections also and add allow rules only for the IP addresses of the websites that you want to allow. This process is named 'whitelisting' and is -security wise- the most safe configuration. But it does mean that you will become the proxy for adding new IPs in the list ;). However it requires minimal administrative skills. 

To find the IP of a website you can install a firefox addon ("ShowIP") so that by just visiting the website you can immediately read the IP address.

If the computer will be used only by the kids, you are done. If the computer is also used by adults, you will have to create a pair of scripts to enable/disable unrestricted outbound access when they login.

---

### Post by foamcarver on 2010-09-13
A "whitelist" is how I would like to have things set up.  There are only a few sites I want the kids to visit for now (probably less than ten).

The computer is shared for the whole family so I want the filtering to be off when big people log in.

My first idea was to run a local DNS server that I control, and only resolve domain names I want the kids to see.  I'm not sure how I would change the DNS server based on user but I did not dig into it much.

A proxy with Dansguardian is another option I thought about but I am not sure if you can configure Dansguardian as a whitelist.  

I had not thought of using the firewall, sounds like a good option though.  I'll do some digging into firewall settings.  

I'll keep pecking away at this.  Will post what I end up with.

Thanks again for all the help.

---

### Post by gzarkadas on 2010-09-14
Setting up DNS properly is a difficult task; and they are a frequent attack target. And the protection scheme can be subverted by just specifying `http://xxx.xxx.xxx.xxx/<rest-of-url>' in the browser's address bar. DansGuardian is a good solution because it looks at the content, not just the ip; If you are not willing to set it up now, study it and prepare for the future. Now, to use the firewall recipy, perform these steps:

A. Use your selected firewall tool to set the policy and make the whitelist. If you have not set a preference, use UFW. There are links to documentation in the sources I referenced.

B. Use iptables to dynamically insert / remove an allow rule at the top of the firewall chain. This works with all firewalls, because they are all frontends to iptables.

B1. Put the following two lines in your ~/.bashrc (or your ~/.bash_aliases if you use that file), so that you can invoke the commands from the terminal.
```

alias ip-open='sudo iptables -I OUTPUT 1 -p all -j ACCEPT'
alias ip-lock='sudo iptables -D OUTPUT -p all -j ACCEPT'

```B2. Make two custom launchers in your desktop (or panel, or both), so that you can invoke the commands from the GUI. In the command string(s) type:
```

gksudo iptables -I OUTPUT 1 -p all -j ACCEPT

``` and ```

gksudo iptables -D OUTPUT -p all -j ACCEPT

```C. Test thoroughly your setup. Login both as parent and as kid and see what happens.

D. Always remember that firewall changes are system-wide changes. When you unlock the output chain, your kids' processes have access too :shock:. Develop a habit to _always lock ips_ _when leaving the computer_.

Happy whitelisting :).

---

