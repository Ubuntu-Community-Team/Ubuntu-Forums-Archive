---
title: "VLC daemon (or bg process) and VLC android remotes."
date: 2011-07-29
forum: Multimedia Software
---

### Post by MetalMusicAddict on 2011-07-29
So I'm using the [VLC Remote (beta)]("https://market.android.com/details?id=org.peterbaldwin.client.android.vlcremote") Android app. It works really nicely. I'm wondering though if there's a way to run VLC in the bg so it's on all the time *but* doesn't show a UI and exits the video but not the process once done.

I use "cvlc" when I want to stream from my MPD server. Maybe something like that?

Anyway, anyone else doing something slick like this?

---

### Post by esc1 on 2012-02-07
go to preferences, startup apps, add one called vlc.. for command, vlc -d

this will start vlc in daemon mode when the computer starts.

---

