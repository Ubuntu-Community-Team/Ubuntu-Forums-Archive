---
title: "XBMC in Lucid"
date: 2010-05-02
forum: Multimedia Software
---

### Post by gtaluvit on 2010-05-02
I just started my upgrades to Lucid for my 3 boxes and started with my XBMC box which is an Acer Aspire Revo. I hit a few snags so I figured I'd start a thread for a one stop shop for current XBMC issues with Lucid since a number of people seem to be having them. First, lets start with install.

The old PPA for XBMC does not have a Lucid version of XBMC. To install it, run:

```
sudo add-apt-repository ppa:team-xbmc-svn/ppa
```
That will allow install of XBMC.

The next issue I had was video. The Revo has an ION nVidia card which should have VDPAU acceleration but all of my video was choppy. In order to get VDPAU, you'll need to install libvdpau1.

```
sudo apt-get install libvdpau1
```

Video should fly now. Finally, audio over HDMI. I currently have the HDMI going into a television, so standard audio is fine. Under System -> Preferences -> Sound and the Hardware tab, I had to change Profile to Digital Stereo (HDMI) Output + Analog Stereo Input. This gave me the menu sounds in XBMC as well as movie audio. If you intend to do passthrough, you'll need to go into XBMC and switch from Analog to Digital audio and HDMI output. This consistently failed for me. On the XBMC forums a solution was to add your user to the audio group. This didn't work for me but just a tip in case it does for you. 

Finally, the movie scraper doesn't seem to be working ATM for images. (Now working)

---

### Post by Flash__Gordon on 2010-05-04
Thanks, this was very helpful and clear. :D

---

### Post by N.Simpson on 2010-05-09
> **gtaluvit said:**
> 
Finally, the movie scraper doesn't seem to be working ATM for images. (Now working)

Did you have to do anything to get the scrapers working? I'm still having issues getting mine to run.

---

### Post by InkyDinky on 2010-05-10
I was having issues as well after upgrading from 9.10 to 10.04 on my Acer Aspire Revo. I'm not exactly sure what the culprit was, but I imagine some things were disabled or removed (libvdpau) during the upgrade process. I just followed the instructions found here :
 [http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step]("http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step") to install xbmc again.  I'm not sure I needed to do this but figured the worst that could happen would be that I'd have an upgraded xbmc. This did upgrade xbmc from the karmic to the lucid version. This was done by issuing these commands:

sudo add-apt-repository ppa:team-xbmc
sudo apt-get update
sudo apt-get install xbmc xbmc-standalone
sudo apt-get update

Things still weren't working as it appeared that vdpau wasn't enabled. This was corrected by issuing this command:

sudo apt-get install libvdpau1

Then all was back and working the way I wanted them too!

---

### Post by N.Simpson on 2010-05-10
> **N.Simpson said:**
> Did you have to do anything to get the scrapers working? I'm still having issues getting mine to run.

I just set them to rerun at the directory level and that started them working again.

---

### Post by jdmpike on 2010-05-15
I have just upgraded to lucid and cannot get vdpau acceleration working.

I have installed the following packages:
[LIST]
[*]xbmc and xbmc-standalone from team xbmc ppa
[*]nvidia-current from lucid repo
[*]libvdpau1 from lucid repo
[/LIST]

vdpau works great in Movie Player, etc - just not in xbmc...

Any recommendations?

Thanks!

---

### Post by jdmpike on 2010-05-16
So after some tinkering, I used Jocky to install the nvidia 173 driver, and video seemed to be accelerated in xbmc.

With both drivers, xbmc realized it should be using VDPAU for rendering, it was just not performing well at all with the nvidia-current package from the lucid repo.

Could it be there was a conflict with nvidia-current, libvdpau1 and my 8200?

I would like to be able to debug this further, as the performance I am getting with the 173 driver isn't as good as it was with the 185 driver I used in 9.10. Can anyone make recommendations on where I can look?

Thanks!

---

