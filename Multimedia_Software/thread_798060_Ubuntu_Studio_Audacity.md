---
title: "Ubuntu Studio Audacity"
date: 2008-05-17
forum: Multimedia Software
---

### Post by nlavon on 2008-05-17
I am trying to use Audacity in the Ubuntu Studio Suite.

"Error Opening Sound Device, check input device settings and the project sample rate."

I have an SB 5.1 Live Sound Card which works (I hear sounds and can play multimedia) but what do I use to configure the audio device. There are close to 10-12 choices. Any suggestions on how to configure this device so I can record some sound?

I also get lots of error messages in the ALSA Sound Mixer. In Terminal, I see the Sound Blaster Linux Driver installed not Sigma Tel. Sigma Tel is my onboard audio and I have the onboard audio disabled in the BIOS. So I'm a little confused. Here are the error messages in Alsa Sound Mixer

Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Master": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Master": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Headphone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Headphone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Bass": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Bass": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Treble": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Treble": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-3D_Control_Sigmatel_-_Depth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-3D_Control_Sigmatel_-_Depth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-3D_Control_Sigmatel_-_Rear_Depth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-3D_Control_Sigmatel_-_Rear_Depth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-PCM": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-PCM": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Synth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Synth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Wave": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Wave": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Wave_Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Wave_Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Wave_LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Wave_LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Wave_Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Wave_Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Line": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Line": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Line_LiveDrive": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Line_LiveDrive": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Line2_LiveDrive": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Line2_LiveDrive": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-CD": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-CD": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Mic": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Mic": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Video": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Video": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Phone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Phone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-IEC958_Coaxial": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-IEC958_Coaxial": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-IEC958_LiveDrive": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-IEC958_LiveDrive": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-IEC958_TTL": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-IEC958_TTL": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-PC_Speaker": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-PC_Speaker": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Aux": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Aux": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Capture": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Capture": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-AC97": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-AC97": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Sigmatel_Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Sigmatel_Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9708,11-Headphone_LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9708,11-Headphone_LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9708,11-Headphone_Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9708,11-Headphone_Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9708,11-Tone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9708,11-Tone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9708,11-3D_Control_-_Switch": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9708,11-3D_Control_-_Switch": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9708,11-Mic_Boost___20dB_": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9708,11-Mic_Boost___20dB_": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9708,11-Mic_Select": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9708,11-Mic_Select": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9708,11-IEC958_Optical_Raw": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9708,11-IEC958_Optical_Raw": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9708,11-Mix": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9708,11-Mix": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9708,11-Mix_Mono": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9708,11-Mix_Mono": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9708,11-External_Amplifier": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9708,11-External_Amplifier": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9708,11-SB_Live_Analog_Digital_Output_Jack": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9708,11-SB_Live_Analog_Digital_Output_Jack": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9708,11-Sigmatel_4-Speaker_Stereo": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9708,11-Sigmatel_4-Speaker_Stereo": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9708,11-Sigmatel_Output_Bias": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9708,11-Sigmatel_Output_Bias": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9708,11-Sigmatel_Surround_Phase_Inversion_Playback_": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9708,11-Sigmatel_Surround_Phase_Inversion_Playback_": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/SigmaTel_STAC9708,11": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_names/SigmaTel_STAC9708,11": `,' is an invalid character in key/directory names

Any help or guidance gratefully appreciated. Sorry for the long error message. New to Ubuntu but enjoying it!

Neal Lavon
Takoma Park, MD
USA

---

