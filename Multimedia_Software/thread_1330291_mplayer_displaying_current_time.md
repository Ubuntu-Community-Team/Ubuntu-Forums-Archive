---
title: "mplayer displaying current time"
date: 2009-11-18
forum: Multimedia Software
---

### Post by Matkyne on 2009-11-18
I am neither a Linux Guru nor a Noob, I have 7 computers in my home and only one runs Windows.  I am accustomed to searching Google for hours and looking through forums to find my answers; and I have done so to no avail. Here is the problem I am having. 

For some reason when I play a video with mplayer, the OSD displays the current system time (not play time or time remaining) in the upper right hand corner. I press "O" to cycle through all the available OSD options, but the time remains there. I have looked in the system wide config file (/etc/mplayer/...) and the user config file (/~/.mplayer/...) and could not find any option to disable the time. (setting the OSD to show nothing did not fix the problem). I have completely read the MAN page for mplayer and read the complete list of options listed on the mplayer website ([http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html)). and just cant seem to figure this one out.  One of the many reasons I prefer Linux is the ability to customize anything the way I want it.  This is driving me batty. I know the solution will be as simple as inserting a "#" somewhere, but where?

Any help would be appreciated.

---

### Post by laceration on 2009-11-18
As far as I know MPlayer has neither a native way to display system time or a way to display something in the upper right hand corner w/o a lot of tweaking.  I am thinking you have a clock app that is set to stay on top and is obscured by your regular background.

---

### Post by andrew.46 on 2009-11-18
Hi Matkyne,

> **Matkyne said:**
> For some reason when I play a video with mplayer, the OSD displays the current system time (not play time or time remaining) in the upper right hand corner. 

Sounds very odd :). Can you take a screenshot of this?

Andrew

---

### Post by Matkyne on 2009-11-18
I have never had this happen with mplayer before. I tried to take some screen shots, but the images came out blank, or black to be exact. So I used the old digital camera.  I took different shots with different aspect ratios, and both full screen and windowed. The time is always there. And it is rendered with the same font that mplayer uses for OSD. I can't figure it out. 
[IMG]http://i83.photobucket.com/albums/j302/matkyne/Mods/IMG_2138.jpg[/IMG][IMG]http://i83.photobucket.com/albums/j302/matkyne/Mods/IMG_2139.jpg[/IMG]
[IMG]http://i83.photobucket.com/albums/j302/matkyne/Mods/IMG_2137.jpg[/IMG]

[IMG]http://i83.photobucket.com/albums/j302/matkyne/Mods/IMG_2136.jpg[/IMG]

---

### Post by andrew.46 on 2009-11-19
Hi Matkyne,

Very interesting :). If it is a product of the OSD the settings should be found in either etc/menu.conf or $HOME/.mplayer/menu.conf although I note rom your original post you have already had a look there. Could you post the contents of these anyway? I confess I have not really used the OSD Menu interface much but it should hopefully be not too difficult to spot the relevant setting...

Andrew

---

### Post by Matkyne on 2009-11-19
[Solved!]

Ok, I went back and looked in /etc/mplayer/mplayer.conf and found a line that reads:

"osdc=1"

and I thought to myself: "Self, what does osdc stand for?"

I assumed it stood for On Screen Display Clock. So I commented it out (by adding a # in front of the line), saved the file and fired up mplayer again and lo and behold it was gone. 

Thanks for all the help.:KS

Just FYI and to help other people who might have the same problem. This was a custom version of mplayer that was bundled in the ubuntu package for the Smart Q7 Internet Tablet.

---

### Post by Jose Catre-Vandis on 2009-11-19
I may well be adding that to my config file :) Is there likely to be a toggle keyboard button for this?

---

### Post by laceration on 2009-11-19
> I may well be adding that to my config file  Is there likely to be a toggle keyboard button for this?
I tried it, since I have been deep in the bowels of the MPlayer OSD system and have never seen this--it didn't work.  It looks to be only in the weirdo tablet version of MPlayer that OP has.
My MPlayer tweak(OSTV) displays the time when I push a certain remote button or key.  It does it by running a little date script and piping the output to MPlayer.

---

### Post by Jose Catre-Vandis on 2009-11-21
> **laceration said:**
> I tried it, since I have been deep in the bowels of the MPlayer OSD system and have never seen this--it didn't work.  It looks to be only in the weirdo tablet version of MPlayer that OP has.
My MPlayer tweak(OSTV) displays the time when I push a certain remote button or key.  It does it by running a little date script and piping the output to MPlayer.

Shame :)

---

