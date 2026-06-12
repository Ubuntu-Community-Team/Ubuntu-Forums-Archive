---
title: "Remote Issues"
date: 2015-09-14
forum: Mythbuntu
---

### Post by jlp_engineer on 2015-09-14
I have just purchased a few of the Adesso ARC-1100 (Ortek VRC-1100).  I followed the instructions on the wiki, and got one to work.  Now I have tried to get the second one working on a nearly identical system, and it has my scratching my head.  When I try the step using IRW...that works.  I can see all the codes printed on the screen.   But when I go into Myth, the remote does not do what I put into ~/.lirc/mythtv, it just acts like a keyboard and mouse.   This one has me stumped.  I was hoping someone could give me some troubleshooting hints so I would know where to look for the error I must have made somewhere in the process.

Here is ~/.lircrc:

```
include ~/.lirc/mythtv
include ~/.lirc/mplayer
include ~/.lirc/xine
include ~/.lirc/vlc
include ~/.lirc/xmame
include ~/.lirc/xmess
include ~/.lirc/totem
include ~/.lirc/elisa

```

Here is my ~/.lirc/mythtv

```
begin
   remote = devinput
   prog = mythtv
   button = KEY_KP0
   config = 0
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_KP1
   config = 1
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_KP2
   config = 2
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_KP3
   config = 3
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_KP4
   config = 4
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_KP5
   config = 5
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_KP6
   config = 6
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_KP7
   config = 7
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_KP8
   config = 8
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_KP9
   config = 9
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_BACKSPACE
   config = Backspace
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_BACKSPACE
   config = Escape
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_PAGEDOWN
   config = Down
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_PAGEUP
   config = Up
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_DOWN
   config = Down
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_ENTER
   config = Return
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_ESC
   config = Escape
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_F
   config = >
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_NEXTSONG
   config = N
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_HOMEPAGE
   config = M
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_LEFT
   config = Left
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_META
   config = M
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_MUTE
   config = |
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_PLAYPAUSE
   config = P
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_R
   config = R
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_B
   config = <
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_RIGHT
   config = Right
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_STOPCD
   config = S
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_UP
   config = Up
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_VOLUMEDOWN
   config = [
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_VOLUMEUP
   config = ]
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_PREVIOUSSONG
   config = B
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_O
   config = Q
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_T
   config = Z
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_M
   config = F
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_I
   config = Y
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_E
   config = T
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_SLEEP
   config = U
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_KPASTERISK
   config = O
   repeat = 0
   delay = 0
end

begin
   remote = devinput
   prog = mythtv
   button = KEY_G
   config = S
   repeat = 0
   delay = 0
end
```

Let me know if there are any other files that I need to post here.

Thanks for any suggestions.

---

### Post by vidtek on 2015-10-05
JLP-

The kernels from about a year ago incorporated infra-red support, which is why your remote is acting like a keyboard.  I suspect that your direction keys work but not the select key - right?

If you are using lirc you need to disable in-kernel support first.

There are heaps of forum discussions on this and how to do it just google it. 

Tony

---

