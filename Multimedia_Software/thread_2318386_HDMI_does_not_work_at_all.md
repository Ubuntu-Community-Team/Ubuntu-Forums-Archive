---
title: "HDMI does not work at all"
date: 2016-03-25
forum: Multimedia Software
---

### Post by Villasukka on 2016-03-25
Hello!

I have an Asus laptot that has a sticker on it reading NVIDIA Geforce 610M 2GB. I used to have Windows 7, but now I have Lubuntu 14.04.

I'd love to watch movies connecting my laptop to the TV screen with a HDMI caple like I used to do. I tried it earlier today, but either my TV or laptop responded at all. No sound, no picture. 

Then I went to Nvidia's web-side and downloaded Nvidia 600-series (I didn't find 610M) for Linux x64. I opened the file and it had only text on it. After that I tried if the HDMI worked, but it didn't. I wasn't surprised, really. But I still have it in my Downloaded folder in case I need it later. 

Should I press Ctrl + Alt + T and put some kind of code in there? Or should I download something else than Nvidia? ...Where should I even begin?


I would really appreciate it, if someone explained this to a complete newbie with plain english! :) 



Cheers,
Villasukka

---

### Post by yancek on 2016-03-25
What kind of movies, commercial movies usually sold on a dvd?
Can you watch these movies from the DVD drive on the computer from Lubuntu?

---

### Post by Villasukka on 2016-03-26
No, just like Youtube, Putlocker, Netflix - directly from the Internet. Also I like to use my TV as a computer screen. 

I got curious and just tried to put a DVD in to my laptop, but it didn't open with Gnomeplayer or VLC-mediaplayer. With Gnome, when I tried to open the DVD (it didn't open automatically) my whole descop screen was filled with pictures of play buttons on gray-colored squares. Also the DVD made weird "scratching" noices in the DVD-player of my laptop. 

But I can go to Youtube and watch videos there.

I've googled about this problem, but I only get links to forums where people ask how to get the sound working on HDMI, but I don't have the picture either, it just doesn't respond at all. It normally worked on HDMI2 on my TV, but it's just a black screen. I tried HDMI1 too, but it didn't work either.

I tried these instuctions: [http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/](http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/)

Still my TV says "no signal"

---

### Post by SeijiSensei on 2016-03-26
Install the NVIDIA driver from the Ubuntu repositories with the command

```
sudo apt-get install nvidia-current
```

or use the "Additional Drivers" app.  If you have a machine with both Intel and NVIDIA graphics things can be a [bit more complicated]("https://wiki.ubuntu.com/Bumblebee").

---

### Post by Villasukka on 2016-03-26
I have an intel core 13 sticker too... :D

---

### Post by SeijiSensei on 2016-03-26
I'm not sure what that response means.  Does the machine have both Intel and NVIDIA graphics adapters, or just the NVIDIA card?  Did you try installing nvidia-current?

If you don't know what hardware you have, run the command "lspci" from a terminal and look at the resulting list for "VGA" entries.  If both the Intel and NVIDIA adapters are listed, and you only intend to use the latter, then go into the system's BIOS and see if you can disable the Intel adapter.

---

### Post by Villasukka on 2016-03-26
It's easter, but after following those instructions you gave and rebooting the computer it felt like christmas, because now the TV connects with my laptop! I have spent hours trying to figure this out, so thank you very much, Seijisensei!

The only problem is now that the sound comes from my laptop, not TV. Any suggestions how to fix this?

---

### Post by Villasukka on 2016-03-26
It reads "VGA compatible controller: NVIDIA Corporation GF119M [GeForce 610M] (rev ff)" and "00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)"


I installent the current and Bumblebee. After I shut and opened the computer again, it worked otherwise, but no sound.

---

### Post by oldfred on 2016-03-26
If you go into system settings, sound icon, do you see the HDMI output. Turn it on.

---

### Post by Villasukka on 2016-03-27
It worked oldfred! I did it on Pulseaudio. Now the sound and the picture comes from the TV. This problem is solved. :popcorn:

Thank you so much for all of you who helped! :KS

---

### Post by Bucky Ball on 2016-03-27
Excellent. :)

Please see the first link in my signature at the bottom of this post to mark it so.

---

