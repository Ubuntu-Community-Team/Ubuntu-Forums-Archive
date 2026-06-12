---
title: "Using a webcam for surveilliance?"
date: 2006-12-16
forum: Multimedia &amp; Video
---

### Post by stoiss on 2006-12-16
Hi,

I have a small server (no X server) running Ubuntu Dapper.

I've been tinkering with the idea of using it for surveillance at my home by connecting it to a standard webcam with motion detection.

I know getting a webcam to work under Linux can be a tricky business, so I was wondering if anyone can recommend me:

[LIST=1]
[*]A relatively cheap webcam with 1024x768 or higher resolution for still pictures, that works with Ubuntu.*
[*]An application/framework which will run as a daemon and generate a mail with still pictures whenever the motion detector on the webcam is triggered.
[/LIST]
*I found [this thread](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras) with *compatible* webcams, but I would like some personal opinions from other Ubuntu users before I head for the store;)

Cheers!

/stoiss

---

### Post by stoiss on 2006-12-16
To begin with I have found these applications that could be useful

[Motion](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)

[ZoneMinder](http://www.zoneminder.com/)

Where the later is the more feature rich with a webfrontend as well as the option of notification via mail or sms.

This still leaves me with the choice of webcam. Any suggestions?

---

### Post by Mike'sHardLinux on 2006-12-16
Hi. I just wanted to make a suggestion. On ebay, you can find generic 4-input video capture cards for less than $30 usually. They have bnc inputs, but it's basically a composite video input with a different connector. I haven't set one up with Ubuntu, only Redhat (older versions) and Fedora, but as far as I know, the chip it's based on is supported in the current Linux kernel, so Ubuntu should also support it out of the box. I believe it's based on the BT878 chip. Anyway, If you get that, you can get any typical video camera that has composite output. They are often pretty cheap, at least for a  black and white camera.

Only thing is, the cheaper cards either have no audio, or only 1 audio input. I didn't need audio for my application.

Here is an example of one of these cards: [http://cgi.ebay.com/New-4-Channel-CCTV-PCI-DVR-Linux-Video-Capture-Card_W0QQitemZ270066699592QQihZ017QQcategoryZ48634QQrdZ1QQcmdZViewItem]("http://cgi.ebay.com/New-4-Channel-CCTV-PCI-DVR-Linux-Video-Capture-Card_W0QQitemZ270066699592QQihZ017QQcategoryZ48634QQrdZ1QQcmdZViewItem")

Edit: I wanted to add that I use motion on one system, and VLC on another system. It was easier for to get motion working with multiple simultaneuos cameras. I still haven't figured out how to do it with VLC and VideoLan Manager. The thing is, with Motion, I had to use Motion to do the capture, and another program to do the streaming output. VLC does both in one program.

---

### Post by stoiss on 2006-12-16
Thanks for a quick reply :)

I probably should have added that the server is based on a via epia ve5000 motherboard crammed into the smallest case I could find. I'm afraid adding a card isn't an option as there simply isn't enough space :(

That's why I'm considering an USB webcam. It basically only needs to take still pictures of a fairly high quality for identification of intruders. Also, sound isn't a requirement.

A webcam that has these qualities and can be installed and work without too much fuzz on an Ubuntu installation would be the optimal solution.

---

