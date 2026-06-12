---
title: "Ubuntu 10.10 Not sound card recognized HP Pavilion dv 2500"
date: 2011-09-09
forum: Multimedia Software
---

### Post by Rey Templario on 2011-09-09
Hi There!,

I am having a lot of trouble with my audio using Ubuntu 10.10 on my HP pavilion dv 2500 laptop. The audio is intermittent meaning that in one single day I have the audio working fine, but the next day my audio card is not recognized, and I can boot the computer 10 times without being recognized. I have followed thousands of instructions in order to get the audio working, without success.
I am not sure if my Virtual Box has something to do with, however, it should not be.
Please any help will be appreciated. Thanks in advance.

Here is the output for alsa-project:

[http://www.alsa-project.org/db/?f=7781124d2ae9f61ecefcad5cfd548e53b1503236](http://www.alsa-project.org/db/?f=7781124d2ae9f61ecefcad5cfd548e53b1503236)

Today I got my sound card back, but maybe tomorrow it will be gone, who knows!!!

from aplay - l I get:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

from lshw -c sound I get:

*-multimedia            
       description: Audio device
       product: MCP67 High Definition Audio
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
       resources: irq:19 memory:fc480000-fc483fff

Today my sound card is again gone (Sept 15, 2011)!!!
Yesterday, the only thing I did was to used the laptop with the battery for 45 minutes. After that I plugged in again and the sound was still working. There were also updates that I installed. Today, I could not get any output after running aplay - l as well as lshw -c sound in a terminal.
Alsa project: [http://www.alsa-project.org/db/?f=7d3f2c57b4ef732b11b4e752ce7018feb295f9df](http://www.alsa-project.org/db/?f=7d3f2c57b4ef732b11b4e752ce7018feb295f9df)
Help!!!

---

### Post by Rey Templario on 2011-09-20
Well, I have 5 days without sound!!! (since Sept 15, 2011),
If you are reading this and you are a newbie with Ubuntu, you want to keep working with a similar machine, my advice to you is **_do not install it_**, try something else.

In the output tab of the sound preferences I have the "Dummy Output" forever. I have tried thousands of solutions but this one in particular, without success: [http://ubuntuforums.org/showthread.php?t=1316634&highlight=no+sound](http://ubuntuforums.org/showthread.php?t=1316634&highlight=no+sound)

adding whatever line to: sudo gedit /etc/modprobe.d/alsa-base.conf, does not produce anything. I even added lines for models different than HP (lol), like in here: [http://ubuntuforums.org/showthread.php?t=1043568&highlight=sound+card](http://ubuntuforums.org/showthread.php?t=1043568&highlight=sound+card)

So disappointed, it was working fine... but this is my goodbye ):P

---

### Post by lkjoel on 2011-09-20
Try Sound Troubleshooting in my signature.

---

### Post by Rey Templario on 2011-09-20
Hello lkjoel,

Thanks for replied me. Something is weird, I reboot using a live cd (Ubuntu 10.10, PC (intel X86) desktop as you suggested, and again not sound, with the usual "Dummy Output"in the sound preferences. **_However_**, I just booted normally and I have sound!!!. Do you understand this? because I don't.

---

### Post by lkjoel on 2011-09-20
I think that it's a problem with your sound card, and has nothing to do with any OS.
I suggest that you try another sound card, and see if it works.

---

### Post by lidex on 2011-09-21
You need to re-install alsa for one thing. It's borked.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by Rey Templario on 2011-09-21
Today I don't have sound.
Lidex I re-installed alsa as you suggested and nothing, again the usual Dummy Output in sound preferences. Is it possible that my virtualbox is messing with the Alsa configuration? or maybe pulseaudio?.
I am now going to reboot the machine with the live cd to see if I get sound as Yesterday.

---

### Post by Rey Templario on 2011-09-21
There you go I have sound again. So, I don't think it is a problem with the hardware. So, what I did was to run the live cd, test the sound, again the Dummy output in sound preferences, then reboot without the cd, I also pressed ESC, and I have sound. By the way, this time my alsa-base.conf file does not have any new line, like suggested here: [http://ubuntuforums.org/showthread.php?t=1043568&highlight=sound+card](http://ubuntuforums.org/showthread.php?t=1043568&highlight=sound+card).

Also, I have noticed that the following string appears during the start up with several others during the sessions without sound: "speech-dispatcher disabled; edit /etc/default/speech-dispatcher", not really sure if it is accurate since it goes really fast. The others are "kernel --- 35, pulseaudio----, virtualbox---, things like that, they go fast and they change colours from white to orange.
I am looking forward to receiving your feedback. 

Cheers

---

### Post by audiomagnate on 2011-11-20
I have the exact same problem with my HP Pavillion DV9700. To suggest that this is a hardware problem is laughable. This OS is worth every penny I paid for it. Life is too short to diddle with your OS for hours on end. Vista restore disks ordered from HP.HP laptops are pretty damn popular, and this has been a problem for years. Bye guys! My disks will be here tomorrow AM. I can't wait.

---

