---
title: "[hardy] How exactly is network started?"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by mirabilos on 2009-03-26
I find myself confused from the Kubuntu 8.04 we use at work.

Of course, we have NetworkManager disabled (or so I at least hope),
because it needs to be brought up before kdm starts, so that it can
display the full list of users in the left thing (which is retrieved
from LDAP).

```
# /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

This pretty much does the trick, for now. However, I have been
given an additional task: set the hostname at system startup,
before X11 starts (because it doesn&#8217;t like its hostname being
changed from under its ar$e).

I tried to place something in /etc/dhcp3/dhclient-exit-hooks.d/
which first checks if $interface is eth0, then does a reverse
lookup on the IP, and uses logger(1) to tell me what it finds.

However, while it _is_ run on /etc/init.d/networking restart,
it is *not* run at system startup. (I was depending action on
existence of /tmp/.X0-lock for now.) Then I tried to find out
how networking, in the absence of NetworkManager, is managed
on Kubuntu, and was pretty amazed to NOT FIND AN ENTRY AT ALL
in /etc/rc2.d/ for anything network related, other than avahi,
which I&#8217;m pretty sure only does Microsoft® APIP.

Short of installing &#8222;file-rc&#8220; (I wonder if this works&#8230; know
it from Debian), I have no idea how to proceed from here.
I also found no inittab (but heard runlevel 2 is the default);
while I recall something called &#8220;upstart&#8221; being used, I have
yet to find anything related in /etc. (As if SYSV init were
not confusing enough to a person spoiled from BSD&#8230;)

---

### Post by terazen on 2009-03-26
Looking at my server here is looks like it's ran from /etc/rcS.d/.

There is a README file in there that sounds like it's what you are looking for, but I'm not the expert here.  

Can anyone confirm if this is correct?

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

---

### Post by mirabilos on 2009-03-26
Ah, indeed. And I thought rcS is only for single user mode.

Well, networking is started, but I still wonder why the DHCP
script isn't run at boot, but on a networking restart.

The other option would be to place something in /etc/rcS.d/S41&#8230;
which parses &#12300;ifconfig eth0&#12301; output. Does this seem doable?

---

### Post by khelben1979 on 2009-03-26
You can take my networking script if you wish. I'll attach it. Remove the .txt extension and copy it to /etc/init.d/

It works on my Debian Lenny system.

---

### Post by mirabilos on 2009-03-26
> **khelben1979 said:**
> You can take my networking script


Exactly for _what_?

Besides, it&#8217;s pretty much the same Hardy already has.

---

### Post by khelben1979 on 2009-03-26
> **mirabilos said:**
> Exactly for _what_?

Besides, it&#8217;s pretty much the same Hardy already has.

I thought that you had trouble in getting the network configured properly after reboot. This bash script solves the problem (at least it does in Debian).

---

### Post by mirabilos on 2009-03-26
> **khelben1979 said:**
> I thought that you had trouble in getting the network configured properly after reboot.

No, I did not write that. Did you read the posting at all?
I have a (probably very in-depth) question about the ini-
tialisation process, coupled with wondering why the DHCP
exit hooks are not called on reboot, but on issuing a ma-
nual &#12300;/etc/init.d/networking restart&#12301;, and wondered where
it was run at all. Then I went into guessing if placing an
S41 script into /etc/rc.d/ would help my original problem,
namely setting the hostname after the IPv4 PTR RR.

> **khelben1979 said:**
> This bash script solves the problem (at least it does in Debian).

Actually, they are run from dash, not GNU bash.

---

