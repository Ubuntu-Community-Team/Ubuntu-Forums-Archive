---
title: "Colors Are Washed Out"
date: 2011-04-22
forum: Multimedia Software
---

### Post by crankin on 2011-04-22
Hey guys. My colors are washed out when trying to record screencast. It doesn't matter what program I'm using. I've tried recording with ffmpeg, xvidcap, and gtk-recordmydesktop. They all the videos come out the same. The text is sharp enough it's just the colors are washed out. 

So research says it's compiz or gnmoe so I've disabled compiz switched to xfce doesn't matter same results. Still washed out. Any idea what it could be? I've messed with every setting imaginable. I don't know what else to try. 

I'm attaching a screenshot of my desktop so you can see what I'm talking about. To the left is what the page should look like. And to the right is the video playing in Movie Player. Notice how washed out the colors are. I'm lost.

---

### Post by crankin on 2011-04-23
Ok so I figured out what it was. I did a screencast from my Windows VM which looked fine in Windows Media Player so I copied to my Ubuntu machine to watch it and still Color is washed out. So LIGHTBULB it's gotta be the player. I looked into View>Preferences under the display tab. Reset Color Balance to defaults and BOOM everything looks beautiful. If you even spent 2 seconds thinking about an answer for this post. Thank you.

---

