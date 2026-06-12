---
title: "SOUND from analog Capture is out of sync in Pinnacle Studio 14."
date: 2010-12-28
forum: Multimedia Software
---

### Post by bozobyte on 2010-12-28
**SOUND from analog Capture is out of sync in Pinnacle Studio 14.:popcorn:**
   
  P-35 Platinum MS-7345 Mobo
  Windows XP  Home Edition SP3
  Intel Core 2 Quad CPU  Q6600 @ 2.40GHz (4 CPUs)
  2.4 GHz, 3328 MB RAM (3.3GB)
  NVIDIA GeForce 8600GT  (512 Memory Size)
  Realtek HD Audio Output Sound
  DirectX version: 9.0c
  Monitor: Viewsonic VX2035wm Series
  WD 500 GB HDD / WD 74GB RAPTOR HDD
  NERO 9 /  Pinnacle Studio 14 with PCI-500
   
  CAPTURE DEVICES
  Video Source Pinnacle 500-PCI
  TV Standard &#8211; NTSC  4.3
  AUDIO &#8211; Realtek HAD Primary Input &#8211; line Volume  (from onboard soundcard
  Using supplied Studio audio cable from camera RCA analog audio to soundcard)
  CAPTURE FORMAT >
  AVI or MPEG 1/ or 2      (I have AVI enabled)
  DATA RATE&#8211; 6000 kbits/sec
   
  Unless I&#8217;m Capturing from a MPEG 1 or 2 file from digital camera, that I have to worry about these settings below?  Right now, I want to capture analog AVI Composite video.
   
  MPEG TYPE > Mpeg1, Mpeg2
  RESOLUTION> 352x480, 480x480, 720x480
  SAMPLE RATE 48 KHz
  ENABLE BACKGROUND RENDERING &#8211; yes
   
  **I have my JVC analog camcorder hooked up as follows:**
  **From Camcorder >VIDEO-OUT to PCI-500 VIDEO IN**
  [B]From Camcorder AUDIO OUT to LINE-IN to my Onboard soundcard (Realtek HD)  
[/B]
[B]*THERE IS NO SOUND CARD ON THIS PCI CAPTURE DEVICE, ONLY S-VIDEO,VIDEO -IN,VIDEO-OUT, AND FIREWIRE.
[/B]
   
  __________________________________________
  Tried this - Clicked on Video Input > COMPOSITE, 
  AVI CAPTURE > USER-DEFINED QUALITY > SETTINGS
   
  PRESETS - AVI, CUSTOM &#8211; GOOD, (I&#8217;ll try &#8220;BETTER&#8221; next time)
  COMPRESSION > M-JPEG  
   
  AUDIO SETTINGS &#8211; Include Audio is checked.  PCM
   When I turn on the camcorder I can see the preview of the video, but when I press START CAPTURE, The preview screen goes black and the &#8216;Captured&#8217; counter is at 00:00:00:00, and the Frames dropped is &#8216;0&#8217;.
   
  I have updated my GPU driver recently and the date is 10-16-2010 version 6.14.0012.6099, also my Realtek HD audio.  My Pinnacle PCI-500 date is 11/21/2005 and version 2.0.19.0.
   
                 I checked my Virtual Memory in SYSTEM and this is what I saw >
  Boot Drive C:\ Initial Virtual MEM. = 2046
                     Maximum    "         "       = 4092
  DATA DRIVE F:\ 0
  I also shut all background APPS off while capturing analog.  Would something like this below, help me with the sync problems?
  _________________________________
  **I just found this and wondered if anyone had to change these settings to fix the sync problem:**
  **_Issue_**: Sound and video are not synchronized on video captured from an analog capture card.
   
  **_Resolution:_** This problem can occur during capture from an analog capture card if CPU utilization exceeds 95 percent. To avoid this problem, configure virtual memory to be &#8220;System managed&#8221; by following these steps:
   
  1. Choose Start -> Control Panel.
  2. Open the System control panel.
  3. Click the Advanced tab.
  4. Click the Advanced tab.
  5. In the Virtual memory box, click Change.
  6. Select System managed size, and click Set.
  7. Click OK.
  Thank you!
   
  [URL="http://www.****************/PressKits/EMEA/Studio/StudioMovieBoardPCI.jpg"][COLOR=Black]I'M ALSO TRYING YO GET AN UPDATED DRIVER FOR THIS PCI DEVICE THROUGH PINNACLE FOR WINDOWS XP.  THANKS!:confused:[/COLOR]
