---
title: "CD Rippers not encoding"
date: 2009-03-29
forum: Multimedia Software
---

### Post by Chew N Tobacca on 2009-03-29
I have used RipperX for extracting CD's to mp3 quite religiously for some time now. Has always worked well, and is time-efficient. But recently it has stopped encoding to mp3 files. I have also used a couple others (GRip, SoundJuicer) and a similar thing is happening. While using RipperX, it will extract the files but does not encode them at all. I end up with an empty mp3-format file 2.0KB in size with no audio or id3 information at all. Under GRip and SoundJuicer, the files are extracted and will play ok on any computer, but again there is no id3 information there.

Long story short, I have like 600 CD's to be ripped to mp3. RipperX has always been the best, easiest, and fastest. I would like to continue to use it, but I am stumped. I have tried re-installing all the components: RipperX itself, and all the lame/mp3-related packages, but still get the same result. I even went so far as to re-install the entire operating system. I am STILL faced with the same outcome all the way around. Perhaps there are conflicting packages somewhere, or an update messed things up?

I have searched through the forums and Google, but nobody seems to be having the same issue. (Leave it to me!) If anyone has any similar experience or has ideas for a solution, I'd love to hear it. 

Thanks in advance.

---

### Post by kelvin spratt on 2009-03-29
Try Asunder,banhee,

---

### Post by Chew N Tobacca on 2009-03-30
As you suggested, I tried Banshee. Seems to work fine, but does not accomplish what I desire on its own. I would still have to go back and re-tag a few fields of the id3. 

All the mp3 encoders seem to be doing their job. I have tried enough different apps to narrow it down to the RipperX program itself that is not ripping correctly. However, I cannot figure out why...

---

### Post by Chew N Tobacca on 2009-03-31
It seems I have arrived at a conclusion.](*,) After testing many variables, I have come to believe that my primary optical drive is on its way out. RipperX defaults to /dev/cdrom, and I thought I'd use the secondary drive. In the config menu, there is a place to put additional options. By typing "-d /dev/cdrom1" in the dialog, It will ignore /dev/cdrom and use whatever drive you specify. Works like it always should have...

---

