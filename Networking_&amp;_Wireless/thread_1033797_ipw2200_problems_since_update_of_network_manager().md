---
title: "ipw2200 problems since update of network manager(?)"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by micschk on 2009-01-07
After having worked flawlessly for over a year, a few days ago my wireless card (ipw2200) along with my soundcard stopped functioning. There seems to be some kind of problem with the loading of the modules, though I can not find out what exactly is first causing problems. I have the output of dmesg attached. Another thing is that I seem to have switched from a generic kernel to a 386 kernel (?) recently. 

The moment i first noticed the problem is when I was installing the virtualbox-ose kernel module from the unstable repos for my kernel version, I removed this right away (synaptic) but this did not resolve the issue.

I then figured it might have something to do with these updates?;
[INDENT]libnm-glib0 (0.6.6-0ubuntu5) to 0.6.6-0ubuntu5.8.04.1
libnm-util0 (0.6.6-0ubuntu5) to 0.6.6-0ubuntu5.8.04.1
network-manager (0.6.6-0ubuntu5) to 0.6.6-0ubuntu5.8.04.1
xterm (229-1ubuntu1) to 229-1ubuntu1.1[/INDENT]
Though I'm not sure any of these are the cause.. I downgraded all of them but that doesn't seem to help. Also booting into an older kernel does not resolve the problem.

Thanks for any suggestions.

> HP nc6220, Intel bg 2200 wifi card, 2.6.24-23-386 kernel

---

### Post by micschk on 2009-01-08
Anyone?

Maybe even some pointers to other places where I could find help?

---

### Post by Praxicoide on 2009-01-12
I get an error trying to download your dmesg file, if you think it's network manager, have you tried to update to Intrepid? It has Network Manager 0.7 which has been substantially overhauled. If you don't want to update Ubuntu, you could try to install just this package.

You could also try WICD to see if it's really network manager that's giving you problems.

---

### Post by kwylez on 2009-01-21
> **micschk said:**
> After having worked flawlessly for over a year, a few days ago my wireless card (ipw2200) along with my soundcard stopped functioning. There seems to be some kind of problem with the loading of the modules, though I can not find out what exactly is first causing problems. I have the output of dmesg attached. Another thing is that I seem to have switched from a generic kernel to a 386 kernel (?) recently. 

The moment i first noticed the problem is when I was installing the virtualbox-ose kernel module from the unstable repos for my kernel version, I removed this right away (synaptic) but this did not resolve the issue.

I then figured it might have something to do with these updates?;
[INDENT]libnm-glib0 (0.6.6-0ubuntu5) to 0.6.6-0ubuntu5.8.04.1
libnm-util0 (0.6.6-0ubuntu5) to 0.6.6-0ubuntu5.8.04.1
network-manager (0.6.6-0ubuntu5) to 0.6.6-0ubuntu5.8.04.1
xterm (229-1ubuntu1) to 229-1ubuntu1.1[/INDENT]
Though I'm not sure any of these are the cause.. I downgraded all of them but that doesn't seem to help. Also booting into an older kernel does not resolve the problem.

Thanks for any suggestions.

> HP nc6220, Intel bg 2200 wifi card, 2.6.24-23-386 kernel

Did you ever get your problem resolved. I am having a similar problem with 8.04

---

