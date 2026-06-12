---
title: "Screen Resolution Problems after Media Center Install"
date: 2011-12-11
forum: Mythbuntu
---

### Post by Shabakthanai on 2011-12-11
Kubuntu 11.04 (Natty)
KDE 4.7.2
Mythbuntu 0.63-Oubuntu1
Mythtv 2:0.25.0.2C 2:0.25.0~master.2C
pdHDTV HD-5500 tuner card
EVGA GTX460
AMD quad 2300mhz w/4gb RAM
Left Monitor – Acer 22”  Right Monitor ViewSonic 27.5” -   Right monitor being default.


         nVidia X Server Settings
                  Layout
Acer V223W           ViewSonic VX2739wm
 1680x1050               1920x1080
Display
Model:  ViewSonic VX2739 (DFP-0 on GPU-0)
Configuration:  TwinView
Resolution:  Auto
Position:  Absolute          +1680+0
x  Make this the primary display for the Xscreen

    System Settings – Display & Monitor
Kmenu>Applications>Settings>SystemSettings>Display and Monitor>Size and Orientation>default (Connected)
Size:  3600x1080
Refresh:  50.0 Hz
Orientation:  No Rotation
Position:  Absolute  0        0

Notice that in Display & Monitor settings only one monitor is mentioned and the size is the combination of the (1680+1920) 3600 x 1080.

Since the installation of Mythtv, programming appears to be stretched to the 3600x1080 resolution.  I am unable to change to the appropriate 1920x1080 setting; as a result, people appear dwarf-like;  people's bodies are short and wide.

While watching the Nutcracker on PBS, the dancers would twirl with arm and legs outreached.  Their arms and legs appeared twice normal length and about ½ thickness, while their bodies were much shorter with the appearance of dwarf.

When I drag a screen from the right monitor to the left monitor, size is retained and the image does not resize to the smaller resolution.  As a result, when the image is at the left border of the left screen, the right portion of the image spills over into the right screen.

**Is this caused by the Media Center installation, or am I able to re-configure to correct the resolution problem and resize problem created when dragging the image from one screen to the other?**

Living alone, I sometimes like to have TV on the left monitor while I work on the right monitor.  It is like having someone else in the room.  When the image from screen 2 does not resize to the smaller left monitor configuration, I have to move the left portion of the image completely off the screen.

Additionally, even when viewing a movie or TV program on the larger monitor, configuration for the screen remains at 3600x1080 trimming information off the width portion of the presentation.  For example if the screen had the following on-screen:  'KUBUNTU IS MY FAVORITE'  it may appear as follows:  'BUNTU IS MY FAVORI'.  Also face views of people completely fill the screen, so it appears that some height is lost from the images.

Thank you for any help you may provide.

---

### Post by Shabakthanai on 2011-12-12
> **Shabakthanai said:**
> Kubuntu 11.04 (Natty)
KDE 4.7.2
Mythbuntu 0.63-Oubuntu1
Mythtv 2:0.25.0.2C 2:0.25.0~master.2C
pdHDTV HD-5500 tuner card
EVGA GTX460
AMD quad 2300mhz w/4gb RAM
Left Monitor – Acer 22”  Right Monitor ViewSonic 27.5” -   Right monitor being default.


         nVidia X Server Settings
                  Layout
Acer V223W           ViewSonic VX2739wm
 1680x1050               1920x1080
Display
Model:  ViewSonic VX2739 (DFP-0 on GPU-0)
Configuration:  TwinView
Resolution:  Auto
Position:  Absolute          +1680+0
x  Make this the primary display for the Xscreen

    System Settings – Display & Monitor
Kmenu>Applications>Settings>SystemSettings>Display and Monitor>Size and Orientation>default (Connected)
Size:  3600x1080
Refresh:  50.0 Hz
Orientation:  No Rotation
Position:  Absolute  0        0

Notice that in Display & Monitor settings only one monitor is mentioned and the size is the combination of the (1680+1920) 3600 x 1080. **How do I change the aspect ration from 3600x1080 to 1920x1080?  I believe this may solve my problem.**

Since the installation of Mythtv, programming appears to be stretched to the 3600x1080 resolution.  I am unable to change to the appropriate 1920x1080 setting; as a result, people appear dwarf-like;  people's bodies are short and wide.

While watching the Nutcracker on PBS, the dancers would twirl with arm and legs outreached.  Their arms and legs appeared twice normal length and about ½ thickness, while their bodies were much shorter with the appearance of dwarf.

When I drag a screen from the right monitor to the left monitor, size is retained and the image does not resize to the smaller resolution.  As a result, when the image is at the left border of the left screen, the right portion of the image spills over into the right screen.

**Is this caused by the Media Center installation, or am I able to re-configure to correct the resolution problem and resize problem created when dragging the image from one screen to the other?**

Living alone, I sometimes like to have TV on the left monitor while I work on the right monitor.  It is like having someone else in the room.  When the image from screen 2 does not resize to the smaller left monitor configuration, I have to move the left portion of the image completely off the screen.

Additionally, even when viewing a movie or TV program on the larger monitor, configuration for the screen remains at 3600x1080 trimming information off the width portion of the presentation.  For example if the screen had the following on-screen:  'KUBUNTU IS MY FAVORITE'  it may appear as follows:  'BUNTU IS MY FAVORI'.  Also face views of people completely fill the screen, so it appears that some height is lost from the images.

Thank you for any help you may provide.

Notice the request to change, (I believe) the aspect ratio in the comment above.

---

### Post by nickrout on 2011-12-12
> **Shabakthanai said:**
> Notice the request to change, (I believe) the aspect ratio in the comment above.

Please do not quote your whole message, we can all read.

I take it you are running two monitors and want to run mythfrontend on one monitor only. The aspect ratio is been seen as the aspect ratio of both monitors combined?

I think yyou need to set the window size manually in the frontend settings|appearance.

---

### Post by BicyclerBoy on 2011-12-12
Another option (best in my opinionated..) is to not use twinview.

Twinview requires a video metamode to encapsulate both monitors & they must have same refresh rate & you can get panning desktops.
Twinview causes problems to certain programs that can not detect the real full screen target dimensions.

If you don't use twinview you will eventually need to know how to launch programs on a target X screen.

---

### Post by Shabakthanai on 2011-12-13
TwinView is and has been my choice too.  That must not be the problem.  Thanks to all who continue to show patience.  I am very grateful for the help.

---

### Post by Shabakthanai on 2011-12-13
> **Shabakthanai said:**
> TwinView is and has been my choice too.  That must not be the problem.  Thanks to all who continue to show patience.  I am very grateful for the help.

