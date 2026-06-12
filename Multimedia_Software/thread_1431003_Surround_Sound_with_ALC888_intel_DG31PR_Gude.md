---
title: "Surround Sound with ALC888 intel DG31PR Gude"
date: 2010-03-16
forum: Multimedia Software
---

### Post by Dimitree on 2010-03-16
Well i will write this down one more time i hope you don't delete it again >_>

To enable surround sound with ALC888 on Intel DG31PR for all versions of ubuntu inluding Lucid.(this works on other distros with alsa as well)

**gksu gedit /etc/modprobe.d/alsa-base.conf**

Find this line (if there is no such line (or the file is empty) it doesn't matter just add the next line and save it)(note that on older Ubuntu versions the file is named "alsa-base" as far as i remember):
**# Prevent abnormal drivers from grabbing index 0**

Add this line after the #Prevent abnormal drivers from grabbing index0:
**options snd_hda_intel model=3stack-6ch-dig**

Then use this command to edit pukeaudio:
[B]gksu gedit /etc/pulse/daemon.conf
[/B]
Find this line:
**; default-sample-channels = 2**
Change it to (make sure to remove the **;** in front of it):
**default-sample-channels = 6**

**Reboot**

After reboot open a Terminal and use this command:
**alsamixer**

Using the Arrow Keys of your keyboard, go to the far right of the list where it says Channel.
Using the Up and Down arrow keys, make the **channels 6**.

Then using the left and right arrow keys go to **Front, Surround, Center, LFE** and using the Up and Down arros increase their volume to max.
If on any of these channels at their bottom it says **"MM"**, this means that the channel is muted, in that case press the **M** key of your keyboard and make them **"00"**, when you unmute them the "00" will "glow" green.
Basically any channel that you use you must make "00" otherwise they are muted.And if you want to mute something press M again.

After that go to where is says **Headphon** and press **TAB** key on your keyboard.
Go to the first **"Input Source"** and using the Up and Down arrow keys make it **"Front Mic"**.This will make the system use the front Microphone jack, so you can use all the back sockets for your surround sound.

press Exit and enjoy :)

Let's see how long will this guide last before the helpful admins delete it lol ... oh blast :) wrote Gude instead of Guide ^^ oh well :p

---

### Post by B:RAD on 2010-03-26
Thanks man ^_^

---

### Post by freestuf69 on 2010-07-07
best man, but I have a small issue for the purpose that when out and get into another program , subwoofer and spatiality is lost, what should I do, thanks, sorry for my poor English.

---

### Post by freestuf69 on 2010-09-21
Thanks again, I solved the problem, instead : # default-sample-channels = 6 , I have made :# default-sample-channels = 6,
# default-channel-map = front-left,front-right,rear-left,rear-right,center,lfe  , everything is ok , shame that we are so far, I think I owe you a beer. Have nice day.

---

