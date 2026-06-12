---
title: "alsa low-pass filter cutoff frequency asound.conf ladspa !!"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by chris_x1 on 2008-04-04
hi there :)
i hope someone out there can explain a bit of code for me. the code below is my asound.conf (or .asoundrc) file (with extra comments)
For 2.0 stereo input, it adds a subwoofer channel with low-pass filter and high-pass filters the first two 
channels. but im not entirely sure how!

please have a read of the comments too, to know what i mean

i used these examples and others to learn the code:
alsa.opensrc.org/index.php/Low-pass_filter_for_subwoofer_channel_(HOWTO)
[http://forums.gentoo.org/viewtopic-p-4528619.html#4528619](http://forums.gentoo.org/viewtopic-p-4528619.html#4528619)
[http://forums.gentoo.org/viewtopic-t-578294.html](http://forums.gentoo.org/viewtopic-t-578294.html)

```
 >>>define the default device "3channels"  which takes channels 1 & 2 and creates a third

pcm.!default {
          type plug
          slave.pcm 3channels
      slave.channels 3
      ttable.0.0     1       # left channel
          ttable.1.1     1       # right channel
          ttable.0.2     0.5     # third channel (1st half)
          ttable.1.2     0.5     # third channel (2nd half)
          }

>>>define a device "filtered"  where channels are filtered (get these filters by installing LADSPA, BLOP
& CMT) I dont know how the correct channels are filtered here, how is input.bindings.0  taking 
channels 1 & 2 only and keeping them separate? adding a second plugin with input.bindings.1 (for 
channel 2 I thought) causes the whole code to be ignored by alsa, and naming the second plugin "1" 
doesnt work either, has to be 3 or 4!! do you know whats going on here??

pcm.3channels      {
    type ladspa
    slave.pcm filtered
    path "/usr/lib/ladspa"
    channels 3
    plugins       {
     
      0 {
         id 1052  # High-pass filter
         input.bindings.0 "Input";
         output.bindings.0 "Output";
         input {
            controls [ 150 ]
         }
      }

      3 {
         id 1671  # Low-pass filter.
         policy none
         input.bindings.2 "Input";
         output.bindings.2 "Output";
         input {
            controls [ 150 3]
         }
      }

                 }
             }
         
>>>send the filtered channels to the surround51 device, although i only have 2.1 system so only need
 the shorter ttable

pcm.filtered {
    type plug
    slave.pcm surround51
    slave.channels 6
    ttable {
        0.0     1       # front left
        1.1     1       # front right
        2.4     0.35       # subwoofer
    }
}
```

---

