---
title: "Need help with mplayer plugin"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by Bossieman on 2007-03-11
I am trying to help a friend install and configure mplayer-plugin on a fresh Edgy install. This is how far we get.


```
sudo apt-get install mplayer cvs build-essential firefox-dev libgtk2.0-dev
```

then

```
cvs -d:pserver:anonymous@mplayerplug-in.cvs.sourceforge.net:/cvsroot/mplayerplug-in login
```

When asked for a password just hit Enter

Countiniue with

```
cvs -z3 -d:pserver:anonymous@mplayerplug-in.cvs.sourceforge.net:/cvsroot/mplayerplug-in co mplayerplug-in
```

Now you have a folder named mplayerplug-in. Enter the folder

```
cd mplayerplug-in
```

Then

```
./configure
```

After that is done, do

```
make
```

This error is reported from make:

 Source/plugin.h:173: error: ‘Widget’ does not name a type  /usr/include/firefox/nsIServiceManager.h:40: warning: ‘class nsIServiceManager’ has virtual functions but non-virtual destructor  /usr/include/firefox/nsIMemory.h:58: warning: ‘class nsIMemory’ has virtual functions but non-virtual destructor  Source/plugin.cpp: In function ‘NPError NS_PluginInitialize()’:  Source/plugin.cpp:101: warning: dereferencing type-punned pointer will break strict-aliasing rules  Source/plugin.cpp: In constructor ‘nsPluginInstance::nsPluginInstance(NPP_t*)’:  Source/plugin.cpp:207: error: ‘widget’ was not declared in this scope  make: *** [plugin.o] Fel 1  

Can anyone help me out here? 
When I do this it works perfect but I have not a clean install, I have alot of stuff installed. So what is missing here to make it work on a clean install?

---

### Post by qamelian on 2007-03-11
Is there some reason you're not installing the plugin from the repos? The Mplayer plugin in the Ubuntu repositories works just fine. No need to compile it from source.

---

### Post by Bossieman on 2007-03-11
> **qamelian said:**
> Is there some reason you're not installing the plugin from the repos? The Mplayer plugin in the Ubuntu repositories works just fine. No need to compile it from source.

Well I like to do things from scratch and  I like to learn new stuff.

---

### Post by SishGupta on 2007-03-11
I do not know the answer to your problem, but try installing libnpsr-dev

---

### Post by Bossieman on 2007-03-12
> **SishGupta said:**
> I do not know the answer to your problem, but try installing libnpsr-dev

what is libnpsr-dev and how do I install it?

---

### Post by SishGupta on 2007-03-12
You can use synaptic to answer both of your questions.

Open up synaptic, search by name for libnspr

read the description for libnspr

install libnspr if you choose.

---

