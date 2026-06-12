---
title: "medibuntu for jaunty"
date: 2010-11-30
forum: Multimedia Software
---

### Post by Joe C on 2010-11-30
Unfortunately, I am stuck running jaunty -- because my company still requires this as our standard OS for our software.  I have a computer with a fresh install of 9.04 but of course none of the medibuntu packages.  

Why, oh why did they take down jaunty from the medibuntu repository!?

Anyway, anyone know where I can get these packages now?  (w32codecs, etc.)

thanks,

jc

---

### Post by runeh76 on 2010-11-30
[http://platonic.techfiz.info/2009/02/24/medibuntu-for-jaunty-jackalope/](http://platonic.techfiz.info/2009/02/24/medibuntu-for-jaunty-jackalope/)

---

### Post by Joe C on 2010-11-30
thanks, but the problem is that the jaunty packages aren't on packages.medibuntu.org anymore -- they were removed on 2010-10-11.  i guess i'm looking for a reputable mirror that still has them?

---

### Post by runeh76 on 2010-11-30
> **Joe C said:**
> thanks, but the problem is that the jaunty packages aren't on packages.medibuntu.org anymore -- they were removed on 2010-10-11.  i guess i'm looking for a reputable mirror that still has them?


Did u try this ?

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update


Whole story:
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories")

---

### Post by Joe C on 2010-11-30
actually, i did try that before i posted.  the result is 404 not found (from wget).

that's because JAUNTY HAS BEEN REMOVED FROM MEDIBUNTU as of 2010-10-11.

does anyone know of a reputable mirror that would still have the jaunty medubuntu packages?

thanks,

jc

---

### Post by runeh76 on 2010-11-30
Any help?
[http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html](http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html)

---

### Post by Yellow Pasque on 2010-11-30
Have you tried just downloading the .debs from medibuntu lucid packages? If the requirements are met, you should be fine. For example, w32codecs just requires libc6 >= 2.0, which jaunty has.

---

### Post by mc4man on 2010-11-30
The old packages are keep on the main server, to access.
Make sure any previous entries are removed in software sources, then add this line and reload. (reopen software sources to make sure the package one is enabled, the sources line is optional.

```
deb http://packages.medibuntu.org/ jaunty free non-free
```
screen shows lines after the above was added
(tested in maverick by disabling all other sources - note the gpg error which is irrelevant to installing any packages
> sudo apt-get update
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg [197B]
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release [11.7kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources/DiffIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources/DiffIndex
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources
Fetched 198B in 1s (150B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by Joe C on 2010-11-30
Thanks everyone, for you help.  Turns out the packages are (evidently) indeed still on the server.

I did a sudo apt-get update manually, and then for some reason I was able to install packages such as w32codecs just fine.  I had been using synaptic and had hit the reload button after adding medibuntu to my sources.list and adding the gpg key, but for some reason it wasn't finding w32codecs until after I ran sudo apt-get update from the command line.

jc

---