I apologize; I misread your suggestion and thought TwinView was your choice.  An electron must have misfired.  I will try it and play for a while, then respond.  Thank you for your patience.

---

### Post by Shabakthanai on 2011-12-13
> **BicyclerBoy said:**
> Another option (best in my opinionated..) is to not use twinview.

When I change to Separate X Screen and boot to set the configuration, screen positioning changes; the left screen becomes the right screen and vice versa.  My primary monitor is meant to be the right screen and it is larger in size.  27.5", it is also a 16:9 aspect ratio.

The left screen opens with only the Kmenu button on-screen.  All other application launchers are missing including the group that includes the time, LAN, etc.

My primary monitor, on the right opens with a desktop, including plazmoids, however the screen falls short of the width of the window by abut 2 1/2 inches.  In that remaining space the right 2 1/2" of Mythtv shows.  Using Alt+the cursor, I can move Mythtv around, however it does not come to the surface and remains underneath the screen containing the plazmoids.

On occasion, when trying to get the Wintv to the surface of the screen or get the screen with plazmoids to fill the entire window, an analog clock plazmoid that usually appears in the upper left corner of the screen and about 3" in diameter, then fills the entire window.  The analog clock is then made oval in shape, left to right, however when the analog clock is in it's normal placement, it is approx. 3" and round, not oval.

I place my panels on the top of the screen with Kmenu in the upper right corner of the screen.  I also have it set to auto-hide.  When the analog clock fills the entire window, the Kmenu and other application buttons drop down and are huge in size.  Each is over an inch square.

When I attempt to restore the settings, in the NVIDIA X Server Settings menu, and when the settings are returned where they are supposed to be, the application is unwilling to save the changes or allow me to boot to set them.  On one occasion, I was told that I did not have write position to make the changes.

I am unfamiliar how to change permissions using the CLI, yet, and am not permitted to make the changes using the GUI, so I am currently stumped at what to do.

I am fairly sure I can resume some normalcy using TwinView, with the exception the problems I am trying to correct will probably also return.

Twinview requires a video metamode to encapsulate both monitors & they must have same refresh rate & you can get panning desktops.
Twinview causes problems to certain programs that can not detect the real full screen target dimensions.

If you don't use twinview you will eventually need to know how to launch programs on a target X screen.

>I will have to get the separate screens opening normally before I can take your advice about launching programs on a target X screen.

Does it appear that I have things too mixed up to repair and restore my dual monitors with proper aspect ration and resolutions on both screens?

Thanks!

---

### Post by Shabakthanai on 2011-12-13
> **Shabakthanai said:**
> >I will have to get the separate screens opening normally before I can take your advice about launching programs on a target X screen.

Does it appear that I have things too mixed up to repair and restore my dual monitors with proper aspect ration and resolutions on both screens?

Thanks!

[B]I was wrong to assume that I could return to TwinView.  Needing to use my computer for other things while waiting for a reply, I attempted to return to the TwinView Configuration.

Now, I can still use the left screen, however, the mouse will not move to the right screen.  The sudo Authentication window opened on the right screen, so I am unable to enter my password to facilitate the changes.  Additionally, the right monitor is now showing the 2 1/2" portion of the mythtv screen on the left side of the window instead of the right side, and since I am unable to move the mouse to the right screen anymore, I can not Al+cursor to see if it could be moved to fill the window.

Another unusual situation is that the remainder of the screen shows the right half of my normal wallpaper.  It is huge by comparison to when normal and appears to reveal the right half of a 3600x1080 screen.

Tempted to make an assumption about how to proceed, I must wait for your reply.

If this should require reinstalling Mythtv, will I be able to do it by just reinstalling the KDE Desktop, or will I have to reinstall Kubuntu?  Ouch, this is ceasing to be the fun it has been so far.[/B]

---

### Post by BicyclerBoy on 2011-12-13
It is never so bad/messed up that you can't recover..

Un-plug the big screen & reboot/logout/login..

I would backup then delete any /etc/X11/xorg.conf file. This file is not mandatory.

Using nvidia-settings...
Just get it working with one screen & twinview off & cleaned out config files; save config to xorg.conf.
Then introduce the second screen & enable in nvidia-settings; save config to xorg.conf.

The other GUI problems may be caused by kubuntu composite manager (mutter/metacity/clutter ?). I'm not sure the fancy bling desktops actually still work with separate X screens.

As NickR said: You can set the mythtv screen size in front end settings.
There can be separate size for GUI & full screen video.

MythTV could be one program that does not understand twinview metamode & then myth full screen tries to span both monitors.
Not directly useful but:
MythTV needs legacy full screen support in Unity (compiz) on Ubuntu 11.04.

---

### Post by Shabakthanai on 2011-12-13
I followed your instructions, however after re-connecting the primary monitor and booting. The computer opened with separate screens, as expected, nonetheless, the primary screen retained the 3600x1080 configuration.  I opened the mythtv frontend to change the settings from 3600x1080 to 1920x1080, but when I attempted to select the proper settings, they were not among the choices, and there were many choices.

