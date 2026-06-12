---
title: "HOWTO: Install OSS4 in Lucid for better sound quality"
date: 2010-08-26
forum: Multimedia Software
---

### Post by levien on 2010-08-26
After upgrading to Lucid I was happy to find that sound finally seemed to work in all applications, but rather appalled at its quality (and the CPU-load of Pulseaudio). So I finally decided to give the OSS4 audio-drivers a try (after having audiophile friends recommend them to me for ages ;)). 

The various instructions that I found online are mostly for older versions of Ubuntu, and make the installation seem quite a hassle. But in fact, installation turned out to be not that difficult, and I think the resulting improvement in sound quality was well worth it! So I put detailed instructions on [my site]("http://levien.zonnetjes.net/?q=oss4"), but these turn out to be difficult to find with Google. And as these instructions may be useful for people here as well, here's how to do it:

[LIST]In a terminal, run ```
sudo dpkg-reconfigure linux-sound-base
```
Choose OSS. This should, among other things, prevent the ALSA modules from loading. Reboot.[/LIST]

[LIST]There are (at least) three ways to install OSS4:

[LIST]Install from the Ubuntu repositories: 
```
sudo apt-get install oss4-base oss4-dkms oss4-source oss4-gtk
```
This will automatically rebuild the OSS modules when your kernel is updated, and is the preferred way of installing third-party kernel modules. However, the oss4-dkms package is currently broken for Ubuntu ([bug #519577]("https://bugs.launchpad.net/ubuntu/+source/oss4/+bug/519577")), so for the time being use the package from the Opensound website (recommended, see below) or [from this PPA]("https://launchpad.net/~sevenmachines/+archive/release+1") (not recommended as it currently breaks sound in the Adobe Flash plugin). [/LIST]
[LIST]Download the OSS4 binaries as a DEB package from [http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi) and install it. This is currently the easiest way, but you'll manually need to reinstall the package every time your kernel is updated. Also, this package is not GPL but has a commercial one-year license.[/LIST]
[LIST]Fetch the source from the Mercurial repository and compile the package yourself, as described in [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound) 
This will give you the latest GPL-version of the drivers.[/LIST]
[/LIST]

[LIST]If you get errors about snd_pcm being in use, try rebooting and running ```
sudo soundon
``` If the problem persists, use [FONT="Courier New"]lsmod[/FONT] to check if any ALSA modules are still loaded. If so, blacklist them manually. For instance, I had to blacklist the [FONT="Courier New"]saa7134_alsa module[/FONT] by creating a configuration file [FONT="Courier New"]/etc/modprobe.d/blacklist-saa7134_alsa.conf[/FONT] with the line ```
blacklist saa7134_alsa
```[/LIST]

[LIST]Either configure Pulseaudio to use OSS4 or remove it altogether.

[LIST]To configure Pulseaudio with OSS4:
Edit the default configuration file: ```
gksu gedit /etc/pulse/default.pa
```
Comment out the modules for automatic hardware detection.
Add the following line: ```
load-module module-oss device="/dev/dsp" sink_name=output source_name=input mmap=0
```
[/LIST]
[LIST]To remove Pulseaudio (recommended):
```
sudo apt-get remove pulseaudio
```
Note that this will remove the volume manager icon from your panel.
[/LIST]

[/LIST]

[LIST]Configure Gstreamer for OSS4 output:
Install the package [FONT="Courier New"]gstreamer0.10-plugins-bad[/FONT]
Run the command [FONT="Courier New"]gstreamer-properties[/FONT] and set input and output to OSS.
[/LIST]

[LIST]Add [FONT="Courier New"]ppa:dtl131/ppa[/FONT] to your Software Sources and run update-manager.
The packages from [this PPA]("https://launchpad.net/~dtl131/+archive/ppa") will enable Gnome audio output and volume management to use Gstreamer instead of Pulseaudio. [/LIST]

[LIST]Right-click over your panel, select "Add to panel" and add the volume control applet. Alternatively, you can add a button to your panel or menu to start the OSS4 mixer ([FONT="Courier New"]/usr/bin/ossxmix[/FONT]) instead of the normal Gnome volume manager.[/LIST]

[LIST]Start [FONT="Courier New"]gconf-editor[/FONT]. Open [FONT="Courier New"]system/gstreamer/0.10/audio/default[/FONT]. The keys [FONT="Courier New"]musicaudiosink[/FONT] and [FONT="Courier New"]chataudiosink[/FONT] are probably still set to "pulsesink". If so, change them to "osssink". This will switch applications such as Rhythmbox, Movie Player and Skype to OSS output.[/LIST] 

[LIST]Set up ALSA (or rather libasound) to output through OSS4 instead of the native ALSA drivers. Create a configuration file: ```
gedit ~/.asoundrc
```
Insert the following:

```

 pcm.!default
 {
   type oss
   device /dev/dsp
 }
 mixer.!default
 {
   type oss
   device /dev/dsp
 }


```
[/LIST] 

[LIST]Configure applications that natively support it (e.g. Audacious, Audacity, Kdenlive, SMPlayer, VLC, Wine, etc.) to [use OSS output]("http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4"). Many applications don't (or no longer) have native support for OSS. This is no problem, these should continue to work fine through Gstreamer or ALSA emulation (or Pulseaudio if you decide to keep it).[/LIST]

**References:**
[http://levien.zonnetjes.net/?q=oss4](http://levien.zonnetjes.net/?q=oss4)
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)
[http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html](http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html)

---

### Post by YavkatA on 2011-01-02
Thank you for the nice tutorial! Pleased to report that these instructions also work for up-to-date Maverick x64. I completely removed pulseaudio and sound mixing works with my on-board Intel card. Sweet!

---

### Post by floopy1962 on 2011-01-31
No sound at all... i don't have "/dev/dsp"

---

### Post by phredbull on 2011-01-31
Just curious, what kind of problems were you having w/ALSA, and how does this change affect system performance? I'm thinking of trying this because my sound is currently broken and I haven't a clue what the problem is...

---

