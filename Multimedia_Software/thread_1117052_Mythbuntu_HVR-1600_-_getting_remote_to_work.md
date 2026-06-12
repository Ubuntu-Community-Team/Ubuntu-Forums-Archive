---
title: "Mythbuntu HVR-1600 - getting remote to work"
date: 2009-04-05
forum: Multimedia Software
---

### Post by rpalmer on 2009-04-05
There is no option for the HVR-1600 in the infrared devices section in the Mythbuntu Control Centre.  How do I get this to work?

I am using Mythbuntu 9.04 beta.

---

### Post by milpool on 2009-04-13
Any luck on getting the remote to work?

---

### Post by rpalmer on 2009-04-14
Yes I did actually.  

The MythTV wiki was helpful.
[http://www.mythtv.org/wiki/PVR150_Remote](http://www.mythtv.org/wiki/PVR150_Remote)

I didn't do what it said to do in the first 7 lines because I think when you install the MythTV modules via synaptic it takes care of this for you.  The part where it talks about the following did help though:
  
-running modprobe and dmesg helped me confirm my hardware was installed correctly.
-running cat /dev/lirc0 helped me confirm that the reciever was actually receiving signals from my remote

then....

If you look in the the lircd.conf file it references another config file at /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge.

I am not sure if this is recommended, but I commented that line out and put the codes right in the lircd.conf file.  

I found out WHICH codes to put in the lircd.conf file by running the following command:

sudo mode2 -d /dev/lirc0 --raw 

*NOTE: In the wiki it talks about running the IRW command to test the remote...the IRW command would NOT work at first because it by default looks for the codes in the lircd.conf file - they were not directly in that file because lircd.conf was referencing another file so I had to use the mode2 command instead*

I pushed every button on the remote and compared the output to the commands shown in the lircd.conf.hauppauge file (so I would be able to tell EXACTLY which remote I needed to pluck out of that file, and copied only what i needed to the lircd.conf file.

It started working after I did this.

Hopefully this helps point you in the right direction.

---

### Post by dapcham on 2009-04-23
> **rpalmer said:**
> Yes I did actually.  

The MythTV wiki was helpful.
[http://www.mythtv.org/wiki/PVR150_Remote](http://www.mythtv.org/wiki/PVR150_Remote)

I didn't do what it said to do in the first 7 lines because I think when you install the MythTV modules via synaptic it takes care of this for you.  The part where it talks about the following did help though:
  
-running modprobe and dmesg helped me confirm my hardware was installed correctly.
-running cat /dev/lirc0 helped me confirm that the reciever was actually receiving signals from my remote

then....

If you look in the the lircd.conf file it references another config file at /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge.

I am not sure if this is recommended, but I commented that line out and put the codes right in the lircd.conf file.  

I found out WHICH codes to put in the lircd.conf file by running the following command:

sudo mode2 -d /dev/lirc0 --raw 

*NOTE: In the wiki it talks about running the IRW command to test the remote...the IRW command would NOT work at first because it by default looks for the codes in the lircd.conf file - they were not directly in that file because lircd.conf was referencing another file so I had to use the mode2 command instead*

I pushed every button on the remote and compared the output to the commands shown in the lircd.conf.hauppauge file (so I would be able to tell EXACTLY which remote I needed to pluck out of that file, and copied only what i needed to the lircd.conf file.

It started working after I did this.

Hopefully this helps point you in the right direction.

Thanks rpalmer.  I tried your method last night and got my HVR-1600 remote to work on Mythbuntu.  Turns out my remote is compatible w/ the HVR-350 remote.  Again, thanks again.  You're a genius.

---

### Post by bnhrobotics on 2010-03-24
Does your remote still work? I hear that they don't work with newer kernels. I cant get a lirc device to show up in /dev. Not sure if I broke the IR connector going into the card, or if its software. It was a tight fit and I heard a pop. Had to wedge the connector in because it was partially obscured by the computer case. I hope to be able to get my hvr-1600 remote working too, but I'd like to know that its still doable before I waste a bunch of time. Thanks

---

