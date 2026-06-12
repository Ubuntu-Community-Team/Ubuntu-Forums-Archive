---
title: "Strange problems with ATI X1300 and fglrx"
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by kstam on 2007-02-27
Good morning,
for some days now I'm facing some strange problems after installing a new graphics card. It's a GeCube X1300 512MB. I installed Ubuntu 6.1 from scratch. The driver that was installed by default was 'vesa'. Not 'ati', but anyway... Second step was to install fglrx, but before that I noticed that trying to go to console (alt, ctrl, F1) was not working... I mean it is trying to go to console but the screen shows noise with mixed multiple colors... also when ubuntu starts on the first screen with the orange bar that is getting full, after half is full it shows some minor blue noise under it...
After the driver was installed according to the unofficial ATI wiki ([http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Revert_to_Xorg_driver](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Revert_to_Xorg_driver)) I checked and everything seems to have gone fine. I made some checks and shows that all is installed well: fglrxinfo, fgl_glxgears etc...
but above mentioned problems remained.
I then proceeded to installing XGL, Beryl and MythTV and all went smoothly. XGL works ok, but I have following problems:

1. Switching to terminal still doesn't work with the same effect...
2. Beryl is not working.... I don't know why but when I try to run beryl-manager through terminal it reports AIGLX server (which is disabled from xorg.conf and XGL is running) and falls back to Metacity
3. MythTV works fine but live TV has wrong colors. As if it is set to wrong TV standard (NTSC instead of PAL), but it is not. I double checked it... I recorded something and the recorded piece had correct colors. Also I changed back to vesa driver and colors are ok. So I end up it is fglrx problem like the others...
4. TVtime is not working... when invoked from terminal gives: tvtime requires hardware YUY2 overlay support from your video card driver. ??Isn't that implemented in fglrx?? tvtime mentions something about gatos. Should I install that to??
5. XawTV gives a black screen and hangs. I have to restart the PC.

That is more or less what I'm facing and I can't find similar reports anywhere. Strange think is that fglrx seems to have been installed properly...

Also I installed yesterday night the latest version of fglrx with same exactly results...

Please anyone with some ideas on the problem help. I can provide more infos tonight when I 'll be at home
Thanks in advance

---

### Post by djrobthaman on 2007-04-03
Hi,

I also have an ATI X1300 running in my machine (not GeCube though) and could not get it to work with mythtv.  Could you tell me how you got mythtv to work with your video card? 

Thanks,
Douglas

---

### Post by hulet on 2007-05-01
> **kstam said:**
> Good morning,
for some days now I'm facing some strange problems after installing a new graphics card. It's a GeCube X1300 512MB. I installed Ubuntu 6.1 from scratch. The driver that was installed by default was 'vesa'. Not 'ati', but anyway... Second step was to install fglrx, but before that I noticed that trying to go to console (alt, ctrl, F1) was not working... I mean it is trying to go to console but the screen shows noise with mixed multiple colors... also when ubuntu starts on the first screen with the orange bar that is getting full, after half is full it shows some minor blue noise under it...
After the driver was installed according to the unofficial ATI wiki ([http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Revert_to_Xorg_driver](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Revert_to_Xorg_driver)) I checked and everything seems to have gone fine. I made some checks and shows that all is installed well: fglrxinfo, fgl_glxgears etc...
but above mentioned problems remained.
I then proceeded to installing XGL, Beryl and MythTV and all went smoothly. XGL works ok, but I have following problems:

1. Switching to terminal still doesn't work with the same effect...
2. Beryl is not working.... I don't know why but when I try to run beryl-manager through terminal it reports AIGLX server (which is disabled from xorg.conf and XGL is running) and falls back to Metacity
3. MythTV works fine but live TV has wrong colors. As if it is set to wrong TV standard (NTSC instead of PAL), but it is not. I double checked it... I recorded something and the recorded piece had correct colors. Also I changed back to vesa driver and colors are ok. So I end up it is fglrx problem like the others...
4. TVtime is not working... when invoked from terminal gives: tvtime requires hardware YUY2 overlay support from your video card driver. ??Isn't that implemented in fglrx?? tvtime mentions something about gatos. Should I install that to??
5. XawTV gives a black screen and hangs. I have to restart the PC.

That is more or less what I'm facing and I can't find similar reports anywhere. Strange think is that fglrx seems to have been installed properly...

Also I installed yesterday night the latest version of fglrx with same exactly results...

Please anyone with some ideas on the problem help. I can provide more infos tonight when I 'll be at home
Thanks in advance
I have the ATI AIW 2006 edition video card, which has the X1300 GPU but didn't encounter the problems. I installed fglrx, xgl and beryl following this guide: [http://ubuntuforums.org/showthread.php?t=399643](http://ubuntuforums.org/showthread.php?t=399643) and it has worked without a hitch.

The mythtv-with-wrong-colours problem I also got but solved that by installing a patched libmythtv package I have found somewhere.

---

### Post by hulet on 2007-05-01
> **djrobthaman said:**
> Hi,

I also have an ATI X1300 running in my machine (not GeCube though) and could not get it to work with mythtv.  Could you tell me how you got mythtv to work with your video card? 

Thanks,
Douglas

I used this guide to set up my Hauppauge PVR-150 tv tuner with my ATI AIW 2006 edition (X1300 GPU) to work with mythtv:
[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O)

What kind of TV Tuner do you have?

---

### Post by djrobthaman on 2007-06-25
Hmmm.... I have the x1300 that acts as a tv capture card.  As for tuner, I thought the x1300 was the tuner (isn't tv tuner/tv capture the same thing?)

Thanks for the link.  I'm gonna check it out and see if I can get this thing working :)

---