I selected the largest settings (still somewhat below the appropriate 1920x1080 and booted again.  Same thing happened and 3600x1080 reappeared.

The boot automatically opens the computer in Mythtv and because of the 3600x1080 configuration, what appears on-screen is too large to be able to read and/or scroll to the options to open the correct configuration page, so when selecting the primary monitor, I guessed, hit the down arrow and then enter and the proper configuration screen appeared.  It is very difficult to describe what I am working with; the image is so magnified that only a small portion of any open window can be viewed.  By selecting Alt+cursor, I was able to drag the config screen to reveal the a part of the of the necessary selection to make changes.  Still after booting, the 3600x1080 remains on the primary monitor.

The 2 1/2" plazmoid analog clock I mentioned in the previous reply is now 12 1/2" high and 15 1/2 inches wide, apd pretty much fills the entire screen, so you can get an idea how large the configuration page was when I was attempting to make the changes.  None of these problems were in anyway a process of experimentation, Apparently whatever mistakes were made to create this problem are set by the computer itself in attempting to comply with the configuration I chose.  I don't know what else it could be.

The panel icons on the primary monitor measure 1 1/4" high x 1 1/2" wide.  At most I have set them at 256 when configuring the size of icons.  

Thank you for your continued patience.  I will wait for further recommendations in how to proceed.  

I am guessing the problems I am having are a bug, but I wouldn't have any idea how to present it to the authors of the program.  Would my post be of interest to them?

---

### Post by BicyclerBoy on 2011-12-14
I don't think it is a bug, the problem is that it is assumed you will use twinview & no one tested separate X screens.
The other problem is the KDE & Gnome desktop display tools do not work properly.

There are good reasons why mythbuntu uses xubuntu/Xfce..

I notice that in an earlier post you mentioned using the kde desktop display & monitor tool.
Using the gnome display tool is a big no-no with nVidia driver & I assume this is the case with kubuntu.

I am guessing that there are other config files (not xorg.conf) that are messing up your display settings.

Can you unplug the 2nd monitor & then from a terminal can you run:
sudo nvidia-xconfig 
then log out/login..

---

### Post by Shabakthanai on 2011-12-14
steven@Yeshuah:~$ sudo nvidia-xconfig
[sudo] password for steven: 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

steven@Yeshuah:~$ 

After booting, the screen that opens up is mythtvfrontend.  The content is so big that only the upper corner of the data from the open screen is showing.  I then click Esc and a window opens that has the dark green box in the center with its options, only none of options are on the screen because only the upper left corner of the green box appears.  Memory suggested that if I arrow down, the second option should shut off mythtvfrontend.  That worked.

The computer struggled to open with my regular default configuration which does not include mythtv, and finally does.  Opening the konsole I got the information provided in the first paragraph.

In /etc/X11, I have the following .org.conf files:

.txt - xorg.conf    
.txt - xorg.conf.backup This file was in my computer before you first asked me to backup the xorg.conf file in a previous reply.
.txt - sorg.conf.failsafe  I don't know how or when this document appeared.
A recycle Icon - xorg.conf.old  This file is the backup I made when you asked me to backup xorg.conf in the previous reply.
A recycle Icon - xorg.conf~  I don't know anything about this or the copies that show the recycle Icon.  By 'Icon' I mean an Icon with a triangle of green arrows creating a loop.  It may not mean recycle, however I didn't know how to explain what I am seeing any better.

**After posting the reply, I tried something else and thought the info may be helpful.  I opened the GUI 'NVIDIA X Server Settings' to disable the 'Separate X screen' and also make sure that TwinView is not ticked.  When the 'Configuration Display Device' window opened, 'Separate X screen' was highlighted, however both other choices were grayed out.  When I attempted to select 'Disabled (requires X restart), it would not accept my attempt to engage the radio button.**

---

### Post by BicyclerBoy on 2011-12-14
Separate X screens is the default setting with one display..
Twinview doesn't add anything with just one display.
Seems the driver will accept twinview enabled with just one display but in reality it does not achieve anything.

You can launch mythtv from a terminal & force/override  the GUI size..
mythfrontend --geometry 1680x1080

Then you can use the GUI & navigate to settings menu etc..

If/when using separate X screens can launch programs to either screen in menu shortcuts/launchers/scripts.
DISPLAY=":0.1" mythfrontend --geometry 1920x1080

If you have the default GUI set to 1920x1080 you only need:
DISPLAY=":0.1" mythfrontend

This overrides any 'default' settings & forces on primary screen:
DISPLAY=":0.0" mythfrontend --geometry 1680x1080


I assume you never wanted mythtv full screen across both displays..

---

### Post by Shabakthanai on 2011-12-15
Dear Bicyclerboy,

**I am sorry to have screwed up so much in my last effort.  I am so confused, I don't know how I got so far from your instruction.  I am returning to post #9; that looks like where I got off the track.**

---

### Post by Shabakthanai on 2011-12-15
Dear Bicyclerboy,

I just carefully completed your instruction #9. I disconnected  the big screen, rebooted, then logged out and back in again.  I had 3 xorg.config files and 2 (whose Icons looked like a recycle triangle with arrows representing the triangle in a clockwise fashion)which I copied to a folder that I created in my documents directory.  Then I deleted their originals from the /etc/X11/ folder.
 
I opened NVIDIA X Server and made sure that under Configuration: it was set for 'Separate X screen' and saved config to xorg.conf.  I preferred and used Kubuntu's composite manager instead of Compiz, so it remains the same now.

When I set the mythtv screen size in mythfrontend, 3600x1080 was the setting and it did not have any other options. so I suppose there is where the problem is, but it does not allow for changing the configuration.

It wasn't that way initially.  During this post, I had TV working on about 13 channels and it worked great excepting perhaps on some converted analog programs from the 50's and 60's.  Those programs were exagerated in size, not as much as they are now, but too large for the screen then.  People had the appearance of being a dwarf.  

Watching 'the Nutcracker', a ballet on PBS, when the dancers turned with arms or legs outstretched, shorter bodies had legs and arms that were twice as long as normal, and the outstretched limbs were thinner than normal.  In fact that was the reason, I created this post, if I remember correctly.

A comment was made in the #9 post as follows,"As NickR said"  You can set the mythtv screen size in front end settings.  There can be separate size for GUI & full screen video.

From there to the end of the post, you lost me.

Since writing this part of my reply, I opened 'NVIDIA X Server Settings'.  The saved settings changed again; I had no part in the changes.
 
The layout changed.  When I saved the settings, my smaller monitor was on the left; it now is on the right.  Additionally, the larger monitor is now on the left, and the saved settings for the larger monitor were 1920x1080.  Now they are 640x480.

Under the XScreen tab, 'Position'remains 'Absolute' for the larger monitor, but the small monitor is indicated as 'right of' instead of 'left of' which would have kept it in the proper position.  I don't know if that information is useful, but I have had to correct that situation each time I re-boot.

Because I am not using TwinView, I always am required to reboot after saving the configuration.  I am confident that if I correct the settings from the previous paragraph, they will go amiss again when I reboot.

I am sorry I screwed up after receiving #9.  I hope this will help get us on the right track again.  You guys are very patient with me.  It is appreciated, because I am doing my best, with the knowledge I have.  Thanks!

---

### Post by BicyclerBoy on 2011-12-15
I am sorry I ever suggested not using twinview..
I think there must be other factors interfering..
It could be that kde forces twinview on nVidia dual screens.

The original mythtv size issue was easy to fix by forcing with --geometry option and/or changing settings in frontend..

Rebooting after changing settings in nvidia-settings is not required; just logout/login..

What you wrote about losing settings when rebooting does not make sense.
If the settings go amiss after a reboot why/how do they work after the 'required' reboot (post nvidia-settings changes)?

Go back to twinview:..
How did you get twinview working originally ?
Can you get back to the original screen/display setup with twinview ?

We can fix the mythtv screen size..& twinview screen position..

---

### Post by nickrout on 2011-12-15
> **BicyclerBoy said:**
> I am sorry I ever suggested not using twinview..

I'm sorry I ever subscribed to this thread...

---

### Post by Shabakthanai on 2011-12-15
I don't  think I can return to the way it was.  For some reason, the size became extreme and never has returned to the larger size that stimulated this post.

I am sorry about your feeling of responsibility in the matter.  I can't even see how anyone can learn from what is happening.  It seems to get worse with every previously working suggestion.

You have done a fine job trying to help me.  Please do not feel the needd to continue.  Frustrating one person is enough.

Do you think it possible to remove and purge Mythtv?  If I did, what operating system should I install, and should I remove Kubuntu? 

Is mythbuntu an OS, or is it just a media addition to one of the other OS's?  If an OS, can I remove Kubuntu and install mythbuntu and probably have a smooth sailing installation?  Cheers my friend!

In my old age, a computer is more the missing person in an empty environment.  Everything that makes life more enjoyable is provided by movies and social contact with my family.  As a result having a TV seemed a good idea.  10 years without is a long time.  Just the quality of the presentation makes it more desirable.

In any event, my computer is not business support; it is simply  company, and certainly not worth the stress it is causing here.  Still, if there is a way to get it working properly, to me it would be worth the extra work.

Please release yourself from any responsibility you feel toward me and help someone where it won't be such a nightmare.  I am still extremely gratefull for the time and effort you have spent trying to help me.  I am in your debt regardless of the result.

But if the ugly task of removing and reinstalling several applications is the best solution, I would appreciate your opinion of which OS to chose.  Keep in mine, I am a retired artist, and the primary reason I don't use Ubuntu is the aesthetics.  Additionally, Kubuntu seems more configurable.  I like to inject my own preferences where possible.  Mostly though I would just like the company of a TV for the other voice in the room.

---

### Post by BicyclerBoy on 2011-12-16
We keep helping until you'll had enough not the other way round..

Get MythTV under control:
If the GUI size only affects MythTV then launch it from terminal:
exit mythtv (frontend) if running
<cntl>+<alt>+<t>
DISPLAY=":0.0" mythfrontend --geometry 1600x1000+0+0

navigate to "Utilities/setup" --> Settings --> Appearance:
Then enter values for the GUI size width & height
Tick use GUI size for TV playback

exit back out to top level menu..
You can make the screen X & Y pixel size exactly right now or just fix it later.
If the screen size 1600x1000 is too big with the current screen setup problems then reduce the size ..

DO NOT fear...the cmd line option --geometry WxH+X+Y always overrides the internal settings..

Stay with kubuntu..
mythbuntu is based on xfce desktop, you can have this installed in parallel. Xfce has no composite (I think).
It will appear as a login session option (at the greeter login screen).

After mythtv is under control we can then re-instate twinview..

We can force mythtv on the "2nd" monitor at a fixed size from the command line or in the setup screen we used above..
We use the GUI size to set W by H size & can use the GUI X & Y offsets to push mythtv off the "twinview primary monitor".

Does this make sense ?
**BUT** first thing is get mythtv started from the above cmd in terminal..

---

### Post by Shabakthanai on 2011-12-17
> **BicyclerBoy said:**
> We keep helping until you'll had enough not the other way round..[B]

I am replying in Bold to more easily separate your instructions from replies.  I hope it doesn't anger you.  I don't remember, but someone was annoyed by my using green font in my previous replies.  I only did that to make it easier to separate my words from theirs.  If that was you, I am not attempting to irritate you with the bold print, just make it easier to separate who is writing what at a glance.

I have read this post and have thought about it prior to these first words.  Strangely enough, I have been experimenting a bit thinking perhaps my last response was a bit presumptuous and that I probably lost you.  I am so grateful that is not the case.

I am again getting very interested in fixing this problem.

During my fiddling, I decided to measure to see how large my monitor would have to be to contain the image it now produces in small segments.  The measurements are not exacect, however they are pretty close.  Probably withing about 1/2 inch.

My smaller monitor has a default resolution of 16:10 and the larger 16:9.  In the 'Appearance' settings of mythbuntu, I reflected these differences in the pixel width and height.  The 1980x1020 resolution of the 16:9 monitor was not available.  The largest setting was 1920, so I used that setting and set the 1020 portion at (I believe) 894 (something like that, anyway it was the closest I could make the setting using 1020 for the larger resolution.  I then measured, as best I could the width and height of the image that was on-screen.  I used Alt+left mouse-click to move the image so that I could eventually measure the width and height of that aspect.  The Image for the 16x10 aspect screen would fit a monitor that was 41 inches wide and 26 inches high.  When I used the same correlation on the larger monitor with 16x9 aspect ratio, I found that a monitor would have to be 4 feet 6 and 1/2 inches wide and 2 feet 2 inches tall to fit that image.  So you can understand what small portion of view was showing when mythfrontend was open.

I hope this information is not irrelevant to you; it was very interesting to me.  In any event, I am sure you understand these things, while I can only theorize.  In any event, I came to a similar suspicion that perhaps modifying the pixel size for X and Y to smaller numbers might reduce the image size on the screen.  I also made similar adjustments to the numbers on the next screen, even the smaller numbers for the alternate two choices.  It seems to me that I sought numbers that might extrapolate to about a 4x2 1/2 +/- entry.

Before I did this, and after closing down mythfrontend, my larger monitor had the large resolution and the smaller monitor had the mostly normal resolution which I was able to work on adequately, but this time, after fiddling with the settings, the left monitor opened with similar large images.  The panel Icons which I show on the top of the screen are much larger and font sizes are much larger.  The print, while I am writing this appear about perhaps 20 point.  It is still workable, but not like it was previously.  And, of course, the larger monitor has the huge panel Icons as would be suited for a 4 foot + wide screen.  I feel much like I assume a scientist might feel working a similar kind of scientific problem; and, I can see how they get pleasure from science.[/B]

Get MythTV under control:
If the GUI size only affects MythTV then launch it from terminal:
exit mythtv (frontend) if running
<cntl>+<alt>+<t>

**Now that my GUI size affects both monitors, I am not confident to proceed with this portion of your instruction, and await further advice, which may differ now that both screens have larger images, even when mythfrontend is turned off.**
DISPLAY=":0.0" mythfrontend --geometry 1600x1000+0+0"DISPLAY=":0.0" mythfrontend --geometry 1600x1000+0+0

**Where will this data be shown, "DISPLAY=":0.0"......DISPLAY=":0.0""?  Will that show in the Appearance settings or in some configuration file?  My lack of knowledge and experience must be very apparent now.**



navigate to "Utilities/setup" --> Settings --> Appearance:
Then enter values for the GUI size width & height
Tick use GUI size for TV playback

exit back out to top level menu..
You can make the screen X & Y pixel size exactly right now or just fix it later.
If the screen size 1600x1000 is too big with the current screen setup problems then reduce the size ..

DO NOT fear...the cmd line option --geometry WxH+X+Y always overrides the internal settings..

**Here again, I am a bit confused, but I am hoping that I understand.  Are you saying that I should open in a terminal with the following command:  mythfrontend --geometry WxH+X+Y  ?  It is what I will try but not in Root.**

Stay with kubuntu..  **This makes me happy, I have become very fond of the Kubuntu OS.**
mythbuntu is based on xfce desktop, you can have this installed in parallel. Xfce has no composite (I think).
It will appear as a login session option (at the greeter login screen).

After mythtv is under control we can then re-instate twinview..

We can force mythtv on the "2nd" monitor at a fixed size from the command line or in the setup screen we used above..
We use the GUI size to set W by H size & can use the GUI X & Y offsets to push mythtv off the "twinview primary monitor".

Does this make sense ?  **It does, if I understand you correctly.**
**BUT** first thing is get mythtv started from the above cmd in terminal..

What I am writing here is being said because by intermingling our conversation the data has not shown up as an addition, and I have been instructed to add data.  Hope this does it.  By the way, thanks friend, I dreaded the thought of giving up.

---

### Post by Shabakthanai on 2011-12-17
I opened mythfrontend in a terminal with the perameters you recommended.  The smaller monitor opened with proper data fitting within the screen.  I set the appearance settings to 1600x1000, closed and reopened mythfrontend.  This time the different channels provided beautiful quality images, however the aspect was screwed up for all channels.

I then set the appearance settings to '0' for both W and H.  For the most part, there was normalcy in the various channels, but channel 2.1 and 2.2 were both playing the selfsame cartoon and the window aspect for the two channels was radically different.  For that reason and because other channels appeared slightly different from what I remember, I am providing probably an excessive amount of information.  I am old and my memory is not what it used to be, so proper memory of the previous TV experience may not be correct, keeping in mind it has been a long time since I had a TV and I was pretty excited and may not have noticed any specific shortcomings on any of the channels.

The dwarf-like appearance of the people that inspired the post in the first place seems to be fixed.  All channels seem to indicate appropriate proportions, with the possible exception of the cartoon that I mentioned.  On one channel the characters may have been stretched a bit vertically.  Being a cartoon, I can not be sure.

Also, the mythtv configuration page opened filling the screen with everything seemingly in the correct proportion. Here are the results of the channels on my computer TV:

2.1  Cartoon Image fills screen top to bottom with black fill on the right and left.
2.2  Exact same cartoon fill the entire screen.

7.1 & 7.2  Fill the entire screen.

16.1  Fills the screen top to bottom, but 2 1/2" of black on rt and lft
16.2  1 1/2" of black on top and bottom but fills the screen rt to lft
16.3  2 1/4" of black on rt and lft and 1 1/2" of black on top and bottom
16.4  2 1/2" of black on rt and lft but fills the screen top to bottom
16.5  2 1/2" of black on rt and lft and 1 1/2" of black on top and bottom
22.1  2 1/4" of black on rt and lft but fills the screen top to bottom
22.2  fills entire screen
45.1  4 1/4" of black on rt and lft but fills the screen top to bottom
45.2  fills the entire screen

The right monitor still retains the 3600x1080 aspect ratio.

I realize the various channels may be appropriately presented due to the combinations of yesterday-technology merging with the current technology. I just recall most channels filling the screen.  Perhaps a faulty memory.

---

### Post by Shabakthanai on 2011-12-17
Originally, when I set up mythtv and had a working TV, I was able to set configuration for TwinView and things worked fine for a while.

I did not wait for further instruction, thinking I could reset for TwinView and maybe surprise you with some help from this end.

I haven't further screwed anything up, but I wasn't able to save the changes, so I was unsuccessful.  Nonetheless, other things changed so I have to report a possible screw-up on my part.

The smaller monitor opened filling the screen appropriately.  Font configuration that had previously been set in System Settings returned to the 9 point font that is hard for this old man to read comfortably.  I am leaving it there, because I am able to use the computer and don't want to mess with configuration until mythtv is stabilized.

A current change is this:  My chosen wallpaper has returned to the larger monitor.  It is offset about 3" to the left of filling the screen, but the Image on the screen is normal again except for the offset to the left.

When I attempt to open an application, the application opens behind the wallpaper and only appears in that 3" area on the right side of the screen.  If you are familiar with the candle with the water-like flame on a gray background, you will know my Desktop.  In any event the background for the candle is an attractive gray.  The background for the 3" portion of screen that the applications open on is similar in color of gray to my wallpaper background, with the exception that it is lighter and should be a bit darker if it would appear as the background for the candle.

The panel Icons are restored to their default size, as well.

I am going to stop trying my experimenting and await your recommendations.  And, although things have changed a little more, they seem partial changes for the better.  Thanks friend for your patience.

---

### Post by BicyclerBoy on 2011-12-17
It does sound like the kde desktop is confused about the screen setup.

I have 11.04 & mythtv with gnome3-fallback, kde, ldxe desktop sessions..but I couldn't find the correct video cables to connect a 2nd monitor yet..

When you run nvidia-setings does it report you are using twinview ?
Can you drag the screens into the correct positions ?
When you select each screen (one click) does it indicate the correct resolution in the screen icon ?

Can you post the contents of the file
/var/log/Xorg.0.log

& this file
~/.nvidia-settings-rc

The aspect ratio of some broadcast material is wrong because of crude resizing to widescreen etc..The same content maybe transcoded to SD 4:3 on one channel & be 16:9 HD/SD on another..
MythTV has OSD menu options to force aspect overrides to fill/half-fill in each direction (W & H)..
But you could check the nvidia-settings: GPU-0 section/DFP-x/GPU scaling methods for each display. I use aspect ratio scaled , this way images etc look correct on any shape/size monitor.

---

### Post by Shabakthanai on 2011-12-18
> **BicyclerBoy said:**
> It does sound like the kde desktop is confused about the screen setup.

I have 11.04 & mythtv with gnome3-fallback, kde, ldxe desktop sessions..but I couldn't find the correct video cables to connect a 2nd monitor yet..

When you run nvidia-setings does it report you are using twinview ?**  It does now, I have been fiddling a little more.  In fact I may be about where I was when I started this post - with dwarflike people in shows.**
Can you drag the screens into the correct positions ?  **If I have mythtv in the large monitor, I am able to drag the screen to the smaller one again - and back.**
When you select each screen (one click) does it indicate the correct resolution in the screen icon ?  **The numbers are correct for each monitor, but actual viewing of the shows seem to be oversize and dwarflike.  Both screens now have 'Absolute' for Position:  I don't remember if that is the same.**

Can you post the contents of the file
/var/log/Xorg.0.log

[B]I couldn't copy and paste.  Each item highlights by itself, so I am typing them as they are:

OpenDocument Text
KWord document
Word document
Microsoft Word Document
Microsoft Word Document Template
Word 2007 document (macros enabled)
Word 2007 template (macros enabled)
application/x-hancomword
XML document
Lotus AmiPro document
plain test document
HTML document
WordPerfect document
Applix Words document
AbiWord document
WML document
LibreOffice Text Document
LibreOffice Text Document Template
application/vnd.sun.xml.writer.master
RTF document
Palm OS database[/B]

& this file
~/.nvidia-settings-rc

[/B]I am going to be a bit embarrassed here, because this window comes up from time to time and I don't know how to get the information that must be encrypted.  I have many things on my list to fix and this one hasn't come to the top of the list yet.  Here I go:

The title of the on-screen box is titled 'KWord's Plain Text Import Filter - KWord next is a title 'Encoding: with Recommended (UTF-8), which can be drop-down opened to reveal other choices, then centered in the box, 'End of Paragraph' then 3 radio button items, the first one ticked and are as follows:

As is:  At the end of line
Sentence:  If the end of line is the end of a sentence
Old method:  If the line is empty or has less than 40 characters

and, of course, at the bottom right corner of the options to 'OK' or 'X Cancel'

If I click OK, the contents are as follows:

#
# /home/steven/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Sun Dec 18 04:49:20 2011
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = Yes
ShowQuitDialog = No
Timer = PowerMizer_Monitor_(GPU_0),No,1000
Timer = Thermal_Monitor_(GPU_0),Yes,1000
Timer = Graphics_Card_(GPU_0),Yes,1000

# Attributes:

Yeshuah:0.0/CursorShadow=0
Yeshuah:0.0/CursorShadowAlpha=64
Yeshuah:0.0/CursorShadowRed=0
Yeshuah:0.0/CursorShadowGreen=0
Yeshuah:0.0/CursorShadowBlue=0
Yeshuah:0.0/CursorShadowXOffset=4
Yeshuah:0.0/CursorShadowYOffset=2
Yeshuah:0.0/SyncToVBlank=0
Yeshuah:0.0/LogAniso=0
Yeshuah:0.0/FSAA=0
Yeshuah:0.0/TextureSharpen=0
Yeshuah:0.0/AllowFlipping=1
Yeshuah:0.0/FSAAAppControlled=1
Yeshuah:0.0/LogAnisoAppControlled=1
Yeshuah:0.0/OpenGLImageSettings=1
Yeshuah:0.0/FSAAAppEnhanced=0
Yeshuah:0.0/RedBrightness=0.000000

Wow!  I must never have just clicked on OK and accepted the preset.  This is wonderful news.[/B]


The aspect ratio of some broadcast material is wrong because of crude resizing to widescreen etc..The same content maybe transcoded to SD 4:3 on one channel & be 16:9 HD/SD on another..
MythTV has OSD menu options to force aspect overrides to fill/half-fill in each direction (W & H)..
But you could check the nvidia-settings: GPU-0 section/DFP-x/GPU scaling methods for each display. I use aspect ratio scaled , this way images etc look correct on any shape/size monitor.[/B]

[/B]I had Stretched ticked.  I changed it to 'Aspect Ratio Scaled, now that I know what that means. (If I took a dictionary out every time I ran into a technical work I did not understand, I would still be reading the instructions for the first time I used a computer.  You have been a great teacher this day.  Thanks.  I suspect I just fixed the problem.  If so, I will make the briefest reply that it worked with my gratitude.

one character

---

### Post by Shabakthanai on 2011-12-18
It is wonderful to have a TV working again, and the use of both screens.

I don't know if because of these problem, I have a too critical eye, but the images still seem to appear dwarflike in height and stretched in width.  I changed the settings in Nvidia X Server Settings to reflect 'Aspect Ratio Scaled', and unticked 'Stretched'.

Let me ask this question?  I was looking at an ad where the seller was saying, "call this number" to contact them.  Words were off screen on both sides of the video.  Half the telephone number did not appear, so his request could not be honored.  At the same time the height seemed to be squashed a bit.  Is this an aspect ratio problem, or is the image being stretch beyond the frame of the photo?

It appears if I could get all the screen image within the vertical borders of the monitor, it would bring the image back into it's proper balance.  I guess I am confused by 'Aspect Ratio' and X and Y values in millimeters.  Would adjusting one of these values change the position of the data within the frame, and by that, if, for instance the X value was 2000 and I changed it to 1800, would it force the image to fit within the 1800 size, or would it trim off a portion of the frame and actually trim off data.  The latter is what appears to happen in my circumstance.

The width of an image looks like information is trimmed off, while the height looks like it is being crushed down.

Is there a setting that would allow me to stretch the vertical image a bit while adding back information that is trimmed off the width of an image?

I don't much like advertising, however all the ads that appear on-screen seem to have data trimmed off the width.  The logo's for the TV broadcasters is always near a border of the screen, and if the company is ABC and near the right border, the C has been trimmed.  If the first word of text is 'California', the actual screen image appears as 'lifornia' with the Ca trimmed off.

I may be being redundant here, but I am not sure I express myself accurately and attempt to reveal my thoughts in different ways to make sure I am understood.  Thanks for your continued patience.

It is such a treat having a working TV, I can still enjoy the result if it cannot be changed, and my gratitude will not be lessened if that is the case.  You forum Guru's are just plain terrific.

---

### Post by BicyclerBoy on 2011-12-18
That /var/log/Xorg.0.log is not file...don't worry about it..

The "import file filter of KWord" is an import filter for ascii text files..
KWord is not a very good editor for text files..
Next time you need to edit/create a text file use "open with" & pick gedit/kedit & tick the "always use the program".


The nVidia scaling settings are separate for each monitor, make sure you have set this for both (or just the big screen).

There are still a couple of possible fill/aspect scaling possibilities...

Some displays/TVs have overscan settings/problems **but** your big monitor is a PC monitor (I believe).

MythTV:
this has a couple of OSD menu options...fill & aspect.
Your 1920x1080 screen is a full HD 16:9 monitor.
The **aspect option** should only be needed for material with incorrectly set metadata (this does happen). 

The **fill option** allows you to fill the screen with aspect fixed scaling. This fill can be off/half/full. This can be good for widescreen material scaled for old 4:3 TVs & then broadcast on HD channels..

These menu options can be set as defaults in the frontend settings, the initial default settings should be off.

---

### Post by Shabakthanai on 2011-12-19
Previously, when I logged into the forum, I was automatically connected as Shabakthanai.  Now when I enter the forum, I am not automatically logged in.  Is this a configuration problem in my computer or a change in how you apply this forum?

I just finished a very thorough reply to the last entry.  It was difficult and a bit complicated.  When I attempted to post the reply, it was refused, and I was required to login.  I did that, however, I cannot seem to find my reply so that I can post it.

The person who was helping me, gave me information I could not confirm.  I tried to apply his instruction; where items were missing that he suggested were there, I copied the data as it is in my computer, thinking he would then see my error and put me back on tract.

Is the data lost, or how can I retrieve it?  Who should I speak with to correct what I am doing wrong.

Because I automatically was logged in previously, I have an extablished habit that it is done when I enter the site, so if it cannot be done that way anymore, I will have to create a new habit, I suppose.  For what it is worth, I much prefer the way it was over how it is now when logging in.

Additionally, this has happened before; I think it was the cause of a double posting of the same data.  A moderater pointed it out and requested I not do that.  I did not know how the double posting happened, so I was unable to change what I was doing wrong.  I am suspicious what has happened now is the same as what happened then.  So, unless my reply was posted automatically after logging in as requested, I must redo the reply.   In this case, I can only hope I get it right.  Also, I apologize if it results in a double posting of the reply that is missing.

---

### Post by Shabakthanai on 2011-12-19
> **BicyclerBoy said:**
> That /var/log/Xorg.0.log is not file...don't worry about it..

The "import file filter of KWord" is an import filter for ascii text files..
KWord is not a very good editor for text files..
Next time you need to edit/create a text file use "open with" & pick gedit/kedit & tick the "always use the program".[B]  My daughter purchased a laptop for me.  I am replying to this post on that computer.  It allows me to have 3 monitors open at the same time, which is handy in replying to this posting.  

So that we could have a functioning Skype with video, she asked that I not install any Linux OS's in the laptop.  Microsoft seems to do the video/telephone thing better than Linux.  I promised I would not change the laptop.  Love it, by the way.

Is there a Microsoft alternative application that would work better for editing?  If not, I will post from my Linux machine in the future.  Another feature of the laptop that I really like is their voice recognition software.  Missing part of a finger, I make and have to correct mistakes all the time when typing.  That doesn't happen when using voice recognition.  A small issue but handy when typing a reply.[/B]


The nVidia scaling settings are separate for each monitor, make sure you have set this for both (or just the big screen).  **I noticed and already corrected settings for both monitors.**

There are still a couple of possible fill/aspect scaling possibilities...

Some displays/TVs have overscan settings/problems **but** your big monitor is a PC monitor (I believe).  **Both of my screens are PC monitors, neither is a TV.**

MythTV:
this has a couple of OSD menu options...fill & aspect.[B]Where do I find the fill and aspect options for the on-screen display?B]
Your 1920x1080 screen is a full HD 16:9 monitor.  [B]The other is 16:10, though./B]
The **aspect option** should only be needed for material with incorrectly set metadata (this does happen). 

