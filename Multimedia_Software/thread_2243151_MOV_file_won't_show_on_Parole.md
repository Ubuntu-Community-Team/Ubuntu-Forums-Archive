---
title: "MOV file won't show on Parole"
date: 2014-09-06
forum: Multimedia Software
---

### Post by ross4 on 2014-09-06
I'm running Xubuntu 14.04 and want to watch a .MOV file. When I try to open it with Parole, I get the message:
GStreamer backend error
Could not initialise Xv output


Can anyone tell me what's happening here and how I can fix it?

My system:
Toshiba Satellite P100 Laptop
Intel Core2 CPU
T5500 @ 1.66 GHz
1.67 GHz, 2.00 GB of RAM
HD: 63 GB for XP, 47 GB for Linux 
Video Card: NVIDIA GeForce Go 7600

---

### Post by Vladlenin5000 on 2014-09-06
A proprietary codec is needed and you probably don't have it installed yet -> Due to licensing restrictions Ubuntu cannot ship with certain proprietary codecs.

Try installing the *ubuntu-restricted-extras* (or equivalent for your specific Ubuntu flavor). Read here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by ross4 on 2014-09-07
Well, my attempt at installing the restricted formats was a minor disaster. My fault, I guess. Tried it from the command line and when the EULA notice came up, nothing seemed be happening (couldn't remove it) so eventually  I had to leave and so shut the machine off. I guess now I have bits and pieces of that package on the machine as I can't seem to install or purge cleanly. Well, I got mplayer working so I'll just put this on hold for now. Unless someone can tell me how remove all the bits and pieces cleanly so I can try again (or not).

---

### Post by Vladlenin5000 on 2014-09-07
You need to accept that license and to do so you need to press TAB and use the cursor keys to move to and select the proper option then ENTER to confirm it...

Now you have a problem with the packages due to the unfinished installation but it's easily solved.

1. First we need to remove any traces of the *ttf-mscorefonts-installer*:
```
sudo apt-get remove --purge ttf-mscorefonts-installer
```

2. Then reinstall and this time make sure you do all the steps needed to accept the M$ EULA:
```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by ross4 on 2014-09-07
Ok, I followed your instructions and I think the whole package was installed correctly. Parole still doesn't work: It won't show my MOV file or run a dvd. After a little more search (I did some before posting), I think there is a bug in the program. In particular, my google search "parole could not initialise xv output" seems to indicate this. Since I am a newbie, I can't successfully follow up these leads. 
Thanks very much for you help. 
Regards,
Ross

---

### Post by Vladlenin5000 on 2014-09-07
Any other player including the one already installed should now be able to open and play any file you trow at it. 
For DVDs there's one step more you need but that's explained in the same restricted formats link I post above. The reason why it doesn't work OOTB is the same.

---

### Post by mc4man on 2014-09-07
run this command, then try parole again. If still no go try another video or try another player like vlc
```
parole --xv false
```

---

### Post by ross4 on 2014-09-07
That last bit of code fixed the problem. Thanks to both of you for you help.
Regards,
Ross

---

