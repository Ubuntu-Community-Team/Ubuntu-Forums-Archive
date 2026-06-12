---
title: "HowTo: Output IEC958 from PulseAudio"
date: 2008-08-02
forum: Multimedia Software
---

### Post by fcr on 2008-08-02
Unfortunately PulseAudio does not seem to support IEC958 directly but ALSA does.
Up to now I have found plenty of posts on how to output ALSA devices via PulseAudio, but very little on how to do the opposite. Since I just solved this problem I thought that it might help others if I post how.

This assumes that you have PulseAudio Session Management running and ALSA configured to output via IEC958. The PulseAudio Session Management should be enabled in the Ubuntu System/Session/Session Preferences dialog.

In addition you will need to install the PulseAudio Device Chooser. You can do this from the Applications/Add/Remove... tool.

If you do not yet have ALSA working with IEC958 you can find instructions at the ALSA site [http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut).

1. With IEC958 working go to the /etc/asound.conf file. You should see something like:
```
pcm.!default {
        type hw
        card 0
        device 2
}
```
The card and device numbers, of course will depend on your particular hardware configuration. Take note of these numbers you will need them. hw:0,2 will be used below as an example only.

2. Now open a terminal and type ```
gksudo gedit /etc/pulse/default.pa
``` and in the editor that opens, scroll down to the section:

```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

```
and insert the line "load-module module-alsa-sink device=hw:<card-number>,<device-number>" where the card number and device number are the same as you have in the asound.conf. Then save the change. Once again, I will continue to use 0,2.

Using the asound.conf example above, you should have something like:
```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
load-module module-alsa-sink device=hw:0,2
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink
```

3. Now start the PulseAudio Device Chooser from the Applications/Sound&Video menu. This starts and minimizes itself to the upper right tool bar near the speaker icon. Click on the Chooser's icon, select "Preferences" and check the "Start Applet in session login. 

4. Next, from the Device Chooser, open the Manager. In the "Devices" tab you should see listed under the "Sinks" something like "alsa_output.hw_0_2" that corresponds to the line you added to /etc/pulse/default.pa. (If you do not see this entry, you may have to restart Ubuntu).
To check that the sink works you can go to the "Sample Cache" tab, select the "alsa_output.hw_0_2" in the list next to "Playback on:, then double click on say "esound.gnome-2/login. You should now hear the Ubuntu login tune trough the device attached to the IEC958 digital output of you computer.

5. The last thing left to do is choose "Default Sink" from the PulseAudio Device Chooser menu and click on the "Other" radio button. This will open a dialog to fill in the name of the sink. Type in the sink that was similar to the "alsa_output.hw_0_2" that was in the Manager. Press okay and now all those applications that were not able to generate sound via the digital port should now work, for example: Miro, Ubuntu login, and Flash in FireFox if you have installed "libflashsupport".

---

