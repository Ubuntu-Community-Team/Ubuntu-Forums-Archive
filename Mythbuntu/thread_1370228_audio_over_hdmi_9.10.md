---
title: "audio over hdmi 9.10"
date: 2010-01-02
forum: Mythbuntu
---

### Post by benlyboy on 2010-01-02
Hi

I know this has been covered before I found quite a good post [here]("http://www.nvnews.net/vbulletin/showthread.php?t=116286&page=2"), It interested me because it was talking about the chip set on my mb ( GeForce 8200) they came up with an answer that seemed to work for them. But when I looked at using there idea I found that my Mythbuntu 9.10 didn't seem to have a asoundrc file. So I'm not sure where this leaves me?
 
 Any ideas :confused:

---

### Post by geekyhawkes on 2010-01-02
I hav sound working over the hdmi in mythbuntu with the same chipset.  Do you get no audio at all over hdmi?  Do you know what version of alsa you are running?  You could look here for an alsa upgrade script 

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Failing that you could create your own asound.conf allong the lines of this;



pcm.!default {
        type plug
        slave {
                pcm multi
                rate 48000
        }
        ttable.0.0 1.0
        ttable.1.1 1.0
        ttable.0.2 1.0
        ttable.1.3 1.0
}

#ctl.!default hdmiout

pcm.optical {
        type hw
        card 0
        device 1
}

ctl.optical {
        type hw
        card 0
        device 1
}

pcm.hdmiout {
        type hw
        card 0
        device 3
}

ctl.hdmiout {
        type hw
        card 0
        device 3
}

pcm.multi {
        type multi
        slaves.a.pcm "hdmiout"
        slaves.a.channels 2
        slaves.b.pcm "optical"
        slaves.b.channels 2

        bindings.0.slave a
        bindings.0.channel 0
        bindings.1.slave a
        bindings.1.channel 1

        bindings.2.slave b
        bindings.2.channel 0
        bindings.3.slave b
        bindings.3.channel 1
}

ctl.multi {
        type hw
        card 0
}



Bit of a frig but should work.  

Hope this helps.

---

### Post by SiHa on 2010-01-02
I have the 8200 chipset, and thanks to Larsolav for pointing me in the right direction, I fixed it like this:

> I should also mention that the first thing I did to get HDMI audio working at all was by first running "alsamixer" and unmuting the "HDMI" output (if it's got a green "00" you're good to go, if not press "m" to unmute it) after which I created "/etc/asound.rc" and wrote the following to it:


```
pcm.!default {
        type hw
        card 0
        device 3
}
```n.b. use "aplay -l" to find which card & device is your HDMI.


ie post #4 in [[COLOR="Blue"]_this_[/COLOR]](http://georgia.ubuntuforums.org/showthread.php?p=8010192) thread.

Although there isn't an asound.rc by default, it will be used if it's there.

After this, I had to change the audio device to alsa:default in MythTV.

---

### Post by benlyboy on 2010-01-02
Thanks for the reply

I went into alsamixer 

It's alsamixer v 1.0.20
interestingly it says my card is a "HDA Nvidia" and my chip is "Nvidia MCP78 HDMI", it is in fact a " GeForce 8200" chip set. I know that this maybe just a standed driver that covers my chip set but I thought I should ask? 

The other thing was there was no slide for "HDMI" Only a follows.

(master) (headphon) (pcm) (front) (front mi) (front mi) (surround) (center) (lfe) (side) (line) (cd) (mic) (mic boos) (iec958) (iec958 d) (iec958 1) (beep)


Any ideas...?:confused:

---

### Post by geekyhawkes on 2010-01-02
Mine doesnt show hdmi as a output either with the same chipset /driver name.  Can you confirm you have made an asound.conf as i posted above and restart alsa/the machine?  If not then definatly start there, if you have then from the sudo alsamixer can you confirm that all of the digital outputs are unmuted?  

By default on several machines i have noticed that the digital outputs seems to be muted.  M should toggle the mute/unmute option in alsamixer.

---

### Post by benlyboy on 2010-01-02
Hi geekyhawkes

No as of yet I haven't made the asound.conf file. that's my next move. I did use the script you linked to, to update the alsa drivers.
I like to make one change at a time, easier to know if something helped or if it didn't as the case may be. 

So later on tonight I will hook it back up to our LCD and see where I am.

If still no go then the  asound.conf file is my next move

thanks again for your help:)

---

### Post by benlyboy on 2010-01-03
Hi all

Well here an update,

I updated the driver, and now have version 1.0.21.

This made no real differents to the HTMI problem.

So I then used the asound file geekyhawkes posted  I didn't change it at all as it seemed to be set up right for my system (my HDMI is card 0,device 3).
There were a few things I wasn't sure on. One was what to name the file. Some posts called it a "asoundrc.conf" while others, yours included call it "asound.conf" 

The other thing was where to place it. Some post say it should go in "/etc" but others say it lives in "/home/user"

So I got around this by creating two files and placing them in both locations. I figured that the system would be looking for one file and wouldn't even see the others. 

Again no luck.

I was thinking I don't really know if the problem is that the sound card cant access the HDMI out, or if the program cant tell it to do so. Is there a way to test the sound card directly. Maybe a command line instruction?  

