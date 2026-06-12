---
title: "My solution for no sound from hda-intel (my card: Realtek alc880)"
date: 2006-06-12
forum: Multimedia &amp; Video
---

### Post by dan4444 on 2006-06-12
After hours and hours of tinkering and searching, I finally found my solution, the final step of which was upgrading to the latest stable kernal (2.6.16). In all, my solution consisted of the following:

1) Download the alsa driver, library, utilities, and oss from [www.alsa-project.org](www.alsa-project.org) (much thanks to chubuntu for this info as well as the basic info in step 2 - see thread at [http://www.ubuntuforums.org/showthread.php?t=187156](http://www.ubuntuforums.org/showthread.php?t=187156))

2) Run the following commands from a terminal session (modify as necessary for your system):

cd /home/dan/downloads/
sudo tar -xjvf alsa-firmware-1.0.9rc4.tar.bz2
sudo tar -xjvf alsa-driver-1.0.9rc4a.tar.bz2
sudo tar -xjvf alsa-lib-1.0.9rc4.tar.bz2
sudo tar -xjvf alsa-oss-1.0.9rc4.tar.bz2
sudo tar -xjvf alsa-utils-1.0.9rc4a.tar.bz2
sudo tar -xjvf alsa-plugins-1.0.9rc4.tar.bz2

cd alsa-driver-1.0.9rc4a
sudo ./configure --with-oss=yes --with-cards=hda-intel
sudo make
sudo make install

cd ../alsa-lib-1.0.9rc4
sudo ./configure
sudo make install

cd ../alsa-oss-1.0.9rc4
sudo ./configure
sudo make install

cd ../alsa-utils-1.0.9rc4a
sudo ./configure
sudo make install

sudo alsaconf
sudo shutdown -r now

3) Upgrade your kernal to the latest version - 2.6.16 by following the steps outlined in the thread at [http://www.ubuntuforums.org/showthread.php?t=157560](http://www.ubuntuforums.org/showthread.php?t=157560) (many thanks to "xXx 0wn3d xXx" for posting this - also, thanks to greghill and his post at [http://www.ubuntuforums.org/showthread.php?t=189929&page=3](http://www.ubuntuforums.org/showthread.php?t=189929&page=3) for giving me the idea that the solution may have something to do with the currently installed kernel)

Upon rebooting, my sound miraculously started to function, with my card now showing up under default sound card, volume control functioning properly, and my ability to change system sounds and play songs in Amarok. 

Note: It would probably make no difference, and even be more logical to run step #3 first, but the above is just the order in which I happened to run the steps.

In any case, these steps worked for me and I now have sound! - hope it works for you too.

---

### Post by dan4444 on 2006-06-12
Forgot to mention:

On step 3, I recieved the following error at the very end of the results from the kernal upgrade step #14 (that step takes several minutes):

make[7]: *** [/usr/src/modules/alsa-driver/acore/hpetimer.o] Error 1
make[6]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[5]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[4]: *** [modules] Error 2
make[4]: Leaving directory `/usr/src/linux-2.6.16ck12'
make[3]: *** [compile] Error 2
make[3]: Leaving directory `/usr/src/modules/alsa-driver'
make[2]: *** [build-stamp] Error 2
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
make[1]: *** [kdist_image] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
Module /usr/src/modules/alsa-driver failed.
Hit return to Continue

I at first thought this meant I would have to install the alsa drivers and other files yet another time, but to my surprise that was not the case.

If anyone knows what this error could mean and perhaps how to fix it, I would appreciate that. Otherwise, as long as it doesn't in some sly way affect my sound capabilities, I could care less.

---

### Post by evilregis on 2006-06-15
When I start to run:

```

cd alsa-driver-1.0.9rc4a
sudo ./configure --with-oss=yes --with-cards=hda-intel
sudo make
sudo make install
```

I get:

```

checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
```

I tried adding "/usr/lib/gcc" and "/usr/lib/gcc/i486-linux-gnu/4.0.3" to my $PATH and I still get the no-compiler error.

Any help?"

---

### Post by jezjones on 2006-06-22
the error is saying its not there atall. giving it those paths wont help if it is not the one it is looking for.

easiest fix is

sudo apt-get install build-essential

which should give you all that stuff it is checking for.

---

### Post by d3dtn01 on 2006-06-30
I downloaded the current stable alsa driver and tried to configure it with the following command:

```
./configure --with-oss=yes --with-cards=hda-intel --with-kernel=/usr
```

It seemed to do its thing just fine, but the last line of output was:

```
checking for which soundcards to compile driver for... configure: error: Unsupported soundcard hda-intel
```

I searched the forum and the Web for advice on this error, but found none. Anyone have advice for me?

UPDATE: I figured out from another thread that I needed to install the kernel headers. Having done so, it now seems to successfully compile the driver.

---

### Post by extremecarver on 2006-08-08
I'm having the same problem - unsupported hda-intel

How can I go on as I'm using 2.6.17.7 (beyond3 patched) kernel? 
What do I need from the kernel-headers - or better what do I have to include in my linux kernel xconfig configuration?

---

### Post by mrgreyshadow on 2006-09-20
Isn't the driver supposed to be called "snd-hda-intel"?

I have this problem right now, but I switched to SUSE in hopes that it would be fixed (I heard they have good hardware compatibility). Unfortunately, this was to no avail, and I'm still trying to figure this out.

I heard someone else say that kernel 2.6.15 has issues with ALC880 sound, so if you upgrade the kernel to a newer one and reinstall the driver, it might just miraculously work as described.

---

### Post by uterrorista on 2007-01-08
in step 1
what should i download ??? so many isdfughdfligusdhsiudffffffff...

thanks

---

### Post by ickyb0d on 2007-02-02
wow thanks.  never knew it was that simple!  heh.

I just got a Shuttle SB86i that needs the hda-intel driver.  It doesn't work out of the box, so i messed with it.  In messing with it, one of the threads said to disable my HD Audio in the bios.  After that i reinstalled ubuntu... and to my surprise it found no cards!  Then i thought "what if i re-enable the HD Audio in the bios.  After that, just ran alsaconf and it worked awesome.

there's tons of threads on here, but this seemed the most to the point.  But a good place for debugging seems to be the [Comprehensive Sound Problems Solutions Guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

Thanks again!

---

### Post by mnolansoc on 2007-02-11
I tried this, but I got stuck at "utils."  It says I need "curses library."  I found in another thread that I needed to install lncurses5-dev.  I tried installing that through Synaptic Package Manager, but it wouldn't install the file, because the path was no longer there.  So, I tried downloading the .deb file directly from debian, but that didn't work either.  Anyway, is there anyway to undo all of what I've done from this thread?  I have no sound right now, because it no longer sees my soundcard, alsamixer is no longer installed and can't be installed, and there are a bunch of folders on my desktop that I can't delete or move, because they're locked.  Thanks.

---

### Post by bogdan.dusa on 2007-04-20
Hi, 

I have a big sound device problem here. I have Ubuntu Edgy, I installed Skype, but I had no sound. I could hear, but I could not be heard.
I followed the steps indicated by dan4444 regarding the download and installation of the alsa driver, library, utilities, and oss from [www.alsa-project.org](www.alsa-project.org). Everything was ok, but after reboot, my computer has no sound at all! Ok, the sound was not working before with Skype, but it was working with Amarok, Kaffeine or XMMS.
Now Skype tells there is a "Problem with sound device", Amarok, when started, says "xine was unable to initialize any audio drivers", the XMMS can't open audio... The audio icon in the system tray is X-ed, telling that the Mixer cannot be found...

What can I do? Thanx!

---

### Post by oxygenws on 2007-09-04
try this post, it helps me:
[http://ubuntuforums.org/showpost.php?p=1357412&postcount=23](http://ubuntuforums.org/showpost.php?p=1357412&postcount=23)

---

