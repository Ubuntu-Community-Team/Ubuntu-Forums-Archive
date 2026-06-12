---
title: "Unmet dependencies"
date: 2012-07-29
forum: Multimedia Software
---

### Post by PsySc0rpi0n on 2012-07-29
I'm trying to install some packages neede to install APP SDK

When i do this

```
[COLOR=Black]apt-get install libroot-python-dev libboost-python-dev zlib1g-dev libssl-dev cmake libboost1.40-all-dev[/COLOR] 
```

I get this

```

cmake libboost1.40-all-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
zlib1g-dev is already the newest version.
cmake is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libboost1.40-all-dev: Depends: libboost-iostreams1.40-dev but it is not going to be installed
                        Depends: libboost-regex1.40-dev but it is not going to be installed
  libssl-dev: Depends: libssl0.9.8 (= 0.9.8k-7ubuntu8.6) but 0.9.8k-7ubuntu8.8 is to be installed
E: Broken packages

```


How can i solve this?

---

### Post by Laiquendi on 2012-07-29
It was somewhere on this forum.
Try:
```
sudo apt-get install -f
```or installing the dependencies by hand, or downloading .deb for them (sometimes solves the problem), or check your sources configuration, in my case turning on some of the other software sources worked.

---

### Post by PsySc0rpi0n on 2012-07-29
I've added a few lines to sources.list

```

deb http://ppa.launchpad.net/dhor/myway/ubuntu lucid main
deb http://mirrors.nfsi.pt/ubuntu/ lucid universe main restricted multiverse
deb-src http://mirrors.nfsi.pt/ubuntu/ lucid universe main restricted multiverse #Added by software-properties

```No good too!!

Where can i get the deb's?

Edited;

```
apt-get install -f libroot-python-dev libboost-python-dev zlib1g-dev libssl-dev cmake libboost1.40-all-dev
```

this didn't worked either!!!

---

### Post by PsySc0rpi0n on 2012-08-01
up

---

### Post by mc4man on 2012-08-01
I'd open up software source & under the 'updates' tab make sure that the 1st 2 are checked (updates & security

Then update your sources & see where you're at.
sudo apt-get update

> libssl-dev: Depends: libssl0.9.8 (= 0.9.8k-7ubuntu8.6) but [COLOR="Red"]0.9.8k-7ubuntu8.8 is to be installed[/COLOR]
That's quite old, the current  in lucid is 0.9.8k-7ubuntu8.13

As in - 
```
openssl (0.9.8k-7ubuntu8.8) lucid-security; urgency=low
clipped
Steve Beattie <sbeattie@ubuntu.com>  [COLOR="Red"]Tue, 31 Jan 2012[/COLOR] 01:41:34 -0800

```
vs. current - 
```
openssl (0.9.8k-7ubuntu8.13) lucid-security; urgency=low
clipped
-- Steve Beattie <sbeattie@ubuntu.com>  [COLOR="Blue"]Tue, 22 May 2012 [/COLOR]16:11:28 -0700
```

---

