---
title: "Update dhcp to version 4 ?"
date: 2010-11-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by muze4life on 2010-11-02
Hi folks,
I'm having strange issues with the internet/dns lookup with Ubuntu (tried out 10.04.1 & 10.10), the other distros I tried (Fedora, Mandriva) work fine, windowsXP & windows7 work fine too.
I looked at the package versions that these distros use that might affect internet/dns lookup behaviour and I only found that both Fedora and Mandriva use version 4 of dhcp while Ubuntu still uses version 3, so I thought (hope) this could be the cause.

So I wonder if Natty is (finally) gonna ship with dhcp v4 for me to have a look at it to test whether this fixes my issue.

I discussed this issue previously at
[http://ubuntuforums.org/showthread.php?t=1606968](http://ubuntuforums.org/showthread.php?t=1606968)
and no one seems to know how to fix it.

---

### Post by cariboo on 2010-11-02
Have you tried setting dhcp addresses manually in network manager?

---

### Post by muze4life on 2010-11-02
aha, didn't help.. worked the same way..

---

### Post by seeker5528 on 2010-11-03
I can't think of any reason the version of dhcp in use would affect DNS.

If the router or whaterver is acting as a DHCP server is giving it's own address as the DNS server instead of a direct line to the DNS servers of your ISP, that is sometimes an issue. If that's that case you could specify the DNS numbers for your ISP in Network Manager. You could also try the [OpenDNS](http://www.opendns.com/start/) numbers to see if they make a difference, scroll to the bottom of the page to get the DNS numbers

It's never made a difference on any of my systems, but for some people complaining of slow look ups, turning IPv6 off has been reported to help. Network manager should provide an option to turn IPv6 off now, at least with the Gnome NM utilities. Otherwise you should be able to create a file in '/etc/sysctl.d/' name ipv6.conf with the contents ```
#disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

Later, Seeker

---

### Post by muze4life on 2010-11-03
Thanks, I created that file and rebooted but still same random glitches, while anything non-Ubuntu works fine on this computer, see screenshot.

---

### Post by zika on 2010-11-03
Or, simply, add **ipv6.disable=1** to Your kernel-line...

---

### Post by seeker5528 on 2010-11-03
> **muze4life said:**
> Thanks, I created that file and rebooted but still same random glitches, while anything non-Ubuntu works fine on this computer, see screenshot.

That doesn't really look like something that would be caused by a DNS or DHCP issue, you might try clearing the browsers temporary files, then open a terminal window and type ```
firefox -safe-mode
``` to start firefox without extensions and plug-ins enabled.

If it still doesn't work close the browser, then in the open terminal window type ```
cd ~/.mozilla
mv firefox firefox.old
```

Then keep the terminal window open but start firefox as you normally would.

If things seem to work after that, you can close the browser and type ```
nautilus ~/.mozilla
```

in the terminal window, then copy the bookmark files from you old profile directory into the new one 'firefox.old/some-random-name/' for the old profile directory and 'firefox/some-random-name/' for the new one.

If none of that works, I don't know what else to suggest.

Later, Seeker

---

### Post by crjackson on 2010-11-03
> **seeker5528 said:**
> That doesn't really look like something that would be caused by a DNS or DHCP issue, you might try clearing the browsers temporary files, then open a terminal window and type ```
firefox -safe-mode
``` to start firefox without extensions and plug-ins enabled.

If it still doesn't work close the browser, then in the open terminal window type ```
cd ~/.mozilla
mv firefox firefox.old
```

Then keep the terminal window open but start firefox as you normally would.

If things seem to work after that, you can close the browser and type ```
nautilus ~/.mozilla
```

in the terminal window, then copy the bookmark files from you old profile directory into the new one 'firefox.old/some-random-name/' for the old profile directory and 'firefox/some-random-name/' for the new one.

If none of that works, I don't know what else to suggest.

Later, Seeker

I've had the same problem in the past. For me it was browser related.

---

### Post by muze4life on 2010-11-04
@Seeker
Thanks, but this stuff happens even after a clean install (of Ubuntu 10.04.1/10.10) on a formatted partition so it shouldn't be cache or browser related and as I said, somehow (magically) Fedora 14, Mandriva spring 2010.1, xp, win7 - none of these have issues on same computer (whether running from VirtualBox or from native partition).

---

### Post by seeker5528 on 2010-11-04
Not something I experience personally, but I have seen other who complained of problems with Firefox on a fresh install who indicated purging it and re-installing cleared up some issues they were having.

Because other stuff depends on Mozilla stuff it's easier to do from the command line ```
sudo dpkg --purge --force-depends firefox xulrunner-1.9.2
sudo apt-get -f install
```

Other than that, I don't know what to suggest.

Later, Seeker

---

### Post by muze4life on 2010-11-05
Thanks, I did so, same result. Chrome & Opera (on Ubuntu) behave the same way, I guess the issue isn't browser related.

---

