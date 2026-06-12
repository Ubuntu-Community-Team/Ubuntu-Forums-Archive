---
title: "Subtitle settings location"
date: 2010-03-07
forum: Mythbuntu
---

### Post by bbruenfl on 2010-03-07
Hello Community!

I have been poking around trying to find where the settings for how the Internal player displays subtitles are stored.

I'm fairly certain they are not in the mythfrontend setup menus.  I systematically changed all the settings that seemed relevant without any effect on the subtitle display.

So, I'm guessing they are in an xml file or (gulp) hard coded in a compiled file.

Any help would be deeply appreciated.

Cheers.

---

### Post by bbruenfl on 2010-03-08
Oi!  I found a partial answer...font size and spacing is hardcoded into osd.cpp.  I found it here...

[http://www.gossamer-threads.com/lists/mythtv/users/423269#423269](http://www.gossamer-threads.com/lists/mythtv/users/423269#423269)

If those are things you want to change you'll have to build your own executables.

Perhaps, I can find settings for position in there too.

---

### Post by bbruenfl on 2010-03-08
Alright, I read the section of code that corresponds to subtitles and it looks like a fairly simple thing.  It takes the reported size of the display and places the subtitle text in a space defined by the number of lines in the particular section of text when the text is broken into lines of not more than 50 characters while respecting the integrity of words plus an area of blank space equal to the height of one line.  

My working hypothesis is the video player is using inaccurate values for the display size.

So, dear community members I have a request:

If you are experiencing what might be described as overscan with regard to subtitle placement when watching videos with embedded or discrete subtitle files (srt, etc), could you post graphics card model, driver version, screen resolution, monitor type, and a rough description of placement or even better a screen shot.

If on the other hand, your subtitles work fine in the situation described above, could you post the same.  Minus, of course, the screen shot and/or description of the error.

If we can scrape together enough data, maybe we can figure out how to solve and problem and get some nice developer to put into the trunk for us.

Thanks.

---

