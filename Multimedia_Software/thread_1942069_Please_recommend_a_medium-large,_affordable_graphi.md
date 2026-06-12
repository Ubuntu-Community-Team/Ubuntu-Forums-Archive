---
title: "Please recommend a medium-large, affordable graphics tablet for Hardy/Natty?"
date: 2012-03-16
forum: Multimedia Software
---

### Post by ageofsteam on 2012-03-16
I've been using a Wacom Bamboo Fun for drawings, navigation, etc. for many years (and despite considerable abuse, it still works well!) but I've heard that using a larger tablet makes the line art smoother.  I used to have a much larger Wacom, but it won't run on Linux. :(  And I don't have much spare cash, *at all*.

Could someone recommend a good, Hardy/Natty compatible graphics tablet that would be larger and somewhat affordable?  I don't want to buy one only to have it not work on Linux...

I use The GIMP, Inkscape and MyPaint if that is relevant; pressure-sensitivity would be nice, but I'm not 100% sure that I would need it, since I seldom use those settings now...

Tablets aren't exactly my field, so could someone more knowledgeable give me some advice?

---

### Post by Favux on 2012-03-16
By any chance do you mean Lucid (10.04) and not Hardy (8.04)?  Because Hardy makes it tough.

First thing is if you are short of cash and have an old Wacom large enough, is it a Wacom serial graphics tablet?  And that's why it doesn't work in Linux anymore?  And did in Hardy which is why you mention Hardy?  If so that is no longer true, see "[HOW TO Set Up a Wacom Serial Tablet in Ubuntu Lucid, Maverick, Natty, & Oneiric]("http://ubuntuforums.org/showthread.php?t=1780154")".  So if it is a Wacom serial graphics tablet you are good to go.  Just a wee bit of compiling.

Otherwise you are probably looking at a non-wacom tablet.  For those check out the [DIGI*mend* project]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend").  That deals with the KYE, UC-Logic, and Waltop tablets rebranded and sold by Aiptek, Genius, Monoprice, Princeton, Trust, and many others. Essentially, any USB-connected tablets not produced by Wacom. 

They now work with the evdev driver if it is recent enough, i.e. Oneiric's 2.6.0 evdev.  Otherwise the WizardPen driver in Natty and earlier.  See the [Tablet support status]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status") page for linux compatablility.  Click on the tablet name in the table and it will take you to the tablet's individual information page that has a picture of it and some spec.s.

---

### Post by ageofsteam on 2012-03-16
I think I may have meant 10.04; I had previously used one under 8.  It's a bit confusing, since I use several comps/ufds and I often reinstall. :(

I no longer have the older tablet; since it no longer worked, I rehomed it to my sometimes-Windows-running sibling.

---

