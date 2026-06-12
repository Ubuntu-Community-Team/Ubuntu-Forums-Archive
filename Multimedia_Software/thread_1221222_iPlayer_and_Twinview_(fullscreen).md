---
title: "iPlayer and Twinview (fullscreen)"
date: 2009-07-23
forum: Multimedia Software
---

### Post by djhworld on 2009-07-23
Having trouble here trying to get the web streaming iPlayer service to display in full screen on my second monitor. 

I have TwinView setup fine, it's just when dragging an instance of Firefox over to the second monitor, maximising then attempting to watch a programme on the iPlayer in "fullscreen" mode - the video pops over to my normal monitor and plays on that instead.

Is there any way of forcing it to play on my second monitor?

---

### Post by SteveDee on 2009-07-24
> **djhworld said:**
> Having trouble here trying to get the web streaming iPlayer service to display in full screen on my second monitor. 

I have TwinView setup fine, it's just when dragging an instance of Firefox over to the second monitor, maximising then attempting to watch a programme on the iPlayer in "fullscreen" mode - the video pops over to my normal monitor and plays on that instead.

Is there any way of forcing it to play on my second monitor?

I don't like using TwinView (i.e. a desktop stretched over 2 monitors) for this kind of application because an app running on one screen tends to launch dialog boxes on the other screen.

To keep your Firefox/video app running entirely on your second monitor/TV it would be better to configure your system for Separate X Windows. This will give you 2 independent screens.

You can then run Firefox on the second screen by using the command (in a terminal or in a launcher):-
 firefox --display=:0.1

You can also play movies on your second display:-
 mplayer "filename" -fs -display :0.1

The display numbering assumes you are the initial user. If a second or third user (i.e. additional users logged on via the switch user feature) the display numbering changes as follows:-
2nd user; display=:20.1
3rd user; display=:21.1 & so on.

I hope this helps.

---

