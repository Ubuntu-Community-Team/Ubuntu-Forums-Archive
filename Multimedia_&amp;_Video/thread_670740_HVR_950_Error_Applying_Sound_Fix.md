---
title: "HVR 950 Error Applying Sound Fix"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by LDRoamer on 2008-01-17
I have been trying to apply the sox fix that is supposed to get you sound with the HVR 950 TV card but I get an error when I run it:

```
prompt@prompt:~$ sox -r 48000 -w -c 2 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

Input File     : '/dev/dsp1' (ossdsp)
Sample Size    : 16-bit (2 bytes)
Sample Encoding: signed (2's complement)
Channels       : 2
Sample Rate    : 48000

sox sox: /dev/dsp1: Premature EOF while reading sample file. (Input/output error)
```

Can anyone tell me what I am doing wrong?

Thanks

---

