---
title: "Displaying 16:9 within 4:3"
date: 2010-08-05
forum: Mythbuntu
---

### Post by Barry_IA on 2010-08-05
Hi Folks!

Frontend with a fresh Mythbuntu 10.04 install (overwrote 9.x) on an IBM 8147, using the VGA port.  The TV is a widescreen LCD but is displaying Mythbuntu within a 4:3 screen (black bars to the side).  During the boot can see the screen being filled but most boot data and all of Mythbuntu's menus and playback are in a 16:9 display withing this 4:3 area:

-----------------------------
-&#9619;&#9619; . . . . . . . . . . . . &#9619;&#9619; -
-&#9619;&#9619;                           . . . . . . . . . . . . &#9619;&#9619; -    Black bars to create 4:3 display
-&#9619;&#9619;                           . . . . . . . . . . . . &#9619;&#9619; - (Arg! had to add periods to get right side to position correctly)
-&#9619;&#9619;                           . . . . . . . . . . . . &#9619;&#9619; -
----------------------------


[FONT=Courier New]---------------------
-&#9619;&#9619;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;[/FONT][FONT=Courier New]&#9618;&#9618;&#9618;&#9618;&#9619;&#9619; -
-&#9619;&#9619; . . . . . . .&#9619;&#9619; -      Black bars added to top and bottom
-&#9619;&#9619;                                         . . . . . . .&#9619;&#9619; -      Mythbuntu displays in white area as 16:9
-&#9619;&#9619;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;[/FONT][FONT=Courier New]&#9618;&#9618;&#9618;&#9618;&#9619;&#9619; -      within the 4:3 field
---------------------[/FONT]

Mythbuntu's resolution is set for 1360 x 768 but for some reason the TV is only getting a 4:3 resolution (1024 x 768?).  The motherboard's video is capable of up to 2048 x 1536).

So the question is, how do I correct this display problem.  Tabbing through the 'w' key for screen size just changes the looks of the display in the white area of the diagram -- it does not expand into the 'black bar' areas.

One thing I did which may be confusing the system is the installation was done up here in the Computer Room on an older CRT -- 4:3.  During testing (using the CRT) Mythbuntu did display in widescreen (as it does on the TV), but only with the top and bottom black bars.  I didn't see any screen to change/reset the monitor being used.

TIA! (Again!)   (Off to work; will check Friday afternoon.)

---

### Post by LowSky on 2010-08-05
This can be any number of things. I'm assuming it only has an intel chipset for graphics.

Check the TV, make sure it is set to widescreen and not set to zoom.

also dont try changing the reloution from mythtv, exit the frontend and set it correctly from xfce's display options.

---

### Post by nickrout on 2010-08-06
go through your frontend options and make sure you haven't got some legacy setting for 4:3.

---

### Post by Barry_IA on 2010-08-06
> **LowSky said:**
> This can be any number of things. I'm assuming it only has an intel chipset for graphics.  

Hi LowSky!

Yes, it is an "integrated Intel Graphics Media Accelerator 900" video chipset.

Will check the other options late -- off to work!

Thanks!

---

### Post by Barry_IA on 2010-08-06
> **nickrout said:**
> go through your frontend options and make sure you haven't got some legacy setting for 4:3.

Hi Nickrout!

Will check for that too, in additional to LowSky's suggestions.  Off to work!

---

### Post by newlinux on 2010-08-06
what resoultion is your desktop displaying it (in System->Preferences->Monitor) What are the supported resolutions your TV set takes via VGA? I concur with the other things mentioned. Check your settings on your TV for stretch/wide/zoom etc.

---

### Post by Barry_IA on 2010-08-07
> **newlinux said:**
> what resoultion is your desktop displaying it (in System->Preferences->Monitor) What are the supported resolutions your TV set takes via VGA? I concur with the other things mentioned. Check your settings on your TV for stretch/wide/zoom etc.

Hi Newlinux!

