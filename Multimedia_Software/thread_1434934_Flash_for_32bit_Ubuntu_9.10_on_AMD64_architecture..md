---
title: "Flash for 32bit Ubuntu 9.10 on AMD64 architecture... PLEASE HELP!"
date: 2010-03-20
forum: Multimedia Software
---

### Post by Hard Device on 2010-03-20
I am running a 32bit Ubuntu 9.10  on a netbook with AMD64 architecture.  

I have read about a 64bit Flash alpha from Adobe and other work arounds to get flash running on 64bit linux, but is there anyway to get flash to work on an AMD64 system running 32bit Ubuntu 9.10?

There's gotta be a way....

---

### Post by 2hot6ft2 on 2010-03-20
> **Hard Device said:**
> I am running a 32bit Ubuntu 9.10  on a netbook with AMD64 architecture.  

I have read about a 64bit Flash alpha from Adobe and other work arounds to get flash running on 64bit linux, but is there anyway to get flash to work on an AMD64 system running 32bit Ubuntu 9.10?

There's gotta be a way....
I'm running 32 bit on a AMD 64 bit processor all you should have to do is
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install ubuntu-restricted-extras adobe-flashplugin
```
type in your password when prompted and hit Enter it wont be displayed.
You'll have to accept the agreement for java.
That should take care of most of your multimedia.

If you get any errors then you may need to enable the medibuntu repositories by running this in a terminal first.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

---

