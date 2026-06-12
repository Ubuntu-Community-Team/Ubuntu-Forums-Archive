---
title: "Edit AAC (mp4, m4b) Tags"
date: 2008-10-15
forum: Multimedia Software
---

### Post by jdforsythe on 2008-10-15
I was searching for how to do this and there was a single, unsolved thread in the archives, so I'll post the solution I found.

Easytag can edit AAC tags if you install the version with AAC support. I'm not sure which repo it is in, but you probably already have them all enabled anyway.

If you already have a version of easytag installed:
sudo apt-get remove easytag

To install the AAC support version:
sudo apt-get install easytag-aac

This will install to your Sound & Video menu. It can also be run at the command line with:

easytag

You can also pass a directory to the command, so it could be added to Nautilus for right-clicking on a folder.

easytag /PATH

Remember to use " quotes when there are spaces in the names, like so:

easytag /data/Music/"Artist Name"/"Album Name"

It does not, however, have the ability to pass a specific file to the program, only a directory.

---

### Post by jdforsythe on 2008-10-16
I forgot to mention, if you want to change the tags of your .m4b audio book files, you have to rename them first to .m4a, change the tags with easytag, then rename them back to .m4b

Haven't found a way around this yet. I'm looking for a command-line aac tag editor.

And btw, that's a typo in the subject, should be m4a, m4b not mp4.

---

### Post by swajime on 2011-12-30
Have you found one yet?

---

### Post by nothingspecial on 2011-12-30
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

