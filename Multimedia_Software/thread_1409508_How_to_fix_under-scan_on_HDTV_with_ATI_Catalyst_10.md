---
title: "How to fix under-scan on HDTV with ATI Catalyst 10.2"
date: 2010-02-17
forum: Multimedia Software
---

### Post by devguy on 2010-02-17
So, I just bought a 32" Panasonic LCD (1080p) and have decided to use that as my main monitor.  Unfortunately, when I hooked it up to my computer, I had under-scan with both Windows 7 x64 and Ubuntu Karmic x64 (using a Radeon HD 4870 1GB).  In Windows, there was a simple slider in the Catalyst Control Center to fix the under-scan issue.  Unfortunately, the same option wasn't available with the Linux counterpart.  I searched online for some answers, but all the ones I found seemed outdated, or gave me errors.  Using the Aticonfig help command, I figured out how to fix the under-scan in Linux.

**Step 1, identify your DISPLAYTYPE:**
  The choices are:
[PHP]        crt1,  lvds,   tv,   cv,   tmds1, crt2,
        tmds2, tmds2i, dfp1, dfp2, dfp3, dfp4, dfp5,  dfp6 .[/PHP]
For my LCD, the correct option was "tmds1".  The way you decide which one you have is by executing the following command:
[PHP]aticonfig --query-dispattrib=DISPLAYTYPE,positionX[/PHP]
where DISPLAYTYPE is one of the above choices.  If it is the correct choice, you'll receive a bunch of information that probably looks like the resolution numbers you are shooting for.  You know you chose the wrong choice if you get an output like:
[PHP]Query information of sizeX attribute failed, may not supported by monitor crt1.[/PHP]
Also, you can try "Xrandr -q" and see which option is listed as connected.
**Step 2, custom fit your screen parameters:**
Once you've figured out which is your DISPLAYTYPE, now you need to try and get positions and sizes that correspond to the actual pixels on your monitor.  Unfortunately, every monitor is different, so you'll just have to play guess and check.  Start by setting your position.  For me, I found these two commands to put my image at the top left of the screen (filling in DISPLAYTYPE with the parameter you found):
[PHP]aticonfig --set-dispattrib=DISPLAYTYPE,positionX:50
aticonfig --set-dispattrib=DISPLAYTYPE,positionY:27
[/PHP]
Once you have gotten your image in the top left corner, now it is time to set your length and width of the image.  My monitor displays at 1920x1080, but as I am starting an x position of 50, then the size value is going to be considerably less than 1920 (and likewise for the height).  These commands did it for me (filling in DISPLAYTYPE with the parameter you found):
[PHP]aticonfig --set-dispattrib=DISPLAYTYPE,sizeX:1820
aticonfig --set-dispattrib=DISPLAYTYPE,sizeY:1020
[/PHP]

**Step 3, making your changes permanent:**
At this point, you should have custom tailored the displayed image to fill up your monitor using the afore mentioned commands.  Now, if you reboot the computer, the under-scan will return, so we need to make these changes permanent.  Open gedit (type gedit on command line or open it from the Applications->Accessories->Gedit).  On the first line, enter:
[PHP]#!/bin/bash[/PHP]
Then, make an empty line after, and then paste the four aticonfig commands you used earlier (starting with positions, then with sizes).  Save the file as "ati-overscan" (without quotes).  For example, my file looks like this:
[PHP]#!/bin/bash

aticonfig --set-dispattrib=tmds1,positionX:50
aticonfig --set-dispattrib=tmds1,positionY:27
aticonfig --set-dispattrib=tmds1,sizeX:1820
aticonfig --set-dispattrib=tmds1,sizeY:1020
[/PHP]
Now, go to System->Preferences->Startup Applications.  Click on Add, and browse to where ever you saved that script.  Give it a name and a description if you'd like, and click OK.  Now you're done!

Troubleshooting:
  Don't try any of these Aticonfig commands while you have some 3d application running.  Just do it with a terminal running on your desktop and no other applications open.  That will reduce the likely hood that the fglrx drivers won't crash the system.

Note:  ATI, please just add a slider in CCC like you do in Windows.  I cannot imagine it being that difficult to add, given that all this already works.  I was really hoping Catalyst 10.2 would include such a slider, but alas...

---

### Post by jlewis05 on 2010-06-01
Thank you for this post, it was very helpful.  My Panasonic plasma was also tmds1 and its settings were very close to start points of 0 and size was 1920x1080.  I'm running Lucid 64-bit and in GNOME can now run HDMI output very well and HDMI audio out also seems to work correctly. 

