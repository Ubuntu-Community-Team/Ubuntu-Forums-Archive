---
title: "need help with a midi problem im investigating."
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by mr.thraz on 2007-07-04
i produce music for a living on my xp partition, started out with fl studio 5, an amd "p3" equivalent with a stock sound card and 512mgs of ram, a mouse and  qwerty keyboard. 

because i started out like this i learned to produce quality music with a minimum of hardware.(I've got a 12 track mixer i don't use, 'cause i mix in the software) all of this has cut down on my costs, and when i found out about the f/oss movement i thought "great now i can get rid of most of my software costs". the hardware i do have is cheap but i use it to professional effect.

my hardware:
0.computer
    * An extreme performance 3.33 GHz Intel Celeron D Processor with a 533MHz FSB
    * 2gig DDR xms3200 400Mhz RAM
    * 150GB Hard Disk + a 100 gig slave
    * Embedded Intel Extreme Graphics engine with 64M shared memory
    * Onboard Realtek ALC655 6-channel audio CODEC
    * A Realtek 10/100 LAN port t
    * One AGPro slot
    * 3 PCI slots, 1 CNR slot
    * 2 available SATA slots (internal)
    * 2 UltraDMA IDE slots supporting UltraDMA/100 devices with 100MB/s transfer rate
    * 4 USB 2.0 ports
    * 300W power supply for expandability
1.ion usb turntable (for sampling vinyl)
2.Sampson usb condenser mic (for vocals or live instruments)
3.akai mpd16 (as a midi controller for drums and sample manipulation)
4.creative prodikeys pc-midi (as a midi controller)
5.wacom intuos2 (for laying down involved scratches and as a midi controller for bowed or string instruments)
6.mixman dm2 (as a controller and used to lay down simple scratches and jogging tracks)

little by little I've been getting my hardware to work on os x and ubuntustudio (i triple boot xp, os x and ubuntustudio) but one piece of hardware is getting on my nerves. [the creative prodikeys pc-midi.]("http://www.prodikeys.com/")
i should really give up on it and get a real midi controller keyboard but truth be told, i love the thing.
the keys are small but seem to fit my hands perfectly and the dual nature of the thing ( its both a midi and qwerty keyboard in one.) means that it takes up much less space on my desk where i need it. 

creative refuses to release Linux or OS X drivers, or vista drivers for that matter. 
so i look for 3ed party drivers and no one has done it.
part of the problem is i don't think the midi portion of the device actually sends midi signals. i think it justs sends a signal to the driver in my window partition which in turn gives a midi signal to my windows d.a.w.'s.

does anyone know how i would go
about collecting the input from it so i can work out how it works....?

I'm sure if i know what the signals were. then a way could be worked out for those signal to trigger one of the virtual keyboards in Linux.


i wont give up on this, (I'm much to stubborn) and I'm an excellent organizer and would love to find a way to help  all the people who have bought this device and now only have a qwerty keyboard (you should see the [creative prodikeys support message board]("http://forums.creative.com/creativelabs/search?board_id=keyboards&submitted=true&q=prodikeys+"), everyone is unhappy. there are people begging for Linux drivers.)

is there an app. i can use to find out what type of signal is comming in from my usb slot when i press the midi keys?

thanks for any help you can provide.

---

### Post by mr.thraz on 2007-07-04
bump

---

### Post by christhemonkey on 2007-07-04
You need to use some sort usb packet snooper,

There doesnt seeem to be anything recent of value for linux.
The only thing i can find (from a quick google) is usbmon, but this was a patch for 2.4 series kernels...

I would suggest using windows and a tool like Usbsnoop:
[http://sourceforge.net/projects/usbsnoop/](http://sourceforge.net/projects/usbsnoop/)

and trying to discover the protocol for this device like that.



(would love to help, but i dont own one!)

---

### Post by mr.thraz on 2007-07-05
thank you.
i'll get started right away and let everyone know about my progress.

---

### Post by claypole on 2007-07-07
I have a Mixman DM2 and although I've had limited success with a driver I found, it only gets the platters to work as X and Y mouse movements and the mouse buttons, I have not even been able to use the platters successfully on any LInux music software.  Would you be able to post your success and tips on using the Mixman DM2?  I am running Ubuntu Studio 7.04 and have most of the mixing tools available for Linux installed.

Also, I don't know if it exists already, but it would be good to create an area, maybe focused on Ubuntu Studio, where people can share their experiences of music/DJ software and hardware for Linux.  I have found numerous sources on the web, but apart from Ubuntu Studio itself which comes with a number of great packages already installed, there is no single reference point.  Just a thought.  I have become a big fan of Ardour having spent some time putting a complex mix together for a friends wedding, using samples from the stag weekend, but it took me ages to realise that Ardour was the tool I needed.

---

### Post by mr.thraz on 2007-07-08
i use the dm2 mostly for windows apps, fl studio  & deckadance.
I've gotten the dm2 to work in Linux with best results in terminator x .
also it seems to do something in mixxx but i cant seem to make mixxx use any outputs
so idont know how good it is to use. mix seem like a promising  oss dj app. 
its just not a priority for me to  learn to use right now.

 i cant see getting the dm2 to work well in Linux without some pure data code.

ardour is a very well rounded app and i can't stand it. it seems bad  to say and i feel bad saying it 
but i cant stand that app. it seems like protools to me and i always felt protools was needlessly complex.

i cant wait tell reaper finishes their linux port.

energyxt2 is done and it works on linux i'll try it out next month.

I'd love a place where we could exchange advice.  lets talk to someone in charge and get it done

---

### Post by mr.thraz on 2007-07-09
[http://www.joemattiello.com/dm2/Notes.html](http://www.joemattiello.com/dm2/Notes.html)
this guy made an os x driver for the dm2.
perhaps we should get him in touch with the linux dm2 project.?

---

### Post by christhemonkey on 2007-07-10
Definately get in touch with him and ask about the protocol and how to get the settings.

Also see if you can get a copy of his source code as this may help as well.

---

### Post by spetroff on 2008-07-14
Any luck in making a Prodikeys driver? 

If not, is it likely to work if one just created a vmware Win2K virtual machine? I don't own one or I'd try it myself. I'd just like to buy one for my 9 yr. old because they are so space efficient.

Shane

---

