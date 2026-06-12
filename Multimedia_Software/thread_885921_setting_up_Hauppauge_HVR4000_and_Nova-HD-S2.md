---
title: "setting up Hauppauge HVR4000 and Nova-HD-S2"
date: 2008-08-10
forum: Multimedia Software
---

### Post by frafu on 2008-08-10
In  reply to the following thread that has been archived: 
[http://ubuntuforums.org/showthread.php?t=633182&highlight=hvr4000](http://ubuntuforums.org/showthread.php?t=633182&highlight=hvr4000)

A few days ago, I succeeded to make my Nova-HD-S2 run on the development version of Ubuntu 8.10.

- I checked out the current version of v4l-dvb; I think that it was revision fcf263987edf

- I patched it with the "scratcpad-8628.diff" file from [http://dev.kewl.org/hauppauge/](http://dev.kewl.org/hauppauge/)

The rest of the procedure was as described in the thread above: I compiled and installed. 

I also had to install the firmware of the card. (The procedure for the installation of the firmware is also described in the thread listed above.) 

Hoping that this helps. 

Francesco

---

### Post by frafu on 2008-09-18
Hello, 

I am now running my Nova-HD-S2 card with the current 2.6.27-3-generic kernel of the Ubuntu 8.10 development version. Here are some short instructions about how to make it work: 

- Place the firmware of the card into
/lib/firmware/2.6.27... 

- Get the drivers: 
hg clone -r 94bd2599004f [http://linuxtv.org/hg/~stoth/s2](http://linuxtv.org/hg/~stoth/s2)
or simpler
hg clone -r 8884 [http://linuxtv.org/hg/~stoth/s2](http://linuxtv.org/hg/~stoth/s2)

- Compile, install and restart the computer and your card should work; at least it works here with kaffeine. 


Remarks: 

1. The drivers currently only work with the Nova-HD-S2; the support for the hvr4000 is not fully implemented yet. 

2. The aim of these drivers is to also support dvb-s2; but there is much to do for this: apart from creating the S2API drivers, the dvb applications will have to be adapted so that they use the new dvb-s2 features. 


Finally, you might be interested to know that a forum has been created about v4l-dvb with a section about Hauppauge cards. Here it is: 
[http://bbs.kewl.org/](http://bbs.kewl.org/)


Hoping to have been helpful. 

Francesco

---

### Post by frafu on 2008-09-23
Hello, 

The drivers should now also work for the 
HVR4000
HVR3000
HVR1300
NOVAS+
PVR350

For it to work, you have to either use the patches for the [http://linuxtv.org/hg/~stoth/s2](http://linuxtv.org/hg/~stoth/s2) repository or the [http://linuxtv.org/hg/~stoth/s2-mfe](http://linuxtv.org/hg/~stoth/s2-mfe) repository. 

You can find more information at [http://dev.kewl.org/hauppauge/](http://dev.kewl.org/hauppauge/) where you can also find the patches. 

Cheers 

Francesco

---

### Post by frafu on 2008-10-01
Hello, 

The drivers for single frontend usage of the HVR3000 and HVR4000 have been merged to the v4l-dvb drivers. In other words, you can get them by: 
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
(After compilation and installation, you still have to put the firmware into /lib/firmware.)

For multi-frontend support for the HVR3000 and HVR4000 cards you have to use the following repository: 
hg clone [http://linuxtv.org/hg/~stoth/s2-mfe](http://linuxtv.org/hg/~stoth/s2-mfe)

You might find more infrastructure at: 
[http://dev.kewl.org/v4l-dvb/](http://dev.kewl.org/v4l-dvb/)

Cheers 

Francesco

---

### Post by frafu on 2008-12-07
Hello, 

I upgraded my test installation to jaunty (Ubuntu 9.04) running kernel 2.6.28-2 and my Nova-HD-S2 worked right away. So it seems to be supported out of the box. 

But for the moment, kaffeine is broken and totem does not run smoothly when it shows channels from the Nova-HD-S2.

Cheers 

Francesco

---

### Post by mtron on 2008-12-10
get a kaffeine svn checkout. [SVN Changelog]("http://websvn.kde.org/branches/extragear/kde3/multimedia/kaffeine/ChangeLog?revision=892681&view=markup") indicates interesting stuff:
> * DVB: added live ringbuffer size option (in misc page)
* DVB: added tuner priority option.
...
* DVB: **add DVB-S2 support**.
* DVB: **port to S2API**.

```

svn co svn://anonsvn.kde.org/home/kde/branches/extragear/kde3/multimedia
```

(you need the modules admin & kaffeine)

---

### Post by frafu on 2008-12-10
@mtron

Unfortunately, I am not able to compile it on jaunty. I get the following error:

```

/usr/lib/libkhtml.so: undefined reference to `KJS::ObjectImp::construct(KJS::ExecState*, KJS::List const&)'
/usr/lib/libkhtml.so: undefined reference to `KJS::Null::Null()'
/usr/lib/libkhtml.so: undefined reference to `KJS::ObjectImp::call(KJS::ExecState*, KJS::Object&, KJS::List const&)'
/usr/lib/libkhtml.so: undefined reference to `KJS::Context::sourceId() const'
/usr/lib/libkhtml.so: undefined reference to `KJS::Value::~Value()'
/usr/lib/libkhtml.so: undefined reference to `KJS::Undefined::Undefined()'
/usr/lib/libkhtml.so: undefined reference to `KJS::ObjectImp::ObjectImp()'
/usr/lib/libkhtml.so: undefined reference to `KJS::Number::Number(int)'
/usr/lib/libkhtml.so: undefined reference to `KJS::ObjectImp::deleteAllProperties(KJS::ExecState*)'
/usr/lib/libkhtml.so: undefined reference to `KJS::ScopeChain::push(KJS::ObjectImp*)'
collect2: ld returned 1 exit status
make[4]: *** [kaffeine] Error 1

```

Have you been able to compile it?

Cheers

Francesco

---

### Post by frafu on 2008-12-11
Hello,

The jaunty update of today with a fresh checkout of kaffeine solved the problem. Moreover, a new channel search after the installation also found the dvb-s2 channels.

Francesco

---

### Post by Propantriol on 2009-01-01
I just compiled kaffeine from svn without problems.
Furthermore I compiled and installed the latest driver sources from [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) but a channel search has not found any dvb-s2 channels.

Any idea what's missing?

Thanks in advance

---

### Post by frafu on 2009-01-01
Hi, and happy new year. 

Did you activate the option in kaffeine to also use dvb-s2? If I remember correctly the option is located in the configuration for the satellites to scan. 

Cheers

---

### Post by Propantriol on 2009-01-01
Hem :-p

Thank you very much, works like a charm!

PS: Happy New Year!

---

