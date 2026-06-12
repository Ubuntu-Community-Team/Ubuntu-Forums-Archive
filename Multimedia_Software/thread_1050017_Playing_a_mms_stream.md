---
title: "Playing a mms stream"
date: 2009-01-25
forum: Multimedia Software
---

### Post by ge0rge04 on 2009-01-25
Hi.
I've checked many forums and installed hundreds of plugins, still i'm not a ble to play this stream:

mms://92.48.193.60/infinitycup-cod4-19-01-2009-4-ag-vs-exabyte.wmv

Totem,VLC,Mplayer would freeze, and xine would report a plug-in issue (i installed every xine plugin from the package manager)

I requested support from the organisation which is offering these streams and i got replied that i can't use any player besides Windows Media Player to handle their streams.

I can't install Windows Media Player under xine because it's not able to validate weather windows is genuine or not.

Any suggestion guys?
Is someone able to play that stream ?

P.S.: using ubuntu 8.10 x64

---

### Post by ge0rge04 on 2009-01-25
bump

---

### Post by kostkon on 2009-01-26
Try installing the windows codecs package that is offered by the [*Medibuntu* repository]("http://medibuntu.org/"). 

Add the repository to your software sources list (instructions are [here]("http://help.ubuntu.com/community/Medibuntu")) and then install the *w64codecs* package using *Synaptic*.

Then try again to play the stream using *Totem* or *Mplayer*.

It would be also good to install every available codec package that you can find in *Add/Remove* (*Applications &#8594; Add/Remove*).

---

### Post by andrew.46 on 2009-01-27
Hi,

I run the latest svn MPlayer with a full codec pack and I am afraid that even this will not play this stream:(.

Andrew

---

