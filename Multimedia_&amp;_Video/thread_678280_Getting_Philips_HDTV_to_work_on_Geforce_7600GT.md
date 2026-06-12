---
title: "Getting Philips HDTV to work on Geforce 7600GT"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by Harksaw on 2008-01-25
I'm running Gutsy, the 64 bit version.

I have a GeForce 7600GT card with component out hooked up to my Philips HDTV which is 1080p capable. (TV number 47PFL7422D/37 )

I have my nvidia graphics card set up with the proprietary drivers. My main monitor works wonderfully.

I go to Administration - Screens and Graphics, go to the second monitor and set it up as Model: Generic LCD Panel 1920x1080 and select the Widescreen box. 

The problem is, it won't let me select 1920x1080. the highest it lets me select is 1680x1050, and after logging out and in, the TV still looks purple and reports that it's in 480i.

But no matter what I select, the TV always looks purple, ugly, and unwatchable. It says it's at 480i. I can barely make out the mouse moving on the TV.

The TV plays well with this card under windows.

Any ideas?

---

### Post by overdrank on 2008-01-25
> **Harksaw said:**
> I'm running Gutsy, the 64 bit version.

I have a GeForce 7600GT card with component out hooked up to my Philips HDTV which is 1080p capable. (TV number 47PFL7422D/37 )

I have my nvidia graphics card set up with the proprietary drivers. My main monitor works wonderfully.

I go to Administration - Screens and Graphics, go to the second monitor and set it up as Model: Generic LCD Panel 1920x1080 and select the Widescreen box. 

The problem is, it won't let me select 1920x1080. the highest it lets me select is 1680x1050, and after logging out and in, the TV still looks purple and reports that it's in 480i.

But no matter what I select, the TV always looks purple, ugly, and unwatchable. It says it's at 480i. I can barely make out the mouse moving on the TV.

The TV plays well with this card under windows.

Any ideas?

HI and have you tried with the nvidia-settings ```
gksudo nvidia-settings
``` to configure your TV

---

### Post by Harksaw on 2008-01-25
> **overdrank said:**
> HI and have you tried with the nvidia-settings ```
gksudo nvidia-settings
``` to configure your TV

Yes, and it doesn't give me the option of any resolution over 1024x768. Also, it doesn't give me the option of any widescreen resolutions.

---

### Post by Harksaw on 2008-02-06
I'd like to bump this up for further consideration. 

Is bumping threads a faux pas? I didn't see anything during a cursory review of the FAQ and the CofC.

---

