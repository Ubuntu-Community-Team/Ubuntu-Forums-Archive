---
title: "Trying to install alsa driver for realtek alc880 sound card"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by dan4444 on 2006-06-09
Trying to run the following in order intstall the alsa drivers (for my Realtek alc880 sound card)

Instructions said (found at [http://www.larsen-b.com/Article/87.html):](http://www.larsen-b.com/Article/87.html):)

apt-get install alsa-base
apt-get install alsa-source
cd /usr/src/
tar xvfj  alsa-driver.tar.bz2
cd modules/alsa-driver
./configure
make
make install
/etc/init.d/alsa start


Modified for my system:

sudo apt-get install alsa-base
sudo apt-get install alsa-source
cd /usr/src/
sudo tar xvfj /tmp/alsa-driver-1.0.9rc4a.tar.bz2
cd modules/alsa-driver
sudo ./configure --with-kernel=/usr/src/linux-source-2.6.15
sudo make
sudo make install
/etc/init.d/alsa start


First off, how does the ./configure command (launched from the /usr/src/modules/alsa_driver) know where to get the latest driver from (was unzipped to /usr/src/alsa-driver-1.0.9rc4a)?

In any case, I get the following errors on the "sudo make" command:

make[3]: *** [/usr/src/modules/alsa-driver/acore/init.o] Error 1
make[2]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.15'
make: *** [compile] Error 2


I searched high and dry on that error and found only vague and incomplete solutions. This is starting to give me a headache. Any idea of where I should go from here?

---

### Post by dan4444 on 2006-06-09
Lots of views, no replies. If there is any more info from my system that would be helpful in assesing this situation, please let me know. Also, if this post seems redundant to others, please do tell me where you think this belongs.

Thanks

---

### Post by jobezone on 2006-06-10
[QUOTE=dan4444]Trying to run the following in order intstall the alsa drivers (for my Realtek alc880 sound card)

Instructions said (found at [http://www.larsen-b.com/Article/87.html):](http://www.larsen-b.com/Article/87.html):)

apt-get install alsa-base
apt-get install alsa-source
cd /usr/src/
tar xvfj  alsa-driver.tar.bz2
cd modules/alsa-driver
./configure
make
make install
/etc/init.d/alsa start


Modified for my system:

sudo apt-get install alsa-base
sudo apt-get install alsa-source
cd /usr/src/
sudo tar xvfj /tmp/alsa-driver-1.0.9rc4a.tar.bz2
cd modules/alsa-driver
sudo ./configure --with-kernel=/usr/src/linux-source-2.6.15
sudo make
sudo make install
/etc/init.d/alsa start, 


First off, how does the ./configure command (launched from the /usr/src/modules/alsa_driver) know where to get the latest driver from (was unzipped to /usr/src/alsa-driver-1.0.9rc4a)?
[/quote]
It seems that you got alsa-driver-1.09rc4a.tar.bz2 from some other place other than the 'apt-get install alsa-source' command, is that right? What I mean is:
When you install the 'alsa-source' package, it places in /usr/src the compressed file named alsa-driver.tar.bz2, which is the source code of the version of alsa available from the repositories. But since you've downloaded yourself the sources of a version of alsa, and extracted them into /usr/src/alsa-driver-1.0.9rc4a, it means you want to compile this one:
```
cd /usr/src/alsa-driver-1.0.9rc4a
./configure --with-kernel=/usr/src/linux-source-2.6.15
sudo make
sudo make install
sudo /etc/init.d/start
```

---

### Post by dan4444 on 2006-06-11
Thank you jobezone. Yes, I did download the driver from another source than the apt-get repositories, as I had already tried that to no avail.

On the running configure from the same directoy as I unzipped the driver files, not doing so did strike me as strange, but that's what the instructions I located specified. Anyways, thanks for clearing that up for me. Next time I will trust my instincts and do as I usually do in only running commands that I have first made sense of.

In any case though, I received the same error when correcting my commands. Have moved on a bit in my way toward a solution (I think). See my posts in the threads at [http://www.ubuntuforums.org/showthread.php?t=187156&highlight=hda-intel](http://www.ubuntuforums.org/showthread.php?t=187156&highlight=hda-intel) and [http://www.ubuntuforums.org/showthread.php?t=184026&highlight=hda-intel](http://www.ubuntuforums.org/showthread.php?t=184026&highlight=hda-intel) for more info.

---

