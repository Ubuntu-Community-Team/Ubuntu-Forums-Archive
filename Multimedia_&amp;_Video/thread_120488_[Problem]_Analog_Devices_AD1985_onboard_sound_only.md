---
title: "[Problem] Analog Devices AD1985 onboard sound only rear channel aktiv..."
date: 2006-01-21
forum: Multimedia &amp; Video
---

### Post by MA! on 2006-01-21
Hello Ubuntu Community sry for being an noob an posting a problem with the first post but I have some trouble with my onboard sound. I get only stereo sound and also only from the rear channel. Is there a way to reconfigure ALSA to make it work ? thanks in advance.

<bump>
Anyone please, i know newbie questions are annoying, but everyone starts off small.

---

### Post by MA! on 2006-01-23
Taking a closer look, i see that the actuall device AD1985 is configured on OSS not ALSA. Maybe thats the problem ? How to change that ?

---

### Post by FarEast on 2006-01-24
Hi,
Please paste the output of the commands below.
$ cat /proc/asound/cards
$ lsmod | grep snd

---

### Post by MA! on 2006-01-24
$ cat /proc/asound/cards :

```
0 [ICH5           ]: ICH4 - Intel ICH5
                     Intel ICH5 with AD1985 at 0xfebff800, irq 17

```

$ lsmod | grep snd

```
snd_intel8x0           34240  1
snd_ac97_codec         84508  1 snd_intel8x0
snd_pcm_oss            53760  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                92900  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25956  1 snd_pcm
snd                    57764  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10176  1 snd
snd_page_alloc         10824  2 snd_intel8x0,snd_pcm

```

And big THX for you trying to help me !

---

### Post by FarEast on 2006-01-24
Below is quoted from the document included in the kernel-source.

```
  Module snd-intel8x0
  -------------------

    Module for AC'97 motherboards from Intel and compatibles.
                        * Intel i810/810E, i815, i820, i830, i84x, MX440
                        * SiS 7012 (SiS 735)
                        * NVidia NForce, NForce2
                        * AMD AMD768, AMD8111
                        * ALi m5455

    ac97_clock    - AC'97 codec clock base (0 = auto-detect)
    ac97_quirk    - AC'97 workaround for strange hardware
                    The following strings are accepted:
                      default = don't override the default setting
                      disable = disable the quirk
                      hp_only = use headphone control as master
                      swap_hp = swap headphone and master controls
                      swap_surround = swap master and surround controls
                      [COLOR="Red"]ad_sharing = for AD1985, turn on OMS bit and use headphone[/COLOR]
                      alc_jack = for ALC65x, turn on the jack sense mode
                      inv_eapd = inverted EAPD implementation
                      mute_led = bind EAPD bit for turning on/off mute LED
                    For backward compatibility, the corresponding integer
                    value -1, 0, ... are accepted, too.
    buggy_irq     - Enable workaround for buggy interrupts on some
                    motherboards (default off)

    Module supports autoprobe and multiple bus-master chips (max 8).

    Note: the latest driver supports auto-detection of chip clock.
    if you still encounter too fast playback, specify the clock
    explicitly via the module option "ac97_clock=41194".

    Joystick/MIDI ports are not supported by this driver.  If your
    motherboard has these devices, use the ns558 or snd-mpu401
    modules, respectively.

    [COLOR="Red"]The ac97_quirk option is used to enable/override the workaround
    for specific devices.  Some hardware have swapped output pins
    between Master and Headphone, or Surround.  The driver provides
    the auto-detection of known problematic devices, but some might
    be unknown or wrongly detected.  In such a case, pass the proper
    value with this option.[/COLOR]

    The power-management is supported.

```

Please give a try;) :
Describe the following in **/etc/modprobe.d/sound** , execute
'sudo update-modules' and restart the system.

```
options snd-intel8x0 ac97_quirk=ad_sharing
```

---

### Post by MA! on 2006-01-25
Dont know maybe I didn't get it right but it didn't work.

If I unsterstood you right I had to edit file called **sound**
in **/etc/modprobe.d/sound** and insert:
```
options snd-intel8x0 ac97_quirk=ad_sharing
```

The file didn't exist so i created it, a empty text file renamed and pasted it.
Then i did **sudo update-modules**,restarted but i didn't work. Did I mistunderstand you or was that you had in mind ?

Maybe i have to use this option somewhere else cause i installed diffrent kernel ? (sudo apt-get linux-686-smp)

And I also connected extra line in and line out to the mainboard (frontpanel of case) maybe the signal is only provided to those.
EDIT:
tryed connecting headphones to front line out and they work but still center and bass channel dont work.

---

### Post by FarEast on 2006-01-25
It seems that your card is properly configured.
Now, try tweaking volume controls with alsamixer.

Please read the thread below.
[http://ubuntuforums.org/showthread.php?t=120941](http://ubuntuforums.org/showthread.php?t=120941)

mpvano's suggestion(#8) will help;) .

---

### Post by MA! on 2006-01-26
Thank you will try ALSA mixer hopfully it finally works ! 
Big Thanks

EDIT: No, doesn't help at all. :-( I can do alsa mixer -c 0 but not -c 1 and still only rear channels.
         Also i booted and only now (i tried it 3 times before) there appeared something about /etc/modprobe.d/sound saying "bad line" or sth. like that

---

### Post by FarEast on 2006-01-27
Hmm...
I am now at a loss what to do.
How about consulting ALSA users mailing list?
[http://search.gmane.org/search.php?group=gmane.linux.alsa.user&query=AD1985](http://search.gmane.org/search.php?group=gmane.linux.alsa.user&query=AD1985)

---

### Post by flight553 on 2006-09-07
Ijust installed Dapper and noticed that although the special volume and mute keys on my laptop did correctly invoke the gnome volume control applet, that applet had no effect on actual volume. 

I checked for my type of soundcard from a terminal:

   lsmod | grep snd_

and the result showed me that my Dell has this AC97  intel8x0 (actually, the ALSA volume control GUI reports it as an Intel ICH5).

Fiddling with the ALSA mixer (doubleclick speaker icon in panel), make sure you are working on the ALSA device (File, Change Device, choose Intel ICH5 (ALSA Mixer)), and then do Edit, Preferences, and check boxes for Master, PCM and Headphone which will make them appear on the mixer.

Now play some music so you can monkey with the mixer  levels on those 3 devices to see what effect they have. I discovered that 

1. the Master level did nothing
2. PCM lever fully controlled all volume
3. with PCM set half way, the Headphone lever did have an effect on volume

Therefore, I fixed my problem by editting this file from a terminal window 

     sudo bash

(enter password, now you have a root shell. No need to sudo every additional command)

     pico -w /etc/modprobe.d/alsa-base

At the end of that file I added this line:

     options snd-intel8x0 ac97_quirk=hp_only

CNTRL+X and then ENTER will save the file and exit the pico editor. Then reboot.

Play some music and then try your multimedia volume control keys. They worked, and then I fine-tuned/calibrated them by doubleclicking the volume icon in the panel and pushing PCM lever up to max, and then adjusting speaker volume to a comfortable level using the Master lever.

If the quirk option I used does not work for you,  try re-editting the file and replacing "hp_only" with some of the other quirk options and rebooting. Repeat until it works or you exhaust all the options.

---

### Post by Steggie on 2007-02-25
Well it would seem that unlike MA! my first post as a noob would not be a problem but a thanks too flight553. 

I have been trawling through countless forums with that exact same problem. I had come across the ac97_quirk before but this was the first time anyone said where it needed to go. 

Thanks again guys that was the last issue I had to solve for a happy Ubuntu life. 

:)

---

