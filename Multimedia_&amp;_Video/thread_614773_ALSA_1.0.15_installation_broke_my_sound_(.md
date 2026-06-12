---
title: "ALSA 1.0.15 installation broke my sound :("
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by Potted Meat on 2007-11-16
I've spent months (literally) now trying to get full function of my sound IO on my Gateway laptop.

I had everything working fine until I decided yet again to go for the holy grail which is to get my microphone working.  I had previously attempted to install ALSA 1.0.15 in an attempt to gain mic support but ran into some errors during utils.  Otherwise it seemed to work fine.  Last night I attempted to reinstall these latest drivers using [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

After following the steps closely I now have no sound at all.  My speaker icon in the taskbar says there is no device to control.  Alsamixer won't load with a report of "no such device" etc.

I am willing to give up on the microphone but I'd like to get my sound back without having to reinstall Ubuntu completely.

I'll be happy to post any information if you could tell me what I need to do.

If you have any idea how I could possibly get my mic to work I'd love you forever for the help!  It sucks having to devote a few GBs to Vista and reboot into it just to use a simple microphone.

Thanks!!!

PM

---

### Post by stchman on 2007-11-16
> **Potted Meat said:**
> I've spent months (literally) now trying to get full function of my sound IO on my Gateway laptop.

I had everything working fine until I decided yet again to go for the holy grail which is to get my microphone working.  I had previously attempted to install ALSA 1.0.15 in an attempt to gain mic support but ran into some errors during utils.  Otherwise it seemed to work fine.  Last night I attempted to reinstall these latest drivers using [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

After following the steps closely I now have no sound at all.  My speaker icon in the taskbar says there is no device to control.  Alsamixer won't load with a report of "no such device" etc.

I am willing to give up on the microphone but I'd like to get my sound back without having to reinstall Ubuntu completely.

I'll be happy to post any information if you could tell me what I need to do.

If you have any idea how I could possibly get my mic to work I'd love you forever for the help!  It sucks having to devote a few GBs to Vista and reboot into it just to use a simple microphone.

Thanks!!!

PM

I have a script to install/update your alsa drivers.  Get them here:

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

My scripts use the 1.0.14 drivers so you may want to try them.  I configure the drivers to use the --with-cards=hda-intel switch.  If your sound board is an HDA Intel then use that switch

I am going to update the script to use the 1.0.15 drivers this weekend.

---

### Post by Potted Meat on 2007-11-16
I ran your script but the situation is exactly the same.

I think I've changed something that's essentially made my sound card disappear.

At one point I was testing all sorts of commands to check the card and was getting "no sound card found" or something similar.

Could it have been the modprobe entries in that guide above?  Or update-modules?  Those are things I had never tried before.

Thanks for any help.

PM

---

### Post by Potted Meat on 2007-11-16
I still haven't made any progress.  

I know the problem must be a simple one.  Any ideas?

Thanks

PM

---

### Post by xeth_delta on 2007-11-16
You could compile the drivers from source. There might also be a way to make deb packages from the resulting binaries so that you install through the package system. Perhaps someone else can help on this.

Download the following packages from the alsa website [http://www.alsa-project.org/main/index.php/Download]("http://www.alsa-project.org/main/index.php/Download"):

Driver - [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2")

Library - [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2")

Utilities - [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2")

Decompress the archives:
```
tar -xjf alsa-lib-1.0.15.tar.bz2
```
```
tar -xjf alsa-driver-1.0.15.tar.bz2
```
```
tar -xjf alsa-utils-1.0.15.tar.bz2
```

Go into the library directory and build:
```
./configure
make
sudo make install
```

Now, make sure what sound card you have on your laptop:
```
lspci | grep -i audio
```

Once you know what kind of driver you need, go into the driver directory, for instance let's say you need the hda-intel driver:
```
./configure --with-cards=hda-intel
make
sudo make install
```

Finally, install the utilities, enter the respective directory and type the usual:
```
./configure
make
sudo make install
```

Restart your alsa sound system:
```
sudo /etc/init.d/alsasound restart
```

Don't delete your alsa source code directories, if you decide to remove the drivers you can issue a:
```
sudo make uninstall
```

Hope this is helpful,
Xeth

---

### Post by Potted Meat on 2007-11-17
I've followed those steps when I installed initially.

One thing I'm confused about is when to use "sudo" and when not to.  When I installed 1.0.15 initially I used sudo for ./configure, make, and make install because without the "sudo" I got errors.

Also after installing all of that I don't have a "alsa-sound" command.

I'm so confused by all of this.  

Thanks for any help!

PM

---

### Post by Yellow Pasque on 2007-11-17
If you can;t get ALSA working, try removing it and using OSS instead. See my sig for details.

---

### Post by Threbus5 on 2007-11-17
Hi,
Sadly my experience duplicates yours. ;-(
I used the same procedures (that you followed and that are posted a couple responses back in this thread) with the same results - all audio evaporated.  I restored the hard disk  from my backup for a 'clean shot' at obtaining microphone input.
Just as you,I determined the sound card and viewed the amixer and alsamixer outputs. I even added the line that assured viewing the increased command set and configured the audio so that "mic was the only selected input'.
Nuts!
If you make headway with this please let me know. (Threbus5@hotmail.com) I have most of today to work on it and will inform you of any success. I am considering abandoning alsa for oss.
I recall that the initial Feisty microphone audio also failed but among the updates something corrected it. Hopefully that will occur for Gutsy.
In the mean time, I am digging for a solution.
Take care and good luck.

---

### Post by xeth_delta on 2007-11-17
> **Potted Meat said:**
> I've followed those steps when I installed initially.

One thing I'm confused about is when to use "sudo" and when not to.  When I installed 1.0.15 initially I used sudo for ./configure, make, and make install because without the "sudo" I got errors.

Also after installing all of that I don't have a "alsa-sound" command.

I'm so confused by all of this.  

Thanks for any help!

PM

Ok, this will go a bit off-topic. When you use "sudo" the commands that follow it will be executed as superuser / root or a different user than your own.
Basicaly, you need to use sudo whenever you need to execute a command whose actions require higher privileges. You can read more about it  the manual
```
man sudo
```

When you decompress and compile in your home directory or any other directory you own, you will need to use sudo only to install. My guess is that you needed to use sudo for "./configure" and "make" because you used "sudo" also when decompresssing, hence the resulting directory and its contents would be owned by root. In this situation you, as a normal user won't be able to modify anything inside those directories. You could check the ownership of a certain directory (say foo_directory) and the files within by issuing a:

```
ls -al foo_directory
```

The "." in the listing is the directory itself.

Now, back to the initial topic.

Regarding the "alsasound" script. I apologize, I mistakenly typed "alsa-sound", the correct form is "alsasound". I will correct it in my initial post, too. You also have to call the entire path to that script, i. e.:

```
sudo /etc/init.d/alsasound restart
```

It could also be that you have an "alsa" instead of "alsasound", in that case:

```
sudo /etc/init.d/alsa restart
```

If after this your card still does not work, issue a:
```
sudo alsaconf
```

That should take you through a number of steps to configure your sound system.

Let us know how it goes,
Xeth

---

### Post by Potted Meat on 2007-11-17
Thanks for the sudo info.

I had tried those commands you posted but gotten errors or no such file etc.

In any case I've spent far too much time on this and can't justify spending any more to get a microphone to work.  Space is cheap enough now so I'll just keep Windows around for the microphone.  It seems silly but time is too precious to bother with with such a trivial thing.  I've cleared my hd and reinstalled gutsy.

Thanks to all for the help.  

PM

---

### Post by xeth_delta on 2007-11-17
> **Potted Meat said:**
> Thanks for the sudo info.

I had tried those commands you posted but gotten errors or no such file etc.

In any case I've spent far too much time on this and can't justify spending any more to get a microphone to work.  Space is cheap enough now so I'll just keep Windows around for the microphone.  It seems silly but time is too precious to bother with with such a trivial thing.  I've cleared my hd and reinstalled gutsy.

Thanks to all for the help.  

PM

You're most welcome! Given more time I am sure you could get it working. Just let us know on this thread whenever you might try again or how you solved it.

Xeth

---

