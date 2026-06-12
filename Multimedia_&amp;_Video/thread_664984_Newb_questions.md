---
title: "Newb questions"
date: 2008-01-11
forum: Multimedia &amp; Video
---

### Post by mrxtambourineman on 2008-01-11
I just installed the 64 bit version of ubuntu 7.1 Now, please realize that I am a complete n00b when it comes to anything linux, but anything is better than vista, which came preinstalled on my laptop. I'm running a Toshiba A215 series of laptop. I have a couple problems relating to sound and video however.

My main problem is that I cannot enable the ATI accelerated graphics driver cannot be enabled. When I try to enable it, it says: "xorg-driver-fglrx is not enabled" How do I go about enabling it in an easy way that I can understand?

My secondary problem is that my soundcard which is some sort of Realtek High Def. Audio card, which is integrated with my motherboard. I'm running an AMD TL-60 processor if that helps. Not sure of the motherboard manufacturer. Also, when I type lspci in the terminal it lists the audio device as ATI SBx00 Azalia. Somehow though it still is not recognized in the volume control. How can I go about fixing this easily. I d/led the realtek linux drivers from the realtek page and I tried the automatic install, but I don't think it worked it says:

eric@portablevegan:~/realtek-linux-audiopack-4.07b$ ./install 
.....Decompress Driver source v1.0.15-4.07b 
.....Decompress ALSA Library source v1.0.14 
.....Decompress ALSA Utility v1.0.14 
Remove old sound driver 
Compile Driver........ 
checking for gcc... gcc 
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables 
See `config.log' for more details. 
make all-deps 
make[1]: Entering directory `/home/eric/realtek-linux-audiopack-4.07b/alsa-driver-hg20080110' 
make[1]: Nothing to be done for `all-deps'. 
make[1]: Leaving directory `/home/eric/realtek-linux-audiopack-4.07b/alsa-driver-hg20080110' 

Please, run the configure script as first... 

if [ -L /include/sound ]; then \ 
                rm -f /include/sound; \ 
                ln -sf /home/eric/realtek-linux-audiopack-4.07b/alsa-driver-hg20080110/include/sound /include/sound; \ 
        else \ 
                rm -rf /include/sound; \ 
                install -d -m 755 -g root -o root /include/sound; \ 
                for f in include/sound/*.h; do \ 
                        install -m 644 -g root -o root $f /include/sound; \ 
                done \ 
        fi 
install: cannot create directory `/include': Permission denied 
install: cannot stat `include/sound/*.h': No such file or directory 
make: *** [install-headers] Error 1 
./install: 40: ./snddevices: not found 
Remove old alsa library 
Compile ALSA Library..... 
checking build system type... x86_64-unknown-linux-gnu 
checking host system type... x86_64-unknown-linux-gnu 
checking target system type... x86_64-unknown-linux-gnu 
checking for a BSD-compatible install... /usr/bin/install -c 
checking whether build environment is sane... yes 
checking for gawk... no 
checking for mawk... mawk 
checking whether make sets $(MAKE)... yes 
checking for gcc... gcc 
checking for C compiler default output file name... configure: error: C compiler cannot create executables 
See `config.log' for more details. 
make: *** No targets specified and no makefile found.  Stop. 
make: *** No rule to make target `install'.  Stop. 
Compile ALSA Utility...... 
checking for a BSD-compatible install... /usr/bin/install -c 
checking whether build environment is sane... yes 
checking for gawk... no 
checking for mawk... mawk 
checking whether make sets $(MAKE)... yes 
checking whether NLS is requested... yes 
checking for msgfmt... no 
checking for gmsgfmt... : 
checking for xgettext... no 
checking for msgmerge... no 
checking for style of include used by make... GNU 
checking for gcc... gcc 
checking for C compiler default output file name... configure: error: C compiler cannot create executables 
See `config.log' for more details. 
make: *** No targets specified and no makefile found.  Stop. 
make: *** No rule to make target `install'.  Stop. 
cp: cannot stat `/usr/lib/pkgconfig/alsa.pc': No such file or directory 
ln: creating symbolic link `/dev/sndstat' to `/proc/asound/oss/sndstat': File exists 
cp: cannot create regular file `/usr/share/sounds/alsa/test.wav': Permission denied 
Remove Folder..... 
./install: 101: alsaconf: not found 

What the heck does any of this stuff mean? By no means am I a neophyte when it comes to pcs, but I don't understand linux very much at this point. Thank you very much for your time.

Eric

---

### Post by aysiu on 2008-01-12
If you have a working internet connection (wired or wireless), try going to System > Administration > Restricted Drivers Manager.

You may be able to easily enable a restricted driver to help with your graphics problem.

---

