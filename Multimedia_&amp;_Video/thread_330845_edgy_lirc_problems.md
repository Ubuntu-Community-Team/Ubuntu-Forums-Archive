---
title: "edgy lirc problems"
date: 2007-01-03
forum: Multimedia &amp; Video
---

### Post by Panhead Bill on 2007-01-03
I read on the boards that a good guide to install MYTHTV on edgy was [http://parker1.co.uk/mythtv_ubuntu2.php](http://parker1.co.uk/mythtv_ubuntu2.php). 

 Well after using that and a few other how-to instructions to fill in the differences in our setups I have basic record playback and scheduling functions.  (I'm in the u.s. and use HPG 150 and 350 cards with zap2it for channel listings vs. his system in the U.K. with HPG nova-t cards )  

Now the challenge is to get the remote functional.  parker1's guide said to check that the kernel recognises the remote by first running: cat /proc/bus/input/devices and looking for entries that refer to the remote and list what inputdevice therremote is using by the event  line.

My setup does not give an entry for IR, just keyboard, mouse and pc speaker.

I know that lirc-0.8.0-5ubuntu2 is loaded, synaptic indicates that it is already in my system.

So what do I try next?

---

### Post by superm1 on 2007-01-05
> **Panhead Bill said:**
> I read on the boards that a good guide to install MYTHTV on edgy was [http://parker1.co.uk/mythtv_ubuntu2.php](http://parker1.co.uk/mythtv_ubuntu2.php). 

 Well after using that and a few other how-to instructions to fill in the differences in our setups I have basic record playback and scheduling functions.  (I'm in the u.s. and use HPG 150 and 350 cards with zap2it for channel listings vs. his system in the U.K. with HPG nova-t cards )  

Now the challenge is to get the remote functional.  parker1's guide said to check that the kernel recognises the remote by first running: cat /proc/bus/input/devices and looking for entries that refer to the remote and list what inputdevice therremote is using by the event  line.

My setup does not give an entry for IR, just keyboard, mouse and pc speaker.

I know that lirc-0.8.0-5ubuntu2 is loaded, synaptic indicates that it is already in my system.

So what do I try next?

Hi,

Unfortunately, this guide doesn't point out that remote setup only works for a particular kind of remote.  Now which remote are you planning on using?  The one that came with the pvr-350?
If this is the case, you will need to set it up to use i2c drivers,
Follow the lirc setup below for some information about how to configure lirc and such.  Be sure to read the note about the i2c bug in the ubuntu packages.  You will need to install the third party repository listed at the bottom to get around it. [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

---

### Post by Panhead Bill on 2007-01-20
I started by reading your how-to and it led me to hexicon's how-to.  In testing the remote things work properly, but after restart the remote isn't automatically recognized.

  I tried the test to determine if lirc_common was causing problems but my result wasn't either of the two described; after killall lirc, *there was no response to the remote*.  This eliminated the entire step nine since it did not match the first result, but since *there was no response to the remote* the second result was also false, (anything in the terminal screen).

At that point I rebooted and hoped for the best, but no joy.

So do I try disabling lirc_common, or remove everything and try again?
(how would I remove all of the changes?) 

It seems that I am 90% there, but am missing something that fires up lirc_i2c.

---

### Post by Panhead Bill on 2007-02-06
Fixed it.

I used superm1's how-to and somehow got it right this time...  Whew!!!

---

