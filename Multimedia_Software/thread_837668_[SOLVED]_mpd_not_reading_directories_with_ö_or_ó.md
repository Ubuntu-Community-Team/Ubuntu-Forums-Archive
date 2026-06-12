---
title: "[SOLVED] mpd not reading directories with ö or ó"
date: 2008-06-22
forum: Multimedia Software
---

### Post by funkydan2 on 2008-06-22
I'm having trouble to get mpd to put files into its database that have a ö or ó in the directory (e.g. Björk and Sigur Rós). Strangely though it happily reads a directory with an ä in its name (Arvo Pärt).

I've already tried a number of different options for the filesystem_charset option (sticking with UTF-8 at the moment).

What do I need to do in order to listen to Björk and Sigur Rós with MPD? Alternatively, is there another project that's equivalent to MPD (enables me to control music playback on my media server remotely).

---

### Post by mcduck on 2008-06-23
> **funkydan2 said:**
> I'm having trouble to get mpd to put files into its database that have a ö or ó in the directory (e.g. Björk and Sigur Rós). Strangely though it happily reads a directory with an ä in its name (Arvo Pärt).

I've already tried a number of different options for the filesystem_charset option (sticking with UTF-8 at the moment).

What do I need to do in order to listen to Björk and Sigur Rós with MPD? Alternatively, is there another project that's equivalent to MPD (enables me to control music playback on my media server remotely).

For me, setting UTF-8 as the charset in MPD's config file has worked nice. But you'll also need to check that the actual names and tags on your files use UTF-8 as well..

---

### Post by funkydan2 on 2008-06-23
How do you do that?  I've just renamed the folder making sure that I copied the ö character straight out of the gnome character map and it made no difference.

The files are all on an ext3 filesystem, on an Ubuntu (gusty) box.  Is there any way to check the encoding that is being used?

---

### Post by vanadium on 2008-06-23
For me, this is working correctly with the default settings in /etc/mpd.conf (or your user specific mpd.conf depending on how you installed):

```

# If file or directory names do not display correctly, then you
# may need to change this.  In most cases it should be either
# "ISO-8859-1" or "UTF-8".  You must recreate your database
# after changing this (use mpd --create-db).
#
filesystem_charset              "UTF-8"
#
# The encoding that ID3v1 tags should be converted from.
#
id3v1_encoding                  "UTF-8"

```

You thus need to check that config file. Look first in your home directory for ".mpd.conf". If such a file does not exist, you are using a system wide config file, which is /etc/mpd.conf.

---

### Post by funkydan2 on 2008-06-23
:redface: Darn.  The problem had nothing to do with unicode and **everything** to do with file permissions!

---

