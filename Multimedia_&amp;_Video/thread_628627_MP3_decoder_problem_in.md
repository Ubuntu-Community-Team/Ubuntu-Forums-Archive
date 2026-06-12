---
title: "MP3 decoder problem in"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by rpirvu on 2007-12-01
Hello. Former Windows user, very new to Ubuntu 7.10 have a problem with mp3 playing. When I try to install the gstreamer codec, i get the following error message:

"Cannot install 'gstreamer0.10-plugins-ugly'

This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."

Anybody can help?

---

### Post by MrFSL on 2007-12-01
Try running it from the command line:

Open a terminal and type:
```
sudo apt-get update
sudo apt-get install -s gstreamer0.10-plugins-ugly
```

The first command updates your package lists. The second command says to simulate the install of the gstreamer package in question. The output should show the packages that are conflicting. Post the results for further help.

---

### Post by rpirvu on 2007-12-03
Thank you for your help. Here's the result:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.10-plugins-ugly: Depends: libid3tag0 (>= 0.15.1b) but it is not installable
                              Depends: libmad0 (>= 0.15.1b) but it is not installable
E: Broken packages

---

### Post by MrFSL on 2007-12-04
```
sudo apt-get update
sudo apt-get -f install
sudo apt-get install -s gstreamer0.10-plugins-ugly
```

---

### Post by rpirvu on 2007-12-04
I'm afraid I got the same result...

---

### Post by Meerkat Avenger on 2008-04-01
I have this same problem :(

I'm a new linux user, just installed Gutsy Gibbon.

---

