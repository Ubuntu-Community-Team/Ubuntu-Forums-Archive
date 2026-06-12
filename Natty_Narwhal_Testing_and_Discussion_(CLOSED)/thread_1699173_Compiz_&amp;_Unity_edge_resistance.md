---
title: "Compiz &amp; Unity edge resistance"
date: 2011-03-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by taavikko on 2011-03-03
Evening to all,

Anyone else noticing that when draggind window to edges it snaps and resists few pixels too soon, leaving a cap to edge.
Rather than fully snapping at the real edge of screen.

x86_64 and nvidia-current, fully updated system.

---

### Post by MacUntu on 2011-03-03
All windows, or just something like gnome-terminal?

---

### Post by taavikko on 2011-03-03
> **MacUntu said:**
> All windows, or just something like gnome-terminal?

All of which I've used.

If I move ex. gnome-terminal by grabbing the title and using the snap feature the window is correctly placed at edge.

Otherwise it just resists few pixels too soon.

---

### Post by Quackers on 2011-03-03
I thought I was seeing this a couple of days ago, but it seems to have disappeared for me. I've been trying to replicate it, but I can't.

---

### Post by MacUntu on 2011-03-03
The gnome-terminal won't work for everyone as it's only resizable in fix-sized steps. Else, I haven't seen this (after they fixed the resize margin issue).

---

### Post by taavikko on 2011-03-03
> **MacUntu said:**
> The gnome-terminal won't work for everyone as it's only resizable in fix-sized steps. Else, I haven't seen this (after they fixed the resize margin issue).

I made a short video that explains ( at least I hope so)
[http://www.youtube.com/watch?v=RtWPTpX4KEY](http://www.youtube.com/watch?v=RtWPTpX4KEY)

The gnome-terminal is at correct position for me, Trying to drag the nautilus window, it resists few pixels too soon. See the cap between the edge and compare it to gnome-terminal.

For the resizing option I have no opinion, cause not really using it.

---

### Post by mc4man on 2011-03-03
myself disable the plugin, but your video looks you have edge attraction enabled

---

### Post by taavikko on 2011-03-03
> **mc4man said:**
> myself disable the plugin, but your video looks you have edge attraction enabled

The plugin is enabled by default, that's why I whine about it :)
The thing used to work correctly in the previous versions of compiz and Ubuntu.

---

### Post by kyleabaker on 2011-03-03
> **taavikko said:**
> Evening to all,

Anyone else noticing that when draggind window to edges it snaps and resists few pixels too soon, leaving a cap to edge.
Rather than fully snapping at the real edge of screen.

x86_64 and nvidia-current, fully updated system.

I tried explaining that [a while back]("http://ubuntuforums.org/showthread.php?t=1611490&page=22#post10416804") and no one seemed to understand me. Its caused by the way they handle the grips to resize windows now with Compiz. :/

---

### Post by MacUntu on 2011-03-04
> **taavikko said:**
> I made a short video that explains ( at least I hope so)
[http://www.youtube.com/watch?v=RtWPTpX4KEY](http://www.youtube.com/watch?v=RtWPTpX4KEY)

Aaaah! I had the grid plugin in mind, but that's something different then.

I'm getting the same, sounds like a bug to me (the grid plugin doesn't care about this resize padding anymore, maybe it's fixable in this case too).

---

### Post by mc4man on 2011-03-04
Taking another look at the snap plugin here - 
The only time it 'snaps' to the screen edge here is with the 'edge attraction' option enabled. (and works fine - A3 fresh
And the only time snap works at all is when the 'grid' plugin is disabled, otherwise no effect whatsoever.
(nvidia cards

---

