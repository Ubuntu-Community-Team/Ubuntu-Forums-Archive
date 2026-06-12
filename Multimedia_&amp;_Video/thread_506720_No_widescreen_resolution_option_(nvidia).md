---
title: "No widescreen resolution option (nvidia)"
date: 2007-07-22
forum: Multimedia &amp; Video
---

### Post by CardUJ on 2007-07-22
It has annoyed me as to how difficult it was to find such an easy answer, so i thought i would post it to save others the trouble. 

Nvidia card, new widescreen monitor

**_Issue_**

On the screen resolution option on System>Preferences>Screen Resolution it did not have the widescreen choice i needed for my new monitor.

**_Fix_**

very simple

sudo nvidia-settings

then you can alter the settings, apply and save configuration changes using a nice simple gui (remember to save)

---

### Post by tommertron on 2007-07-24
Thanks! I never would have found this otherwise. I was beginning to think I could never get a widescreen resolution in Ubuntu with Nvidia drivers...

---

### Post by tommertron on 2007-07-27
Hi,

Just restarted Ubuntu after making this change, and my resolution went back to 1280X900! And in the Ubuntu screen resolution settings, my 1440X900 resolution wasn't there anymore. I had to back back to the command line and open nVidia settings again.

Did you experience similar issues? Is there a file I can configure to set the resolution to permanently 1440X900?

thanks,
Tom

---

### Post by darkmage77 on 2007-07-27
This could potentially solve my problem then!

Is there a sudo command for ATI driver config? This might help with my poor video performance; it may be a crappy driver, but if it's not configured properly it's just worse, isn't it? :D

And Tom, I had the same issue with a lot of different settings for Ubuntu in general; you have to set it upon startup a few times, but most settings will eventually settle in. No idea why it's like that, though...

---

### Post by akira9000 on 2007-07-28
would this work with my 37inch widescreen tv?
I think its res is 1366 x 768

---

### Post by HautingLu on 2007-08-16
Thanks!

Fixed my 19" widescreen issue. :guitar:

---

