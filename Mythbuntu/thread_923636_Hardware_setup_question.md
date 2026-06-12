---
title: "Hardware setup question"
date: 2008-09-18
forum: Mythbuntu
---

### Post by ohzopants on 2008-09-18
So I'm considering diving into the exciting (frustrating/challenging?) world of MythTV.

I'm finally getting a satellite dish hooked up on Saturday and I've opted for the HD receiver.  I could buy a PVR from the provider... but then I don't get the geeky pleasure of having to set it up :)

Anyways... I realize the the Hauppauge HD-PVR is my only option for getting the HD input from the dish to Myth (I'm going to hold out for it to be better supported, by I have faith).  Bear in mind that I'm starting from scratch here so I want to build the PC just right for this application.

If I want to buy one machine to be both backend and frontend for my setup and I'm using the HD-PVR, am I correct in understanding that all the processing of the video will be done by the HD-PVR and that the Myth box will only need to decode the video?  Can Myth handle that, or does it have to convert it to a specific format?

How would the IR blaster set up work in this case?  Would the Myth box control it and the HD-PVR would just record whatever happens to be playing?  Or will the HD-PVR driver allow for control of the IR blaster attached to the HD-PVR through Myth?

And since this thing is USB I don't need a tuner card at all, right?

Man, I hope that all makes sense.  I'm pretty confused.

---

### Post by paulg on 2008-09-18
There are some HD receivers that will send the video over firewire. If there is a broadcast flag enabled then the receiver will block this feature. It's also possible to send the change channel command over firewire. Not all receivers have firewire so your mileage will very (greatly).

The reciever will be your tuner. The HD-PVR is just a recorder, but MythTV will use the receiver, HD-PVR and blaster as one. So when it's time to record something the blaster (or firewire) will send the signal to the receiver to turn on, change to the appropriate channel and turn on the HD-PVR when it's time to the record. With only one HD-PVR and one receiver you won't be able to watch live tv and record a show as you will be restricted to one stream (same as having a single tuner card). 

All the heavy lifting is done by the HD-PVR to encode the broadcast. You should have no problem playing the files back if you're building a new computer from scratch.

---

### Post by ohzopants on 2008-09-19
Thanks for the reply.  But now I have more questions...

The receiver I'm getting has a USB port.  Does that mean it will be controllable via USB?  I checked the myth site and did some googling but couldn't find anything.

The HD-PVR is sort of a "pass-thru" device, so I would need component video inputs on the PC, correct?  Do video cards have these?  I have never seen any.

Thanks again.

---

### Post by ohzopants on 2008-09-19
More thorough googling tells me that the USB port on my receiver is a dud (although some people report successfully charging an ipod with it).

---

### Post by Malibyte on 2008-09-25
The HD-PVR takes the analog stream from the component outputs of the set-top-receiver box, encodes it to h.264 format and sends it out the USB port to the PC, which does the actual recording onto the hard disk.  It comes with an IR blaster and a remote, but you shouldn't need them, since there are several "channel changer" scripts out there for popular STBs which will change the channel via FireWire.

Myth should have HD-PVR support "real soon now".  My current Myth box is running Mandriva, but they're slow about getting package updates out the door so am thinking about switching it over to Ubuntu, which most of my other machines are running.  There was recently a Myth update for Hardy, does anyone know if it has any of the HD-PVR backend support enabled?  

I have one but am only able to record from it manually in Linux by doing a direct "cat /dev/v4l/video1 > (filename).ts".  The recordings it produces are VERY nice in 720p.  

Bob

> **ohzopants said:**
> Thanks for the reply.  But now I have more questions...

The receiver I'm getting has a USB port.  Does that mean it will be controllable via USB?  I checked the myth site and did some googling but couldn't find anything.

The HD-PVR is sort of a "pass-thru" device, so I would need component video inputs on the PC, correct?  Do video cards have these?  I have never seen any.

Thanks again.

---

### Post by ohzopants on 2008-09-26
Can you watch live tv through the usb connection?

---

