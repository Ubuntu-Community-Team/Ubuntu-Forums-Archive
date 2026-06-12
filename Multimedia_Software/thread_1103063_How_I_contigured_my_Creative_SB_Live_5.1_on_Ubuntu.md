---
title: "How I contigured my Creative SB Live 5.1 on Ubuntu 8.10"
date: 2009-03-22
forum: Multimedia Software
---

### Post by javaholic5 on 2009-03-22
I understand that alot of people have been experiencing some issues while trying to setup their Creative Soundblaster Live 5.1 Sound CardSpeaker and subwoofer systems in Ubuntu and since I managed to get mines to work, I decided to share it with the Ubuntu Community.

I am running Ibex Intrepid (Kubuntu 8.10) LTS server with an installation of the KDE4 desktop (xserver).

The steps in this guide may be able to work with other soundcard makes/models or other versions of Ubuntu but I have not tested others, so give it a try.

NOTE:
[LIST]
[*] **ALSA** is An audio library (and kernel level API) for Linux, and stands for ***'Advanced Linux Sound Architecture'***.
[*] The following steps have been tested on Kubuntu 8.04 and 8.10.
[/LIST]


Now lets begin...


[LIST=1]
[*]   I Visited Google and searched for "alsa project"

[*]   On the search results I found this link and clicked it:  [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

[*]   I searched for my sound card vendor (in this case 'creative labs' )

[*]   On the next page, (Soundcard List for Creative Labs) I was able to find information for the SoundCard, Chipset, Driver & Docs

[*]   I clicked on the details link for my soundcard and landed on a page with information pertaining to my soundcard.

[*]   I went through the information and read that I needed to create a .asoundrc file and add some chipset information. (This file gives you better control over your card/device)

[*]   I followed the following steps found in the afore mentioned page to create the file and add the chipset (NOTE: Use Vi/Vim/or any other editor):

Make a file called .asoundrc in your home and/&#8203;or root directory:

       *[COLOR="Green"]vi ~/.asoundrc[/COLOR]*

Copy and paste the following into the file, then save it:

       [I][COLOR="Green"]pcm.emu10k1 {
          type hw
          card 0
       }
       
       ctl.emu10k1 {
          type hw
          card 0
       }[/COLOR][/I]

[*]   Next I executed the following commands from the terminal to terminate pulseaudio services:

*[COLOR="Green"]sudo killall pulseaudio[/COLOR]*


[*]   then I executed the following command to restart Alsa Services :

*[COLOR="Green"]sudo alsa force-reload[/COLOR]*


[*]   Next, to make alsa the permanent default I entered this code:

*[COLOR="Green"]sudo alsactl store 0[/COLOR]*


[*]   Now I started my mixer / volume control in my system tray.

[*]   Next I opened the mixer at the panel (usually at the bottom of the desktop) and changed the settings to add all the speakers and turn them on by doing the following:

[LIST]
[*]-   Click on the mixer(a speaker icon on the panel - ussually next to the system clock) and pressed 'mixer
[*]-   On the mixer windows, I went to 'settings'
[*]-   Then 'Configure Channels'
[*]- On the next window, I selected 'front', 'lft', 'center', 'sorround', all the wave settings and all the SB Live as well as all the 'Sigmatel' settings and clicked 'OK'
[/LIST]

[*]   Next I tested my speakers by playing my favourite songs (Belly danza by Don Omar/Bennie Man, Some Arcangel songs, and of course some Wisin and Yandel songs) and all worked great.
[/LIST]

---

