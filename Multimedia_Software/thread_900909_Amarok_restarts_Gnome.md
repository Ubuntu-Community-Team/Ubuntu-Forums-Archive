---
title: "Amarok restarts Gnome"
date: 2008-08-25
forum: Multimedia Software
---

### Post by DGambrinus on 2008-08-25
I have been using Amarok as my media player for months now and it has been performing flawlessly but today it started doing something odd. I fired it up and everything was cool. I have mine configure to only show the small player window instead of the playlist window. I clicked on the "PL" button in order to show the playlist window and my Gnome session was immediately restarted. All subsequent attempts have done the exact same thing.

What I am running:
Running Ubuntu 8.04 Hardy Heron
Amarok 1.4 (According to the splash screen)

Anyone got anything that may help me figure this out?

Thanks.


[EDIT]
I just found out some more info. If I right click on a media (mp3) file and "Open With" Amarok the file plays and Amarok gives me the playlist screen when I click on the "PL" button. I haven't restarted and tried from scratch yet because I am going to bed. I will update the thread tomorrow...

---

### Post by DGambrinus on 2008-09-04
I played with Amarok a bit and noticed more things that weren't working. I couldn't load playlists. I figured that it must be a DB issue so I whacked the database tables and let Amarok rebuild them. (I'm using MySQL) After the database tables were rebuilt and my collection had been rescanned everything worked fine and has been just fine now for over a week.

The only downside was that whacking the DB killed my Podcasts and streaming radio stations that I had.

---

