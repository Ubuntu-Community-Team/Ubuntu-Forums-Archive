---
title: "2 Apps -- 2 Sound cards -- 2 Output Jacks"
date: 2009-08-18
forum: Multimedia Software
---

### Post by brookie on 2009-08-18
Hello and good afternoon everybody, 

Has anybody set up Intrepid with 2 sound cards (one onboard, one PCI), so that one app can play through one card and another app play through the other card without constantly switching output jacks? 

For example:
1. Play Banshee through my PCI sound card (Creative Audigy 2 ZS Notebook) for music
2. Play Totem through my on-board sound card (Intel) for movies


**Note - I actually got it to work temporarily by accident:
With initial setting in sound preferences/music and movie sound playback set to use Audigy 2 ZS Notebook...OSS

1. 
* Start banshee and play a song 
* Banshee plays out of the Audigy sound card out to my stereo and attached speakers

2. 
* Open up sound preferences, and switch sound playback for music and movies from Audigy 2 ZS Notebook...OSS to PusleAudio Sound Server. 
* Start Totem and play a movie. The movie sound plays out of my on board Intel sound card out to my TV.

At this time Banshee plays out of my Audigy sound card while Totem plays out of my on board sound card simultaneously. 

If I reboot it doesn't work anymore. Banshee and Totem will use whatever driver was selected last (in sound preferences/sound playback for movies and music) and play out of the Audigy card. 


This would be a cool set up so I don't have to switch my output jacks all the time. In essence, I'm trying to set the 1st sound card to use one driver and and the 2nd sound card to use another driver (I think? :confused:).


Any ideas on how I can make this work? I have searched all the comprehensive sound solutions and I still can't figure out how to make it stick. 

I would appreciate any input or output (pun intended...hehehe :P) you all may have. Thanks in advance and sorry if it sounds confusing. 

Cheers,
brookie

---

### Post by markbuntu on 2009-08-18
That is very easy to do when you have pulseaudio set up correctly. I have on-board sound and a pci card and a usb headset and usb webcam and they all work and I can switch apps around with just a few clicks.

Read this if you are using Intrepid or Hardy

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by brookie on 2009-08-18
Thanks markbuntu! Everything is working but some strange happenings to report. 

1. Gnome Alsa mixer errors when opened - shows STAC9750,51 on one tab, and a skinny tab with no name (this is my Audigy card).  

Here is the error:
An error occurred while loading or saving configuration information for GNOME ALSA Mixer. Some of your configuration settings may not work properly.

Details:
```
ad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9750,51-Master": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9750,51-Master": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9750,51-Master_Mono": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9750,51-Master_Mono": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9750,51-Headphone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9750,51-Headphone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9750,51-3D_Control_-_Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9750,51-3D_Control_-_Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9750,51-3D_Control_-_Depth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9750,51-3D_Control_-_Depth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9750,51-PCM": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9750,51-PCM": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9750,51-Line": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9750,51-Line": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9750,51-CD": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9750,51-CD": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9750,51-Mic": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9750,51-Mic": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9750,51-Video": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9750,51-Video": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9750,51-Phone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9750,51-Phone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9750,51-IEC958_Playback_AC97-SPSA": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9750,51-IEC958_Playback_AC97-SPSA": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9750,51-PC_Speaker": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9750,51-PC_Speaker": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9750,51-Aux": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9750,51-Aux": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9750,51-Capture": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9750,51-Capture": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9750,51-3D_Control_-_Switch": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9750,51-3D_Control_-_Switch": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9750,51-PCM_Out_Path___Mute": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9750,51-PCM_Out_Path___Mute": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9750,51-Mic_Boost___20dB_": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9750,51-Mic_Boost___20dB_": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9750,51-Mic_Select": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9750,51-Mic_Select": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9750,51-IEC958": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9750,51-IEC958": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9750,51-Mono_Output_Select": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9750,51-Mono_Output_Select": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9750,51-Mix": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9750,51-Mix": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9750,51-Mix_Mono": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9750,51-Mix_Mono": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9750,51-External_Amplifier": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9750,51-External_Amplifier": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/SigmaTel_STAC9750,51": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_names/SigmaTel_STAC9750,51": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/": Key/directory may not end with a slash '/'
Bad key or directory name: "/apps/gnome-alsamixer/display_names/": Key/directory may not end with a slash '/'
```

2. Can I fix this error, and if not should I uninstall the gnome alsa mixer? 

3. Pulse Audio applet is working but the output devices show as:
ALSA PCM on front:0 (Intel 82801DB-ICH4) via DMA - this is the onboad card, easy to understand

but...
ALSA PCM on front:2 (ADC Capture/Standard PCM Playback) via DMA - this is my Audigy card but the name does not show. 

The pulse applet works great with the simultaneous setting but I have to open up the volume control to adjust the volume on my Intel card. My default for my keyboard is the Audigy for music. 


So, a recap on the issues I saw were: 
1. the errors when I open gnome alsa mixer, click ok on error box and mixer works.

2. the tab for the Audigy card has no label in the gnome alsa mixer, just a blank skinny tab.

3. pulse applet volume control works but the names of the two sound cards on the output devices tab are not user friendly or intuitive. 

4. i need to right click on the little speaker/volume control and select the ALSA Intel mixer to adjust volume for Totem movies, since I have the Audigy set up as the Default mixer in System/Preferences/Sound. 

It's all kinda funky, but the simultaneous output works great, and both cards work, no more switching jacks. I just have to streamline volume control, watching/listening to flicks on totem via the on board Intel. Playing tunes in Banshee and adjusting volume via keyboard set to default mixer works like a charm. 

If you have any other suggestions about this set up or th gnome alsa mixer issue please let me know. 

Thanks again man! It's not perfect but it works! :-)

---

### Post by markbuntu on 2009-08-18
Well, the pulseaudio version for Intrepid is very old and a lot of functionality has been added since, like names for the Output devices. When Koala comes out in October it will be a lot more fun.

The gnome alsa mixer worked for me the last time I used Intrepid which was some months ago so an update may have kludged that. I don't have Intrepid anymore so I can't test it. The gnome alsa mixer controls the alsa drive the same as the panel volume control or the cli alsa mixer. I just thought it was easier to use but the other methods are just as good for controlling the sound hardware.

But anyway, it is good to learn that it still basically works for Intrepid users and got your problem fixed.

regards,
mark

---

