---
title: "Hostname Resolution Problems"
date: 2005-12-08
forum: Networking &amp; Wireless
---

### Post by bakert on 2005-12-08
Hi there,

I have recently installed Ubuntu on a server on my home network.  This was a terifically painless process.  I love Ubuntu!

I'm now down to getting the little details worked out.  One thing I'd really like to sort out is hostname resolution.  I hope someone can help me.

The current situation is that the Windows clients can do everything to the Ubuntu box via hostname - ping, map drives, visit in a browser, etc. 

But the Ubuntu box has a number of problems:

1. It can't ping anyone by hostname (although ping by ip works and ping localhost works).
2. It can't mount drives to the clients with dynamic IPs via hostname (works fine via hostname for the machine with a static ip and works fine via ip).
3. It can't visit ANY clients via hostname via a browser (I get redirected off to a search in firefox) but can visit them via ip.

I think this is because Ubuntu is only using "files" (hosts) and dns (my isp's dns servers) to do lookups (in some cases?) but I tried editing /etc/nsswitch.conf's "hosts:" line to include bcast or wins and neither improved the situation (even after reboot).

The other thing is is that I'm sure this WAS working at some point, for ping at least.  So something I've done has messed it up.  Perhaps installing firestarter firewall, or setting the ADSL connection to run at boot time, or something like that.

Any help/hints/pointers/questions to help you help me, etc. greatfully received I seem to have exhausted what google can do for me given my limited starting knowledge!

Thanks, Tom.

---

### Post by ssam on 2005-12-08
can you install [zeroconf]("http://www.zeroconf.org/") on all the machines and use mdns.

you'll need avahi-daemon and libnss-mdns on linux (and to add "mdns" on to the end of the "hosts:" line in /etc/nsswitch.conf).

there is a windows client at [http://developer.apple.com/networking/bonjour/index.html](http://developer.apple.com/networking/bonjour/index.html)

---

### Post by bakert on 2005-12-08
I certainly could but I'm a bit wary of breaking everything!

Is there an apt-get type install for zeroconf or do I need to install it "manually"?

Thanks,

Tom

---

### Post by bakert on 2005-12-08
OK, it seems that I already HAVE zeroconf!

Must have installed when getting this far!

If I issue the command in a terminal I get:

RTNETLINK answers: Cannot assign requested address

So I assume that zeroconf sets the IP address, etc. of the machine it's run on.  That makes me think maybe it's not for me as DHCP, ip addresses, internet connection sharing, etc. are all perfect as I want them - I just want the Ubuntu machine to hook into whatever it is the Windows machines hook into in order to resolve hostnames to IP addresses.  Is that possible?

Thanks for looking!  Tom

---

### Post by sciurus on 2005-12-14
Did you install winbind? See [http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

---

### Post by bakert on 2005-12-20
I could kiss you.

apt-get install winbind

edit /etc/nsswitch.conf

from

hosts:        files dns

to

hosts:         files dns wins

and awaaaaaaay we go.

Thanks so much!

---