Some related oddities though.  It seems that when booting and logging into GNOME initially that I could only set resolutions in Catalyst up to about 1400x1050 while still being able to correct underscan to fill the screen, yet this aspect ratio is wrong and the GUI appears somewhat squished.  Video playback looks fine because I can change aspect ratio in something like VLC.  No other display resolution will work with the underscan correction numbers I came up with in my script.  Now what's more weird is that if I run XBMC it has the underscan problem, but then when I drop back into GNOME the Catalyst options now go up to 1920x1080 which I can set and then run the ati scan script which gives me true fullscreen 1080 display with proper aspect ratio.  

So somewhat XBMC has something to do with this which is a question for another post perhaps, but there's also the question of what's going on with Catalyst normally that it won't go up to 1080 resolution until XBMC has been run.  Maybe I can manually with aticonfig also set resolution just like the over/underscan is set, I'll have to dig into it and see.  And if that can be done, I need to figure out how to run this script or equivalent when XBMC is loaded.  XBMC handles video much better than any of the GNOME video players.

---

### Post by daemonfly on 2010-07-10
Thanks for figuring this out! My searches also came up with nothing useful until I found this thread. I was also thinking that the aticonfig would be the solution, but hadn't scoured all the available settings.

I'll put up my setup results for anyone else with similar hardware:

PC has Gigabyte mobo with integrated ATI HD 4200. This is hooked up to a Pioneer VSX-1020 A/V Receiver, then to a 50" Panasonic Viera TC-P50G20 Plasma Display. tmds2i was the display type I needed (not sure if the AVR being in between affects this or not). Luckily, I didn't need any special offsets or sizes.

Values:
aticonfig --set-dispattrib=tmds2i,positionX:0
aticonfig --set-dispattrib=tmds2i,positionY:0
aticonfig --set-dispattrib=tmds2i,sizeX:1920
aticonfig --set-dispattrib=tmds2i,sizeY:1080

Position x is just a tad off though, it really should be somewhere around -5 but aticonfig doesn't seem to allow negative numbers. No big deal though, I just tried to get it "perfect" ;)

Also, to note, you may have to set the script file you save as executable (right-click, properties, permissions). I did this by default.

---

### Post by devguy on 2010-11-05
Glad I could help you all.  I just updated the OP as I noticed that in Ubuntu 10.10 with Catalyst 10.10, the displaytype attribute I needed wasn't listed by aticonfig.

My new one is dfp2, so just a heads up.  You can get the correct one by querying xrandr -q as well!

---

### Post by tbessie on 2010-11-15
> **devguy said:**
> Glad I could help you all.  I just updated the OP as I noticed that in Ubuntu 10.10 with Catalyst 10.10, the displaytype attribute I needed wasn't listed by aticonfig.

My new one is dfp2, so just a heads up.  You can get the correct one by querying xrandr -q as well!

So do we know why this is happening, tho'? Why suddenly some displays are underscanned by default?

- Tim

---

### Post by devguy on 2011-01-27
> **tbessie said:**
> So do we know why this is happening, tho'? Why suddenly some displays are underscanned by default?

- Tim

Not sure why AMD has their drivers do that by default.  The RadeonHD open source drivers work fine out of the box in Ubuntu 10.10 on my HD 5850.  The Windows drivers actually used to default to underscan as well.

This script is still working fine with Catalyst 11.1 BTW.

---

### Post by kulimazi on 2011-01-30
I'm using Ubuntu 10.10 with HD6950 and latest drivers from AMD (11.1 - released on 1/26/2011) and ran into this as well. I did not like the script approach and but found a "better" solution.

I simply ran this command:

sudo aticonfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0

(needs to be re-run if you upgrade your drivers)

and now my Panasonic TC-P50GT25 over HDMI has full screen - no more blank bars on the sides or top ( I believe it is 1:1 pixel mapping - at least visually it seems that every pixel is used).

I found the solution here:

