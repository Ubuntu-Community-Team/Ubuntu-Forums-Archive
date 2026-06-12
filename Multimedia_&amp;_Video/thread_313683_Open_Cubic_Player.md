---
title: "Open Cubic Player"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by HeavyAl on 2006-12-06
I just installed Open Cubic Player. I used to run it in DOS many years back. The port to Linux looks cool but there appears to be a dependency issue.

On running it from the cl I get the following:

```

linking default objects...
libadplug-1.5.1.so.0: cannot open shared object file: No such file or directory could not link default objects!
Generic, unspecified error.

```

On doing a 'locate libadplug' I find that I have libadplug-2.0 installed. 

So the question is threefold:

A. Can I force the app to link to libadplug 2 somehow?
B. Do I need to try compiling OCP from scratch and link to the new lib?
C. Do I need to somehow revert my libadplug lib to the 1.5.1 version?

Thanks for any help!

---

### Post by FactTech on 2007-02-17
I've run into the exact same problem, and I would love to get it working.

Anyone have any clues for this? I'm too new to Linux to figure it out, it seems.

---

### Post by FactTech on 2007-02-17
I went over to the #ocp irc channel and asked about this. Apparently, the ubuntu package repository is out of date for this program, but it works if you use the debian repository and dpkg to install it. It's apparently an ongoing annoyance to them to get reports of this "problem" that they consider out of their hands.

I didn't know how to do what was suggested, so I just downloaded the source for the latest version (v0.1.11) and compiled it myself. It takes a lot of optional packages to do this, but complete lists can be found at:

[http://packages.debian.org/testing/source/ocp](http://packages.debian.org/testing/source/ocp)

and

[http://packages.debian.org/testing/sound/opencubicplayer](http://packages.debian.org/testing/sound/opencubicplayer)

The source code can be downloaded from the first link.

Once the tar.gz file was downloaded, I did the following:

1) uncompressed the archive using Xarchiver, being sure to preserve full paths during extraction
2) went to the ocp-0.1.11 directory that was created by the extraction
3) "bash configure" to run the configuration check -- note that this did not catch all dependencies as I've seen in other programs
4) "make" to build the binaries
5) "sudo make install" to get it installed in the /bin directories

It's working now! You have to type "ocp-0.1.11" to get it to execute, and I'm not sure if the documentation installed OK, but it plays music.

This is probably not the best way to go about installing it, but it's the best I could do as a newbie.

---

