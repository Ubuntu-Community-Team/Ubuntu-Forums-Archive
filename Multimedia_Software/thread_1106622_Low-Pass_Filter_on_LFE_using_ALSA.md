---
title: "Low-Pass Filter on LFE using ALSA"
date: 2009-03-25
forum: Multimedia Software
---

### Post by maxim99 on 2009-03-25
I have ALSA working flawless on my system. All the channels assignments are correct.

The concern that I have is regarding the LFE channel. I use an application called XBMC to play video files and such. When I encounter a video that's is encoded with stereo sound XBMC reproduces the sound on all channels and distributes the sound appropriately.

It also distributes the sound to the LFE channel in full range audio.

I found this page here: [http://alsa.opensrc.org/index.php/Low-pass_filter_for_subwoofer_channel_(HOWTO](http://alsa.opensrc.org/index.php/Low-pass_filter_for_subwoofer_channel_(HOWTO))

However this only applies when the source is stereo, and the application is assigned to use the stereo PCM device.

I can copy paste the asoundrc config off of that page and it works without a hitch. However, i'm looking to have it apply at a higher level to the surround51 device.

I tried modifying the lowpass_21to21 device to 6 channels and changed the slave device to plughw:0,0 which would be the sound card. However, doing this seems to bypass the plugins.

This will be the first time i've used ladspa plugins with alsa is anyone else familiar with them and might be able to give me some pointers?

This is the config I thought would work but it seems the plugins aren't applied:```
pcm.lowpass51 {
    type ladspa
    slave.pcm default      
    path "/usr/lib/ladspa";
    channels 6
    plugins {
        0 {
            id 1098 # Identity (Audio) (1098/identity_audio)
            policy duplicate
            input.bindings.0 "Input";
            output.bindings.0 "Output";
        }
        1 {
            id 1672 # 4 Pole Low-Pass Filter with Resonance (FCRCIA) (1672/lp4pole_fcrcia_oa)
            policy none
            input.bindings.6 "Input";
            output.bindings.6 "Output";
            input {
                controls [ 300 2 ]
            }
        }
    }
}
```I would call the device using plug:lowpass51

---

### Post by maxim99 on 2009-03-28
I have no idea why this wasn't working for me before. Here is the final working configuration, with comments to explain various aspects.
```
pcm.lowpass51 {
    type ladspa                         # Define the type of device, this is plugin called ladspa
    slave.pcm "plughw:0,0";             # Defines the device the sound will be sent to, this being the hardware locator of the soundcard in question.
    path "/usr/lib/ladspa"              # This is needed for the ladspa plugin to tell it where the modules are.
    channels 6                          # Defines how many channels this device is, 5.1 or 6 channels.
    plugins {
        0 {                             # First plugin
            id 1098                     # Identity (Audio) (1098/identity_audio)
            policy duplicate            # This plugin's capability is pass-thru audio to the next plugin
            input.bindings.0 "Input";   # Only channel zero is called out becuase the module itself
            output.bindings.0 "Output"; # duplicates all channels when it's uses, so just one is needed.
        }
        1 {                             # Second plugin
            id 1672                     # 4 Pole Low-Pass Filter with Resonance (FCRCIA) (1672/lp4pole_fcrcia_oa)
            policy none                 # Standard policy? Not sure what this does exactly
            input.bindings.5 "Input";   # Defines which channels the plugin applies
            output.bindings.5 "Output"; # Channel 5 is alsa's LFE channel
            input {
                controls [ 250 2 ]      # Controls the cross-over frequency, and resonance. 250hz with 2 resonance
            }
        }
    }
}
```
Call this device by using the plug: prefix so for this device I would call "plug:lowpass51"

---

### Post by mas1o on 2011-05-19
I can use this in ubuntu 11.04? 
But here is pulseaudio?

---