[http://wiki.cchtml.com/index.php/Configuring](http://wiki.cchtml.com/index.php/Configuring)

---

### Post by The_Fool on 2011-01-31
Thanks for the assistance with extending the display.  It now fills the entire screen.

---

### Post by devguy on 2011-02-03
> **kulimazi said:**
> I'm using Ubuntu 10.10 with HD6950 and latest drivers from AMD (11.1 - released on 1/26/2011) and ran into this as well. I did not like the script approach and but found a "better" solution.

I simply ran this command:

sudo aticonfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0

(needs to be re-run if you upgrade your drivers)

and now my Panasonic TC-P50GT25 over HDMI has full screen - no more blank bars on the sides or top ( I believe it is 1:1 pixel mapping - at least visually it seems that every pixel is used).

I found the solution here:

[http://wiki.cchtml.com/index.php/Configuring](http://wiki.cchtml.com/index.php/Configuring)

Glad to hear that is working now.  When I wrote the script, the method you describe did nothing.  I'll try that when I get home.

I still don't understand why this is not a simple slider in the CCC like in Windows...?

---

### Post by Septor on 2011-02-22
> **devguy said:**
> Glad to hear that is working now.  When I wrote the script, the method you describe did nothing.  I'll try that when I get home.

I still don't understand why this is not a simple slider in the CCC like in Windows...?

Are you sure there isn't?  Last time I checked it was there...

---

### Post by und on 2011-08-27
> **Septor said:**
> Are you sure there isn't?  Last time I checked it was there...

Sorry, but I have TV plugged in HDMI input. It recognized as "CVTE TV" and there's nothing about setting underscan in amdcccle (Catalyst 11.6) settings. So, thanks to TS for solution!

---

### Post by petri on 2011-09-24
Thanks devguy!

Even with the new 11.8 there is problem with underscan and no slider. Bad AMD. :---)

Though it seems that everytime I boot Ubuntu the resolution is slightly off and I have to adjust it just a little bit. No black borders though.

---

### Post by devguy on 2011-10-13
> **Septor said:**
> Are you sure there isn't?  Last time I checked it was there...

Yeah, it is there for a select few of the display options like "tv", but not for tmds or dfp.

I'm using eyefinity across three DVI monitors now, so I don't use this fix anymore, but I'm glad to hear it helped others.  I'll try Oneiric soon with my 6950 and see how it goes!

---

### Post by leprotic on 2011-12-12
Hi. The first two commands are OK but with the third (aticonfig --set-dispattrib=dfp2,sizeX:1920), I get:
------------------
Value 1920 for display attribute 'sizeX' out of range [752-1776]
------------------

I'm absolutely sure my TV is Full HD (1920x1080). Any ideas?

---

### Post by sibbor on 2011-12-22
I've had this issue as well with my 1080p projector. I solved it thanks to this thread, by forcing size to be 1920x1080 and position 0:0. This even though I set this resolution with aticonfig (it reported 1920x1080 but was something like ~1760x~980). I can't help but to feel embarrassed for AMD's sake. This is lousy.

There's NO slider in the Catalyst Control Panel!! 

Thanks op, now my picture is once again pixel mapped correctly (as with the default drivers of Ubuntu 11.10)!

---

### Post by fiddur on 2012-03-29
I got far with these instructions, but still not 1 to 1 pixel, so it was blurry.

Then I found in the amdcccle the right setting for me:
  Display manager
   - DTV(1)
     - Adjustments
       - Image Options: Use graphics processor for scaling.

That gave me back the correct aspect completely!

---

### Post by JvdP on 2012-04-08
This thread has helped me a lot. I have been stuck on the underscan for quite a while. It took some time to figure out that the TV connected through HDMI on my ASUS E35M1-I DELUXE (which has an integrated HD6310) was called "dfp1". Mind you guys, this one isn't listed so you're out of luck if you just try the obvious ones.

The problem I have is, the script doesn't execute properly at startup. Also, when an application goes full screen (such as XBMC) the default displayattributes are set back (underscan). Anybody knows what is wrong here?


> **fiddur said:**
> I got far with these instructions, but still not 1 to 1 pixel, so it was blurry.

Then I found in the amdcccle the right setting for me:
  Display manager
   - DTV(1)
     - Adjustments
       - Image Options: Use graphics processor for scaling.

That gave me back the correct aspect completely!
I don't have those options with my HDMI connected tv.

---

### Post by dew7777 on 2012-05-23
> **JvdP said:**
> 

The problem I have is, the script doesn't execute properly at startup. 

I had the same problem I fixed it by right clicking on the script i made, going to properties then to the permissions tab and there is a check box to make it "execute" . I also added .sh to my script (ati-underscan.sh)  that seemed to do the trick to make it run at start up.  Im in the process of installing xbmc now.

---

### Post by yeahdef on 2012-12-09
Thank you for this informative post! Much appreciated. fixed my problem!

---

### Post by benibuntu on 2013-05-25
Using ATI 13.4 driver on a HD7570 and Ubuntu 13.04 and it worked for me also with

[COLOR=#000000]sudo aticonfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0
[/COLOR]

---

