---
title: "Ubuntu 7.10, mythtv, backend, frontend, hauppauge pvr-500 disturbed video :("
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by petekn on 2008-01-18
Hi all,

first of all, i'm new to the linux world, so it could be that i'm making stupid mistakes... :)

anyway here we go :
i have setup a ubuntu 7.10 server on a machine with a PVR-500, on which i installed all updates, and mythtv-backend.  I did some configuration of mythtv as described in several HOWTO's (no rocket science).  The setup is able to find all my channels in the scan (but i can't verify them through the setup util).

i have on my gigabit network, another pc, on which i installed Ubuntu 7.10 workstation. here i installed the ubuntu-mythtv-frontend.

configuration is done according to the same Howto, and the connection works.  However when i start livetv, i see all kind of disturbed channels with stripes etc, allthough sound is ok...

any ideas what might be the problem/solution ?

thanks
Peter

---

### Post by curtis1552 on 2008-01-18
have you checked to see if you are recieving the correct format? PAL ASTC NSTC etc

I had selected ASTC and recieved vary garbled video until I changed it to NSTC.

---

### Post by petekn on 2008-01-19
I'm in belgium and selected plain PAL...

so i think it's ok :confused:

Pete

---

### Post by curtis1552 on 2008-01-19
I also forgot to ask are you using broadcast or cable?
 - If cable your company might be using a differnt format then you selected - hnce the garbled video; or if the cable is encrypted it will distort the video (this usually occurs if you have to use a set top box)

---

### Post by petekn on 2008-01-19
Hi,

it's cable, and before i used gbpvr in windows, which didn't give any problems... :( 

these channels are definitely not scrambled :)

P.

---

### Post by curtis1552 on 2008-01-19
The only thing I can think of is that it is a different variant of PAL;
you could try changing from PAL to PAL-M PAL-N etc. in the MythTV Backend Setup ; General section.

---

### Post by Fionns on 2008-01-24
Hi there, I've got exactly the same setup and I have the same problem. I'm in a PAL area also (Ireland).
I've got a PVR350 in the same box and it works perfectly so it's definitely an issue between ubuntu and the PVR500.
I'm looking into the firmware info on the [IVTV site ]("http://www.ivtvdriver.org/index.php/Firmware") to see if that will help.
Will post back if I manage to get it fixed.

---

### Post by petekn on 2008-02-05
been there, done that... :(
it didn't help me out, but feel free to give it a try, maybe i did something wrong...
P.

---

