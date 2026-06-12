---
title: "alsa by source?"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by cisbrane on 2006-11-04
Hi,

In order for my sound card to have the best support i needed the newest version of alsa 1.0.13 , so i download the packages of the website and i then tried to install it by source.

I first extracted each file to its own respective folder.

then for alsa-driver i did
./configure --with-cards=hda-intel
sudo make
sudo make install
./snddevices

I then did the similar thing of 
./configure 
sudo make 
sudo make install

for the rest of the packages.

after rebooting the first time i hear a reptitive drum beat comming from my head phone jack (so that is kinda working..) but nothing from my internal spakers which were working before.

Then I reinstalled each package (and i did not run the ./snddevices script, and i did a make install-modules for the driver package) and now the drum beat is gone, but no programs can access the alsa now or something. like the audio player xmms and the rhythm box player doesn't work.

i try to go to gstreamer-properties and then test my output and i get this following error: could not open resource for writing
gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not open resource for writing. [gstalsasink.c(640): gst_alsasink_open (): /pipeline6/alsasink3:
Playback open error on device 'default': No such device]


any suggestions?

thanks

---

