---
title: "Hide samba shares from the Nautilus tree"
date: 2013-04-24
forum: Networking &amp; Wireless
---

### Post by darkhelmetchris on 2013-04-24
Greetings all.

So, I've been using Ubuntu now for a while, and helping out here when I can.  I use Samba networking pretty regularly, and if you have used it to much extent, you already know that Nautilus will show your server-share mounts in the places/tree.  I'm looking for a way to hide those, but I don't want to hide all of the gvfs mounts, just the samba ones.  Here's a little more detail about what I'm saying and what I'm after...

If you make nautilus show the tree on the left, and you connect to a samba share on some other machine (be it a Windows machine or a Samba server) you get a convenient link in your tree view, something like:  "myshare on myserver."  Now, many software apps can handle that, but there are still a great many that do not, and need to have a standard path.  So, you might browse to "~/.gvfs/myshare on myserver/myfile" in order to work with your data.  Some of you keeners know that you can create a symlink in your home folder to the "~/.gvfs" path and you'll get a nice tree view to your share that works with the "nautilus/gvfs unaware" software.  That's all cool.  My question is:  how can I hide the samba shares that have been mounted via gvfs from showing up in the Nautilus tree/places.

Now, some of you real keeners will say, hey just mount it in fstab (with cifs and credentials) and that's not bad, truly.  I would really prefer to actually hide the quick-links in the Nautilus tree, because I often disconnect from and connect to other servers, and so do my users; it's a dynamic environment here, with servers being tested or machines moving around.  So, the fstab isn't a great option for this scenario.  I like using gvfs, because it's dynamic.  And, no matter how hard I try, every once in a while I still use the quick-link in nautilus and I try to open a file that loads software that won't follow that kind of link and... such is the nature of this call for a little help.

I've looked around, and tried to find other docs on this and, I can't seem to locate what I'm after.  Maybe I'm just the only one that's like this?  I don't know.  I have seen some docs on how to hide all the gvfs, but then I have very inconvenient access to removable devices, or they don't work at all.

This isn't a showstopper, just a nice to have; When I forget, I just grit my teeth and mutter.. duh, darkhelmet, you've opened the nautilus quick-link again... go to the filesystem symlink.  But, it would be nice if I could remove the temptation.

So, does anyone have any info on how to hide or otherwise prevent nautilus from showing my samba mounts in the tree/places?

---

### Post by darkhelmetchris on 2013-05-03
It might be more accurate to say that I'm looking for a way to hide Samba shares from the "Places" structure that is available in Nautilus.

I have attached a picture to show you what I'm talking about.

---

