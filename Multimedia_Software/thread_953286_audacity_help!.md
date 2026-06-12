---
title: "audacity help!"
date: 2008-10-20
forum: Multimedia Software
---

### Post by wanichan on 2008-10-20
I can't get audacity to record or play back. 

I've googled around and although this is a common problem, none of the suggested fixes work.

I've tried compiling the latest version of audacity 1.3.5 from source, but then the only available i/o devices are oss dev/dsp which doesn't do anything.

When I use the repository version it gives me more choices for the i/o devices but then whatever I select I get the:

"Error while opening sound device. Please check the output device settings and the project sample rate."

error. 

I've tried installing and uninstalling Jackd to no avail, ditto with pulseaudio.

Utterly stooped. :confused:

Any suggestions??

FYI I'm using hardy heron 8.04 and lspci yields:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

---

### Post by markbuntu on 2008-10-20
If you are serious about recording, you should use ardour and jackd.

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

If you are wondering how to sync applications together through jack. 

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

Audacity is incapable of providing the easy use and control of real jack applications working together.

---

### Post by wanichan on 2008-10-21
Thanks for the suggestion. Yeah, I'm in the process of teaching myself Ardour and the JACK stuff. Sigh.

I started relying on audacity in my xp days. I found it quite idiot proof there and thought it would be on ubuntu too. I'm kind of surprised at how much less usable audacity is in linux.

---

### Post by Johny_123 on 2008-10-21
:KS:KS

Good!

---

### Post by markbuntu on 2008-10-21
The basic problem with audacity in linux is that it was written to use the portaudio sound server which is no longer used. The oss and alsa and jack plugins that audacity uses are buggy and at least 3 years old and have not been corrected or updated at all in that time. 

Maybe you should be asking the audacity developers what's up with that.

---

### Post by Zimmer on 2008-10-22
To use audacity stop the jackd server running, it probably starts every time you start Ubuntu.
Use the System Monitor to find it and kill the process. Audacity will then get control.....

Check the ALSA Volume/mixer control settings are ok. In the Recording tab that capture is not muted and the sliders are up.
and the Options tab, that a valid input source is selected...  mic  is a good one :)  my laptop shows mic and Front mic, the Front mic appears to be the built in microphones by the webcam and mic is the socket at the front of the laptop (?)

If you cannot see some of these settings on your mixer GUI then click Edit>Preferences and enable them there..

---

### Post by fedemw on 2008-10-24
I solved this issue with Audacity and Ubuntu 8.04 (this problem applies to older instalations too).

"Error while opening sound device. Please check the output device settings and the project sample rate."

1) sudo apt-get remove audacity

2) Download audacity 1.3.5 beta

Sources:
[http://audacity.sourceforge.net/download/](http://audacity.sourceforge.net/download/)
[http://ftp.heanet.ie/mirrors/www.getdeb.net/getdeb/ubuntu/hardy/au/audacity_1.3.5-1~getdeb1_i386.deb](http://ftp.heanet.ie/mirrors/www.getdeb.net/getdeb/ubuntu/hardy/au/audacity_1.3.5-1~getdeb1_i386.deb)

3) In the download folder, exec:

sudo dpkg -i audacity_1.3.5-1~getdeb1_i386.deb 


4) Execute and enjoy!
:popcorn:

---

### Post by wanichan on 2008-10-31
> **fedemw said:**
> I solved this issue with Audacity and Ubuntu 8.04 (this problem applies to older instalations too).

"Error while opening sound device. Please check the output device settings and the project sample rate."

1) sudo apt-get remove audacity

2) Download audacity 1.3.5 beta

Sources:
[http://audacity.sourceforge.net/download/](http://audacity.sourceforge.net/download/)
[http://ftp.heanet.ie/mirrors/www.getdeb.net/getdeb/ubuntu/hardy/au/audacity_1.3.5-1~getdeb1_i386.deb](http://ftp.heanet.ie/mirrors/www.getdeb.net/getdeb/ubuntu/hardy/au/audacity_1.3.5-1~getdeb1_i386.deb)

3) In the download folder, exec:

sudo dpkg -i audacity_1.3.5-1~getdeb1_i386.deb 


4) Execute and enjoy!
:popcorn:

K got that up and running, now it records and plays back without error message.

However, I can't hear audio when I press play. where'd the sound go? volume is maxed, and audio works fine on e.g. youtube.

grrr so close yet so far.

---

### Post by wanichan on 2008-10-31
weird went to edit->preferences 

put playback and recording on same device and now I get sound...That did the trick, but now I can't play audio in my browser (e.g. youtube).

---

### Post by Skipnaz on 2008-11-23
I use to get the "Error while opening sound device. Please check the output device settings and the project sample rate" popup when recording from Youtube. I'd play a Youtube clip and then press Record button to start recording the audio portion in Audacity
My workaround to prevent the error popup
Always open Audacity before opening Youtube webpage then visit Youtube and record the clip
The trick is to close all Youtube webpages first before you press the Playback button
Audio now plays back without the error popup. For some reason it needs that disconnect
I did not save as a project either. At least it works for me in Ubuntu 8.04
Old Emachine T3085 onboard chip
There are some settings in Multimedia Systems Selector. In Terminal type: gstreamer-properties
Both my boxes are set to ALSA

---

