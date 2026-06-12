---
title: "[SOLVED] After updates broke LiveTV and Video playback, what now? Also Music Player p"
date: 2008-03-15
forum: Mythbuntu
---

### Post by freymann on 2008-03-15
I guess I don't have the best timing in the world.

I just started on my MythTV setup yesterday. I have 3 machines.

Master backend/frontend in the basement
Secondary backend/frontend upstairs living room
Frontend in master bedroom

Yesterday I had most things working (including LiveTV and watching videos)

I had all the machines do their updates overnight, so now I'm at the newest version of MythBuntu.

And now none of the machines will display LiveTV or video. If I didn't get everything working yesterday before the updates I would be sitting here wondering why I bothered with MythBuntu.

How long till there's a fix? Is this normal to break it so badly?

I have issues with the Music Player as well.

On the Master backend/frontend, when you edit the playlist and tick off a few things, when you get back to the play screen there's at least 5 duplicated lines of the same item? when it starts playing music, then I lose all interaction with the system and I have to CTRL-ALT-BACKSPACE, log in, go back to music, exit and tell it to stop playing music.

On the secondary backend/frontend upstairs, when I try to play music I just get:

```

2008-03-15 12:05:54.677 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu/music-ui.xml
2008-03-15 12:06:06.296 Opening audio device 'default'. ch 2(2) sr 44100
2008-03-15 12:06:06.296 Opening ALSA audio device 'default'.
2008-03-15 12:06:06.392 Mixer unable to find control Master
2008-03-15 12:06:06.392 Mixer unable to find control Master
2008-03-15 12:06:06.701 Decoder error. DecoderMAD: Failed to open input.  Error 5.
2008-03-15 12:06:16.531 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu/music-ui.xml
2008-03-15 12:06:57.966 Decoder error. DecoderMAD: Failed to open input.  Error 5.
2008-03-15 12:07:09.002 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu/status-ui.xml
2008-03-15 12:08:01.105 MythThemedMenuPrivate: Unknown tag image in background

```

I dunno if this is related to the latest version or not.

Any suggestions? I actually have all afternoon and evening to sit back and enjoy the system and now I can't :-(

---

### Post by murbanci on 2008-03-15
Your problem with the video is probably because mythvideo doesnt update on its own for some reason.  I had to open package manager and mark mythvideo for upgrade and then it would uninstall mythdvd and upgrade mythvideo and your videos should work fine.  I dont use the music player so im no help there.  Hope this helps a little.

---