The **fill option** allows you to fill the screen with aspect fixed scaling. This fill can be off/half/full. This can be good for widescreen material scaled for old 4:3 TVs & then broadcast on HD channels..

These menu options can be set as defaults in the frontend settings, the initial default settings should be off.
**I couldn't find any of these menu options in the Mythfrontend configuration.**

I was apparently not logged in when I answered this post previously; this reply may be a duplicate for a more descriptive previous reply.  sorry!

---

### Post by nickrout on 2011-12-19
> **Shabakthanai said:**
> **I couldn't find any of these menu options in the Mythfrontend configuration.**stop shouting.

Most of the fill options etc are accessed during playback via an on screen menu.

Press the m key on the keyboard, or whatever key on the remote is mapped to m, and follow your nose.> 

I was apparently not logged in when I answered this post previously; this reply may be a duplicate for a more descriptive previous reply.  sorry!

---

### Post by Shabakthanai on 2011-12-20
Dear Nickout,
 
You must be the one that does not like format changes, but you have not been the one helping me.  I am not yelling and never have.  I am not trying to emphasize either.  I simply change the format to separate what Butcherboy is saying from my response, when I use 'quote' as opposed to reply.  I do that simply to draw attention to a 'quote' reply as opposed to a reply where He is stating his opinions in one post and I am replying in another.

