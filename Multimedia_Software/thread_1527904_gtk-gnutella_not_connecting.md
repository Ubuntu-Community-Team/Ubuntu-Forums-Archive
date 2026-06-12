---
title: "gtk-gnutella not connecting"
date: 2010-07-09
forum: Multimedia Software
---

### Post by uRabbit on 2010-07-09
I'm used to LimeWire. Very straightforward. gtk-gnutella has all these frames, windows, etc. Anyways, it's not connecting. Nicotine connects fine, but people say gtk-gnutella is better, as it has access to more.

---

### Post by Sonsum on 2010-07-10
> **uRabbit said:**
> I'm used to LimeWire. Very straightforward. gtk-gnutella has all these frames, windows, etc. Anyways, it's not connecting. Nicotine connects fine, but people say gtk-gnutella is better, as it has access to more.

Does Limewire work in Wine? Cause that sounds like the best option for you.

---

### Post by uRabbit on 2010-07-10
> **Sonsum said:**
> Does Limewire work in Wine? Cause that sounds like the best option for you.

I have no idea. Wine has been nothing but trouble for me. Haven't gotten anything with Gold rating to run. *shrug*

---

### Post by gandaran on 2010-07-10
are using the ubuntu repository version? 
that version is old and I think it gives an error message, you can update it, download the new version [here]("http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html")

---

### Post by Yellow Pasque on 2010-07-10
In Lucid, the Ubuntu repo has the latest stable gtk-gnutella (0.96.8), so no other version should be necessary.

@uRabbit: Have you set up port forwarding on your router, and if so, have you entered the port number in gtk-gnutella options?

---

