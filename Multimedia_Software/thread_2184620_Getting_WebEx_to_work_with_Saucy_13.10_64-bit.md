---
title: "Getting WebEx to work with Saucy 13.10 64-bit"
date: 2013-10-29
forum: Multimedia Software
---

### Post by perpetualv on 2013-10-29
I was having a very hard time getting webex to work under Saucy.  Up until now I've been able to just install a java plugin, install ia32-libs, and I was good to go.  With Saucy ia32-libs is gone, so it is left up to us to figure out which 32-bit libraries we need to install.  I'd struggled blindly installing this and that until I found the answer.


I got the clue I needed from this post:
[http://blogs.kde.org/2013/02/05/ot-how-get-webex-working-suse-linux-122-64bit#comment-9534](http://blogs.kde.org/2013/02/05/ot-how-get-webex-working-suse-linux-122-64bit#comment-9534)


and for anyone who wants it, here is a step-by-step method to follow that works every time (so far)

1. Install JDK and configure java plugin for browser.  No need for a 32-bit JDK or Firefox

2. Try to start a webex.  This will create $HOME/.webex/1324/<lots of 32 bit .so files>

3. Check those .so libraries for unresolved dependencies by running ldd against them.  For example:


```
ldd $HOME/.webex/1324/*.so >>check.txt

```Look in check.txt for anything that is not found.  For example, I found:


```
libdbr.so:
        linux-gate.so.1 =>  (0xf7742000)
        libjawt.so => not found
        libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf75e6000)
        libXmu.so.6 => not found
        libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf75e0000)

```

4. Find what packages provide that file by installing apt-file with:
```
sudo apt-get install apt-file
apt-file update

```note: apt-file update will take a while, go get a cup of tea


then locate which package contains your missing libraries with:
```
apt-file search libXmu.so.6
apt-file search libjawt.so

```

5. and fix it using:


```
apt-get install -y libxmu6:i386
apt-get install -y libgcj12-awt:i386

```

---

### Post by corentin.dupont on 2013-11-11
Hi,
I tried your method, some of the library not found are gone.
However, doing:
```
apt-get install -y libgcj12-awt:i386
```
Does not remove the message:
```

$ ldd *.so | grep not
libjawt.so => not found
```

Webex is starting, the share screen feature seems to work.
**However the sound is not working.**

If I remember those sound issues were removed by installing java 32bits.
I tried to follow this tutorial: [http://www.theunixtips.com/setup-webex-on-64-bit-ubuntu-12-04-using-32-bit-oracle-java](http://www.theunixtips.com/setup-webex-on-64-bit-ubuntu-12-04-using-32-bit-oracle-java)
But when I put the 32bits version of file libnpjp2.so in the plugins folder of firefox, the plugin doesn't show up in plugin page.
If I put the 64bits version of file libnpjp2.so, it works (without sound).
Which java livrary is in charge of the sound?

---

### Post by perpetualv on 2013-11-12
Corentin - sorry, all I worked on was getting desktop and application sharing, didn't do anything with audio.  One of my systems is all 32-bit (OS, Firefox/Chrome, Java) and I haven't noticed that Audio works on that one either so I'm guessing 32-bit java isn't the answer.

If you still want to get libgcj12-awt:i386 you'll find it here
[http://packages.ubuntu.com/saucy/libgcj12-awt](http://packages.ubuntu.com/saucy/libgcj12-awt)

---

### Post by corentin.dupont on 2013-11-12
Thanks perpetualv.
How do you get the sound for your meetings, then?

---

### Post by tstaerk on 2014-05-21
I love you :) It works, I am writing this from the remote computer :)

---

### Post by corentin.dupont on 2014-05-23
Please see:
[http://askubuntu.com/questions/368270/how-to-i-make-cisco-webex-work-with-13-10-64bit/](http://askubuntu.com/questions/368270/how-to-i-make-cisco-webex-work-with-13-10-64bit/)
for a complete answer.

---

