---
title: "All video players failing with Gutsy"
date: 2008-01-16
forum: Multimedia &amp; Video
---

### Post by wheezer on 2008-01-16
I upgraded to Gutsy and mplayer fails complately, It opens and closes instantly.  I ran from terminal, and these were the errors.   VCL does somehing almost as bad. It plays, but the image is outsde the frame of the player

Can some guru tell me what the clue is here?  Thanks


matt$ mplayer 2.mpg

MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 2.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG1  320x240  (aspect 1)  30.000 fps  590.0 kbps (73.8 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 320 x 240 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 1 ch, s16le, 32.0 kbit/4.54% (ratio: 4000->88200)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 320x240 => 320x240 Planar YV12 
Cannot sync MAD frame: -0.010 ct: -0.449 208/208  1%  0%  0.7% 0 0 
Cannot sync MAD frame
Cannot sync MAD frame: -0.010 ct: -0.450 209/209  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.010 ct: -0.451 210/210  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.010 ct: -0.452 211/211  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.010 ct: -0.453 212/212  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.010 ct: -0.454 213/213  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.010 ct: -0.455 214/214  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.010 ct: -0.456 215/215  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.010 ct: -0.457 216/216  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.010 ct: -0.458 217/217  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.010 ct: -0.459 218/218  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.318 ct: -0.462 219/219  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.318 ct: -0.465 220/220  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.318 ct: -0.469 221/221  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.318 ct: -0.472 222/222  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.318 ct: -0.475 223/223  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.318 ct: -0.479 224/224  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.318 ct: -0.482 225/225  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.318 ct: -0.485 226/226  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.318 ct: -0.489 227/227  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.344 ct: -0.492 228/228  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.652 ct: -0.495 229/229  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.652 ct: -0.499 230/230  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.652 ct: -0.502 231/231  1%  0%  0.7% 0 0 
Cannot sync MAD frame: -0.652 ct: -0.505 232/232  1%  0%  0.6% 0 0 
Cannot sync MAD frame: -0.652 ct: -0.509 233/233  1%  0%  0.6% 0 0 
Cannot sync MAD frame: -0.652 ct: -0.512 234/234  1%  0%  0.6% 0 0 
Cannot sync MAD frame: -0.652 ct: -0.515 235/235  1%  0%  0.6% 0 0 
Cannot sync MAD frame: -0.652 ct: -0.519 236/236  1%  0%  0.6% 0 0 
Cannot sync MAD frame: -0.652 ct: -0.522 237/237  1%  0%  0.6% 0 0 
Cannot sync MAD frame: -0.677 ct: -0.525 238/238  1%  0%  0.6% 0 0 
Cannot sync MAD frame: -0.985 ct: -0.529 239/239  1%  0%  0.6% 0 0 
Cannot sync MAD frame: -0.985 ct: -0.532 240/240  1%  0%  0.6% 0 0 
Cannot sync MAD frame: -0.985 ct: -0.535 241/241  1%  0%  0.6% 0 0 
Cannot sync MAD frame: -0.985 ct: -0.539 242/242  1%  0%  0.6% 0 0 
Cannot sync MAD frame: -0.985 ct: -0.542 243/243  1%  0%  0.6% 0 0 
Cannot sync MAD frame: -0.985 ct: -0.545 244/244  1%  0%  0.6% 0 0 
Cannot sync MAD frame: -0.985 ct: -0.549 245/245  1%  0%  0.6% 0 0 
A:   7.7 V:   8.7 A-V: -0.985 ct: -0.552 245/245  1%  0%  0.6% 0 0 
gnome_screensaver_control()
Exiting... (End of file)
matt $

---

### Post by nexu56 on 2008-01-16
I have similar problems on some machines when compiz is running. Have you tried disabling desktop effects, if they are on?

---

### Post by wheezer on 2008-01-16
> **nexu56 said:**
> I have similar problems on some machines when compiz is running. Have you tried disabling desktop effects, if they are on?

All my "Desktop effects" are set to none. 
I am very frustrated. Any other ideas?

---

### Post by revoltism on 2008-01-16
Have installed through synaptic or compiled it by your self? You could try reinstall through synaptic.. is this error happening with all your movies?

---

### Post by wheezer on 2008-01-16
> **revoltism said:**
> Have installed through synaptic or compiled it by your self?

Synaptic. Don't know how to compile myself.

---

### Post by revoltism on 2008-01-16
You could try reinstall through synaptic.. is this error happening with all your movies?

---

### Post by frodon on 2008-01-16
Have you installed all the needed codecs ?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by revoltism on 2008-01-16
It could maybe be some codec issue.. what happens when you open mplayer from the menu not nautilus?

---

### Post by revoltism on 2008-01-16
I need to run mplayer with the x11 video setting

---

### Post by wheezer on 2008-01-16
> **revoltism said:**
> It could maybe be some codec issue.. what happens when you open mplayer from the menu not nautilus?

I resintalled mplayer again (2nd time)

NOw i get a differnet error

"Error opening/intializing the selected video_out (-vo) device"

????

PS
What is "x11 setting?"

---

### Post by wheezer on 2008-01-16
> **revoltism said:**
> It could maybe be some codec issue.. what happens when you open mplayer from the menu not nautilus?

When I open latest install from Menu, the player window opens, and the toolbar opens, but then the message appears.  The audio starts playing. No video at all

---

### Post by revoltism on 2008-01-16
sorry.. i didn't know how to explain that cause i'm sitting at my work right now and not infron of my computer... 

You can in the video settings of mplayer choose diffrent "codecs" i think normaly it's set to "xv" i had to change that to "xv11" to be able to see movies..

That last error though seems to point to some problem with your graphic card.. strange..

---

### Post by wheezer on 2008-01-16
> **revoltism said:**
> sorry.. i didn't know how to explain that cause i'm sitting at my work right now and not infron of my computer... 

You can in the video settings of mplayer choose diffrent "codecs" i think normaly it's set to "xv" i had to change that to "xv11" to be able to see movies..

That last error though seems to point to some problem with your graphic card.. strange..

THe interface that shows up, has no settings menu at all.  Just the video player buttons.  Now wait through the GUI at all

---

### Post by revoltism on 2008-01-16
you need to right click to get to the settings

---

### Post by wheezer on 2008-01-16
Well, ok.  That get things playing/

But the player window  is separate from the buttons that control the player. That was NOT how my old setup worked.  There was one integrated windown with buttons at the bottom, and a playlist on the side.

I have never been clear on what is mPlayer, MoviePlayer and Totem.  They seem to all use the same name.  

I also need the mozilla plug it again. Is that ONLY totem? Only movie player?  I just don't get the distinctions.

Are they completely different? Is one obsolete? Do they need each other?  I just don't get it.  Can you explain what might give me back my unified, single interface window?



Thanks for help. Greatly appreciate it

---

### Post by wheezer on 2008-01-16
Wait

It worked once when I right clicked and changed the settings to x11, but it keeps reverting back after each play.  I cannot open from nautilus.  How can I save the X11 setting?

THis is just clear as mud

---

### Post by wheezer on 2008-01-16
Ok.. I changed to another X11 setting, and now it sticks.   But the windows don't scale the video, as they used to.  This is just not the application I once used.  Perhaps the integrated window with pls playlist files was Totem????? 


In Mplayer, My Mux Codec familes are all "none"  Should this be the setting, or should i be choosing one?

ARGGGGGGGGGGG
Not only can I not resize anything, but all the AVIs are reversed. Literally, the images are flipped

---

### Post by eye208 on 2008-01-16
If X11 is the only video output that works for you, then your graphics driver is not configured properly. I guess you are using ATI's proprietary driver as it's the only one that ships with XVideo disabled by default. XVideo is required for hardware-accelerated video playback (anti-aliased scaling, separate contrast/brightness/saturation control). To enable XVideo with this driver, run the following command once:

sudo aticonfig --ovt Xv

---

### Post by wheezer on 2008-01-16
Ok

THe flipping is solved. Somehow a "flip image": setting was checked. I didn't do it. 
Anyway..
Now I guess the video codecs are wrong because the video quality is pretty poor. So which  of the dozens to i choose?

---

### Post by wheezer on 2008-01-16
> **eye208 said:**
> If X11 is the only video output that works for you, then your graphics driver is not configured properly. I guess you are using ATI's proprietary driver as it's the only one that ships with XVideo disabled by default. XVideo is required for hardware-accelerated video playback (anti-aliased scaling, separate contrast/brightness/saturation control). To enable XVideo with this driver, run the following command once:

sudo aticonfig --ovt Xv

I could not originally get the ATI driver to work.  So I tried the open source version Fglrx???   That didn't seem to work when I "tested" it, but when I just accepted the resolution, it worked.  I never tried just accepting the ATI commercial version.   Should  I have tried that?  Should I got back and use the ATI driver?

---

### Post by wheezer on 2008-01-16
Well.. it seems the player i was always using was Totem's "Movie player" That is the single interface I was using.   But now it's simply opens and closes instantly (I installed the xine version)

I am so frustrated. I the problem just that ATI sucks? Should I throw out this damn card and get an NVIDEA?  What is my best, least problematic choice for Ubuntu?

---

### Post by revoltism on 2008-01-16
I also are running ATI why i recognize your problems =)

