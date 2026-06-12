---
title: "Voice Recording with Sound Recorder"
date: 2007-08-11
forum: Multimedia &amp; Video
---

### Post by kmir on 2007-08-11
I am new to ubuntu and LINUX and I have had problems with most programs I tried, and I am hoping to find a few solutions in this forum. Here is my "Sound Recorder" problem:

I have a microphone that works fine under Windows. I open Sound Recorder, and I have chosen basically every possible combination for "Record from input", "Record as", and the mute or unmute options under "Volume Control" in the tab "Capture". Of course I started with the obvious settings but after those did not work, I tried many others.

Please help! Is there anything that I might have overlooked?

Thanks!

---

### Post by nzadLithium on 2007-08-11
go into the volume control. Look for microphone. unmute it. Turn volume to maximum. Say something into ur mic. If you get sound out of your speakers thats good. If you don't then ubuntu probably hasn't detected your microphone. 

If you dont get sound try going into edit proeferences then add microhone capture and mic boost.
then go back to the volume controlls and click the switches tab. make sure mic boost is checked.
goto the capture tab make sure the mic picture and sound picture are unmuted and move the sliders to maximum. Then try talking into it. Tell me whether or not you get sound out of your pseakers by the end of this.

Do everything i just said. Then try sound recorder again. My record from input is blank so i dont think it matters what is there. but if it doesnt work blank see if you can put microphone there.

Tell me whether you get sound out of your speakers and whether it records by the end of this. 

If you don't get either then is your microphone usb or one you plug into your soundcard?

---

### Post by kmir on 2007-08-12
Hey nzadLithium!

It is working now. I thought I did all the stuff you told me to do before, but obviously, some helpful mind is needed :)

Thanks so much,

Miriam

---

### Post by racepics on 2007-08-17
I have the same problem with sound recorder not working. (Ubuntu 7.04 /64 )
My sound out works fine but cannot get mic to work.
Have checked mic and capture 1, 2, 3, in prefs but there is still only one thing showing in switches tab ( headphone )
Recording tab doesnt show mic - only capture, capture1 and capture2
Playback tab does show mic and nothing is muted anywhere.
In prefs I have the following ticked:
Headphone
PCM
Front
Front mic
Front mic boost
Line in
CD
Microphone
Mic Boost
Capture
Capture1
Capture2

Soundcard is onboard (Asus M2N32-SLi mobo ) and is recognised as HDA NVidia (Alsa mixer )

---

### Post by nzadLithium on 2007-08-21
Nothing being in the switches tab just means ur soundcard doesnt support mic boost.

Go into the capture tab and unmute the speaker and the microphone icon in all the capture columns.

---

### Post by racepics on 2007-08-21
Thanks nzadLithium.

But I dont have a capture tab - only Playback | Recording | Switches | Options

In the Recording tab I have: Capture | Capture1 | Capture2

In the Options Tab I have Input Source > Mic

Everything is unmuted.

---

### Post by nzadLithium on 2007-08-25
I would suggest trying the microphone in a different computer and checking that it goes. Otherwise i think it will be a driver problem. Tell me if it goes in another pc. If it doesnt post your soundcard model here.

---

### Post by racepics on 2007-08-26
> **nzadLithium said:**
> I would suggest trying the microphone in a different computer and checking that it goes. Otherwise i think it will be a driver problem. Tell me if it goes in another pc. If it doesnt post your soundcard model here.

The mic is part of a Altec Lansing Headset and it works well on my other PC for skype etc.
 
The sound card is part of the Asus M2N32-SLi motherboard.

