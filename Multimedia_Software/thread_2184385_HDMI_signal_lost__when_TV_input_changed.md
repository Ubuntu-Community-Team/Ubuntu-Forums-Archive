---
title: "HDMI signal lost  when TV input changed"
date: 2013-10-28
forum: Multimedia Software
---

### Post by progressnerd on 2013-10-28
I have Ubuntu 13.10 running on my HTPC, connected to my TV via HDMI. The video signal from the HTPC to the TV works great when I boot the computer while the TV is set to that HDMI input. However, if I change the TV input and then change it back to the HTPC's HDMI input, the TV often (not always) claims "no signal". I've configured Ubuntu to never suspend and the the screen to never turn off due to inactivity, so it is not a problem with the HTPC failing to wake-up from suspend --- it must be something subtler than that.

I have noticed one way that consistently restores the signal: use key combinations to logout. I press CTRL-ALT-DEL (to bring up the logout selection window) followed by ENTER (to logout). I can't see the logout actually being selected (because the TV still shows no signal), but after pressing ENTER, the screen "flickers" and the HDMI signal is restored. I then enter my password to log back in.

So I know the OS isn't hanging in any way and still responding to all keyboard input. It just seems as if after changing the TV input back to the HDMI/Ubuntu machine, the display needs a little "kick" to let the TV know a signal is present.

Finally, I should note I haven't had any similar problem with this HDMI port on the TV. I used to have Windows on the HTPC and didn't have this problem.

Any ideas?

---

### Post by Rawit on 2013-10-30
I don't know what brand TV you have, but on my Sony I can switch off Auto Scale and Auto Detect/Switch On. It turns the HDMI into a "dumb" input, which for me is actually better when using the HTPC, because I would get the same issue you have with Auto everything on On when a temporarily resolution switch was made.

---

### Post by progressnerd on 2013-11-20
It's a Vizio and doesn't appear to have that option. Any idea what is happening when I bring up the login window that causes the hdmi to "wake up"? Is it a resolution change at that point?

---

