---
title: "Setting up Frontend/Backend - is this correct?"
date: 2010-11-03
forum: Mythbuntu
---

### Post by Sternfan on 2010-11-03
Hi all,

I was thinking of setting up a home theatre with the following:
- I am trying to avoid fan sounds, drive sounds etc.
- One myth box near the TV, another in a closet on the other end of the room (quiet and has an electrical outlet).  Both connected at a gigabit.
- the box near the TV will have an HDMI video connection to the TV.  It will also have a HD-PVR setup connected to the Verizon cable box.  It will also have a wireless keyboard & mouse.  This PC will be fairly small, running a small SSD - just enough to run Mythbuntu but holds no data.
- the box in the closet will be mass storage - about 4tb of storage in either raid 5 or 10.  Otherwise this PC is headless - no monitor, etc.  I want to store all data here - DVR'd programs, DVDs etc.

Q - is this the standard frontend/backend?  It doesn't sound like it - I keep seeing references to the backend having the video inputs etc...  Which will not work with the way I am setting it up.  And since the Verizon box is on the other side of the room, it makes no sense to run the composite cables that far.

So - is it possible to set this up the way I want?  Or am I misreading the documentation?

Any help greatly appreciated before I start buying stuff,
Thanks,
Rob

---

### Post by Spr0k3t on 2010-11-03
It is possible to do what you are wanting.  I'm still working on a very oddball setup that is a tad bit different.  The primary backend can be the HTPC with a small SSD drive, and the mass storage can be mounted as an NFS/Samba/CIFS share if you want.  If the mass storage is running a Linux distribution, you can even use that as a secondary backend (only without the PVR).  Leave the HTPC up and running as well as the mass storage so you can still record shows.

What I would do in your shoes though... start with setting up two VMs on a system.  Test the theory you have to see if it all works the way you want it.  That's how I've done most of my research when setting up oddball configurations.

Seriously though, if you have any really tough questions on setting up the details... post up a reply and I'll offer advice where I can.

---

### Post by LowSky on 2010-11-04
Some things to consider. A HD-PVR uses the cable box so forget changing channels when its recording. If you need the ability to play and watch you might want another box. Yes that can be expensive. So option 2 get a tv tuner card. QAM will get all local bradcast channels like CBS, ABC, NBC,FOX, CW, and Univision. That card can go in the backend and keeps the cable box freed up unless its recording something on a cable channel like USA or MTV or whatnot.

In my experience the best thing to do is write down everything you watch regularly. If most of it is on the local broadcast stations then getting a regular tuner will work better. If you watch a lot of cable a HDPVR is a better choice, but it may annoy you if you want to watch something else. in that case consider the cable company DVR.

And to talk about noise. I'm running a combined fronted/backend  and I barely hear the PC's fans, and maybe the occasional HD click. With the TV on it less than noticable. My PS3 makes more noise and sits father away than the HTPC and I hear it all the time, the HTPC has 5 fans running and barely ever noticable with the TV on. Something to think about.

---

### Post by Mad_Professor on 2010-11-05
I have had at one time a setup similar to what you want, except it was a secondary backend, and I had tv tuners in this one and master too.

The master backend took all storage, the secondary backend would record and store locally then forward it to the master backend for permanent storage.

I remember long time ago when I first started getting into myth, that you could have a central master backend with no tuners and multiple secondary/frontends recording and sending data back to the master backend for transcoding/processing and storage.

Frankly This is what I would do....

I assume you're going to be using mythbuntu or a distro with the mythtv package installed?

If your master backend is not going to have inputs from cable/sat/net TV then set it up normally with smaba or NFS your preference and set the storage pools, guide data and anything else relevant to the master, and leave it headless, and on 24/7. It will run fine as long as you can use putty or ssh from another machine and doesn't overheat. Also enabling remote control & pin# in the master backend setup for controlling the myth backend is a PLUS.

On your very quiet frontend, set it up as a secondary backend/frontend, install the tuners in there and set it up like you normally would on a master backend, be sure to select video input and data source. Skip guide data setup, and storage pool. This should be automatic during setup when it ask's for the master backend ip. Be sure to disable this frontend for transcoding/commercial detection as that will cause your fanless cpu to over heat. Also if you're going to be doing HD recordings you might want to keep the tuners to 1-2 per secondary/frontends as this will cause problems due to software encoding of video streams which it relie on the cpu, UNLESS you get hardware based encoders then you should be fine. 
Set up scripts for IR blaster or LIRC or serial interface it with SET-TOP Boxes so it can change channels.

BTW: This machine  has to remain on 24/7 inorder to record.

I can't think of anything else, so take it for a test run.

Experiment with it on currently owned or older hardware, unless you already have the hardware then just experiment.

HTH
~MP

---

