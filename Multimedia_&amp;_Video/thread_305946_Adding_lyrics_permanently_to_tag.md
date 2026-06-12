---
title: "Adding lyrics permanently to tag"
date: 2006-11-24
forum: Multimedia &amp; Video
---

### Post by rigol on 2006-11-24
Hi there,


I'm using Amarok and edited lot of track informations for the correct lyrics (yes, I know about the built-in lyrics finder). But recently I had to reinstall Amarok and all the lyrics were gone, even the built-in finder would now just show "fetching lyrics..." and nothing happens.

Is there any way of adding the lyrics *permanently* to the tag? 
Or are the lyrics added to songs under Amarok saved to a specific direction?

I already tried several tag editors (EasyTag, Ex Falso, Cowbell), but to no avail.

---

### Post by flugh on 2006-11-24
I have amarok configured to use sqlite for storage (goto Settings->Configure Amarok->Collection, at the bottom is a Collection Database option). The database file is stored at ~/.kde/share/apps/amarok/collection.db. You can back that file up from time to time.

I did a query on the lyrics table in the db, and it looks like the song file is identified by uri (filename), so if you rename a file outside of amarok, it may not be able to associate the lyrics with the new filename.

Basically, reinstalling amarok may have munged/deleted your well customized lyrics in collection.db, or if you moved your music files, move them back (or just do a symlink to make the old path+filenames legitimate).

Sorry if this makes no sense. Starting to confuse myself :-)

---

### Post by alphane on 2006-11-24
I'm guessing that Amarok saves this kind of data to an "Amarok Specific" location.  I say this because I have all of the MP3 songs on a 300gig portable HD that's formatted to NTFS. Since I've not enabled NTFS mounts (or such like) this drive is just read-only.

Whenever I load back into Amarok, the CD art etc I've got remain, but I can't write Tag info to the portable HD.

So I'm guessing that Lyrics and CD art, and probably some other stuff too, are stored locally in the file structure.

Can't help you with where though...

---

### Post by flugh on 2006-11-24
Check ~/.kde/share/apps/amarok/albumcovers/(cache,large,tagcover). I'm guessing if you're the type to do a lot of work on your music collection, backup ~/.kde/share/apps/amarok early and often!

---

### Post by rigol on 2006-11-25
I didn't moved or renamed the files.

The lyrics were gone simply due to the fact I changed the database from SQLite to MySQL *stupid me*- is there any way to export the settings? (I'm sure it is, I'll be looking.) 

But that way the lyrics are stored in an Amarok-specific location and are not accessable by other applications - I'm looking for a way to add the lyrics permanently to their files tags (I'm sure there was such an option when using a Windows lyrics tags manager) so I've got them even if I move or rename the files.

---

### Post by rigol on 2006-11-27
Nobody an idea?

---

### Post by Vaidya on 2007-08-10
Sorry not at my Linux machine... if you go to script manager in Amarok, and download a list of hot new scripts, you will find one script that claims to be able to add lyrics to mp3... have not tried it but the script seems to be pretty popular... see if this helps...

---

