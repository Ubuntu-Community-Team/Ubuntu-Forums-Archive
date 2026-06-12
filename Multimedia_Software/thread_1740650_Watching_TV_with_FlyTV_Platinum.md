---
title: "Watching TV with FlyTV Platinum"
date: 2011-04-27
forum: Multimedia Software
---

### Post by TheStroj on 2011-04-27
Hi everyone!

I found this old LifeView FlyTV Platinum card, put it in the computer and tried to make it work with Ubuntu. It gets recognized with
```
dmesg | grep saa7133
```
but this is where I'm stuck. I know this might sound stupid, but, what now? :P

It is in, but what do I have to do to actualy _watch_ TV? Is there any program for that that I have to install? Any more configuring to do? I can do anything, it's not a problem :).

I hope anyone knows the answer, any links to tutorials or useful sites are also appreciated :)

Thanks in advance!

---

### Post by sq7bti on 2011-04-27
There is a few apps to watch using v4l (or v4l2) compatible tuner. I use xawtv and mplayer, with preference for latter, as I use a headless PC humming in my hallway, to watch TV via network.

This is a part of .mplayer/config:
```

[radio]
radio = driver=v4l2,channels=93.4=Radio_1,94.0=Radio_2,94.9=3FM,95.9=Radio_4,96.4=Radio_5,97.4=VRT_Radio_1,99.4=VRT_Radio_2,100.1=VRT_Klara,92.9=Omroep_Brabant,94.4=Lokale_Omroep,102.6=Radio_Decibel_Eindhoven,107.9=BBC_Radio_1,106.5=BBC_Radio_3,91.6=100%_NL,90.1=WDR_3,92.1=WDR_4,90.6=Arrow_Classic_Rock,100.9=Arrow_Jazz_FM,103.5=FiP,88.9=BNR_Nieuwsradio,88.4=Classic_FM,101.9=Radio_6,97.0=Radio_Hollandio,98.5=Slam_FM,97.9=FunX,101.4=Kink_FM,103.1=Q-Music,107.4=Radio_8FM_Brabant,106.9=Radio_10_Gold,105.4=Radio_538,91.1=Radio_Veronica,105.0=Radio_Royaal,104.4=Sky_Radio,87.9=XFM,95.5=Efteling_Radio,100.5=Studio_Brussel,98.9=Tweede_Kamerlijn
ao = esd

[tuner]
tv = driver=v4l2:norm=PAL:chanlist=europe-west:width=384:height=288:adevice=/dev/dsp:audiorate=32000:tdevice=/dev/vbi:channels=216000-Nederland_1,184000-Nederland_2,192000-Nederland_3,720000-RTL4,728000-RTL5,736000-RTL7,792000-SBS6,784000-NET5,672000-Veronica,176000-DisneyChannel,264000-Omroep_Brabant,256000-Studio040,200000-VRT_TV1,208000-CANVAS/Ketnet,544000-NationalGeografic,800000-Discovery,568000-KinderNet,528000-MTV,224000-ARD,232000-ZDF,240000-WDR-3,768000-EuroNews,272000-BBC1,280000-BBC2,752000-CNN,552000-10,288000-TV5,248000-RTL8,816000-Eurosport,536000-Nickelodeon,664000-AnimalPlanet
display = nb10:0.0
vf = crop=368:208:10:40
ao = esd

```

s.

---

