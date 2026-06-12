---
title: "No sound in Xubuntu. Sound OK on Vista"
date: 2012-08-10
forum: Multimedia Software
---

### Post by GuYem on 2012-08-10
Hello all, 

I'm new here and quite new in the Linux world. 
I own a Sony Vaio Laptop and had my systems installed by someone else. I have a Windows Vista OS that I never use and a Xubuntu that I always use.

Problem is that Windows has sound, while Xubuntu does not. My mixer says volume is not mute, apart from that I cant tell anything more : I dont know which sound card I own, not sure if Alsa is correctly installed etc...

Anyway, may someone help me fix this sound problem ? Here are some infos : 
- Xubuntu 10.04 LTS
- XFCE 4
- lspci gives the following information : 
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4381 (rev 11)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

---

### Post by daimaru on 2012-08-11
```
aplay -l
```
should list your audio devices.

simplest thing:
have you tried clicking the speaker symbols -> select sound settings
select the "playback tab" if a program is playing sound for example clementine it should be listed there. Next to the app name there is a drop down box where it says something like "build-in audio analog stereo" i for one have to change that to my output device (headset). maybe yours is listed there too. 

sorry don't know much more about this, but since nobody else has answered i wanted to give it a try.

---

### Post by 55tptag on 2012-08-11
I don't have an answer; only some notes on this.

Please review this Ubuntu Forum thread for troubleshooting audio, **[http://tinyurl.com/8sndtr9](http://tinyurl.com/8sndtr9)**

I see other people had similar devices as the ones you listed:
[I]**00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)** and [B]
01:00.1 Audio device: ATI Technologies Inc RV710/730[/B][/I]

It looks like some of those people found success by modifying the file, **/etc/modprobe.d/alsa-base.conf**

And, two posts about modifying that file:
**[http://community.linuxmint.com/hardware/view/1397](http://community.linuxmint.com/hardware/view/1397)**
**[http://tinyurl.com/clj5349](http://tinyurl.com/clj5349)**

Just want to add that you might want to try the program named PulseAudio Volume Control (**pavucontrol**) which is a simple GTK+ based volume
control tool (mixer) for the PulseAudio sound server.

Please provide the model number of your Sony Vaio as well.

---

### Post by GuYem on 2012-08-13
Hello, 

Thanks for your replies. Here is how it goes : 

* Clicking on the speaker symbols gives : 
```

GStreamer was unable to detect any sound devices. Some sound system specific GStreamer packages may be missing. It may also be a permissions problem.

```
Launching mixer or Gnome Alsa mixer gives the same.

* I followed the troubleshooting guide. The big command supposed to list all recognizes sound cards gave : 
```
Sound cards recognized by the system:
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
01:00.1 Audio device [0403]: ATI Technologies Inc RV710/730 [1002:aa38]
Sound cards recognized by ALSA:
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
01:00.1 Audio device [0403]: ATI Technologies Inc RV710/730 [1002:aa38]
Sound cards recognized by ALSA, and activated:
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
01:00.1 Audio device [0403]: ATI Technologies Inc RV710/730 [1002:aa38]

```
I think this is good.

* Then I ran the command fixing permission problem, this did not display anything, I rebooted as mentionned. Now aplay -l still gives : 
```
aplay: device_list:223: no soundcards found...

```

* I also tried to modify alsa-base.conf and creating modprobe.conf, no success either.

I must admit I dont really know what I am doing. Any help will be appreciated.

---

### Post by daimaru on 2012-08-14
try reinstalling gstreamer 
```
sudo apt-get remove --purge gstreamer0.10-alsa
sudo apt-get install gstreamer0.10-alsa

```

---

### Post by GuYem on 2012-11-18
Well, 

If this is of any help to someone, sound works now that I upgraded to 12.04 LTS. I did not have anything else to do.

---

