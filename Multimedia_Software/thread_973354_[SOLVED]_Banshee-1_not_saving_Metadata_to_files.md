---
title: "[SOLVED] Banshee-1 not saving Metadata to files"
date: 2008-11-06
forum: Multimedia Software
---

### Post by ChildOfMana on 2008-11-06
I'm having problems with Banshee 1.2.1 on Intrepid.

I've re-imported all my music to my Banshee library after installing Intrepid (I opted for a fresh install over an upgrade) and nearly all the Artist/Album/Track metadata is missing.

I went to Edit > Preferences and checked the 'Write metadata to files' box before editing the Artist/Album/Track info on a few files. As a test I then removed these files from the library and re-imported them again. Unfortunately the metadata doesn't appear to have been written to the files. This is potentially a bit of a nightmare as I have literally *thousands* of songs. If I'm going to go through them all and edit the metadata then I'm only prepared to do it *once* and once only - not every time I switch distros.

I found these bug reports:

[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/157722](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/157722)
[http://bugzilla.gnome.org/show_bug.cgi?id=476366](http://bugzilla.gnome.org/show_bug.cgi?id=476366)

but, apparently, they have been resolved and the bug has been fixed.

So, am I missing something here?

The problem affects both .mp3 and .m4a (a throwback from the bad old iTunes days) files.

Any ideas?

Thanks.

---

### Post by ChildOfMana on 2008-11-06
Fixed!

Apologies but it was just me being daft again. It was a permissions problem - not a Banshee problem.

For some reason all my music files are owned by root. Once I changed the permissions on the files and tested it out again Banshee successfully wrote the changes to the files.

Which now leaves me with another problem... how to change the ownership of all my music files from root to me en mass. 

I'm sure there's plenty of threads regarding that problem already though so I'll search round.

---

