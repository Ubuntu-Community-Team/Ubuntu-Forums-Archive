---
title: "tvtime closes immediately with Asus P7131 (saa713*)"
date: 2009-09-06
forum: Multimedia Software
---

### Post by ooli on 2009-09-06
UPDATE:   The installation of Catalyst Drivers ([http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&#9001;=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English")) solved my graphics/monitor/video-related-tv-tuner problems.   The Catalyst 9.9 driver (the most recent driver for the Radeon HD3200, as well as others) did the job, i.e. allows tvtime to work.  Xawtv doesn't **need** the Catalyst driver but my impression is that the image is better with it. 

So, if anyone else is having the same tv-tuner issues (tvtime opens and closes immediately), I'd recommend giving the Catalyst driver a go.  :)

PS.1.  My video-related tv-tuner problems are solved, but not the audio-related. :(  After doing some research on the net, I **suspect** DMA is not properly handled.  If I'm not able to sort it out, I'll start a new thread.

PS.2.  Although no longer relevant, I'm not deleting my original post(s), in case someone else has similar problems and recognises the symptoms. 

Thanks!

-------------

*(Original post follows):*


[I]Fellow forumites, 

My original post was about an overlay error with tvtime, but I now think that it all boils down to the lack of support of tvtime by ati.  

So, my questions are:  

1. does ati still not support tvtime?  

2. (if 1. is true) is there a workaround that would allow tvtime to work with one of the newer ati cards?    

3. would you please recommend another tv-viewing/recording programme that works with ati cards?  

4. would installing a second non-ati video card allow me to use tvtime for tv-viewing/recording?  

Thanks for your time!  

-----------  

[SIZE=1](original post follows but probably isn't relevant any more)   


Fellow forumites, I am trying to make an Asus P7131 analog tv tuner (apparently saa713*) work on a new (Hardy) box I just built. 

The card was working perfectly in an older (Hardy) box, and I had absolutely no problems getting tvtime to work with the card then.  I've tried the advice given in other threads, but now I'm overwhelmed. Would you please help? 

Symptoms: tvtime opens and closes immediately, producing the following error: 

 *** tvtime requires hardware YUY2 overlay support from your video card 
*** driver.  If you are using an older NVIDIA card (TNT2), then 
*** this capability is only available with their binary drivers. 
*** For some ATI cards, this feature may be found in the experimental 
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
  *** If unsure, please check with your distribution to see if your 
*** X driver supports hardware overlay surfaces.  

Information: instead of being correctly detected as P7131, it is detected as follows:

saa7133[0]: subsystem: 1043:4845, board: ASUS TV-FM 7135 [card=53,autodetected]

and:

03:06.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
    Subsystem: ASUSTeK Computer Inc. TV-FM 7135
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at fbfff800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>

As recommended in other threads, I tried various suggestions: 

1. running 'modprobe saa7134 card=146' (which corresponds to ASUSTek P7131 Analog). 

2.  modifying /etc/modprobe.d/options to include: 

options saa7134 card=146 tuner=5 
install saa7134 /sbin/modprobe --ignore-  install saa7134; /sbin/modprobe saa7134-alsa 
options saa7134-alsa index=1

3. adding the lines:

Option "VideoOverlay" "on" 
Option "OpenGLOverlay" "off"

in the relevant section of xorg.conf and disabling Compiz.

No change. 

You may have guessed I'm pretty unfamiliar with inner Linux workings, so please ask any questions/request any outputs you believe are relevant.

Thank you for your time! :)[/SIZE][/I]

---

### Post by ooli on 2009-09-07
In case it makes any difference, I must mention that there are some (seemingly) minor issues with the onboard graphics (radeon hd3200).  I tried both open and proprietary drivers; no apparent difference regarding image distortion and neither makes tvtime work. At the moment I'm using ati drivers (otherwise the monitor is not correctly detected).

(For example, during startup and shutdown the image becomes distorted for a few seconds, similarly to the image in this post: [http://forum.boxee.tv/showpost.php?p=7849&postcount=1](http://forum.boxee.tv/showpost.php?p=7849&postcount=1)).

Also, I tried different settings for Primary Video Controller in BIOS (currently set to IGFX-GFXO-GPP-PCI) but there was no change in terms of image distortion.  No change in tvtime either.

At this time, my main questions are:  

1. is the error I get with tvtime (ie. about overlay support from my video card) the actual reason why tvtime isn't working, or is it just a default message?

2. does the mis-detection of my tv tuner (i.e. as P7135 instead of the correct P7131) play a role?  Apparently P7131 and P7135 have the same driver (but P7131 doesn't have radio function).

Thanks for your time!

---

### Post by HappyFeet on 2009-09-07
Have you tried xawtv?

---

### Post by ooli on 2009-09-07
Thank you, Happy Feet, I'll try xawtv right now! :)

When I first needed a tv viewing/recording programme tvtime gave (in my opinion) the best results, but since it's not working now, I'm open to suggestions. 

I'll let you know how it goes. Again, many thanks!!

---

### Post by ooli on 2009-09-07
HappyFeet, this is fantastic: xawtv seems to work. :P

I had to uninstall the proprietary drivers, enable overlay and run xawtv -nodga (otherwise I got a black screen), but I'm now getting tv signal. 

I'm now trying to figure out scanning channels and how to do recording (recording **is** possible with xawtv, right?), but it's a big improvement. 

In the meantime I also installed zapping, which keeps crashing when I enter preferences or channels, so for the time being I'll be trying to figure out xawtv.  

Thank you very much, HappyFeet! :P

(what a shame for tvtime... :()

---

### Post by HappyFeet on 2009-09-07
This may help:

"Well, the user interface should be self-explanatory. There are only very few things you need to know to get started. Most important one is how to do a scan for DVB Stations:

   1. start xawtv
   2. click with the right mouse button into the main window to popup the control window.
   3. select "Menu / Edit / Scan DVB ..." to get the DVB scanner window.
   4. DVB-S only: xawtv should ask for the LNB configuration now. It needs to know that for tuning.
   5. Tune a initial bouquet now. You can do that manually via "Menu / Commands / Tune manually ..." if you know the parameters. Or you can pick one from "Menu / Database". This menu is build from the database maintained by the linuxtv guys, xawtv assumes to find that in /usr/share/dvb/.
   6. If the tuning worked fine the frontend should get a lock (check the status line of the DVB scanner window) and the window should start filling with information about the current bouquet within the next few seconds.
   7. Now you can start a complete scan using "Menu / Commands / Full scan". Get a coffee now, that may take some time to complete. 

Once the scan is complete you can search in the list, zap through the stations found, and put the ones you like into your personal station list. The best way to to that is to just drag'n'drop them from the DVB scanner window info into the control window.

You can also use edit menu in the control window to add stations, but it's easier to build the initial list using drag'n'drop and later on only change some station properties like group or hotkey using the edit menu of the control window."

---

### Post by ooli on 2009-09-07
Thanks for the info, HappyFeet! 

Actually my tuner is analog, so I wonder if the personal station list you mentioned is available for analog too. I'll  check it out. 

In the meantime, in case other users find this helpful, here're some observations I made while trying to figure out xawtv (just to remind people, I have an onboard ATI video card and an saa173* tv tuner under Hardy): 

1. running xawtv and v4l-conf under proprietary ati drivers produces a black screen, with and without DGA.  

2. running 'xawtv -nodga' under open drivers produces tv signal but also v4l-conf errors.  

3. running 'xawtv -remote' under open drivers produces signal correctly, without errors.  

4. in order to scan and save a station list, I created an empty document named .xawtv in the home directory and ran 'scantv -C /dev/vbi0 -o .xawtv'. Other syntaxes produce errors about /dev/vbi or don't save station information at all. 

So far, so good.  :)  Now I need to figure out how to get sound, but it's possible that my connections and/or audio/mixer settings are wrong.  I hope after all this, video capture works!

Incidentally, I've been a Ubuntu user for a couple of years but never had any serious hardware issues, which means I never had the opportunity/reason to delve deeper into Linux.  This somewhat bothered me, so running into these issues is helping me learn a lot with the help of fellow Ubuntians! :)

---

### Post by ooli on 2009-09-20
Problem solved!

(please see post #1 [http://ubuntuforums.org/showpost.php?p=7908099&postcount=1](http://ubuntuforums.org/showpost.php?p=7908099&postcount=1) for details)

By the way, I don't seem to be able to edit the original subject (to add "[SOLVED]")...

---

