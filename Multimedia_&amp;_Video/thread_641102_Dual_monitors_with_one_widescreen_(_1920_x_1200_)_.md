---
title: "Dual monitors with one widescreen ( 1920 x 1200 ) with intel 945 video card on Feisty"
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by mobiusdim on 2007-12-15
I signed up just to post this. It has been a harrowing three days to say the least and I would like to save someone ..anyone, out there the trouble I went through. The question is, if you just bought a widescreen monitor with a resolution that's around the 1920 x 1200 range, will you be able to hook it up to your laptop with an intel 945 GM card and use both the monitors in a dual monitor (xinerama) type of setup. The answer is ...(drumroll)..yes in Gutsy and most probably not (at least to my knowledge) in Feisty. Apologies to those who have been disappointed by the answer but that's been my experience, unless you are proficient enough to mod the i810 driver or the new intel driver (xserver-xorg-video-intel). I will briefly go through the events that led me to these conclusions and hopefully that will save you some time.

I will specifically speak of the 1920x1200 resolution here since lower resolutions like  (1600 x 1200 ) seem to work in Feisty with i810 driver and 915 resolution and the familiar mods to the xorg.conf file. But let me take a step back for the benefit of those who don't know these terms. 

The problem with widescreen resolutions is twofold , Firstly, it is a non standard size (note that the intel 945 GM card has in its VBIOS the 1920 x 1440 mode but  not the 1920 x 1200 ). In order to obtain this/any  non-standard resolution , we need to hack the available modes. 915resolution is the standard program used to do this. One can find umpteen number of guides to install and use 915resolution so I won't be going into that. Once you have the program running, you can choose some available mode that you are sure you will never need and change it to a new mode depending on your specific needs , for example the command 

sudo 915resolution 30 1900 1200 

changes the mode named 30 which on the intel 945 card is 640 x 480 and hacks it to 1920 x 1200. A word of caution though,  although 915resolution can hack any existing mode to any desired mode, actually getting it to work has been known to be slightly probabilitic. Sometimes you might have to choose to change a mode that's close to the desired hack before your i810 driver makes your card start pumping out the right resolution. Now, if you only desire to get display on a widescreen (1920 x 1200) screen then you can get the new intel driver (xserver-xorg-video-intel) to do the trick for you. i810 driver might be able to do this too but I have not been able to get anything beyond 1600 x 1200 from it.
 