### Post by uRabbit on 2010-07-10
Interesting... I opened gtk-gnutella to look at my port forwarding settings, and it had a window pop up saying I had an ancient version. I go to the website, download the Lucid amd64 version (I assume that's the one I need for 64-bit), and when it gets to the Package Installer, it says 'same version already installed'...

gtk-gnutella still recognizes it as an old version. 0.96.6

edit: Don't know how to set up the network. I'm using a switch (not a router), if that matters. I don't like all these manual settings...

---

### Post by Yellow Pasque on 2010-07-10
My apologies. I could have sworn I reported a bug about the old version right before Lucid was released, and a dev did an FFe for the new version. I don't see the bug report though, so maybe it was reversed.

Good news: it is possible to build latest stable 0.96.8 from source fairly easily:
```
sudo apt-get install build-essential wget fakeroot debhelper
sudo apt-get build-dep gtk-gnutella
cd ~/
wget http://downloads.sourceforge.net/project/gtk-gnutella/gtk-gnutella/0.96.8/gtk-gnutella-0.96.8.tar.bz2?use_mirror=cdnetworks-us-1&ts=1278787510
tar xjf gtk-gnutella-0.96.8.tar.bz2
cd gtk-gnutella-0.96.8/
fakeroot debian/rules binary
cd ..
sudo dpkg -i gtk-gnutella_0.96.8-0*.deb
```

OR if you want to use an svn snapshot .deb: [http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html](http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html)

EDIT: Here was the ancient version bug: [https://bugs.launchpad.net/ubuntu/+source/gtk-gnutella/+bug/538900](https://bugs.launchpad.net/ubuntu/+source/gtk-gnutella/+bug/538900) They said they would grant an FFe, but they never put 0.96.8 in Lucid...

---

### Post by gandaran on 2010-07-10
> **uRabbit said:**
> Interesting... I opened gtk-gnutella to look at my port forwarding settings, and it had a window pop up saying I had an ancient version. I go to the website, download the Lucid amd64 version (I assume that's the one I need for 64-bit), and when it gets to the Package Installer, it says 'same version already installed'...

gtk-gnutella still recognizes it as an old version. 0.96.6

edit: Don't know how to set up the network. I'm using a switch (not a router), if that matters. I don't like all these manual settings...
then you downloaded the wrong version, I have the 0.96.9 and it works, the version from ubuntu repo doesn't connect anymore.
this is the the link for the 64-bits deb
[http://stinker.serveftp.net:8000/gtkgnutella/gtk-gnutella_0.96.9u%7Esvn17435%7Elucid_amd64.deb](http://stinker.serveftp.net:8000/gtkgnutella/gtk-gnutella_0.96.9u%7Esvn17435%7Elucid_amd64.deb)

---

### Post by JoelOl75 on 2010-08-03
Sometimes the server list gets outdated and it cannot find other ultra nodes to connect to.  There's a script on my website that will download a more current list of servers.  Just d/l it, chmod a+x (make executable) start up gtk-gnutella and then run it.

It's called kickstart.sh and listed right above the versions list:

[http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html](http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html)

---

### Post by Yellow Pasque on 2010-08-03
Thank you for maintaining that site, Joel. :)

---

### Post by amitst on 2010-09-04
I am getting issue while loading this site.
[http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html](http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html)

Any pointers?

---

### Post by Yellow Pasque on 2010-09-04
Works for me.. but here's the links for Lucid. You can use wget.
```
cd ~
wget http://stinker.serveftp.net:8000/gtkgnutella/gtk-gnutella_0.96.9u%7Esvn17435%7Elucid_i386.deb
wget http://stinker.serveftp.net:8000/gtkgnutella/gtk-gnutella_0.96.9u%7Esvn17435%7Elucid_amd64.deb
```

---

### Post by amitst on 2010-09-05
Looks like some issue for me. I am getting timeout errors as below,

```

amit@amit-desktop:~/installable$ wget http://stinker.serveftp.net:8000/gtkgnutella/gtk-gnutella_0.96.9u%7Esvn17435%7Elucid_i386.deb
--2010-09-05 11:52:19--  http://stinker.serveftp.net:8000/gtkgnutella/gtk-gnutella_0.96.9u%7Esvn17435%7Elucid_i386.deb
Resolving stinker.serveftp.net... 108.8.118.43
Connecting to stinker.serveftp.net|108.8.118.43|:8000... failed: Connection timed out.
Retrying.

--2010-09-05 11:55:29--  (try: 2)  http://stinker.serveftp.net:8000/gtkgnutella/gtk-gnutella_0.96.9u%7Esvn17435%7Elucid_i386.deb
Connecting to stinker.serveftp.net|108.8.118.43|:8000... failed: Connection timed out.
Retrying.

--2010-09-05 11:58:40--  (try: 3)  http://stinker.serveftp.net:8000/gtkgnutella/gtk-gnutella_0.96.9u%7Esvn17435%7Elucid_i386.deb
Connecting to stinker.serveftp.net|108.8.118.43|:8000... failed: Connection timed out.
Retrying.

```

I have downloaded the source tarball for now and will follow the README.debian instructions to install it. Will keep you posted. Meanwhile let me know in case you can find out form the wget log why I can't reach the host with ready made deb file.

Thanks,
Amit

---

### Post by amitst on 2010-09-05
I could build the source code and installed the latest version. It is connecting fine now. Thanks.

---

### Post by JoelOl75 on 2010-09-09
Sorry, my site was temporarily down over the holiday weekend.

Should be working now, also starting to update the svn's to version 17438.

---

### Post by Yellow Pasque on 2010-10-21
> **JoelOl75 said:**
> Sorry, my site was temporarily down over the holiday weekend.

Should be working now, also starting to update the svn's to version 17438.
Hi Joel, just pinging you to see if you're still updating your site. There have been some nice updates to gtk-gnutella and svn17535 connects really fast for me. If you don't have time right now, I will work on getting the latest svn snapshots into PPA form. Thanks.

---

### Post by Smiley Coyote on 2010-10-28
> **JoelOl75 said:**
> Sometimes the server list gets outdated and it cannot find other ultra nodes to connect to.  There's a script on my website that will download a more current list of servers.  Just d/l it, chmod a+x (make executable) start up gtk-gnutella and then run it.

It's called kickstart.sh and listed right above the versions list:

[http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html](http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html)

I sense, from this, that I am oh so close to getting this app to finally work.  One question: what does it mean to "chmod a+x" something?  I sense this goes in the command line terminal followed by what, the location of the file?

---