Didn't find the information in that location (path didn't exist) but did verify the Mythbuntu desktop resolution was set at 1360 x 768 x 60 Hz.  ...Switched it to the lower one (1024 x 760 x [?] ) and the TV resolution display showed the same.  Switched back to the higher resolution and the TV's resolution again displayed 1024 x 768.  Haven't seen anything in the manual indicating what resolutions the VGA input will accept.   Last night the playback was in widescreen (all the way across, no black bars at the side) but there were black bars at the top -- I'm supposing the display was squished but didn't look too bad.  ...Maybe excited by it display all the way across! <g>

Currently re-installing Mythbuntu 10.04 on that computer, the difference being this time on the monitor (TV) it will be using.  As the others seemed to indicate, there are potentially a bunch of not-quite-right settings.  Perhaps if I had the expertise of LowSky and the others I could figure it out but being a newbie at this point it seems easier to do a re-install.  Will report back, of course!

---

### Post by Barry_IA on 2010-08-07
Hi Folks!

Just got done with the re-install of Mythbuntu on the Frontend with the above problem (display size / black bar quirks).  Appears that solved that problem and a couple of others I hadn't mentioned.

Still getting black bars at the top and bottom but not nearly to the extent was originally -- is this corrected with the overscan  control?  Toggling the "W" key does enlarge this picture -- first toggle almost fills the screen top-to-bottom but is slightly larger than the screen left-to-right.  Subsequent toggles further enlarges/stretches the display.

Thanks again for the suggestions and guidance!

---

### Post by bance on 2010-08-07
Hi Barry,

Not sure if it'll help, but a lot of info on resolution etc. [_[COLOR="Red"]Here[/COLOR]_]("http://www.mythtv.org/wiki/User_Manual:JudderFree")

---

### Post by newlinux on 2010-08-07
> **Barry_IA said:**
> Hi Newlinux!

Didn't find the information in that location (path didn't exist) but did verify the Mythbuntu desktop resolution was set at 1360 x 768 x 60 Hz.  ...Switched it to the lower one (1024 x 760 x [?] ) and the TV resolution display showed the same.  Switched back to the higher resolution and the TV's resolution again displayed 1024 x 768.  Haven't seen anything in the manual indicating what resolutions the VGA input will accept.   Last night the playback was in widescreen (all the way across, no black bars at the side) but there were black bars at the top -- I'm supposing the display was squished but didn't look too bad.  ...Maybe excited by it display all the way across! <g>

Currently re-installing Mythbuntu 10.04 on that computer, the difference being this time on the monitor (TV) it will be using.  As the others seemed to indicate, there are potentially a bunch of not-quite-right settings.  Perhaps if I had the expertise of LowSky and the others I could figure it out but being a newbie at this point it seems easier to do a re-install.  Will report back, of course!


Yes, sorry, I keep forgetting mythbuntu comes stock with XFCE (I use gnome) and thus the menus are different.  Glad it is all working now. Resolutions can get tricky, with combination of how your TV behaves and what signal you are sending it there are a lot of variables.

---

### Post by Barry_IA on 2010-08-07
> **bance said:**
> Hi Barry,
Not sure if it'll help, but a lot of info on resolution etc. [_[COLOR=Red]Here[/COLOR]_]("http://www.mythtv.org/wiki/User_Manual:JudderFree")

Hi Bance!

I just might play with that screen to see if it helps with the narrowed display (still have black bars at the top and bottom after the re-installation of Mythbuntu this morning).  

Thanks for the site!  (Printing out now. :))

---

### Post by Barry_IA on 2010-08-07
> **newlinux said:**
> Yes, sorry, I keep forgetting mythbuntu comes stock with XFCE (I use gnome) and thus the menus are different.  Glad it is all working now. Resolutions can get tricky, with combination of how your TV behaves and what signal you are sending it there are a lot of variables.

Hi Newlinux!

Figured something like that was the problem as to why it wasn't where you said it was. :)   Was hoping it wasn't a problem with a restricted resolution level on the VGA input!

---

