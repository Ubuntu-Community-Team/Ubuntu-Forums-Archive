---
title: "Unable to play a DVD"
date: 2009-11-04
forum: Multimedia Software
---

### Post by Wander_Free_Forever on 2009-11-04
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

Hello every one,

From what I have observed, I can not play a DVD movie and then some.
Mplayer gives me the error message "No URI handler implemented for "dvd"."
However, I am able to play music CDs.

In addition, I have encountered a strange bug I guess. I can not unmount a
DVD even ejecting it does not unmount the drive. If I were to insert a
second CD or DVD, it would show up as a second drive. Only when two drives
are present can I unmont the first one.

obligatory info:
Release 9.10 (karmic)
Kernel Linux 2.6.31-14-generic
GNOME 2.28.1

-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFK8Sb3zH0f+AFrIBkRCG2qAP9Ef3nfQK6e83eSPaBuLQ/hrs+3tbgeSW/F
hUbqg20ZnwD8D1sdnpUSqZTNe56Hk7ukJP29yOn3tMEjvDXHz9hz/z8=
=7SEu
-----END PGP SIGNATURE-----

---

### Post by tripleaces on 2009-11-04
I'm not really sure how experienced of a Ubuntu user you are so I'll be generic. Ubuntu doesn't come DVD playback ready after it's initially installed, have you downloaded and installed the necessary files to enable it? If not check out this post: 

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

It will help you setup all of your media needs including DVD playback. 

As for the DVD unmount issue does it happen every time or just once in awhile? Most likely it's probably an issue with mplayer (or whatever you are using to attempt watching DVDs) when you get that error/crash and its keeping the disk from being unmounted as it's still declaring it in use. If you eject the DVD/cd regardless the system will still think it's in use and that's why you are getting the fake 2nd drive when you insert a different disk. I'm guessing when you do insert a different disk it's not able to read while the other is mounted?

If this is the cause of your unmount error, and you haven't enabled DVD playback, then the problem should go away after fixing the DVD playback issue.

---

### Post by Wander_Free_Forever on 2009-11-04
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

Simply put, the second drive has occurred before.

I was under the impression that Ubuntu 9.10 was able to play DVDs out of
the box. This was stated in one of the installation screens.

[http://farm4.static.flickr.com/3505/4073815295_49d913ee71_o.jpg](http://farm4.static.flickr.com/3505/4073815295_49d913ee71_o.jpg)

-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFK8lOYzH0f+AFrIBkRCE41AQDTD668jPrfrvtRvLShcJ0OnhimAFR9gyk1
qkEuXOg+bwD/fjnL8zVYrnetYxNGeo/AzecUUZzJGbTa2oH0v1qI4x4=
=xH+0
-----END PGP SIGNATURE-----

---

### Post by soapBAR2 on 2009-11-04
```
sudo apt-get install ubuntu-restricted-extras 
```

or

```
sudo apt-get install libdvdread4 libdvdcss2
```

Make sure you have the restricted repositories enabled (check your favourite GUI APT client - synaptic, aptitude, kpackagekit, etc.)

---

### Post by Wander_Free_Forever on 2009-11-05
Oh those commands were not listed at http://ubuntuforums.org/showthread.php?t=766683. I had followed these instructions to no avail:


[I]DVD PLAYBACK

UBUNTU FAMILY 9.04+ USERS ONLY


Note: I recommend disabling the CD/DVD-ROM source before completing this section, as you will receive numerous prompts if you need to run the "install-css.sh" command. If you're not sure whether it's disabled or not, take a look at the preparation instructions in Part 1.

For the best DVD playback in Ubuntu, including menu support, install the following packages:

sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4 vlc

You can also use the Xine engine in Ubuntu (the default engine in Kubuntu) for video/DVD playback. This can be done without having to change the back-end of Totem - just install an alternative GNOME front-end for Xine called Gxine (this is optional, VLC will do just fine):

sudo apt-get install gxine libxine1-ffmpeg

Now you can test a DVD with VLC, Kaffeine, Gxine or whatever your favourite media player is. Enable deinterlacing ("VLC > Video > Deinterlacing > Blend") if playback is choppy or if you notice artifacts.

Note: Those of you still having DVD playback issues after installing the above packages should try the solutions in the troubleshooting section, which you can find at the end of this howto.

DVD PLAYBACK


ZERO DVD PLAYBACK

Installed the necessary applications and packages but still cannot play/rip commercial DVDs? Perhaps you should make sure the DVD drive has been set to the correct region. If you have never successfully played DVDs in Ubuntu or Windows, install the following command line based application:

sudo apt-get install regionset

Please be aware that most drives limit you to about 5 changes (regionset should tell you how many you have left), so if you plan to watch foreign DVDs, it would be best to have a secondary external DVD drive, and have it set to a different region to the one in your machine. To set or change your DVD drives region, put any disc into your drive, and type "sudo regionset" into the terminal, then simply select the relevant region code. Here is the list of region codes and which countries they cover:

RC1 = North America (USA and Canada)
RC2 = Europe, Middle East, South Africa and Japan
RC3 = Southeast Asia, Taiwan, Korea
RC4 = Latin America, Australia, New Zealand
RC5 = Former Soviet Union (Russia, Ukraine, etc.), rest of Africa, India
RC6 = China

For those of you who previously played DVDs in GNU/Linux or Windows, but for some reason are unable to now, it could be related to faulty leads/connectors, but give this one last software-related method a try:

sudo apt-get install build-essential debhelper fakeroot

then:

sudo /usr/share/doc/libdvdread3/install-css.sh

or if you get an error with that command:

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

SOME DVD PLAYBACK

If unlike above you have followed Part 4 of my howto and most DVDs play fine, but you're having trouble with some newer DVDs, please refer to this link, and concentrate on the solution for VLC (this bug was apparently fixed in February 2008).[/I]

It would seem that none of the software, Mplayer, VLC player Xine can reconize my D: drive. This is very odd  due to the fact that I can access thedrive and the DVD via GNOME as a regular user!

---

### Post by Wander_Free_Forever on 2009-11-05
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

Arrg double post. At least I have recorded my efforts into a number of
videos. They should shed some light upon my current difficulties.


[http://www.youtube.com/watch?v=OpAUxCb95OQ&fmt=18](http://www.youtube.com/watch?v=OpAUxCb95OQ&fmt=18)
[http://www.youtube.com/watch?v=FQPh3XyPBbo&fmt=18](http://www.youtube.com/watch?v=FQPh3XyPBbo&fmt=18)
[http://www.youtube.com/watch?v=YeHHQDr-LzU&fmt=18](http://www.youtube.com/watch?v=YeHHQDr-LzU&fmt=18)


-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFK8zBEzH0f+AFrIBkRCLqbAQDts29I2U9WME8WY3jyReR1TazWE5LfX2l+
1P9lCWr++wD/cVrAASBY1Bci9leZ/VeJGYhNA0iIF0wO7hrBRyaf9Hk=
=dNMn
-----END PGP SIGNATURE-----

---

### Post by Wander_Free_Forever on 2009-11-05
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

I forgot to mention that my D: drive (and only CD or DVD drive) is:

PLDS DVD+-RW DH-16A6S SCIS CdRom device

-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFK8nAGzH0f+AFrIBkRCAdmAQDbJ8W7juML+6RbQ5QzBZUXaYhV6UJVKlg5
FT9/56sFpQEAu1L7y0wSFxf62OWzO/XfKBjTbqTlhiRRcxvP1m6slNQ=
=VzNa
-----END PGP SIGNATURE-----

---

