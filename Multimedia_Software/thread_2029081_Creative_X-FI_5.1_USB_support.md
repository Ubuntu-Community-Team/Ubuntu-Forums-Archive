---
title: "Creative X-FI 5.1 USB support"
date: 2012-07-19
forum: Multimedia Software
---

### Post by netikras on 2012-07-19
Hi everyone.
Yes, I am aware that there already exists a post with a driver for this device. I don't know what's wrong (about the driver or me) but I couldn't make it work 100%.
So I created a 'driver' myself. It is not really a driver as it's just a bunch of scripts and a few lib-like files. So here's what it does:
   * preloads alsa modules required for the soundcard
      (so that pulseaudio can use all 6 channels instead of stereo-mode)
   * trigers some events after the device is plugged in
      (launches daemons used by remote-control; restarts pulseaudio server (I'm looking forward to fix this in the future))
   * completely supports remote control RM-820 (all the buttons + knob-events).
If you want to edit remote control config, take a look at the ~/.lircrc file.

I created it using ubuntu 12.04 so it should work if you're using it as well. It MAY work on some previous versions of ubuntu. I have not tested yet (and probably will not).

Hope someone will find this usefull :)

1) untar
2) enter the directory
3) $ sh install
4) inform me in case any error occurs (THANK YOU)
5) &joy :)

---

### Post by ubik89 on 2012-08-03
Thank you!

How did you manage to get the remote control working? On my system it doesn't work.

I've installed lirc, but when i press the buttons on the remote control there is no signal?

---

### Post by netikras on 2012-08-03
Hi,
have you installed my scripts?
Your remote control may not work because there are no libraries that assign signal received from remote to some meaning. The lib is in my package.

Does the blue light on the soundcard blink when you press any button/knob?

---

### Post by ubik89 on 2012-08-04
Ah, it works, great! Thank you. I had to change the .lircrc in my home folder

---

### Post by ubik89 on 2012-08-04
But not all keys are working...

Just the following works, when I run irw

```
ubik@Lenovo-S205:~$ irw
0000000000000010 00 knobvolup RM-820
000000000000000f 00 knobvoldn RM-820
0000000000000010 00 knobvolup RM-820
000000000000000f 00 knobvoldn RM-820
0000000000000027 00 left RM-820
0000000000000028 00 right RM-820
000000000000001b 00 menu/back-long RM-820
000000000000001a 00 return RM-820

```

---

### Post by netikras on 2012-08-04
that's odd... is it RM-820 you're using (remote)?

---

### Post by ubik89 on 2012-08-05
yes, I'm using RM-820. irw shows that I'm using it.

---

### Post by koiVIII on 2012-09-03
Thanx for scripts and funny a shell construction:


: <<'INFO'
This script was created using ubuntu 12.04..
....
INFO

---

### Post by donkarziavelli on 2012-11-09
hey,

i got that card too and it works like a charm. only the remote is not working. my problem is now that i don't want to **** with the running card, so when i install this script, will it change something with the drivers? i only need that remote control part of his script.

---

### Post by netikras on 2012-11-09
ugh.... it's been a while since I used it :)
well.. basically you just could comment line

sudo cp files/100-creative-SB-xFi-51.rules /etc/udev/rules.d/

in the "install" file. It will still copy the configs to your computer but it won't set the trigger to launch a bunch of commands when the card is plugged in...

---

### Post by Mapkoz1 on 2012-11-20
I am trying to use the card for recording stuff with audacity.
cannot either get it to record or play sound.

---

### Post by zjorzzzey on 2013-02-26
the $HOME/.lircrc file contains a lot of references to 

```
/home/netikras/skriptai/creative/remote/volume-switch
```

doing a simple search&replace with the appropriate username got me a working remote...

---

### Post by szilvesztercsab on 2014-01-16
I've tried many things... including your solution but...

when I start irw... it doesn't have any output and it kills lirc...

I'm not sure what am I doing wrong :(

---

### Post by Dan_Ashby on 2014-01-25
> **netikras said:**
> 
   * preloads alsa modules required for the soundcard
      (so that pulseaudio can use all 6 channels instead of stereo-mode)
   * trigers some events after the device is plugged in
      (launches daemons used by remote-control; restarts pulseaudio server (I'm looking forward to fix this in the future))
   * completely supports remote control RM-820 (all the buttons + knob-events).
If you want to edit remote control config, take a look at the ~/.lircrc file.

I created it using ubuntu 12.04 so it should work if you're using it as well. It MAY work on some previous versions of ubuntu. I have not tested yet (and probably will not).


This has been very useful to me. I'm running Ubuntu server 12.04 with no GUI and previously couldn't get anything to show up in aplay -L. Now I can see all the PCMs and some extra stuff. What I can't understand is how to get a useable mixer? Amixer etc. reports nothing. I've corrected the entries in .licrc but can't really tell if anything's working as I can't see or get a mixer to run.

If I'm using the output PCM surround51:Pro and input hw:Pro,0 then does it use PulseAudio at all? I just can't tell what the hell is going on.

Any help would be hugely appreciated because I'm extremely confused right now.

Thanks,
Dan

---

