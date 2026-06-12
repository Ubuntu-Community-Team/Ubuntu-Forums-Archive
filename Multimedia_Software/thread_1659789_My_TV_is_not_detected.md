---
title: "My TV is not detected"
date: 2011-01-04
forum: Multimedia Software
---

### Post by glendo on 2011-01-04
I have a ASROCK ION 330 running as HTPC.  Currently running XBMC live DHARMA.  I decided to install full Ubuntu 10.10 desktop.  After installation of Ubuntu and current NVIDIA drivers system detects Onkyo AV receiver as monitor and will not allow resolution greater than 640X480.
 
Ion 330 -> Onkyo SR-tx705 -> Mitsubishi TV (via HDMI)
 
Everything works as expected if I connect directly from PC to TV,  I get good overscanned video that is easily correctable to fit screen.  Audio is also good.  problem is only when the AVR is inserted between PC and TV.  
 
I have temporarily reverted to booting XBMC Live installed on HDD which is works.  The only glitch I see with XBMC live is that the monitor shows as ONKYO and says its running at 640X480 but it is actually running at correct resolution.
 
Also as a side note I had the same problem months ago with Ubuntu 9.4.  Back then I finally gave up and installed vista, which ran without issue.  With new versions of Ubuntu and Xbmc released I decided to try this again.
 
I have searched forums/web for a solution but while I find countless overscan and audio discussions I found no help for this.
 
can anyone give me a shove in the right direction?

---

### Post by BicyclerBoy on 2011-01-04
I don't have a simple solution or any experience of this problem.

But this problem is not uncommon..seems to be a common windoze (xp) problem as well.
Problem occurs with the AVR pass-thru of the EDID data.
Onkyo & Yamaha are mentioned.

It is possible to configure X server to force a native resolution that would match your display & ignore any reported EDID.

[http://marantz.custhelp.com/app/answers/detail/a_id/298/~/hdmi-edid-handshake-problems-with-pc-connection-sources](http://marantz.custhelp.com/app/answers/detail/a_id/298/~/hdmi-edid-handshake-problems-with-pc-connection-sources)

Options:
I would try the latest nvidia drivers (260) in an attempt to find the best solution.
Could give up HDMI audio & use S/PDIF to your AVR. Connect TV direct to PC.
Edit xorg.conf file to force 1080p.

Note: The best PQ on DFP TV (i.e LCD plasma) is at the native resolution, direct pixel mapping & definitely no over-scan. Often this must be by HDMI.

The latest nvidia driver can be found from 3rd party ppa that does not require stopping x server & install from terminal login..Depends on your Linux skills..

---

### Post by glendo on 2011-01-05
Thanks.  That reference is MS specific, but I'll search for the linux solution to edit EDID settings.

---

### Post by BicyclerBoy on 2011-01-05
The reference was still relevant..

Linux & windoze graphics card drivers are having problems reading display  EDID DDC thru' AVR HT amps.

Did you read the options I listed ?
Have you tried the latest nvidia driver ?

If you want to try to stop mode validating against the EDID then :
edit /etc/X11/xorg.conf

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "ModeValidation" "AllowInterlacedModes"
    Option         "UseEDID" "FALSE"
    Option         "UseDisplayDevice" "DFP-0"
    SubSection     "Display"
        Depth       24
        Modes      "HD1080p"
    EndSubSection
EndSection

```The"DFP-0" may not match the wired ports of your video card, may need "DFP-1".
You may need to try these commands as well:
   Option   "ModeValidation" "NoEdidModes"   
   Option   "IgnoreEDID" "True"     # not used anymore ?
   Option   "ConnectedMonitor" "DFP-0"    # not recommended as overwrite scan
   Option   "TVStandard"  "HD1080p"

This assumes your TV is 1080p capable..
"HD720p" "HD1080i"  are valid built-in TV video modes.

---

### Post by glendo on 2011-01-05
sorry BicyclerBoy I did not mean to say your post was irrevelent just that the microsoft link did not enlighten me. 
 
 Yes I have the latest NVIDIA drivers.  I'm at work ATT but I think your advice about editing xorg.conf is what I need, I'm going to try it first chance I get, probably not till weekend.  
 
Thanks a million for your input I'll post back here after I try it.

---

### Post by glendo on 2011-01-10
I tried all sugestions.  I was able to make things worse and much worse but was unable to make it work the way I need it to.  I have reluctantly decided to hang it up for now I have gone back to Windows.  I prefer Linux but in this case windows is what works.
 
I will keep looking for a solution.

---

### Post by BicyclerBoy on 2011-01-10
Can you post your Xorg log file..

/var/log/Xorg.0.log

dmesg

There may be some good clues.

FYI
You do not want to use overscan with DVI/HDMI connections.
The TV display will have an input mode setting like just scan/direct pixel mapping/PC input.
Some TVs make this obscure.
Normally you want to drive the TV at its native resolution but the ION chipset may not be as good as the later Pioneer/Sony/Panasonic engines.

---

### Post by glendo on 2011-01-14
Don't I feel stupid!  I had overlooked a HDMI splitter in the equation removed that, configured system while connected directly to tv saved xorg.conf rerouted through AVR and all is well, except for no audio over HDMI.  But I just got here, I'm sure I wont have too much trouble fixing that.

---

### Post by BicyclerBoy on 2011-01-14
Well you still solved it in the end.

Good luck with the audio.

---

