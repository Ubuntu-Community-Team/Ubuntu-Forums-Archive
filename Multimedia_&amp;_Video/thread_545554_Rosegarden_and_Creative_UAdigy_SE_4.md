---
title: "Rosegarden and Creative UAdigy SE 4"
date: 2007-09-07
forum: Multimedia &amp; Video
---

### Post by Echo35 on 2007-09-07
I installed Rosegarden through synaptic, but I'm running into a bunch of problems.  I'm using a Creative sound card with OSS loaded, but that's all I know of that I have. Whenever I try running the program I get an error:

"System Timer resolution Too Low"

Is there anyway to fix this? Also, here is my sound output code:

Rosegarden 1.4.0 - AlsaDriver - alsa-lib version 1.0.13

JackDriver::initialiseAudio - JACK server not running

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)            (DUPLEX) [ctype 2, ptype 655362, cap 99]
    16,0 - (CA0106, CA0106 MPU-401 (UART))            (DUPLEX) [ctype 2, ptype 589826, cap 127]

Creating device 0 in Play mode for connection 16:0 CA0106 MPU-401 (UART) (duplex)
Default device name for this device is MIDI external device
Creating device 1 in Record mode for connection 16:0 CA0106 MPU-401 (UART) (duplex)
Default device name for this device is MIDI hardware input device
Creating device 2 in Play mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI output system device
Creating device 3 in Record mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI input system device
System timer is only 250Hz, sending a warning
    Current timer set to "system timer"
    WARNING: using system timer with only 250Hz resolution!
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

System timer is only 250Hz, sending a warning
    Current timer set to "system timer"
    WARNING: using system timer with only 250Hz resolution!
AlsaDriver::setRecordDevice - successfully subscribed device 1 as record port

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)            (DUPLEX) [ctype 2, ptype 655362, cap 99]
    16,0 - (CA0106, CA0106 MPU-401 (UART))            (DUPLEX) [ctype 2, ptype 589826, cap 127]

AlsaDriver::setRecordDevice - 255:255 failed to subscribe device 3 as record port

---

### Post by Co.Sinecure on 2007-09-07
I think the only way to fix this is to use a low-latency kernel, either by installing/upgrading to UbuntuStudio or installing the low-latency kernel via synaptic (you may need the ubuntustudio repos to do this)

[http://ubuntustudio.org/]("http://ubuntustudio.org/")

---

### Post by Jaaxx on 2007-09-07
From the Ubuntu Studio Wiki:

Timer Resolution

The Ubuntu kernel currently is set to 250Hz timers, which is insufficient for MIDI. We can correct this:

 sudo sysctl -w dev.rtc.max-user-freq=1024

To make it persistent across reboots, you need to add a line to the /etc/sysctl.conf file.

 sudo su -c 'echo dev.rtc.max-user-freq=1024 >> /etc/sysctl.conf'

This guy [WWW] [http://tapas.affenbande.org/wordpress/?page_id=40](http://tapas.affenbande.org/wordpress/?page_id=40) even recommends setting the max-user-freq to 8192. He claims that he is achieving latencies <1ms with stable zero xruns There may be other useful information on this page.

---

### Post by Echo35 on 2007-09-07
I installed StudioUbuntu, but now I get no audio output :???:

---

