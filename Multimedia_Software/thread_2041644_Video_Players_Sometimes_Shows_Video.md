---
title: "Video Players Sometimes Shows Video"
date: 2012-08-13
forum: Multimedia Software
---

### Post by Shadius on 2012-08-13
Hey everybody! :)

Sometimes Movie Player and VLC Player will play videos and sometimes they won't. I restarted the computer to see if it would fix the issue and it did. That's great, but I would like to know what to do besides restarting the computer in case this issue comes up again. I don't want to be restarting the computer everytime I try to play a video using Movie Player or VLC Player. Also, I'd like to know how to clear the history in Movie Player. 

Thanks for the help.

---

### Post by mc4man on 2012-08-13
Totem gets it's it's history from ~/.local/share/recently-used.xbel, parsing out the last 5 from "<bookmark:group>Totem</bookmark:group>"

A lot of other 'histories' are stored there so generally not a great idea to delete the file itself. Editing out the individual totem entries would be quite a pita & not worth doing.

As far as sporadic playback issue try to produce an error message, either run vlc in a terminal with the -vv option or you can set vlc up to log messages to a text file

Otherwise when this happens ck. the tail end of ~/xsession-errors, may have something useful

---

### Post by Shadius on 2012-08-13
> **mc4man said:**
> Totem gets it's it's history from ~/.local/share/recently-used.xbel, parsing out the last 5 from "<bookmark:group>Totem</bookmark:group>"

A lot of other 'histories' are stored there so generally not a great idea to delete the file itself. Editing out the individual totem entries would be quite a pita & not worth doing.

As far as sporadic playback issue try to produce an error message, either run vlc in a terminal with the -vv option or you can set vlc up to log messages to a text file

Otherwise when this happens ck. the tail end of ~/xsession-errors, may have something useful

Okay, I'm a beginner when it comes to using the Terminal. Could you walk me through on trying to produce an error message with VLC or Movie Player and checking the tail end of ~/xsession-errors (don't really know what this means). :(

---

### Post by mc4man on 2012-08-13
Well - 
if you open your home folder & go ctrl+h it will show hidden files.
Scroll down to the bottom to find .xsession-errors. You can open it in a text editor.
No sense doing so until a vid won't play, then ck. it out (tail end means look near the end of the file.

If you open a terminal & go 
```
vlc -vv
```
vlc will produce debug info. Then just open your vid, if it won't play then ck. back in the terminal (don't close vlc or it will add alot more lines of info.
 vlc -vv does produce a lot of output so it may be easier to set up logging to text file, I could do that here tomorrow, (if some one else doesn't), as it's a bit late here

As far as totem - start from terminal with 
```
totem --debug
```
It will produce almost nothing but if the vid fails something may show up in the terminal

---

### Post by Shadius on 2012-08-13
> **mc4man said:**
> Well - 
if you open your home folder & go ctrl+h it will show hidden files.
Scroll down to the bottom to find .xsession-errors. You can open it in a text editor.
No sense doing so until a vid won't play, then ck. it out (tail end means look near the end of the file.

If you open a terminal & go 
```
vlc -vv
```
vlc will produce debug info. Then just open your vid, if it won't play then ck. back in the terminal (don't close vlc or it will add alot more lines of info.
 vlc -vv does produce a lot of output so it may be easier to set up logging to text file, I could do that here tomorrow, (if some one else doesn't), as it's a bit late here

As far as totem - start from terminal with 
```
totem --debug
```
It will produce almost nothing but if the vid fails something may show up in the terminal

Okay, let's continue this tomorrow since it's after 3 AM here. Thank you for your help so far.

---

