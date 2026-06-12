---
title: "Video display saturates with false color"
date: 2009-04-22
forum: Multimedia Software
---

### Post by bart1452 on 2009-04-22
I've searched for something like this and haven't found it yet. My Compaq Presario 700Z laptop with Hardy 8.04 has been having problems with the color starting to saturate with green and giving a false color appearance. The effect comes and goes for no apparent reason. It effects the wall paper, photos, and videos, window frames, and even the print. It seemed to get a little worse after accepting 2 updates for a 686 kernel. I'm running 32 bit and don't really understand why that would have been in the update manager, but I'm wondering if there is a connection.

The problem happens during boot-up when the loading screen appears, or the screen could be normal during boot-up, and it could come and go away during a computer session. I can shut it down when the problem is there and it will likely be there when I restart the computer. It looks almost like when you push the color and contrast settings too far and get false colors, but it's always green. It makes every other line in the email address book look green.  I checked Xorg in the system log and found that it spends about 100 steps trying to figure out the screen settings during boot up. It seems like a bug in the video driver.

At the moment it looks OK, but a half hour ago it looked like it was going to be hard to see everything. Is there a setting I need to change a value on?

Dave

---

