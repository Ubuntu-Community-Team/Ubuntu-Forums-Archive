---
title: "Problems with Intel HDA 5 Series audio"
date: 2010-01-31
forum: Multimedia Software
---

### Post by defaria on 2010-01-31
I recently received my new multimedia laptop - an [HP Dv7]("http://www.shopping.hp.com/series/category/notebooks/dv7tqe_series/3/computer_store?jumpid=reg_R1002_USEN"). I proceeded to install Ubuntu 9.10 on it and I've had no end of troubles with the sound card including, muffled sound - seemingly only coming from the LFE channel, only stereo controls in pavucontrol, failure to send sound out the HDMI port, headphones not working and not cutting of the speakers when the headphones are plugged in. I believe that all of this will be solved if I get the appropriate driver for my card. I have searched around and sound in particular has tons of posts from many people all with slightly different problems, solutions and hardware. None of the solutions seem to be working. 

Also I just tried booting from the live CD and the sound is the same - no 5.1 and just muffled sound.

I'm hoping somebody with a similar sound card/set up can help me. I think my sound card is just too new and there doesn't exist a proper driver for it yet. Here's what I get with lscpi:

```

% lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)

```

Let me know if there is any other information that I can provide.

---

### Post by mepuka on 2010-02-01
Hi, try [this]("http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/"). I've been struggling to get my sound to work on my Intel HDA ICH9. At least you have some sound.  :icon_frown:

---

### Post by defaria on 2010-02-01
I did see that. It seems pretty intense. I see you say "try" this and that you don't have any sound. Given that I must ask, why do you think I should try it? I mean it seems like a lot of effort and you don't even seem to be sure it'll fix things for me.

As for you, you get no sound at all? What happens if you boot from the Live CD? Still no sound?

---

### Post by defaria on 2010-02-01
Well that actually did good! I can now here at least stereo.

Pro: Sound now playing stereo
Con: Not 5.1

Pro: Headphones now work!
Con: Plugging in headphones does not turn of speakers! :-(

Con: HDMI still does not have sound associated with it. So when I plug my laptop into an HDMI cable to my HDTV I don't hear sound coming from my Bose Home Theater system - just from the laptop.

Con: Bluetooth has now busted. In the past I could use my Bluetooth Headset to listen to content playing on the laptop - even in stereo! Now I get nothing. I suspect that this is because I have the pulseaudio-module-bluetooth verion 1.0.9.19. Perhaps I need to build that too.

As it stands now I cannot use my laptop on the bus to say watch a video because the sound will bother everybody else. I can't listen to it with my headphones because it still plays out the speakers and I can't use my bluetooth headset because that doesn't work. And I still can't use it to drive my HDTV viewing yet...

Any other ideas?

---

### Post by lidex on 2010-05-02
You guys need to make sure you're using 1.0.23 alsa:
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2]("http://ubuntuforums.org/showpost.php?p=9136618&postcount=2")

