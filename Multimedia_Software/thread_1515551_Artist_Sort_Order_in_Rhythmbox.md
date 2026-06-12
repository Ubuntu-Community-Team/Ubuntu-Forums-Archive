---
title: "Artist Sort Order in Rhythmbox"
date: 2010-06-22
forum: Multimedia Software
---

### Post by @B6Mwu8fN9M on 2010-06-22
Anyone have any idea how the "Artist Sort Order" and "Album Sort Order" works in Rhythmbox (Right-click>Properties>Sorting)?

---

### Post by Freelance Physicist on 2010-06-29
These options allow you to specify an alternate name for artists and albums for the purpose of ordering them alphabetically in the browser and song list.

For example, I have an mp3 with the song "Scene of the Crime" by The Amazing Royal Crowns.  Originally, this would be filed near the other artists starting with T (e.g. Temple of the Dog) because the artist name starts with "The."  If I write "Amazing Royal Crowns, The" in the Artist Sort Order, it will appear next to the other artists whose names start with A (e.g. Alice in Chains).

---

### Post by @B6Mwu8fN9M on 2010-06-29
Thanks! I wish this was in the Help somewhere; it's so useful.

---

### Post by Ni85 on 2010-08-26
is there any way to set this automatically?
so that i don't have to enter each artist that starts with "the"?

thanks...

---

### Post by Freelance Physicist on 2010-08-26
No.  I've read the developer discussions regarding this and the consensus was that there would be no way to account for multiple languages.  You can select multiple files within rythmbox using shift+click to do all songs of an artist at once.

The only other thing I can think of is closing rhythmbox and running a command line filter on ~/.local/share/rhythmbox/rhythmdb.xml, something along the lines of:
```
cd ~/.local/share/rhythmbox
cp rhythmdb.xml old-rhythmdb.xml
sed 's/<artist>The \([^<]\+\)<\/artist>/\0\n    <mb-artistsortname>\1, The<\/mb-artistsortname>/' old-rhythmdb.xml > new-rhythmdb.xml
mv new-rhythmdb.xml rhythmdb.xml

```

Then restart rythmbox to see if anything has changed.

If you want to get back to your database before any changes were made, just do:
```
cd ~/.local/share/rhythmbox/
cp old-rhythmdb.xml rhythmdb.xml

```

This command uses sed to look for any songs with an <artist> tag starting with "The" and creates a new tag on the next line <mb-artistsortname> with the "The" moved to the end of the name.  Of course, this assumes your files have English tags and "The" is capitalized in all your tags.

If you want to try this, definitely make a copy of ~/.local/share/rhythmbox/rhythmdb.xml in another directory first.  I've had to restore my rhythmdb.xml a couple of times from backups because I forgot which file was which and deleted the original.

---

### Post by elboulangero on 2011-06-26
There is a plugin for that now,

[http://code.google.com/p/artistprefix/](http://code.google.com/p/artistprefix/)

hope this helps

---

