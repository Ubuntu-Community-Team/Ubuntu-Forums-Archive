---
title: "My solution to the hda-intel/headphones plugged in doesn't mute speakers bug"
date: 2008-05-19
forum: Multimedia Software
---

### Post by henkeb on 2008-05-19
I had the problem that speakers didn't mute when headphones were plugged in and it seems there is a large number of people experiencing the same problem. I probably tried every possible solution available and spent a LOT of hours with this bug. I am myself a beginner to linux but this solution worked for me. (I also installed the latest ALSA drivers but I don't think it is necessary, there are howto:s available if you want to try that also)

OK let's begin.

1) Type  cat /proc/asound/card0/codec#* | grep Codec in a terminal to find out which codec is in use.

2) Search for the file ALSA-Configuration.txt and open it. Search in the document for your particular codec. There should be a list with model name and description. Find the description that best fits your computer and copy/remember/write down the model name for that description. (In my case with an LG E500 it's 3stack-6ch)

3) type sudo gedit /etc/modprobe.d/alsa-base in a terminal. On the bottom of the file add: options snd-hda-intel model=your_model_name_here
I saw somewhere that there should also be a blank line after that, however I'm not sure it's necessary.

4) Restart and pray

I hope this can help someone out there who has struggled with this as much as I have.

Good luck.

---

