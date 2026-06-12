---
title: "ffdshow-like filters or Multichannel audio mixer?"
date: 2011-02-08
forum: Multimedia Software
---

### Post by fblinux on 2011-02-08
Hi there,
is there anything similar to ffdshow for ubuntu?
I mean something that has all the filters that ffdshow has.

In particular I am interested in being able to re-mix the audio channels before sending them to the spdif output.

For example (my real configuration in ffdshow for movies):
1. center and sub channel volumes are a bit higher than other channels. 
2. all low frequencies are redirected to sub channel 
3. the subchannel is then redirected to the back speakers

(In case you wonder why, I have a satellitar speaker set for the back channel with a great passive subwoofer that I don't want to change with an active one). 

Any solution in ubuntu?

Thanks,

Fabrizio

---

### Post by BicyclerBoy on 2011-02-08
Part of a solution...

To get multi-channel audio over S/PDIF you need to use AC3 or DTS.

The alsa modules plug-in a52 (AC3 encoder) will let you do this.
This is not part of Ubuntu alsa normally..
Pulseaudio is meant to be able to do similar but it crashed very badly..

The channel order will need to be rearranged as SMPTE is diff to alsa is diff to AC3 etc..

The channel re-arrange is easy in alsa, it also allows simple mixing 

```

# 15-01-2011 a52 encoding in alsa plugins.
pcm.a52 {
    @args [ CARD ]
    @args.CARD {
               type string
               default 0
    }
    type plug
    slave {
           pcm {
               type a52
                 bitrate 448
                 channels 6
               card $CARD
           }
            rate 48000 #required somehow, otherwise nothing happens in PulseAudio
    }
}

pcm.swap51 {
   @args.0 SLAVE
   @args.SLAVE {
               type string
               default "a52"
   }
   type route
   slave {
         pcm $SLAVE
         channels 6
   }
   ttable {
     0.0= 1
     1.4= 1
     2.5= 1
     3.2= 1
     4.1= 1
     5.3= 1
   }
}

```The values of 1 in the ttable can be changed ...just keep the sum of the squares the same
[http://www.volkerschatz.com/noise/alsa.html](http://www.volkerschatz.com/noise/alsa.html)

So you can have two ttable entries (in.out) for the same output i.e. mix..

Note: speaker-test numbers the channels = (alsa_channel+1)
```

label  spk-test   alsa  a52 (libavcodec AC3)
FL                 1                    0             1
FR                2                   1             5
LR                3                   2             6
RR               4                    3            3
Centre          5                  4             2
LFE               6                  5             4

```The AC3 order depends on the libavcodec version compiler directive/variable..
This order is odd & not as expected...
Left Front, Center, Right Front, Surround Left, Surround Right, LFE

Test/use: 
speaker-test -D swap51: -c6
speaker-test -D swap51:\'a52\' -c6

VLC usage
vlc --aout alsa --alsa-audio-device swap51
(play ac3 test file to check channel ordering)

Clementine multi-channel audio..
alsa swap51

---

### Post by BicyclerBoy on 2011-02-09
Warning.
I am not at all sure that the a52 alsa plug-in sounds right.
There is something wrong in the chain, still attempting to find which part.

---

