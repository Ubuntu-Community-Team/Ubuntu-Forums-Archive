---
title: "Compaq Armada 3500 sound card works but sound is scrambled"
date: 2007-01-30
forum: Multimedia &amp; Video
---

### Post by trevva on 2007-01-30
Gudday,

I have Fluxbuntu nBuild1-rev2 installed on my ancient Compaq Armada 3500 laptop (if you're not familar with Fluxbuntu, its basically Ubuntu 6.05 LTS with Fluxbox). It runs really well, but the sound has been a wee bit problematic for me - the on board card is a ESS Audiodrive ESS 1869. When I first installed it, the sound card wasn't enabled, so I downloaded and built the alsa  drivers for it using the instructions provided on the alsa webpage,  [here.]("http://tinyurl.com/dcpgq") They seemed to compile ok, once I had added the missing libraries. I then was able to insert the new modules into the kernel without problem, and then successfully played some streaming audio off the internet with XMMS. Great. It works.

Or not. The problem is, its never worked since. I tried to make the modules load automatically by adding them to /etc/modules, and rebooted. When I then tried to play the audio again, I got sound, but basically just white noise. I have since removed the reference in /etc/modules, rebooted and tried loading the modules in manually. Same problem. I then completely uninstalled (make uninstall) all of the drivers, and rebuilt them. Same problem. I also worked through the "Comprehensive Sound Problems Guide" that sits at the top as a sticky, removing everything with apt-get --purge and then putting it back in again and configuring it using dpkg-reconfigure - same problem. 

The modules seem to be working ok - aplay -l lists the card correctly, and it certaintly makes noise. But something seems to be messing it all up and just spitting out garbage. Any ideas where to look next?

Mark

---

### Post by deadgobby on 2007-01-30
OK lets see here...
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)
 There is information of your sound card. 


Gobby

---

### Post by trevva on 2007-01-30
Thanks for the reply and the pointer - unfortunately the page that you pointed to doesn't really provide any information that I haven't already tried or done...

I'm wondering if the problem may be the settings that I am using with the modules that are loaded. Is there any way to tell what IRQ, DMA etc a loaded module is actually using (I'm not exactly clear either where these options should be set, so it would be nice to get the information directly from the loaded module).

---

### Post by trevva on 2007-01-31
Hi,

Here's the details that I could put together. Hopefully this is of use. 

[FONT="Courier New"]```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ES1869 [ESS AudioDrive ES1869], device 0: ES1869 [ESS AudioDrive ES1869]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

lsmod | grep snd
snd_es18xx             37900  0 
snd_pcm                88420  1 snd_es18xx
snd_page_alloc         11336  1 snd_pcm
snd_opl3_lib           12320  1 snd_es18xx
snd_timer              26660  2 snd_pcm,snd_opl3_lib
snd_hwdep              10436  1 snd_opl3_lib
snd_mpu401_uart         9504  1 snd_es18xx
snd_rawmidi            26720  1 snd_mpu401_uart
snd_seq_device          9068  2 snd_opl3_lib,snd_rawmidi
snd                    62052  8 snd_es18xx,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10784  1 snd
```[/FONT]

As you can see, ALSA seems to be installed (its detecting the card), and the modules are there in the kernal. As I said, it does make noise when I play a file, its just that the sound is scrambled and varies between white noise, and horrific speaker killing sounds.

BTW, just to answer the obvious qn - the sound card does work ok - this machine is currently dual boot with Windows ME, and it plays sound fine there...

Cheers,

Mark

---

### Post by trevva on 2007-02-04
Is anyone able to help me with this please? I'm kind of stuck... :-(

---

### Post by Klausgena on 2007-03-15
I have the same problem. Xubuntu 6.10 installed on Compaq Armada 3500 but no sound. Have not tried to fix it yet. Currently looking for a fix on the internet.

Have you had any succes yet?

---

