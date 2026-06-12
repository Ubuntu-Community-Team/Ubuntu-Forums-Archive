---
title: "Solution found for small TV fonts!"
date: 2007-12-14
forum: Mythbuntu
---

### Post by thematadorme on 2007-12-14
I have seen many posts by users complaining about the small size of Mythbuntu fonts as displayed on their television screens, and that changing the font size on the desktop does not affect their size in Mythbunutu. I have also read many "solutions" that involve opening a terminal and altering the dpi manually. This seemed a little complex, so I found an alternate solution. Hopefully, it will work for you as well. (By the way, I'm using Mythbuntu 7.10)

*Note*
This fix can be difficult, as it requires you to navigate the very screens with the fonts that are too small to read. If you can, hook your box up to a computer monitor to make these changes, then plug back into your TV. If not, I will try to talk you through "blind", as it were.

Start by running the MythTV Frontend. You will see a status bar witch reads, "Pre-scaling theme images" (in case it's too small for you to read). Once at the main menu, use the up/down arrow keys (or your remote, if it's configured) to highlight "Utilities/Setup" and hit <enter>. Go down to the bottom and select "Setup". The settings we're looking for are in "Appearance", so select it.

Now we are at the point where the fonts get really small. If you can read these fonts, please bear with me as I describe them for those who can't.

On this first screen, users can chose different "themes" and you will see a thumbnail of the current theme in the upper right corner. The screen is dominated by long blue boxes. These are the fields for the various settings and the text to their left is the name of that setting. (I warned you I would be describing these! However, I would rather be too descriptive, than not descriptive enough). Two thirds down, on the left-hand side, there is a Black Check-box before the setting, "Use a random theme". It is the setting just above this one that concerns us. The text above the check-box is, "Font size:".

"But, thematadorme! I've already tried that and nothing changed!"

I know, but I'll get to that in a minute. First...

You can use Up/Down to highlight the blue field in a thin white outline, then use Left/Right to cycle through the three settings: "default", "small" and "big". Even if you can't read it, you will know you have selected "big" because it is the shortest of the three words/blurs. As many of you may have discovered, this doesn't seem to do much. Well, it hasn't. In fact, the font size has only increased a few points. That is our next stop, and, in fact, you can just skip this one, if you want, and go straight to the real problem.

Highlight' "Next>" all the way down in the bottom right corner and hit <enter>.

This screen doesn't help us, so hit "Next>" again.

The third screen is mostly blank by default, with one line of text at the top preceded by a Black Check-box. Skip it by hitting "Next>".

The fourth screen is language and date/time, skip it: "Next>".

Finally! the fifth screen is what we've been looking for! The upper right portion of the screen contains three long black boxes. These are the fields for the three font sizes! The top one is "Small", the middle one, "Medium", and the lower one, "Big". Use Up/Down to highlight each field. Then use Left/Right it increase or decrease (yeah, right!) the font size. The default sizes are: 12, 14 and 26. I changed mine to: 18, 26 and 40, but I had also already selected "big" on the first screen, so if you skipped that step, I suggest you make your "small" font 40. Then, you should have no problem seeing what you're doing and can go back and change it later. When you're done, highlight "Next>" in the lower right and hit enter.

This is the last screen in the "Appearance" settings. Hit "Finish" in the lower right-hand corner to apply the changes you've made.

Ta-da! Well, at least that worked for me. I hope it helped you too. Now, if only I could solve my other problem...
[http://ubuntuforums.org/showthread.php?t=639079]("http://ubuntuforums.org/showthread.php?t=639079")

---

### Post by talbot_sk on 2010-07-06
This is useless for me, because my small fonts are competly unreadable. They are 1 pixel height on PC monitor. I'm lost in mythtv-setup... Please could you write me complete manual, how many times I should click down arrow, press enter etc.? Thank you very much for your help.

---

### Post by LowSky on 2010-07-06
> **talbot_sk said:**
> This is useless for me, because my small fonts are competly unreadable. They are 1 pixel height on PC monitor. I'm lost in mythtv-setup... Please could you write me complete manual, how many times I should click down arrow, press enter etc.? Thank you very much for your help.

You just resurrected a 3 year old post. Many things have changed. What resolution are you using? Try switching to a smaller one to increase the font size.

---

