---
title: "Change the playlist format for Amarok 2.3 ??"
date: 2010-05-02
forum: Multimedia Software
---

### Post by arsenic23 on 2010-05-02
OK, For years I've always saved all of my playlists to a share so that I could then play them over my media server when I leave my office (using an mplayer script).  Well the new version of Amarok saves its playlists as *.xspf files.  Completely useless for playing in mplayer (apparently).  Is there anyway to force Amarok to switch back to .m3u playlists?

I wanna save some of these neat new generated playlists and que them up in the living room while I bake.

---

### Post by mc4man on 2010-05-02
While I don't use amarok 2, have it on a lucid testing install I haven't yet dumped.
In the 'export playlist as' there are 3 choices here - the mp3 audio (streamed) will create a .m3u 

do you not have that option?

---

### Post by arsenic23 on 2010-05-02
> **mc4man said:**
> While I don't use amarok 2, have it on a lucid testing install I haven't yet dumped.
In the 'export playlist as' there are 3 choices here - the mp3 audio (streamed) will create a .m3u 

do you not have that option?

Hmmm, I completely didn't notice that. I suppose I could do it that way.
Having to export each playlist one at a time is going to be monstrously tedious though.

Thanks.

---

### Post by mc4man on 2010-05-02
> Having to export each playlist one at a time is going to be monstrously tedious though.

Have you tried seeing if you close amarok 2 after setting to .m3u in the export option if it then defaults to .m3u?

Otherwise maybe there's something in it's config file, I'll take a look

Edit: don't see anything in the rc file and at least here the export always opens to .m3u so don't know how to change for your purpose

---

### Post by arsenic23 on 2010-05-19
Well I think I'm getting used to exporting each playlist.

Unfortunately they don't set their permissions correctly.  Is there a separate KDE setting for default permissions?  The exported playlists are set to 660 instead of 644 like everything else I save.  Completely locks my media server out of them until I chmod each one.

As much as I've always disliked KDE, konversation and amarok have always been daily use programs for me.  I'm soundly tempted to try and find another playlist manager, even though I kind of like the new dynamic playlists feature in amarok.

---

