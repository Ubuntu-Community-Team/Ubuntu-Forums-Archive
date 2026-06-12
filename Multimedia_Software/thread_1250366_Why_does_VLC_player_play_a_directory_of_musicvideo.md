---
title: "Why does VLC player play a directory of music/video files in wrong order?"
date: 2009-08-26
forum: Multimedia Software
---

### Post by Rytron on 2009-08-26
Hi.
I notice that when I download a series of videos and name them 1,2,3,4,etc that VLC player does not play them in alphabetical/numerical order.
This strange behavour also happens sometimes when I play a directory of music with VLC player. I want music & video files to be played in alphabetical order.
I don't know the order that VLC player decides to play the files.

I never get this problem with Totem Movie Player. On occasion I get a bunch of video files that Totem Movie Player wont play. VLC does play them but as I say, not in the desired order.

As far as I know when I used VLC in Windows, the files always played in the correct alphabetical/numeric order. 

Does anyone have a solution?
Thanks.

---

### Post by andrew.46 on 2009-08-26
Hi Rytron,

> **Rytron said:**
> I notice that when I download a series of videos and name them 1,2,3,4,etc that VLC player does not play them in alphabetical/numerical order.

Unfortunately I am no expert with vlc but I notice with my own copy when I ask vlc to play a directory of files this then can be *reordered* by using the playlist feature ctrl+L. But for the life of me i could not see a setting to mandate an alphabetic/numerical order for all playlists :(.

Andrew

---

### Post by Rytron on 2009-08-27
> **andrew.46 said:**
> Hi Rytron,

Unfortunately I am no expert with vlc but I notice with my own copy when I ask vlc to play a directory of files this then can be *reordered* by using the playlist feature ctrl+L. But for the life of me i could not see a setting to mandate an alphabetic/numerical order for all playlists :(.

Andrew

Thank you andrew.46
The Playlist feature certainly helps a bit. However say for example someone has a directory of a series of 12 video files. Thats a lot of reordering.

I'd like to know does everyone else have this problem with VLC in Ubuntu?

:confused:

---

### Post by wildnfree on 2009-08-27
> **Rytron said:**
> Thank you andrew.46
The Playlist feature certainly helps a bit. However say for example someone has a directory of a series of 12 video files. Thats a lot of reordering.

I'd like to know does everyone else have this problem with VLC in Ubuntu?

:confused:

Hello,

If you import your directory of clips into the Media Library first, you can then very quickly drag and drop them into the playlist from the Media Library. This means they go in in what ever order you want.

One tip: Try dragging and dropping in the reverse order to what you want. ie start from last to first. :P

---

### Post by Rytron on 2009-08-27
Thank you wildnfree

---

### Post by mc4man on 2009-08-27
There have been issues with opening dir.'s in vlc since it went to the qt4 interface.
Depending on what distro and what vlc release the behavior will vary

What seems to also work on 0.9.9a is to have the playlist box open and drag the dir. into it. It will show up as a single entry, double clicking on the entry should expand it with the tracks or files in proper order.

---

### Post by Rytron on 2009-08-27
> **mc4man said:**
> There have been issues with opening dir.'s in vlc since it went to the qt4 interface.
Depending on what distro and what vlc release the behavior will vary

What seems to also work on 0.9.9a is to have the playlist box open and drag the dir. into it. It will show up as a single entry, double clicking on the entry should expand it with the tracks or files in proper order.

Thank you mc4man.

---

### Post by mc4man on 2009-08-27
Just as a note and another possibly useful thing for all vlc ver. 0.9.x, 1.0.1. 1.0.2, 1.1

The drop and expand in playlist will probably only work correctly in 0.9.x, which is the version i've settled on for the moment ( though I ocassionally change to 1.0.2

What can prove useful is to create a 2nd vlc.desktop with an enqueue command.
While it's created initially from the r. click menu,( and will remain a r. click option on any file type ) it's use is better suited from the d. left click when any particular file type has been associated with it.

The effect would be to first add and start playing a file. Then any additional files clicked on will be appended to the playlist in the order clicked on **without stopping p**layback of the current one.

 The 'allow only one instance must be set as per screen 1, screen 2 shows setting 'Vlc Enqueue' as default for m4a, ( Vlc Enqueue was previously created on some other file type

described here
[http://ubuntuforums.org/showthread.php?p=7584086#post7584086](http://ubuntuforums.org/showthread.php?p=7584086#post7584086)

---

### Post by Rytron on 2009-08-27
Thanks again mc4man. Does anyone know exactly the order that VLC decides though? Its a mystery!

---

