---
title: "Video aspect ratio problem, some install comments and questions"
date: 2008-01-03
forum: Mythbuntu
---

### Post by Gloves on 2008-01-03
Hi everyone, I'm a new user of Mythbuntu, installed 7.10 over the weekend and have been trying to get it working properly since.

My main problem at the moment is that video playback (Watch TV or watching Apple trailers for example) is all compressed into a narrow band across the playback area. That is, the aspect ratio is correct in width but compressed in height. In the Myth Control Center I have all three players selected - should I try one at a time to see if its a player specific issue? The Myth frontend display and desktop are all fine. Anyone else have a similar problem?

My second problem is that I can't reliably tune into channels. I can receive the EIT data and sometimes get some channels, so I know the tuner is basically working. From reading this and other forums I suspect I might have to play around with the tuning frequencies - is there anyone here from the UK getting their signal from Crystal Palace who might have had to make similar changes?

My relevant hardware is a Hauppauge Nova-T 500 and an ATI Radeon 9600.
I'm using the fglrx proprietary drivers.

I had some problems with the TV out initially, but this is my current working xorg.conf (relevant sections):

```

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        HorizSync   30-50
        VertRefresh 50.0 # I saw this recommended for UK PAL-I
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "NoTV" "no"
        Option      "TVFormat" "PAL-I"
        Option      "TVStandard" "VIDEO"
# I had the following two options toggled in reverse, but this gave a
# blank screen when trying to Watch TV
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "TVHSizeAdj" "0"
        Option      "TVVSizeAdj" "0"
        Option      "TVHPosAdj" "0"
        Option      "TVVPosAdj" "0"
        Option      "TVHStartAdj" "0"
        Option      "TVColorAdj" "0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes "800x600"
        EndSubSection
EndSection

Section "ServerFlags"
        Option    "blank time" "0"
        Option    "standby time" "0"
        Option    "suspend time" "0"
        Option    "off time" "0"
EndSection

```

I installed the V4L-DVB drivers as described here:
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

This was to get my remote working - which it now does. Question is, do I need to change my capture card types as they were setup using the exisitng DVB option when running Myth setup - or is that the V4L-DVB driver anyway?

Other comments:
Had to replace my DVD drive as initial install would randomly fail with an "errno 5 Input/Output Error" - this is possibly because the disk was written on a fast writer and the drive in my Myth box was fairly old. Might be that Ubiquity is a little fussy...

If you don't have the install DVD in the drive, enabling some options in the Control Center appear to work but don't really as it can't get the files from the disk. I removed the DVD from my sources list and that seems to have fixed the problem.

I hope someone can help with the issues I've described above, and maybe this will help someone experiencing some of the problems I've had.

Thanks
Gloves

---

### Post by notquitemichael on 2008-01-03
As a quick fix to your aspect problem, use VLC (which can be integrated into myth tv,) and using the context menu you can manually change the aspect ratio the video is shown in.

I suspect the option needed to permentantly help this problem is in the myth tv settings, but unfortunately i don't have my mythtv box with me.

Used UK Crystal palace (guildford,) to get any signal I had to round the frequnecy to 3 significant figures. Try 2 and 4 (up and down,) if you're having trouble. Also, as much as I hate to suggest it, if you have a windows computer; try that with the native drivers: atleast then you can assetain if it's just bad signal.
I personally found that I only had good enough signal to pick up BBC channels until I got a boosted areial.

Myth probally picked V4L, if it's working well enough and not complaining about 'no capture source' then you're probably fine.

I found when fine tuning your TV card etc it was better to use Kaffine which has a very customisable, easy to use TV interface; making tweakin' significantly esaier.

The DVD drive, and what you did, were exactly what you have to do; as if you consider: the DVD has to be in the drive to be a source for packages.
n.b. you could have checked the DVD using the 'check dvd for defects' option on the start.

Well, good luck. No doubt someone with a little more experience then me'll be able to give you more exact pointers.

Tom.

---

### Post by Gloves on 2008-01-04
I've made some progress. I put a tuning delay in my settings, and I now seem to get a better signal strength - I can only Watch TV using one of the tuners, the other can't seem to get a signal. I'll go through all the settings for the problem tuner this evening and hopefully get it working too.

Which brings me to my other problem - all my video playback is still compressed into the top half of the playback area. I tried VLC and MPlayer separately using the Control Center, but the results were the same. I also played around with the VertScanPercentage and YScanDisplacement settings but they didn't make much difference.

When I watch an Apple trailer that appears in a video window in the Myth GUI, the video is also compressed into the top half of the playback area, but the GUI is fine, so I suspect its a player setting and not a problem with my xorg or tv out.

If I try and change aspect ratio using 'w' when watching TV, the display indicates that its changing, but the video is still stuck in the top half of the screen.

:confused:

Does anyone have any ideas? Where can I see what player command is being used to watch tv / play video - can it be customsed?

Thanks
Gloves

---

### Post by Jaramia on 2008-02-13
I've actually been having a similar problem. Any video played (dvd, vlc, divx, etc) on all players is squished to the top half of the screen.

I've used fedora core, and various other window managers. none seem to help.

Did you fix the aspect ratio problem?

---

### Post by Gloves on 2008-02-21
Hi Jaramia,

I solved the problem by getting a cheap Nvidia card :)

I know thats cheating, but Myth forums everywhere have loads of people with ATI driver problems. I was struggling enough with getting my Nova T 500 to work properly that I took the easy and lazy option!

I'm sorry that doesn't help you.

Hans

---

