---
title: "How to auto reconfigure sound?"
date: 2007-09-05
forum: Multimedia &amp; Video
---

### Post by helwitch on 2007-09-05
When I install kubuntu 7.04 on my new laptop, sound worked perfectly out of the box. Some updates and wireless&NTFS configging later, I don't have sound. Kmix comes up when I boot, but the sound card it lists is wrong. Is there a way I can rerun the auto sound hardware detection?
Aplay-l gives
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0

---

### Post by coxy on 2007-09-05
Try running the ALSA config tool:

```

sudo alsaconf

```

That should allow you select the correct sound card. You will need to have the alsa and alsa-utils packages installed to do this.

---

### Post by helwitch on 2007-09-05
I had tried that, it didn't work. I compiled and reinstalled alsa-driver, alsa-lib, and alsa-utils, the latest versions from the website, and that's done the trick! Painful tho, but it worked, I'm happy.

---

### Post by willsomebody on 2007-09-05
I also need to redo my sound, but I need to redo the sound card detection.  I have sound with the live CD, but not with my alternate install CD install.  Does anyone know how to make it go through the hardware detection that it goes through in the live CD boot up?

---

### Post by helwitch on 2007-09-06
> **willsomebody said:**
> I also need to redo my sound 
If you can't find out how to make it rerun the hardware config, what worked for me is to go [here]("http://www.alsa-project.org/main/index.php/Main_Page"), DL the driver, lib, and utils, and then follow the compiling instructions from [here]("http://alsa.opensrc.org/index.php/Quick_Install"), specifically step 3, for driver, lib, and utils. 
you'll need to install libasound-dev and libncurses5-dev from the ubuntu repository beforehand, and will also need build essentials and some other things, I'm not sure which. What I know I have is based off my having run the following, which I'm sure has things that aren't needed for compiling ALSA, but I don't know what isn't needed. ```
sudo apt-get install dh-make fakeroot gcc-3.4 build-essential
``` so if you wanted to get those and libasound and libncurses, you'd do ```
sudo apt-get install dh-make fakeroot gcc-3.4 build-essential libasound2-dev libncurses5-dev
``` and then follow the compilations instructions from step 3 of the alsa quick install. I didn't need to do anything other than compile and reinstall, the modules were already inserted and everything,

---

