---
title: "Sound and Graphics problems"
date: 2009-01-07
forum: Multimedia Software
---

### Post by 5nak3 on 2009-01-07
Hi all, right a couple of little things have been bugging me as of late with my ubuntu install and I was wondering if someone could help me out. 

Firstly I have a problem with the sound, basically even with my headphones in the sound comes out of the speakers, so at the moment I have my speakers muted when i want to use headphones.  
 
I believe the reason for this comes from the lack of a switch on my PC so I ran "aplay -l" to get some information about my card and I received this output:

"card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0"

I couldn't understand what model sound card I have, and how to go about creating the necessary switch.

Secondly it is my graphics card. I have an ATI mobility radeon 9000 using "lspci" i get an output of "01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]".

Now the problem with my graphics is that while I have compiz running, and glxinfo comes back with "direct rendering: yes" I do not think that the accelerated 3d is working, if indeed my card can actually use 3d acceleration. 
Essentially i do not know if i have the restricted ATI drivers running or if i have the open source alternative (which i believe do not perform as well, although are better supported). Is there anyway to check?

I have decided I would like to run a couple of games on my PC and despite meeting the specifications for them and running them under windows, with ubuntu they either run very slowly or not at all. I think this comes down to the use of incorrect drivers, so if someone can help identify which drivers i have installed and if needed how can i alter my set up to improve performance.

Thanks in advance.

---

### Post by 5nak3 on 2009-01-08
Has no one got any advice?

---

### Post by 5nak3 on 2009-01-10
bumping from page 12 in the hope that someone can help me :)

---EDIT---

Just thought I'd add, the sound issue is not a huge problem to be honest, i just mute the speakers and stick my headphones in.

I am more interested in fixing the graphics card. I would try the ati wiki instructions but I am unsure if they will work with my graphics card.

---

### Post by 5nak3 on 2009-01-15
up we go, still not solved :(

---

### Post by 5nak3 on 2009-01-29
anyone care to try and help out?

---

### Post by sornen on 2009-01-29
I use nvidia but you do need the correct drivers installed for gaming.  With nvidia their drivers work well with linux.  I am not sure about ATI.

For the sound, usually it is not possible to separate the audio output of a single sound card or chip.  Do you have a separate jack for headphones and speakers?

---

### Post by 5nak3 on 2009-01-30
Firstly thanks for the reply, Nvidia from what I understand tend to be better supported and more friendly with linux, so to that end I know my gfx experience won't be amazing. However the same laptop ran the games under windows without problems and with linux it seems to struggle which begs the question have I overlooked something.

At the moment as i said i'm not sure what drivers I have installed, so it is difficult to actually assess if this is the best my laptop will run with linux. In fact i checked the ATI wiki but i don't understand if they ([http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)) are suited for my graphics card and if indeed i have them installed already.

As far as the sound goes, yes I do have a separate headphone jack and while the sound comes out of the headphone jack when they are plugged in the problem is that the speakers don't switch off and continue to play unless i mute them. Again a problem which I never had with XP, and from my reading I think it is because of the lack of a switch telling the PC to turn off speakers when the headphones are plugged in.

---

### Post by sornen on 2009-01-30
If the game is running but struggling under linux it probably indicates that you do have the drivers installed.  If the game is a windows game that uses directx and you are using wine to run it, then it won't work well.

Run in a terminal 
$glxgears
it will show you how many fps you are getting, should be above 1000 i would have thought.


For sound this may help:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)


To find out what device you have type:

aplay -l

---

### Post by 5nak3 on 2009-01-30
I figured that running games under Wine would not work as well, so I looked for games which would run on both linux and windows (obviously installing the linux client) but even then, unless the linux client has been compiled in such a way that it adds added strain to the PC i cannot see why the windows version would work better, leaving me only to conclude that drivers were at fault.

Running glxgears, i get outputs of 500 FPS which I'm guessing may indicate the incorrect drivers.

And as for the article you posted, I already have that article bookmarked and that is where I got this switch idea into my head :)

The problem is that it is based on an intel HDA card (worked perfectly for my laptop with a HDA card) but doesn't work for this laptop which using "aplay -l" I'm told i have an "ATI IXP AC97" (as detailed in the first post)

---