Thanks for your help :confused:

---

### Post by benlyboy on 2010-01-03
ok I was playing With "aplay" and tried "aplay -L" this gives you the pcms list. Don't know to much about what this is, but what was interesting was that HTMI has null under it? 

> default:CARD=NVidia
    HDA NVidia, ALC883 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)


does this help at all...?

---

### Post by myth_cougar on 2010-01-03
What is the output of [B]aplay -l

[/B]  I found with mine I had to do **sudo alsamixer -c 1 **to be able to unmute the hdmi output as mine is card 1 device 3.  I notice you put card 0 device 3, but thought it might be worth a check.

---

### Post by geekyhawkes on 2010-01-03
asound.conf is the name of the file. I still think the problem is a muted output rather than anything more serious if you have the updated alsa and the asound.conf file.

Can you confirm that form sudo alsamixer all of the digital outputs are unmuted ?  Cycle through them and pressing M will toggle mute/unmute.  Esc to exit and then try again.  Do you have any audio via hdmi from the ubuntu desktop if you quit out of myth?

---

### Post by benlyboy on 2010-01-04
ok I cleaned things up a little, and installed a copy of the asound file in /home/user and in /etc. I then opened alsamixer and made sure that every thing was unmuted. 

Then rebooted and I thought we had cracked it as there was no longer sound (from the pc speakers). I thought this may have been because sound was now rooted to the HDMI. but when I hooked it up still no sound.

The good news is that the asound file did make a difference when i renamed them the sound returned after a reboot.

any thoughts...?:confused:

---

### Post by geekyhawkes on 2010-01-05
Can you confirm you have no audio in both ubuntu and myth?  I would double check every output is unmuted in both alsamixer from terminal but also the audio manager within ubuntu when you exit out of myth.  I had a lot of faff initially sorting the hdmi audio as the outputs kept muting.

---

### Post by benlyboy on 2010-01-06
Hi 

Yes can confirm no audio out of myth or ubuntu. 
The asound.comf file placed in /etc does change things. in that I loss my sound output from the sound jack. The HDMI still doesn't work though.

I went into alsamixer, none of the inputs were muted however some had there slides right down so I turned every thing up to full. After reboot they do return to there low setting. However low or high make no differents.

One thing I have been thinking about could it be the TV?
The TV is a LG 46inch lcd about two to three years old, are there different standeds for HDMI? 

I may try another tv if I can find one. However I am not about to go out and buy another tv so it may be a mute point, if i can't get it working with my tv there is no point in having it.

---

### Post by geekyhawkes on 2010-01-06
I would be suprised if it is your tv to be honest.  Cable is more likely but its difficult to work out whats going on if you havent got another hdmi source (ie dvd player) to try. Out of interest which version of the nvidia drivers are you using?

---

### Post by ginjaninjaa on 2010-01-06
had the same problem with the 8200 chipset

(iec95:cool: (iec958 d) (iec958 1) 

i then enabled the  ICE958  2 in the switches part of the mixer and then sound came on the TV :) over hdmi, but still no volume controls

hope this helps

---

### Post by benlyboy on 2010-01-06
I will play with the switches and see if that helps. Thanks for the idea.

My drivers are
alsa 1.0.21  
Nvidia 173.14.20  

Thanks again for all the help

---

### Post by benlyboy on 2010-01-07
Hi just wanted to say thanks to geekyhawkes and everyone else that helped me with this problem

The good new is I got it working last night. I last piece of the puzzle I found  [here]("http://ubuntuforums.org/showthread.php?t=1285957"), I updated to Repo Build .22 then tried again. Still no luck, but then I went into control center and looked at the video driver manager and found that since I had updated it no longer showed that I had the recommended driver. So I updated to the recommended driver and there you go, it worked.

Thanks again for the help

---

### Post by Dewey_Oxberger on 2010-01-07
Nab you a copy of the asound.conf file from this post:

[http://ubuntuforums.org/showthread.php?p=8184659#post8184659]("http://ubuntuforums.org/showthread.php?p=8184659#post8184659")

Then see if the instructions in the file are clear enough.  If not post back here.

---

### Post by Dewey_Oxberger on 2010-01-07
LOL - doh, didn't see you'd already fixed it.

---

### Post by danimaldaisy on 2010-08-29
I have a different solution that doesn't require ANY hacking or TWEAKS!!!!        This is from a CLEAN INSTALL!!!!

First you need to set the audio output to "Digital Stereo (HDMI) output" under System\preferences\sound

then you need to open up a bash shell and type "sudo alsamixer" and un-mute anything that is labeled "spdif" or "IEC958" by simply using the arrow keys to navigate and then pressing the "M" key on the keyboard to un-mute.

Lastly install the proprietary nvidia driver.

If you do not do it in this order in ubuntu 10.04lts than you are screwed because the audio will never work no matter what you do.

if you fail to do it in order...don't expect help from me...i just went through 9 installs just to prove my results.

hope this helps someone desperate enough to get audio over HDMI working on their shiny new LCD TV

WARNING!  do not screw with the settings after this.

In mythtv dont forget to set the audio as HDMI.....its default is ALSA:default

---

