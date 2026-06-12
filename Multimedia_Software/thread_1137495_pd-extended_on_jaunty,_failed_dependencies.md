---
title: "pd-extended on jaunty, failed dependencies"
date: 2009-04-25
forum: Multimedia Software
---

### Post by cmbryan on 2009-04-25
Hi everyone, am blown away by jaunty!!

One problem though:  When installing pd-extended I get:

===
pd-extended:
 Depends: libmagick++10  but it is not installable
 Depends: libmagick10  but it is not installable
===

I found this is because these packages now have different names.  Can we get the pd-extended package updated please??

Thanks!

---

### Post by capheen on 2009-04-26
I was having the same problem.
I found a deb for jaunty at [http://autobuild.puredata.info/auto-build/latest/](http://autobuild.puredata.info/auto-build/latest/)
works fine.

---

### Post by cmbryan on 2009-04-26
Sweet!

---

### Post by Endolith on 2009-05-25
I used the Jaunty rc2 .deb from [http://at.or.at/hans/pd/installers.html](http://at.or.at/hans/pd/installers.html)

It complained that I was missing tk8.4, but I installed it manually and it works.  Are they from the same people?  Is the rc3 from the autobuild site better?

---

### Post by mumumuu on 2009-05-28
I installed that same rc2 version for Jaunty, but I'm having problems with sound. 

OSS seems to work ok, with ALSA I get little crackles the whole time and the "DIO errors" box flashes red. But the real problem is jack, because I want to use pd connected to other programs using jack.

With jack it's the same as with ALSA, crackles and the DIO errors box flashes red. In the terminal it says "cannot lock down memory for RT thread (Cannot allocate memory)" and it goes wild with xruns.

---

### Post by Endolith on 2009-05-28
> **mumumuu said:**
> I installed that same rc2 version for Jaunty, but I'm having problems with sound. 

I haven't even tried to get this working. I have always had these problems when trying to use JACK.   Are you running the realtime kernel?

Is there a way to make Pd and other audio software work *with* PulseAudio instead of disabling it?  What's the command for disabling Pulse for a specific program again?

---

### Post by mumumuu on 2009-05-29
> **Endolith said:**
> I haven't even tried to get this working. I have always had these problems when trying to use JACK.   Are you running the realtime kernel?0
Yeah I'm running the realtime kernel. I use other programs with jack in realtime with very minor problems or no problems at all (Renoise, Audacity, Qsynth, JackRack and others)

I installed RC3 and I noticed something in the terminal while installing:
```
Setting up pd-extended (0.41.4~cvsrc3-1) ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...

Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'
```Could the "Unknown media type in type" stuff be causing any malfunction?

Oh and now jack actually gives an error instead of just getting around 10000 xruns in a minute:
```
JACK: jack returned status 33
error: JACK: unable to connect to JACK server
JACK: jack returned status 17
error: JACK: unable to connect to JACK server
JACK: jack returned status 17
```

---

### Post by vixmusic01 on 2009-11-13
Hi All,

I am having the exact same problem with Jaunty.

pd-extended:
Depends: libmagick++10 but it is not installable

I only know how to install programs with Synaptic. Is there a repository or can someone give me instructions to get the software so that synaptic will update it?

Thanks,

Victoria

---

