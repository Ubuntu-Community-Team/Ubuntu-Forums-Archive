---
title: "???no Dvd Video???"
date: 2008-05-26
forum: Multimedia Software
---

### Post by slicemaster on 2008-05-26
well,
i am really new to linux and have really enjoyed all the cool fun stuff that can be done with it, such as 3d desktop and all that. but i have been sorely disapointed recently when i tried to watch a DVD. the bottom line is it is not possible. or atleast it is severily broken in 8.04 and does not function. i have downloaded all the packages that i should need but that doesnt change the fact that it still does not work. i have read alot of forum posts about other people having the same problems but that doesnt change the fact that i am really new and cant really follow what the recomend in the forum. so could you please help me.

thanks,

p.s. isnt it kind of sad that a simple feature that everyone needs and uses is non functional, wht has this issue not been fixed?

---

### Post by masonfoley on 2008-05-26
> **slicemaster said:**
> i am really new and cant really follow what the recomend in the forum. so could you please help me.

That's a bit self-contradictory no?  

Not sure what you are expecting if you aren't able to try out suggestions that are made here in the forums.

---

### Post by otchie1 on 2008-05-26
> **slicemaster said:**
> 
p.s. isnt it kind of sad that a simple feature that everyone needs and uses is non functional, wht has this issue not been fixed?

Sadder by far the inability to use a search function or follow simple instructions.

1. Open a terminal window.

2. Execute the following terminal command to install the necessary packages (make sure to approve any prompts):
sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3

3. Execute the following terminal command:
sudo /usr/share/doc/libdvdread3/install-css.sh

After you have executed the above terminal commands, insert a DVD into your drive. Totem will open and the movie will begin playing.

Thanks to [Tech-recipes]("http://www.tech-recipes.com/rx/2765/ubuntu_enable_dvd_playback").

---

### Post by slicemaster on 2008-05-26
> **otchie1 said:**
> Sadder by far the inability to use a search function or follow simple instructions.

1. Open a terminal window.

2. Execute the following terminal command to install the necessary packages (make sure to approve any prompts):
sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3

3. Execute the following terminal command:
sudo /usr/share/doc/libdvdread3/install-css.sh

After you have executed the above terminal commands, insert a DVD into your drive. Totem will open and the movie will begin playing.

Thanks to [Tech-recipes]("http://www.tech-recipes.com/rx/2765/ubuntu_enable_dvd_playback").
step 3 isnt working...
it says this

Install debhelper and fakeroot, then run this script again

how do i install those

---

### Post by slicemaster on 2008-05-26
> **masonfoley said:**
> That's a bit self-contradictory no?  

Not sure what you are expecting if you aren't able to try out suggestions that are made here in the forums.
actualy is not so if you arent willing to help dont bother posting spam.

---

### Post by digish778 on 2008-05-27
You can install lidvdread through Synaptic. Please dont forget to install win32codec pack.

there is this package libdvdcss which might be required. You can install Mplayer, Kplayer and Kaffeine. Once of which will hepl you in watching DVD.

Rest is your luck.

---

