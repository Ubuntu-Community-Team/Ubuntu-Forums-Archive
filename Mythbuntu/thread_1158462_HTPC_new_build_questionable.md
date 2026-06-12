---
title: "HTPC new build questionable"
date: 2009-05-13
forum: Mythbuntu
---

### Post by dredded on 2009-05-13
Hello there, My inquiry has to do with a build I am wanting to create using specific hardware and figured I would post the specs to see if any one in the community could give me some insight. Im not entirely new to linux although I am new to trying a Media box with it. I am sick of having the restrictions to M$ when it comes to my movie and TV watching.

Here goes:
P4 2.6 800 mhz fsb HT
HP standard MOBO intel chipset came out of a d530c workstation
EVGA 6200le 128 meg w/s-video out
creative SB ct4830 w/digital audio out
I'm looking at the Hauppuage 1600 tuner card
(I don't subscribe to cable or sat so I am only interested in OTA signal)
My TV is a SONY 32" flat screen WEGA (old school I know, But the picture is amazing for its age and it serves me well, can't afford an LCD or Plasma just yet)
Stereo Receiver can accept digital or multi-chan input so as for sound I can get that figured out.
it is the use of the vid card and tuner card that makes me wonder things like how much ram would be the most suitable, if there may be any issues or conflicts to be aware of? or if someone has a suggestion for an OS or application that will suit me best.

Any help will be appreciated.

---

### Post by phroman on 2009-05-13
Generally all that stuff looks ok, but have a look at the mythbuntu recomended hardware guide here:

[http://www.mythbuntu.org/requirements](http://www.mythbuntu.org/requirements)

I always liked the rule of get as much RAM as you can afford...   :p

---

### Post by dredded on 2009-05-15
Cool-since im dealing with a DDR rig then I can use my GeiL dual channel 2gig kit @pc3200

I have already installed 8.04 on this rig to test its compatability, and so far everything works(except for the tuner card, should be receiving it soon by courier) I have a few drives around 2 160's one is ata and the other is a sata, and a sata 80gig. im leaning towards one of the 160s, what im wondering is if data transfer is gonna matter where the bus is concerned if im really gonna need to use sata or not considering im planning on making this rig a PVR setup? I guess this is what happens to folks when they have waaay too much gear lying around from generations past :). I am so pleased to be a part of this community, and I appreciate the help and welcome I have received.

Evantually I will get posted here my main gaming rig specs and I may actually be able to help others in the near future.

Thanx again,
DreaD

---

### Post by teet on 2009-05-16
I've used both PATA and SATA drives in my mythtv machines...can't really tell any difference.

Be sure to choose a good filesystem on the partition where you store your recordings.  I chose JFS (it does a good job when working with huge files) but there are several other options.

-teet

---

### Post by dredded on 2009-05-16
Here is another question, hopefully a good one.

Most of my media is stored on a 400 gig sata drive located on my main rig, sadly enough also on a load of WinXP pro.

Im wondering what headaches I may encounter loading MythBuntu on this media PC and still having access to all of these media files, Or is there an option I can workaround to get the job done effectively.

I do have a dual boot setup on this Rig, running WinXP/ Ubuntu, would I have to have it booted into Ubuntu to access these files or is there another way to have the Mythbuntu box be able to read the files on the shared drive from Win?

In addition, so far ubuntu is reading all the hardware nicely in this new media rig, digital audio and all.

Wish me luck on my cobbled mess of used pieces.

DreaD

---

### Post by tgm4883 on 2009-05-16
> **dredded said:**
> Here is another question, hopefully a good one.

Most of my media is stored on a 400 gig sata drive located on my main rig, sadly enough also on a load of WinXP pro.

Im wondering what headaches I may encounter loading MythBuntu on this media PC and still having access to all of these media files, Or is there an option I can workaround to get the job done effectively.

I do have a dual boot setup on this Rig, running WinXP/ Ubuntu, would I have to have it booted into Ubuntu to access these files or is there another way to have the Mythbuntu box be able to read the files on the shared drive from Win?

In addition, so far ubuntu is reading all the hardware nicely in this new media rig, digital audio and all.

Wish me luck on my cobbled mess of used pieces.

DreaD

You need to look into mounting samba shares

---

### Post by dredded on 2009-05-30
So far I have tested the hardware out and all seems in good working order, the downside is I had to run Install WinXP to test it all out and used the app MediaPortal. I am impressed by its functionality and ease of use (at least im using open source software right?). I have had quite alot of roadblocks and minor speedbumps with the LinuxLoad but that will not stop me, I will continue to attempt to get it working properly and hopefully flawless. Until I get all of the wrinkles ironed out I may dual boot to tinker til I get it just right. If there is any thought or suggestions on an app or alternate solution I am all ears, I can get Ubuntu running excellent, its just mythtv that gets me a bit stumped.

Where I am having the most trouble is getting the tuner card recognized and fully working, as for the media files go I have a 500gig HDD and will be using that for the whole setup. The remote seems a bit tricky too, I am leaning towards the belief that it is a Media Center Remote and not a Hauppuage although it came with the card, during the WinXP setup I found that the remote setup works as a M$ MCE remote. There is a very long post about the WinTV-HVR 1600 and I will root through it and hope I can get it working but if anyone has had luck or at least success with this card, please help.

thanks again for the help and support.

DreaD :D

---

