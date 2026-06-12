---
title: "Browser(s) not working properly"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by Snapdog on 2010-03-20
Alright I just installed Linux as the only OS and got it all set up but now I have a problem with firefox or actually any browser. As far as I understand my internet works fine, I was able to download updates from the software center and various programs too. My problem is that when I try to go to any other website than google the browser just freezes up. The bar in the left bottom corner just says "Waiting for <site name>" Strangely google and google mail works. Ive tried going through all of the network settings but I am at a loss now :(

We have a ADSL Ethernet Router and a ZyXEL Wireless Router.

Any ideas? :(

---

### Post by Iowan on 2010-03-20
Check contents of */etc/resolv.conf* That should contain your nameservers. There have been a couple of similar threads - I'm trying to remember some causes. They seem as varied as installing/removing **resolvconf** to drivers, to ACPI settings.

---

### Post by Snapdog on 2010-03-21
Could you possibly explain more in detail what to do and from where since im quite new to this stuff? :D

Thank you.

---

### Post by Iowan on 2010-03-21
Open a terminal (Applications>Accessories>Terminal) and enter:```
cat /etc/resolv.com >resolv.txt
```Copy that file to USB drive, floppy, or other media so it can be opened on whatever machine you're using to access Internet - post results here.

---

### Post by kio_http on 2010-03-21
Try using Opera and post results.

---

### Post by Snapdog on 2010-03-21
I've tried almost every browser that I could find on the software center with no luck. I have noticed that some of the downloads do not work properly on the software center, which in turn jams my synaptic package manager program up(=not letting me use it for other programs since it wants the former program to finish).

I couldn't get Opera since I couldn't find it on the software center and their site doesn't work for me. It was just says "waiting for opera.com" and doesn't load the page.

Anyways I typed the command in the terminal and it said that there's no such directory.
I looked the up in the folders and noticed that I only have something called /etc/resolvconf/update-libc.d/ and in there a shell-script file called "avahi-daemon"

I opened that file in a text editor and this is what I got:

#!/bin/sh
#
# If we have an unicast .local domain, we immediately disable avahi to avoid
# conflicts with the multicast IP4LL .local domain

if [ -x /usr/lib/avahi/avahi-daemon-check-dns.sh ]; then
  exec /usr/lib/avahi/avahi-daemon-check-dns.sh
fi

---

