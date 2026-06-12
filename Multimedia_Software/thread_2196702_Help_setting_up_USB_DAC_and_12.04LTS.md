---
title: "Help setting up USB DAC and 12.04LTS"
date: 2013-12-30
forum: Multimedia Software
---

### Post by tbone3421 on 2013-12-30
I've been reading and searching the forums and found lots of good information, and I really hoping someone can suggest something new for me to check/inspect/fix.  First of all:  The goal is to use a Schiit Audio USB DAC to connect to a headphone amp, but I can't get Ubuntu to play through the USB DAC.  It would be ideal to use the built in soundcard sometimes if I want to play music on my plain computer speakers through the mini-jack outpout, but mainly I want to use the USB DAC  I found this thread, but no answers:
[http://ubuntuforums.org/showthread.php?t=2155168&highlight=usb+dac+modi](http://ubuntuforums.org/showthread.php?t=2155168&highlight=usb+dac+modi)

Also, from reading other threads, I see that I can detect the DAC on card 1, device 0:
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Device [Schiit USB Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I've tried adding/removing PulseAudio too.  If PulseAudio is present and the USB DAC is plugged in, then the Settings->Sound->Output list is empty.  I removed PulseAudio and now the Output list shows the built-in audio stuff, but nothing specific to the Schiit DAC.  If I run lsusb, then:

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 1058:1110 Western Digital Technologies, Inc. 
Bus 001 Device 003: ID 0d8c:1319 C-Media Electronics, Inc. 
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 005: ID 0a5c:217d Broadcom Corp. 
Bus 002 Device 003: ID 413c:2107 Dell Computer Corp. 
Bus 002 Device 004: ID 0461:4dd6 Primax Electronics, Ltd 

and it appears to be missing here too.    I also tried selecting the Schiit USB DAC in alsamixer, but it doesn't seem to change anything.  I'm not sure what else to do or where else to look.    Thank you for any suggestions.

---

### Post by tgalati4 on 2013-12-31
Your hardware is not being detected.  Perhaps your DAC dongle is not working.  Try it on another port, then on another machine.  And, no I will not say that your dongle took a ****.

Right after you plug it in:

```
dmesg | tail -40
```

Only paste the DAC-related error messages.

A Haiku:

No sound, no Schiit.  Really.
Sound hardware not detected.
Bad port or dongle?

---

### Post by tbone3421 on 2013-12-31
Thank you for the advice.  I tried it on another port and immediately checked dmesg:

[81462.446224] usb 2-1.6: new high-speed USB device number 5 using ehci_hcd
[81462.556949] input: Schiit Schiit USB Audio Device as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/input/input19
[81462.557132] generic-usb 0003:0D8C:1319.0009: input,hidraw4: USB HID v1.00 Device [Schiit Schiit USB Audio Device] on usb-0000:00:1d.0-1.6/input2

Does this not imply that the device is detected?  I'm not sure how to proceed, so thank you for any suggestion.

---

### Post by tgalati4 on 2013-12-31
So your hardware is being detected.  That is the Schiit. (That is good.)

Open a terminal, install the following:

```
sudo apt-get install pavucontrol pavumeter paprefs
```

Now run them:

```
paprefs
pavumeter
pavucontrol
```

There is a setting in paprefs:  "Simultaneous Output" -- Check "Add virtual output for all sound cards".

That should wake up all of your sound devices so that you get output on all channels.

The other two apps allow you to control levels (make sure your channels are unmuted).

---

### Post by tbone3421 on 2014-01-01
Thank you so much for your help.  I ended up solving the problem inadvertently:  I had been meaning to upgrade from 12.04 to 12.10, so last night I ran the standard distribution upgrade through Upgrade Manager and voila! When I rebooted, the USB DAC was recognized in the Settings->Sound->Output list.  Thank you again for your help diagnosing the problem.  I'm curious why it decided to work all of a sudden, in case it ever disappears from the list.  Happy New Year!

---

### Post by tgalati4 on 2014-01-01
The graphical dialogs to select things--like the sound card in the output list simply write the settings to a settings or configuration file.  If that file gets mangled or written incorrectly, then stuff doesn't work.  So the update fixed the problem, perhaps by rewriting the configuration files.  Sometimes removable/USB hardware can change settings because they are hot-swap--they can be disconnected at any time, but the configuration files don't get changed if you simply change ports.

So remember what port you used when you set up the sound card, because that is what is written to the sound configuration file.  If you change it, there is a good chance it will not work without editing that file.

---

### Post by tbone3421 on 2014-01-01
That makes sense.  If I switch ports and the config files become garbled, then I should inspect the sound configuration file (perhaps:  /etc/pulse/client.conf ? )

---

### Post by tgalati4 on 2014-01-01
If you look at your /etc/pulse/client.conf file, it has some simple, generic pulse settings.  You need to look for ~/.asoundrc or /etc/asound.conf for special alsa configurations.  Run *alsamixer* to see how to change settings.  Also:  [http://askubuntu.com/questions/50067/howto-save-alsamixer-settings](http://askubuntu.com/questions/50067/howto-save-alsamixer-settings)

---

### Post by jatindevani9586 on 2014-01-01
How can I Enable Idea netsetter e1550 in usb 3.0 ??. my ubuntu version is 12.04 LTS

---

