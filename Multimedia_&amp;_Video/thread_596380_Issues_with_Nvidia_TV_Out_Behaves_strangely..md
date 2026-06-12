---
title: "Issues with Nvidia: TV Out Behaves strangely."
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by mao42ranma on 2007-10-29
While using an Nvidia 6800 GS (PNY OC), I was trying to figure out how I wanted to run dual screen to work with my TV, and eventually settled on running two different X screens, since I was only using the TV for playing movies, slideshows, and fullscreen games. Getting the X screens set up wasn't any problem, however Compiz wouldn't work properly across two X screens, causing interface lag on one screen while the other would behave fine, and while looking around I found someone with a similar problem who wrote a script to run Compiz with --current-session-only (I forget the exact name of the option) on both screens with no issues. However, I found I had a separate problem after fixing Compiz, and I'll do my best to detail it below, as I've never even heard of this issue or seen it before.

Basically, any fast animation like that of a game or movie, or Compiz's wobbly windows exposes a very obvious screen tear that crawls slowly down the screen. It's not like normal screen tearing where the graphics aren't sync'd properly to the refresh and creates tearing across the whole image. Above and below the tear, the animation is sync'd fine and animates with no frame dropping. The tear starts from the top of the screen, and moves down the television, taking about two to three seconds to make it's way down and start again from the top. This occurs even with TwinView and cloned screens, with Compiz turned on or off, and with video and OpenGL. It -doesn't- occur if I have -only- the TV enabled, or only the LCD enabled, only when both are.

I have been unable to find any other case of this issue on any forum relating to the mentioned hardware and software, or with any search engine.

The problem has been difficult to troubleshoot. Under Vista (uhg), I am unable to reproduce the issue at any level. The only thing I've been able to figure out is that, under the Vista drivers and utility, the card reports a refresh rate of 29hz on the TV, while under Ubuntu, the Nvidia settings manager reports a full 60hz.

Has anyone heard of this kind of problem, or experienced it? It seems so obscure to me that it might not be solvable.

A side note, the ATI card I had in it a day previous didn't show the tearing on either screen. I decided to swap cards with my friend since he has a XP machine, since I was having issues with the ATI card on Ubuntu (the same that everyone with an ATI card has).

---

