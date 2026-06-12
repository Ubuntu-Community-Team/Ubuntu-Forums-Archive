---
title: "Media Player(s)"
date: 2016-03-20
forum: Multimedia Software
---

### Post by manikinxvx on 2016-03-20
For quite some time I've been using Banshee to manage my music library, but I've been running into some issues and as such I'm now in the market for a new default media player. Does anyone have any recommendations for one that meets some requirements, such as: 1) has an interface similar, at best, to iTunes; 2) handles and eliminates (per user parameters) duplicate files; 3) has features of Banshee, like "Rescan Music Library" and "Fix Music Metadata"

I believe I could have gotten all of these issues resolved with Banshee, had I been able to get the Community Extensions package([https://launchpad.net/ubuntu/+source/banshee-community-extensions](https://launchpad.net/ubuntu/+source/banshee-community-extensions)) to install/work for me, but that just isn't seem like it's gonna happen and I'm not sure of the issues around that.

---

### Post by TheFu on 2016-03-21
Clementine?

I haven't seen banshee in years and haven't looked at itunes in decades (loaded quicktime and itunes was forced too and had to remove it quickly since it behaved like a virus).

---

### Post by manikinxvx on 2016-03-21
Thank you for the Clementine recommendation, TheFu. I'm just getting it set up, but if it is as it appears it does seem as though it'll work out quite well for me.

---

### Post by manikinxvx on 2016-03-21
... although, I'm not quite sold on the GUI, but that wasn't one of my primary concerns. ;)

---

### Post by TheFu on 2016-03-22
> **manikinxvx said:**
> ... although, I'm not quite sold on the GUI, but that wasn't one of my primary concerns. ;)

I haven't used clementine much the last few years either.  Generally, music is manually placed into /genre/artist/album/ directories and Plex Media Server parses the files for metadata, then makes them available on the network to any devices.  Clementine is client/server, but for me, getting the server working on all the client devices is non-trivial.  With plex, any DLNA client works, though DLNA is clunky, it is ubiquitous.

Used gnump3 for over a decade - web-server, streamer. Very lite, perl.  Then almost any player on any platform worked - like winamp. Worked fine through openvpn too, but being able to have a 64G SD card pretty much removed that need when on-the-go. Storage is cheap.

Honestly, most of the time, I just use mplayer from the shell to play a group of albums feed by a 'find' cmd.

---

### Post by Alex_Moonshine on 2016-03-22
I've used mpd in conjunction with different clients (ncmpcpp, sonata, gmpc) for a long time. It requires a bit more effort to set up than a conventional player but allows accessing music library from other computers in the network, which was huge for me. Then mpd was broken by an update (I was using Debian Sid back then) and I switched to Clementine. However, since I transitioned from Debian to Xubuntu 14.04, the library search in Clementine didn't work for me (it just freezes). I've searched for a solution, didn't find any (apparently, for some people the issue resolved itself after some time), tried Banshee and Exaile, and then settled with Deadbeef. It's a simple playlist-based player that doesn't manage library at all, but it's fine, I always manage my music library manually anyway.

---

