---
title: "Graphics driver problem"
date: 2010-03-22
forum: Multimedia Software
---

### Post by theelk801 on 2010-03-22
So I recently freshly installed Karmic Koala and while it's mostly functional (the terrible sound issues from Hardy are gone, thank god), I have a bit of an issue with my video card. I'm running an Nvidia e-GeForce 7600GT and have restricted drivers installed at the moment. My problem is that when I boot up, it reverts to a really low resolution and when I go to change it back (System>Preferences>Display) it pops up with the following: > It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?
So I click "yes" and Nvidia's preferences pop up. I select X Server Display Configuration and use the tool to switch my resolution back to 1600x1200. But when I click "Save to X Configuration File", it spits the following back at me: > Failed to parse existing X config file '/etc/X11/xorg.conf'! And then as soon as I click OK, the program exits on me. The resolution is still back to where I like it and stays that way until I shut down and boot up again, but it's rather annoying to have to deal with it every time. What should I do about it?

EDIT: Well, I found a solution [here](http://www.techhamlet.com/2009/09/ubuntu-linux-how-to-fix-nvidia-x-server-settings-error/) for anyone who happens upon this and is having the same trouble.

---

