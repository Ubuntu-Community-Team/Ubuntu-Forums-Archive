---
title: "Seeking in windows stream"
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by v-gudmk on 2007-07-30
I have a problem where I cannot make Ubuntu (feisty) do something that works in windows.
A website I like to visit makes video wmv streams available for material which has been recorded previously.
On windows I can seek to any position in such a stream with very little delay.  On ubuntu (    mplayerplug-in-wmp.so  mplayerplug-in 3.31) I can only play from the beginning,  I cant skip anywhere and even if I pause for more than a few seconds I have to start again from the beginning.

The website also makes available multiple links into the same .wmv file using offsets specified in an asx playlist, for example:
<asx version="3.0">

  <moreinfo href="http://www.<website>/" />

  <title>Program name</title>

  <entry>

    <title>title of program</title>

    <copyright>Company name</copyright>

    <ref href="http://<url>/filename.2007-07-30.wmv" />

    <starttime value="00:28:24.0080" />

    <duration value="00:03:05.0960" />

  </entry>

</asx>

These starttime and duration entries are completely ignored by the mplayer plugin.

Is there any way to play these streams on Ubuntu, with the ability to skip back and forth to any location, and to use these playlists to locate certain sections of video within a longer program?

I have found ways to play the stream and copy to my own local .wmv file.  But often I'm not interested in copying the file down, it takes a long time and diskspace, when I'm only interested in a small section.

---

