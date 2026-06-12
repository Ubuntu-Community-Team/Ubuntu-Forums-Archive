---
title: "some basic &quot;is this possible&quot; questions"
date: 2007-10-20
forum: Mythbuntu
---

### Post by Helmi on 2007-10-20
Hi TV-Folks,

i'm currently running a windows machine just to watch tv which sounds too stupid to last for more than a few more weeks. This is why i think about using linux to watch tv.

I don't like to put that TV-Card (Hauppauge [PVR-150]("http://www.hauppauge.com/pages/products/data_pvr150.html")) into my desktop pc - i'd more likely have it in the server running a mythbuntu backend (i don't know too much about that yet) there and stream the live tv programm over the network.

I heard this is primarly possible but there's still some questions left:

- Does Mythbuntu run on VMWare? The Server is currently hosting 5 virtual machines with his load beeing still < 0.20 (P IV 2,66 GHz, 2GB RAM)
- How is the CPU impact with the PVR-Cards as they do lot's of stuff themselves and provide a mpeg-stream it shouldn't be too high
- can i add more cards to serve more clients or probably record and view TV the same time?
- how much bandwidth does the tv streaming over the internal network need?

Thanks for any helping answer ;) ):P

---

### Post by leech on 2007-10-20
The quick answer would be yes.  

The long answer is that I'm not sure about the VMWare part of it.  I'm not sure if VMWare would see your TV card or not, since it basically creates a virtual system itself and only supports a subset of your hardware (in the same way that it doesn't really use your video card, just emulates one through the vmware driver.)

MythTV works as a frontend / backend system.  So I think you can actually have as many front ends as you'd like to view streaming video on, but not sure how it works if you had two computers wanting to view two different TV stations with only one TV tuner (I don't think this is possible) but you could always have two or more PC's viewing recorded media from the same back end, as long as you have the bandwidth, of course.  Which with Gigabit is easy.  

Leech

---

### Post by superm1 on 2007-10-20
Well in your particular situation, this won't work.  As leech said, vmware lists virtualized hardware only.  

Multiple people have however setup mythbuntu backends in virtual machines for other types of tuners.  USB and network tuners are both accessible in virtual machines.

As for the other questions:
around 6mbps for streaming to other machines.  You can add up i think 6 pvr-150's in the same box.  There is a hard limitation somewhere around there.  You can add more backends though if you need more.  These cards are not CPU intensive at all.

---

### Post by Meph1st0 on 2007-10-20
Just a few days ago I downloaded Mythbuntu RC and tried to run it in VMware just to see how it looks even though I don't have a tv tuner in this machine.  It wouldn't even get past the option screen to install.  I really don't think VMware is a good solution.  Though, it may have just been my setup.

Nevertheless, superrm1 and leech are right about the virtualized hardware statement.  It's not going to take full advantage of the hardware in your machine as it will use VMware's drivers and virtual hardware.

---

### Post by apauna on 2007-10-21
I use VirtualBox every day it is much like VMware, but maybe it will work for you. As far as vming the tuner, good luck. Best bet is usb tuners as superm1 said and I have never tried that in VirtualBox. I use VirtualBox over VMWare because I did some testing and found it to be more usable then VMWare.

Some downfalls of VirtualBox.
[LIST=1]
[*]Have to create a Bridge Network to do full network support. Unlike VMWare, Virtual Box makes you do this manually. Hopefully in the future they go closer to the way VMWare creates bridges, which I have heard will also fix #3 below.
[*]Cap Locks do not work well in VM.
[*]If wireless and Virtual Box running in windows XP, good luck getting bridge networking to work.
[/LIST]

Anyway here is a link to VirtualBox.
[http://www.virtualbox.org/]("http://www.virtualbox.org/")

---

