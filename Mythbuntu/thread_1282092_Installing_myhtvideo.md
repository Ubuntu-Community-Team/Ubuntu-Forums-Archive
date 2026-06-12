---
title: "Installing myhtvideo:"
date: 2009-10-03
forum: Mythbuntu
---

### Post by zymurgist on 2009-10-03
I am in the process of (re)building a mythbuntu box. I have pretty much everything working well, except the DVD player, so I am trying to install mythvideo.

I did a apt-get install mythvideo and got this:

```

aasland@Myth:~$ sudo apt-get install mythvideo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythvideo: Depends: libmyth-python but it is not going to be installed
E: Broken packages

``` 

So I did apt-get install libmyth-python:

```

aasland@Myth:~$ sudo apt-get install libmyth-python
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libmyth-python: Depends: python (< 2.6) but 2.6.2-0ubuntu1 is to be installed
E: Broken packages
aasland@Myth:~$ 


```

but ... I already have python 2.5 installed:

```
aasland@Myth:~$ sudo apt-get install python2.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python2.5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
aasland@Myth:~$ 

```

The most recent thing I installed prior to this was Avenard's VDPAU drivers, which gave me an error on the make but in the end, it works. I just can't for the life of me remember what that error was ....

Any ideas how I can fix this without starting over with a fresh install of Ubuntu?

---

