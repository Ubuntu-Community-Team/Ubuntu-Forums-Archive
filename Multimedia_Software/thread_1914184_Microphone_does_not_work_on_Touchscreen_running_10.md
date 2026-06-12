---
title: "Microphone does not work on Touchscreen running 10.04"
date: 2012-01-23
forum: Multimedia Software
---

### Post by RockOut on 2012-01-23
Here's my issue:

I have 10.04 installed. The speaker/headphone OUTPUT does work. The inputs do not. I have an HP Touchsmart Desktop. This comes up a lot, so here's the code I used in Terminal to get my settings:
```
uname -a
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```

And here is the output:
```
coooperhive@coooperhive-desktop:~$ uname -a
Linux coooperhive-desktop 2.6.32-37-generic-pae #81-Ubuntu SMP Fri Dec 2 22:24:22 UTC 2011 i686 GNU/Linux
coooperhive@coooperhive-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
coooperhive@coooperhive-desktop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Analog Devices AD1984B

```

I'm a little lost.

At one point the MIC DID WORK on Ubuntu 11.10. This leads me to believe that the soundcard itself is not the issue. 

I downgraded to 10.04 LTS was because this Touchscreen is a production/work machine and 11.10 was way too buggy for professional use. 10.04 works a dream on the touchscreen, and I would recommend it to anyone.

Except that I can't get the mic to work. This error impacts both the internal mic and the plug-in/external mic.

---

### Post by RockOut on 2012-01-24
After tinkering and milling about the forum, I discovered 2 things:

1) If you're having a sound issue, open Terminal and type ```
alsamixer
``` From here you can control the input volumes of your external mic.

2) While I can't get my internal microphone to work, I DID get the external mic to work. In fact, I probably got it to work on my first crack at solving the problem by updating the Kernel and salsamizer. 

This is where user-error comes into play.  The external mic I was using to test was busted. Barely worked. This is why I couldn't hear anything from the external mics. I ponied up and bought an Audio Technical monodirectional mic. It is BEAUTIFUL. Great sound quality. So, if you are having the same problem I am, please snag a working microphone before embarking on your troubleshooting.

The internal microphone doesn't work still. I'm still at a loss as to how to fix that issue.

---

