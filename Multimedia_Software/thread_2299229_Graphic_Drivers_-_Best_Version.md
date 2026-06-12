---
title: "Graphic Drivers - Best Version"
date: 2015-10-16
forum: Multimedia Software
---

### Post by bman on 2015-10-16
Hi,

Running Ubuntu Gnome 15.04 and wondering if I have the best graphics available.

All I did was go into Additional Drivers and choose the Nvidia option (there are two but are the same). Currently says 346.96.

Is there a better driver, how would I upgrade?

---

### Post by bman on 2015-10-16
**bump? Anyone..

---

### Post by efflandt on 2015-10-16
It depends what graphics card/chip you have and whether a newer driver would do anything different or might no longer support an older card.

The graphics-drivers/ppa has nvidia352 or nvidia-355 packages: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

### Post by bman on 2015-10-16
I have a 980TI card.

How would I add that PPA exactly, and can I add it just on top of what I have done already without issues?

---

### Post by Bucky Ball on 2015-10-17
*Thread moved to **Multimedia Software**.*

---

### Post by mc4man on 2015-10-17
> **bman said:**
> I have a 980TI card.

How would I add that PPA exactly, and can I add it just on top of what I have done already without issues?

```
sudo add-apt-repository ppa:graphics-drivers/ppa && sudo apt-get update
```

Then, if not already, install synaptic. Open it up,  click on the Origins tab, find the ppa, click on the listing for it.
Find the latest  driver, currently 355, mark & install it. Your current driver will be removed as part of the install.
(- newer Nvidia  drivers are not seen as upgrades, you have to manually install as above so check for newer versions from time to time. 
While you're at it upgrade libvdpau & nvidia-settings.

---

### Post by bman on 2015-10-17
Which is the driver in Synaptic?

The only one that might seem like it is libcuda1-355 which shows 355.11 being the latest, even though there are some files installed that say 358.09.

Actually most of the files listed as installed (I think) are saying there are updates to them.

---

### Post by mc4man on 2015-10-17
> **bman said:**
> Which is the driver in Synaptic?

The only one that might seem like it is libcuda1-355 which shows 355.11 being the latest, even though there are some files installed that say 358.09.

Actually most of the files listed as installed (I think) are saying there are updates to them.
I'm on 14.04 & 15.10 but shouldn't be much different for 15.04. See screen, example from 15.10
(- after you install from the ppa then in synaptics > Origin there will be 2 listings for a ppa, 1st. is packages installed, 2nd is all packages from that ppa for your Ubuntu release.
I wouldn't be surprised if nvidia-358 shows up shortly as nvidia-settings & libxnvctrl0 have moved to 358

When it comes time to dump 15.04 I'd  do a fresh install, if doing an upgrade from 15.04 to 15.10 better to remove the nvidia drivers & related ppa packages, reboot to check that things are ok, then do the upgrade, ect. (fresh installs are better...

---

### Post by bman on 2015-10-17
Well I got them installed.

Seems to be causing me more issues than before. VLC is basically broken when playing videos :( Sadness.

---

### Post by shantiq on 2015-10-17
> **bman said:**
> Well I got them installed.

Seems to be causing me more issues than before. VLC is basically broken when playing videos :( Sadness.

no longer the best video player it seems.   for the last year or so I always use mpv  ...   maybe try it see if you like it ..   more stable than vlc i would say and never tears  ... right-click on any video and play

V to make subs visible
J to toggle through subs
# to toggle through audio tracks
S for screenshots to home folder

i use mc's PPA
[https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)
 [https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)

```
sudo add-apt-repository ppa:mc3man/trusty-media
```     or depending on distro version
```
sudo add-apt-repository ppa:mc3man/mpv-tests
```
then  >> ```
sudo apt-get update ; sudo apt-get install mpv
```

---

### Post by Bucky Ball on 2015-10-17
> **bman said:**
> Actually most of the files listed as installed (I think) are saying there are updates to them.

In that case:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

... before going any further. This will not upgrade your OS to a newer release but will bring everything up to date so the whole system is on the 'same page', so to speak ...

---

### Post by bman on 2015-10-17
> **shantiq said:**
> no longer the best video player it seems.   for the last year or so I always use mpv  ...   maybe try it see if you like it ..   more stable than vlc i would say and never tears  ... right-click on any video and play

V to make subs visible
J to toggle through subs
# to toggle through audio tracks
S for screenshots to home folder

i use mc's PPA
[https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)
 [https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)

```
sudo add-apt-repository ppa:mc3man/trusty-media
```     or depending on distro version
```
sudo add-apt-repository ppa:mc3man/mpv-tests
```
then  >> ```
sudo apt-get update ; sudo apt-get install mpv
```

I have SMPlayer installed, is that not the same as what you refer? Does the one you talk about have a GUI?

---

### Post by bman on 2015-10-17
I installed it, and it opens a video window for mpv to play the file (from the context menu_ but it stays black, and the video never starts.

---

### Post by shantiq on 2015-10-17
> **bman said:**
> I installed it, and it opens a video window for mpv to play the file (from the context menu_ but it stays black, and the video never starts.


no it does not require a gui   you just right-click on your video and then pick mpv then it opens

see image[ATTACH=CONFIG]265008[/ATTACH]

---

### Post by mc4man on 2015-10-17
If I were you I'd dump that 15.04 install & install 15.10, either now or wait for it's release in 10 days or so. You'd get a newer kernel & mesa than what's in 15.04 & 15.04 will be end-of-life in a few months anyway.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
Some of those ppa's mentioned for mpv are just for 14.04, they aren't in any way for 15.04

---

### Post by bman on 2015-10-17
> **mc4man said:**
> If I were you I'd dump that 15.04 install & install 15.10, either now or wait for it's release in 10 days or so. You'd get a newer kernel & mesa than what's in 15.04 & 15.04 will be end-of-life in a few months anyway.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
Some of those ppa's mentioned for mpv are just for 14.04, they aren't in any way for 15.04

Interesting, I didn't know it was that soon. That being said, is Ubuntu Gnome in 10 days, or just regular Ubuntu? Though I shouldn't really need to upgrade OS to fix issues like this. Though many times it does :(

---

### Post by mc4man on 2015-10-17
> **bman said:**
> Interesting, I didn't know it was that soon. That being said, is Ubuntu Gnome in 10 days, or just regular Ubuntu? Though I shouldn't really need to upgrade OS to fix issues like this. Though many times it does :(
Both are releasing near end of Oct. Mainly suggesting because your hardware seems fairly new & could benefit from 15.10, though - 
Not too long ago a got a laptop (returned for heat issues) with a GTX 970M nvidia card, it worked ok with 14.04.3 (vivid-lts) so it's not like recent nvidia gpu's can't work in vivid or even 14.04.3 or the upcoming 14.04.4 (wily-lts

As far as mpv - 
it's mainly command line but does have a 'psuedo' gui. It also benefits from the mpv.conf file/settings & lua scripts.
The version in Ubuntu's vivid repo  is a bit dated though should have worked ok.

If you want to try a newer version in vivid then go here, read first, ect. 
[https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1](https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1)
Then for a simple test in a terminal - 
mpv /path/to/video
post results

---

### Post by bman on 2015-10-17
mpv seems to work for some videos and not others, even though they seem to be same file types/codecs. These are network files, and it seems it will load all files, but will take up to 5 minutes to do so, and if I scan through to a different part, its stopped and froze again. So clearly not doing the best job in that way. I also dislike not having any real menu options and settings. Will try a newer version if I can figure it out. Not the most important right now though.

Might as well wait to see what 15.10 brings me :)

---

