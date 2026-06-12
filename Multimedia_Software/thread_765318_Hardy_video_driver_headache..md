---
title: "Hardy video driver headache."
date: 2008-04-24
forum: Multimedia Software
---

### Post by orre64 on 2008-04-24
Before I say anything else, I am a newbie to Linux.

Now, I recently hyped myself up awaiting the release of Hardy, telling myself that this would be the moment of clarity, where I could finally give Windows the finger. This, however, did not turn out as expected.

Ubuntu installed quite easily on a dedicated HDD, everything was fine until I wanted to get some drivers for my HD2900XT. Ubuntu politely suggested that I use the restriced drivers, I said what the hell let's go and leaned back while scary text started popping up in the terminal thingy. So far so good.

After reboot, however, I encountered some problems. The splash screen churned on as usual, but after that there was nothing but a black screen and a frozen mouse pointer. (Though I think I did catch the colors on the splash screen getting all grainy and inverted a split second prior to this.)

I figured that I must have done something wrong, although still mighty convinced that googling the the crap out of the problem would fix things. I made a clean install and came across an app called Envy. Using this only resulted in the same black screen upon reboot and subsequently, my second clean install.

Now I'm bummed out to say the least. I mean, what does it take to get a relatively mainstream GPU such as HD2900 to run in Ubuntu? Because I figure that it should be supported, since ATI provides some sort of Linux based driver for it.

Thus, I put my faith in the community; anybody who encountered the same problem as me and solved it?

My system specs are:

Ubuntu Hardy LTS x86_64
Asus P5K
Core 2 E6750
4x Corsair XMS2 CL4 1GB
ATI Radeon HD2900XT

---

### Post by Kowalski_GT-R on 2008-04-24
same here without frozen pointer, I get nothing instead :-)

I guess it all boils down to the same issue with ATI drivers.

I have a Radeon 1600.....I'm waiting to gather info before having another go at the darn proprietary drivers

---

### Post by orre64 on 2008-04-24
I would try to follow this guide, but unfortunately I don't get half of what it says: 

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method)

---

### Post by drguerra on 2008-04-25
Sigh.

I really wish these drivers would actually work.

It sucks to throw XP and Windows away only to realize that your 2900 Pro/XT won't work properly with Ubuntu.

I am in the exact same boat.

---

### Post by dubbedout on 2008-04-25
I feel your pain, I had everything working on my Gutsy install, 3D effects and everything.  I've got a ATI 9600 Mobility and now I cant enable 3d effects, tried the restricted driver and it goes to a white screen for a while and then back to none selected for the visuals.

---

### Post by bladerunner6 on 2008-04-25
i managed to get 8.3 working with hardy heron beta,

but with the final i cant get ati 8.4 to enable dri 3d

i keep getting indirect rendereing

i am using 9800pro agp card with an 875 p4 chipset

---

### Post by orre64 on 2008-04-25
Do you think there will be a solution for this anytime soon, I mean, is the Ubuntu/ATI team aware of and concerned about this problem or am I better off just screwing the whole thing?

---

### Post by theironyofitall on 2008-04-25
I have had Feisty and Gutsy  Very Standard Nvidia Geoforce5500 + 1440x900  & 1024x768 screens

My Nvidia card is not detected, so  X cant start.

It seems to me that the 'release' dose not work. My upgrade has left me limping along with low res and only one.

Have tried all combinations of
[LIST]
[*]Envy
[*]Nvidia new
[*]Backup xorg files
[*]X configuration screens at bootup
[*]nvidia downloaded driver
[*]Reloading via synaptic from repos
[/LIST] 

I cannot even get full res in non X mode 


Help !

Bill,  your not as bad as I thought

Gary

[www.theclearboxstore.co.uk](www.theclearboxstore.co.uk)

---

### Post by cooke77 on 2008-08-19
Ditch the ATI card...get a nVidia one. (nVidia is 'supported'...ATI is not.)
And use a PS2 keyboard/mouse.(Until you figure out 'why' your USB is not working properly.)

---

