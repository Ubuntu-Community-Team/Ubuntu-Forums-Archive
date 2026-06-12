---
title: "Jaunty - Firefox 3.0.10 w/latest flash - Sound stops working randomly in videos"
date: 2009-05-06
forum: Multimedia Software
---

### Post by James78 on 2009-05-06
As said in title, I'm using Kubuntu Jaunty, all upgraded. I have firefox 3.0.10 and the latest version of flash player (whatever that may be). When I play videos on my browser, the sound will either work for a bit, and stop randomly, or won't work (flash ONLY). I took the liberty of opening Firefox in the terminal to see the output, this is what I get:
```
Greasemonkey getFirebugConsole() error:
(new TypeError("chromeWin.Firebug is undefined", "file:///home/james/.mozilla/firefox/essddnbn.default/extensions/%7Be4a8a97b-f2ed-450b-b12d-ee082ba24781%7D/components/greasemonkey.js", 392))             
Removing DOMNodeRemoved listener                   
Removing DOMNodeRemoved listener                   
Greasemonkey getFirebugConsole() error:            
(new TypeError("chromeWin.Firebug is undefined", "file:///home/james/.mozilla/firefox/essddnbn.default/extensions/%7Be4a8a97b-f2ed-450b-b12d-ee082ba24781%7D/components/greasemonkey.js", 392))             
Removing DOMNodeRemoved listener                   
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.                                         
I: caps.c: Dropping root privileges.               
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.                                         
Removing DOMNodeRemoved listener

```

If any more info is needed, feel free to ask. I've tried fixing it with so many codecs, alsa, pulse, it never worked, which leads me to think this is a flash and/or Firefox issue. Getting tired of this! My sound works perfectly fine anywhere else, except on flash videos..

---

### Post by James78 on 2009-05-07
I *think* I fixed the problem. I downloaded and installed this .deb here. Libflashsupport. It adds Additional Interface Support for Linux Flash Player. It's supposed to add library support for oss, openssl and icu. Hopefully this may have helped others with similar issues.

[http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb](http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb)

---

### Post by acimmarusti on 2009-05-07
You could try: 

```

sudo apt-get install ubuntu-restricted-extras

```

---

### Post by James78 on 2009-05-07
Oh, ya, I already did that. Got a few things installed from that. Kubuntu-restricted-extras for me actually though.:)

---

### Post by psyke83 on 2009-05-08
Don't use libflashsupport, it's obsolete and causes serious instability in Firefox. See my PulseAudio guide and [bug #192888]("https://bugs.launchpad.net/bugs/192888") for more information.

If you're using Kubuntu, you don't even have PulseAudio installed, so libflashsupport would never have been useful to you.

---

### Post by James78 on 2009-05-09
Well, from checking in my package manager, pulseaudio seems to be installed, and judging from all my related error messages when starting pulseaudio, and when pulseaudio is being used: ```
Pulseaudio: cpulimit.c: Received request to terminate due to CPU overload.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.                                         
I: caps.c: Dropping root privileges.               
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE. 
``` before my audio stops working at all, I'm pretty sure I'm using pulseaudio right now.

As for your guide, it's useful, but unfortunately it fixed absolutely nothing for me. Pulseaudio still seems to be malfunctioning.

---

### Post by mikekchar on 2009-05-21
Delete your ~/.pulse file.  That will fix this (and probably several other random problems).  You know, I really want to like pulseaudio... But every upgrade it's the thing that is always broken on my machine... sigh...

---

### Post by pumrel on 2009-09-05
Thank you very much mikekchar. I've been looking for a solution for a very long time and your simple method did the thing. Thanks again.

---

