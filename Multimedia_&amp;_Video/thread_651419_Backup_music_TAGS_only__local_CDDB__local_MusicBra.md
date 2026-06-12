---
title: "Backup music TAGS only / local CDDB / local MusicBrainz data - how to?"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by kko1 on 2007-12-27
Hello.

Simple question, probably with a simple answer, and hopefully with some fellow forumer knowing the said answer. ;)

I have my CDs as FLAC files, one album per directory. Should I lose the files, re-extracting the music isn't the time-consuming part, as the machine does all the work. Ensuring the correctness of the tags is the part that takes time. I *don't* want to backup the files on DVDs. It seems pointless as I already have the music on the original CDs. So, what I would like to do, is *backup the TAGS only, which I could re-apply on a **per-directory** basis after re-extracting the files.*

Sure, a solution that *automatically* does this for an entire collection (directory tree) would be ideal.

***

My solutions:

1) **A single program** to do this? I don't know of one, and doubt whether one exists. *Please prove me wrong! ;)*

2) Using the **CDDB data on public servers**? Nope, can't do that, they don't contain my own local edits. And if they did, they'd always have a number of entries to choose from. *Too cumbersome, forget that.*

3) **Using a local CDDB database**? Sounds good. *But how do I do it?* **EDIT:** A locally running **MusicBrainz** database is another option. See the fourth post for more.


***

I can use EasyTag (or anything else that can fetch data *per album = per directory*) to tag the files if needed. It can do FLAC nicely. Apparently it can even do m4a (MP4/AAC), if I want to use my FLACs as a source for Apple-compatible files. (Actually there probably already is something that could treat each directory as an album, and automatically fetch and apply the CDDB data for the entire collection, or if there isn't yet, something can be scripted up to do it.)

*But how do I store the CDDB data locally, from my **existing collection**, and ask the tagger to use the **local** data?*

Pointers would be appreciated.

Yours, kko1

---

### Post by pelago on 2008-01-07
I second this request, as I too have a very similar use case: obtaining the raw files isn't hard, but recreating all my carefully-constructed metadata is.

I'm hoping that there is a command-line utility (because that would be more easily scriptable) to dump all the tags to a text file in a certain format, with recursive folder-traversing options, and a similar utility to restore the tags.

One problem might be in ensuring the filenames are the same before and afterwards, as I imagine most utilities would rely on the filenames. If the filenames differ, then some sort of hash would have to be used, I guess, but even that might have problems - if the music rips just slightly differently then the hash fails and the utility wouldn't be able to match the tags.

Hmm, trickier than I thought.

---

### Post by kko1 on 2008-01-07
Thanks for the interest.

1. About a script-based approach:
- I considered this. It's a possibility. I have my music (currently) in FLAC, so the command-line tool *metaflac* can dump the tags to a file and re-tag music with these tags, easily on a **per-file basis**.
- It is also trivial to extract a CD to numbered tracks in a directory.
- So, it shouldn't be too hard to script something to handle **one directory at a time***, based on numbered files on one hand and matchingly numbered tag-backups on the other.
- So far, I haven't bothered trying to implement this, for two main reasons. One, this doesn't seem as practical as the server-based option. And two, this only applies to FLAC and I'd prefer a universal solution. An other reason is time.

EDIT: I have no doubt that other programs can dump the tags from other file formats besides FLAC, but I don't know how wide a selection any *one* program can cover. *If you know of a tagger that can dump the tags from a variety of different file formats, preferably including both FLAC and M4A (a tall order), as well as re-tag files using these backups, **and** can also be command-line operated, i.e. scripted, please let us know.*

*) A note about filenames:
- I'd take the opposite approach from what you suggested. That is, first re-tag the files, then rename based on the tags. After all, we're not trusting *all of* the new (filename-)data we get (when re-extracting CDs) based on network-CDDB queries, so *the best filename data is (should be) available from our own backup tags.*
- This proposition gives me a pointer for the implementation. Namely, the tags can (and probably should) be backed up with a directory structure that exactly **mirrors** the directory structure of our music archive.
- This way, when re-extracting (ripping) the CDs, all we have to do is **ensure that the directory names and the directory structure match**, and that we have the right amount of numbered files in the directory.
- **The rest** - that is, re-tagging and renaming the files - **can be left to automation**, that is the script / program / whatever.


3. About the local CDDB solution:
- I think this should be workable, but haven't had time to look at it. Just now I tried downloading the server software from freedb (they say in their FAQ that there's a "very helpful HOWTO" in the archive), but their ftp server isn't responding. I'll have to try again later. Here's the link:
[http://www.freedb.org/en/download__server_software.4.html](http://www.freedb.org/en/download__server_software.4.html)
- A major benefit of the server-based approach would be that, once implemented, it would be *perfectly transparent* for the user. When re-extracting CDs, the right data would automatically be fetched. (As long as whatever you're extracting the CDs with is pointed to use the local server.)


In the hopes that this might aid in our quest.

kko1

---

### Post by kko1 on 2008-01-10
OK.

It seems the lack of a download server for the freedb is a new (semi-?)permanent state of affairs, see [http://www.freedb.org/en/forum/read.php?1,514](http://www.freedb.org/en/forum/read.php?1,514) . I've tried downloading the server software a number of times during this week, without success. If this condition persists, they are effectively denying the common public access to their (GPL'd) server software.


I will be looking for a **MusicBrainz**-based server solution instead, it shows more promise at the moment. (It doesn't seem all too trivial, and my motivation to work on this is low, so don't hold your breath.)

**Some links to the MusicBrainz-server setup:**
[http://musicbrainz.org/doc/Server](http://musicbrainz.org/doc/Server)
[http://musicbrainz.org/doc/ServerDownload](http://musicbrainz.org/doc/ServerDownload)
[http://musicbrainz.org/doc/MusicBrainzServerSetup](http://musicbrainz.org/doc/MusicBrainzServerSetup)
[http://bugs.musicbrainz.org/browser/mb_server/trunk/INSTALL](http://bugs.musicbrainz.org/browser/mb_server/trunk/INSTALL)
[http://musicbrainz.org/doc/DebianServerSetup](http://musicbrainz.org/doc/DebianServerSetup)
[http://musicbrainz.org/doc/DebianServerPackage](http://musicbrainz.org/doc/DebianServerPackage) (Sadly, the package doesn't exist yet, but the page is a (copy of a) wikipage documenting the process of hopefully creating the package.)

**Probably the most promising way to get a running server, in the short term, is this:**
[http://musicbrainz.org/doc/VirtualMusicBrainzServer](http://musicbrainz.org/doc/VirtualMusicBrainzServer)


HTH someone.

kko1

Besides, on a further note about MusicBrainz, how can you not like a project that takes their tagger names from Star Trek? *"Picard will soon get an automatic tagging algorithm called "Data" which should do large parts of the tagging process for you."*  :)

---

