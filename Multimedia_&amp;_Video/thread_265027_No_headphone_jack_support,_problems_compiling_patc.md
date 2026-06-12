---
title: "No headphone jack support, problems compiling patched ALSA."
date: 2006-09-25
forum: Multimedia &amp; Video
---

### Post by marinosr on 2006-09-25
I have a Compaq V3000 laptop with an nVidia chipset. There is a [known bug](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2412) with this setup, such that ALSA will not output to the headphone jack. I'm attempting to apply the patch provided at the above link and then compile ALSA. This is the first time that I've ever had to do a patch like this, and I know very little about diff files. I run the file, and this is the output:

```
root@ENIAC:/home/marinosr/Desktop/alsa-driver-1.0.12# ./hda-generic-hp-fix.diff
diff: 63e58b008259: No such file or directory
./hda-generic-hp-fix.diff: line 2: ---: command not found
./hda-generic-hp-fix.diff: line 3: +++: command not found
./hda-generic-hp-fix.diff: line 4: @@: command not found
./hda-generic-hp-fix.diff: line 5: syntax error near unexpected token `}'
./hda-generic-hp-fix.diff: line 5: ` };'
root@ENIAC:/home/marinosr/Desktop/alsa-driver-1.0.12#

```
 
I don't know if this is good or not, but I went ahead and compiled ALSA anyway. This is my ./configure line...

```
root@ENIAC:/home/marinosr/Desktop/alsa-driver-1.0.12# ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=hda-intel  --with-oss=yes

```

Then, I just did make and make install. Everything seemed to be OK, but there is still no headphone output. The internal speakers just keep playing, regardless if there is a plug in the front or not. Any help with this would be appreciated, as I have a radio show @ 10 tonight, and I really want to play music off my computer. Thanks!

---

### Post by marinosr on 2006-09-25
Aha. Got it. I just didn't know how to use patch. My headphone jack now works.

-Richard

---

### Post by ambience713 on 2006-10-01
> **marinosr said:**
> Aha. Got it. I just didn't know how to use patch. My headphone jack now works.

-Richard

The complete tutorial for getting the sound to work can be found here:


Sound Card