### Post by Barry_IA on 2010-08-07
OK, now I'm more confused!  The 'squished' widescreen display is also displayed when I'm on the Backend computer but only in High Definition (AFAICT); I think Standard Definition is OK.  ...A chart because I am not sure:

 4.1 - - WHBF-DT - - Squished (widescreen with bars at top and bottom)
 4.2 - - RTV  - - - - - Full screen

 6.1 - - KQWC-TV - - squished
 6.2 - - Weather- - - Full screen

 8.1 - - WQAD-HD - - Squished
 8.2 - - Weather - - - Full screen
 8.3 - - WBQD-LP - - Full screen

18.1 - - KLJB-HD - - Squished (also no closed captioning :( )
18.2 - - KGCW - - -  Full screen

24.1 - - WQPT-HD - - Squished
24.2 - - WQPT-SD - - Full screen

36.1 - - KQINHD - -  Not sure: airing an old programme
36.2 - - KQINSD1 - - Full screen
36.3 - - KQINSD2 - - Full screen

So it's looking like the primary channel is High Definition and is always widescreen (when available) but squished, yet the sub-channels, which are standard definition, are being displayed in full screen.  Is this due to needing to separate GUI and TV as suggested by the gentleman with the JudderFree link??

And how come I'm not getting Closed Captioning on 18.1?  I am seeing CC using the old MythDora system (through cable).  (Not an isolated incident; I don't recall ever seeing CC on 18.1 on this system.)

TIA!

---

### Post by Barry_IA on 2010-08-08
Hi Folks!

Well, I'm disappointed!  Last night turned on the Frontend on which I had re-installed Mythbuntu -- back to it's old tricks!  Worked fine in the morning. :(   

OS boot appears normal, but when the Frontend portion starts it gives me the "Language Screen" (English, French, Italian, etc.).  Select English.

Next is a screen indicating can't find the uPNP.  (Assume it's looking for the BackEnd.)  Hit OK for next screen, which is the one for selecting the Backend's IP, etc.  They're all OK so just hit Enter through the set of configuration screens.  

It then finds the Backend but gives me the wrong Selection Display -- whatever it's called.  it gives me the one where the selections are made left-to-right and the Play Recordings is a red drape on a stage.  Going to Setup the selected and displayed-in-the-picture one is the one I want: "Mythbuntu Widescreen".  Sometimes I can get it to change, sometimes not; last night I couldn't.

Display is also the 16:9 within the 4:3 thing again.

LISB4, I had reinstalled Mythbuntu yesterday morning.  Did notice a few of my previous options had been retained, one being the font sizes.  Defaults are something like 12, 15, and 25 and after the re-install (which theoretically reformats the drive) my 8, 11 and 15 were still there.

