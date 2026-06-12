---
title: "Wizardpen"
date: 2010-07-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23dornot23d on 2010-07-30
I thought I should bring this topic here as its to do with Maverick 10.10
( Brief explanation - these are used for the drawing tablets and pens - like G-Pen )
 The wizardpen drivers ....... do they need changing now ,,,,, so they will work on the new version,

It took me quite a long time setting these up in past versions of Ubuntu.

Has anything changed with the drivers to stop them working. as I noticed the following thread,

[wizardpen 10.10 problems thread]("http://ubuntuforums.org/showthread.php?t=1524847")

I have a link to how I set them up before - I will find it so that I can see what happens

Thread link to set up drivers ( [Paint Programs]("http://ubuntuforums.org/showthread.php?t=1322647&highlight=paint+program&page=3") - I addded it here - I need this information copying to try again)

```

but once I get the Genius Pen working on here .....

we will be on the right road ......... So how do I do that ?

we need a driver called ...........  wizardpen ......... 0.70 ....... or something .... 

find a link for it there is a Debian package somewhere .... ?       

I followed this once ....... but I never got it to work on the laptop .... 

**************************************************  *********************************

I HAVE NOW THOUGH WICKED ............ this works for a Genius ,,, Pen ... and Tablet ... on 9.10 ....

[http://www.mediafire.com/file/nyzyyn...lpha2_i386.deb]("http://www.mediafire.com/file/nyzyynygiyy/wizardpen_0.7.0-alpha2_i386.deb")

I added the fdi file after this as shown in the readme ...... here ..........

README - CONFIGURATION
======================
Primary author (documentation): Felix Leong (seh_hui at yahoo.com)

This document describes how to configure the Wizardpen driver.

**TODO** Proofreading and formatting polish

CONFIGURING THE DRIVER
----------------------
** RECOMMENDED CONFIGURATION STEPS FOR XORG 7.3 **

To fully exploit HAL-based hotplugging provided in Xorg 7.3, the following
steps should be observed:
    1. Connect your Wizardpen tablet
    2. ** IMPORTANT ** Find out the name of your tablet by executing
        `grep -i name /proc/bus/input/devices`
    3. Create a new file 
gksudo gedit /etc/hal/fdi/policy/99-x11-wizardpen.fdi
    4. Edit the fdi file and paste the following template:
            <?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="NAME OF YOUR TABLET">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
                </match>
            </device>
            </deviceinfo> 


    5. Restart your computer


__________________________________________________  ____________________

This works just fine .......... love it ......... UBUNTU 9.10 ROCKS now ....... :wink:

```I will install and try it out ....... (now I have found how to do it again.)
UC-LOGIC Tablet WP5540U


[B]CONFIRMED ...... THIS NO LONGER WORKS

The pointer jumps straight to the left top corner of the screen and sits there,



[COLOR=Red] THIS THREAD CAN BE DELETED AS I HAVE [ADDED IT TO THE OTHER THREAD]("http://ubuntuforums.org/showthread.php?t=1524847") NOW
[/COLOR]


[/B]

---

