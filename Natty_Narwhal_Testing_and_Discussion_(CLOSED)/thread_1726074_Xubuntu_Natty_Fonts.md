---
title: "Xubuntu Natty Fonts"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by XubuRoxMySox on 2011-04-10
I'm a total Xubuntu fanboi and couldn't wait to try Natty. There's alot to love about the new Xfce and the truly lightweight implementation of the new Xfce with truly lightweight applications! Awesomeness!

The only little thing is the fonts in Firefox (4) and Thunderbird (probably the *only* two exceptions to the "lightweight apps" comment above). Sometimes linked text looks like someone struck through the text with a Sharpie using an unsteady hand. But if I mouse over the text it returns to "normal."

Weird.

Then there's text running over the next line of text or running "out of bounds" in Firefox. I think I can reduce the font size in Firefox Settings and fix that, but the Sharpie thing? Just for grins I installed Midori and had the same issue with the "Sharpie strikeout" looking stuff, so I'm guessing it's something in Xubuntu Natty.

[COLOR="Purple"]**FIX:** Menu > Settings > Settings Manager > Appearance > Fonts > Check the Enable Anti-aliasing box and set Hinting to Full.[/COLOR]

**All fixed up!** Also the Ubuntu font is prettier than the default Droid font (chosen because - when it's not messing up - it's lightweight and easy on the eyes). Marked SOLVED.

---

### Post by XubuRoxMySox on 2011-04-11
Made the following changes on the advice of a friend... so far it seems to have fixed the issue. 

Locate /etc/fonts/config.d and delete the 3 files that start with a "10."

Then open a terminal and enter:

```
sudo dpkg-reconfigure fontconfig
```

I like the new Droid default font in Xubuntu! But I've never seen this Sharpie-strikeout looking stuff before. I'll browse all over the place and see if this fix works long term.

-R

---

### Post by teachop on 2011-04-11
I have Xubuntu Natty running, but I switched right away to the Ubuntu font family.  I have not seen any font issues, it looks fine, including Firefox.

I had not tried Xubuntu for several years, and like what I am seeing in the beta1 so far (using it as my main home machine right now to get some good testing on it).

---

### Post by XubuRoxMySox on 2011-04-11
My solution (post #2 above) kinda sorta worked... at least it reduced the severity and frequency of the problem (not unique to Firefox, Midori acted the same way). I just switched to the Ubuntu font family. Will post results here after I've had a chance to try it out for awhile.

Thanks!

-Robin

---

### Post by XubuRoxMySox on 2011-04-11
Okay, that helped a little more... it's odd that the problem persists but with less frequency and severity after changing those settings and switching to Ubuntu font.

Google suggests that "aliasing" may have something to do with it, but I dunno what that means (yet)...

---

