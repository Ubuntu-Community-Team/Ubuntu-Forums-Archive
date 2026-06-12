---
title: "no gnome/poor flash"
date: 2010-03-29
forum: Mythbuntu
---

### Post by joejoe148 on 2010-03-29
I am working on a Mythtv frontend/backend/desktop and am at a loss. The goal is to use myth to record programming from the free broadcasts (I fired the cable) and the desktop to watch flash video of the shows that arent on the broadcast networks...like TNT, natgeo or the comedy channel.

Software is Mythbuntu 9.04 running nvidia 180 drivers 

I imagine the hardware is adequate, it is well above minimum specs that I can find. 

AMD Athlon 3000+ processor
2gigs of PC2700 memory
Gforce 6200LE 512MB DDR2 video card AGP
Hauppage HVR-1600 tv card PCI

I have two problems, well three now if you count the crashing firefox.

Myth TV is working fine. There was a conflict with the video card and the tv card but there were enough helpful posts here for me to noodle through it and get it working. 

But now when I try to view flash video it is jittery...Firefox has started crashing now and that is a new thing. It will allow me to start a video and then the window will just close with no warning. I tried a local radio stations website and it did the same thing. When I connected to pandora it worked but I could only get the songs to play for around 30 seconds before it would skip to the next one.

The other problem I cant figure out is probably simple. I wanted to have the Gnome desktop instead of XFCE but nothing I do seems to change it

With that explanation in mind:
Is this hardware enough for what I want to do?
Is loading Mythtv first then adding gnome the best solution? (if not, I think I can redo the Mythtv setup and conflict resolution again without cracking up)

and I suppose any suggestions? 

I have spent a little bit looking over the working hardware sticky and dont see any reason why what I have isnt working...at least from a raw horsepower standpoint.  I evidently broke something getting the HVR1600 to work.  and damnit it seems to be working fine.  I am now in a quandary.  Does anyone have a sense of the best way to aproach the above goal?  or should I dig up another box and separate the front and backends?  Should I reload from the beginning starting with ubuntu and add myth?  


thanks in advance

---

### Post by nickrout on 2010-03-29
to get gnome run ```
sudo aptitude install gnome-desktop
```

---

### Post by joejoe148 on 2010-03-31
Nope, several dependency conflicts and none of the resolutions offered worked.  Obviously I need more tequila.  It appears that flash isnt all there either when I tried to install/reinstall flash it errored out also.  

I plan on trying the ubuntu install with myth on top next and if that doesnt work I suppose I will separate the front and backends.  

do I need a tv tuner card for the front end and the back end...I need to do some reading again.  the hardware sticky should be a place to start i guess

---

### Post by nickrout on 2010-03-31
once you have installed ubuntu do ```
sudo aptitude install mythbuntu-desktop
```

No you do not need a tuner card in the frontend. Thats the whole point of the backend - frontend split.

---

### Post by joejoe148 on 2010-04-01
OK, system seems to be working.  Installed in this order
Ubuntu 9.04
updates
flash
Mythtv-desktop
then I did the magic with the cx18 drivers and the nvidia upper memory allocation.(as you can tell I was following instructions and had no idea what I was doing)
Then I setup the backend and we are good to go

Flash works
Myth works
Gnome works

Now I just need to figure out the remote

---

### Post by nickrout on 2010-04-01
why 9.04?

---

### Post by joejoe148 on 2010-04-02
9.04...The first time I loaded Ubuntu on this setup the onboard sound did not work with 9.1.  It was right after the release of 9.1 and sound issues were comon.  At the time a lot of folks were going back to 9.04 and that worked for me.  I decided to stick with that for now instead of introducing new worries. 

Is there a compelling reason for me to try 9.1 or even 10.04?

---

### Post by nickrout on 2010-04-02
yes, 9.04 -> mythtv-0.21
9.10 -> 0.22
10.04 -> 0.23

---

