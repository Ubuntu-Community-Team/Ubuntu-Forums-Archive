---
title: "Configuring Hauppauge HD-PVR and SA4350HDC STB"
date: 2010-08-29
forum: Mythbuntu
---

### Post by stratoscape on 2010-08-29
Hello, I finally broke down and bought a HD-PVR, it seemed easy enough to setup in MythTV but I cannot find anything current or useful how to change the channels on my Scientific Atlanta (sa4350HDC) STB. I looked at the scripts in the contrib folder but get errors trying to compile them (at my skill level I have no business attempting anyway)

Does anyone know of a precompiled version or currently working script that will change the channels on my STB. 

I noticed that I can configure the STB as a capture source (FIREWIRE) and I can watch/record local OTA content no problem and channel changes great so whatever is "baked" in 10.04 it's working with my box without any external channel changer. Just tring to figure out how to leverage the firewire channel changer (or USB) to continue changing channels only record with the HD-PVR 

thanks

Strato

---

### Post by LowSky on 2010-08-29
Here ya go, this will help change channels over firewire.
if you need more info let me know
see the attached, it has instructions in the readme

---

### Post by stratoscape on 2010-08-29
Hey thanks for the quick reply. I installed the script and now wondering if I am suppose to see the channel actually change? I tried running and seems like it ran but I do not see any activity on the STB. 

I configured the external changer line in the myth setup with just the command mythchanger -c with no quotes and no channel as I thought myth would add the channel # (wondering if quotes are needed)

strato@godzuki:~$ mythchanger -c 709 -f 3 -v

mythchanger .10f beta

Acquiring firewire handle... OK.
1 port(s) found

Acquiring handle on port 0... 1 devices detected.
Skipping empty node 0
STB Vendor ID: 0x1cea Model ID: 0x10cc, Scientific Atlanta Model SA4250HDC

(Using user selected channel changer #3)

1 STB(s) found:
-------------
STB 1: port=0, node=1, changer=3, GUID=0x0011234567890000

strato@godzuki:~$ 


I think I may have a seperate issue with the video as it is not displaying either. When I open the frontend and try and watch live TV, I get the really long "Please wait" then times out returning to the menu and no activity on device other than basic blue power source (I will create a separate thread for the non-picture issue, just kinda surprised this thing is so rough setting up) 

Thanks again

strato

---

### Post by LowSky on 2010-08-30
instead of this
```
mythchanger -c 709 -f 3 -v
```

try this as a test in a terminal. ```
mythchanger -f 4 -c 709
```

look at the cable tv box, you should see the channel change.  leave the channel number out when you program it in mythTV backend

if not try the command

```
plugreport
```
this will check your firefwire connection if it fails then you have to call your cable company to get a them to activate the firewire port or give you another cablebox.

make sure you set up the HD PVR correctly in the MythTV backend.

if not follow these instructions
[LIST=1]
[*]Add a new capture card. When prompted, select "H.264 Encoder Card (HD-PVR)" as the card type. Set the /dev/video node to the number of your HD-PVR. Finish adding the new capture card. You can also set the audio input on this screen. All cables must be functional and properly attached in order for capture to succeed with the HD-PVR. If every recording fails with a "Unknown type, recording width was 0" error in the mythbackend log, it is possible that one of your cables is faulty or has become disconnected. 
[*]Enter option 3, "Video Sources." Set up a video source for your HD-PVR's tuner as described in the manual. 
[*]Enter option 4, "Input Connections." Connect the video source to the appropriate input on the HD-PVR. Important Note: You must set a channel change script for the HD-PVR to work properly
[/LIST]

if it still doesn't work check this
[http://www.mythtv.org/wiki/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Hauppauge_HD-PVR)

---

### Post by stratoscape on 2010-08-31
Success!
Problem (1): 
Channel changing over the firewire works great. your suggestion to force STB selection first did the trick even though I gave you the wrong STB, it was a SA4240HDC and not SA4250HDC you still provided right answer, sorry and THANKS! 

Success!
Problem (2):
No picture. Fixed this one just by reading post on the HDPVR, Lots of problems I guess with SPDIF. When connected no picture, in fact it times out almost hanging my system. I reconfigured the sound in the backend to use RCA Rear and it started working. I have to ATI HDTV Wonder PCI cards that I was using for recording HDTV OTA and they would not even work with the SPDIF enabled on the HDPVR.

I found that I was using old firmware on HDPVR 1.2.x and upgraded to 1.5.7 and still get funky message(s) in logs that it is untested and may not work but reasearching this I find that everyone is getting it.

I am testing my first recording as I type so hopefully I at least will have 2ch sound but disapointed SPDIF is not working as advertised, guess I will keep up on it to see if Hauppauge gets around to addressing it.


Thanks for all the help!!!!


strato

---

### Post by nojstevens on 2010-09-19
After three days of trying to get channel changes to work on my SA4640HD STB I followed this thread and bingo - it works straight away. No error messages, no dependency issues (after installing the listed ones above) added the command to MythBackEnd and voila - channel changes work - and very fast (comparatively) too.

Thank you - very very happy this morning

Jon

---

### Post by LowSky on 2010-09-19
Glad to help

---

### Post by nojstevens on 2010-09-27
So, this is working great for me - so reliable and much faster than using IR on my previous setup.

I am wanting to add an extra STB - this approach will work for two HD-PVR's and two STB's I presume? 

Any watchouts I should be aware of?

Jon

---

### Post by LowSky on 2010-09-27
> **nojstevens said:**
> So, this is working great for me - so reliable and much faster than using IR on my previous setup.

I am wanting to add an extra STB - this approach will work for two HD-PVR's and two STB's I presume? 

Any watchouts I should be aware of?

Jon

I have no idea if you can use this command to be used over two boxes. Maybe rebuilding the package with a slightly different name might do it.


More info about mythchanger can be found here
[http://ubuntuforums.org/showthread.php?t=977820](http://ubuntuforums.org/showthread.php?t=977820)

Unfortunately the original developer, isn't working on the project anymore.

---

### Post by nojstevens on 2010-09-27
The README indicates that you can send messages to specific boxes ( -g <GUID> GUID of target STB), so I'm wondering if I can just use the same mythchanger but specify the GUID in the command. Was hoping it had already been done, but I guess I can try it and report back if it works....

Jon

---

### Post by LowSky on 2010-09-27
Use the command in terminal```
plugreport
``` so you can get the GUID

---

