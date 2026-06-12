---
title: "Remote jukebox"
date: 2009-12-20
forum: Multimedia Software
---

### Post by Tulth on 2009-12-20
I recently setup a headless (no monitor, etc) server on one of those mini-itx atom platforms.  I'm running ubuntu 9.10 i386 on it.  

I'm looking for software to use this server as a remote stereo/jukebox.  I plan to connect speakers up to this server, and I want to remotely control what the server is playing via a web interface.  

I looked at Jinzora but it only seems to stream music to play on the client not the server.

Can anyone here point me in the right direction?

Thanks!

---

### Post by Tulth on 2009-12-20
Self update:
[This thread]("http://ubuntuforums.org/showthread.php?t=1107284") has some info.

Looks like Jinzora's Jukebox MPD mode should work.  I went and apt-get installed mpd.

now lsof -i -nP shows these entries for mpd:
mpd       8328      mpd    4u  IPv6  46345      0t0  TCP [::1]:6600 (LISTEN)
mpd       8328      mpd    7u  IPv4  46347      0t0  TCP 127.0.0.1:6600 (LISTEN)
mpd       8328      mpd   13u  IPv6  46395      0t0  TCP [::1]:45729->[::1]:6010 (CLOSE_WAIT)
mpd       8328      mpd   16u  IPv6  46544      0t0  TCP [::1]:45738->[::1]:6010 (CLOSE_WAIT)

so it looks like its running.

I set jinzora to use an mpd jukebox, but so far the jukebox stays empty.  I'm probably missing something simple.

---

### Post by Tulth on 2010-01-03
well I figured out my problem.

With the desktop install, sound doesn't work until I'm logged into the gui.  So for my headless install, I have to VNC in, then MPD actually works.

Now once I am logged in MPD works with jinzora, but I found I actually liked the GMPC program better.

The setup is pretty sweet now, I have some good speakers hooked to my server box, and I can control them from my Ubuntu desktop, and so can my girlfriend from her windows XP64 machine.

---

### Post by bcdudley on 2010-06-10
I know this is several months old, but if you are still looking, check out calliope. I am running that on my 9.04 server and it is great. It does take quite a bit of work to get it installed, but it is worth it once you get it going.

---

### Post by chiques on 2010-06-20
What about simply remote logging in to Ubuntu and controlling Amarok from that interface?

---

