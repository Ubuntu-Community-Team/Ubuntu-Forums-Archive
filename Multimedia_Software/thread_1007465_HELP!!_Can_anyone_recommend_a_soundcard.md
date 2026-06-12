---
title: "HELP!! Can anyone recommend a soundcard?"
date: 2008-12-10
forum: Multimedia Software
---

### Post by Truckerpunk on 2008-12-10
I have a Soundblaster Live CT4830 witch I've tried to get to work with Ubuntu 8.10. Have really tried everything to make this work, but without luck. Don't go there!!!! Had a minor breakthrough where the system didn't freeze right after booting, but after minutes instead... Woohoo!! But it generally just makes your system freeze. I have no problem when removing the soundblaster Live card and using the onboard card(other than it doesn't support multiple audio playback at the same time ). Well just have to miss out on multiple audio playback, won't go back to Windows. But really don't think you will ever get a stable Ubuntu-system with s Soundblaster Live-card... Sadly. Can anyone recommend a soundcard that they haven't had ANY trouble with while running Ubuntu? Would be sweet to get sound playback working perfectly.

---

### Post by squaregoldfish on 2008-12-10
I recently installed a Trust 5.1 Sound Expert Optical (514DX). Works like a charm - detected and all working straight away (I'm using Hardy 64bit). I got the card after it was recommended elsewhere on these forums.

The only thing to watch for is that the optical connectors are on a separate blanking plate connected by a cable. I didn't have two slots available next to each other in my case, and the cable isn't long enough to stretch further than one slot - I had to build my own connector cable. It's not hard to do at all, but just be aware of it.

Steve.

---

### Post by markbuntu on 2008-12-10
I got a SIIG Soundwave 7.1 PCI card. It is cheap, it uses the C-Media chipset and it works out of the box and sounds great, better than my onboard HDA ALC 888. It has digital in and out and connectors on the back for surround sound, line-in line-out, mic etc.

I can confirm that it works on Hardy i386, Hardy amd64 UbuntuStudioHardy amd64 and i386, Interpid amd64 and Intrepid Studio amd64.

Anyway, you onboard will do multiple application sound output, it is just not configured properly. If you want to fix that go here:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If you want more help, go here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by conimex on 2008-12-10
I have the same SoundBlaster Live CT4380 in Ubuntu 8.10. Rock stable. Try to reinstall Ubuntu, but first in BIOS disable integrated sound card if you have it. Ubuntu support SounBlaster Live CT4830, but is actually CT4832 recognized by Ubuntu. Read official Ubuntu Documentatio and follow the link with supported sound card.

---

### Post by kraymore on 2008-12-10
i can recommend the HT Omega Striker.  It works out of the box in Intrepid i386 and uses cmedia chipset as well.  it sounds even better if you compile the alsa 1.0.18a driver though.  it works in analog mode out of the box i haven't figure out how to get digital out working yet.

---

### Post by Truckerpunk on 2008-12-10
First of all thanks for the answers.

It says right here([https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs)) that my Soundblaster Live card should work perfectly in older versions of Ubuntu and I doubt it that it shouldn't work flawlessly in Intrepid as well.So I'm down to that it might be a Hardware problem instead. Somtheing like that my motherboard doesn't like Soundblaster Live all that much. I may need to check on that. Meanwhile I'm still looking for a perfectly functional soundcard for Ubuntu Intrepid i386, that _doesn't_ have surround support(sorry...should have mentioned that in the first post. But I've always liked straight up stereo better, and I'm a student so money is short). So a fairly cheap card that work Flawlessly..?

---

### Post by markbuntu on 2008-12-10
Pretty much any PCI card with a c-media chipset will work out of the box and they are cheap.

I use my card strictly for stereo output myself and it works just fine.

---

### Post by Truckerpunk on 2008-12-11
Yeah I know. But Creative Soundblaster Live IS a PCI card with a c-media chipset, and it doesn't work for my setup. It's so frustrating. Not having flawless audio playback is a pain in the ***. And not being able to solve it i even worse, and knowing that it should work right out of the box sure doesn't help either... I'm loosing hope here. This might call for a reinstallation, and perhaps don't upgrade to Ubuntu 8.10. I could get some sound from the card with 8.04, but still not stable. Crashed over and over again.

---

### Post by markbuntu on 2008-12-11
The sb live uses the emu10k1 chipset

and a SigmaTel STAC9708/11 chip for the soundmixer.

[http://alsa.opensrc.org/index.php/Emu10k1](http://alsa.opensrc.org/index.php/Emu10k1)

C-Media is a Chinese company that makes OEM sound cards for resellers like Turtle Beach, Diamond and SIIG. They definitely do not make cards for Creative or supply them with chipsets.

---

### Post by Seq on 2008-12-11
I have an asus xonar dx that works rather excellently (Intrepid 64-bit).

---

### Post by Truckerpunk on 2008-12-11
Sorry Markbuntu. I'm loosing my head over this. Appreciate the answers. I just might get myself PCI card with a c-media chipset, and try that. thanks again.

---

