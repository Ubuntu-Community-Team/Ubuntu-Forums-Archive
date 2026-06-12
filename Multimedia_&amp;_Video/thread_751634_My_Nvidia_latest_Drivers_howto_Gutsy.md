---
title: "My Nvidia latest Drivers howto: Gutsy"
date: 2008-04-10
forum: Multimedia &amp; Video
---

### Post by taget on 2008-04-10
Hi everybody, this is my first post here just picked up ubuntu about a week ago. i absolutely love it, but more on that some other time.

the problem i keep seeing with everyone that wants to run the latest drivers on gutsy is the inability to shutdown gdm or kdm and go to init3, this was the most frustrating thing for me .

but i did find a way to do this, without editing any rc.d files to change default runlevels.

you will also need another computer that is on the same network

the first thing you need to do is un-install the restricted drivers package and any other nvidia packages that may be floating around, then install the linux-source packages relevant to your distro. 

you need to set up a SSH server, way easy.
yeah this seems kind of weird.

use this at the terminal window
```
sudo apt-get install ssh
```

now that you have all of those things done, go to your other computer.

open a ssh connection to the computer that you want to install the nvidia package on(remember where you downloaded the package) find the gdm or kdm process and kill it, i think i had to do the same to xorg. then

```
sudo telinit 3
```
then go to the directory where the nvidia package is
```
sudo ./NV*
```
after it has completed be sure to run the nvidia-xconfig

once all of this is done restart.
sorry if i missed anything, im trying to write this from memory and i might have missed a few steps. but this did work for me. please remember i am kind of new to linux, so these intructions are not going to be very good. if there is someone out there that could explain it better by all means please do so. 

questions or comments please.
thanks and hope i helped someone

---