More stuff:
[http://forum.xbmc.org/showthread.php?t=59877]("http://forum.xbmc.org/showthread.php?t=59877")
[http://ubuntuforums.org/showthread.php?p=9220267#post9220267]("http://ubuntuforums.org/showthread.php?p=9220267#post9220267")

---

### Post by defaria on 2010-05-02
> **lidex said:**
> You guys need to make sure you're using 1.0.23 alsa:
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2]("http://ubuntuforums.org/showpost.php?p=9136618&postcount=2")

Please don't do this. Don't point us to some 51 pages of forum postings going on and on about various different things. You mention updating to 1.0.23 yet if one clicks that link it doesn't tell us at all how to do that. It's spits out verbiage about 1.0.23 then points to a forum entry with 51 pages that starts off about ALSA 1.0.22 - not 1.0.23. This gets nobody nowhere fast.

> More stuff:
[http://forum.xbmc.org/showthread.php?t=59877]("http://forum.xbmc.org/showthread.php?t=59877")

Likewise this thread's a dead end because they state up front and emphatically "IMPORTANT: the 190 series driver breaks ipcm hdmi output totally or partially". I have an HP laptop. Prior to the 190 series of Nvidia drivers suspending the laptop would cause the X server to display things so fuzzy that it was impossible to use. Sorry, I can't go backwards to 185 - it plain just doesn't work!

> [http://ubuntuforums.org/showthread.php?p=9220267#post9220267]("http://ubuntuforums.org/showthread.php?p=9220267#post9220267")

LIkewise this didn't work at all either...

---

### Post by lidex on 2010-05-02
> **defaria said:**
> Please don't do this. Don't point us to some 51 pages of forum postings going on and on about various different things. You mention updating to 1.0.23 yet if one clicks that link it doesn't tell us at all how to do that. It's spits out verbiage about 1.0.23 then points to a forum entry with 51 pages that starts off about ALSA 1.0.22 - not 1.0.23. This gets nobody nowhere fast.

Funny, more than a few individuals have managed to upgrade to 1.0.23 using that info. Sorry you couldn't figure it out.

---

### Post by defaria on 2010-05-02
Oh I could figure it out given some time - but why should I? Wouldn't it be a hellofa lot better if you just pointed me directly to the information instead of making me wade through it? That's my point, that you obviously missed....

Sorry, obvious expression of frustration. It just should not be this hard to get simply functionality working. A little calmer now, a pointer to where to get 1.0.23 would be appreciated. I'm currently on 1.0.22.1. What does 1.0.23 fix/bring in? Is there an HDMI fix in there? That'd be great!

OK so I downloaded, compiled and installed 1.0.23. Observations:

. Why is it whenever I need to recompile my kernel it falls flat on it's face until I cd /usr/src/linux-headers<current version>-generic/arch and then ln -s x86 linux?
. HDMI doesn't work at all. Same as before - nothing comes out. Also I have two HDMIs one that says HDA Nvidia and one that say HDA Nvidia Digital Stereo. Neither work.
. If I start pavucontrol and go to Output attempting to change the output of say VLC playing a movie I had to hit the button several times before it will post the menu and I can attempt to switch from Internal Stereo Duplex to one of the HDA Nvidia modes. Why is that? It's a simply menu popup!
. Adjusting the volume on the speaker icon or with the volume control on my laptop no longer works. Also, when I lower the volume to zero it used to change the little blue light on my laptop to a reddish orange indicating mute. This broke too.
. Trying to use gnome-alsamixer to play with the settings reveals a Nvidia 220 tab but my Nvidia is 230.
. Even tried reverting back to the Nvidia display driver 185 (Normally I'm on 195 due to an X display bug which renders suspend model totally useless on the laptop as it comes back so fuzzy that you need to reboot). Switching to 185 to test out HDMI output - no difference, still nothing comes over the HDMI wire.
. Why is it when you hibernate your system when playing a moving from say VLC then come back from hibernation, VLC is terminated?

---

### Post by Earth_Quake on 2010-05-05
Hello all. :)

I have  a problem, it works with audio and HDMI output, but when I connect  headphones to it, "said the speaker.
Laptop: Asus K52j  Link:

```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
05:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
05:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
05:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 80)
05:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```I  installed the alsa package is 1.0.23, but nothing changes.

My sound config file 
```

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel

```

Thank you  :)

---

### Post by godjil on 2012-01-26
update to 1.0.25

sudo /sbin/alsa-utils stop
sudo apt-get -y install build-essential ncurses-dev gettext xmlto libasound2-dev linux-headers-`uname -r` libncursesw5-dev

cd ~
rm -rf ~/alsa* ~/.pulse*
wget [ftp://ftp.alsa-project.org/pub/driver/a](ftp://ftp.alsa-project.org/pub/driver/a) … 25.tar.bz2
wget [ftp://ftp.alsa-project.org/pub/lib/alsa](ftp://ftp.alsa-project.org/pub/lib/alsa) … 25.tar.bz2
wget [ftp://ftp.alsa-project.org/pub/utils/al](ftp://ftp.alsa-project.org/pub/utils/al) … 25.tar.bz2

sudo rm -rf /usr/src/alsa
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/alsa* .

sudo tar xjf alsa-driver-1.0.25.tar.bz2
sudo tar xjf alsa-lib-1.0.25.tar.bz2
sudo tar xjf alsa-utils-1.0.25.tar.bz2

cd alsa-driver*
sudo ./configure
sudo make V=99
sudo make install V=99

cd ../alsa-utils*
sudo ./configure
sudo make V=99
sudo make install V=99

rm -f ~/alsa-driver*
rm -f ~/alsa-lib*
rm -f ~/alsa-utils*

sudo reboot

sudo alsaconf - allways YES

sudo reboot

---

### Post by defaria on 2012-01-26
Why doesn't this just come with the OS like all the other software? Why must I do anything different or special?

---

### Post by kenoby31 on 2012-02-17
Work fine for me


 [http://alegnalinux.blogspot.com/2012/02/sin-sonido-en-ubuntu-10x-11x-int...]("http://alegnalinux.blogspot.com/2012/02/sin-sonido-en-ubuntu-10x-11x-intel-hda.html")
 



Best regards

---

