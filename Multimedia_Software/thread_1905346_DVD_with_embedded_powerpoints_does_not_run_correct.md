---
title: "DVD with embedded powerpoints does not run correctly."
date: 2012-01-06
forum: Multimedia Software
---

### Post by dreamquartz on 2012-01-06
[FONT=Verdana][SIZE=2]Received a DVD (vob-format files) which includes powerpoint slides with embedded video links.

When this DVD is played in a DVD player, linked to a TV, it runs.[/SIZE][/FONT][FONT=Verdana][SIZE=2]
To move to the next slide, you have to push start again, because the moment a slide is shown, the DVD pauses.

Some slides do hold a link to a video snippet.[/SIZE][/FONT][FONT=Verdana][SIZE=2]
The snippet is played when you push start. When the video is finished, you can move on to the next slide via the play button.

The DVD runs under Windows 7 Pro with Media Player 12, but is slower to respond to commands. To move to the next slide you use the forward button.[/SIZE][/FONT][FONT=Verdana][SIZE=2]
Sometimes is does and sometimes it does not play a linked video.

When running the DVD with Movie Player, SMPlayer, VLC, or GNOME MPlayer, the controls are working rarely, meaning that with e.g. Movie Player I am able to skip to the next slide, but there is no way of starting a video snippet.[/SIZE][/FONT][FONT=Verdana][SIZE=2]
With VLC even, there is no control what so ever to move forward a slide, or even start a video.

I did download the following:[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
[LIST=1]
[*]     [FONT=Verdana][SIZE=2]sudo apt-get install     libdvdread4[/SIZE][/FONT]
[*]     [FONT=Verdana][SIZE=2]sudo     /usr/share/doc/libdvdread4/install-css.sh[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]Mediabuntu repositories[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]sudo apt-get install     ubuntu-restricted-extras[/SIZE][/FONT]
[/LIST]
[FONT=Verdana][SIZE=2]Right now I am ripping the DVD via DVD::RIP to see if I can do something with it that way.

Couple of questions:[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
[LIST=1]
[*][FONT=Verdana][SIZE=2]I am trying to figure out what kind of software, likely under Windows, can create such kind of videos?[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]Is there a way that this type of video can be played?[/SIZE][/FONT]
[/LIST]
[FONT=Verdana][SIZE=2]

Thx,[/SIZE][/FONT][FONT=Verdana][SIZE=2]


Dream[/SIZE][/FONT]

---

### Post by Mark Phelps on 2012-01-07
It probably works in Win7 because you have MS Office installed there.

It's most likely NOT going to work in Ubuntu -- for the same reason.  You do NOT have MS Office installed and working.

---

### Post by dreamquartz on 2012-03-31
I know what you're saying, but there are so many different players available under Ubuntu, you could think that a DVD, which contains vob files, should run.

The problem is the menus that are part of the "movies".
The files contain PowerPoint slides with menu-functions and buttons, converted to vob-files, which can be operated and do function under Windows, but do not function correctly using any of the movie players under Ubuntu.

So I am at a loss.

Dream

---

### Post by dreamquartz on 2012-07-07
There is no more requirement to use the DVD, therefore the question became obsolete.

Dream

---