Additionally you assume I know more than I do when it comes to using Ubuntu as well as mythbuntu.  When you complain about such a simple thing, it only makes it more difficult for me to keep up to speed with hopefully understanding.  Have I broken a post 'Rule'?  If so, I will follow your instructions.

You said, "Most of the fill options etc are accessed during playback via an on screen menu."  I don't understand what this means.  What is a fill option?  Is playback when I open 'mythfrontend' or when I have opened, for instance the 'Appearance' selection?  or Settings?  or what?

I opened Mythfrontend, then pressed 'm' as instructed and three options were provided, 'Shutdown', 'Reboot', and 'About'.  I don't see anything about 'fill options'.

I don't know what you mean by yelling, either, unless bold print is an indication of yelling.  My limited knowledge of the subject was that 'all caps' is considered yelling.  Additionally, why are the formatting options included in posting if it is improper to use those features.

I am interested in complying to all of the rules of the forum.  I do not want to do anything that would cause people to not want to help me.  I find that my lack of knowledge is unacceptable to some who help, yet I never really know when I am doing something wrong.  In this case, why did not Bicycleboy complain with my posts?  He seems the one most interested in helping me.

A fine guru named dibl has even come to my home to help me, because I have no one to communicate with about problems that occur except in the forums.  Although I don't understand why I seem to be offensive to some of you; my heart and intentions are good in all cases.  My gratitude for the help I receive is the most it can be.  And, I am doing the best that I know how.  Take a moment to list the things you want me to change or do or not do in my posts, and I will try to comply.  If you want me to terminate my inquiries, I will do that too.

