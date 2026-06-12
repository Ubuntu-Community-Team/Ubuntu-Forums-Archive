---
title: "Jack OSS support"
date: 2011-05-13
forum: Multimedia Software
---

### Post by kgenus on 2011-05-13
I'm trying to compile the OSS support for Jack with 11.04 amd64.  I've got opensound.com working with my LynxTWO-A card with all it's audio channels and Jack/OSS  is the last hold out.  [The Ubuntu Manual link]("http://manpages.ubuntu.com/manpages/natty/man1/jackd.1.html") seems to imply functionality exists.... 


> [SIZE="1"]**[SIZE="2"]OSS BACKEND PARAMETERS[/SIZE]**
       -r, --rate int
              Specify the sample rate.  The default is 48000.

       -p, --period int
              Specify the number of frames between JACK process() calls.  This
              value  must  be  a  power of 2, and the default is 1024.  If you
              need low latency, set -p as low as you  can  go  without  seeing
              xruns.   A  larger  period size yields higher latency, but makes
              xruns less likely.  The  JACK  capture  latency  in  seconds  is
              --period divided by --rate.

       -n, --nperiods int
              Specify  the  number  of  periods  in  the hardware buffer.  The
              default is 2.  The period size (-p) times --nperiods times  four
              is  the  JACK  buffer size in bytes.  The JACK output latency in
              seconds is --nperiods times --period divided by --rate.

       -w, --wordlength int
              Specify the sample size in bits. The default is 16.

       -i, --inchannels int
              Specify how many channels to capture (default: 2)

       -o, --outchannels int
              Specify number of playback channels (default: 2)

       -C, --capture device_file
              Specify input device for capture (default: /dev/dsp)

       -P, --playback device_file
              Specify output device for playback (default: /dev/dsp)

       -b, --ignorehwbuf boolean
              Specify, whether to ignore hardware period size (default: false)[/SIZE]


However, I see no options anywhere to build OSS drivers with the Jack 1.9.7 source.  Any "up to date" help would be appreciated.

Kevin

---

### Post by kgenus on 2011-06-05
I was using jack2, installing jack1 resolved the issue.

---

