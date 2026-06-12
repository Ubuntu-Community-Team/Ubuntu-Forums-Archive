---
title: "any how to for Audio through HDMI ATI Radeon HD 3200 ?"
date: 2009-01-07
forum: Mythbuntu
---

### Post by jeremycobert on 2009-01-07
well ive got pretty far so far without too many problems, but i still cant get the audio to work through my hdmi cable. ive been using ubuntu for about a year and feel comfortable with it, but xubuntu has been a slight adjustment.

i have the restricted drivers enabled and alsa mixer shows the device IEC958 but there are no volume sliders for it. i cant hit "M" to mute it but unmuting it does nothing.
aplay -l shows this.

card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

its funny that when i boot the machine up i can hear a slight audio "pop" almost like the drivers initiating.. but no sound.

any help is appreciated. if i can just get past this sound issue i will be a very happy camper.

---

### Post by onehotcutey on 2009-01-07
I have the ATI Radeon HD 3200 integrated into my motherboard.  The audio through HDMI worked straight away with a fresh Intrepid installation.

The things I did do before testing the audio were to turn on the HD audio options in BIOS and then in a terminal I ran alsa-mixer and un-muted the playback mixer.  I wasn't given the option of adjusting the volume, but it worked just fine.

I'll look through my setup and see if there is anything else I did to make it work.

Daniel

---

### Post by jeremycobert on 2009-01-07
thanks for looking, i did run this in the command prompt and got audio.
```
aplay -D plughw:1,3 tada.wav
```
so i know the hdmi audio is working ! i just cant seem to set it as my default audio playback. im not familiar with xubuntu yet. i cant find the volume control. i found the volume settings and alsa mixer, but its not quite the same as ubuntu 's volume control.

i was reading this [http://alsa.opensrc.org/index.php/DigitalOut#MythTV](http://alsa.opensrc.org/index.php/DigitalOut#MythTV)
and i think i might try to set it as the audio in mythbuntu. i really dont need audio in anything else as this is going to my media center and not a user machine.

seriously , thanks for the help.

---

### Post by lglenn on 2009-02-06
OK, I have just been through this dance as well, here are the steps that I took to get audio to work over HDMI. I hope this saves someone else a few hours!

I have a Gigabyte GA-MA78GM-S2H motherboard, BTW. 

1. Installed Mythbuntu 8.10 (Ubunto 8.10)

2. Installed the proprietary ATI driver, via the Hardware Drivers control panel. 

3. From the command line, ran aticonfig --initial --input=/etc/X11/xorg.conf

(** steps 2 & 3 were really just to get X windows working properly with the ATI driver, but I'm pretty sure you need to have the full-on ATI driver going to make all this work. Most probably, you've already gotten that far. **)

3. aplay -l lists audio devices: 

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

...from this, you can see that determine that HDMI out will be plughw:1,3 (that is, card 1, device 3). As mentioned above, it has to be plughw, not just hw. 

4. Run sudo alsamixer -c 1

5. There's no option to raise/lower volume, but you can un-mute by hitting 'm'. If you see a box at the bottom of the terminal window with 'mm' in it, you're muted. If it contains '00', you're un-muted.

6. Hit esc to quit. 

7. Run aplay on a .wav file to test, like so: sudo aplay -D plughw:1,3 <soundfile>. If your device number was different, use that. 

8. Assuming that all works, edit /etc/asound.conf (which may not exist yet), put this in it: 

pcm.!default {
        type hw
        card 1
        device 3
}

Again, use your device numbers. Now the 3200 HDMI is your default audio out. 

The Alsa wiki page on Digital Out ([http://alsa.opensrc.org/index.php/DigitalOut#MythTV](http://alsa.opensrc.org/index.php/DigitalOut#MythTV)) was super-helpful.

---

### Post by zosky on 2009-05-31
this was what i needed for my HTPC. 
thank you. Thank you. Thank you!!!
i dont have a TV signal, so no myth lovin' 

1. Ubuntu Jaunty Minimal 
2. ati driver - [_method 2 (command line)_]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually")
  (( /etc/X11/xorg.cong [_from this post_]("http://www.gossamer-threads.com/lists/mythtv/users/380414#380414") ))
3. aplay -l lists audio devices:  ... exact same as above
 
> **lglenn said:**
> 4. Run sudo alsamixer -c 1

[INDENT]THIS IS THE GOLDEN STEP. 
its missing from all other guides out there !!! 

the default [-c 0], that you get with "alsamixer" is Card/Chip= **HDA ATI SB** / Realtek ALC1200. 
this contains **2x IEC958** + 10 more... but no control for HDMI sound. ???

'aslamixer **-c 1**' ... Card/Chip= **HDA ATI HDMI**/ ATI ATI RS690/780 HDMI 
this contains only IEC958 ... unmute ... BINGO![/INDENT]
4. sudo apt-get install xbmc xbmc-live + all the deps 

bingo-bango a kick-*** HTPC in the living room. 
i was about to crack and replace the mobo with nV
thanks lglenn for saving me some $$$

---

### Post by angry_norwegian on 2010-05-04
Thanks alot, Iglenn, step 8 did it for me on Xubuntu.

---

### Post by gunnarflax on 2011-03-09
I'm having the same problem except with the Gigabyte GA-880GM-UD2H motherboard (ATI graphics). I've done all the steps but I still get stuttering sound (VERY) when viewing over the HDMI connection (which I must use). Please help!

---

### Post by jherm on 2012-02-05
lglenn, thank you so much for the details. Your directions are still applicable to Oneiric 11.10. I ended up using 'plughw:1,3' with AC3 and DTS enabled in XBMC. Enabling AC3 prior to that would make XBMC throw an "Error initializing sound card" with no audio out.

See also:
[http://wiki.xbmc.org/index.php?title=HOW-TO:Install_a_Miminal_Ubuntu_and_XBMC_with_sound_over_HDMI_on_the_AppleTV#Set_up_the_HDMI_audio_output](http://wiki.xbmc.org/index.php?title=HOW-TO:Install_a_Miminal_Ubuntu_and_XBMC_with_sound_over_HDMI_on_the_AppleTV#Set_up_the_HDMI_audio_output)

---

### Post by sportzfan28 on 2012-02-25
hello all, first time poster, long time fan :)

I am actually running open SuSE, however this tutorial was very helpful for a newbie such as myself.  The only problem I'm having is at the very end when I need to edit etc/asound.conf

in openSuse I have a file called etc/asound-pulse.conf which has the pulse as the default.  

So my question is obviously will these two files conflict with each other? Should I just edit the pulse.conf and add/change it's default?  

This may be a really stupid question, but as I said, I'm new to linux so please be gentle :)

Thanks!

---

