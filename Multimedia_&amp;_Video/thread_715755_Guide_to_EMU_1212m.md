---
title: "Guide to EMU 1212m"
date: 2008-03-05
forum: Multimedia &amp; Video
---

### Post by Eisenwinter on 2008-03-05
This is a HOWTO get sound working with ALSA, on EMU 1212m sound cards.

First, download the latest ALSA drivers (current latest version is 1.0.16).

Open up terminal (Applications -> Accessories -> Terminal) and type this:
```

**wget** [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)

**wget** [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2)

**wget** [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2)

**wget** [ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2)
```

This will create four new different archives inside your home folders.
Now, lets extract them.

In terminal, type this:
```
**tar -xf** alsa-driver-1.0.16.tar.bz2
tar -xf alsa-lib-1.0.16.tar.bz2
tar -xf alsa-firmware-1.0.16.tar.bz2
tar -xf alsa-utils-1.0.16.tar.bz2
```

This will uncompress them, and you will then see a folder, inside your home folder, with the name of the archive.

In order to install packages from source, you need to get the package **build-essential**, which installs compiler libraries and other programming and compiling utilities.
```
sudo apt-get install build-essential
```
You will be asked to type in your password, as installing packages using apt-get requires you to be root.

Now lets start installing.
First, ALSA-Driver.

```
cd alsa-driver-1.0.16
./configure --with-cards=emu10k1
make
make install
```

Let me explain what this does.
The **cd** commands goes into a directory, in our case, it's alsa-driver-1.0.16
**./configure** prepares the sources for installation, in here, we have also used a parameter saying --with-cards=emu10k1, which tells ALSA to include the driver for this card in the installation.
**make** compiles the sources.
**make install** installs the compiled sources.

Do the same for all other archives, and reboot your computer.

Open up terminal.
```
asoundconf list
```
This will list all the available sound cards now.

EMU 1010 should be listed, if it is, you can now play sounds with your Ubuntu system.
Now (for most users) another problem appears.
You get sound, but when you play music, it sounds faster than it should be, why is that?

This is caused because most music today is made on a sample rate of 44100, but our sound card configuration is set to a sample rate of 48000.

Open up terminal.
```
alsamixer
```
This will open up the Alsa Mixing tool.

Tune the volumes to your liking, and keep moving to the right with the arrow keys, until you reach Internal Rate Clock.
Change that from 48000 to 44100.
-------------------------------------------------

I hope this guide helps other Ubuntu users who have an EMU 1212m card, or any other card from the EMU series.
I've struggled with mine for quite a few hours until I finally found out what I needed to do.

If you wish to contribute to this guide, please do so.

I have just edited it, to make the commands clearer and easier to read.

---

### Post by c_wolf on 2008-03-21
Thank you! My 1212m now plays music :)

--

Here is a bit of extra information if someone gets stuck despite the guide. I tried above guide from a fresh Ubuntu 7.10 installation.

Package 1, 2 and 3 each compile all the same way as before mentioned.

[I]alsa-driver-1.0.16.tar.bz2
alsa-lib-1.0.16.tar.bz2
alsa-firmware-1.0.16.tar.bz2[/I]

But on my fresh Ubuntu 7.10 install, the 4th package:

**alsa-utils-1.0.16.tar.bz2**

..ran into a configuration error, complaining about 'libcurses',
so then I did:

sudo apt-get install libncurses5 libncurses5-dev

Also, after 'apting' the above stuff for the 4th package, 'make' failed to complete, whereas 'make install' worked fine. Not sure what that is about, but 'make install' gave no errors.

If you still get errors on the 4th package, also try installing gettext, sudo apt-get install gettext.

--

After rebooting, sound worked. If you use KDE 3 then kmixer, in stead of alsamixer, can also be used to set the internal clock to 44100.

If you use alsamixer to change it from 48000 to 44100, it does not save this after a reboot and you need to correct it manually again via alsamixer. Not sure how to get alsamixer to save changes you make it between reboots, but at least kmixer does this for me now and that works for me too.

:guitar:

---

### Post by lemmyc on 2008-04-04
If after all that, the EMU1212 doesn't appear as the default card in alsamixer, do this:

```
asoundconf set-default-card EMU1010
```

---

### Post by justin13 on 2008-04-05
well
for those of you who get bored sitting there watching things go when you cant even listen to anything.... here's the fast way:
sudo apt-get build-dep 
sudo apt-get build-dep alsa-lib alsa-utils alsa-firmware alsa-driver

now this will give you an error - but the point was to get the sudo pass into memory :> here comes the fun part:
sudo apt-get -y build-dep alsa-lib alsa-utils alsa-driver && cd /home/$USER/Desktop/alsa-driver-1.0.16 && ./configure --with-cards=emu10k1 && make && sudo make install && cd ../alsa-lib-1.0.16 && ./configure --with-cards=emu10k1 && make && sudo make install && cd ../alsa-firmware-1.0.16/ && ./configure --with-cards=emu10k1 && make && sudo make install && cd ../alsa-utils-1.0.16/ && ./configure --with-cards=emu10k1 && make && sudo make install

