---
title: "Help! Dvd in ubuntu - 'tried everything'"
date: 2009-09-04
forum: Multimedia Software
---

### Post by Zenxlow on 2009-09-04
Hey everyone, let me explain my issue. I have had ubuntu for a while, I have a pretty slow lap top but I don't use it much aside surfing the web, watching videos, writing, etc.

I just recently had problems with the updater, for a while I would get a strange cd-rom? error (couldn't retrieve something or other) so after an hour of reading forums and trying things out I upgraded my ubuntu from 8.04 to 8.10 and that seemed to finally fix the issue, now I can install/update my ubuntu with no problem.

But I still have some issues, I can't watch DVD!
I have vlc, and totem (xine), I have gstream packages and the libdvd is up to date as well as restricted extras.

I open the dvd in vlc and I get:
Errors
Playback failure:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disk.
Playback failure:
DVDRead could not read block 0.

((why is there two totems anyway? One is just movie player, movie player(xine)))
When I try the regular movie player:
Could not read source

Then I try totem (xine):
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

In synaptic I type in 'libdvd' in the search and I see I have the latest versions installed: libdvdread3 (0.9.7-11ubuntu2), libdvdnav4 (4.1.2-3), as well as the libdvdread-dev & libdvdnav-dev, but not the libdvdread/nav-dbg
(keep in mind I am not personally sure what all these are for, just been following directions of others)


I was looking around, & in administration -> software sources, under third-party software there is nothing checked off -- could this be contributing to the problem? I remember seeing many checked off before I upgraded..

If there is some specific specs or info that would help clarify my issue let me know. Im really at a loss of where to go from here. I have read through dozens of threads on multiple sites and tried advice given to others but to no avail. Can someone help me please? I am sort of a noob with ubuntu but I understand the basics.. Thank you!!!!!!!

---

### Post by khelben1979 on 2009-09-05
To having working codecs you need to add the repositories from Medibuntu. Have a look [here]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories").

Other than that I suspect that your default user is lacking the right file permissions and because of this you need to add some things to it. Look at my attached pictures.

System / Users and groups.

---

### Post by stinkinrich88 on 2009-09-06
ahhh, thank you so much khelben1979!

---

### Post by khelben1979 on 2009-09-06
You're welcome!

---

