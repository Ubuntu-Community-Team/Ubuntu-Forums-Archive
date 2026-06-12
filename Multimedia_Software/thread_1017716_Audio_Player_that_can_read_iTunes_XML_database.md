---
title: "Audio Player that can read iTunes XML database?"
date: 2008-12-21
forum: Multimedia Software
---

### Post by mfleonhardt on 2008-12-21
Hello everyone,

Sorry if this has been brought up already...I tried searching, but keywords like iTunes, XML etc. bring up all kinds of unrelated topics...

So, I've almost got my ideal music setup going on the home network.  Basically, I've got a Ubuntu 8.04 machine that handles all the server functionality (file serving, proxy, MySQL, Apache, et al).  I've got a music drive on that machine that is shared via Samba for Windows clients on my network (We've bot both Mac and PC laptops on our network for various reasons).

On our clients, I've got iTunes configured to locate the music library (audio files and the library files) on the linux server.  Total synchronization--my wife imports a CD on her PC laptop, I open iTunes on my Mac and there it is!  The only irritant here is that we kind of have to coordinate so that we don't have two machines trying to write to the library file at once.  For the most part, though, I'm pretty happy with this part of the setup.

Here's the question...are there any media players for Linux that can read the iTunes library file instead of/in addition to keeping it's own library.  I've used Amarok/Rhythmbox/Exaile, and haven't run into this functionality.  It's very irritating to have to re-import the whole music directory every time I open a music player in Linux.  We're at 10,000 songs and growing, so it's a pretty time consuming process.  I have to imagine there's something that can just check the XML file that iTunes keeps to sync the library, or a little utility that could quickly convert the XML to Amarok's database format...just don't know where to look.

I'm also open to the option of running iTunes under wine, but it doesn't seem like anyone has got that really functional yet...correct me if I'm wrong.

For the server, I'm mostly interested in playback.  I don't see us using it to add to the collection, burn CDs or do any kind of iPod stuff.  The server is hooked into the sound system for the house though, so it would be nice to manage the library from our various laptops and be able to just open the music player on the server and have our collection all updated and ready to go.

TIA,
Matt

---

### Post by programmer8922 on 2009-01-16
I have not tried any of these, so hopefully they will work.
[Banshee iTunes import plugin.]("http://www.ubuntuessentials.net/?p=515")
[iTunes Library Importer for Songbird]("http://addons.songbirdnest.com/addon/9"), requires a work around for some versions, which can be found [here]("http://getsatisfaction.com/songbird/topics/cant_import_from_itunes_in_linux").

---

### Post by mfleonhardt on 2009-01-16
> **programmer8922 said:**
> I have not tried any of these, so hopefully they will work.
[Banshee iTunes import plugin.]("http://www.ubuntuessentials.net/?p=515")
[iTunes Library Importer for Songbird]("http://addons.songbirdnest.com/addon/9"), requires a work around for some versions, which can be found [here]("http://getsatisfaction.com/songbird/topics/cant_import_from_itunes_in_linux").

Thanks for the links.  I'll check these out.  Since it looks like it's still a manual process, I'm wondering what the time saving advantage might be.

I'd really like something transparent such as a plugin that would automatically sync the library when the player opens if the mtime is newer than the last sync, or a command line utility that could be cron'ed to do the same thing.

Looks like I might have to whip something up myself...

---

### Post by zim2dive on 2009-01-18
I;ve been searching for the same thing... sure I can write a cron job and adapt the scripts floating around to convert the iTunes XML to a library for Rhythmbox, convert playlists, etc... but my overall question is that if *I* can do this fairly easily, why the bleep isn't there a player that will read the DB directly (over SMB share, etc) ??  Not a one-time Import, but an on-going "use this as my source".

---

### Post by mfleonhardt on 2009-01-19
> **zim2dive said:**
> I;ve been searching for the same thing... sure I can write a cron job and adapt the scripts floating around to convert the iTunes XML to a library for Rhythmbox, convert playlists, etc... but my overall question is that if *I* can do this fairly easily, why the bleep isn't there a player that will read the DB directly (over SMB share, etc) ??  Not a one-time Import, but an on-going "use this as my source".

Hear, hear!  I'm sure that if Apple didn't want other players to be able to do this, they would have chosen to store their data in some proprietary serialized format.  Instead, they went with XML, a specification designed to aid data portability between languages and applications.  I mean c'mon!  They're begging us to do this!

</tirade>

---

### Post by umechanism on 2009-01-19
Have you tried gtkpod?
[http://www.gtkpod.org/about.html](http://www.gtkpod.org/about.html)

---

### Post by zim2dive on 2009-01-19
> **umechanism said:**
> Have you tried gtkpod?
[http://www.gtkpod.org/about.html](http://www.gtkpod.org/about.html)

It looks great if you want to sync to iPod, but can it play music?

---

### Post by umechanism on 2009-01-19
It seems like I once was able to import my database to my hard drive then play the tunes.  It has been a while since I used it so I can not remember exactly.  Download it and give it a try.  They have .deb files.

---

### Post by mfleonhardt on 2009-01-19
> **zim2dive said:**
> It looks great if you want to sync to iPod, but can it play music?

1. If anything, it further reinforces the point that this operation ought to be possible in an audio player.

2. If you look at the OP (me), you'll notice that I'm strictly interested in playback and specifically NOT in iPod connectivity

[QUOTE=mfleonhardt]I don't see us using it to add to the collection, burn CDs or do any kind of iPod stuff.[/QUOTE]

3. On an unrelated note, it is nice to see that libgpod now has algorithms to deal with the iPod Touch.  I know that was a mess when they were released because they didn't mount as a USB Mass Storage Device like previous iPods.  ref: [http://gtkpod.wikispaces.com/Supported+iPods](http://gtkpod.wikispaces.com/Supported+iPods).  The amarok wiki doesn't paint such a pretty picture, however: [http://amarok.kde.org/wiki/Media_Device:IPod#iPod_Touch_and_iPhone](http://amarok.kde.org/wiki/Media_Device:IPod#iPod_Touch_and_iPhone)

---

### Post by zim2dive on 2009-01-20
gtkpod appears to play music via xmms... except we don't have xmms as a package to install, you can edit the tools menu to switch it to xmms2.. altho I'm only just puzzling out the xmms2 syntax (I can add a song to the playlist and get it to play, but can't quite puzzle out how to skip that step and play directly...)

I don't see how to load up an existing iTunes XML file.

I also tried Songbird.  It has a import function for iTunes XML and actually appears that it might check each time it launches... BUT it doesn't seem smart enough to reconcile a root path difference .. argh.. so close and still not there.

So I manually creating the same path structure under Intrepid and made a symlink for the level to my $HOME/Music folder on my Mac, mounted over sshfs (for the moment anyway).

Now under Songbird go to Tools->Options->Media Importer and you can do an import.

I got 2935 out of my 2988 songs.. and several(all?) of my "dumb" playlists.. none of my "smart" playlists.

EDIT: I'm using the most recent songbird 1.1 nightly in case it matters

---

