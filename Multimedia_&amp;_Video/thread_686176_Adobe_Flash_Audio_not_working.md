---
title: "Adobe Flash Audio not working"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by Ginger Towel on 2008-02-03
i know what your thinking... not another one of these F***ing posts why cant they just search and find the solution somewhere else.

well ive tried and most of the people fix there problem in a different way than each other person.

i have seen the problem with it saying "adobe flash player was NOT installed", thats not my problem
i have seen that people have had flash blocked by an ad blocker, not my problem
i have seen that people have had the gnash installed, that is not my problem

i cannot seem to find out what exactly to do to fix this but im getting sick of it.

i have purged my adobe and tried to install it from a recommended package, directly from the adobe website and directly from the synaptic packet manager also. nothing has worked.

thanks in advance

---

### Post by gandaran on 2008-02-03
there are many post's with the same problem as yours. 
I believe you have to install libflashsupport, I don't know where you can find it, it's not on synaptic, look it up

see this [http://packages.ubuntu.com/hardy/libs/libflashsupport](http://packages.ubuntu.com/hardy/libs/libflashsupport)

---

### Post by Ginger Towel on 2008-02-05
libflashsupport is on hardy (i believe) and i am on gusty i did instal this anyway and it did not work. i also searched around and people were saying pulseaudio fixes this but i also installed this with no success in fixing my problem any other ideas?

---

### Post by schnizzle on 2008-02-05
Do you have more than one sound card in your system?

I have an nVidia embedded and an EMU-0404 installed.  When I installed Flash initially video worked but audio did not.  After much trial and error the audio would work after some reboots but not others.

I eventually found a tip, now long since lost, that led me to force the detection of the EMU-0404 as the secondary audio device.  To do this, I added the following to /etc/modprobe.d/alsa-base:

options snd-emu10k1 index=1

This forces the nVidia sound card to index=0 which stabilizes /dev/dsp for Flash.

Hope this helps.

---

### Post by wmikes on 2008-02-05
this is what i have found out:  

after a fresh install of 7.10, i don't use anything else but the flash installer on adobe's website.  i don't do gnash, i don't install from firefox if it asks me, i don't do it from synaptic.  if you try any of these first and not the official installer from adobe it will screw up your install and it won't work no matter what you do, even if you use synaptic or a terminal to remove it.  trust me, i have battled this too.  do a fresh install of ubuntu and from the "get go" install the official release from adobe's website.  

party on...   :guitar:

---

### Post by Ginger Towel on 2008-02-05
yeah i only have the embedded audio in my motherboard and im not planing on doing a fresh install... maby a purge would work to remove them? or i maybe i will search to delete the files (i did thst for wine)

---

### Post by Ginger Towel on 2008-02-08
i did a clean install... here were my steps
1. install ubuntu
2. update and install restricted driver for my nvidia gfx card
3. download flash installer from adobe
4. install flash
5. test on youtube

still doesn't work....

anyone know what i can do????

if it matters i have a gigabyte motherboard and logitech Z-10 speakers

---

### Post by Ginger Towel on 2008-02-08
Bump

---

### Post by Ginger Towel on 2008-02-09
bump... anyone??

---

### Post by Ginger Towel on 2008-02-10
bump.. come on someone has to be able to help

---

### Post by Ginger Towel on 2008-02-11
ok this is my last time then im gana leave this alone and just live with it ugh....

if no one knows what i can do to fix this please point me in the direction of someone who can.

---

### Post by gandaran on 2008-02-12
[http://ubuntuforums.org/showthread.php?t=590989](http://ubuntuforums.org/showthread.php?t=590989)

---

