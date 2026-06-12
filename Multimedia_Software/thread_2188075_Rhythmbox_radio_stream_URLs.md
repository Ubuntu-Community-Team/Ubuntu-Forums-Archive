---
title: "Rhythmbox radio stream URLs"
date: 2013-11-15
forum: Multimedia Software
---

### Post by virgoboy on 2013-11-15
Hi.  I feel like I have looked everywhere for an answer to this question, to no avail- where does Rhythmbox store (or does it store?) the URLs for radio streams?  I want to finally upgrade from 10.04 to the latest version of 12.04 and really don't want to lose my radio stations as there are so many of them.  So I want to back-up my RB settings, etc. including stream URLs.  Is this possible with Rhythmbox or is there some other way to do this, like via Terminal?  I'm pretty new to all of this so... be nice to me!  Thanks! :KS

---

### Post by tgalati4 on 2013-11-15
I'm on Jaunty right now and rhythmbox files can be found at .local/share/rhythmbox.

Yours may be slightly different.  There are playlist and database files that are text-readable XML files.  So you can either filter on radios or just try importing the XML files into the new rhythmbox and see what happens.  You can research the changes in rhythmbox between 10.04 and 12.04 or just be bold and try it and see if it works.


tgalati4@tpad-Gloria7 ~/.local/share/rhythmbox $ grep radio rhythmdb.xml
    <title>I Can't Unlove You (not radio)</title>
  <entry type="iradio">
    <location>http://network.absoluteradio.co.uk/core/audio/ogg/live.pls?service=vcbb</location>
  <entry type="iradio">
    <location>http://network.absoluteradio.co.uk/core/audio/ogg/live.pls?service=vc</location>
  <entry type="iradio">
  <entry type="iradio">
  <entry type="iradio">
  <entry type="iradio">
  <entry type="iradio">
  <entry type="iradio">
  <entry type="iradio">
  <entry type="iradio">
  <entry type="iradio">
    <title>http://www.wholewheatradio.org:8100/listen.pls</title>
    <location>http://www.wholewheatradio.org:8100/listen.pls</location>
  <entry type="iradio">
  <entry type="iradio">
  <entry type="iradio">
  <entry type="iradio">
  <entry type="iradio">
  <entry type="iradio">
    <location>http://network.absoluteradio.co.uk/core/audio/ogg/live.pls?service=vx</location>
  <entry type="iradio">
    <location>http://network.absoluteradio.co.uk/core/audio/ogg/live.pls?service=vxbb</location>
  <entry type="iradio">
    <location>http://network.absoluteradio.co.uk/core/audio/ogg/live.pls?service=vrbb</location>
  <entry type="iradio">
    <location>http://network.absoluteradio.co.uk/core/audio/ogg/live.pls?service=vr</location>
  <entry type="iradio">
  <entry type="iradio">

---

### Post by efflandt on 2013-11-18
That rhythmdb.xml file is in the same place on both 10.04 and 12.04 in ~/.local/share/rhythmbox

Besides the default list of internet radio stations, it would also have URLs of any you added and URIs of any music files.

---

