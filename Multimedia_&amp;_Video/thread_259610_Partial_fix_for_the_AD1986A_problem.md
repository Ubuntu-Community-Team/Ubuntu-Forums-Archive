---
title: "Partial fix for the AD1986A problem"
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by zx80user on 2006-09-17
Various posters have complained of problems with this sound device/driver (particularly no good sound on the left channel, etc).

This appears to be (at least partially), a configuration problem. By default ALSA considers your AD1986A device to have 6 output jacks.

Adding 

snd-hda-intel model=3stack

to /etc/modules at least partially fixes this - though seems to be a better match to my hardware config rather than a full match. The ALSA system still falls over if I attempt to adjust the mixer.

More details can be found in the ALSA-Configuration.txt file in the ALSA-driver documentation

---

### Post by zx80user on 2006-09-17
Even more partial that I thought, as it is actually only playing sound out of the right speaker, though at least there is no awful whine.

---

### Post by mcmc on 2006-09-30
try adding position_fix=1 as well

---

### Post by tux21 on 2007-02-21
M2N-MX and audio AD1986a (Ubuntu edgy)

Published from openlab on December 2nd, 2006

And hour we see like installing the audio card integrated SoundMax AD1986a on one ubuntu edgy. My card mother is one Asus M2N-MX (GeForce 6100 Nforce 430).
In order to make it to work we must first of all unload the packages alsa, in particular the driver, the bookcases and the utility for release ALSA 1.0.13:

[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.13.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.13.tar.bz2)

[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.13.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.13.tar.bz2)

[ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.13.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.13.tar.bz2)

As usual scompattiamo and we extract the packages:

tar jvf alsa-driver-1.0.13.tar .bz2

tar jvf alsa-lib-1.0.13.tar .bz2

tar jvf alsa-utils-1.0.13.tar .bz2

Then in the order we install the driver:

cd alsa-driver-1.0.13/
./configure --with-oss=yes --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-2.6.17-10-generic/
make
make install

the bookcases

cd ../alsa-lib-1.0.13/
./configure
make
sudo make install

Before installing the utilities we must install the package libncurses5-dev, therefore

sudo apt-get install libncurses5-dev

and then

cd ../alsa-utils-1.0.13/
./configure
make
sudo make install

Now we shape alsa, with the utility alsaconf:

sudo alsaconf

we follow the passages of the tool graphical () until the end.

In order to end, we shape our card adding to the /etc/modprobe.d/alsa-base rows the line

options snd-hda-intel position_fix=1 model=3stack

Riavviamo and we would have to be in a position to feeling something…
in any case we control that the volume is not annulled from alsamixer…

sudo alsamixer

This voice has been inserted the Saturday, December 2nd, 2006 to 5:48 pm and is archiviato under Hardware. You can follow any responses to this entry through the RSS 2,0 feed. You can you leave one answer, or trackback from your situated one.
4 Answers to “M2N-MX and audio AD1986a (Ubuntu edgy)”

   1. RattoRosa Dice:
      December 5th, 2006 to 6:36 pm

      Thanks thousands of the explanation!

      finally they are successful to make to work also the audio card!

      I use kubuntu and hour, after to have put aposto the audio card volume (PC speekers) in kmix does not work me piu'… succeeds pear tree' to put aposto the volume with “lever” front and PCM… ce' some way in order to make to rifunzionare lever PC speekers?

      hello and thanks still!

      RattoRosa
   2. Nokao Dice:
      December 6th, 2006 to 11:54 pm

      Worked, all ok, thanks ;)

      p.s but ste bookcases could not include compiled them in the repository? mah
   3. openlab Dice:
      December 7th, 2006 to 7:20 pm

      it knows to me that in the repository they are firm to one previous version…
   4. Alfredo Pironti Dice:
      January 20th, 2007 to 4:01 pm

      Thanks!
      Your indications have worked also with Debian.

      I am using the kernel 2.6.20.rc5, but the not improved situation and `, in fact they remain still two problems:
      1) I have had to modify /etc/modprobe.d/alsa-base manually, from this I deduce that the card and `officially not recognized
      2) I have houses with jack the caps and mic-in on the facade, it connects to you to the pin azalia of the m2n-MX: the sound comes only emitted on the jack of the houses, and they do not give those on the back of the card mother! (even if in not riproducibile way some time the sound exits from the doors on the back…)

      Suspicion that these behaviors have had to the parameters that we pass to the driver.
      You can give some elucidation to me in piu `? Or you know as we can bring back this worm near the sviluppatori of the kernel (or alsa? or what). I have bought from little the card mother, and can collaborate gladly, so that the 2.6.20 come rilasciato with a complete support for this card mother…

      Thanks still of the support!
      Hello,
      Alfredo

---

