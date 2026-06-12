---
title: "MusicBrainz in Rhythmbox: insists on a message + can disable or change it by freedb?"
date: 2011-03-29
forum: Multimedia Software
---

### Post by vezolmi on 2011-03-29
Hello:

I have an Audio CD with CD-Text. When it opens with Rhythmbox this warning (1) appears:
> 
Could not find this album on MusicBrainz.
You can improve the MusicBrainz database by adding this album.
I click on "Submit Album", then Firefox opens a page starting with [http://musicbrainz.org/bare/cdlookup.html?id=](http://musicbrainz.org/bare/cdlookup.html?id=) , with this message (2):
> 
CD not found
MusicBrainz doesn't currently have any CDs which have this TOC:
I click on "Submit this CD using the simple method.", then on "FreeDB  import". This way the CD-Text info fills the form. Then I click on  Submit. A page with this message (3) appears:
> 
CD Stub Added
Thank you for adding/checking the information for this CD. You can now request this CD via your client.But when I open the CD I have the warning (1) again. If, instead of  clicking on Hide I click again on "Submit Album", the story repeats,  just with little changes:
Message (2) is now like:
> 
CD not found
MusicBrainz only has a CD Stub for this CD.
This time there is no need to click on "FreeDB import".
The message (3) appears now as:
> 
CD Stub Updated
Thank you for adding/checking the information for this CD. You can now request this CD via your client.
With very popular albums I have no problem: no warning (1).

So I imagine that Rhythmbox or MusicBrainz needs a number of CD-Text  submits (perhaps in different dates and from IPs of different  countries/regions) to the MusicBrainz DB to consider that the album is  verified. Anybody knows about this?

Can I stop the warning (1) from appearing?

Can I disable MusicBrainz in Rhythmbox? How?

Can I change MusicBrainz by freedb or another DB in Rhythmbox? How?

Thank you

---

### Post by vezolmi on 2011-03-29
As I've seen that MusicBrainz also searches for cover art:
/usr/lib/rhythmbox/plugins/artdisplay/MusicBrainzCoverArtSearch.py

I've disabled the cover art plugin.

But the warning (1) continues to appear.

By the way, when I enable the cover art plugin it doesn't get the cover images, even for very sold albums: when you click on the play button and the music begins to sound at the left-bottom a searching icon appears and if you pass the mouse cursor over it says "Searching... drop artwork here". But no cover image appears. How can I solve this?

By they way. I cannot find the messages of the program, that are in:
[http://git.gnome.org/browse/rhythmbox/tree/po/es.po](http://git.gnome.org/browse/rhythmbox/tree/po/es.po)
in my hard drive. I've tried, among others:
/usr/share/gnome/help-langpack/rhythmbox/es/rhythmbox.xml
In which file are they?

---

### Post by murdos on 2011-04-01
FYI what you have submitted is a "CDStub" : [http://wiki.musicbrainz.org/CDStub](http://wiki.musicbrainz.org/CDStub) i.e. a non moderated contribution that is separate from main MusicBrainz data and doesn't benefit from other features such as cover art.

However on the second lookup, you shoud not have the warning and information should be retrieved. This might be a bug in Rhythmbox, in the way it sends its request to MusicBrainz.

---

### Post by vezolmi on 2011-04-03
Thanks.

I've submitted the CD info to MusicBrainz several times but the warning continues to appear ... :-(

---