Ubuntu Hardware Manager detects:
Vendor:  nVidia Corporation
Device:  MCP55 High Definition Audio
Screenshots here 
[http://www.linuxpc.co.nz/screenshots/Screenshot.png](http://www.linuxpc.co.nz/screenshots/Screenshot.png)
[http://www.linuxpc.co.nz/screenshots/Screenshot-1.png](http://www.linuxpc.co.nz/screenshots/Screenshot-1.png)
[http://www.linuxpc.co.nz/screenshots/Screenshot-2.png](http://www.linuxpc.co.nz/screenshots/Screenshot-2.png)
[http://www.linuxpc.co.nz/screenshots/Screenshot-3.png](http://www.linuxpc.co.nz/screenshots/Screenshot-3.png)
[http://www.linuxpc.co.nz/screenshots/Screenshot-4.png](http://www.linuxpc.co.nz/screenshots/Screenshot-4.png)

---

### Post by nzadLithium on 2007-08-27
on this page:
[http://www.asus.com/products4.aspx?modelmenu=1&model=1163&l1=3&l2=101&l3=0](http://www.asus.com/products4.aspx?modelmenu=1&model=1163&l1=3&l2=101&l3=0)
>  High Definition Audio
Enjoy high-end sound system on your PC! The onboard 8-channel HD audio (High Definition Audio, previously codenamed Azalia)

I looked up azalia it seems it is intel based
[http://www.intel.com/standards/hdaudio/](http://www.intel.com/standards/hdaudio/)

I looked it up in the alsa soundcard matrix
heres the supported intel cards list
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)
as you can see there is nothing to do with azalia.

So i'm assumming your card isn't supported. I could be wrong though it might be one of the supported intel cards on that page just named differently.

The only suggestions i have are
Make sure when you use the microphone you have no other programs that might 'grab' the audio open. This should really only be a problem if you have an OSS sound program open though.

Otherwise i would say get a new soundcard. I would ask around on other forums though because i've only had linux about half a year so i may be wrong with my assumption that the card is not supported.

I'm sry i couldnt help you more.

---

### Post by thamane on 2007-08-27
I've got an ASUS M2N-E with the same Nvida-Based HD-Audio MCP55, and I'm running Ubuntu 7.04. On my machine I get playback just fine. Same here, no program will record from the mic (I tested audiorecorder, audacity, skype).

But, I CAN HEAR when I am talking into the mic. In the audio mixer I can even change its levels and mute in - which seems to indicate that the sound DOES pass through the system, thus the drivers are working correctly (no matter whether I plug it in on the front or back of the machine BTW). 

So to me the problem seems rather that I can't chose the right input device in the different programs, what do you think ? Needless to say I tried all that appeared ...

Anybody got any ideas ?


EDIT :
I checked on the alsa-site for MCP55 and found the following changelog :

Changelog between 1.0.13 and 1.0.14rc1 releases
alsa-driver 

   - Audio: Add nvidia HD Audio controllers of MCP67 support to hda_intel.c    
     Add the support for HD audio controllers of MCP51,MCP55,MCP61,MCP65 & MCP67.
     Signed-off-by: Peer Chen <pchen@nvidia.com>

This changelog is from Aug 10. S maybe I'll try to install a new driver ... 
still strange though that I'm already able to hear my voice but am not able to select the right source in the programs.

---

### Post by thamane on 2007-08-27
OK, it works now :D :guitar:

On a terminal I started "alsamixer". In the capture tab, I activated the three last items capture1, capture2 capture3 by hitting the space key (I have no idea which one is which, in the GUI I set the first one to front mic).

with "arecord -vv -fdat test.wav" I could record a file. Now it works in Skype too.

This really is bizarre that I could get it to work with alsamixer but not with the GUI audio mixer. Maybe I'm just stupid, but I'm so glad it now works ;-)

So maybe there is hope for racepics, too ?

---

### Post by racepics on 2007-08-27
nzadLithium - thanks for everything you've done :)

thamane - are you using the 64bit version of Ubuntu 7.04?
I've just done what you did and it created test.wav but its empty (no sound )
The strange thing is, when I unmute Capture, Capture1 & Capture2 and then select one of them in the sound recorder it sometimes ( but not always ) re-mutes one or all of them on its own.

Also with the sound recorder, should I be able to play back a recorded sound before saving it?
Or do you have to save it before you can play it back?

When I try to save an attempted test recording I get the error message "could not save the file - invalid parameters" 
[http://www.linuxpc.co.nz/screenshots/Screenshot6.png](http://www.linuxpc.co.nz/screenshots/Screenshot6.png)
[http://www.linuxpc.co.nz/screenshots/Screenshot7.png](http://www.linuxpc.co.nz/screenshots/Screenshot7.png)

---

### Post by nzadLithium on 2007-09-02
I used to have the same problem with my onboard audio. It would only work through alsamixer not though normal gui. I used the gui for alsamixer though. it makes it easier to use. alsamixergui is available in synaptic. I kinda forgot about that as i got an audigy 2 zs card and everything has been perfect since :) (cept the surround sound coz i want to try get it to do stereo through all speakers as well)

and racepics that means that u've mucked something up in the gui for volumes. I think you should try them one at a time instead of all at once?

if its muting them again it could indicate that either those things don't exist on your soundcard or that you have nothing plugged into them? I'm not sure but its possible.

---

### Post by racepics on 2007-09-05
I've tried every combination of settings I can think of - I guess it must be some sort of hardware incompatibility.
I suppose I'll have to give Skype a miss for now.
Later versions of Ubuntu might be more compatible.
cheers
c

---

### Post by illuminaris on 2007-10-02
EDIT: Never mind. I must be slow, you solved the entire problem before I was finished typing my explanation.

---

