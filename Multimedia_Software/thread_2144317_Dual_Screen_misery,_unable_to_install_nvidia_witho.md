---
title: "Dual Screen misery, unable to install nvidia without crashing unity and turning machi"
date: 2013-05-11
forum: Multimedia Software
---

### Post by cpokane on 2013-05-11
I am currently on Ubuntu 12.10 and have tried and FAILED to install a  graphics card to run a dual screen.  I am currently running the  following graphics card,  Intel Mobile Series 4.  The machine is a Dell.  It's also a 32 bit machine.

I have tried everything to get nvidia (or any other graphics card AMD) on  this machine, but to no avail.  

Everytime I follow some of the advice,  unity shuts down and turns the computer into a brick - and I have to  re-install Ubuntu from scratch.

The following was the latest example I followed, [http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal/](http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal/)
 
I am disappointed with Ubuntu for not pre-installing these drives in the  first place.  Wasted time in my opinion, trying to get a dual screen  working.

What I need to know?

- Am i better off upgrading to 13.04?
- Is the Intel Graphics processor not going to work with nvidia?

Is there anyone out there who resolved this situation with a machine  with similar spec?  I am begging Ubuntu to sort this out.  My time could  be better spent learning command line, and doing more productive  things.  Any help would be gratefully accepted.

UPDATE:  

I folowed the advice of nvidia installation was taken from here, [http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal/](http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal/)

This part is fine

| sudo su
| apt-get update
| apt-get install linux-headers-generic
| apt-get dist-upgrade
| reboot

The part where it goes wrong...

| sudo su
| apt-get install nvidia-current-updates
| nvidia-xconfig
| reboot

Once this has been done and I reboot, there is just brick - no unity just login into truncated home screen with black colouring at the side.

Is there a potential conflict between Intel grpahics cards and nvidia drives.  I also must stree that the method set out by Mr Falkfinge is for 64-bit machine, I am running a 32-bit.

Again any help would be gratefully accepted.

---

