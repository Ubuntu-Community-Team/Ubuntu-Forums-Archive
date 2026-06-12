---
title: "myth settings"
date: 2009-10-30
forum: Mythbuntu
---

### Post by eliofall on 2009-10-30
ok i am doing my first myth install. i am using the gnome desktop, the hauppaugel hvr 1600 card, i am in in Texas(kinda close to houston) with suddenlink(analog) cable.i have been googling around all night trying to find what i'm missing but i cant get any channels. i booted up xp and installed the isk that came with the card to see it it would show me what protacall to use but the setting it had were every basic(analog-cable>us>auto scan> and it was working)   

one thing i'm not understanding is the video source. is that just a tv guide? so couldnt i just use the "no grabber' setting or do i need it to scan for channels? i tried just adding a channel, no luck there either.

ok this is the long way of asking( i was wanting to say what i already tried), in capter card setup>card type>analog v4l capture card.dev/video0  the right settings there?   it shows my card under probed info as hauppauge hvr-1600 [cx18] 

and is there a .conf file? it takes a lot of time to navigate through all those menus.

any detection some one could give me would be greatly welcomed

---

### Post by mythding on 2009-10-30
First things first. Read through this and see if it helps.
[http://www.mythtv.org/docs/mythtv-HOWTO-9.html#ss9.1](http://www.mythtv.org/docs/mythtv-HOWTO-9.html#ss9.1)

---

### Post by eliofall on 2009-10-30
oddly i read thought that and didnt see what i was looking for so i have my gf read it to make sure i didnt miss something... 

do i have to have a SchedulesDirect.org account to make mythtv work?

---

### Post by uopjohnson on 2009-10-30
Yes, you need to setup schedules direct, otherwise you won't get a lot out of mythtv.

---

### Post by egandy on 2009-10-30
I started out using Mythbuntu 7.10 at that time you could get everything working without Schedules Direct.  I had it working without it but quickly decided to subscribe to Schedules Direct because my guide data was unreliable on my OTA stations. Here are the basic steps you need to do for a tuner.

1. add the capture card

2. add the video source
    I would add Schedules Direct 
    Remember to name it in the top box or it will be invisible on
      the video source list I have done this many times.
    Retrieve the listing data or your guide data won't show up.

3.  Connect the capture card to the video source.
    Go to Input Connections and select your tuner.
    On the Input Connections screen go up to video source and 
      hit the right arrow until your video source is in the box.
    Go down and scan for channels.


That should be it. Good Luck

---

### Post by eliofall on 2009-10-31
ok ii seem to me coming along but i have have hit another problem.

the WinTV-HVR-1600 tuner card i have is having a conflict with the nvidia driver. if i have the driver activated and the card luged in then ubuntu not boot in to x.  it jsut cos to a commandline longin and the screen will flicker.

 i have been looking round but cant find fix for this. is there a way to make the tuner card and the nvidia driver both work?

---

### Post by dano1 on 2009-11-01
see this:

 [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

regarding nvidia .

---

### Post by eliofall on 2009-11-01
hey thanx dano1. i seemed to have over looked that. 



... i guess noobs should come with a worning lable.

---

