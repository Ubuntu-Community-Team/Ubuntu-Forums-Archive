---
title: "Steps for HVR 1600"
date: 2009-03-04
forum: Mythbuntu
---

### Post by Hackit on 2009-03-04
Hi all,

I have been asking a lot of questions and have not added anything that might help someone else. I feel like a bum.

So here goes, I was able to get my HVR 1600 working with these steps, it was very easy and this most likely why no one has asked. But just in case this is what I did.

```

Hi all I was able to get it working following this link and these steps.

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

You can get the latest snapshot of the driver from
[http://www.linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://www.linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)

Extract that file and instead of doing 1b in the link above, do the following.

cd v4l-dvb-e876c1b66fd8 (or whatever the directory that was created 
when you extracted the the file)
make
sudo make install
sudo /etc/init.d/mythtv-backend stop
sudo make unload
sudo modprobe cx18
sudo /etc/init.d/mythtv-backend start

You can skip step 2 in the link above because the firmware will already be installed.

Make sure that you,
sudo apt-get install ivtv-utils
You'll need it to change the channels.

Continue from step 3.
One thing that might not be obvious is the external channel change command.

Set it to "ivtv-tune -c". I needed it to change the channels.
( I did not have to follow this part, your mileage may vary).

```

---

### Post by boof1988 on 2009-03-04
@ Hackit,

Thanks for posting your method.

I appreciate that you included the command to stop the backend.  The MythTV-Hauppauge-HVR-1600 wiki page indicates that the backend needs to be stopped (during some steps), but doesn't say how to do it.

Thanks Again

---

### Post by sneakk on 2009-03-12
i have been unable to get this going trying for a week now. i have a cable box comcast, do i plug this int the hvr 1600 tv coax or the atsc coax??

when i go to add card mythtv i can never get mpeg to show it always states not probed??? any help appreciated, also i am new to linux so if you can give me instructions like you are talking to a kid

---

### Post by boof1988 on 2009-03-12
> **sneakk said:**
> i have been unable to get this going trying for a week now. i have a cable box comcast, do i plug this int the hvr 1600 tv coax or the atsc coax??

My HVR-1600 has 3 inputs (fm, tv & ant).  If you are going to use the cable box to do the "tuning", I think you want to plug it into the tv input.

My (WOW-Cable) service provides clear (basic) cable so I just plugged the cable line into HVR's tv input and picked up the *clear* channels by scanning.

I believe the atsc (labelled as "ant" on my HVR) is used for the over-the-air digital (HD?) channels.

> **sneakk said:**
> when i go to add card mythtv i can never get mpeg to show it always states not probed??? any help appreciated, also i am new to linux so if you can give me instructions like you are talking to a kid

IIRC... I had to input a name for the MPEG2 then Tab to the next block (the tuner's probed info would then show up) for it to show the proper (any) information.  I found out this trick on some website but I can't remember where.

Hope this helps a little and maybe someone more knowledgeable will chime in and either confirm or correct this info.

---

### Post by sneakk on 2009-03-12
THANK YOU i got to recognize mpeg just as you explained, know i can see tv but no color and grainy with a ton of dropped frames(not really watchable but atleast i am seeing something).... any help to fix thiss thank you again

---

### Post by boof1988 on 2009-03-16
> **sneakk said:**
> THANK YOU i got to recognize mpeg just as you explained, know i can see tv but no color and grainy with a ton of dropped frames(not really watchable but atleast i am seeing something).... any help to fix thiss thank you again

Sorry I don't have any ideas on how to fix this.  Hopefully someone else can help with this next problem.

---