go ahead, have a cup of coffee.. 
in fact... ever notice how cup and cpu is similar? O:



oh yes
i recommend making a folder: 
mkdir /home/$USER/compiled
mv /home/$USER/Desktop/alsa*  /home/$USER/compiled
enjoi ^^

---

### Post by ytsestef on 2008-05-11
Does anyone knows if digital output (optical) works???

---

### Post by rat_poison on 2008-05-27
Hardy comes with 1.0.16 pre-installed. Is there anyway to avoid the messy ./configure stuff?

---

### Post by PeterGK on 2008-06-11
Justine13 at post number 4 did it for me! Been trying with the first method for some time, with only partial success. The problem I had was with permissions at the make install stage.

Then tried Justines solution, which worked after some fiddling. There is one error in that the alsa folders have been placed in the home directory under "compiled", but then the script is looking for the files in the Desktop. But with that simple change I have a working soundcard. I'm now another step closer to ditching XP!

The corrected script goes like this:

sudo apt-get -y build-dep alsa-lib alsa-utils alsa-driver && cd /home/$USER/compiled/alsa-driver-1.0.16 && ./configure --with-cards=emu10k1 && make && sudo make install && cd ../alsa-lib-1.0.16 && ./configure --with-cards=emu10k1 && make && sudo make install && cd ../alsa-firmware-1.0.16/ && ./configure --with-cards=emu10k1 && make && sudo make install && cd ../alsa-utils-1.0.16/ && ./configure --with-cards=emu10k1 && make && sudo make install

Hope this helps someone!

It maybe obvious to most, but for those new to the Linux thing, just copy and paste the above code into a terminal. (Terminal can be found under Applications / Accessories) When pasting in the terminal you need to use "paste" from the drop down menu. Control and V doesn't work, just gives you funny symbols in the terminal window

---

### Post by alibro on 2008-06-14
I installed a fresh copy of Ubuntu Studio 8.04 installed all the updates and then followed these instructions to the letter but they would not work until I ran the following command. After that everything went smoothly. 

sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`

Run this before doing the rest and all should be ok

Cheers all
Alibro

---

### Post by alibro on 2008-06-15
Looks like I spoke too soon. I was able to get sound out of the EMU 1212 OK but when I tried to record using Jack and Ardour things didn't go so well. Jack and Ardour (and Audacity which is usually more stable) constantly crashed and when I managed to get Ardour to stay up I couldn't get it to record. I ended up reinstalling my Delta 66 which worked with the minimum of fuss. 
Has anyone any suggestions for getting my Emu card to work with Jack and Ardour.
I was told the Emu 1212 is a better card for recording than the ageing Delta 66. Does anybody have any opinions on this or know if it is true?

Cheers
Alibro

---

### Post by Cantstopwinning on 2008-06-22
Thanks so much for this howto. I've got my emu1212 working finally! Unfortunately I can only seem to get playback and have no idea what needs to be done to get capture working.

I don't have any (apparent) software glitches, it seems like I just don't have the levels or a switch turned on somewhere in alsamixer but I have been fiddling with it for hours and I have no idea what could be missing.

Any ideas? Also how should I go about testing this? I've been plugging instruments directly in the card.

---

### Post by Eisenwinter on 2008-06-23
I've never attempted to record sound on my 1212m in Linux.
I know in Windows you can use Wavelab to record sounds from the sound card, though.

---

### Post by jukingeo on 2008-07-21
Be VERY wary of installing one of these cards.  If you are considering buying one, I would hold off.

Under the ALSA documents for the EMU series of cards they are only showing support up to 48k and there is NO mention of Midi support as of yet.

I found this information by accident under the Sound Blaster LIVE heading...yet it gives info for the EMU high end series as well.

[http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1)

Granted it looks like a full driver is in the works, but if you need a sound card NOW, I would stay away from these for a while.  These EMU high end series cards supposed to boast 192k, but the driver in Linux only goes to 48k.  If that is the case you are better off with a SoundBlaster Live and you will MIDI support as well.

Thank goodness I found this document or I would have made a serious mistake in buying this card.

Moving forward with my research, the Echo Gina is very similar to the 1212 and it has a bit more features.  The Midi doesn't require a special cable hook up either.

Personally I think I am going to go with putting a regular Soundblaster Live in my computer again for the main audio and use a Focusrite Saffire Firewire device for high-end audio.  Firewire uses the FreeBob driver within Jack.  The good thing about Firewire is that if the device doesn't work, just unplug it and return it.

Otherwise wait until they complete the driver for the EMU series.

Personally, I am going to look elsewhere.

Just figured I would post this here as a heads up that you are not getting what you think you will be getting out of the EMU series of audio cards.

Caveat De Emptor 

Geo

---

