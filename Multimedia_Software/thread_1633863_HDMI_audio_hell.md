---
title: "HDMI audio hell"
date: 2010-11-29
forum: Multimedia Software
---

### Post by Lipw123 on 2010-11-29
I setup a old computer as a media machine next to our TV and installed ubuntu, everything works great but for the life of me I can't get audio over the HDMI.

Its a Asus p5k3 edluxe motherboard with a geforce 8400GS video card. I connected the Spdif header on the motherboard with the vid card.

I used this guide: [https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#HDMI_Output_Does_Not_Work](https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#HDMI_Output_Does_Not_Work)

My setup looks almost the same as that, except that I dont get 3 audio devices listed. I only have a intel analog/digital option.

When I try do test the sound with this command: aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav It said it played the audio but I hear nothing from the TV. (previously I selected the wrong device and had a error)


I also tried to change the audio hardware device from the sound icon at the top of the screen to the IEC958 digital output and restarted the machine -nothing.

Oh and lastly, analog out from the green jack works perfectly fine(but the stupid TV wont accept hdmi + analog audio for some reason)

I'm not exactly a Linux buff :P So I'd really appreciate any and all feedback. If there is more info required just tell me what to do.

---

### Post by lbharti on 2010-11-30
Can you raise your volumes to full, and wait for a while (something like ten seconds) after playing?

I had the same problem, but later realized that the audio output starts late(it is not delayed).

---

### Post by Lipw123 on 2010-11-30
Thanks for the response!

Which volume do I raise, and where?

In the guide it sais to find the IEC958 output in the alsamixer, but I don't have that listed. The closest I have is SPDIF and I set that to max. 
The machine was busy playing a mp3 for at least 2 minutes while I was playing around and I heard nothing.
Aslo when I did the aplay -D ... part nothing happened for the next 15mins I was browsing around searching the forums etc for possible answers.

I'm still not even sure which output device I'm supposed to select at the hardware config part. I have several analog and digital variants there, I think the last one I tried was "Digital duplex output".

I'm starting to think that I'll just go buy some cheap 2.1 speakers and hook them up to the regular analog out ><

---

### Post by lidex on 2010-12-01
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

And post this output please:
```
sudo lshw -C display
```

---

### Post by Lipw123 on 2010-12-01
Thanks for the response, It's already 1am here and I'm about to goto bed.

I will run that tomorrow after work and update this post with the results.

Kay! I setup a VNC connectio so I don't have to fight the people watching TV to try things out :D

Here is the results of the command you said to type:
duplessis@teevee-PC:~$ sudo lshw -C display
[sudo] password for duplessis: 
  *-display               
       description: VGA compatible controller
       product: G98 [GeForce 8400 GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:bc00(size=128) memory:fe8e0000-fe8fffff

And here is the link the script generated:
[http://www.alsa-project.org/db/?f=99332e143dff73fe29971311af017be18fff29e3](http://www.alsa-project.org/db/?f=99332e143dff73fe29971311af017be18fff29e3)

Tanks again.

---

### Post by Scorpuk on 2011-01-09
When you run alsamixer can you please press F6 and let us know if it lists more than one sound card? If it does have a look at the other one. :-)


For my Asus Revo R3700 the HDMI audio out was on a second sound card.


Go figure.

---

### Post by sylar666 on 2011-01-09
Hello

Ive got the same issue with the same motherboard, the Asus P5K Premium, but I have an Asus GTX260 video card.  (Two DVI outs, i use a HDMI adaptor)
Ive got audio throught XP, and sometimes I used to have audio in Ubuntu 10.10, the thing was odd, at system start my TV outpout was 0 sound. After using the system or certain applications used, magically sound was alive via HDMI at the LCD. 
When saying applications I mean using vlc to watch videos, rhytmbox working, playing Dark Crusade with Wine... Didnt realize which combination was the trigger.
The thing is after the last kernel upgrade, I ve no HDMI sound at all.

There are my confs:

script 

[http://www.alsa-project.org/db/?f=747df0a11e99703b03296c4f1734eec614dc1d97](http://www.alsa-project.org/db/?f=747df0a11e99703b03296c4f1734eec614dc1d97)

aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: AD198x Analog [AD198x Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: AD198x Digital [AD198x Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0


And yes, I can assure you I had Hdmi audio throught the video car

Thanks for your time

---

### Post by efflandt on 2011-01-09
I have done HDMI audio on newer NVidia cards (GT 220 and GT 430) that have HDA NVidia devices that show up in **aplay -l**, but don't know anything about older cards with separate SPDIF wire.

To use analog sound on your TV (assuming it has VGA and PC audio input) check its menus for the audio input used for HDMI.  Sometimes setting PC or PCM audio input may only work for one of multiple HDMI inputs (maybe only first one).

---

### Post by lidex on 2011-01-09
> **sylar666 said:**
> 
The thing is after the last kernel upgrade, I ve no HDMI sound at all.

If you boot into previous kernel does it still work there?

---

### Post by sylar666 on 2011-01-09
Thanks for answering

> 
If you boot into previous kernel does it still work there? 	

I have tried what you told rigth now, but still no HDMI sound...

It makes nosense, I mean I know i can make audio work even I doesnt have HDMI at my lscpi -l outpout, but I dont know how to reply it.

Is there any way I can record or any config file I can save when the audio works (if it does)?

---

### Post by lidex on 2011-01-09
I would just be guessing no experience with dvi but it may help to see driver/dmesg info.
```
dmesg | grep -i hda
```
(Thanx efflandt)
A digital reference here:
[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)

---

### Post by sylar666 on 2011-01-10
Thanks again for the help lidex

This is my 

 	Code:
 	dmesg | grep -i hda 
dmesg | grep -i hda
[   25.744518] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   25.744589] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   25.744620] HDA Intel 0000:00:1b.0: setting latency timer to 64

---

### Post by sylar666 on 2011-01-24
Amazing, the solution is quite strange...

At start I dont have HDMI audio

I start pulseaudio control app
Go to Outpout Devices
Double Click mute and block channels of "Stereo Analog outpout Internal Audioi"

I have to repeat this operation everytime I restart

Weird as hell

---

### Post by sylar666 on 2011-12-06
Well, Im back again  Sound issues were solved at ubuntu 10.04 bay using pavucontrol (pulseaudio audio manager) EVERY time I reboot the machine, just mutting and unmutting outpout audio.  My machine is still the same (hardware), Im trying to move to kernel 3.0xxx and have tried Ubuntu 11.10 and Linux Mint.   The thing is I still have to use this "trick" to make sound works, but after a while (no consistent amount of time) sound dissapears and I have to reboot to have sound again.  Im still comfortable at my 10.04 machine, but Im looking to move on to newer distros.   ¿Any ideas?

---

### Post by sylar666 on 2011-12-07
Well, Ive found this, new trick, now Ive to add to pulseaudio at start this terminal command everytime I lose sound

```
killall pulseaudio; sudo rmmod snd-hda-intel; sudo modprobe snd-hda-intel
```

Found here

[http://ubuntuforums.org/showthread.php?t=1758927](http://ubuntuforums.org/showthread.php?t=1758927)

---

### Post by sylar666 on 2012-01-15
Any new ideas about this, for sure problem is new kernel management of HDMI audio, oder kernels work just fine.

---

### Post by sylar666 on 2012-05-27
12.04 still have the same issues, its quite annoying. 
Sometimes Im seeing a video with vlc, or listening music audio just disappears when I pause, I have to mute/unmute, open terminal, alsamixer, redo everything if it doesnt works...

Why 10.04 was so easy, just muting/unmutting at system start 0 problems and this is so painfull?

I opened an Ask Ubuntu issue, but this issue doesnt have to make special attention

[http://askubuntu.com/questions/119809/hdmi-audio-problem](http://askubuntu.com/questions/119809/hdmi-audio-problem)

Please some guru help¡¡¡
XD

---

