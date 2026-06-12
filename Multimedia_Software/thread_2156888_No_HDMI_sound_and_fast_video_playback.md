---
title: "No HDMI sound and fast video playback"
date: 2013-06-23
forum: Multimedia Software
---

### Post by frikkieh on 2013-06-23
After several years of inactivity, I feel Ubuntu deserves another chance. 
I failed to get the Compro K100 IR remote working with the lirc package, and had to revert to Windows as an OS.
But Windows (put swear word here) right?
 
I did a fresh install of raring (13.04) and ran an update today.
The intention is to use it for a media center so XBMC was installed as well.

There are 3 issues:

1.) when runningfullHD (1920x1080) the display is chopped to the side and top. There is only half a launch bar to the left and no top bar (where the time is supposed to be).

[IMG]http://i1196.photobucket.com/albums/aa408/frikkieh/IMAG1405_zpsebd40e7f.jpg[/IMG]

1680x1050 gives me the full screen, but that is not the resolution for FHD movies?

2.) All video playback in both Ubuntu native media player and XBMC plays extremely fast. How do I change the playback speed? All roads lead to issues in Flashplayer, which has nothing to do with XBMC or the native media player (the Ubuntu application is called "videos" - it does not seem to have a real name).

3.) There is no sound. I tried HDMI and SPDIF - no sound. No volume is muted anywhere, Not even in alsamixer.

After about 3 hours of Googling around, I found no fix to any this :confused:

The graphics card is a Asus Radeon HD5450. Motherboard is Asus a8n-sli premium.

Any help would be appreciated.

---

### Post by frikkieh on 2013-06-23
I found this to work to get the HDMI audio going and the fast playback:
[http://askubuntu.com/questions/67113/fast-video-playback-with-no-sound](http://askubuntu.com/questions/67113/fast-video-playback-with-no-sound)

However after banging heads with a few rocks, I still cant get 5.1 surround, only L/R stereo.

I will try to install the proprietary Linux drivers for Radeon tomorrow to see if it will resolve the resolution problem.
Perhaps it will resolve both :)

---

### Post by trag on 2013-06-24
I just spent a full day working on a solution to this exact same problem( no problems with accelerated playback though)and I will try to be succinct and to the point.
Do not upgrade graphics drivers,Kernels etc.
In  Synaptic Package Manager install "pavucontrol".   (Pulseaudio Volume Control). 
Open Terminal type"pavucontrol" then enter. In Volume Control under OUTPUT DEVICES go to PORT: and select "HDMI/Display Port", also check boxes ( DTS,AC3,MPEG,EAC3 ).
Now open CONFIGURATION and at the first Built-in Audio selection change that Profile: to "Digital Stereo (HDMI) Output".
Change the second Profle: to  "Digital Stereo (IEC958) Output +Analog Stereo Input". No more changes here so close the window.
Install GRUB-CUSTOMIZER in terminal.
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
Open Grub customizer from the Dash.Open GENERAL SETTINGS, go to "kernel parameters" and change (quiet splash) so it now reads (quiet splash radeon.audio=1) OR (quiet splash nvidia.audio=1).Save and Exit.
Shut everything down and do a Restart. After Restart, from Unity open System Settings and then Sound, Choose HDMI/DisplayPort  and open TEST SOUND, HDMI audio should be coming from the TV, and your desktop should now fit inside the screen.

---

