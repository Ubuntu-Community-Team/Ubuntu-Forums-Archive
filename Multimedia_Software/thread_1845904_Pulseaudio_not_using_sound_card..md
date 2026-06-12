---
title: "Pulseaudio not using sound card."
date: 2011-09-18
forum: Multimedia Software
---

### Post by shiman6 on 2011-09-18
Pulseaudio won't detect and use my sound card. It's been going on for a while now, but a simple "pulseaudio -k" "pulseaudio --start" has been making it work. Needless to say, it doesn't work anymore.

arecord -l shows that the sound card is detected and used by alsa just fine.
```

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC270 Analog [ALC270 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

But pulseaudio doesnt even see it. It just defaults to "dummy output"

This has been recent to the last month or so. Any help?

---

### Post by lidex on 2011-09-21
> **shiman6 said:**
> Pulseaudio won't detect and use my sound card. It's been going on for a while now, but a simple "pulseaudio -k" "pulseaudio --start" has been making it work. Needless to say, it doesn't work anymore.

arecord -l shows that the sound card is detected and used by alsa just fine.
```

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC270 Analog [ALC270 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

But pulseaudio doesnt even see it. It just defaults to "dummy output"

This has been recent to the last month or so. Any help?

Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*
Next use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by shiman6 on 2011-09-21
> **lidex said:**
> Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```**Reboot**
* Ignore any 'No such file or directory' errors*
Next use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.

If i remove the configurations and reboot, will automatically generated and/or default configurations be put in place?

I forgot to mention, ALSA works perfectly. aPlay plays music without pulse, jack server works fine. I have tried re-installing pulseaudio before too. Just to add this in.

---

### Post by lidex on 2011-09-22
> **shiman6 said:**
> If i remove the configurations and reboot, will automatically generated and/or default configurations be put in place?

I forgot to mention, ALSA works perfectly. aPlay plays music without pulse, jack server works fine. I have tried re-installing pulseaudio before too. Just to add this in.

Yes. Please follow direction.

---

### Post by shiman6 on 2011-10-03
Here is the alsa-project help link

[http://www.alsa-project.org/db/?f=b62dc6b0f43ba554ff37cc5fe1cbd0ca3447fcc0](http://www.alsa-project.org/db/?f=b62dc6b0f43ba554ff37cc5fe1cbd0ca3447fcc0)

I noticed my sound card is using the HDA-Intel driver, when it is listed as an ATI or something.

---

### Post by lidex on 2011-10-11
Fully update your system then re-install pulse:
Re-install Pulse
```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
```
```
sudo apt-get install pulseaudio gstreamer0.10-pulseaudio
```

Now remove pulse config again:
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**

If it happens again, run this command and post back result:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by shiman6 on 2011-10-11
> **lidex said:**
> Fully update your system then re-install pulse:
Re-install Pulse
```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
``````
sudo apt-get install pulseaudio gstreamer0.10-pulseaudio
```Now remove pulse config again:
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```**Reboot**

If it happens again, run this command and post back result:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

This almost competely removed "ubuntu-desktop" package, i had to reinstall, now sound icon doesnt even show up in the notification bar, where it would usually be next to the icon that shows me if i'm connected or not. Pulseaudio still uses the dummy output. (i'm using pavucontrol to see this)

Here is the output for what you told me to run

```

Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.

```

---

### Post by shiman6 on 2011-10-12
Maybe i should have mentioned that JACK worked perfectly? I used qjackctl and JackEQ to amplify the input (because jack is quiet normally) and i could use some programs that had jack plugins.

Well, jack doesnt work anymore.

---