I used Envy ([http://albertomilone.com/index.html](http://albertomilone.com/index.html)) to install my ATI-drivers and now it works perfectly.. also compiz-fusion does 

And yes.. i think you tried Totem before and i'm not sure but believe xine is better than gstream.. generally VLC and Mplayer is better than Totem according to my believes

---

### Post by wheezer on 2008-01-16
I just came across ENVY.  SO it works?  It will save this X1600 ATI card? I was just about to scrap all this and get an NVIDEA

Just run the debian package installer?  His instructions are a bit vague

---

### Post by revoltism on 2008-01-16
yeah.. after you will find Envy in your menu and it will probably work it  did so for my x1950 card. I checked the ATI homepage and it's the same driver you use for your x1600 as i do =)

---

### Post by revoltism on 2008-01-16
oh.. and of course you will need to follow the wizard which Envy pretty much is..

---

### Post by wheezer on 2008-01-16
Well.. some progress

Envy seemed to work... but it used the open Source Fgxlr driver!! I thought the whole idea was it would install the REAL ATI drivers

But anyway, 

1 )totem now works, but there is some distortion at the bottom of all videos (a band of noise at the bottom, and overall, the quality is less than stellar.  Are their codecs and configs i should be using?

2) VCL not longer works now. It opens, but will not show any video. I wanted to see if the quality was better.

Can you tell me what your key settings are for both Totem and VCL?  Perhaps if I copy you, i can get it to work

Thanks for all your help. This is farther than I've gotten before

---

### Post by revoltism on 2008-01-16
lol, no problem.. then you will need to wait until i get home from work as i can't remember it exactly =)

in the mean time If you find to set ffdshow codecs somewhere in the settings i think that might help in VLC.. Totem is very simple and i don't think you can change anything in the gui so i'm not sure how..

---

### Post by wheezer on 2008-01-16
I ran Envy with my ATI 1600, and it installed the open source fxlgr driver.  I then went back and checked the instructions, and realzied i had not enabled the multverse repositories. 

Should I try reinstalling envy to see if it will use the real ATI drivers?  Do I need to uninstall envy first?

---

### Post by wheezer on 2008-01-16
Well, I reinstalled VCL.. it seems that it fails to open if i open from a windows drive (via samba).  It always worked doing that in Feisty.

ANd VLC quality just sucks. Multi-hue and grainy. Unwatchable. Obviously, something is off somewhere. Any ideas?

---

### Post by wheezer on 2008-01-16
UPDATE

Now I am down to one problem

I installed totem-mozila, thinking it would fix a complete corrupt what Totem played.

It did..but after a reboot, I think get a complete black dispay. Audio,m but not video

Is there a right way to install Totem

This has been a nightmare. 

An entire day, to upgrade from Feisty.  I warn anyone planning this, if you have ATI card, you could be in for a struggle

HEEEEEEEEEEEELP!

---

### Post by nexu56 on 2008-01-16
If you only have a black screen, you're going to have to fix things from a command line (either that or reinstall from scratch)

You can get to a command line if you reboot and select "recovery mode" from grub options.

There is a great walkthrough for installing ATI drivers here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

But yes, I personally avoid ATI for these exact reasons!

---

### Post by eye208 on 2008-01-17
Just a word of warning: Switching to Nvidia will not magically solve all your problems. In fact the Nvidia driver that comes with Gutsy is full of bugs: XVideo sometimes fails to work (You have to switch to the text console and back to fix it.), enabling anti-aliasing will cause all kinds of crashes and/or freezing. I switched from ATI to Nvidia, but fglrx was indeed more stable.

Of course I know you all can't live without desktop effects, so my words will probably fall on deaf ears, but anyway: If you want a painless experience, install fglrx using the Restricted Drivers Manager, run "sudo aticonfig --ovt Xv" to enable XVideo, and use Metacity instead of Compiz. This way you will have direct rendering in OpenGL apps and smooth, non-pixelated video playback with all media players.

---

### Post by revoltism on 2008-01-17
Yes, you are probably true.. but for me i can live with a bit choppiness as long as i have a working Compiz =)

