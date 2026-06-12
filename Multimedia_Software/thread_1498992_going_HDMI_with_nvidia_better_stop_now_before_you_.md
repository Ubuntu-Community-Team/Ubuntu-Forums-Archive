---
title: "going HDMI with nvidia? better stop now before you go mad"
date: 2010-06-01
forum: Multimedia Software
---

### Post by puntua on 2010-06-01
Im using ubuntu since 2007, 2 laptops, one without any problem, the second had a few minors issues that i get to fix, and that eventual releases get better.
So... i think building a pc for my hdtv with hdmi, since my laptop just do vga and look gosthly (maybe a cheap cable)
If you think the same FORGET IT
i get a nvidia GT240 and its just problem after problem

1. livecd dont work, so you had to go around
2. after installing, the hardest by far in my 3 years installing ubuntu on several machines, it need several restarts, sometimes did nt boot at all, sometimes crash, sometimes go to a dialog.
3. much work after, i installed the property drivers, thinks go a little better, but no sound.
4. not sound with hdmi, nor with spdif, i manage to get sound with the vga output, but sometimes work sometimes dont.
5. trying a lot of things for hdmi, from building sources, running scripts but nothing work, so i ve up.
6. 2 LONG weeks its a no sound, either hdmi or spdif, so lame

- i just start downloading ubuntu 9.1, to see if i get lucky, because ubuntu 10.4 its by far the most unstable, buggy, crashing release i had ever used. for the first time since 2 years im looking to try other distro.
never before an ubuntu release had crashed on my, im talking about my trusty laptop not that pc im building, had so many bugs, even im not sure it will boot fine, something i take for granted in the past.

---

### Post by puntua on 2010-06-03
OK... maybe i rushed my last post.

ABOUT ANALOG SOUND
my tv seems to had a problem with hdmi/dvi and analog sound, hard to find out... until i check my pc sound out with mi line-in laptop... so google my tv and found that the problem is general and can be fixed with a firmware, if any had a sony should check this [http://esupport.sony.com/US/perl/swu-download.pl?template=&upd_id=5350&SMB=YES](http://esupport.sony.com/US/perl/swu-download.pl?template=&upd_id=5350&SMB=YES) but sadly it didnt work for mY HDMI4, my analog sound just dont work when hdmi or dvi are plug in, oddly it work as soon as i disconect the hdmi/dvi cable, or when ubuntu go to safe graphic mode, but now that i test it the line-out with my laptop i think its more like a tv problem than ubuntu or nvidia, STILL NO ANALOG SOUND

ABOUT HDMI SOUND
after i discover my pc was doing nothing wrong at the analog front, i look to give one last try at the hdmi, since wasting money in a dvi-hdmi cable didnt work, and finally i get the sound, i take some parts from some tutorials, because not a single one worked for me, but taking parts from one and another get the job done...so

1. first use this script [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)
2. sudo apt-get remove linux-backports-modules-alsa-`uname -r`
3. sudo gedit /etc/modprobe.d/sound.conf
4. put that line in the new file "options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2"

* you can skip step one, you just need alsa 1.0.23, so you can download the source and built manually, but since i had never compiled or used source,i search for a deb, cant find one, but find the script, thank you SOUNDCHECK

---

### Post by puntua on 2010-06-03
last post also rushed...
weird, seems like only totem play sound, speaker-test also work.
but everything else NOT, firefox, ubuntu, and other aplication dont make sound.
im buying speakers to put along my tv and get digital video (dvi) and analog sound with the speakers, cause analog video (vga) at full hd that work with my tv with sound is just a no-no(gosthly blurry images), now i dont know who to blame nvidia, ubuntu or sony... most likely nvidia.

---

### Post by puntua on 2010-06-03
installing new beta drives from nvidia didnt work, and i almost sure nvidia is the problem, i just got back with my not so light pc from a friends house that let my try my pc in their samsung tv.
the vga looks more sharp and less blurry and less ghostly than in my sony, but not perfect, apparently tvs get more precise color and overall better image from vga than from dvi/hdmi, at least was the same the case in both sony and samsung, you just need to do a lot of settings in dvi/hdmi to get a natural experience, vga input get a better job.
sadly with the dvi/hdmi and analog, the samsung was worst than sony, it also get no sound, but neither with just the analog, the sony did get sound this way.
so, im sure nvidia is the problem, i guess somehow the card send sound (white noise or not real sound) so the tvs ignore the analog input in favor of the "sound" that came in the hdmi.
i guess i will wait a lot of time for the hdmi to work since the beta drivers dont work neither, the thing i get sound to totem but not everything else, give me hopes, but its much trouble and got to a road-end.
actually i get video and sound from dvi+analog, with nouvoe (or that driver that ubuntu use before the restricted are installed) but no 3d games
so i will need to install windows (blasfemy i know) but since i waste 2 weeks trying and reinstalling ubuntu many times, im not scared anymore to go the bad way, 3 years away, wonder whats the windows world is today, i just build the pc to play some games in wine, so, maybe if i installed windows just for the games the last 2 weeks i had been playing instead of going mad.
one thing its sure, after this i will give up to pc games, windows or wine, too much trouble... im regreating building this pc, i could buyed a lot of ps3 games instead and problems free... yeah i should go that way

---

### Post by puntua on 2010-06-04
FINALLY get the sound from hdmi, im so happy dont have to go back to windows, well cross fingers.
i recommend this links, they save me from go back to windows (i dont really know if i would end up returning to windows, its like last step before suidide, lol)

1. [http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240) you get most information from this site, it didnt work for me, but it was the most useful
2. [http://www.nvnews.net/vbulletin/showthread.php?t=150113&page=3](http://www.nvnews.net/vbulletin/showthread.php?t=150113&page=3) zim2dive: i feel your pain, sadly it didnt work for me entirely, but knowing someone with the same card was getting near, help me hang in there and keep searching
3. [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137) dont know how harder would be to install the new alsa drivers without this script thx
4. [http://ubuntuforums.org/showthread.php?t=1501027](http://ubuntuforums.org/showthread.php?t=1501027) it help me to see were the problem was, the code improve my results, so i read a lot of pulseaudio and .asoundrc to find the answer.

i dont really know what exactly worked, i was just throwing everything to see what hit.
i just wanted digital video and sound for wine, and i got it, sure i wont touch this system/ubuntu/so, not even install updates, neither messying trying to find what worked and what not.
the last i change was in .asoundrc
pcm.!default hdmi:NVidia_1
pcm:iec958 hdmi:NVidia_1
just put the _1, cause i had 2 NVidia sound cards, the analog from the mobo and the hdmi from the pci gt240, used aplay -l, to find which
also in alsamixer i get a new column with volumne for the hdmi that i never see before, i get it after the code from point 4 and installed 3 packages from synaptic, pulse audio volume control, gtk default sound card and dont remember the other, i may installed other packages, dont remember, i was just trying everything i found to the hope it worked, so dont know if those are mandatory.
this is mandatory for wine to work from point 2, at least in my case
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel

well that end this thread, that apparently was just and scape to my frustation cause nobody was interested in it, so it can be deleted, or whatever, im happy and VERY tired

---