Secondly, we also want a dual monitor system (xinerama style) not just a widescreen on one monitor ...right. This is where it gets tough . With all the usual mods in the xorg.conf file (i.e. dual Device/Screen/Monitor sections, MonitorLayout option Screen lines in the  Device section, Screen lines from the ServerLayout section,  RightOf/LeftOf indication in the in ServerLayout section, Modelines in the Monitor Section, the famed Xinerama Option ) it doesn't work . Why ? well it seems to me, there is some absurd limitation in the i810 driver which causes it to balk, when asked to provide any resolutions in the range of 1920 x 1200. This is signalled by the "Not using mode 1920 x 1200 (no mode this name) " message in the Xorg.0.log files in /var/log. Then the driver belts out messages about how its going to use the "Built in Modes" and reverts to some wretchedly handicapped resolution modes like 800 x 600 , 1204 x 768 or even 640 x 480. Even performing the seemingly insane hack of changing all the modes of your card using 915resolution into 1920 x 1200 ( knowing that sometimes the i810 driver tries to escape using the desired mode by choosing a lower mode ) doesn't ameliorate the situation. Infact if you change all the modes into 1920 x 1200 , the Xorg.0.log file shows a "set VBE failed" error and your are left stranded in the text mode (incidentally you can also get this message if your ScreenLayout  "CRT,LFP" is written as "LFP,LFP" or anything else that doesn't start with a CRT, I thought this was weird since my external monitor is not a Cathode Ray Tube  but an LFP but I guess CRT is being used in the loose sense of the word as any external monitor).  Anyways, so you can't make this "not using mode 1920 x 1200" message go away and you can't get a widescreen 1920 x 1200 dual monitor in xinerama mode. What you do get is a xinerama mode with two 1204 x 768 screens even though the resolution on the widescreen is marked as 1600 x 1200 ( it is not, the 1600 x 1200 entry in the System -> Preferences -> Resolution  is not accurate). 

  Ok, well what do you do now.. try the intel driver, turns out the intel driver is great in resolving widescreen issues but is absolutely hopeless in getting dual monitors set up working. It did although work right out of the box when I tried to get native resolution on only the widescreen. Another note of caution, make sure that you understand how the toggle CRT/Local Screen comibnation keys (on my tablet it is Fn+F5) functions on your computer. If you plan to test only one screen you should make sure using this combination key and toggle only that screen that is desired to be active before X starts (which happens a little after the "Configuring Network interfaces" step). Sometimes you might have to go into the BIOS and  change options there in order to only activate local screen/external screen on power up, I had to use this on my tablet (toshiba m405). If you don't understand the importance of this toggle key , you testing might not  reflect accurate results. 

So what is one to do on Ubuntu Feisty for this problem ? i810 cannot give you the required widescreen resolution on a single monitor, let alone a xinerama dual monitor setup and intel is dual monitor handicapped . Turns out there is a new version of XRandR (1.2) that comes that can help . It makes making on-the-fly changes to display, a trivial job (the way it should really be in the year 2007)...but alas...it's not yet available for Feisty ( you could try to install it yourself) . Hence I concluded that unless someone takes a look into this murky error messages in the Xorg.0.log file and figures out why i810 puts an artificial limitation on the resolution range or somehow makes the intel driver more dual monitor friendly on Fiesty or  unless XRandr 1.2 is released for Feisty, there is no known (read sane) way of getting this kind of setup in Fiesty. 

Now the good news for me was , that during the installation of Ubuntu , I had separated my data (/home) and / mount points into separate partitions and had an extra free space partition for trying out new OS versions if I was ever interested in ( I am so glad I did that ) ...so I installed Gutsy ...making sure that the GRUB was installed in the / of Gutsy (the partition ID was sda5 and hence I used hd(0,4) to indicate the partition to install GRUB) and it was a breeze may I add. Gutsy even migrated some of my options for my user and i still have access to all the data from my /home partition. After installing Gutsy  ( which came with the intel driver pre-installed although it says its experimental ?) I connected both my monitors , I did

Xserver - Dpkg-Reconfigure xserver-xorg

which generated a new xorg.conf and then added ....check this out ..one line ..that's right one line to the Display Section.

virtual 2048 2048 

and that was that . Well I added a couple of  additional lines to indicate that no TV was connected but that was all it took. And upon restarting Xwindows , I had both the screens at native resolutions , I used a couple of commands to indicate the positions of my VGA and local screeen (called LVDS) and bingo ....I am in xinerama'ish dual monitor-widescreen heaven ...you've gotta be kidding me !!!...

(check this site out for instructions [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2))

After a ton of mods to the xorg.conf, and trying on different drivers , trying to parse the Xorg.0.log file,  this seemed to be a cruel joke but at least I am no longer embarrassed in front of my windows friends.


BTW ,  I strongly recommend using a fresh automatically generated xorg.conf file as shown above. 

 Sorry for not adding the old xorg.conf and the log files from the experiments in Feisty but I no longer have them (since these are updated every time X starts ) and I don't have the motivation to recreate the entire scenario again.

Hope this helps somebody.

---

### Post by mobiusdim on 2007-12-15
Oh forgot to mention that when I tried to do a similar procedure using i810 and get dual monitor setup with my office monitor ( 1600 x 1200, one of the modes in the VBIOS of the intel card) it worked immediately without any problems. This fact in addition to all other above mentioned events led me to conclude that getting a widescreen resolution in the range of 1920 x 1200 with i810 on an intel 945 gm card is probably not possible in a regular installation of Feisty without XRandr 1.2.


hope this helped someone

---