I have discovered that not all movies works by switching to the xv11 setting and i took some time yesterday to try solve it but still not any luck..

---

### Post by wheezer on 2008-01-18
> **nexu56 said:**
> If you only have a black screen, you're going to have to fix things from a command line (either that or reinstall from scratch)

You can get to a command line if you reboot and select "recovery mode" from grub options.

There is a great walkthrough for installing ATI drivers here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

But yes, I personally avoid ATI for these exact reasons!


Thanks.  I've just reinstalled gutsy from scratch. Clean install. Fixed most problems, but ATI not running special effects, but at least it's running 1680X 1050. 
It is just amazing. Someone should create a banner saying IF YOU HAVE AN ATI CARD, junk it! LINUX HATES IT.


The only issue i now have is that sometimes Totem refuses to exist full screen.

ANyone that thinks these video players even comes close to something like Windows Media player is smoking something.  And what i fear is that without any commercial incentive, no one is ever going to make anything better.  Why people think VLC is much better, i have no idea. I hate it.
Thanks for help!

---

### Post by eye208 on 2008-01-18
> **wheezer said:**
> ANyone that thinks these video players even comes close to something like Windows Media player is smoking something.
If you consider Windows Media Player any good then clearly you must be smoking something.

> Why people think VLC is much better, i have no idea. I hate it.
People prefer VLC and MPlayer because these work when all the others fail. That applies to both Linux and Windows.

OK, you did a clean install. That's good because now we have a well-defined starting point. Please post your xorg.conf so we can see which driver and settings you're actually using. I found it quite confusing when several times you mentioned an "open source fglrx" which, to the best of my knowledge, doesn't exist.

fglrx = closed source
ati = open source

I successfully installed the proprietary ATI drivers on several computers, i.e. in a way which made video playback a non-issue. And that wasn't even hard to do. I just used Ubuntu's "Restricted Drivers Manager", then ran "sudo aticonfig --ovt Xv" to enable XVideo. I did NOT use Compiz. With the current state of the ATI driver you have to choose between smooth video playback and desktop effects. You can't have both. Sorry, but that's just the way it is. If you desperately want both, ditch your card and switch to Nvidia. They will give you a different set of bugs which may or may not be easier to work around.

---

