---
title: "Rhythmbox podcast property"
date: 2011-02-21
forum: Multimedia Software
---

### Post by db579 on 2011-02-21
How do you tell rhythmbox that podcasts already downloaded outside the program are in fact podcasts? Mine are mostly just mp3 files and it doesn't seem possible to drag and drop them into the podcast section but I also can't find anything in the song properties.

Anyone know? Thanks

---

### Post by db579 on 2011-02-24
bump?

---

### Post by db579 on 2011-02-28
There must be a way of doing this but I can't find anything? Basically I want the ability to take podcasts where I've deleted the library episode but kept the file and import the file back into rhythmbox and have it be picked up as a podcast.

---

### Post by shunt31 on 2012-05-13
For anyone that's still wondering about this, you have two options - I'm using Rathole Radio as an example:

Assuming you already have the feed in Rhythmbox, you can copy the podcast you downloaded into the same folder as the other podcasts (make sure it has the same filename as the others) - with the latest RR, it would be RR077_29_04_12.ogg in [your podcast directory]/RatholeRadio.org (Ogg Version). Then, go into the Podcasts pane, and click on the episode you have copied, and after a few seconds, under "Status", it should jump straight to "Downloaded".

If you don't have the feed already, you have to edit ~/.local/share/rhythmdb.xml by hand. Copy this example and change the fields as needed. <mountpoint> is where the file is  on the Internet after it's been downloaded, and <location> is is  where the file is on the Internet before downloading, and the location  of the file on the hard drive afterwards.

```

<entry type="podcast-post">
    <title>RatholeRadio 77 &#x2013; 29th Apr 2012</title>
    <genre>Podcast</genre>
    <artist>Dan Lynch</artist>
    <album>RatholeRadio.org (Ogg Version)</album>
    <duration>4099</duration>
    <file-size>66588290</file-size>
    <location>file:///home/nathan/Music/RatholeRadio.org%20(Ogg%20Version/RR077_29_04_12.ogg</location>
    <mountpoint>http://feedproxy.google.com/~r/RatholeRadio-ogg/~5/uXknSyncmlw/RR077_29_04_12.ogg</mountpoint>
    <first-seen>1336932264</first-seen>
    <last-seen>1336932264</last-seen>
    <bitrate>128</bitrate>
    <date>0</date>
    <media-type>audio/x-vorbis</media-type>
    <status>100</status>
    <subtitle>http://feeds2.feedburner.com/RatholeRadio-ogg</subtitle>
    <summary></summary>
    <lang></lang>
    <copyright></copyright>
    <image></image>
    <post-time>1335888673</post-time>
  </entry>

```If you're looking for something barebones, this should do:

```
<entry type="podcast-post">
    <title>[name of podcast]</title>
    <genre>[genre]</genre>
    <artist>[artist]</artist>
    <album>[album]</album>
    <location>file://[location on hard drive]</location>
    <mountpoint>[location on Internet]</mountpoint>
</entry>
```I don't think it really matters where you insert it into the xml file, but it would make sense to put near any another podcasts.

---

