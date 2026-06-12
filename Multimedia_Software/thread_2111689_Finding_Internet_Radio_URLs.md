---
title: "Finding Internet Radio URLs"
date: 2013-02-02
forum: Multimedia Software
---

### Post by jcllings on 2013-02-02
So I was wondering, what are some good techniques for finding Internet Radio URLs? There really ought to be a FireFox plugin for revealing all the IR URLs hidden within a page or one that custom builds a Google search that pulls the information which is surely buried in Google's archives somewhere. 

What else can a person do? Is there something I can grep for in a page using wget? Frankly, I don't even know how to identify such a URL as yet. I need to build a compendium of possible forms such a URL might take.  That probably means looking at what Banshee and RhythmBox's data looks like but a clue in that regards wouldn't hurt. I'll check for ".config" directories after I am done writing this.

Thoughts? Clues? Ideas? I've found that my music collection is stagnating because I don't listen to anything but the mp3's I already own. 


Jim C.

---

### Post by jcllings on 2013-02-02
OK, so what I am seeing in rhythmbox's data is that an Internet Radio station's URL takes the form of a standard URL with a sound file format file extension. For example:

<entry type="iradio">
    <title>HBR1.com - Tronic Lounge</title>
    <genre>House</genre>
    <artist></artist>
    <album></album>
    <location>http://ubuntu.hbr1.com:19800/tronic.ogg</location>
    <date>0</date>
    <media-type>application/octet-stream</media-type>
  </entry>

Hmmm... that looks a little strange though. Does Ubuntu actually host IR stations or is it a mirror of some sort? 


Jim C.

---

### Post by andrew.46 on 2013-02-02
In my perfect world radio stations that broadcast over the Internet would feature not only whatever fancy interface they wished to showcase but also a *direct link* to their stream.

One technique which is often a good start is to examine the source of the launching page, Ctrl+u will normally do this...

---

