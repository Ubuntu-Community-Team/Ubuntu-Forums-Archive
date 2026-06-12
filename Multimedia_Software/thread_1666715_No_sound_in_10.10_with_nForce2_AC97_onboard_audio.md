---
title: "No sound in 10.10 with nForce2 AC97 onboard audio"
date: 2011-01-14
forum: Multimedia Software
---

### Post by humphreybc on 2011-01-14
Hi guys and gals,

Over the last few days I've been spending some time converting my headless web server into a media center running Boxee for our lounge.

I have managed to get *nearly* everything working with the exception of sound. The computer has onboard sound, both front and back ports, and I tried every combination of outputs and plugs.

I also checked it wasn't muted, or anything like that.

So, I wasn't able to get it working with the stock Ubuntu 10.10 stuff - I turned to Google and found a thread which suggested I download and install [this.]("http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false")

I ran the ./install as root, and it took about 3 minutes to install everything. Rebooted and now I'm left worse off than before - this time [I actually have no sound card even listed.]("http://dl.dropbox.com/u/1887929/no-sound-device.png")

I've been thinking some more, and after another hour or two reading through random threads, I think it may have been a mistake to install those drivers.

I couldn't find a way to uninstall them, so I've been reinstalling all the alsa and PulseAudio packages I can find with no luck.

Now I'm stuck with doubly no-sound.

If I can't get onboard working then I'm considering buying a new graphics card with HDMI out (the current one has a hard time with Boxee), or maybe a dedicated sound card instead.

Suggestions?

Thankyou so much!

---

### Post by me4oslav on 2011-01-14
Have you tried gstraemer-properties + gamix (I mean setting up gstreamer-properties according to gamix).This two always solve my problems,but I am far from alsa/pulse expert,my father usually fix those.

---

### Post by Richard_T on 2011-01-14
Try this Bud If not do some more searches.   

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

:)

---

### Post by baekgaard on 2011-01-14
When unmuting, have you used the GUI based programs for that? If so, pls try also the CLI alsamixer. I've set up several similar devices, and often had to go to alsamixer to find and change the one line that was muted for some strange reason.

Not sure how to uninstall the other drivers -- haven't looked into that. But you could also try to create a new user and log in as that user, just to make sure you don't have any gnome sound related left-over settings somewhere that accidently gets invoked.


-- Per.

---

### Post by -::Bas::- on 2011-01-14
Like the bro above me said: install alsamixer, and run it from the commandline. Very powerful tool for getting sound to work.

---

### Post by ActionParsnip on 2011-01-14
wget -O alsa-info [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) ; bash ./alsa-info --stdout 
 
What is the output please?
 
Thanks

---

### Post by dr_rimzi on 2011-01-14
Well I've got the same exact configuration on my desktop PC -
nforce2 AC97 with Ubuntu 10.10, and everything worked out of the box. 

Some misconfiguration or some other hardware properties might be at fault here.

Could you please give us more details on that?


Cheers,
RimZi

:popcorn:

---

### Post by humphreybc on 2011-01-14
> **ActionParsnip said:**
> wget -O alsa-info [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) ; bash ./alsa-info --stdout 
 
What is the output please?
 
Thanks

[http://paste.ubuntu.com/553988](http://paste.ubuntu.com/553988)

@dr_rimzi

Yes, I think I may have made a mistake by installing the Realtek driver from their website. 

I'm most likely going to buy [this graphics card]("http://www.trademe.co.nz/Computers/Components/Video-cards/PCIExpress/auction-347213974.htm") to give Boxee some extra oomph, and if that happens, I'll be using audio via HDMI.

Now all I have to do is restore the system's audio config files back to default so it'll play nice with that new card. 

The only way I can think to restore the damage Realtek's drivers caused would be to copy across the original relevant files from a stock Ubuntu 10.10 Live CD. 

Anybody know which files I need to replace?

---

### Post by Richard_T on 2011-01-14
First try uninstall the realtek driver. Thats if you think its not helping.   I'm a bit stumped with Ubuntu I've just started using it.  Used Mandriva Kde. So it was a tad different :)

---

### Post by zer010 on 2011-01-15
I just downloaded the AC'97 Linux drivers package and checked out the ReadMe:
> The source code copy from [www.alsa-project.org]("http://www.alsa-project.org").      ver:3.3-4
Linux Source Code for ALC audio codec
Support Codec list:
====AC97 Codec=====
ALC100,100P
ALC200,200P
ALC650D
ALC650E
ALC650F
ALC650
ALC655
ALC653
ALC658
ALC658D
ALC850
ALC101
ALC202
ALC250
ALC203

====HD Audio codec ====
ALC260
ALC262
ALC660
ALC861
ALC880
ALC882
ALC883
ALC885
ALC888

Installation:
This Source Code is from [www.alsa-project.org]("http://www.alsa-project.org").
For driver installation, please follow below steps. 

Automatic install:
execute

  ./install

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support (soundcore module, default turn on)

Step 3. Complied source code
    a. cd alsa-driver-1.0.xx
    b. ./configure
    c. make
    d. make install
    e. ./snddevices

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
     (Please refer to the attached modules.conf)
     
        snd-xxxx is the card ID.

    -- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
       --- Intel ICH6 ICH7 ---------
               snd-hda-intel
           --- ATI chipset -----
           snd-atiixp

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
           snd-via82xx
           --- ATI Chipset  -------------------------------
           snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
    # ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss

Step 5. reboot your machine

Step 6. Use the alsamixer the disable mute (All audio line default is mute)
        *Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Note:     1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
    2. Kernel Version must be 2.2.14 or later.
    3. All mixer channels are muted by default. You must use a native
        or OSS mixer program to unmute appropriate channels.
    4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
    5. The driver added to support the SPDIF functoin.     
    6. a. You can download the alsa-lib-1.0.9 and alsa-utils-1.0.9a form the [www.alsa-project.org]("http://www.alsa-project.org"), then unzip and install them. 
       b. Suggest use "alsamixer" to control mixer function.
       c. Used "alsaconf" can autodetect which drive you need to install (step 4).     
        7. SUSE Distribution must install the ncurses package.  > 3. All mixer channels are muted by default. You must use a native
        or OSS mixer program to unmute appropriate channels.This seems like it could be the issue.  Run 'alsamixer' in the terminal and adjust the settings.
Edit: As a side note, it's interesting that Realtek's Linux drivers are nothing more than ALSA, which should have been installed by Ubuntu by default. :D

---

### Post by lidex on 2011-01-15
Do this to reset alsa to default. Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

### Post by john_schimandle on 2011-03-17
Same problem here. I installed those drivers from realtek and wiped out my default audio device. Did you ever get a solution to the sound not working on your system?
 
I went for a clean Ubuntu Reinstall just to get a new start point. I'm going to image that onto another partition so I can quickly get back to my install point if I screw it up again.
 
I've got a Quanmax KEEX-2030 SBC in a kiosk. Trying to get stereo sound out of the onboard ALC655 codec.
 
/var/log/dmesg does not have any reference to finding the device at boot.

---

### Post by john_schimandle on 2011-03-17
After re-install the sound is now working. Last time I installed I did not check the install of third party software. I checked that this time but don't know if that fixed it.
 
Saw the ALC655 get set up in /var/log/udev
 
Sound tests OK now in the System->Preferences->Sound Preferences speaker test. KEEX-2030 with out of the box Ubuntu 10.10 seems to work fine.
 
False alarm.

---

