---
title: "Help design new setup"
date: 2009-03-18
forum: Mythbuntu
---

### Post by muscleman on 2009-03-18
I am hoping to get some advice on designing a new setup. I currently have a cable company provided DVR. I don't watch cable stations, so I am going to cancel cable and use over the air. I am thinking about the following setup. Can you look it over and tell me your thoughts?

I think I am going to setup a Mythbuntu server. The server will have a WinTV-HVR-2250 card installed. This server will be used to record and store TV programs, and serve up MP3's.
 
My main TV will use an xbox 360 to stream video from the mythbuntu server. This TV will have a digital converter box because it does not have an HD tuner.
* QUESTION - How well does the xbox 360 work with mythbuntu or does it?
* QUESTION - Xbox 360 vs Xbox XBMC - which is better on this setup?

My bedroom TV will have an Xbox running XBMC. It also needs a converter box, but I don't have a second one.
* QUESTION - With the above setup, are there any other ways for me to view over the air HD besides buying a converter box?

Is there a better way to design this? Thanks in advance!

---

### Post by Afkpuz on 2009-03-19
> **muscleman said:**
> 

* QUESTION - Xbox 360 vs Xbox XBMC - which is better on this setup?


Well, I know that in mythtv, there is an option to use "xbox hardware".  However, how to get mythtv on your xbox is not something I know about.  So, I assume that mythtv+xbox front end would work well.


> **muscleman said:**
> 
My bedroom TV will have an Xbox running XBMC. It also needs a converter box, but I don't have a second one.
* QUESTION - With the above setup, are there any other ways for me to view over the air HD besides buying a converter box?

Is there a better way to design this? Thanks in advance!

I'm not sure if you completely understand how mythtv works.  You have computers (or an xbox which is a console sized computer) which can either run backends or frontends for mythtv.  Backends do the actual work of recording shows, talking with TV tuners, and forwarding media over the network.  Frontends only playback media received from a backend.  



Thus, there is a way to get HD on your xbox frontend: use it as a frontend and use component(not composite) input from the xbox.  RCA output from the xbox can't get carry an HD signal, but the red/green/blue cables can.  Also, HDMI can.  So, record your HD content on a computer, then watch them on your xbox.  Furthermore, you won't need a converter box if you simply buy a digital TV tuner for your computer.

---

### Post by newlinux on 2009-03-20
I don't think an Xbox has the hardware power to playback HD Mpeg-2. So that might be one problem. If you are capturing your signal from one of those converter boxes it won't be HD however (it will have been downconverted). An Xbox 360 definitely has the power to playback HD Mpeg-2, but I don't know what the XBMC support is for the Xbox 360. It can playback myth recordings using UPnP however...

---

