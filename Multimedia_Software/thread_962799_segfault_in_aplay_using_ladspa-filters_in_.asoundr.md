---
title: "segfault in aplay using ladspa-filters in .asoundrc"
date: 2008-10-29
forum: Multimedia Software
---

### Post by -AB- on 2008-10-29
hey all, 

my external active frequency crossover just broke down yesterday, the right high frequency channel is dead.

some time ago i read some article about [using ladspa to split off the subwoofer channel ]("http://alsa.opensrc.org/index.php/Low-pass_filter_for_subwoofer_channel_(HOWTO)") - so i hought i can do that as well and split up 2 channels to 6 and filter them, all before the sound even gets translated to an analogue signal.

so i made a test setup - but "it doesn't work" - to be precise, aplay crashes with a segfault when i try to handle more than 2 channels.


first of all, the working .asoundrc configuration:

```

pcm.split_channels {
     type plug
     slave.pcm filter
     slave.channels 2
     ttable {
         0.0     1       # hi left
         1.1     1       # hi right
#         0.2     1       # mid left
#         1.3     1       # mid right
#         0.4     1       # lo left
#         1.5     1       # lo right
     }
 }

pcm.filter {
    type ladspa
    slave.pcm finish
	#slave.pcm "plughw:0,0";
	#slave.pcm surround51
    path "/usr/lib/ladspa"
    channels 2

    plugins {
        0 {
            id 1098 # Identity (Audio) (1098/identity_audio)
            policy duplicate
            input.bindings.0 "Input";
            output.bindings.0 "Output";
        }
        1 {
            id 1904
            policy none
            input.bindings.0 "Input"; #left
            output.bindings.0 "Output";
            input {
                controls [ 200 0.755 ]
            }
        }
        2 {
            id 1904
            policy none
            input.bindings.1 "Input";#right
            output.bindings.1 "Output";
            input {
                controls [ 200 0.755 ]
            }
        }
    }
}

pcm.finish {
	type plug
	slave.pcm "hw:1,0";
}

```

so i send the split_channel result to filter, and then to finish. this setup works.

when i switch the 2 channels in split_channels to 6 or some other value [2..6] (leaving the value in filter as it is) results in a complaint about bad settings (as it should)

when i adjust the value in filter as well i get a segfault in aplay:

ab@pcab:~$ aplay -v -D split_channels daslied.wav
Playing WAVE 'daslied.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
Segmentation fault

so, what might be the problem? the card is a cheap C-Media 5.1 card... a driver problem maybe?

btw, my soundcards keep switching places (i have 2 - 1 onboard (even worse) and 1 pci) and aplay -l shows them in random order after reboot... how to fix that?

attached you'll also find the original files...

thanks for all help :)

---

