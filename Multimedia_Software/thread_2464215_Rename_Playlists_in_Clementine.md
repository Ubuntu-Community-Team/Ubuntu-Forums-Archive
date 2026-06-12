---
title: "Rename Playlists in Clementine?"
date: 2021-06-26
forum: Multimedia Software
---

### Post by Deanimator on 2021-06-26
I just built a media player/music file server from a recently retired desktop.  After being dissatisfied with Rhythmbox, I found Clementine, which overall I find quite good, although not quite on the level of Winamp.

One issue I've run into is an inability to rename playlists.  There seems to be a known bug, but the issues I've seen transcend what I've seen.

At first, Clementine wouldn't let me rename a playlist at all.  Then it would only let me put in a single character for the name, then wouldn't even let me change that.

Any clues as to whether there's a fix for this?

Thanks.

---

### Post by coffeecat on 2021-06-26
Support, not chat. *Thread moved to **Multimedia Software**.*

Renaming playlists works for me in Clementine by right-clicking on the playlist tab and selecting rename playlist.

---

### Post by Deanimator on 2021-06-26
> **coffeecat said:**
> Support, not chat. *Thread moved to **Multimedia Software**.*

Renaming playlists works for me in Clementine by right-clicking on the playlist tab and selecting rename playlist.

That most definitely does not work for me, as described.

Could it have something to do with permissions?

While my music is in a Samba share on the PC, the playlists are saved in my music folder.

After posting, I discovered that I could rename the playlists by exiting Clementine and manually renaming them in the file utility.

---

### Post by Holger_Gehrke on 2021-06-27
> **Deanimator said:**
> 
After posting, I discovered that I could rename the playlists by exiting Clementine and manually renaming them in the file utility.

And that genuinely surprises me. Clementine doesn't use files for playlists, it has a sqlite database in ~/.config/Clementine/clementine.db in which it stores everything except for the queries for generating "smart" play lists (those are stored in the configuration ~/.config/Clementine/Clementine.conf). If you have a play list in one of the many supported formats you can import it, but it should end up in the database and changing the filename after importing should not even get noticed.

The only player I know of the top of my head that behaves like you describe would be audacious.

Holger

---

### Post by Deanimator on 2021-06-27
> **Holger_Gehrke said:**
> And that genuinely surprises me. Clementine doesn't use files for playlists, it has a sqlite database in ~/.config/Clementine/clementine.db in which it stores everything except for the queries for generating "smart" play lists (those are stored in the configuration ~/.config/Clementine/Clementine.conf). If you have a play list in one of the many supported formats you can import it, but it should end up in the database and changing the filename after importing should not even get noticed.

The only player I know of the top of my head that behaves like you describe would be audacious.

Holger

I have no idea.

One of the options is to save the playlist.  When I attempt this, it gives an automatically numbered playlist which I cannot rename in the program.  If I save the playlist to the hard drive, I can kill Clementine and manually rename it in the O/S.  Playing around with file permissions has no effect.

I'm totally new to Clementine, so I can't explain any of this.  I did see a bug report where people couldn't rename the playlists.

Another possible issue is that for the most part, I've been running Clementine over SSH and VNC from a Windows laptop and an Android tablet.  One thing I noticed today while trying to get VLC media player running remotely was that I couldn't make certain changes over VNC, but could make them from the local desktop.  I wonder if this also affects Clementine over VNC.  I've got the Android remote for Clementine running, which is much better than VNC, at least from Android.

---

### Post by Deanimator on 2021-07-05
The problem is apparently trying to perform the operation over VNC.  I had not wanted to, but for a different reason, I ended up leaving a keyboard and mouse attached to the music server/player.  If I create a playlist at the primary desktop, I am able to rename it immediately.  Only a minor annoyance.

---

### Post by Holger_Gehrke on 2021-07-06
This might be due to the client, the server or the Desktop Environment used in the VNC session. Using the server from the package vnc4server on my XUbuntu 18.04 and the vncviewer from the package realvnc-vnc-viewer on RasberryPi OS (aka Rasbian) with a simple OpenBox session in vnc I can access the context menu of a tab in clementine to rename a playlist without any problems.

Holger

---

### Post by Deanimator on 2021-07-07
> **Holger_Gehrke said:**
> This might be due to the client, the server or the Desktop Environment used in the VNC session. Using the server from the package vnc4server on my XUbuntu 18.04 and the vncviewer from the package realvnc-vnc-viewer on RasberryPi OS (aka Rasbian) with a simple OpenBox session in vnc I can access the context menu of a tab in clementine to rename a playlist without any problems.

Holger

I'm using TightVNC on both ends.  I'm using xfce for the VNC session, while the local desktop is the default 20.04 desktop (LightDM?).  I'm connecting from a Windows 10 laptop wirelessly.  I'm using xfce because that's what worked to get VNC to work.  Otherwise, I got the typical gray screen that people always complain about.

---

