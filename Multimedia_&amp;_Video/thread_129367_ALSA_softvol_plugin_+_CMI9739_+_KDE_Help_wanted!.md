---
title: "ALSA softvol plugin + CMI9739 + KDE: Help wanted!"
date: 2006-02-13
forum: Multimedia &amp; Video
---

### Post by CyberRaven on 2006-02-13
Hi!

I struggle with the issue [described by linuxgrrl]("http://ubuntuforums.org/showthread.php?t=87599"):
> 
My onboard sound is working but I am unable to adjust the volume other than to mute / unmute channels. (...) Whichever one I choose, the same symptoms: sound works, mute/unmute works, but sliders don't. 

According to a link in the mentioned thread, the solution is an ALSA plugin called "softvol". This plugin shall be defined in $/home/user/.asoundrc to work. I googled a bit, and came up with [this example, claiming to be functional]("http://www.linuxforums.org/forum/gaming-games-multimedia-entertainment/45725-alsa-works-fine-except-volume-controls.html"):
> pcm.!default {
    type plug
    slave.pcm "svol"
}

pcm.svol {
    type softvol
    slave.pcm "hw:0,0"
    control {
        name "Volume"
    }
}

This setup didn't produce any errors at startup (which other variants I tried did), and I got a new slider in KMix/alsamixer ("Volume"). A simple ```
$ aplay foo.wav
``` plays just fine, AND varies in output volume according to the setting of the new slider!

However, all the system sounds in KDE are garbled - it sounds mostly like static. When I try to play sound and video files with Kaffeine, it claims that > ALSA device "default" is already in use by another program.

So, does anyone have an idea in terms of what might be the problem? Any help would be greatly appreciated! Here is btw a link to what seems to be the [official reference for the PCM plugins]("http://www.alsa-project.org/alsa-doc/alsa-lib/pcm_plugins.html").

And to whom it may be helpful, here are some outputs:
```
$ lsmod | grep snd
snd_mpu401              6472  0
snd_mpu401_uart         7424  1 snd_mpu401
snd_usb_audio          68800  1
snd_usb_lib            14336  1 snd_usb_audio
snd_rawmidi            23840  2 snd_mpu401_uart,snd_usb_lib
snd_seq_device          8332  1 snd_rawmidi
snd_hwdep               8864  1 snd_usb_audio
snd_intel8x0           30912  1
snd_ac97_codec         73084  1 snd_intel8x0
snd_pcm_oss            47008  0
snd_mixer_oss          16896  1 snd_pcm_oss
snd_pcm                82052  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    52452  16 snd_mpu401,snd_mpu401_uart,snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9696  2 saa7134,snd
snd_page_alloc         10376  2 snd_intel8x0,snd_pcm
usbcore               107260  8 snd_usb_audio,snd_usb_lib,hci_usb,usb_storage,usbhid,ehci_hcd,ohci_hcd

```
```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.9 (Sun May 29 07:31:02 2005 UTC).
```
```
$ cat /proc/asound/cards
0 [SI7012         ]: ICH - SiS SI7012
                     SiS SI7012 with CMI9739 at 0xe000, irq 18
1 [Camera         ]: USB-Audio - Camera
                     Camera at usb-0000:00:03.2-1, full speed
2 [UART           ]: MPU-401 UART - MPU-401 UART
                     MPU-401 UART at 0x330, irq 10

```

Well, that's it! And btw, I'm quite new to (K)ubuntu (and Linux in general), so please excuse any half-wittedness ;-)

Best regards,
CyberRaven

---

### Post by anath3ma on 2006-02-22
ok... part of the problem is that from:
    ALSA device "default" is already in use by another program.
i can assume that your card does not do software mixing.  this is exactly the /etc/asoundrc that i use in order to use the software mixer and volume plugin.  i am currently trying to use softvol as well as dmix plugins but i cant seem to use the software vol control after i enable the plugin.  good luck...

pcm.!default {
    type softvol
    slave.pcm dmixer
  control {
    name "PCM Volume"
    card 0
  }
}

pcm.dmixer  {
        type dmix
        ipc_key 1024
        slave {
            pcm "hw:0,0"
            period_time 0
            period_size 1024
            buffer_size 4096
            rate 44100
        }
        bindings {
            0 0
            1 1
        }
}

ctl.dmixer {
        type hw
        card 0
}

---

### Post by anath3ma on 2006-02-22
also, where did you see the new slider pop up?
i looked in kmix and alsamixer and i only see my physical cards.  

thanks,
m

---

### Post by CyberRaven on 2006-02-25
Hi, anath3ma, thx for the reply!

...success!...
I replaced my old, not-working asoundrc with the setup you provided, and suddenly it all worked like a charm! Now the "PCM" slider in both Kmix and alsamixer adjusts the systemwide volume level, and the system sounds, amaroK, Kaffeine etc. works together in harmony! Amazing...(I'm still to unfamiliar with such coding and scripts to understand _what_ made it work, though (former Wintendo-user), but thanks a lot!)

...the new "Volume" slider...
My new slider appeared in the far right of both Kmix and alsamixer, under my card O (see enclosed pic)[ATTACH]6420[/ATTACH]. Unfortunately am I unable to remember exactly which asoundrc setup I tested when it appeared... The funny thing is that it remained also after I changed the asoundrc again - it's still there, but doesn't seem to do anything!

...and as for the garbled system sound...
The system sounds in KDE sounding like static, mentioned in my original post, was actually due to a mistake of my own... In "System Settings" - "Sound & Multimedia" - "System Notifications" - "Player settings" I had set the option "Use external player" - but without specifying any player..! I believe this resulted in KDE sending the sound files directly to the sound device, naturally resulting in noise/static in stead of sound :-)

But, as mentioned, your post solved my problem! Thanks again!
Best regards,
CyberRaven

---

