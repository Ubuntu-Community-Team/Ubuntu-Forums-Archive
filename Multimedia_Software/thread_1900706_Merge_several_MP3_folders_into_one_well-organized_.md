---
title: "Merge several MP3 folders into one well-organized folder"
date: 2011-12-26
forum: Multimedia Software
---

### Post by xubuntu84 on 2011-12-26
I've googled and searched these threads with no luck on what I am trying to accomplish.

I have 3 folders of music, spread out between computers, that I would like to merge into one folder on my Ubuntu media server from which I can stream later.

My problem is that when I copy the music files over to the server, I am creating a lot of duplicates.  What is the best method to copy these folders at about 30 GB each into one that is organized by a media player on the server?  I am not partial to Banshee or Rhythmbox, but it seems I need some sort of software that will read the mp3 tags and put the music in folders by Artist/Album, only if that song does not already exist.

This seems like a rather straight-forward task, but I am having no luck with it.  Any help is much appreciated!

---

### Post by papibe on 2011-12-27
That is not a trivial task.

This is what I think I've learned doing a similar task:
[LIST]
[*]Although it sounds very appealing to design and sort your music in a structured directory tree, for the most part the you will be fine with the player's own sort (using ID3 tags).
[*]Classical music could be the exception.
[*]Then, in general, it is more important to have the correct tags, than a good directory tree.
[*]There are two cases of duplicate songs:
[LIST]
[*]Same content, but different 'rips' (the files are different).
[*]The file are identical (even if the have different names).
[/LIST]
[*]For identical files, you can relatively easy eliminate duplicates. You would need to write a script that:
[LIST]
[*]Determine every song sum (using any sum command line tool, like md5sum).
[*]Sort that list.
[*]Then delete files with duplicate sums.
[/LIST]
[/LIST]
I hope that helps.
Regards.

---

### Post by xubuntu84 on 2011-12-27
Thanks for your response, and I will look in to using the checksum to find identical files within the directory structure; I had not thought about that approach yet.

What about adding new songs to Banshee?  I can't seem to find a feature that will allow you to remove duplicates within that program.  One would think that under the Tools menu there would be a "remove duplicates" option.  I hate to bring up other OSs, but iTunes does this quite nicely.  Like I said, if I had to switch from using Banshee to something else I would not mind (so far I've attempted Rhythmbox and Songbird).

---

### Post by rubylaser on 2011-12-28
This looks to be a very good start for [automating this with bash]("http://cefn.com/blog/itunes_duplicates.html").  It's tailored toward iTunes, but should work well with standard folder structures as well.  Or, [dupeGuru]("http://www.hardcoded.net/dupeguru_me/") is another option.  Here's a [Youtube video]("http://www.youtube.com/watch?v=Vn6Iu1JtPkA") of a guy demonstrating it's use.

---

