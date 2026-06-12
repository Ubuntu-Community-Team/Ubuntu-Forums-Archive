---
title: "ati hd 3200 problem..."
date: 2008-08-31
forum: Mythbuntu
---

### Post by juicestain on 2008-08-31
I've installed/uninstalled the ATI drivers multiple times and have the same results. When I start up the frontend or backend, The menu is displayed with horrible distortion. It's as if the picture is made up of a horizontal puzzle pieces, and the pieces are all mixed up. When I click watch tv, the video and audio play smoothly, however its the same puzzle looking display. 

(sorry i really don't know how to describe it.)

If I run the frontend or backend without the drivers installed, i get the menu working fine. But when i click Watch TV, the video and audio stutter.

Is there a way to take a screenshot of the menu and whatnot so i can upload it to the forums? I've installed KSnapshot, but if i try ctrl+alt+tab to bring it up, nothing happens.

Any help would be appreciated

---

### Post by juicestain on 2008-08-31
heres a pic of what it looks like.

I tried changing the painter from qt to opengl after and i get a functional menu... but when i hit watch tv the menu stays and I only hear sound.

any ideas?

---

### Post by JugeHuge on 2008-09-01
I think that you get wrong refresh rates from your tv.
try to find correct ones and edit them to xorg.conf. 
btw. how do you have tv connected your to ati?? HDMI??

---

### Post by juicestain on 2008-09-02
I've tried both HDMI and VGA. I chose not to use HDMI because i couldn't get alsamixer to utilize iec958. It's been quite the frustrating process. hehe

How do i edit refresh rates in the xorg.conf file?

---

### Post by JugeHuge on 2008-09-02
Hello.. here is guide..
[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973")

It's not actually hard to get through HDMI once you find proper guide... Took me about 2 months to get it working properly..  :)

Here is what i used to get HDMI audio working: [No sound over HDMI with ga-ma78gm-s2h AMD 780G motherboard]("http://www.gossamer-threads.com/lists/mythtv/users/333112#333112")

---

### Post by juicestain on 2008-09-02
2 months?!?! haha I guess i'll need more excuses to tell the wife. 

Thanks for all your help!

---

### Post by netslacker on 2008-09-02
This also looks similar to a known problem with the Bob deinterlacer.  You may want to try changing the video playback profile to CPU- or something less than what it is.

For the record, there are many issues with ATI 3200 video cards and linux, just search around and you will see (myself included).  Ultimately, many of us just opted for a cheap nVidia card to get around the myriad of ATI issues.

---

### Post by JugeHuge on 2008-09-03
netslacker: did you check that picture?? it's taken from menu screen.. No de-interlacers active in menu.. :)

juicestain: Said badly.. tried 2 months to get HDMI working on all players until found that guide. Took about half hour to get it work after then.

---

### Post by xykevinr on 2008-09-03
I really dont think this is an interlacing problem - at least its not that simple.

Try this - Remove/disable the ATI drivers, go through the menus (veerrry slowly) and select the option to run the frontend in a window (or presumably you can do this direct in the database if you feel like it). Then enable ATI drivers again, I think you'll find it'll work without the stupidness. Not really a solution I know - but at least a bit more useable.

I've seen two places on the web where people apparently have this working, but with no details. I've seen more with screenshots like yours.

This below might be a link to me asking the a similar question to you for a specific motherboard.

[http://ubuntuforums.org/showthread.php?t=908628](http://ubuntuforums.org/showthread.php?t=908628)

Finally I have a picture very similar to yours, I'm using a monitor with a standard VGA cable.

Kev

---

### Post by JugeHuge on 2008-09-03
I have Asus M3A78-EMH HDMI with 780G chipset which have integrated HD3200.

Don't use Catalyst 8.6, 8.7 and 8.8 drivers.. At least what i have tried. It will cause mosaic effect on mythtv menu or shows menu but no submenus.

i would suggest that you use repository fglrx driver.. it has it flaws also but currently it works best.

Good installation guide for ATI
[ATI Ubuntu Hardy Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

---

### Post by juicestain on 2008-09-03
Ok I have been researching and testing xorg configurations and am still stumped. My television is a Samsung ln-t4069f with a refresh rate of 120hz. And after a few black screens, I'm back here with my xorg.conf code.

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

Any ideas? Or links to where i'll be able to understand this?

---

### Post by JugeHuge on 2008-09-04
I would suggest that you try with HDMI and try first at 1280x720 resolution with different refresh rates. If you get that working properly. Then try to get it work 1920x1080 resolution with different refresh rates.

First try to get repository fglrx driver to work properly.

Then from xfce settings try to change correct resolution or amdcccle.

your tv might not response correct EDID data.

find this which might help you: [Samsung LNT4069 connecting to a laptop]("http://www.digitalhome.ca/forum/showthread.php?t=89899")

---

### Post by bml137 on 2008-09-05
I know when I let MythTV frontend go full screen (1920x1080), it is messed up like that.  When I change the MythTV frontend resolution to specifically 1920x1080 (instead of autodetect using 0x0), I have the same problem.  When I change it to 1919x1080, it works perfect.

---

### Post by Pegel03 on 2008-09-06
> **JugeHuge said:**
> 
juicestain: Said badly.. tried 2 months to get HDMI working on all players until found that guide. Took about half hour to get it work after then.

Can somebody please point me to that guide? I'm running out of excuses...
Thanks.

---

### Post by juicestain on 2008-09-06
> I know when I let MythTV frontend go full screen (1920x1080), it is messed up like that. When I change the MythTV frontend resolution to specifically 1920x1080 (instead of autodetect using 0x0), I have the same problem. When I change it to 1919x1080, it works perfect.

That worked!!! Now all i gotta do is work on the overscan and the toolbar showing on the top of the screen and i'm done!

Thank you!

---

### Post by JugeHuge on 2008-09-08
> **Pegel03 said:**
> Can somebody please point me to that guide? I'm running out of excuses...
Thanks.

Hello..

[http://ubuntuforums.org/showpost.php?p=5711698&postcount=5]("http://ubuntuforums.org/showpost.php?p=5711698&postcount=5")

---

### Post by Pegel03 on 2008-09-08
Thanks for the effort, but found that one. I's not the sound (yet) i'm having problems with. But the video over HDMI itself. I did some googeling, onestly i did:)
Will try to install Catalyst 8.8 again, but now with tv attached i.s.o. a lcd screen. See if that will work.

---

### Post by JugeHuge on 2008-09-09
I have said this earlier.
Don't use Catalyst 8.6, 8.7 and 8.8 drivers.. At least what i have tried. It will cause mosaic effect on mythtv menu or shows menu but no submenus.

i would suggest that you use repository fglrx driver.. it has it flaws also but currently it works best.

---

### Post by igorc on 2008-09-09
Hi,

I don't know if this is helpful but found on the phoronix ati/amd support forum [http://www.phoronix.com]("http://www.phoronix.com") that best features for now for the ati HD3200 card is being provided by ati catalyst driver 8.5

I have that driver installed and I get perfect full screen HD picture 1920x1080 on my 32" LG LCD TV without any tweaking in the xorg.conf file. Have tried CRT 17" monitor and HDMI connection to the TV and both were automatically configured by the driver.

---

### Post by Pegel03 on 2008-09-10
Great, i'll try those. 
Even before my first message, i tried installing the default fglrx from the repository. That didn't work for me. Maybe i did something wrong?
After that 8.8 was installed and that worked fine. Except that HDMI was not properly configured. During the install i was working on a LCD screen. 
Myth is still an other problem that i'm not up too yet. Maybe the 8.9 release will solve some problems...
Keep you posted in a week or two. My deadline is before the end of the year. Then the misses will buy a media center:(

---

### Post by JugeHuge on 2008-09-10
Fingers crossed. :)

---

### Post by igorc on 2008-09-15
The only thing I have enabled for the ati driver is this:

Option   "TexturedVideo"  "on"

in "Device" section to fix the slow motion problem I got when watching TV in MythTV. This created a bouble picture output and to fix this I unchecked "Use OpenGL for vertical synchronization" option in MythTV (I can't remember where exactly)

I have also enabled the sound over HDMI (HDMI to HDMI cable) by making the ATI HDMI sound card/device as default and setting the video output to D-SUB/HDMI in BIOS.

By the way, I have tried 8.5 and the fglrx driver from Ubuntu repository, which is 8.3 I think, and both work fine for me. You can also install ATI catalyst control center, "amdcccle" package from the repository I think, and try to configure the card using that tool.

---

### Post by erotomanic on 2008-09-18
I'm also having this same mosaic problem.  Using the latest Catalyst drivers ( 8.8 ) because default fglrx driver gave me very choppy playback no matter what I did.

Funny thing is though, when I go into MythTV configuration, there is no more mosaic and everything appears fine.  Could I have screwed something else up?

Also, in the Proprietary Driver Manager, fglrx is marked as 'in use' AND checked.  I thought if using the Catalyst drivers it would be marked as 'in use' but not checked?

Has anyone be able to get the hd3200 working through hdmi at 1920x1080 with smooth playback?

Thanks for the help!

---

### Post by smiley119 on 2008-09-18
> **bml137 said:**
> I know when I let MythTV frontend go full screen (1920x1080), it is messed up like that.  When I change the MythTV frontend resolution to specifically 1920x1080 (instead of autodetect using 0x0), I have the same problem.  When I change it to 1919x1080, it works perfect.

How do I specifically tell mythfrontend to use 1919x1080?

---

### Post by JugeHuge on 2008-09-19
btw. ATI 8.9 drivers are out..
[ATI Drivers]("http://ati.amd.com/support/drivers/linux/linux-radeon.html")

---

### Post by nwpowell on 2008-09-19
> **smiley119 said:**
> How do I specifically tell mythfrontend to use 1919x1080?

mythfrontend --geometry 1919x1080

the --geometry 1919x1080 parameter will also work with mythtv-setup

---

### Post by erotomanic on 2008-09-19
Ok, I finally got my video to work at an acceptable level.  I have the GIGABYTE GA-MA78GM-S2H mb using the HD3200 & HDHomeRun.  Here is what I did:

Clean install of 8.04.1

Used the PC input of my TV with the D-Sub output
 - This gave me a default resolution of 1920x1080@60Hz and looks surprisingly good! (could only get 24Hz from hdmi or dvi out before)

Use the fglrx driver from the repository
 - Video was still slow and choppy at this point

Did full update from the update manager

Check option to use restricted codec's

Add Option "TexturedVideo" "on" to Device of xorg.conf
 - This fixed the choppiness I believe

Ran aticonfig --overlay-type=Xv
 - Not sure if this helped at all

Changed Video playback to use CPU++

Now all video is pretty smooth with occasional horizantal lines coming through a little.  At this point, not sure if I want to try new ATI drivers, but I'll try to change resolution to 1919x1080 and see if that clears up the lines.

---

### Post by Dupey on 2008-09-25
erotomanic thanks for your help. I am using mythbuntu with the GIGABYTE GA-MA78GPM-DS2H mb and the HDHR and I followed your instructions with some success. The audio no longer stutters and the video plays smoothly but... video usually plays in an over under split screen. When I change the channel the video gets totally scrambled but the audio stays good. I am new to mythtv and don't understand why I can play a DVD or an AVI with no problem.

---

### Post by nmahini on 2008-09-26
Hi all,

I desperately need help. I'm running ubuntu 8.04 on a machine with following configuration:

MB: M3A78-EM 
CPU: AMD 
Ram: 2 gb
Tuner: Hauppauge HVR-1600 

I installed and configured the mythtv and I'm running an S-Video cable from my Directv H21 setup box to the Hauppauge.

The problem that I ran to is that once I start mythtv and I chose the "Watch TV" option, I only couple of frames per second, so instead of being able to get anything out of what it's being showed, I just get pictures being refreshed every 3 seconds.

I tried installing an update for my video card( which is by the way on the MB) and I got an error sayin the version was incorrect. Now the driver was downloaded from Asus website and I'm assuming that it's the latest. 

Any thoughts regarding the problem?? Any solutions you guys might've think of??


Thanks

---

### Post by bturig on 2008-09-27
> **nmahini said:**
> 

MB: M3A78-EM 
CPU: AMD 
Ram: 2 gb



I have same hardware on a diskless server, that I am putting together. Unfortunately, this my first ATI video experience with mythTV

---

### Post by Dupey on 2008-09-28
After days of editing xorg.conf and installing various versions of the ati drivers I decided to do a fresh install of mythbuntu 8.10 alpha 6. Surprisingly the default driver that it installs works fine on the HD 3200. Even the most current ATI drivers (8.9) are not compatible with the version of X in 8.10 so there isn't even an option to install the proprietary driver. So when setting up mythtv you can't use any OpenGL settings. The video is not perfect, some HD stations seem just a little slow and SD stations get some horizontal jitters on fast moving objects. All in all it is much better quality than any of the ATI drivers and it also requires no configuration it works right out of the box. Hopefully the October release of the ati drivers support Xorg 7.4 so it can be included in the official release of mythbuntu 8.10 that should be available by the end of October. Until then I am perfectly content with using the open source drive.

PS. Mythbuntu 8.10 Alpha 6 uses the 2.6.27 kernel and will fry certain Intel network adapters see [http://www.ubuntu.com/testing/intrepid/alpha6](http://www.ubuntu.com/testing/intrepid/alpha6) for details and you can sign up for a notice when the problem is fixed.

---

### Post by serian on 2008-10-14
> **Dupey said:**
> After days of editing xorg.conf and installing various versions of the ati drivers I decided to do a fresh install of mythbuntu 8.10 alpha 6. Surprisingly the default driver that it installs works fine on the HD 3200. Even the most current ATI drivers (8.9) are not compatible with the version of X in 8.10 so there isn't even an option to install the proprietary driver. So when setting up mythtv you can't use any OpenGL settings. The video is not perfect, some HD stations seem just a little slow and SD stations get some horizontal jitters on fast moving objects. All in all it is much better quality than any of the ATI drivers and it also requires no configuration it works right out of the box. Hopefully the October release of the ati drivers support Xorg 7.4 so it can be included in the official release of mythbuntu 8.10 that should be available by the end of October. Until then I am perfectly content with using the open source drive.

PS. Mythbuntu 8.10 Alpha 6 uses the 2.6.27 kernel and will fry certain Intel network adapters see [http://www.ubuntu.com/testing/intrepid/alpha6](http://www.ubuntu.com/testing/intrepid/alpha6) for details and you can sign up for a notice when the problem is fixed.

Somebody played the game (Dota), with this card?

---

### Post by alejandro.mc on 2009-02-20
I'm about to buy this motherboard; I know all this can be a bit of a pain, but maybe solved, makes a great motherboard for a HDCP. 

I would like to know which is the status of all of this issues?

Anything still not working? Updated drivers already functional?

Thanks!

---

### Post by Dupey on 2009-02-22
The latest drivers from ATI work fine with the HD 3200 and MythTV. There are a few bugs I have noticed but they work better than the other options. I was very disappointed with ATI when I first got this board and couldn't get myth working properly but the 9.1 and 9.2 drivers have solved my problems and the thing works great. Now all I have to do is buy a TV with a HDMI port to test if that is working properly too.

---

### Post by TMcC on 2009-02-22
I've got a Jetway mini-itx that contains that IGP; you won't get GPU accelerated HD through it, and the ATI drivers really gave rise to lots of four letter words. 

I got fed up of the video tearing and ever extending promises about documentation and HD support from AMD... so bought an 8200 based board instead. I jumped ship before the latest drivers arrived, so maybe they're a lot better wrt video playback.

The 8200 is great though, using VDPAU with no problems; actually have a solution that doesn't sound like a hoover when playing high def.

I've still got the HD3200, and plan to build another when XvBA gets released.

I did install Windows 7 beta on it just so I could test the HD playback... and it does produce very good results. But right now, I'd buy an NVidia IGP 8200 board...

---

### Post by alejandro.mc on 2009-02-22
Thanks

---

### Post by Pegel03 on 2009-02-28
Two weeks became few months. Than finally upgraded to 8.10 and installed 9.1 ATI drivers. Was looking good, but found out i had some keyboard problems and noticed that 3D was slow. Helios screensaver would not run and page up/down, slash and arrow keys did not function. 
Installed 9.2 hoping it would solve someting. 

Further investigation took me a few nights and then just before reinstalling from cd (or giving up completely) I removed xserver-xgl (sudo apt-get remove xserver-xgl). 
This did the trick:) 
Will be working on HDMI connection and hopefully Myth shortly (yeah right, married with children).

@alejandro.mc 
So, it's looking much better now. And the future is even better:)
Decide for your self if it its worth the trouble. What alternative do you have. May be you can wait a little longer for things to grow (more) stable. 
Dupey will probably get there first.


Btw. glxgears was running, but glxinfo told me direct rendering: No

ATI ccc would not start. A message appeared that no ATI card was found.

And a message in Xorg.0.log gave:
(EE) Error compiling keymap (server-0)
(EE) XKB: Couldn't compile keymap

Tried using setxkbmap in /etc/X11/xinit/xinitrc, but didn't notice anything. Also created a HAL fdi file for the keyboard. Did not work either.

After removing xserver-xgl

Now is direct rendering: Yes:)

Before 9.1 installed correctly, the following symbolic link was created. Do not know why it was missing?
sudo ln -s /usr/src/linux-headers-`uname -r` build
Only now the DKMS part of installation would succeed.

For more detail mail to this thread, i'll receive a notification.
And again hopefully HDMI and Myth will be running before the end of this year:P

---

### Post by Pegel03 on 2009-03-02
Follow up: Connection to TV via HDMI was a breeze. Just connect and boot. Second screen was found and via ATICCC i choose identical screen.

Sound was a bit more difficult, but following this how to it was running within a few minutes:)
[http://www.mandladventures.com/2008/11/03/ubuntu-810-hdmi-sound-configuration/](http://www.mandladventures.com/2008/11/03/ubuntu-810-hdmi-sound-configuration/)

---