---

### Post by nickrout on 2011-12-20
> **Shabakthanai said:**
> Dear Nickout,
 
 I simply change the format to separate what Butcherboy is saying from my response, when I use 'quote' as opposed to reply. just put your reply outside the quote tags, like I am doing. > 
You said, "Most of the fill options etc are accessed during playback via an on screen menu."  I don't understand what this means.  What is a fill option?  Is playback when I open 'mythfrontend' or when I have opened, for instance the 'Appearance' selection?  or Settings?  or what?

I opened Mythfrontend, then pressed 'm' as instructed and three options were provided, 'Shutdown', 'Reboot', and 'About'.  I don't see anything about 'fill options'.playback is playback, playing a video or a recorded tv programme. A fill option affects how the video/recording is stretched.

---

### Post by BicyclerBoy on 2011-12-20
The MythTV OSD menus mentioned previous are the interactive menus that are usable when running mythfrontend.
These menu are context sensitive..i.e.
Main menu:
- not much is possible exit yes no.(ignoring hot keys)
Recordings playback: 
- can pick audio stream
- can change aspect & fill
- can enable subtitles.
- enable picture-in-picture
- stuff I have forgotten..
LiveTV
- change tuner
- change channels
- etc

Hot Keys: (context sensistive as well)
Recording playback or LiveTV:
There are many, if using a keyboard:
- "i"  information
- "p"  pause/play
- "s"  jump to scheduler (<ESC> to return)
- <space> or <return> save a bookmark
- navigate with cursor keys..

