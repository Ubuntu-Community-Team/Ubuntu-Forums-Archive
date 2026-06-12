---
title: "Trying to Play a movie DVD - my experience"
date: 2008-09-11
forum: Multimedia Software
---

### Post by selahlynch on 2008-09-11
I installed Ubuntu 8.04 Hardy Heron with a Gnome desktop on my Gateway laptop.

Then I tried to play a DVD from the USA. (House MD Season 3 :) )


Problems Decoding DVD:

When I inserted my DVD the computer recognised it as 'House', Totem Movie Player opened automatically, but I got a message "An error occurred, Could not read from resource."

This was because I needed to install some packages to decode my dvd.

I used synaptic package manager to download and install package libdvdcss2.  Later I also installed libdvdnav4 and libdvdread3.


Problems with Totem Movie Player:

Now my dvd played in Totem, but only the first episode!  I couldn't figure out how to move to another episode.  The Playlist displayed only one entry "cdrom0".  Same problem if I open it by right clicking the DVD icon that pops up on the desktop.  

However, I opened Totem using the Applications Menu after the DVD has been inserted.  In totem I choose "Play Disk 'HOUSE'" from the Movie menu.  This time it works and it gives me a playlist with several options from which I can choose, each one a different episode.  Still no menu though.  Also, sometimes it will jump back to the first episode if I use any controls while watching a different episode.


Install Gxine:

Eventually I chose to install a different movie player, gxine, and now I use that instead of Totem.  It has menus!  I also edited my home preferences so that Ubuntu will "Do Nothing" when I insert a DVD instead of automatically starting Totem Movie Player.

---

