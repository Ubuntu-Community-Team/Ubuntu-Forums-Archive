---
title: "Can't uninstall fglrx; Synaptic now useless"
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by Lux Perpetua on 2006-06-02
I was trying to install fglrx 8.25.18 using the howtos in this forum, but somehow I bungled it so badly that now I seem to have a broken fglrx package that just won't go away. Every time I try to remove it (apt-get remove, dpkg -r, or Synaptic), I see the following error: ```
Removing xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1' with
  different file `/usr/lib/fglrx/libGL.so.1.xlibmesa', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
```and the package does not get removed. To add insult to injury, now xorg-driver-fglrx is permanently marked for complete removal in Synaptic, and there's nothing I can do to unmark it. This means that any attempt to use Synaptic for package management fails, since the first thing it tries to do is remove xorg-driver-fglrx, which fails and for whatever reason makes it abort everything else, too (WTF?). Can anybody explain this error? Please, just let me be rid of this package...

(If there's no fix, I'll just reinstall Dapper. PITA, but not a big deal, since I installed it today.)

---

### Post by st4rdr1ft3r on 2006-06-02
```

sudo mv /usr/lib/libGL.so.1 /usr/lib/libGL.so.1.backup
sudo mv /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1.2.backup
sudo apt-get remove xorg-driver-fglrx

```

---

### Post by Lux Perpetua on 2006-06-02
Thanks, I should have known it was that simple. :-)

---

### Post by xristoforosth on 2006-07-04
I have a similar problem!!!


I was trying to install fglrx 8.25.18 using the howtos in this forum, but somehow I bungled it so badly that now I seem to have a broken fglrx package that just won't go away. Every time I try to remove it (apt-get remove, dpkg -r, or Synaptic), I see the following error:

```

Removing xorg-driver-fglrx ...
dpkg-divert: mismatch on divert-to
  when removing `**diversion** of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx'
  found `**diversion** of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)


```


and the package does not get removed. To add insult to injury, now xorg-driver-fglrx is permanently marked for complete removal in Synaptic, and there's nothing I can do to unmark it. This means that any attempt to use Synaptic for package management fails, since the first thing it tries to do is remove xorg-driver-fglrx, which fails and for whatever reason makes it abort everything else, too (WTF?). Can anybody explain this error? Please, just let me be rid of this package...



What should i do to fix this problem???

---

### Post by larryni on 2006-07-07
[QUOTE=xristoforosth]
and the package does not get removed. To add insult to injury, now xorg-driver-fglrx is permanently marked for complete removal in Synaptic, and there's nothing I can do to unmark it. This means that any attempt to use Synaptic for package management fails, since the first thing it tries to do is remove xorg-driver-fglrx, which fails and for whatever reason makes it abort everything else, too (WTF?). Can anybody explain this error? Please, just let me be rid of this package...[/QUOTE]
I have the same problem and would love to get this fixed. And since I'm getting this error Amarok won't start. When I try to launch it the splash screen flashes up for a second and that's that. 

Any ideas?

---

### Post by larryni on 2006-07-07
Here's my output
> Removing xorg-driver-fglrx ...
dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
Looking around I can't find /usr/lib/libGL.so.1.2, nor do I have a /usr/share/fglrx/ directory. The closest I could find was /usr/lib/libGL.so.1 which is a broken link.

Any help greatly appreciated. I need my machine running for tonight and really don't have the time to re-install today ](*,)

---

### Post by larryni on 2006-07-07
Phew, got it sorted with a blog entry on [this page]("http://www.undiscoverable.com/category/linux/") (scroll down a bit).

And don't forget to change the following lines:

sudo dpkg-divert &#8211;rename &#8211;remove /usr/lib/libGL.so.1.2
sudo dpkg &#8211;force-all &#8211;purge xorg-driver-fglrx

to 
> sudo dpkg-divert --rename --remove /usr/lib/libGL.so.1.2
sudo dpkg --force-all --purge xorg-driver-fglrx

---

### Post by xristoforosth on 2006-07-08
> **larryni said:**
> Phew, got it sorted with a blog entry on [this page]("http://www.undiscoverable.com/category/linux/") (scroll down a bit).

And don't forget to change the following lines:

sudo dpkg-divert –rename –remove /usr/lib/libGL.so.1.2
sudo dpkg –force-all –purge xorg-driver-fglrx

to


Thanks! It worked like a charm for me!!

---

### Post by pdusen on 2008-01-12
> **larryni said:**
> Phew, got it sorted with a blog entry on [this page]("http://www.undiscoverable.com/category/linux/") (scroll down a bit).

And don't forget to change the following lines:

sudo dpkg-divert –rename –remove /usr/lib/libGL.so.1.2
sudo dpkg –force-all –purge xorg-driver-fglrx

to

All that's on that page is gibberish...

---

### Post by thejeswi.nk on 2008-04-05
:confused: I have exactly the problem that you guys had...
The link above does not work!!!
Can anybody post how to fix this problem?
Please!

---

### Post by observative on 2008-04-05
Did you try these instructions from the Ubuntu Documentation?
[https://help.ubuntu.com/community/RadeonDriver#head-229f59879c2a2b6c6635d1e189706d97f836b879](https://help.ubuntu.com/community/RadeonDriver#head-229f59879c2a2b6c6635d1e189706d97f836b879)

---

### Post by Matt26 on 2008-06-13
i am having a very similar issue with synaptic not allowing me to unmark packages set for removal (FF, FF gnome support and xulrunner) and i can't get rid of them no matter what i try- and i am having the same issue when these packages run into an error whenever synaptic tries to do anything with them- certain directories do not exist for each package and it won't get past this point.

i tried the link that larryni posted but it's dead- does anyone have an updated link to this site?  i am in bad need of a fix here.. been going on a week now with this problem.

any help is greatly apreciated.

thanks.

---

### Post by Matt26 on 2008-06-16
i'm not sure if this will help anyone else but it worked for me to fix the issue with my broken packages- basically you have to modify a file that tracks the status of all packages installed on ubuntu so that it will ignore your broken packages-as if they don't exist on the system anymore (which in my case were listed as half/partially installed) and they will then have to be installed again.

[https://answers.launchpad.net/ubuntu/+question/4838](https://answers.launchpad.net/ubuntu/+question/4838)
(details are in the grey section)

---