The ubuntu forum allows you to set the browser to auto-logon but it still times-out the session. If you are just reading posts you will not notice. But if you are in the middle of editing a post, this session time-out after no activity & re-login will result in loss of data.
I copy the text to 'clipboard' if I suspect time-out..

---

### Post by Shabakthanai on 2011-12-21
> **nickrout said:**
> just put your reply outside the quote tags, like I am doing. playback is playback, playing a video or a recorded tv programme. A fill option affects how the video/recording is stretched.Wow, I never noticed how this works.  I suppose I should feel stupid, however, I just feel grateful.  If ever this was explained to me before, I must not have understood.  Thanks!

---

### Post by nickrout on 2011-12-21
> **Shabakthanai said:**
> Wow, I never noticed how this works.  I suppose I should feel stupid, however, I just feel grateful.  If ever this was explained to me before, I must not have understood.  Thanks!No problems, good luck with mythtv.

I must say if you had a separate computer just with mythtv attached to one tv/monitor, it would all have been easier, good on you for persevering.

---

### Post by Shabakthanai on 2011-12-22
> **BicyclerBoy said:**
> The MythTV OSD menus mentioned previous are the interactive menus that are usable when running mythfrontend.
These menu are context sensitive..i.e.
Main menu:
- not much is possible exit yes no.(ignoring hot keys)
Recordings playback: 
- can pick audio stream
- can change aspect & fill
- can enable subtitles.
- enable picture-in-picture
- stuff I have forgotten..
LiveTV
- change tuner
- change channels
- etc

