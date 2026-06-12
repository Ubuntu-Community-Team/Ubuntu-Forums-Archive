---
title: "CD to FLAC (with Tags)"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by pdowling on 2007-03-12
Hi,

Fairly new to Ubuntu, but having a great time!

Anyway, I'm using GRIP to Rip and Encode to FLAC.  Only problem I'm having it when I try to add those into Rhythmbox it looks like they have no tagging.

I know FLAC supports tagging, but GRIP only seems to have the option of adding tagging to MP3.

What is the preferred way to create FLAC files from CD with tagging?

Is it possible with GRIP?

I'm using Edgy, and thanks!

- Peter

---

### Post by Ergo on 2007-03-12
Under preferences, have you tried changing the the version of the tag.  i.e. v1 or v1.1 
Also, I seem to remember having the option of selecting the file types to add tagging to.  I'm not on my usually machine right now, so I can't be more precise.

---

### Post by shirilover on 2007-03-13
you can add the following to the encoder command line text box:

```
-T "ARTIST=%a" -T "TITLE=%n" -T "ALBUM=%d" -T "DATE=%y" -T "GENRE=%G" -T "TRACKNUMBER=%t"
```

---

### Post by yabbadabbadont on 2007-03-13
If you don't mind using a non-gui app, abcde is a nice ripper.  It supports ripping to flac, ogg, mp3, and others.  It can rip to multiple formats at the same time if you wish and it supports tags for flac.

---

### Post by pdowling on 2007-03-13
> **Ergo said:**
> Under preferences, have you tried changing the the version of the tag.  i.e. v1 or v1.1 
Also, I seem to remember having the option of selecting the file types to add tagging to.  I'm not on my usually machine right now, so I can't be more precise.

Thank you for the suggestion, but I believe that only applies to ID3 tags which are not supposed to be used with FLAC I think.

---

### Post by pdowling on 2007-03-13
> **yabbadabbadont said:**
> If you don't mind using a non-gui app, abcde is a nice ripper.  It supports ripping to flac, ogg, mp3, and others.  It can rip to multiple formats at the same time if you wish and it supports tags for flac.

I don't mind command line, and I'm certainly interested in ripping to multiple formats.  I'll take a look - thanks.

- Peter

---

### Post by pdowling on 2007-03-13
> **shirilover said:**
> you can add the following to the encoder command line text box:

```
-T "ARTIST=%a" -T "TITLE=%n" -T "ALBUM=%d" -T "DATE=%y" -T "GENRE=%G" -T "TRACKNUMBER=%t"
```

Aha! -T --tag.  And of course it is in the documentation...

[http://flac.sourceforge.net/documentation_tools_flac.html#encoding_options](http://flac.sourceforge.net/documentation_tools_flac.html#encoding_options)

I feel silly for missing it.  Now I'm off to find a reference on what tags are available.

Thanks for the tip.

- Peter

---

### Post by pdowling on 2007-03-13
> **yabbadabbadont said:**
> If you don't mind using a non-gui app, abcde is a nice ripper.  It supports ripping to flac, ogg, mp3, and others.  It can rip to multiple formats at the same time if you wish and it supports tags for flac.

Wow!  abcde rocks!  thanks for pointing me to it.

Couple of quick questions about abcde though...

After some funking around with the abcde.conf file I've got it pretty close to doing exactly what I want.  Two issues:

1. I can't get the mp3 encoding (using lame) to do the bitrate I want.  Here is what I put on the OUTPUTTYPE line in abcde.conf...

[INDENT]OUTPUTTYPE=flac,mp3:"-b 320"[/INDENT]

But the output files are still coming up with the default 128 bit.

2. I get an error message at the end of the encoding as follows:

[INDENT]Couldn't reset permissions on '/media/sdb5/abcde.e011460f/track02.mp3'
Finished.[/INDENT]

When I play the mp3 files I can see that the tagging was done so I'm not sure what this error message is about.  It doesn't seem to affect anything, but I want to make sure it isn't something to worry about before I start encoding all my CDs!

Thanks for the help so far!  Unbuntu and Linux rock.

- Peter

---

### Post by pdowling on 2007-03-13
> **pdowling said:**
> 1. I can't get the mp3 encoding (using lame) to do the bitrate I want.  Here is what I put on the OUTPUTTYPE line in abcde.conf...

[INDENT]OUTPUTTYPE=flac,mp3:"-b 320"[/INDENT]

But the output files are still coming up with the default 128 bit.


Never mind about this one.  I realized I was putting this in the wrong place in the abcde.conf file.  Instead I needed to change the LAMEOPTS= line by uncommenting it.  I then had to put in a lame option as defined in the man page for lame.  Haven't totally decided on what I'm going to use, but leaning towards...

LAMEOPTS="--preset insane"

...which is maximum (320) constant bitrate - I heard that VBR sometimes causes problems.

Thanks again for all help.

- Peter

---

### Post by yabbadabbadont on 2007-03-13
What filesystem is used on sdb5?  If it is (v)fat or ntfs, you would see errors about permissions as there isn't any support for them with those filesystem types on Linux.

---

### Post by pdowling on 2007-03-13
> **yabbadabbadont said:**
> What filesystem is used on sdb5?  If it is (v)fat or ntfs, you would see errors about permissions as there isn't any support for them with those filesystem types on Linux.

It is indeed fat32 - makes sense.

Thanks very much.

- Peter

---

### Post by yabbadabbadont on 2007-03-13
> **pdowling said:**
> It is indeed fat32 - makes sense.

Thanks very much.

- Peter

You can add the "quiet" option to the mount options in /etc/fstab for vfat drives so that attempts to chown or chmod permissions on that filesystem will not produce error messages.

---

### Post by andrew.46 on 2007-09-20
Hi'

> **pdowling said:**
> Thank you for the suggestion, but I believe that only applies to ID3 tags which are not supposed to be used with FLAC I think.

 To add metadata to flac files *manually* you can use metaflac. As you have probably already found abcde will add these for you using metaflac.

                                            Andrew

---

