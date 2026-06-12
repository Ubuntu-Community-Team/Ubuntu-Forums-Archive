---
title: "Quiet Sound Output"
date: 2008-11-05
forum: Multimedia Software
---

### Post by waspinator on 2008-11-05
Hi,

I've noticed that the sound output in Ubuntu 8.10 (first version one I've tried) is very low compared to Windows Vista. I have tried to change output from ALSA to OSS, ran alsamixer and set output to 100%, and tried to plug the speakers into every possible port on my computer. Nothing has helped.I noticed that my motherboard isn't compatible with ubuntu, but I hoped to use it anyway. 
Is there any known fix for this? Specs below. 
Thanks

Waspinator


Specs
-----
Motherboard: P5KPL-CM
Chipset: Intel G31 / ICH7
Audio: VIA VT1708B 8 -Channel High-Definition Audio CODEC 
O/S Compatibility: Windows Vista / Windows XP

[http://www.asus.com/products.aspx?modelmenu=2&model=2068&l1=3&l2=11&l3=563&l4=0](http://www.asus.com/products.aspx?modelmenu=2&model=2068&l1=3&l2=11&l3=563&l4=0)

If there is anything else I can provide that would help in the diagnosis please let me know.

---

### Post by c/Kr3t on 2008-11-05
did you turn the speaker volume up with the little dials?
heh


try this

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

### Post by waspinator on 2008-11-09
Hi,

I chose not to listen to c/Kr3t, and instead try to do the standard thing when hardware doesn't work. Try the audio drivers provided by ASUS. They installed fine, but immediately after my sound card stopped working. I thought, no problem, they included an uninstall script. Unfortunately it didn't help, since it most likely did not reinstall the previous quiet drivers.

So now I'm without sound altogether. I really want to use ubuntu, but if something as simple as installing a driver for a sound card from asus itself breaks ubuntu instead of fixing it, I'm not sure if I'm ready for it. I'm willing to stick with it for a while longer, but there is only so much time I can spend without sound.

I hope someone can help me.

Thanks,
Waspinator


INSTALL SCRIPT
--------------
```
#!/bin/sh

######## VERSION 1.5 ########

KERNEL_VER=`uname -r`

echo ".....Decompress Driver source ALSA Driver 1.0.14....."
tar xvpfj alsa-driver-1.0.14.tar.bz2 > /dev/null 2>&1
sync

echo "Remove old sound driver"
if [ -d /lib/modules/$KERNEL_VER/kernel/sound ]; then
   rm -rf /lib/modules/$KERNEL_VER/kernel/sound/pci
   rm -rf /lib/modules/$KERNEL_VER/kernel/sound/acore
   rm -rf /lib/modules/$KERNEL_VER/kernel/sound/driver
fi

echo "Compile Driver........"
cd alsa-driver-1.0.14
./configure --with-cards=hda-intel
make
make install
./snddevices 
cd ..
if lsmod |grep -q "snd_hda_intel" ; then
    modprobe -r snd_hda_intel
fi
modprobe snd_hda_intel

```

UNINSTALL SCRIPT
----------------
```
#!/bin/sh

######## VERSION 1.5 ########

echo ".....Uninstall Driver....."
if [ -d alsa-driver-1.0.14 ]; then
    cd alsa-driver-1.0.14
    make uninstall
    cd ..

    echo "......Remove Folder....."
    rm -rf alsa-driver-1.0.14
fi

#remove installed modules
echo ".....Remove Modules....."
if lsmod |grep -q "snd_hda_intel" ; then
    modprobe -r snd_hda_intel
    modprobe -r snd_seq_oss
    modprobe -r snd_pcm_oss
fi

```

---

### Post by phat_penguin on 2008-11-09
I have noticed the same thing.  In fact my Ubuntu 8.10 is less than half as loud as my fedora installation on the same machine.
unfortunately after turning everything up and trying several tests, I ended up just cranking up the amp. :( not my preferred solution

---

### Post by waspinator on 2008-11-11
bump

---

### Post by james.wilde on 2008-11-12
I have the same problem.  Brand new Acer Extensa 5620 with, apparently, a HDA Intel sound card.  This machine now dual boots to Vista or Ubuntu 8.10, and the sound level in Ubuntu is only a fraction of what it is in Vista.

I'm trying to find some suggestions in here, although av is not my strong point, but if someone who is more experienced comes up with a solution, I will be extremely grateful.

//James

---

### Post by james.wilde on 2008-11-12
Waspinator, try this:

"Have you checked your volume levels (i.e. the hardware ones, if there are any) by right clicking on the small speaker in your taskbar and selecting Open Volume Control.

In then Volume Control, select Edit -> Preferences and see if all the available volumes that you can edit are selected.

There may be exist a volume level that controls the volume of the headphone jack."

I got this suggestion from Kostkon (I think that was it) in another thread.  Fixed it for me.

Good luck.

//James

---

### Post by supernovus on 2008-11-14
I have noticed that in general, Ubuntu seems quieter than Windows. It's very strange.

I have a different problem though.

I recently bought a new computer. It uses the Intel HDA audio. I have two sets of speakers. One of them are standard Altec Lansing computer speakers. The one one is actually connected to a stereo amplifier, with pro-audio speakers attached to it. If I plug the PC speakers into either the green or black audio port, the sound is loud and clear. However, if I plug the adapter that connects to the stereo into either the green or black port, it is very, very, quiet. Unbearably so. It's so quiet, it's almost like the audio that is coming through is just feedback. When playing a standalone CD player, with the audio dial turned up to '2', the stereo is loud enough to hear clearly in my back yard. The output from the new computer however is barely audible even when the volume dial is turned up to '8'.

I don't have Windows on this particular computer, so I can't test to see if it's a OS specific issue, or if it has something to do with the on-board sound.

Whatever it is, it's highly annoying. Any suggestions?

---

### Post by waspinator on 2008-12-03
I couldn't get my system to get sound back, so I was forced to reinstall ubuntu. It works now, and I found an extra volume meter to increase the sound volume. 
I am a bit dissapointed in ubuntu and asus for not making reinstalling drivers easier, but hopfully I won't have to do this again any time soon.

Waspinator

---

### Post by courtneythevegan on 2008-12-11
I've been having the same problem. Right click on your speaker icon, and select *Open Volume Control*. I'm not terribly well versed in Ubuntu yet, so I don't know if everyone's computer will list the same options, but I left my *Device* set to *HDA Intel (Asla mixer)*.

From there, go to preferences, and select *Front*. Turn it up. It should considerably boost your volume, in both headphones and speakers.

I hope this works for others!

---

