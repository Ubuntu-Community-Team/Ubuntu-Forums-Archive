---
title: "Run myth on a second monitor windowed?"
date: 2014-02-26
forum: Mythbuntu
---

### Post by sdowney717 on 2014-02-26
Idea is keep ubuntu desktop on one monitor
run myth on the tv hooked to the same PC.

How can I do that?

or is there a program that can do that, stay running over there showing up on the TV?

can myth play wtv files recorded in windows7 wmc and play them over the LAN?

---

### Post by sdowney717 on 2014-02-26
yes, you can.
program is mythtv

To run windowed use

mythfrontend -w --geometry 1024x768

then drag window to TV screen.

but you need to setup mythbackend first
with the videos folder etc...

I just set mine up using video files on a second drive in another folder. If you have videos set for root of the drive, then every file will get a scan, not good.
So set the videos in a subfolder in the drive.

/media/username/drivenamenumber/movies folder

for me it is

/media/scott/0C3655E6635050E4/movies

if you add movies, you might have to rescan, not sure yet.
Rescan takes a while, mythtv pulls in album art, and if you have lot of movies can take a long time.

---

