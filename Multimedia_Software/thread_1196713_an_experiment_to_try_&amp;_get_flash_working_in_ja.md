---
title: "an experiment to try &amp; get flash working in jaunty"
date: 2009-06-25
forum: Multimedia Software
---

### Post by spamhippy on 2009-06-25
well- flash 10 plays about 2 seconds of any video & craps out on me... so I had an idea. went to this page-

[http://kb2.adobe.com/cps/406/kb406791.html](http://kb2.adobe.com/cps/406/kb406791.html)

went to the bottom of the page.. downloaded flash 9 & installed (..figured I was using 9 before I upgraded.. it worked then...)

videos actually play now (a little bit of jump every now & again- but a lot better than 10..)

only one problem... NO SOUND! (I'm guessing it's pulse...) 

any ideas? if I can figure it out- I'll have a working version of flash.

---

### Post by madverb on 2009-06-25
I had a problem with sound and Flash 9 ages ago. Ended up fixing it by installing different releases until one worked.

---

### Post by lidex on 2009-06-25
spamhippy:
2 issues here - let's deal with flash first.
1)remove old flash - enter one line at a time in terminal

```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper

sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
sudo apt-get install ia32-libs nspluginwrapper

```

Next enter
```
sudo apt-get install flashplugin-installer
```

or install package in synaptic. Post results.

---

### Post by lovinglinux on 2009-06-25
Take a look at the thread [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by spamhippy on 2009-06-25
hey 'lovinglinux' had actually gone to your thread & gave it a shot before- to no avail. sorry man-

& let me see.. looks like lidex wants me to remove & try to install flash again LOL... okay... got a few things to do- but will post results as soon as I get a chance to do this.

thanks-

---

### Post by lovinglinux on 2009-06-25
> **spamhippy said:**
> hey 'lovinglinux' had actually gone to your thread & gave it a shot before- to no avail. sorry man-

& let me see.. looks like lidex wants me to remove & try to install flash again LOL... okay... got a few things to do- but will post results as soon as I get a chance to do this.

thanks-

Have you tried removing pulsaudio and installing esound?

---

### Post by spamhippy on 2009-06-25
no I haven't.. but I'm running ubuntu studio 9.04 -realtime kernel, 2 sound cards- an AC97 built into the mobo & an maudio 1010lt. both sound cards are functioning.. neither plays sound from flash & when I go into 'pulse audio volume control' & check where sound is coming from (see if maybe something is playing but muted or something..) I don't see anything- have also experimented with settings in system>preferences>sound to no avail.

taking out pulse I don't think is really an option for me. the whole reason I'm running ubuntu studio is that I self-publish a comic book & play guitar in a band (ie record..) I don't want to screw up my audio setup.

(LOL-why not? & in case your wondering)

[http://www.archive.org/details/Lofi2008Cd](http://www.archive.org/details/Lofi2008Cd)

[http://www.lulu.com/spamhippy](http://www.lulu.com/spamhippy)

---

### Post by ppjdd on 2009-06-25
> **lidex said:**
> spamhippy:
2 issues here - let's deal with flash first.
1)remove old flash - enter one line at a time in terminal

```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper

sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
sudo apt-get install ia32-libs nspluginwrapper

```

Next enter
```
sudo apt-get install flashplugin-installer
```

or install package in synaptic. Post results.

I tried this on my computer and it finally works. Thank you. This is great. It has never worked. SO this is great. Thanks again.

---

### Post by spamhippy on 2009-06-25
E: Couldn't find package ia32-libs


where do I get this packager for jaunty?

---

### Post by Majikayo on 2009-06-25
> **spamhippy said:**
> E: Couldn't find package ia32-libs


where do I get this packager for jaunty?


Same for me...We might be onto something here...

---

### Post by ppjdd on 2009-06-26
Well my computer never installed that either, but it worked. So I don't know, where one could find it.

---

### Post by anycon on 2009-06-26
My Flash* video* is working fine but I can't hear it. Anyone got advice? All the fixes I find on Google are out of date.

---

### Post by spamhippy on 2009-06-26
am starting to make progress... the reinstall didn't do anything. flash 9 plays- but no sound. flash 10 plays sound- but stalls a few seconds into every video.

& then I remembered something-

in ubuntu studio there's a thing called 'ubuntu studio controls' 

what it does is- if you're running say.. a multi track recording.. it gives setting on how much total system memory it'll use to keep one program going. it's there so a recording program won't glitch up & screw up the recording (more memory devoted to the program = less chance of messing up..)

anyways- I re-installed flash 10 (the one that had sound- but stalls out..) & tweek the settings in ubuntu studio controls to about 90% 

video now plays (it is little funky if too many things are going..) but it actually works now. so I guess the next step on this problem for me is to read up on ubuntu studio controls & see if I can get the settings fine tuned.

but as is- it works.. so I think the problem's solved. thanks guys :)

---

### Post by spamhippy on 2009-06-26
LOL- maybe I spoke too soon... now pulse & flash fight for memory.. flash stalls.. if I killall pulseaudio ... the video plays perfectly- but with no sound!

---

### Post by spamhippy on 2009-06-26
yeah.. this still isn't working... sorry.. did the studio controls thing- it played a video all the wat through (with sound & everything...) & that was the first & last time... I don't think flash likes pulse.

---