Hot Keys: (context sensistive as well)
Recording playback or LiveTV:
There are many, if using a keyboard:
- "i"  information
- "p"  pause/play
- "s"  jump to scheduler (<ESC> to return)
- <space> or <return> save a bookmark
- navigate with cursor keys..

The ubuntu forum allows you to set the browser to auto-logon but it still times-out the session. If you are just reading posts you will not notice. But if you are in the middle of editing a post, this session time-out after no activity & re-login will result in loss of data.
I copy the text to 'clipboard' if I suspect time-out..Thanks, I can live with it either way.

I am confused on what to do next.  I have the mythtv configuration where I can see a TV program again, but it is about the same now as when I started the very first post on the subject.

Is 'Manage Recordings' what you mean when you say, 'Recordings Playback:'?  I am still unable to find anything that relates to an option for 'change aspect and fill'.  

When I open 'Appearance', and attempt to set GUI width and GUI height, the maximum GUI width I can select in pixels is 1920, and my primary monitor is 1980x1020.  I have wondered if that may be my problem.  But when I set it at '0' to get a default setting, everything ends up either too large or dwarflike for the people on screen.

The next screen provides me with further confusion, because if I select 'Separate video modes for GUI and TV playback, I haven't the foggiest idea what the settings should be for 'GUI:' or 'Video output', and for 'Overrides for specific video sizes, I don't know what settings to choose.

Is this where I should be changing 'aspect and fill' settings?  Can you help me with this?

Is my problem happening because I have 2 monitors with differing aspect ratios?  one is 16x10 the other is 16x9.

---

### Post by nickrout on 2011-12-22
> **Shabakthanai said:**
> Thanks, I can live with it either way.

I am confused on what to do next.  I have the mythtv configuration where I can see a TV program again, but it is about the same now as when I started the very first post on the subject.

Is 'Manage Recordings' what you mean when you say, 'Recordings Playback:'?  I am still unable to find anything that relates to an option for 'change aspect and fill'.
when you are playing video on the screen (either LiveTV, a recording (ie a programme you recorded yesterday and are watching now) you press the m key and a menu pops up on the screen. press the down arrow until you get to video and press enter, there are your options.

Have you actually read [http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index) ?> 

When I open 'Appearance', and attempt to set GUI width and GUI height, the maximum GUI width I can select in pixels is 1920, and my primary monitor is 1980x1020.  I have wondered if that may be my problem.  But when I set it at '0' to get a default setting, everything ends up either too large or dwarflike for the people on screen.

The next screen provides me with further confusion, because if I select 'Separate video modes for GUI and TV playback, I haven't the foggiest idea what the settings should be for 'GUI:' or 'Video output', and for 'Overrides for specific video sizes, I don't know what settings to choose.

Is this where I should be changing 'aspect and fill' settings?  Can you help me with this?

Is my problem happening because I have 2 monitors with differing aspect ratios?  one is 16x10 the other is 16x9.

That won't make that much diffference.

---

### Post by Shabakthanai on 2011-12-23
Thank you friend.  I believe this is the solution for my problem.  I have attempted many different options and have had interesting results.  Finally the images appear in balance with reality.  I still have a small problem, that I believe will probably resolve when I have become comfortable with the options. 

It appears that while in balance with relation to the width and height of items, portions of each frame in both height and width are missing from the picture.  As a consequence, when written material is presented on screen, letters and numbers may be missing at the beginning and ending of a sentence.  Additionally, sometimes the tops of the heads of individual are trimmed a bit.  It is as though the image has been magnified and spills past the height and width of the screen.  Nevertheless, these are problems that do not bother me too much.  At least the people are not dwarf-like, unless they are images of real dwarfs.

One thing is apparent, though, and that is if I set the aspect ratio as 16:9, which is the aspect of my primary monitor, there is black fill on the top and the bottom of the image.  To resolve this problem, I simply have stretched the image vertically and it then fills the screen.

It will probably take me quite a while to become comfortable with all the configuration opportunities, but at least I can see success as the result.  Thanks so very much for the help.

I see the problem as sufficiently resolved.

---

### Post by BicyclerBoy on 2012-01-04
Please note that your primary monitor resolution is: 
1920 (W) x 1080 (H)
please don't do anything rash...

---

