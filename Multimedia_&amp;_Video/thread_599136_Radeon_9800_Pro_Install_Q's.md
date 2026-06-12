---
title: "Radeon 9800 Pro Install Q's"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by TheBigBentley on 2007-11-01
Ok so I am trying my best to move away from the evil MS and have used Wubi (Im afraid of commitment) to install Ubuntu 7.04. So far Im starting to get the hang of it but im a little scared about updating my Ati drivers. Im using the default ones that load when Ubuntu is installed but feel I should be getting a lot better performance. So to make a long story short I tried enabling the restricted drivers from the administration menu a few days back. Needless to say it caused me to have to reinstall everything becuase it would just show me a black screen when X loaded. 

My question is if Im going to try out the drivers from ATi's website what are the steps and procedures if any to revert back to the original drivers if I screw this up and cant get back into X?

Im not well versed with the terminal commands quite yet so please talk in your best baby voices to me :)

Thanks!

---

### Post by pay on 2007-11-01
If you still have a command line that you can edit your xorg.conf file and change the drivers to the opensource driver```
sudo nano /etc/X11/xorg.conf
```> Section "Device"
        Driver      "fglrx"
EndSection
to ```
Section "Device"
        Driver      "ati"
EndSection

```Don't change the bits that you don't understand. If you don't have the command line for some reason you can boot a liveCD and then mount the drive and change the file from there```
sudo mount /dev/hdX /mnt/ubuntu #where X is the name of the drive letter)
```

---

### Post by TheBigBentley on 2007-11-01
oh great thanks so much for the help!!! Im gonna give this a go. I did a back up of the virtual disks just in case but I feel better knowing now I could fix this without resorting to that.

---

