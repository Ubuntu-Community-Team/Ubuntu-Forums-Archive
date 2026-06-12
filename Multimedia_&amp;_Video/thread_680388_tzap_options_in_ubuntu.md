---
title: "tzap options in ubuntu"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by RawMustard on 2008-01-27
Have the options somehow been changed in tzap on ubuntu?

Reading linuxtv.org I should get this when running:```
usage:
      tzap [options] <channel_name>
        zap to channel channel_name (case insensitive)
    -a number : use given adapter (default 0)
    -f number : use given frontend (default 0)
    -d number : use given demux (default 0)
    -c file   : read channels list from 'file'
    -x        : exit after tuning
    -r        : set up /dev/dvb/adapterX/dvr0 for TS recording
    -s        : only print summary
    -S        : run silently (no output)
    -F        : set up frontend only, don't touch demux
    -t number : timeout (seconds)
    -o file   : output filename (use -o - for stdout)
    -h -?     : display this help and exit
```But all I get is this:```
usage: tzap [-a adapter_num] [-f frontend_id] [-d demux_id] [-c conf_file] [-r] <channel name>
```

So when I try to do this:```
tzap -r 0 -t30 -o tenDigi.ts "Ten Digital"
```I get  invalid option --t 

Also following other instructions on linuxtv.org, the -S options doesn't work either.
I don't get it?

---

### Post by rforub on 2008-04-07
Does it work with a space between -t 30.
Wondering if ubuntu tzap uses options -t and -o.

Rob.

---

