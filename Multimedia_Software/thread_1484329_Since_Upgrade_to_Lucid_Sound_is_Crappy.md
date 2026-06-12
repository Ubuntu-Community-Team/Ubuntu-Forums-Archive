---
title: "Since Upgrade to Lucid Sound is Crappy"
date: 2010-05-15
forum: Multimedia Software
---

### Post by kelocena on 2010-05-15
Okay. So, I managed to fix my craptastic sound. And now... *drum  roll* the juicy details!

[SIZE=5]_The Problem_[/SIZE]
Poor sound quality after upgrading from Karmic to Lucid. I did not have a  problem with literally no sound, nor was my sound muffled. It was  just... bad. I don't know any other way to put it. My headphones played just fine, though. ALSA is a cruel mistress.

[SIZE=5]_The Specs_[/SIZE]
I'm using a Lenovo IdeaPad Y530 with HDA Intel. Frankly, it doesn't  matter much because the solution could probably be applied to many different models and sound cards. Heck, if you have no sound at all, this may may still work.

[SIZE=5]_The Solution_[/SIZE]
On top of doing a little bit of my own jiggerpokery (only not really), I  used information from two different guides.

**_STEP 1_** :: Now, so we're all on the same page here, you need to double check which version of ALSA you're running. If you haven't touched it since  the Lucid Lynx upgrade/install it should be 1.0.22. But do this anyway!  Open up the Terminal (Applications->Accessories->Terminal) (mine's  hot pink c: ). There are actually two parts to this step:
....... a) run **cat /proc/asound/version**
If your terminal returns that your ALSA version is indeed 1.0.22, then  you'll want to upgrade to 1.0.23. In fact, simply doing this may solve  your sound problems, but if it does not, then waltz on back over here. [_Linky, linky to upgrade_.]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") If you're already 1.0.23, then let's move on!
....... b) run **wget -O alsa-info.sh  [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh**
It's going to ask if you want to give permission to send info to  alsa-project.org. Say yes. The URL it gives you contains tons of  information on your sound setup beyond just your current ALSA version. Find the section that looks something like this:
> !!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23In my case, the utilities version was still 1.0.22 after following the basic instructions in the script upgrade guide, so I upgraded that, too. It's probably not terribly important, but you might as well do it for "teh lulz." In terminal, go back to whichever directory you unpacked the script in (**cd <insert directory here>**). Then run **sudo ./AlsaUpgrade-1.0.23-2.sh -t** .

**_STEP 2_** :: I'm going to link you to a helpful, but slightly outdated guide. But first, in separate tabs, open [_ALSA-Configuration.txt_]("http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=bfcbbf88c44dd7da7c9a0fc161308d173a7d1a36;hb=0c8e73dc82fce0832b7b85bf5a06d9fbfd27a31b") and [_HD-Audio-Models.txt_]("http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/HD-Audio-Models.txt;h=1d38b0dfba95f6138038716f215991c0f7fd6be9;hb=0c8e73dc82fce0832b7b85bf5a06d9fbfd27a31b"). So when he mentions ALSA Configuration, turn to the one I linked you to and at the point he says "Now take a look at ALSA-Configuration.txt  again, and you will find a section that looks like this, which matches up with my soundcards codec:" turn to the HD Audio Models document* I linked to instead.
.......... [_Sound Troubleshooting Guide_]("https://help.ubuntu.com/community/SoundTroubleshooting")
*You may not find your exact model on the list. I didn't. However, for example, I'm using a Lenovo so I tried all the Lenovo models that matched my codec until I found one that worked (I found two, actually). Remember, you have to save your changes then reload ALSA every time. If you've tried all your manufacturer's models that have the same codec as yours with no luck, give up and move on; the following steps may solve the problem.
.......... Stop before you hit the Manual Installation section (for now, anyway). I'd like to make note of something first. After I added that "options <driver> model=" line to my config, upon reloading ALSA I got an error message saying that it couldn't load the driver I needed (snd-hda-intel in my case). Then I had *no* sound, which was a lot of fun. If you received a similar error, then manually starting the driver isn't going to do diddly.
.......... So if you received a "couldn't load <your driver>" error, move on to step 3 of this guide. If you did *not* receive an error and are still having trouble with sound, you might want to try following the instructions for manually starting your audio driver before moving on to step 3 if necessary.

**_STEP 3_** :: Return to the troubleshooting guide and this time hop, skip, and jump on down to ALSA Driver Compilation. You can try following his instructions for using the module-assistant. I found that it didn't work because it couldn't find a certain directory. It's worth a shot, if you feel like wasting time.
.......... I found it much easier to just use these commands:
> cd /usr/src/Alsa-1.0.23/alsa-driver-1.0.23
sudo ./configure
sudo make
sudo make installThat will basically re/compile and re/install all the drivers that come with ALSA 1.0.23. I don't recall if I had to reload, but you may want to run **sudo alsa force-reload** just in case. Now regardless of whether or not you skipped "Manual Installation" you'll probably have to go back and try finding the correct model for the "options <driver> model=" line again.

If this doesn't work for you, I don't know what to say. Sorry.

---

### Post by ensleepent on 2010-05-15
I'm having a similar problem, and this is the only thread I've found so far that seems to be on the same page as me.  Fresh installation of Lucid, headphones sound fine, speakers sound like a dying elephant.  The sound is so screwy I can't hear what people are saying, etc.  And I know the speakers were working fine before.

The computer in question is an old Gateway Performance 1400 with all the RAM it can take.

"aplay -l" gives me:

> card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
I, for one, have run out of ideas.  Not that I know as much about computers as I wish I did.

If there's anything else anyone would like me to quote from the commandline, let me know.  There's probably more information available via the terminal than I'm aware of.

At least, for now, I can use the headphones if there's anything I really want to hear.  :)

---

### Post by kelocena on 2010-05-16
Well, I'm glad I'm not the only one with this problem. Hopefully there's someone out there more computer/Ubuntu savvy who has it, too, and can figure out to fix it.

I talked to a friend of mine today who's quite Linux-savvy and he says there was probably a module or kernel (or something) the devs thought was no longer necessary, so they removed it in this upgrade. According to him, it's a vicious cycle. "Something gets changed/removed because they think it's not needed, people cry, so then they put it back in."

So I'm told it's just a matter of time before someone finds a fix, but then it'll be an extra month or two after for it to be determined "stable" enough to be "officially" included in Ubuntu's updates. And that's probably not far off.

Also, I'd like to add that GNOME's volume control icon disappeared and can now only be run via the terminal. I'm sure these bugs/issues will be fixed soon, as there seems to be a lot of people who experienced sound problems after upgrading/installing Lucid Lynx.

---

### Post by lidex on 2010-05-16
> **kelocena said:**
> 
Also, I'd like to add that GNOME's volume control icon disappeared and can now only be run via the terminal. I'm sure these bugs/issues will be fixed soon, as there seems to be a lot of people who experienced sound problems after upgrading/installing Lucid Lynx.

Right-click on the panel, select add to panel> indicator applet

---

### Post by kelocena on 2010-05-16
> **lidex said:**
> Right-click on the panel, select add to panel> indicator applet
I tried that after it first happened.. It doesn't work.

---

### Post by lidex on 2010-05-16
Make sure you have installed:
```
gnome-control-center
gnome-media
gnome-media-common
gnome-system-tools
indicator-applet
indicator-applet-complete
indicator-applet-session
indicator-application
indicator-session

```
Log out/in

---

### Post by kelocena on 2010-06-02
I've solved this problem and updated the first post with the solution. So if a mod could slap a [SOLVED] on this, that'd be peachy C:

Should I mention my issue in the upgrade script thread? Because for me the problem partly seemed to be that for one reason or another, the drivers weren't properly compiled or installed after using the script. I still have the logs.

---

### Post by alphacrucis2 on 2010-06-02
> **kelocena said:**
> I've solved this problem and updated the first post with the solution. So if a mod could slap a [SOLVED] on this, that'd be peachy C:



You don't need a mod to mark your own thread as solved. You can do that yourself.

---

### Post by kelocena on 2010-06-02
> **alphacrucis2 said:**
> You don't need a mod to mark your own thread as solved. You can do that yourself.
Really? Where's the option? I don't see it T_T

...Never mind. Found it. *headdesks*

---

### Post by SanjoEel on 2010-07-07
Thanks for the info it helped me get my sound working in lucid!

---

### Post by chrone on 2010-07-30
thanks dude, i think this updated alsa-driver helped me solved my mp3 skipping problems on lucid with amd 780g chipset and realtek alc889a onboard soundcard from gigabyte. :)

---

