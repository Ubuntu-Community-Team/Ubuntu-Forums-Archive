---
title: "Sound Problem with Multiple Hardware Devices (11.04)"
date: 2011-09-30
forum: Mythbuntu
---

### Post by chrismurf2900 on 2011-09-30
I've been having a lot of issues trying to get my sound working on Flash, as well as system sounds.  I'm using Mythbuntu 11.04.

My sound works great in MythTV, as well as in VLC (once I set the proper output area), however, I have not been able to get the system sound to work or Flash player sound working.

I think it is because I have to set the default sound output, but haven't had any luck with performing that.  Here is my "aplay -l" results:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I'm utilizing the ALC887 Digital device for my surround sound.
Here is my ~/.asoundrc file:

```
defaults.ctl.!card "hw:Intel,1"
defaults.pcm.!card "hw:Intel,1"
```

Please, if anyone can assist me or give me any suggestions, I would greatly appreciate it.
I haven't been able to have sound with youtube videos or any flash apps for a long time.

Thanks!

---

### Post by nickrout on 2011-09-30
I think you need to set the default output device in the gui. This is a separate setting to the one in mythtv. In ubuntu go to System menu|Preferences|Sound, but I am not sure where the equivalent is in mythbuntu's menus.

---

### Post by chrismurf2900 on 2011-10-01
Nickrout, I would agree with you on doing that, however, Mythbuntu (as far as I could find) does not have a gui for setting the default output device.

Ideas on where the GUI (or if there is one) is to set the output device on Mythbuntu?

Thanks!

---

### Post by klc5555 on 2011-10-01
I've had it happen on several occasions, that while aplay -l is listing the correct playback devices, it could be that alsa in your primary user account has defaulted to one of the sound chips in whatever tuner card you happen to be running.

From a command prompt on your desktop, run the command "alsamixer" (It's still there on Xubuntu 10.04; I imagine it survives in Mythbuntu 11.04). If it comes up with the full set of 8 to a dozen controls, and indicates your correct sound card, then it's defaulted to your correct device. In which case I'm not sure what the problem is, unless the mixer is indicating "muted". In which case unmute.

If, however, "alsamixer" shows only a single control, and indicates some sound controller chip unrelated to your actual card, then it's defaulted to the sound controller in your tuner card (or some other wrong controller chip). If the mixer has defaulted to a wrong device, depending on whether your configuration enables it, you may be able to find and set the correct device (for that single session) in "alsamixer" with the "F6" key. Then the .asoundrc in your home directory would need to be modified to point to the correct device to make the changed selection permanent.

---

### Post by chrismurf2900 on 2011-10-02
klc5555,

Thanks!  Yup, what do you know, it was on some other device as the default, with only one speaker.  So, after some research on how to change the ALSA ~/.asoundrc file to utilize my Intel device 1 as the default output, here is what the file looks like:

~/.asoundrc
```
pcm.!default {
    type hw
    card 0
    device 1
}
ctl.!default {
    type hw
    card 0
    device 1
}

```

I also put this same text into the /etc/asound.conf file since I want every user to utilize this as the default speaker.

Thanks everyone for your help!

---

### Post by chrismurf2900 on 2012-04-29
For those that may wind up here from a web-search, I had to change my asoundrc and asound.conf in order to work properly in Ubuntu 12.04 (LTS).  See updated version below:

```
pcm.!default {
     type plug slave.pcm {
           type hw card 0 device 1
     }
}
ctl.!default {
     type plug slave.pcm {
           type hw card 0 device 1
     }
}
```

I found this solution via the [Ubuntu 12.04 Sound Troubleshooting Document]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1#bookmark=id.pjdult4q3zz8").

---

### Post by anonymousdog on 2012-05-03
Is that change due to pulse audio being on your 12.04 system, or is there a syntax change for .asoundrc/asound.conf?

---

### Post by chrismurf2900 on 2012-05-03
I believe it is a syntax change.  I utilized the default Mythbuntu 12.04 distribution, and had this issue since I wanted to output audio only through the digital output (by default).

---