So, back to square one for suggestions.  (I have not tried Bance's resolution configuration screen suggestion as of yet.)

TIA!

---

### Post by nickrout on 2010-08-08
Is it possible that mythfrontend is starting before networking?

---

### Post by Barry_IA on 2010-08-08
> **nickrout said:**
> Is it possible that mythfrontend is starting before networking?

Hi Nickrout!

I suppose...  I understand the concept but don't understand how to check -- turn off automatic log-in?  There is an approximately twelve second delay between the time the desktop disappears and the next screen appears; in the interim the grayish-black 'window screen' pattern is displayed.

Is that is the problem is there some way to implement a delay?  The other person using the system is essentially computer illiterate.  (And no, not causing any of these problems! <g>)

TIA!

---

### Post by itlarson on 2010-08-09
Could this be a dpi issue?  I just fixed a similar issue by forcing the dpi (dots per inch) to 100 in xorg.  My high def shows were being squashed vertically, and this fixed it completely.  The exact thing I did is specific to nvidia, but if you Google "mythtv dpi" you should find the info you need.

---

### Post by bance on 2010-08-09
Hi Barry,

Not related to your resolution problems, but the start up issues have been reported as a bug.

See _[COLOR="Red"][this]("https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/470672")[/COLOR]_ page, post No.16 appears to have a solution.

I have been having similar behaviour with a remote front-end and am going to try it out. Will report back!

Good luck with the other stuff.

Steve.

---

### Post by Barry_IA on 2010-08-09
Bance (Steve) and Itlarson:

Thanks for the suggestions, though didn't seem to help -- either because I'm such a newbie or did something wrong.  ...What I did find out:

Looked at the "Bug: Frontend Starts to Fast"  (jk: must be on a diet).  the "#16 solution" indicated it was for the Backend, MySQL, and Frontend all on the same computer.  Here the problem is with a Frontend computer.  

Code: sudo nano /etc/init/mythtv-backend.conf
Result: no such file.  Makes sense as I'm on a Frontend.

Code: sudo nano /etc/init/gdm.conf
result: no such file.  Darn.

On to the vertically squashed stuff (mythtv dpi).    The stuff in the 'Configuration' section makes sense as to why it's not working.

Looking for the X configuration files listed, /etc/X11/XF86Config and/or /etc/X11/xorg.conf.  neither one found.  Poo.  

Try the xdpyinfo thing: "if reports your display is using something other than 100x100 DPI..."   grep'd for '100'.  Only finds "visual id: 0x100".  We may be on to something!  Played with some search options, eventually typed in "xdpyinfo | grep -i 'dots per inch'" which resulted in "resolution: 80x60 dots per inch".  That's not a square!  No idea what to do about it.  (If this value seems low it might be because I had to change the Desktop resolution to 800x600 so I could read the screen from the couch.)

BTW, speaking of changing resolutions. if I set the Desktop to 1360 x 768 the TV displays "VGA 1024 x 768 x 60 Hz".    
Desktop: 1024 x 768 - - - - - -TV: 1024 x 768
Desktop: 800 x 600 - - - - - - - TV:  800 x 600
Desktop: 848 x 480 - - - - - - - TV: 640 x 480  (hmm!)
Desktop: 640 x 480 - - - - - - - TV: 640 x 480

I think all those are 4:3 resolutions.  1360 x 768 is a 16:9 resolution which the TV is responding to with 1024 x 768.  I also noted the TV's specs say 136***6*** x 768.

...One thing I did forget to check in the "Display Size" wiki was the note at the end specific for Mythbuntu re: "Mythbuntu erronously forces DPI to 100x100"  (so the 80x60 is right??  I'm getting more confused!)  Will upload this message and report back those results in another.

Thanks again for your assistance!

---

### Post by Barry_IA on 2010-08-09
OK, back again!

Follow-up to Display Size lead (BTW, I'm looking at [www.mythtv.org/wiki/Display_Size]("http://www.mythtv.org/wiki/Display_Size")).  The document suggests "removing the '-dpi 100' arguement from the file ./gdm/gdm-cdd.conf".  ...Yup: you guessed it: couldn't find the file!  ](*,)

OK, off on another tangent.  Let's turn off Auto Log-on and see what happens.  Mythbuntu Control Centre > Start Up Manager > uncheck Auto Log in.  Soft reboot.  Ah!  After clicking at the Desktop to start the Frontend I get the correct menu display!  Still the 16:9 within the 4:3 screen but at least getting somewhere!

This time power boot -- turn computer back on after maybe 15-20 seconds.  Argh!!  Screen is shifted to the left by about 2/3rds of a screen (off center) but is displaying without any bars!

Power boot again -- this time waiting about a minute.  Now the TV displays "VGA 1280 x 768".  And now getting a *full screen display*!!   Yes: it's filling the entire screen!!  No screen within a screen!  Well, almost: still have the squished/squashed display problem but at least we're getting somewhere!!  =D>



<Whew!  I'm going to work to get some rest!! <gg>  See you tomorrow!>

---

### Post by nickrout on 2010-08-10
have you looked in /var/log/Xorg.0.log?

What resolution are you actually running at? ssh in to the machine as the use that runs mythfrontend and execute

```
export DISPLAY=:0
xwininfo -root
OR
xrandr

```

Your basic problem is that X is running at (we think) 1024x768 or a 4:3 ratio on a 16:9 display. Software assumes square pixels, but your pixels are not square.

The best solution is to get your X running at the native mode of the screen. As you say that is 1366x768. However 1X must run at multiples of 8 pixels so the nearest you will get is 1360x768 which is certainly acceptable. Often such screens will be run at 1280x720 by X which can also look OK.

There could be a few reasons why X isn't running at either of the higher resolutions. The most likely is that the EDID data is missing or wrong. EDID is a standard for monitors to pass their characteristics to X (or windows etc). 

If the EDID info is wrong or missing X will default to something low res (like 1024x768 ) which won't overdrive and potentially wreck the screen.

Often adding lines fir vertrefresh and horizsync into xorg.conf often fixes this. Your TV manual should have info to help you choose the right values.

all this is usually revealed in /var/log/Xorg.0.log, but it is very verbose and can take a bit of reading.

If you can't get X running at the right resolution the other alternative os to set the right ratio in the frontend config. Go to Settings|TV Settings|Playback - on the second page there is a setting for "Video-Aspect-Override" - set that to 16:9

at least I THINK that's the right setting :)

---

### Post by Barry_IA on 2010-08-11
> **nickrout said:**
> have you looked in /var/log/Xorg.0.log?

What resolution are you actually running at? ssh in to the machine as the use that runs mythfrontend and execute

```
export DISPLAY=:0
xwininfo -root
OR
xrandr

```Your basic problem is that X is running at (we think) 1024x768 or a 4:3 ratio on a 16:9 display. Software assumes square pixels, but your pixels are not square.

Hi Nickrout!

I have the Desktop resolution usually set at 1360x768, which seems to be the only 16:9 resolution setting available in the list.  (The 'usually' is because at that resolution it is hard to read the screen.)

Have tried various options, with soft boots and hard boots in between.  Seems like when it's right then the next boot it's wrong.

Currently at a full screen (albeit squished) display xrandr gives:

Screen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
[Next the data is in three columns -- I had to put punctutation to get to line up.]
....1360x768.....59.8*
....1024x768.....60.0
......800x600.....60.3.....56.2
......848x480.....60.0
......640x480.....59.9.....59.9






> **nickrout said:**
> There could be a few reasons why X isn't running at either of the higher resolutions. The most likely is that the EDID data is missing or wrong. EDID is a standard for monitors to pass their characteristics to X (or windows etc).

If the EDID info is wrong or missing X will default to something low res (like 1024x768 ) which won't overdrive and potentially wreck the screen.

Often adding lines fir vertrefresh and horizsync into xorg.conf often fixes this. Your TV manual should have info to help you choose the right values.

I was unable to find xorg.conf -- doesn't mean it's not there just I couldn't find it (/etc/X11/xorg.conf??)



> **nickrout said:**
> If you can't get X running at the right resolution the other alternative os to set the right ratio in the frontend config. Go to Settings|TV Settings|Playback - on the second page there is a setting for "Video-Aspect-Override" - set that to 16:9

at least I THINK that's the right setting :)

Found it at (Frontend) Utilities/Setup > Setup > TV Settings > Playback (not Playback OSD).  Here it was original "off', I set to 16:9.  Originally didn't fix anything ==> did a power boot (computer shut off) and watched a few minutes of TV.  Booted up, several times.  Got the "4:3 Display" black bars to the left and right sides, Mythbuntu's Desktop and FrontEnd displaying within that region), but sometimes was shifted to the left, sometimes to the right ==> within the 4:3 viewing area the Desktop and Frontend would be shifted to the left/right, IOW with the desktop the clock at the upper right would be shifted off the screen and the left side of the Desktop  would be about 2" to the right of the left side of the 4:3 viewable area.... "Applications" would be about 2" towards the screen center instead of to the left boundary.  (Hope that's making some sense!)

Right now the screen is displaying correctly -- horray, but as has happened in the past I don't know if it will hold/retain the settings.  Right now have the computer off, will get a bite of lunch and see what happens.

---

### Post by Barry_IA on 2010-08-11
> **Barry_IA said:**
> Right now the screen is displaying correctly -- horray, but as has happened in the past I don't know if it will hold/retain the settings.  Right now have the computer off, will get a bite of lunch and see what happens.

Back from lunch with a follow-up.  Back to the old 16:9 display within the 4:3 boundary (black bars to the left and right).  <sigh>

Did the "export DISPLAY=:0   xrand: thing; same results as posted previously.

Soft reboot; get a full screen (1280x768) but the Desktop screen is shifted to the left by about 6"  (I know it would vary with the dimensions of the screen).

2nd soft reboot; full screen but now the Desktop is shifted to the right.

3rd soft reboot.  Still full screen and correct centering.

That pattern of having to do multiple soft reboots seems familiar.  Hopefully means something to someone out there!


And speaking of familiar sightings, not sure if this has any meaning but I have the BIOS configuration set so it will display the text rather than a pretty picture.  The various screens (the one with the hardware information, another one with network) change in size and resolution.  The initial one (cpu, memory, hard drive, etc.) is always in the 4:3 mode (has the black bars to the side); TV displays the resolution as 640x486x60.  The next screen is for the network and it is full screen, the TV displaying a resolution of 720x400x70.  It then blanks, goes to another screen (think it's blank -- no text) but the TV is showing a resolution of 640x480x60 again.  No idea if this is significant.

Thanls again!

---

### Post by nickrout on 2010-08-11
you need to look at /var/log/Xorg.0.log

---

### Post by LowSky on 2010-08-11
You have a monitor issue, not a PC problem. The only thing you should be doing from the OS is setting the screens recommended resolution.

The BIOS scren and boot up screen will show at odd screen sizes, dont worry about that. Its completely normal!

If the image isn't centering there is no need to reboot the computer. The monitor should have an option to refresh the display from its own menu or settings button.

---

### Post by Barry_IA on 2010-08-11
> **LowSky said:**
> You have a monitor issue, not a PC problem. The only thing you should be doing from the OS is setting the screens recommended resolution.

The BIOS scren and boot up screen will show at odd screen sizes, dont worry about that. Its completely normal!

If the image isn't centering there is no need to reboot the computer. The monitor should have an option to refresh the display from its own menu or settings button.

Hi LowSky!  

The image centering problem I'm thinking I didn't quite explain correctly: the Mythbuntu Desktop (and Frontend if I go that far -- currently doing a manual log-in) is off-center within in the "4:3 screen" boundary.  

The last three-four times I've powered up the system today the raster (not sure if that's the correct term any longer -- think it was with CRTs) appears to be centered: can see the slightly gray scan area.  The signal from Mythbuntu is off-centered.  Will look for a reset on the TV.

...Perhaps there is a problem with TV; I hope not!

Glad to hear about the BIOS screens not being the sign of a problem -- was thinking not but then figured I may as well bring it up.

..Just thought of something: I'll have to check the TV's manual to see if there is some setting which needs to be changed.  

Thanks!

---

### Post by nickrout on 2010-08-12
read my previous posts.

also, what TV is it and how is it connected to the computer?

---

### Post by Barry_IA on 2010-08-13
LowSky and Nickrout:

I apologize for the delay -- family matters.  

Looks like LowSky is the 'winner', or at least for part of the problem! Was looking at the resolution displays on a different TV; it displayed "1360x769" with a VGA connection, how come the one I'm working on doesn't?  Looked at the specifications more closely: <grumble!>  PC Mode only goes up to 1024x768!  (See attached: TV-SR.jpg -- the one with the top line of "PC Mode".)

The looked at the specifications for the other TV.  (TV-LR.jpg -- the one with the top line of "Model".)  Only gives me the maximum resolution but no specifics for each input.  

Looks like I'll be buying an HDMI daughtercard!  (May as well buy two!)

Nickrout: you did provide lots of valuable information which I do appreciate.  I may or may not need it after getting a compatible signal source for the TV.  It will be kept for future reference.

---

### Post by nickrout on 2010-08-13
Ahh well yes that would be the problem. As they say "if all else fails, read the (TV) instructions !"

I found my (Sony LCD) TV was much nicer with HDMI than VGA, even though both would do good resolution.

Now you need to make sure you get an nvidia card that supports VDPAU, and you will get a MUCH better experience from myth. 

A GT220 or GT240 seem to be the current best value cards, make sure you get one with 512M RAM, not 256.

Other things to look at: fanless (quiet, but often have huge heatsinks)?

---

### Post by tabcom on 2010-08-14
I have an Insignia duo TV\DVD|PC monitor. Does the same thing -- VGA only setting. I'll have to swap monitors to get proper screen res.

Thanks for the thread -- very helpful.

:D

---

### Post by Barry_IA on 2010-08-18
Hi Folks!

Installed the video card with a HDMI output this morning -- fixed the problem!!  (So LowSky was right about the monitor - on this TV the VGA input does not support anything above 1024x768, which is a 4:3 format resolution).  

Nickrout did suggest two video cards -- unfortunately I received that information I after I had placed the order.  Maybe fortunately. <g>  I have an EVGA 210 (nVidia GeForce 210) with 512 MB on-board memory.  Live TV viewing and recorded TV playback appears fine -- audio needs to be cranked up but that's a different problem.  For fun I was checking out a video and song I like on YouTube; default size was fine but switching to Full Screen mode was choppy (the video; audio was continuous).  Haven't checked if the problem was just with that video or what.  (before installing the video card had checked the video with the VGA output -- at Full Screen it was fine, though we are talking an increase in resolution and maybe even the size of the display area gets factored in).

The video card uses the PCIe x16 slot.  A quick note to us other amateurs: be certain your computer's power supply is capable of supplying the needed power.  The video card I got wants a minimum of 300 Watts.  This is the power being put *out* by the PSU, not the amount of power being drawn by the computer's power cord.  You may have to look on the data plate affixed to the power supply box (open up the computer).  (The data plate on the back of the computer chassis does not have the information we're needing.  ...That help any, Tabcom? :) )

---

### Post by Barry_IA on 2010-08-18
> **tabcom said:**
> I have an Insignia duo TV\DVD|PC monitor. Does the same thing -- VGA only setting. I'll have to swap monitors to get proper screen res.
Thanks for the thread -- very helpful.:D

Hi Tabcom!

Glad to be of assistance!  Maybe: these little quirky problems have been giving me virtual headaches! <g>  It's kind of amazing the things we take for granted/overlook: I assumed the TV's VGA input would accept the highest resolution listed - nope! :(   ...Will be 'interesting' when I add the second TV to the system -- it's the one without any specs (TV-LR.jpg, IIRC).  Same brand, just larger.

---

### Post by Barry_IA on 2010-08-26
**[FONT=Palatino Linotype]SUMMARY:[/FONT]**

The Mythbuntu Frontend  computer was using the VGA In of the widescreen TV but displaying a 16:9 picture within a 4:3 window (black bars to the left and right -- see my initial post for an ASCII diagram).

The problem was due to the TV's VGA input; it had a maximum resolution of 1024 x 768, which is a 4:3 resolution.  The TV itself has an overall maximum resolution of 1366 x 768, which is a 16:9 resolution.  (I'm assuming other inputs are also lower than the maximum, such a S-Video -- IIRC that standard is around 400.)  A more careful look at the specifications for the TV revealed the unfortunate fact.

- - - - - - - - -

I have seen the following chart elsewhere and it seems accurate:

1360 x 768 - - - 16:9
1152 x 864 - - -  4:3
1024 x 768 - - -  4:3
 800 x 600 - - - - 4:3
 640 x 480 - - - - 4:3

My computer monitor is set for 1920 x 1080, outputting 16:9, so presume that resolution could be added to the above.

---

