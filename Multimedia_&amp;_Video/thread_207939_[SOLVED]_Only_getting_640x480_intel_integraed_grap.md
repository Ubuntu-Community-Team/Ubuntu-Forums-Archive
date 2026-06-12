---
title: "[SOLVED] Only getting 640x480 intel integraed graphics"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by n00bWillingToLearn on 2006-07-02
I have a 4 year old laptop with intel integrated graphics and my native resolution is 1024x768 but when I go to System-> preferences-> screen resolution the only option is 640x480. This is a fresh install of dapper, with the default drivers.

[edit] It would only let me upload my xorg.conf if I copied it and added the .txt

---

### Post by fragos on 2006-07-02
Your xorg.conf says your only available resolution is 1024x768, 640x480 isn't even an option.  You have a valid looking driver selection but I have no way of knowing if its correct.  If Linux was confused about what driver to use it would select "vesa".  For reference I've included an extract from my xorg.conf.  There are a number of "Display" subsections and I'd change all Depths to be the same.  If you choose to add a resolution beyond the capabilities of your display you can damage it.

SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection

---

### Post by n00bWillingToLearn on 2006-07-02
[quote=fragos]Your xorg.conf says your only available resolution is 1024x768, 640x480 isn't even an option.  You have a valid looking driver selection but I have no way of knowing if its correct.  If Linux was confused about what driver to use it would select "vesa".  For reference I've included an extract from my xorg.conf.  There are a number of "Display" subsections and I'd change all Depths to be the same.  If you choose to add a resolution beyond the capabilities of your display you can damage it.

SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection[/quote] I deleted the 640x480 from the xorg.conf when I was running the liveCD to try to force it to use 1024x768 ( Although I don't remember doing it after the install so mabe the install copies the xorg.conf from the current xorg.conf in memory when it installs or my memory is bad ). In the liveCD ( and still now ) I am only getting 640x480 surrounded by black. 1024x768 is my resolution in windows so it is definately not "beyond the capabilities of my display". The only reason I mentioned anything about the driver is I veguely remember hearing about another intel driver for older computers and I was wondering if the default driver that is installed is in fact the correct driver. Just to be clear ( as I don't know much about xorg.conf and probably shouldn't have messed with it in the first place ) what do you mean by change all the depths to be the same? I remember there being a command to reconfigure x, should I try that to be sure all of my changes are gone? ( I didn't really take note of what I changed because I figured that it was just a liveCD and wouldn't affect the install )

---

### Post by n00bWillingToLearn on 2007-10-05
Solved : [https://help.ubuntu.com/community/FixVideoResolutionHowto#head-0e3051713171cb5d1bf49dc2dc7bea24eb9ed83e](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-0e3051713171cb5d1bf49dc2dc7bea24eb9ed83e)

---

