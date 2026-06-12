---
title: "9800 GX2:, Only allows one display in ubuntu!"
date: 2008-12-15
forum: Multimedia Software
---

### Post by AronShultz on 2008-12-15
Hi, I am a little new to linux, I recently recieved a Nvidia 9800 GX2 as a gift, I installed it in my computer and it works fairly well in windows. under Ubuntu, I cannot use more than one monitor. in the nvidia configuration, it only gives me an option to set the second monitor it detects as a seperate x screen, and not twinview, which i would preffer.

after rebooting in to windows, and tinkering with the Nvidia control panel, I found that the card itself had SLI enabled, and would not allow more than one screen  unless SLI is disabled. When SLI under windows is disabled, the Display manager detects three different screens (my monitor on port one,my monitor on port 2, and, i think, my tv on the HDMI.)

I just want to know how to gain multiple monitors under ubuntu with this card. (ubuntu desktop is more comfortable to me:) not afraid to get technical, and will supply information that will be beneficial.
thanx

---

### Post by acalafra on 2008-12-15
do you have the package nvidia-settings installed?


sudo apt-get install nvidia-settings

You can change settings from the gui but to save over the xorg.conf file you need to run it as root but you should probably backup you xorg.conf file incase of catastrophe.

cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backedup

then you can run a

gksudo nvidia-settings 

it should let you switch to twin view. it will require an x-restart

ctrl-alt-backspace

This is all pretty risky business and shouldnt be attempted lightly. and certainly not without double checking this stuff. im not an authority on here but thats how i got it to work. see attached screenshot.

---

### Post by AronShultz on 2008-12-15
I tried, but that didnt work, I actually have an 8500 gt, and it works with twinview just fine, I have the Nvidia settings, and it doesnt allow twinview. thanks anyways. I am starting to believe that it is in SLI mode, and I need a way to specify for it to STOP focusing both GPUs on the first monitor. so, if anyone can tell me how to control this feature, it would be great.

---

### Post by acalafra on 2008-12-20
Yeah i read that particular card behaves as though it were two cards in SLI and apparently SLI causes headaches with dual screens. I've never had enough money for SLI so no real experience there. also people seem to be having the same problem with that card dual screening even in windows. complain to nvidia i guess. sorry man, but I bet that card is still sweet to just look at.

---

### Post by Armaron on 2009-02-18
In my case (yes, nVidia 9800 GX2), TwinView is greyed out. So even with the nvidia-settings I can't do anything. :(

Anybody got a fix for this?

---

### Post by Armaron on 2009-02-19
bump

---

### Post by amrbekhit on 2009-03-28
bump, got this same problem

---

### Post by KuroSatsu on 2009-04-02
I have the same issue (and the same card).  From my reading it seems that it has something to do with the multi-gpu nature of the card.  Instead of both monitors being run off of one of the GPUs, it will instead connect one monitor to GPU-0 and the other to GPU-1.

Does anyone know if there's a way to change this, or modify the xorg.conf to do this?

Alternatively, you can use Xinerama to give you the dual-view you'd be used to in Windows (can drag windows to the other screen).  The only problem with this is that you can't enable visual effects (can't enable composite) with Xinerama on.  That kind of upsets me since I want to try that stuff out, but no one has a resolution yet (except, use TwinView, but I don't have the slightest idea how to tie my monitors to only 1 GPU to even get the option to enable TwinView).

Anyway, if you're ok with not having the visual effects here's how to enable Xinerama:

Open the Terminal
Applications->Accessories->Terminal

```

user@computer~$: sudo nvidia-settings
```

The NVIDIA X server settings window should pop up.  
1. Under 'X Server Display Configuration" click on the 'Disabled' monitor.
2. Click 'Configure' and select 'Separate X screen' and click 'OK'
3. Check the check box next to 'Enable Xinerama'
4. Click 'Save to X Configuration File' and click 'Save'.
5. Restart X (or whatever they call it) by logging off and then logging back on (don't have to do a full system restart). 

Some people would tell you to do the CRTL-ALT-Backspace thing to restart X.  I don't like that, I just log out and log on again, does the same thing for the most part.

I'm pretty sure that's all the steps.  If anyone hears or knows how to enable the TwinView thing for us though (so I can do visual effects), please let us know.

---

