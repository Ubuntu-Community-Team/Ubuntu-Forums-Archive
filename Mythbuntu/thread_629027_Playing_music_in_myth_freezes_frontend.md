---
title: "Playing music in myth freezes frontend"
date: 2007-12-01
forum: Mythbuntu
---

### Post by Saint Nocturnal on 2007-12-01
Hi all! Usually a lurker but I came across this problem I can't seem to find a fix for anywhere.

I'm running Mythbuntu 7.10 64-bit on an AMD64 3700. I'm running my audio over S/PDIF to a Bose 321. In MythTV, this works perfect for DVD's and playing the online streaming music option. However when I try to play a normal mp3 through the MythTV music option, the frontend freezes when I hit the P key to play. Nothing in the frontend responds after that and I have to kill it but alt+tabbing to terminal and using xkill. Playing the same mp3's with VLC/Mplayer works fine outside of the frontend.

I've tried playing the file both from the default location of /var/lib/mythtv/music and also thinking maybe it was a root access thing, tried playing it from a folder under my home directory. Either way ends in tragedy :\ Also uninstalling/reinstalling the mythmusic plugin didn't help.

Hopefully that's enough info. Any ideas guys?

---

### Post by uopjohnson on 2007-12-03
Have to checked to see if it is a problem with a specific mp3.  Does it always fail on the same track?  What happened if you delete that one file?  Are you logging frontened events tot the DB?  There is a checkbox for that in General options that may give you a clue.  You could also start the frontend from the terminal and then you would be able to see any errors on the terminal when it failed.

---

