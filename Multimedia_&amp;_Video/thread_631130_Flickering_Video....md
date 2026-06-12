---
title: "Flickering Video..."
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by Mattaus on 2007-12-04
Hi all,

Firstly apologies if this has been posted else where. I must admit I have seen a few posts here and there regarding video flickering issues but none seem to address my problem.

Whenever I play a video, whether it be in Movie Player or VLC Player, the video flickers badly. Just in the player, not my monitor itself, everything else is fine, just the screen of the video player itself.

I have no idea what is wrong or how to fix it. I'm using a ATI 2900XT Video card and after much screwing around got that working fine complete with all the whiz-bang compiz effects. So my initial thought of it been a driver problem seems wrong...or is it? I'm also using the 64-bit version of Gutsy.

Any help anyone could provide me with would be great and very much appreciated. 

Thanks.

---

### Post by harold4 on 2007-12-04
I'm assuming the flickering only occurs when compiz is running.

This is how I fixed flickering with my NVidia card.  While not an answer, it might point you in the right direction.

I added the following to file /etc/modprobe.d/nvidia-kernel-nkc
```
options nvidia_new NVreg_Mobile=1 NVreg_RegistryDwords="PerfLevelSrc=0x2222"
```

Double check that the compiz video playback plugin is enabled.

---

### Post by Mattaus on 2007-12-04
Hmm, can;t remember having tried it without compiz running, but seen as I use compiz all the time it dosn't really matter though it might help verify the problem. 

Im not on my Ubuntu PC at the moment but i'll use the info you've given me to try and find something for the ATI side of things.

Thanks for your help.

---

### Post by TheLions on 2007-12-10
i have same problem:

while compiz is running video is flickering, but when disabled, it dosen't flicker!

(i have ati x1300 and video playback turned on)

any solutions?

---

### Post by erginemr on 2007-12-11
Hi there,

I am not sure if yours is the same, but the following thread discusses such a problem and puts forward a solution:

[http://ubuntuforums.org/showthread.php?t=624498](http://ubuntuforums.org/showthread.php?t=624498)

---

### Post by danmeyer on 2008-03-13
I am still having this flickering video problem with compiz running.
I noticed that flash video inside firefox has no problem like this. 
I am also using an ATI card with the most current proprietary driver.
What settings should I be looking to change? vsync? I saw on the link to the help with an nvidia card someone had a fix that had to do with a texture setting instead of overlay or something?

Thanks dudes.

---

### Post by erginemr on 2008-03-13
I believe adding the line:
```
    Option         "XvmcUsesTextures" "True"
```
to the Section "Screen" in your xorg.conf file is worth a try and may work for ati drivers, too. But you should first back up your current xorg.conf file. 

So the steps are:
1. First back up:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
```

2. Edit the X config file:
```
gksudo gedit /etc/X11/xorg.conf
```

3. Add the above line inside the section screen:
```
Section "Screen"
    ...
    Option         "XvmcUsesTextures" "True"
    ...
EndSection
```
Save the file and exit.

4. Change to a virtual terminal with: Ctrl+Alt+F1-6 and issue the following commands to restart gdm:
```
sudo /etc/init.d/gdm stop
```
```
sudo /etc/init.d/gdm start
```

Good Luck.

---

### Post by Spoken on 2008-03-13
i would suggest trying it without compiz running, then see what happens.

---

### Post by Job_314 on 2008-03-14
For anyone with an ATi card still suffering from this problem, I've solved it. Follow the instructions in [this thread](http://ubuntuforums.org/showthread.php?t=723860).

-Austin

---

### Post by jameskeagie on 2008-04-14
This broke my compiz installation.  

What ended up working for me is the following step by step instructions.  If other things haven't worked for you you might try it - its pretty simple to try.

[http://ubuntuforums.org/showthread.php?t=754712](http://ubuntuforums.org/showthread.php?t=754712)

---

