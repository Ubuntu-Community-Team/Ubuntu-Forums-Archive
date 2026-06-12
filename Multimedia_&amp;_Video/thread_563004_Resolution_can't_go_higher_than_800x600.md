---
title: "Resolution can't go higher than 800x600"
date: 2007-09-29
forum: Multimedia &amp; Video
---

### Post by yohosuff on 2007-09-29
Hi, I'm new to the forums.

My screen resolution can't go any higher than 800x600.

I'm running Ubuntu (latest version) on a HASEE laptop computer, VIA 1.5 GHz Celeron Processor, 256 DDR.

I don't know what other information would be helpful in solving this problem. Let me know what to do because this resolution sucks.

Any help on this would be appreciated. Thanks.

---

### Post by skyjacker on 2007-09-29
> **yohosuff said:**
> Hi, I'm new to the forums.

My screen resolution can't go any higher than 800x600.

I'm running Ubuntu (latest version) on a HASEE laptop computer, VIA 1.5 GHz Celeron Processor, 256 DDR.

I don't know what other information would be helpful in solving this problem. Let me know what to do because this resolution sucks.

Any help on this would be appreciated. Thanks.

Try this Interminal type "sudo dpkg-reconfigure -phigh xserver-xorg". Leave out the " "
Select the resolutions you want available by hitting the spacebar. This will place a + sign in the small box to the left of the line. Validate the settings by hitting "Enter". Restart X with Ctrl+Alt+Backspace. That will restat X When The system restarts you should be able to find your resolutions in the list. Good Luck


Ubuntu Rocks:guitar:

---

### Post by thunderdell on 2007-12-03
Hi skyjacker,

I am having the same problem, even after following the step given by you.
I am using Samsung Syncmaster 710N, and my resolution stuck at 800x600 :confused:

Here is the screen section of my xorg.conf
--------------------------------------------------------------
Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G70 [GeForce 7600 GS]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024"
        EndSubSection
EndSection
--------------------------------------------------------------
Can anyone tell me what's wrong?

Thanks before.

---

