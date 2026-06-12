---
title: "Files not being read correctly in Media Player"
date: 2011-01-20
forum: Multimedia Software
---

### Post by Sugi on 2011-01-20
I am not sure what is happening with my music, but it's driving me mad and making me pull out my hair.  My ID tags are not being read correctly through through both Rhythmbox and Banshee, but my tag editor, dBpoweramp, and Ubuntu properties reports the information correctly.  All of my music is stored on another computer stream via the network.  For example, I have an album by X Japan label as this:
Track: Break the Darkness
Artist: X
Album: I'll Kill You EP
Year: 1985

But banshee breaks up the album into two different albums, and on top of that, Banshee see it as X Japan, but reads it as X for the artist.  And it's not just this album, it happens to a lot of my albums, sometimes they are missing tracks or mislabel or missing cover art, etc, etc, but only within the media player.  Why is this happening and has anyone else notice this?

Here's an image just to prove I am not crazy!
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181574&stc=1&d=1295540209[/IMG]

Ubuntu 10.10 x64
Banshee 1.8.0
Rhythmbox 0.13.1
Music streamed over network

Sugi

---

### Post by renzokuken on 2011-01-20
notice the capital 'J' and lower case 'j' of japan.

standardise those (i.e. all upper case) and should be ok

---

### Post by renzokuken on 2011-01-20
notice the capital 'J' and lower case 'j' of japan.

standardise those (i.e. all upper case) and should be ok

---

### Post by renzokuken on 2011-01-20
*removed

---

### Post by renzokuken on 2011-01-20
could it have something to do with the 'J' of 'Japan'

in your image above, one is upper case and the other is lower case. try standardising them and see what happens

---

### Post by Sugi on 2011-01-20
But that's the thing though, It's not labelled as "X Japan", but instead it's labelled as "X" without Japan.  You can see in the photo that it's Just simple "X" but the preview of the album says other wise.  I even included the properties of the file name for track 4 of that album.  Why is it mislabelling it?

Sugi

---

### Post by Sugi on 2011-01-21
So, I went through my whole music collection and made folder images for everything and check all files.  Everything is tagged correctly within tag editor, ubuntu's properties, and dbpoweramp, but still banshee reports mislabelled tags.  It's as if I never retagged my music, but of course I did, [checked it three times now over both ubuntu and windows.]  Hasn't someone else noticed this problem too?

Sugi

---

### Post by Sugi on 2011-01-22
24 bump :S

Sugi

---

### Post by Sugi on 2011-02-01
I still don't a clue what's wrong with this.

Sugi

---

### Post by Sugi on 2011-02-03
I have noticed, some of the music files has corrected themself, but I did not make any chances to them. This is such a weird problem.

Sugi

---

### Post by Sugi on 2011-02-06
I am still having issues with this problem.

Sugi

---

### Post by cascade9 on 2011-02-06
Have you tried checking the ID3 tag versions? Maybe what ubuntu, etc can read banshee cant. 

You could also see if the tags are unicode as well (IIRC non-unicode tags can cause all sorts of odd problems on some systems).

---

### Post by Sugi on 2011-02-07
I have tried to check ID3 and ID2, as I thought this might be the problem, but I haven't been able to check them separately.  Though, I am sure my problem writes to them both, or only ID3 tags.  They are unicode coded though I enabled writeable unicode coded on my tagger, Tag & Rename.

Sugi

---

### Post by cascade9 on 2011-02-08
I havent seen Tag & Rename for ages. I'd give a different tagger a go, EasyTag if you want a linux native tagger, or MP3Tag if you do your retagging with windows.

---

### Post by Sugi on 2011-02-11
I use to use EasyTag, but the automatic tagging features is lacking compared to Tag and Rename.  I hate to use non-native application, but my searches hasn't come close to the ease and usefulness of Tag & Rename. :S

I am actually wondering, if this is related more directly to transcodes within Linux Media players...

Sugi

---

### Post by Sugi on 2011-02-13
Bump for more information.

Sugi

---

### Post by cascade9 on 2011-02-13
> **Sugi said:**
> I am actually wondering, if this is related more directly to transcodes within Linux Media players...

I doubt it. Though I'm a little confused about what you mean with "transcodes within linux media players", maybe you've got a different meanign for 'transcodes' (to me its converting one file format into another). 

AFAIK, the issue you are having must be from either the tags, or (less likely but still possible) your media player is pulling the information from the net.

---

### Post by New00Folder on 2011-02-16
Probably you've got multiple tags with different data in your files. There's a program called mp3tag for windows. That's the thing that'll work. You can cut the tag you want to keep and remove all other tags and paste the correct tag back. All tag editors available for linux are lousy.
Hope it helps.

---

### Post by cascade9 on 2011-02-17
> **New00Folder said:**
> Probably you've got multiple tags with different data in your files. There's a program called mp3tag for windows. That's the thing that'll work. You can cut the tag you want to keep and remove all other tags and paste the correct tag back. All tag editors available for linux are lousy.
Hope it helps.

MP3Tag is great. I've used it a lot. 

I've never had any porblems with Easytag, and to say that 'all tag editiors avaible for linux is lousy' is going too far IMO.

---

