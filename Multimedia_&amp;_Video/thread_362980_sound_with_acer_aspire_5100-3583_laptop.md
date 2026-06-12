---
title: "sound with acer aspire 5100-3583 laptop"
date: 2007-02-16
forum: Multimedia &amp; Video
---

### Post by randytuggle on 2007-02-16
I just installed 6.10 32bit last night on my refurbished acer aspire 5100-3583 laptop. The sound controls don't seem to offer much help! Most of the time, the volume control at 100% gives a very low volume level through the speakers. I did several reinstalls of alsa drivers and also installed the gnome-alsamixer program. The Gnome-Alsamixer program helped to give volume to the speakers - but this install doesn't come close to the way 6.10 worked on my HP desktop. Does anyone have a solution to this issue? ALSO - I cannot get alsamixer to start. I get "alsamixer failed to load:invalid argument" when trying to run alsamixer from the terminal. Please help me get this acer aspire 5100 to run normally if you can. Thank you!

---

### Post by dominykast on 2007-03-04
Applies to Ubuntu 6.10 Edgy. Not tried on other versions

Hi to everyone,

I bought myself Acer Aspire 5100 (aspire 5104WLMi just to be precise) just to find out that video card ATI Radeon Express 1100 is an issue (_[solution here]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")_) with linux and sound card HDA Intel is an issue as well. After long very long research I finally found a solution for Ubuntu 6.10

Firstly install latest alsa drivers, alsa libs and alsa utils ([_there is many guides around_]("https://help.ubuntu.com/community/HdaIntelSoundHowto")) DO NOT RUSH to push the link. Please note that in this description the author did not mention that after you ./configure, make and make install the alsa driver you also have to enter command "sudo ./snddevices" to create sound devices, hence the compilation of alsa driver looks as follows

sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
sudo ./snddevices

Now you can push the [_link_]("https://help.ubuntu.com/community/HdaIntelSoundHowto").

Once you configure compile all the drivers enter the command

sudo chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi

then

sudo modprobe snd-hda-intel
sudo modprobe snd-pcm-oss
sudo modprobe snd-mixer-oss
sudo modprobe snd-seq-oss

then 

sudo gedit /etc/modrobe.d/alsa-base

and enter the following into this file

snd-hda-intel probe_mask=3 position_fix=3
alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel

sudo gedit /etc/modrobe.d/sound
options snd-hda-intel probe_mask=3 position_fix=3
l
ast but not least 

sudo rm /etc/asound.*
sudo rm /var/lib/alsa/asound.*

and finally

sudo reboot

after you will restart no more sound in one speaker or any troubles with the sound. I am still working with microphone problem as the sound which one is able to record can be barely heard and if I find solution I will post it here. 

Regards,

Dom

More information [http://www.burghardt.pl/wiki/articles/installing_and_using_debian_on_acer_aspire_5102wlmi](http://www.burghardt.pl/wiki/articles/installing_and_using_debian_on_acer_aspire_5102wlmi)

---

