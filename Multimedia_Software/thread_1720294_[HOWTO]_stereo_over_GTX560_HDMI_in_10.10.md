---
title: "[HOWTO] stereo over GTX560 HDMI in 10.10"
date: 2011-04-03
forum: Multimedia Software
---

### Post by MasterZ on 2011-04-03
I bought an Nvidia GTX560ti and after a fresh ubuntu install, I had no Sound over HDMI , no nvidia drivers installed. 

In this guide I'll explain how to get basic stereo sound functionality (over HDMI) for all applications.


Procedure:

**1 - install Nvidia drivers and VDPAU libraries (for smooth video)**
Add the following repository to your sources: ppa:ubuntu-x-swat/x-updates ([https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates)) (graphics drivers)
with this command: 
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

Then install the packages: 
```
sudo apt-get update
sudo apt-get install nvidia-current libvdpau1 nvidia-185-libvdpau
```


Reboot.
run: 
```
sudo nvidia-xconfig
```
You now have the latest nvidia drivers installed. you can go int the Nvidia X server settings utility to check that everything works ok.


**2 - Update your sound drivers with the latest ALSA & pulseaudio**
Add the following repository to your sources: ppa:ubuntu-audio-dev/ppa ([https://launchpad.net/%7Eubuntu-audio-dev/+archive/ppa](https://launchpad.net/%7Eubuntu-audio-dev/+archive/ppa)) (alsa, sound)
with this command: 
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa

sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```

(source: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules))

To make things clean, I started synaptic and upgraded all packages. (my pulse packages were upgraded in the process)

Reboot


**3- Determine Alsa device:**

Now your hdmi sound card should be listed by typing 
```
aplay -l
```

Unfortunately the sound do not work at this point, even if I select Nvidia HDMI Stereo as 'output' in the sound preferences. 

run alsamixer in a terminal. 
press F6 to change to your hdmi sound card, then unmute all channels (there should be 4 SPDIF channels).

Run VLC an play a sound file, then go to Preferences/Audio.
Set the 'output module' to ALSA and the device to one of your hdmi device.
Save the preferences and test the sound. If it does not work, try another hdmi device. 

For my GTX560ti the correct device was "hw:1,7"
Now You should be able to output sound from a terminal with the command: 
```
speaker-test -D plughw:1,7 -c2
or 
pasuspender -- aplay -D plughw:1,7 /usr/share/sounds/alsa/Front_Center.wav
```
(replace the device number with the correct number for you)



**4 - pulse audio configuration**

edit the file /etc/pulse/default.pa (as root)
under the line:
#load-module module-alsa-sink
add this line:
load-module module-alsa-sink device=hw:1,7
(replace the device number with the correct number for you)

reboot. 
Now if you open your sound preferences on the output tab, you will see that a new device has appreared, called "HDA Nvidia". 
Select it as your default sound output device. 


That's it. You should now have stereo sound over HDMI in all your applications. 
I hope this helps.

---

