---
title: "Zoiper blocks any other sound"
date: 2008-05-17
forum: Multimedia Software
---

### Post by aspora.isernia on 2008-05-17
Hi to all,
recently I installed the Zoiper softphone on my Heron. I feel it's a good softphone (good sound quality and many more) BUT... It blocks any other sound!! No music, no video... All is blocked!!
Could anyone help me?? I cannot use nothing if it's turned on!! Please....

Thanks for any clue

a.i :)

---

### Post by tseligkas on 2008-05-28
Hello,

Same here. I installed Zoiper because I never managed to configure Ekiga to use our company's SIP with proper audio quality. I either had hissing sound or the person I have been talking to was hearing me with fading volume... O_o

Concerning what aspora.isernia said, I could not find anything in any Zoiper support pages (does a Zoiper forum exist by the way?).

Let me give a few extra details on the problem:

First of all, there is no command line output. I can give a debug log from Zoiper, although I think it doesn't show anything particular that could help.

I have an onboard sound card. The audio devices available to select from are the following:

Input Device:
HDA Intel: ALC882 Analog (hw:0,0)
HDA Intel: ALC882 Digital (hw:0,1)
HDA Intel: ALC882 Analog (hw:0,2)
spdif
default

Output device:
HDA Intel: ALC882 Analog (hw:0,0)
HDA Intel: ALC882 Digital (hw:0,1)
front
surround40
surround41
surround50
 surround51
 iec958
spdif
default
dmix

Ringing Device:
(Same options as output device)

In my configuration Zoiper can play if I select for all devices the option "HDA Intel: ALC882 Analog (hw:0,0)"

When Zoiper starts, it "locks" the audio device and there is no way you can listen to audio (rhythmbox, listen media player, VLC, Totem etc.).

Any guesses?

---

### Post by graffiX on 2009-05-03
I have this same problem, and I can't seem to find a combination of any settings that will allow multiple sources to be active at once.

Google shows that others have this problem too, but does anyone know of a solution?  Is it something so simple nobody has recorded it?

Thanks for any insight.

Dave

---

### Post by pepperedeggs on 2009-05-29
Same here, I don't think it's the codecs as I have used several with Zoiper and it doesn't make a difference. 

I actually have the same problem if I play some music before running Zoiper. Zoiper can not access the audio device to play ring or output sound throuhg. The audio device and or daemon seems to get locked not allowing any other app to access it. 

I am trying to find a work around but the only one I can see is to install another sound card specifically for Zoiper so that system sounds, music can play out and use the onboard sound and mic for Zoiper alone.

---

### Post by stone5 on 2010-03-06
Hey All

I don't wanna be rude but, i tried it all!!!  from Zoiper input to output options,,, and Ubuntu Sound Preference too.. i spent...  instead... i Wasted multiple hours in trying to find a solution and the only thing i came up with,  is.. Zoiper on Ubuntu is a Useless Piece of **** Device that disrupt and unbalance the proper functions of sound and unbalanced my cool and patience too.  Fk!!! Zoiper.. i hope someone else comes up with another program that connects Phone services, unless i go back to use Windows, direct and easy with no complications...

Sorry all,,, but am pissed than a Mutha-fka!!

Stone5

---

### Post by tseligkas on 2010-03-08
> **stone5 said:**
> Hey All

I don't wanna be rude but, i tried it all!!!  from Zoiper input to output options,,, and Ubuntu Sound Preference too.. i spent...  instead... i Wasted multiple hours in trying to find a solution and the only thing i came up with,  is.. Zoiper on Ubuntu is a Useless Piece of **** Device that disrupt and unbalance the proper functions of sound and unbalanced my cool and patience too.  Fk!!! Zoiper.. i hope someone else comes up with another program that connects Phone services, unless i go back to use Windows, direct and easy with no complications...

Sorry all,,, but am pissed than a Mutha-fka!!

Stone5

Just to let you know,

1. Going back to Windows isn't a solution. Indeed you may find "peace" in Windows but that's only because some apps are developed for that operating system originally and are badly ported to Linux. Going back to Windows due to a single bad-ported app not working in Linux is like saying hybrid cars are trash because they lack HP and going back to petrol cursing god and daemons for that reason. Your motivation is theatrical.

2. This isn't a Zoiper forum. It's an Ubuntu forum. Any rant without proposed solution is pointless here. And so is reviving an old tread for that reason.

To aspora.isernia or any op, I would suggest closing this thread...

---

### Post by vaiaco on 2011-02-08
> **tseligkas said:**
> Just to let you know,

1. Going back to Windows isn't a solution. Indeed you may find "peace" in Windows but that's only because some apps are developed for that operating system originally and are badly ported to Linux. Going back to Windows due to a single bad-ported app not working in Linux is like saying hybrid cars are trash because they lack HP and going back to petrol cursing god and daemons for that reason. Your motivation is theatrical.

2. This isn't a Zoiper forum. It's an Ubuntu forum. Any rant without proposed solution is pointless here. And so is reviving an old tread for that reason.

To aspora.isernia or any op, I would suggest closing this thread...

Have you tried to run Zoiper using WINE, I will give it a shot

---

