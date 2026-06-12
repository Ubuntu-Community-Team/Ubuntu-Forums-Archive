---
title: "Ekiga -- No V4L2 Plugin Available ?!?"
date: 2007-09-02
forum: Multimedia &amp; Video
---

### Post by mbsullivan on 2007-09-02
Hi All,

I have a Logitech Pro 5000 which I am trying to get working under Linux.  According to multiple sources, this webcam only will operate under uvcvideo (which is V4L2 only).  Ekiga (versions > 2.0.4) are supposed to support V4L2 and should work with the Logitech Pro 5000.  [here]("(such as [URL="http://ubuntuforums.org/showthread.php?t=118517"))"]This[/URL] source illustrates that, and many others have verified this.  However, when I start ekiga, the V4L2 plugin never loads for me!  Ekiga seems to detect the device (incorrectly) as V4L, and then errors out when I try and capture video.

I've gotten uvcvideo compiled, built, and loaded.  I can capture video using luvcview, and everything seems to be okay (driver-wise).  Here is the output of my dmesg when I plug the device in:

```
[  814.332000] usb 5-3: new high speed USB device using ehci_hcd and address 4
[  814.596000] usb 5-3: configuration #1 chosen from 1 choice
[  814.596000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ce)

```

I have the newest version of ekiga installed:

```
username@hostname:~$ ekiga --version
GNOME ekiga 2.0.9

```

Starting ekiga (with -d 4 debugging enabled) gives the following output:

```
username@hostname:~$ ekiga -d 4
2007/09/02 20:26:57.213   0:01.013                        ekiga Detected audio plugins: ALSA
**2007/09/02 20:26:57.213   0:01.013                        ekiga Detected video plugins: Picture,V4L**
2007/09/02 20:26:57.213   0:01.013                        ekiga Detected audio plugins: ALSA
**2007/09/02 20:26:57.213   0:01.013                        ekiga Detected video plugins: Picture,V4L**
2007/09/02 20:26:58.065   0:01.865                        ekiga Detected the following audio input devices: Default,HDA Intel,USB Device 0x46d:0x8ce with plugin ALSA
2007/09/02 20:26:58.066   0:01.866                        ekiga Detected the following audio output devices: Default,HDA Intel with plugin ALSA
**2007/09/02 20:26:58.066   0:01.866                        ekiga Detected the following video input devices: UVC Camera (046d:08ce) with plugin V4L**
2007/09/02 20:26:58.067   0:01.867                        ekiga Detected the following audio input devices: Default,HDA Intel,USB Device 0x46d:0x8ce with plugin ALSA
2007/09/02 20:26:58.068   0:01.868                        ekiga Detected the following audio output devices: Default,HDA Intel with plugin ALSA
**2007/09/02 20:26:58.068   0:01.868                        ekiga Detected the following video input devices: UVC Camera (046d:08ce) with plugin V4L**
2007/09/02 20:26:58.076   0:01.876                        ekiga AVAHI   Failed to create client: Daemon not running
2007/09/02 20:26:58.473   0:02.274                        ekiga Ekiga version 2.0.9
2007/09/02 20:26:58.474   0:02.274                        ekiga OPAL version 2.2.8
2007/09/02 20:26:58.474   0:02.274                        ekiga PWLIB version 1.10.7
2007/09/02 20:26:58.474   0:02.274                        ekiga GNOME support enabled
2007/09/02 20:26:58.474   0:02.274                        ekiga Fullscreen support enabled
2007/09/02 20:26:58.474   0:02.274                        ekiga DBUS support enabled
2007/09/02 20:26:58.481   0:02.281                        ekiga Set TCP port range to 30000:30010
2007/09/02 20:26:58.482   0:02.282                        ekiga Set RTP port range to 5000:5059
2007/09/02 20:26:58.484   0:02.284                        ekiga Set UDP port range to 5060:5100
2007/09/02 20:26:58.485   0:02.285                        ekiga OpalEP  Created endpoint: h323
2007/09/02 20:26:58.486   0:02.286                        ekiga H323    Created endpoint.
2007/09/02 20:26:58.486   0:02.286                        ekiga OpalMan Added route "pc:.*=h323:<da>"
2007/09/02 20:26:58.487   0:02.287                        ekiga OpalEP  Created endpoint: sip
2007/09/02 20:26:58.487   0:02.287                        ekiga SIP     Created endpoint.
2007/09/02 20:26:58.488   0:02.288                        ekiga OpalMan Added route "pc:.*=sip:<da>"
2007/09/02 20:26:58.488   0:02.288                        ekiga OpalEP  Created endpoint: pc
2007/09/02 20:26:58.489   0:02.289                        ekiga PCSS    Created PC sound system endpoint.
2007/09/02 20:26:58.490   0:02.290                        ekiga OpalMan Added route "h323:.*=pc:<da>"
2007/09/02 20:26:58.490   0:02.290                        ekiga OpalMan Added route "sip:.*=pc:<da>"
2007/09/02 20:26:59.052   0:02.852        Opal Listener:8440150 Listen  Started listening thread on tcp$172.16.83.1:1720
2007/09/02 20:26:59.053   0:02.853        Opal Listener:8440150 Listen  Waiting on socket accept on tcp$172.16.83.1:1720
2007/09/02 20:26:59.055   0:02.855                        ekiga AVAHI   Error initializing Avahi: %sDaemon not running
2007/09/02 20:26:59.056   0:02.856        Opal Listener:833e888 Listen  Started listening thread on udp$172.16.83.1:5060
2007/09/02 20:26:59.057   0:02.857        Opal Listener:833e888 Listen  Waiting on UDP packet on udp$172.16.83.1:5060

```

Where's my V4L2 plugin? Nobody else seems to require any special configuration!  Does anybody know what is going on, and how I could get my webcam to work with ekiga?

Thank you,
Mike

---

### Post by mbsullivan on 2007-09-02
As soon as I post, I figure it out... it's a conflict with some older webcam drivers, and a product of the fact that I'm working off of a server install.

I needed to install the V4L2 plugin (duh!)... I did so with the following command:

```
sudo aptitude install -t gutsy libpt-plugins-v4l libpt-plugins-v4l2 libpt-plugins-avc libpt-plugins-dc
```

I hope this helps anybody who runs into this problem! 

Mike

---

