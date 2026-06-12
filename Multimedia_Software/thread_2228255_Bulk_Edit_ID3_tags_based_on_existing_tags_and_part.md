---
title: "Bulk Edit ID3 tags based on existing tags and part of filename"
date: 2014-06-06
forum: Multimedia Software
---

### Post by Jamie_Dow on 2014-06-06
I am wanting to know how to get the ID3 tags of some .ogg files (and some mp3 files) into the format I want.
I'm doing this for some public domain audiobook files for large works where the book is split between several files. The current filenames are (for example):

201-LYSIS.ogg
202-LYSIS.ogg
203-LYSIS.ogg

This is for 3 audio files of Plato's Lysis, read in order (where 201.... is the first, and 203 ... is the last). That's fine. I don't need to change the filenames.

What is more of a problem is that the "title" ID3 tag for all of these files is simply "Lysis". So, when these are played on an audio player (e.g. a phone) that displays tracks by their id3 tags, it's impossible to tell from a list which file you are on.

There is an id3 tag for "track number", where these 3 files (and other similar - larger - sets) are correctly numbered 1, 2 and 3.
So, what I'd like to do is to create the new id3 'title' tag, based on typing "Lysis - part " and then adding (concatenating onto the end) either the third character of the filename, or the 'track number' id3 tag. So as to yield, "Lysis - part 1" (.... part 2, .... part 3, etc.).

In other cases, the "title" id3 tag contains things like "Book 2 - part 7", but doesn't contain the title of the work itself.
So I'd like to be able to concatenate that into the "title" tag for multiple files, but without losing the existing information that is there already.

It's not at all obvious that the supposed mass-editors for id3 tags can do this. But I'm mystified as to why they can't!
What I'm after is something like KRename for id3 tags.
I've tried Kid3 and EasyTag. And it's possible that they can do this. But if they can, I have not yet worked out how to do it. As far as I can see, they can only do the crude pasting of filename and file information into id3 tags (where there's no indication of how to select only part of the filename, for instance - e.g. the 3rd character), or vice versa - i.e. the creation of a filename based on the tags.

Grateful in advance for any help. Thanks.
Jamie

---

### Post by papibe on 2014-06-06
Hi Jamie_Dow.

I've used some of those editors, and most of them, if not all, assume that songs are stored in an album subdirectories.

For instance: if you have LYSIS's tracks on one directory, and Book2's in another, like this:
```

Music/
    LYSIS/
        201-LYSIS.ogg
        202-LYSIS.ogg
        203-LYSIS.ogg
    Book2/
         Book 2 - part 1.ogg
         Book 2 - part 1.ogg
         Book 2 - part 2.ogg
...

```
editors like Kid3 should be able to set tags from the file name, based on a custom rule. You would have to provide a custom rule for every directory. For example, I believe something like this would work for the 1st directory:
```
20%{track}-%{title}
```
Alternatively, you could use the same 'rule' approach using a command line tool like 'lltag' to script the tagging. 

If I remember correctly Kid3 lets you rename/tag, without actually changing them until you said so. In case of the command line tool, there's an 'dry run' option that would show what would change without actually doing it. In any case, I'd recommend either backing up, or creating a test directory with copies of some of the files.

Hope it helps. Let us know if you need more help with that.
Regards.

---

### Post by ufleisch on 2014-06-07
You can set tag frames from the contents of other tag frames using Kid3's "Import from Tags" function. To set the title using information from the track number, select the files in Kid3. Use menu File/Import, From Tags, Add, then enter

Format: Add part nr to title
Source: %{title} - part %{tracknumber}
Extraction: %{title}(.+)

Click button Save Settings, you have now added a new import format.
Now click Apply, Close, OK.

If there is no track number present, you can set it from the third character in the filename using another import format:

Format: Track from 3rd character of filename
Source: %{file}
Extraction: \d\d%{track}(\d)

In this case you will have to apply first "Track from 3rd character of filename", then "Add part nr to title".

The "Import from Tags" function is explained in the [Kid3 handbook]("http://kid3.sourceforge.net/kid3_en.html#import-text"), at the end of the "File -> Import" section.

---

