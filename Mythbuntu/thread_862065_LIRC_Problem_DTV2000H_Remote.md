---
title: "LIRC Problem DTV2000H Remote"
date: 2008-07-17
forum: Mythbuntu
---

### Post by RTucker on 2008-07-17
Hi All,

I'm trying to set up the remote that comes with the leadtek DTV2000H J and am not having much luck.

I've replaced the lircrc, lircd.conf, and hardware.conf files with the ones from [here]("http://ubuntuforums.org/showthread.php?t=708217"), and currently the enter button and number buttons work, but nothing else. I suspect this is because LIRC isn't running properly, as the keys that work seem to be being handled by whatever handles normal keystrokes. What makes me say this is that the number and enter keys work anywhere on the system (in a terminal window, etc.) and function exactly as the same keys on the keyboard.

When I run sudo /etc/init.d/lirc start, I get:
```

: not foundardware.conf: 5: 
: not foundardware.conf: 8: 
: not foundardware.conf: 11: 
: not foundardware.conf: 14: 
: not foundardware.conf: 22: 
 * Starting remote control daemon(s) : LIRC                                     ' not supported.t
Supported drivers:
    accent
    alsa_usb
    asusdh
    atilibusb
    audio_alsa
    bte
    bw6130
    creative
    creative_infracd
    default
    devinput
    dsp
    dvico
    ea65
    i2cuser
    irman
    livedrive_midi
    livedrive_seq
    logitech
    macmini
    mp3anywhere
    mouseremote
    mouseremote_ps2
    null
    pcmak
    pinsys
    pixelview
    sb0540
    silitek
    tira
    udp
    uirt2
    uirt2_raw
    usb_uirt_raw
    usbx
                                                                         [fail]
```Also, if I try to run irw it says command not found.

irrecord works though and will record all buttons.

Any help would be greatly appriciated.

Thanks in advance

---

### Post by RTucker on 2008-07-19
Ok, after replacing the hardware.conf file with what seems to be the orriginal that installed with LIRC, and editing it by hand to match the DTV2000H remote, I now have LIRC starting without complaint.

I can run irw and all of the buttons are received and displayed correctly (corresponding to lircd.conf).

My problem now is that once in mythtv, the  only buttons that work are 'Enter' and 0-9, as before.

I've tried the lircd.conf and lircrc files from [here]("http://ubuntuforums.org/showthread.php?t=708217") and [here]("http://www.users.on.net/%7Epromus/") and both do the same thing, I have lircrc at /home/user/.lircrc, and a symlink to it at /home/user/.mythtv/lircrc, and I saw somewhere that putting it in /etc sets those settings globally, so its also at /etc/lircrc.

Again, any help would be appreciated
[[COLOR=Black][/COLOR]]("http://ubuntuforums.org/showthread.php?t=708217")

---

### Post by itsdaveperdue on 2008-07-21
Judging from your comments I'm assuming that irw shows all of the keys and what they're mapped to in lirc.  The lircrc file will translate them to a keypress.  In MythTV's frontend you have to setup the keys the way you want them (if they're not working the way you need).

I think the key is you need to make sure that the frontend is getting your keypresses from lirc and you have to make sure they're mapped the way you want them.  Go into the frontend and check the key bindings.

Also: make sure the lircrc button names match what you have programmed in the lircd.conf file (e.g. lircd.conf shows the button name CH+, make sure lircrc shows CH+ for the button, and make sure the "config" shows the correct keypress).

---

### Post by xfred on 2009-03-21
Don't know if you've solved your problems, but I just upgraded from 8.04 to 8.10 and had similar problems.  After some messing around and a lot of googling I cobbled together the solution that I've posted [here]("http://ubuntuforums.org/showthread.php?t=1102033&highlight=DTV2000H") which worked in my case.

Hope that helps.

---

