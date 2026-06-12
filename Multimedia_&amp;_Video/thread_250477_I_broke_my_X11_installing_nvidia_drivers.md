---
title: "I broke my X11 installing nvidia drivers"
date: 2006-09-04
forum: Multimedia &amp; Video
---

### Post by Seine on 2006-09-04
Hi. I'm sorry if this should be in the beginners forum, because I am a beginner. 

I was following the guide at [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) to update the nvidia drivers.

When I ran the command ```
sudo nvidia-glx-config enable
``` it responded with a failure message. Stupidly I didn't write it down. It suggested a command to run to regenerate an MD5 for I dont know what. I ran this command and then ran nvidia-glx-config enable again.

**Lesson learnt**: know roughly what the commands are doing before I run them!

After restarting X I received a failure message. I'll post back in a moment with the message and my x config (if I can figure out how to make it available for copy/paste in windows).

Is there any way I can re-enable my previous X config?

Thanks
Jem

---

### Post by damidalla on 2006-09-04
> **Seine said:**
> Hi. I'm sorry if this should be in the beginners forum, because I am a beginner. 

I was following the guide at [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) to update the nvidia drivers.

When I ran the command ```
sudo nvidia-glx-config enable
``` it responded with a failure message. Stupidly I didn't write it down. It suggested a command to run to regenerate an MD5 for I dont know what. I ran this command and then ran nvidia-glx-config enable again.

**Lesson learnt**: know roughly what the commands are doing before I run them!

After restarting X I received a failure message. I'll post back in a moment with the message and my x config (if I can figure out how to make it available for copy/paste in windows).

Is there any way I can re-enable my previous X config?

Thanks
Jem

I once tried the same. I only did what the tutorial told me to do, regenerating the MD5. I did not have to...
I suggest doing a
```
sudo dpkg-reconfigure xserver-xorg
```
Usually, you can press 'ENTER' to every question. The only point where you should take care is when it asks you about the driver to use: select 'nvidia'.
Then, you'll have a working xorg configured to use nvidia drivers...

---

### Post by tseliot on 2006-09-04
Try this:
```
sudo nvidia-xconfig
```


and restart the xserver:
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

then if even that doesn't work:
```
sudo dpkg-reconfigure xserver-xorg
```

Select "nv" and press ENTER whenever you don't know the answer to the other questions.

---

### Post by kerry_s on 2006-09-04
If you installed nvidia-glx than you might still be able to load it.

do
sudo nano /etc/X11/xorg.conf    <look for the driver and change like this->

Driver		"nvidia"

Then do ctrl + x and then y and enter to save, then reboot or type startx . if that don't work change it to "vesa" to get the stock drivers.

---

### Post by Seine on 2006-09-04
I am writing this from my beloved Ubuntu! 

Thanks everyone, I'm absolutely stoked with the prompt helpfulness here. :mrgreen: :KS

---