Kernel module hda-intel (alsa-1.0.10) is automatically loaded and the internal speakers work fine, but you do not get any audio output from the headphone. This can be solved installing alsa-1.0.12 and applying this patch [http://xopen.dyndns.org/linux/v6024ea/hda-generic-hp-fix.diff:](http://xopen.dyndns.org/linux/v6024ea/hda-generic-hp-fix.diff:)

$ tar -xjvf alsa-driver-1.0.12.tar.bz2
$ tar -xjvf alsa-lib-1.0.12.tar.bz2
$ tar -xjvf alsa-utils-1.0.12.tar.bz2
$ cp hda-generic-hp-fix.diff alsa-driver-1.0.12/alsa-kernel
$ cd alsa-driver-1.0.12/alsa-kernel
$ patch -p1 < hda-generic-hp-fix.diff
$ cd ..
$ ./configure --with-oss=yes --with-cards=hda-intel
$ make
$ sudo make install
$ cd ../alsa-lib-1.0.12
$ ./configure
$ make
$ sudo make install
$ cd ../alsa-utils-1.0.12
$ ./configure
$ make
$ sudo make install

Optionally, download/install alsa-oss-1.0.12.tar  

SOURCE: [http://xopen.dyndns.org/linux/v6024ea/#sound](http://xopen.dyndns.org/linux/v6024ea/#sound)

works with Compaq Presario V3000Z and Compaq Presario V6024EA

---

### Post by Charles Hand on 2006-10-04
I tried this on Vaio AGN-AR170P (intel ICH7). The drivers are up to 1.0.13. When I went to apply the patch, it said it was already applied. After making and installing everything, the headphone jack still doesn't work.

---

### Post by Charles Hand on 2006-10-04
It didn't install. proc/asound/version still says 1.0.11rc4.

---

### Post by ldlzp on 2006-11-13
Thanks a lot,I just can't download the "hda-generic-hp-fix.diff",Can you send me one to my email [email]ldlzp@yeah.net[/email].
Thank you again.

---

### Post by daniel2501 on 2006-11-13
I've installed alsa 1.0.13 and am running kernel 2.6.19. Still no working headphones on my compaq v3000t :-(
Not sure what I'm doing wrong...

---

### Post by baserg on 2006-11-28
[http://dev-board.com/?p=16]("http://dev-board.com/?p=16")

---

### Post by Wickednix on 2006-12-03
Any word on getting this resolved? I have the Ati/ Intel HD chipset and get the same results as most people in this forums. I have the toshiba Satillite L35 and for the life of me cannot get the headphones jack working.

---

### Post by manny0 on 2006-12-16
> **Wickednix said:**
> Any word on getting this resolved? I have the Ati/ Intel HD chipset and get the same results as most people in this forums. I have the toshiba Satillite L35 and for the life of me cannot get the headphones jack working.

you are not alone man i have the same problem. it makes the L35 almost useless to me in an outside of the house or late night computing session

---

### Post by ivanbone on 2006-12-24
it works.. but it just seperate speaker and headphone control but jack sensing not working. have to do mute on of it manually ... :(

---

### Post by ivanbone on 2006-12-24
I installed alsa version 1.0.14rc1 and it fixed the jack sensing bug.
My kernel version is 2.6.17

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2734]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2734")

---

### Post by manny0 on 2006-12-24
how do i install this? its just a txt file...?

---

### Post by yuanfangcan on 2006-12-26
> **manny0 said:**
> you are not alone man i have the same problem. it makes the L35 almost useless to me in an outside of the house or late night computing session

I have have the same problem with L35, did you find the solution?

---

### Post by manny0 on 2006-12-26
i wont get a chance to try it untill tonight. im going to be at work all day. try and follow that Tut. on the previous page. and tell me how it goes :) my email is [email]manny00@gmail.com[/email]

---

### Post by SpiralSlash on 2006-12-27
Toshiba L35-S2151 owner checking in here... I'm running Kubuntu 6.06 - most of you seem to be running Ubuntu. I also can't use the headphone jack and it's somewhat annoying. It's not too much of a problem at the moment as I'm still on break from school, but it'll be a pain once I have to go back to college. Can't exactly blast my music over the speakers in the hall while I wait for my next class. :(

Has anyone tried applying the previously mentioned patch yet?

---

### Post by manny0 on 2006-12-27
no i havn't myself im afraid it might not work for Toshbia because they are using it on a compaq or something. can anyone confirm this. or at least help me figure out what hardware i have so i can do this as well?

---

### Post by naxmul on 2007-03-15
same problem here with the toshiba satellite L35. anyone know how to resolve this?

---

### Post by DonnieP on 2007-03-15
And . . . same problem here with Toshiba A135

---

### Post by airencracken on 2007-03-22
Yup. I have the same problem and I've seen a multitude of posts on the issue without a solution from anyone. Looks like I/We have to live with it for now. :(

---

### Post by spivak.d on 2007-03-25
Also reproducible on Toshiba Tecra M7.

---

### Post by manny0 on 2007-04-01
I have no clue man its getting really frustrating. i was wondering if there was a usb audio device i could use like a usb to phono jack plug?

---

### Post by jmstern on 2008-03-06
I am not a total newbie - in that i have gone through several different methods of getting Java to work on my Presario A900 without reloading MS Winders.   I admit i am stymied by the commands quoted below.  What directory do i need to load  alsa-1.0.1r2 into?  What directory do i need to be in when i enter the SUDO commands?  I am a reactionary rebel - yes i detest all things MS Windows.  I would love to be able to play tunes through the headphones!   Sound hardware is at end of this post



> **ambience713 said:**
> The complete tutorial for getting the sound to work can be found here:


Sound Card

Kernel module hda-intel (alsa-1.0.10) is automatically loaded and the internal speakers work fine, but you do not get any audio output from the headphone. This can be solved installing alsa-1.0.12 and applying this patch [http://xopen.dyndns.org/linux/v6024ea/hda-generic-hp-fix.diff:](http://xopen.dyndns.org/linux/v6024ea/hda-generic-hp-fix.diff:)

$ tar -xjvf alsa-driver-1.0.12.tar.bz2
$ tar -xjvf alsa-lib-1.0.12.tar.bz2
$ tar -xjvf alsa-utils-1.0.12.tar.bz2
$ cp hda-generic-hp-fix.diff alsa-driver-1.0.12/alsa-kernel
$ cd alsa-driver-1.0.12/alsa-kernel
$ patch -p1 < hda-generic-hp-fix.diff
$ cd ..
$ ./configure --with-oss=yes --with-cards=hda-intel
$ make
$ sudo make install
$ cd ../alsa-lib-1.0.12
$ ./configure
$ make
$ sudo make install
$ cd ../alsa-utils-1.0.12
$ ./configure
$ make
$ sudo make install

Optionally, download/install alsa-oss-1.0.12.tar  

SOURCE: [http://xopen.dyndns.org/linux/v6024ea/#sound](http://xopen.dyndns.org/linux/v6024ea/#sound)

works with Compaq Presario V3000Z and Compaq Presario V6024EA

o[IMG]http://home.comcast.net/~johnmstern/Nov10_20.jpg[/IMG]




===========

        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        


*-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-L632H
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: HS02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready

---

