---
title: "ATI HD5770 Karmic (Myth 9.10) How I got res to stick Catylyst 10.1"
date: 2010-02-14
forum: Multimedia Software
---

### Post by rodercot on 2010-02-14
Hey All,

 So I had to go out and get an ATI card just to hurt myself some more actually I was bored. I have been at this since last night at 7pm. I had a GT-220 in the test machine hooked to a Asus VH242H monitor. Finally I decided a clean install would be best as I could not get aplay -l to see the ati card as an audio device no matter what.

 I had already installed the deps for ATI. one of the libs is depracted and you need to create symlink to it. These are the deps I used

 **sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms libQtGui4 **
 
 Here are the details from the Jaunty install page - not sure if it is still req'd but I did it anyhow. 

 **NB in 9.10 (Karmic Koala) libstdc++5 has been superseded by libstdc++6. In some cases, libstdc++5 is still needed; however there is a workaround to this by symlinking libstdc++5 to libstdc++6. ** 

 and the link is 
 
 **sudo ln -s /usr/lib/libstdc++.so.5 /lib/libstdc++.so.6** 

 New install mythbuntu 9.10 installed all updates and catylyst 10.1 drivers via .run no packaging. 

 everytime I set the res it would reboot and default to 30Hz 1080i and would not scale. Finally after several hours what I did was open a terminal and launch catylyst with sudo from the command line.

 Then I went to DTV1 under display manager under pixel format I changed to 4:4:4 full RGB and clicked apply. Then under adjustments I checked the radio box for Use graphics processor for scaling and then I slid the scale slider ALL the way to the right.
 
 Then under the HDTV tab in the top box I enabled 1080p 60Hz and in the lower box I clicked on 1080p60 Standard and clicked apply format it should blank the screen and change the res and then tell you need to restart to apply, just to be safe in the lower box I clicked on 1080p60 Standard again hit add and chose OK as is. Then it will tell you to hit apply I did; then I selected 1080p60 Standard one more time and hit apply format again it applied the res and told me to reboot to apply changes so I hit OK closed CCC and rebooted and voila FULL SCREEN 1080p 60Hz instead of 1080i 30Hz.
 
 I played with the monitor settings quite a bit to get what I wanted I find all the modes from ASAU with Splendid ARE very very bright and the sharpness is set WAY TOO HIGH. Now I have perfect text no blurr at all. 

 Now on to HDMI audio. The card was detected by default on the new install. aplay -l list it as card 1. So I upgraded also to 1.0.22.1 via the script -d, -c -i and then rebooted ran alsamixer and hit f6 and I have a new card listed there with a single spdif channel which I hit "M" to unmute. 
 
 NOw to setup mythfrontend and test, I will report back with the results.

 to be continued...

 Rgds,

 Dave

---

