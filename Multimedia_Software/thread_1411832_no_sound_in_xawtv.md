---
title: "no sound in xawtv"
date: 2010-02-20
forum: Multimedia Software
---

### Post by leeper69 on 2010-02-20
Hi  I have just purchased a PCHDTV 5500 TV card and am trying to get it working with XAWTV. the following is a list of my hardware.
EVGA Nvidia Ge Force 9500gt video card
Sound Blaster live platinum sound card
Q9550 Pentium quad core CPU  
EP45-UD3R Gigabyte motherboard
Sony DVD drive
Sony DVD recorder
500 GB Seagate Barracuda sata hard drive

 The TV card is hooked up to my Direct TV receiver using svidio and the included cables audio connector is plugged into the line in jack on the sound card. 
 I am using Ubuntu 9.10 and Alasa for sound I down loaded Gnome Alasa mixer and the line in slider is not muted and turned all the way up. if I go into sound preferences to the hardware tab I get two devices the cx23880/1/2/3 pci video and audio decoder(audio port) 1 input analog stereo input and the SB Live! emu10k1 1output/1 input analog stereo duplex. I am confused shouldn't the TV card be showing an output not a input but there is only the input and off choices in the property field. under the input tab the cx23880/1/2/3 pci video ans audio card has the spot in the radio button and under the output tab the radio button is marked for the SB Live stereo stereo.
NOTE: when xawtv is started and the small window pops up there are green vertical bars on the screen with the picture but if I enlarge the window they go away.
can anyone help me with the sound problem?

---

### Post by leeper69 on 2010-02-21
I tried to set up the pchdtv 5500 card with coax cable from my Direct TV receiver and the sound output from the TV card plugged into the line in jack on my Sound Blaster live card (still no sound)

I tried to use the on-board sound card on my EP45-UD3R Gigabyte motherboard. (still no sound)

I went back to the Sound Blaster live card  because of better sound quality and am hoping to get a response to this thread from someone who has the pchdtv 5500 card working with Ubuntu 9.10. kernel 2.6.31.17-generic
I tried to load the newest v4l-dvb drivers using mercurial from [http://linuxtv.org](http://linuxtv.org) but when I was done installing them after the reboot tv time couldn't find device 0 and I couldn't even get the picture anymore so I removed the kernel then reloaded it the picture is now back but sound is still not there. next I tried blacklisting the cx88_alsa driver still no sound so I set everything back the way it was originally 'in blacklist .conf next I tried to alter alsa_conf by rimming out the line 
options cx88_alsa index=2 (the rimmed line= ( # options cx88_alsa index=2 )the brackets are not used.  then I added the following lines under it.
alias snd-card-0 snd_em19k1 
options snd_em10k1 index=0
alias snd-card-1 cx88_alsa
alias snd-card-2 cx88_alsa 
alias snd-card-3 cx88_alsa
options cx88_alsa index=1,2,3
then saved the file and rebooted still no sound from the pchdtv card.

NOTE: the green bars found when using the svideo setup are no longer on the screen when xawtv starts up with coax going to the tuner on the card.

Has ENYONE got the pchdtv 5500 card to work with ntsc signals?

---

### Post by leeper69 on 2010-04-05
I just received a new pc-HDTV 5500 card from Jack and guess what still no sound using the svideo input with  the blue jack of the adapter cord plugged into my sound blaster value card. I finally got the system to work by making a patch cored with RCA jacks on one end and a mini din jack on the other,and plugging the rca jacks into my Direct TV receivers composite audio out red and white and the mini din jack into my sound cards mike in   
now when I start up the Direct receiver the sound is automaticly on all the time. I chose tvtime for the Gnome desktop and xwatv for the KDE desktop I now use the TV as my desktop wallpaper in Ubuntu.

---

