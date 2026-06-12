---
title: "Got tired of rhythmbox issues after upgrade -&gt; build from git"
date: 2010-05-12
forum: Multimedia Software
---

### Post by maedox on 2010-05-12
Basically I got tired of trying to fix some annoying bugs, incompatilities (or whatever you'd call it) with Rhythmbox after upgrading from Karmic to Lucid.

I would get errors on startup like these:
> rhythmbox: error while loading shared libraries: libtotem-plparser.so.12: cannot open shared object file: No such file or directory
> rhythmbox: symbol lookup error: rhythmbox: undefined symbol: GObject API

I decided to build if from git, because it looked like these bugs had been squashed recently (after 0.12.8 in lucid was built).

You will need to install some packages, but I never wrote down which ones I needed, so you're on your own, but I'll help if needed. When running ./autogen.sh you will be given fairly explanatory errors when packages/libs etc. are missing. So just open Synaptic and search for the package missing and install it (mostly -dev packages).


**Check out a git copy**
```
$ cd
mkdir git.gnome.org && cd git.gnome.org
sudo apt-get install git-core
git clone git://git.gnome.org/rhythmbox
```

**Prepare, build, install**
```
$ cd rhythmbox
./autogen.sh
make
sudo make install
sudo ldconfig
```

**Install plugins**
```
$ cd plugins
make
sudo make install
cd ../remote
make
sudo make install
```

**Done**
Start it normally with the installed launcher, or make your own and use command(s): 
```
rhythmbox 
or 
/usr/local/bin/rhythmbox
```


**rhythmbox-client**
Rhythmbox comes with a rhythmbox-client which we just built from git (from the remote directory). With this client you can control rhythmbox with simple shell commands. I use it for setting the rating of played tracks. When I hear a track I like/hate I click a launcher to set the desired rating.

To make such launchers, add one to a panel or your desktop and use this as command:
```
rhythmbox-client --set-rating #
```
# must be the number of stars you want to set; 0-5, 0=remove stars.

rhythmbox-client can do all sorts of stuff, so take a look at the man page for more info.
```
man rhythmbox-client
```



Post any feedback, ideas, issues, questions and so on here, and I will try my best to improve the instructions and help those in need.

---

