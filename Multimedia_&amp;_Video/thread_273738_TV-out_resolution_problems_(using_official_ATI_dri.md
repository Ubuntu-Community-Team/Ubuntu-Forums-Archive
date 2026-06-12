---
title: "TV-out resolution problems (using official ATI drivers with aticonfig)"
date: 2006-10-08
forum: Multimedia &amp; Video
---

### Post by gigiya on 2006-10-08
I'm having a really odd problem with using two displays.  I have a Radeon X1400 on my Dell E1705.  While trying to get my clone display working, I encountered some problems.  I used the ATI Control utility that came with the drivers, and simply chose to use the second display as a clone.  I restarted, and my display was only on my TV at 1440x900 (I'm using a composite cable so my max res on the TV is 800x600).  I restarted again, and my display was only on my laptop at 800x600.  I restarted again, and my display was on both my laptop and TV at 1440x900.  I tried using the ati-config --tv-geometry command to change the size of my TV display (here's what's in aticonfig --help in regards to that in case you don't use it):

> --tv-geometry=WIDTHxHEIGHT{+|-}X{+|-}Y
              =WIDTHxHEIGHT
         Change the size and position of the TVout display.
         WIDTH and HEIGHT are in percentage units. Please note
         that the valid range for WIDTH and HEIGHT depends on
         the tv-format selected. However, as a rule of thumb
         WIDTH and HEIGHT are valid in the range [1,100]
         X and Y are pixels offsets from centre
         of the screen. X and Y are have variable ranges dependant
         on ASIC. Use tv-info to get valid X and Y ranges
         If tv-geometry is invoked with just width and height
         then X and Y are assumed to be 0

I think I set it to 55x66 with no pixel offset.  I restarted again in hopes of it working, but I again encountered the same problem.  First restart, only 1440x900 on the TV, second restart, only 800x600 on the laptop, third restart, 1440x900 on both.  Info on the ATI site is almost nonexistent, and I couldn't find much in regards to this specific problem on the forum.

---

