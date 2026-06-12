---
title: "No sound in Vaio VPCEB24EN"
date: 2010-08-17
forum: Multimedia Software
---

### Post by SaswataDutta on 2010-08-17
I recently installed Ubuntu 10.04 in my Sony VAIO VPCEB24EN laptop, everything is working just fine except there is no sound.

---

### Post by tarunks21 on 2010-09-04
Hi Saswata, I also had the same problem with the same laptop model. Here is the a solution that worked for me...

[B]sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update[/B]
(Now use the output of 'uname -r' in the next command below. Form me it was '***2.6.32-24-generi**c*'. I guess that it would be the same for you as you laptop is the same as I have.)
**sudo apt-get install linux-alsa-driver-modules-*2.6.32-24-generic***

I expect that should solve the problem for you. 
If it doesn't then you may have to do the following as well.
[B]sudo apt-get install gnome-alsamixer
gnome-alsamixer[/B]
The second command will open graphic window for alsamixer where you may have to unmute some of the muted options.  But I guess it won't be required. 

Hope that helps

---

