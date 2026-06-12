---
title: "vfd display help need"
date: 2007-11-22
forum: Mythbuntu
---

### Post by madman100 on 2007-11-22
hi all i have a Thermaltake  Mozart Sx Media Lab case and remote is a imon pad  vfd is oem version 
i have installed mythubuntu 32bit runs very well but no vfd display and the remote only play  , stop,enter
will work on the remote so can any one please  help me to get the  vfd display work and get the other buttons working

---

### Post by orasetaina on 2007-11-23
i have the exact same case ...and the exact same problem!!!! :confused:

---

### Post by mutation on 2007-11-24
can't help you with the remote problem as i lost mine, but the vfd display, let me see if i can remember what i did,

1. install LCDproc

2. edit LCDd.conf and change driver=imon

reboot and you should be up and running on the display

---

### Post by madman100 on 2007-11-24
hi mutation thanks vfd display  all working now got the remote working with only a few buttons missing you can get lircconf files for most remote from this site [http://lircconfig.commandir.com/](http://lircconfig.commandir.com/)
and LIRC iMON Patches from this one [http://brakemeier.de/electronics/vdr/lirc-imon.html](http://brakemeier.de/electronics/vdr/lirc-imon.html)
thanks :guitar:

---

### Post by orasetaina on 2007-11-26
> **mutation said:**
> can't help you with the remote problem as i lost mine, but the vfd display, let me see if i can remember what i did,

1. install LCDproc

2. edit LCDd.conf and change driver=imon

reboot and you should be up and running on the display

cool i will try this.!

I will update here after ive tried this. 
Thank you :)

---

### Post by orasetaina on 2007-11-26
Madman,
Can you put up a descriptive detail as to how and what you did?
It might help others like me who are not very technical but would like the imon and vfd working in gutsy too!!!

---

### Post by orasetaina on 2007-11-26
:)

---

### Post by madman100 on 2007-11-28
hi m8 install lcdproc  then open a text editor in root ie sudo kate =password then click on the blue folder in kate then click the arrow till you get to / then click on /etc and then scroll till you find LCDd.conf open it and change the line drivers=cruse to imon then click save then click save as and overwrite it  reboot the pc then in myth setup in go too appearance enter it till you find LCD device and enable it and now your vfd will be working and showing myth display :)

---

### Post by orasetaina on 2007-11-29
All that is ok...but im trying to make the VFD work ...without any mythtv. I dont want mythtv...im running plain gutsy!

---

### Post by orasetaina on 2007-12-01
ok ive successfully managed to make my vfd work.!

Now all thats left is the remote. As stated before i have the thermaltake mozart case!

the remote works when im actually in mythtv and when im playing a file. so when im playing a video only play and pause buttons work. and the volume button. None of the buttons works including the pad in the middle.

Can someone help me this please?

---

### Post by orasetaina on 2007-12-03
ok so i managed to finally get the VFD working...looks great! 

now currently trying to get the remote to work. 
The volume buttons work fine..as to stop, pause and play ...but nothing else works! 
when i press up and down. It kinda functions like a page up and page down (will go to the first or last item on the menu)

Anyway what can i do to make my remote properly?:(

---

### Post by volkswagner on 2007-12-30
I did a fresh install and performed these steps

>  Originally Posted by mutation  View Post
can't help you with the remote problem as i lost mine, but the vfd display, let me see if i can remember what i did,

1. install LCDproc

2. edit LCDd.conf and change driver=imon

reboot and you should be up and running on the display

I also ran the following first not sure if it made a difference
```

sudo apt-get install module-assistant
sudo m-a update,prepare
```

VERY HAPPY TO SEE VFD DISPLAY!  THANK YOU!

---

### Post by radu.c on 2008-03-26
Does anyone of you have a /dev/lcd0 device? I have a Mozart SX with MediaLab case, but there is no /dev/lcd0 device, thus lcdproc says imon can't work. I'll have a Mythbuntu installed later, to see if it works with it and what it does different.

---

### Post by Laughing man on 2008-04-10
I am also in plain ubuntu without mythtv i have done all those things and i can't make the vdf work and show anything neither the remote.:confused:
I simply can't do it and i have tried other ways too but :confused::confused:
](*,):roll: HeLp

---

### Post by zugol on 2008-04-18
Hi, 

I'm looking for vfd plugins for media applications like totem or mplayer. Both of my iMon vfd and remote are working but I need stuff to display...

Thanks for your help.

---

### Post by Trollslayer on 2008-05-04
> **orasetaina said:**
> All that is ok...but im trying to make the VFD work ...without any mythtv. I dont want mythtv...im running plain gutsy!

How do you want to drive it? [COLOR="Red"]echo "Hello world" >/dev/lcd0[/COLOR] works for me that way.
no changes to LCDd.conf either.

---

### Post by zugol on 2008-05-12
The lcdproc delivred with Ubuntu is server side. I need client. But I've fount nothing for i-mon.

---

