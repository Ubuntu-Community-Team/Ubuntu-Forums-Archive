---
title: "mythbuntu or mythtv"
date: 2009-04-28
forum: Multimedia Software
---

### Post by jarrah-95 on 2009-04-28
i am thinking about downloading eather mythbuntu (to put onto my ubuntu9.04 laptop or mthhtv but im not sure witch one ill mainly be using it for watching an recording tv so ill need capability for both and an epg  also my tv card works with ubuntu but im notsure about myth tv its a
gigabyte u8000

witch one whould you recomend

thanks

---

### Post by rubberist on 2009-04-28
Mythbuntu is based on mythtv so they are effectively one and the same. You can either install mythbuntu from scratch (which is arguably easier to set up) or add it to your existing ubuntu install from the repositories...

---

### Post by issih on 2009-04-28
Mythbuntu is a version of ubuntu that is really meant to be a turn key media center. It uses a light weight window manager and has almost no applications installed, other than mythtv itself. Technically, however, it is a full operating system, designed to be installed onto a spare machine to turn it into a media centre appliance.

If you just want to be able to use mythtv, and still use your computer as normal alongsde it, you want to install mythtv onto a normal install of ubuntu.

Fortunately all of the work that the mythbuntu team has done to make using mythtv a bit easier is available from a normal ubuntu install, just install the mythbuntu control centre package from the repositories, and it will provide you with a little wizard type thing, that will guide you through installing and setting up mythtv on your box.

Hope that helps

P.S. myth can view and record tv from any device that linux can interact with, and provided you have a listings source it can also handle EPG duties

---

### Post by jarrah-95 on 2009-04-28
ok thanks i think ill just download mythtv and the control center but do i need to install the backend as well as the frontend

---

### Post by issih on 2009-04-28
Just download the control centre...it will take care of downloading everything else. The command:

```
sudo apt-get install mythbuntu-control-centre
```

will install the required package (mythbuntu-control-centre), or just search for it using synaptic or add/remove.

The control centre will automate downloading all the extra packages required to use mythtv, dependent on how you plan to use the computer.

If you want a single seat set up with the recording backend and the viewing software on one machine the control centre will download and install both, alternatively if you plan to split the functionality between machines it will let you just install the backend or the frontend. It will also take care of installing and configuring the sql database. It will make your life much easier.

Hope that helps

P.S. I may be wrong, but from your posts I suspect you aren't quite clear how myth works.

In essence, think of the backend as a video recorder. It is the only bit of software that connects directly to the tv tuner hardware (and therefore must be installed on the machine that has that hardware connected to it). The backend sits there running in the background, and whenever a recording is scheduled, connects to the tv tuner and records the program to a file on the hard disk. The backend can do a few other things, but the only other really important trick up its sleeve is that it can take a video file on the disk and stream it (over networking protocols) so that it can be viewed.

The front end is in essence a network viewer, it connects to the backend over the network, instructs it to start recording whatever channel you want to watch, and then instructs it to stream the file that channel is being recorded into. It then displays that stream. In the same way, anything that has already been recorded is simply located on disk by the backend and streamed to the front end. You can also use the front end to schedule tasks for the backend to perform, such as future recordings, or transcodings.

This separation of functionality means that if you just want to have 1pc that acts as your dvr/television you need to use the control centre to install both the backend and the frontend, and they will communicate on the pc via the loopback interface.

You can also set up a pc that you never intend to watch tv from as a headless server running just the backend, or a pc used solely for viewing running just the frontend (note that all this pc needs to view tv is a network connection to the backend, nothing more) the system is very flexible.

---

### Post by jarrah-95 on 2009-04-29
thanks you where right i was using me tv with 8.04 then 8.10 dident work with my card so i couldent use anything but now that i want to record im looking at mythtv

thanks for all your help

---

