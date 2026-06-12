---
title: "My music player is no longer recognized by Rhythmbox!"
date: 2009-02-03
forum: Multimedia Software
---

### Post by ePierre on 2009-02-03
Hi!

I've been using Rhythmbox along with my Meizu miniplayer for ages now, but I experience a nasty bug for a few weeks...

When connecting my USB music player to my laptop, it's recognized by Ubuntu (8.04) as a media disk, so I can open it and browse its content, add files, etc. Moreover, Rhythmbox is automatically launched; it used to display the content of my media library (on my laptop hard drive) as well as the music stored on my music player (accessible through an icon on the left panel), but now there is no more icon!

The main problem is I used to select albums from my media library and send them on my music player using Rhythmbox because, since my music player filesystem is FAT32, it doesn't allow "special" characters such as "? : ;" ... which are unfortunately quite common in the files I have...
Rhythmbox has a function that convert filenames in order to be able to send them on a FAT FS.

I tried several Rhythmbox options (such as the MTP plugin, changing the settings on my Meizu to use MTP as well), but it didn't work either.
I also tried to format my Meizu, but still: no changes!

A friend of mine told me to check in the [FONT="Courier New"].gnome2/rhythmbox/[/FONT] folder, but even when deleting all content inside this folder, nothing changes... I tried to check in the GConf editor too, but there are no Rhythmbox-related options that look strange...

Could anyone help me on that problem?

Thanks in advance!

---

### Post by kostkon on 2009-02-03
Go to the root folder of your mp3 player and create an empty text file called
```
.is_audio_player
```
Unplug your player and plug it again and see if Rhythmbox will recognise it.

---

### Post by ePierre on 2009-02-03
Whoo!
[B]
Thank you very much, it works now![/B]

Where did you learn this? And do I have to keep this file forever?

Once again: thanks! I'll now be able to listen to my favorite John Coltrane recordings in the train :)

---

