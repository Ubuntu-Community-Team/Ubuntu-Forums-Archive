---
title: "HP RC6 remote control play button issue."
date: 2011-03-10
forum: Multimedia Software
---

### Post by kage52124 on 2011-03-10
Hey all,

I was wondering if anyone who had an HP RC6 remote control could explain how they got _all_ their buttons working.

My remote is a RC1762308/01B and has config files for LIRC, but I am not running LIRC as it seems Ubuntu sees the remote as basically a keyboard.

The only button that doesn't work for me is the Play button, but I have read that some people get all but Play, FF, and Rewind to work in the same fashion.

Also, when I try and make a custom command for keyboard input, the Play button is the only button that will not register, so I think I need to change something a little deeper.

For anyone who hasn't been able to get their HP RC6 remote to work, I've also read that updating your BIOS has helped, as well as not using LIRC; I will edit this post if needed.

So my overall question is: "Can anyone tell me how to make Ubuntu see just this one button and tie it to the XF86Play keystroke?"

Thanks a bunch!

Also, should this be here or Hardware, kind of a coin toss to me...

related link: [See here]("http://ubuntuforums.org/showthread.php?t=1000299")

---

### Post by kage52124 on 2011-03-12
Okay, just to post information found: It turns out that both my play button and the Quickplay button do not get read by *at least* the kernel I'm using (2.6.35) according to both the command 'xev' , 'acpi_listen' , and the instructions overall found [here]("https://wiki.ubuntu.com/Hotkeys/Troubleshooting"): [https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)

So I guess the only thing to do is continue waiting for a new built kernel.

Sorry again if this is the wrong place for this issue.

---