[/URL]

---

### Post by bozobyte on 2010-12-30
Because of a possible Paging file problem when I import video to my  boot C:\ Drive,I changed the directory to import video to my secondary  500GB HDD, with no paging files (0) to free up resources when capturing  using my JVC Analog Camera with VHS-C tapes.

I have an on board sound card (RealtekHD Audio) separate than my PCI-500  Capture on ny Mobo that I bring the Video in and the sound is about 5  to 8 seconds out of sync!.  Someone also mentioned going through START UP  at MSCONFIG and shut off programs that may interfere with the capture  process,with programs running in the background,but I'm afraid I might  delete an important windows START UP program that is needed.

All I know is that Pinnacle Support told me that they recommend the  PRESETS are set at MPEG, Video Compression Codec is MPEG2,and Audio is  MP2 with the DATARATE set at 6 Mbit. Then I changed it to 2 DATARATE,and still problem. But others tell me to set the  PRESET at AVI capture not MPEG2, so you see my confusion here.

Pinnacle Studio 14 HD Software with PCI500 Capture device

So I'll tell you what I have to work with - 

A friends SONY VRD VC-20 Video recorder DVD drive with ( FireWire,DV IN,S-Video IN,Yellow Video IN,Audio-Right / Left)

Pinnacle Studio 14 HD with PCI-500 Capture with (Video IN, Video Out, S-Video IN, S-Video OUT,and FireWire) 

And old JVC 1997 GR-AXM25U Analog Camcorder with (one Audio OUT, Video OUT JLIP, and RF DC out)

An old Panasonic PV8451 VCR with RCA Composite AUDIO IN/OUT, VIDEO IN/OUT ONLY, ((  no FireWire, Component, or S-Video ))

Tons of VHS-C camcorder tapes I want to capture (using most audio on video) edit, create chapters,effects, then burn to DVDS.

*Any ideas on what scenario(s)  could possible work using any of the above hardware/software for the (best analog capture with the best sound and video in sync?  My issues is the sound does not match the video when being captured from camcorder. I've tried starting the camcorder, pausing it until I see the video frame on my Studio preview Capture screen then hit record, but it still goes out of sync. 
I free up most resources, Run Defrag,empty temp Files, recycle bin, Clean Disc,start-up programs,etc. record file to onboard WD500 Data HDD (no paging files) My Boot drive is WD Raptor 74GB with paging files) so I don't output to there.

 __________________________________________________

 Someone else wrote, and doubt it was you,  " After going through Studio 7 (around 2002), 8, 9, 10 and 11....I hit snags with the out-of-sync stuff (from analog only) with every version. Recently, I bought the Canopus ADVC110, and it finally seemed to take care of the problem...Maybe a solution!" 

My response:

So this Canopus ADVC110 Analog/Digital converter is the hot ticket? 

I'm thinking the issues with my out if sync issues may have or a lot with me hooking up the audio from camcorder to an on-board sound card, independent from the Video from camcorder to the pinnacle PCI-500 Capture device.

Can you tell me if this Canopus hardware also edits and burns with any type of editing, effects software, or would I still be able to use that in PINNACLE STUDIO 14 for finishing effects before burning to DVD? 

Did you uninstall your PCI-500 capture, if you ever did have one before?

Also, does it really matter which DVD-R+, DVD-R- Blanks I use for final burn?

 Has anyone have any bad stories from using the CANOPUS ADVC110?  

Before I go out and spend more $$$ on more capture/editing/burning software/hardware, my friend just let me borrow her old SONY VRD-VC20 Video recordable Drive to burn either to DVD, or to computer, but it also came with  NERO6 software, probably included on the supplied DVDirect Software Disc Rev. 6.10W. Disc 

 At present, I have NERO 9  and this old SONY VRD-VC20 hardware came with NERO 6 software, probably included on the supplied DVDirect Software Disc Rev. 6.10W. ?  Is it Possible to use this SONY VRD-DVD burner as a pass-through from analog composite  camcorder > Sony VRD-VC20 > Digital output to computer for capture into Studio14?

---

