---
title: "Audacious GTKui playlist question"
date: 2010-06-25
forum: Multimedia Software
---

### Post by Richard85 on 2010-06-25
So the problem:
In audacious, I can drag a song wherever I like in the playlist but in GTKui all the songs are fixed in the playlist. Is there anything I can do about this?

This one is out of curiosity but are you able to resize the audacious player? I know you can do ctrl+d to double size it but I can't seem to be able to stretch the player.

Seriously, in the last month since I've updated to lucid , I've switched from amarok to exaile to vlc to audacious to audacious gtkui. And I miss XMMS.

---

### Post by Deadite81 on 2010-06-25
Audacious GTKui would be so much better with the drag and drop functionality of the other Audacious.  The other Audacious is so ugly and in all those separate parts and won't accept being dragged from viewport to viewport...

Anyway, I just assumed that's the way it was made.  Linux music players are...well, you know.  Instead of putting a bunch of great features in ONE player, developers spread them out over 10 different players.  It sucks and is the bane of my existence.

If you find an answer- if there is one- I'd love to know, since Audacious GTKui is my favorite for simple quick playing of music files.

---

### Post by gandaran on 2010-06-25
> The other Audacious is so ugly
ugly? skin it! I have about a dozen xmms/winamp skins that makes it the best beautiful player to go with any gnome theme.

---

### Post by nenolod on 2010-07-11
> **Deadite81 said:**
> Anyway, I just assumed that's the way it was made.  Linux music players are...well, you know.  Instead of putting a bunch of great features in ONE player, developers spread them out over 10 different players.  It sucks and is the bane of my existence.

Audacious 2.4's gtkui is at (and infact exceeds) feature parity with the old Audacious UI.  In fact, we like it so much we made it the default UI in the 2.4 series starting with alpha3.

I mean with QMMP, we really don't feel the need to limit ourselves to the limitations imposed by the old UI.

---

### Post by Deadite81 on 2010-07-11
> **nenolod said:**
> Audacious 2.4's gtkui is at (and infact exceeds) feature parity with the old Audacious UI.  In fact, we like it so much we made it the default UI in the 2.4 series starting with alpha3.

I should say that I use Audacious GTKui quite a lot.  I use Rhythmbox for my heavy duty needs, but for playing directories from Nautilus, quickly checking out songs, podcasts from Gpodder, etc. nothing beets Audacious GTKui.  It's super fast and light.  I have not done much research about it, but I don't get why I have to have BOTH versions of Audacious when I never use the other one.

I also have 2.3, which I guess is the official stable release.  It sounds like you're a developer of Audacious GTKui, so were might I find 2.4?  Are you on Launchpad?  I suppose I'll search around.

So if you are a developer, what about the original question?
> So the problem:
In audacious, I can drag a song wherever I like in the playlist but in  GTKui all the songs are fixed in the playlist. Is there anything I can  do about this?
Are there new playlist features in 2.4?  This is the main thing that keeps me from relying on it more than I already do.

Also, why is the Getdeb version older than the one in the official repo?  I really dislike this, it seems epidemic - that is, things getting put on Getdeb and then neglected or abandoned.  Celtx comes to mind.

---

### Post by Deadite81 on 2010-07-12
Well I found Audacious 2.4.  I had to download all kinds of build-deps.  Everything compiled correctly, but it does not work.  The log says this:
```

** LOGGING STARTED AT Mon Jul 12 02:07:32 2010

Initializing Gtk+
Loading configuration
Initializing signal handlers
Handling commandline options, part #1
Initializing D-Bus
Trying to initialize D-Bus
D-Bus RC
Registering remote D-Bus interfaces
D-Bus MPRIS root
D-Bus MPRIS player
in mpris_player_init object->proxy == NULL, not adding some signals.
result=0x9cbe260
D-Bus MPRIS tracklist
D-Bus support has been activated
Initializing plugin subsystems...
Populating included interfaces
Handling commandline options, part #2
Registering interface hooks
Selecting interface gtkui

** LOGGING STOPPED AT Mon Jul 12 02:07:32 2010

```
Which tells me nothing.

At the command line it says this:
```

ALL OUTPUT PLUGINS FAILED TO INITIALIZE.
/usr/local/bin/audacious: unable to launch selected interface gtkui
```
So that's how my Audacious 2.4 experiment ends...tragically.  Not surprised.

---

### Post by Deadite81 on 2010-07-17
I realize that this post is old, but I have compiled Audacious 2.4 alpha3 and it is so much better than 2.3 there's almost no comparison.  And to answer Richard85's question, since I guess the developer or whoever won't, is that in 2.3 the playlist is what it is, but in 2.4 the features you are asking about are present.  You can rearrange your playlist to your hearts content.  

You have to build from source, which didn't work at all the first time I tried, but I was thinking about it today tried it again and it work with little issue (a few dependency errors and I had to run ldconfig).  I recommend using Checkinstall from the repositories.  You can get Audacious 2.4 [here]("http://audacious-media-player.org/") if you're still interested.

---

### Post by phz_swe on 2010-08-28
Relevant to this thread, Audacious 2.4.0 is now released. The difference in the GTK UI from 2.3 is remarkable.

I'm more familiar with Debian's release cycles, but I guess Maverick freeze has already passed, and thus the package won't show up in the official repositories until the next release ("Natty Narwhaal" :-) The names takes a bit getting used to). Since 2.4.0 in my eyes is clearly more pleasant and functional than 2.3, I would encourage people to build it themselves (soon enough "someone" will surely include 2.4.0 in a PPA though).

EDIT: Audacious 2.4-RC is in Maverick, which to me sounds like 2.4.0 also should make it.

I found a PPA to use in the meantime: [http://www.webupd8.org/2010/08/install-audacious2-24-beta-1-in-ubuntu.html](http://www.webupd8.org/2010/08/install-audacious2-24-beta-1-in-ubuntu.html)

---

### Post by Richard85 on 2010-08-29
Thanks for the update. I'm pretty exited about Audacious 2.4!

---

### Post by Richard85 on 2010-09-02
Is there a way to download Audacious 2.4 to 10.04 without having to compile ?
I don't even understand how to compile or what even needs compiling.....

---

### Post by Deadite81 on 2010-09-02
I found a PPA to use in the meantime: [http://www.webupd8.org/2010/08/insta...in-ubuntu.html]("http://www.webupd8.org/2010/08/install-audacious2-24-beta-1-in-ubuntu.html")

From 2 posts up...

---

### Post by Yellow Pasque on 2010-09-02
Ok, while we're on the topic of audacious, how do you make the playlist white text and black background? The opposite is the default for me and it's hurting my eyes at night.

---

### Post by Richard85 on 2010-09-02
Thanks Deadite

---

