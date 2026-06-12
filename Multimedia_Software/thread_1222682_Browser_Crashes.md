---
title: "Browser Crashes"
date: 2009-07-25
forum: Multimedia Software
---

### Post by ssdt on 2009-07-25
I am trying to watch some videos off from Youtube and because I watch it with my family, I make it full screen so that everyone could see. But after I watch at least 5 parts, the flash starts to lag (sometimes the sound doesn't come up or the video plays by really fast) and then it crashes the browser. 

Can anyone tell me any kind of plugin that could help me support flash in by browsers?
I use Opera to watch from Youtube.

Thank you

---

### Post by quixote on 2009-07-26
I use firefox, not opera, so I'm not sure what could be causing your problem.  (This question is tagged "firefox", by the way.)  I'd suggest giving firefox a try, but if you do, try 3.5.  In FF, in versions before 3, there were sometimes memory leakage problems.  Those get worse over time, as you describe, so maybe that's what's going on in your case.  In that situation, it's the program, not your computer, and there's nothing to do but try something else.

How much system memory does your computer have?  It takes quite a bit to run large flash files.

---

### Post by martinbaselier on 2009-07-26
Which flash plugin do you have installed? What soundcard do you have?
Please paste the output of the following commands:
**lspci | grep Audio -i**
**dpkg -l | grep flash**
Do you have pulseaudio running ?
**ps -e | grep pulse**

I used to have a similar problem with flash, and with me it was the alsa driver causing this. But your case might be different.

---

### Post by ssdt on 2009-07-28
> **quixote said:**
> I use firefox, not opera, so I'm not sure what could be causing your problem.  (This question is tagged "firefox", by the way.)  I'd suggest giving firefox a try, but if you do, try 3.5.  In FF, in versions before 3, there were sometimes memory leakage problems.  Those get worse over time, as you describe, so maybe that's what's going on in your case.  In that situation, it's the program, not your computer, and there's nothing to do but try something else.

How much system memory does your computer have?  It takes quite a bit to run large flash files.
I have FF 3 installed and my system has 2 GIG RAM and it's dual processor. Everything is fine working except for this.

---

### Post by ssdt on 2009-07-28
In termial i pasted all of them and see the results:
*lspci | grep Audio -i*
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
[I]
dpkg -l | grep flash[/I]
ii  adobe-flashplugin                          10.0.22.87-1                              Adobe Flash Player plugin version 10
ii  flashplugin-installer                      10.0.22.87ubuntu2                         Adobe Flash Player plugin installer
ii  flashplugin-nonfree                        10.0.22.87ubuntu2                         Adobe Flash Player plugin installer (transit

I didn't get any response with the pulse audio (last one) in the terminal.

---

