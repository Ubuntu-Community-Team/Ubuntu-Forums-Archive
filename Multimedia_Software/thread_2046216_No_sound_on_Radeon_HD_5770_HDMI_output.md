---
title: "No sound on Radeon HD 5770 HDMI output"
date: 2012-08-22
forum: Multimedia Software
---

### Post by macin42 on 2012-08-22
I installed Ubuntu 12.04 and the onboard sound works. I installed the proprietary AMD drivers for the Radeon card and "aplay -l" seems to list the card:

```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC898 Analog [ALC898 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC898 Digital [ALC898 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I can also select the appropriate output in System Settings > Sound. The alsamixer also reports the card to be unmuted. However, there is no sound...

For further informations see the ALSA information script upload: [http://www.alsa-project.org/db/?f=f6be227cf1708f0ec2f6b23e13b758f7abaf6c7d](http://www.alsa-project.org/db/?f=f6be227cf1708f0ec2f6b23e13b758f7abaf6c7d)

Any ideas what I can try?

Regards,
Tobias

---

### Post by macin42 on 2012-08-24
*bump*

---

### Post by Newlinuxlove on 2012-08-24
I am by all means, no Linux pro, but i figured since i am in the same catagory in question i would respond with what i have tried. Here is what i have tried that doesnt work for me but might work for you that did for others. 
 
   Change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"           GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"  
You do this by opening a terminal and typing 
gksudo gedit /etc/default/grub 
It will pull up an editable file, search for the line and change it.
Make sure you close then open your terminal again and type sudo update-grub
some say to do update-grub2 also
Supposedly the HDMI isnt default audio because there are issues with
black screens with some video cards in the new 12.04 build.


This didnt help me at all. Try it thought in a terminal.
        pact set-card-profile 0 output:hdmi-surround         
Failure: no such entity

 Sound Settings: Right click speaker > sound settings > Output Tab 
        Digital Output (S/PDIF) Built in Audio 
        Speakers Built in Audio 
        Only 2 settings i get
Right click the speaker, sound settings then right click the blank area below to unhide devices if none of the above works. If nothing i posted works im sorry i tried. I have the same problem i cant get sound to work through HDMI.

---

### Post by macin42 on 2012-08-27
@Newlinuxlove: Thanks for your reply and thanks for trying to help!

> Change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"           GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"  This seems to apply only to the open source driver not to the proprietary one from AMD.

> pact set-card-profile 0 output:hdmi-surroundUnfortunately this broke my pulseaudio daemon by probably sending the onboard Audio to my onboard HDMI output (which is not connected). Since I didn't know how to reset it I cleared all pulseaudio user settings:

```
killall pulseaudio && rm -rf ~/.pulse/
```What finally did the trick was installing fglrx instead of fglrx-updates. Ubuntu comes with two versions of the AMD proprietary driver: The AMD driver release at the time of the release of Ubuntu (fglrx) and the latest AMD driver release (fglrx-updates). See [http://askubuntu.com/questions/66707/differences-between-the-2-fglrx-graphics-drivers](http://askubuntu.com/questions/66707/differences-between-the-2-fglrx-graphics-drivers). Originally I installed the fglrx-updates package but now I switched to fglrx:

```
apt-get install fglrx
```After a reboot and selecting the correct output in "System Settings > Sound > Output" everything worked like a charm. Let's see whether it stays that way...

---

### Post by Zvezdica27 on 2012-08-28
hi, 

if you can see the output in the sound control center and if opensource drivers work, then it's most likely a driver issue. try older / dev drivers. Try finding an ATI app for sound if it help. You sure both alsa and pulseaudio have it all unmuted?

just for the sake of it, try:

sudo alsa force-reload 

no more ideas,

zz

---

