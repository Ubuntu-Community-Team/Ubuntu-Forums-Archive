---
title: "Howto: Install Hollywood+ MPEG card"
date: 2008-05-31
forum: Multimedia Software
---

### Post by Bubbel on 2008-05-31
This howto is just a small list of steps to install the card mentioned.
A Thanx goes out to Roial for some extra handyness.

The install consists of three steps:
[LIST]
[*]Remove/deactivate the original 'support'
[*]Retrieve the new drivers & software
[*]Compiling & installing
[/LIST]

Most of the data from this howto came from the makers of the driver: [http://dxr3.sourceforge.net/](http://dxr3.sourceforge.net/)

This howto assumes you have root privileges in the terminal. To do so, open a terminal and type the following:
```
sudo -s
```Enter your own password (not the root password). You are then presentend with a root prompt.

[B]Removing/deactivating the original 'support'
[/B]At first you have to make sure you have no remnants of the installed files from the Ubuntu repositories. To be sure of that, type the following:
```
apt-get purge /y em8300 em8300-bin em8300-source em8300-headers
```Apt-get may give some errors if the packages aren't installed. That is ok.

Now we are going to deactiveate the driver subset that came with the distro:
```
echo blacklist adv7175>> /etc/modprobe.d/blacklist
echo blacklist adv7170>> /etc/modprobe.d/blacklist
```_*Note:*_ Be sure to use double redirection symbols: >> an not single > ones. That can ruin your installation.
To unload the already loaded drivers, reboot or do the following:
```
modprobe -r adv7175
modprobe -r adv7170
```_*Note:*_ Again you may see some harmless errors.

**Retrieve the new drivers & software**
Before we can build the drivers, we need to create the correct enviornment to build. Of course this only is applicable when you haven't done this already:
```
apt-get install build-essential linux-headers-`uname -r`
```Be sure to use back-tick ` quotes, instead of straight ' quotes.

Now we're ready to retrieve the drivers. Please use a simple folder name (no spaces or whatsoever) to be sure it all goes correct. For example:
```
mkdir /date; cd/data
```The we can retrieve and unpack the drivers:
```
wget -O- http://downloads.sourceforge.net/dxr3/em8300-0.17.0.tar.gz|tar xz
```This downloads and extracts the source code in a subfolder called em8300-0.17.0
[U][I]
Note:[/I][/U] In time there could be a newer version. Check here: [http://sourceforge.net/project/showfiles.php?group_id=5165](http://sourceforge.net/project/showfiles.php?group_id=5165) for the newest version.

Now the good part:
```
cd em8300-0.17.0
./configure
make
make install
cd modules
make
make install
depmod
```That's it, your driver is installed, together with the supporting software.

Now we need to configure it (There are more ways here. *Roial* pointed me to this elegant option).
Start a text editor as root, so from inside your terminal (like nano, for instance) and create the following:
```
alias char-major-121 em8300
options adv717x pixelport_16bit=1 pixelport_other_pal=0 swap_redblue_pal=0 color_bars=0
options em8300  use_bt865=0 bt865_ucode_timeout=1 dicom_fix=0 dicom_control=0 dicom_other_pal=0 audio_driver=oss

```Save the file as /etc/modprobe.d/em8300

Maybe you have to set some extra options for your card. You can read about it in the README-modoptions text file. To test them first unload the drivers```
modprobe -r em8300 adv717x
``` and another ```
modprobe adv717x em8300
```This will be done automatically on restart

That's it. The modules are loaded. Now it's time for me to go testing how nice my DIVX movies are :) (Using mplayer)

Please comment as you like to make this howto better.

Some things I ran up to:
When having a Kernel Update, a recompile is needed. It didn't work nice, so I deleted the source folder and re-downloaded it again. Later on I discovered the need for the depmod command. Will revise when I have more info on this.

:-? Bubbel

---

### Post by Roial on 2008-06-05
Hi Bubbel,

thanks for your howto for the dxr3. I hope you don't mind if I add a few things I found out while getting to know ubuntu and the dxr3 over the last 6 months.

Since I'm using ubuntu on a headless HTPC, I was happy enough originally just loading the modules manually because a) I didn't yet know how to do it any other way and b) I only restarted the server after updates

There was a kernel update a few months back that broke the modules. I didn't realise then that they needed re-compiling and that gave me the opportunity to work out how to get the modules to load automatically on booting

This is how I did it (after compiling the modules):

After examing a few other files in /etc/modprobe.d and some experimenting, I created a file /etc/modprobe.d/em8300 containing the following:
```

# commands installed by some package that don't work
# alias /dev/em8300* em8300
# alias char-major-121 em8300
# install em8300 /sbin/modprobe adv717x && /sbin/modprobe --ignore-install em8300

# commands installed by some package that don't work
# alias char-major-121 em8300
# pre-install em8300 modprobe adv717x
# post-install em8300 em8300setup

# alias char-major-121 em8300

install em8300 /sbin/modprobe --ignore-install adv717x $CMDLINE_OPTS \
	&& { /sbin/modprobe --ignore-install em8300 $CMDLINE_OPTS ; }

# default options installed by package
# options adv717x pixelport_16bit=1 pixelport_other_pal=0
# options em8300 dicom_fix=0 dicom_control=0 dicom_other_pal=0

# my options
options adv717x pixelport_16bit=1 pixelport_other_pal=0 \
	pixeldata_adjust_pal=3 pixeldata_adjust_ntsc=1
options em8300 major=0 use_bt865=0 dicom_other_pal=0 dicom_fix=0 \
	dicom_control=0 bt865_ucode_timeout=0 audio_driver=oss



```Note: the commented lines were mostly added when I tried to install the em8300 packages using Synaptic or with debs from the debian repository (which had a newer version). I haven't added a remove command (yet) because I'm not sure how necessary it is

This worked until the last 2 kernel updates (2.6.24-17 & 2.6.24-18). 2.6.24-17 obviously broke the modules again and was an opportunity for me to upgrade em8300 from 0.17-rc1 to the final version. Now comes the bit I didn't know about and had me stumped. I re-compiled the em8300 modules against 2.6.24-18. But they wouldn't load. FATAL: file not found etc. But I _could_ see them in nautilus. 'Search for files' didn't find them either. After some research I find out the 'locate' can find files in terminal. But that also found nothing. After another hour of research on depmod, I found a suggestion to do an 'updatedb'. And hey presto! the files were 'there'. The OS could finally see the modules as well. 'sudo modprobe em8300' worked and 'cat /proc/em8300' showed the expected results

By the way, is there a typo in your howto?
```
cd em8300-0.17.0/modules
./configure
make
make install
```
Shouldn't this be
```
cd em8300-0.17.0
./configure
cd modules
make
make install
```?

---

### Post by Bubbel on 2008-06-12
> **Roial said:**
> Hi Bubbel,

thanks for your howto for the dxr3. I hope you don't mind if I add a few things I found out while getting to know ubuntu and the dxr3 over the last 6 months.

Since I'm using ubuntu on a headless HTPC, I was happy enough originally just loading the modules manually because a) I didn't yet know how to do it any other way and b) I only restarted the server after updates

There was a kernel update a few months back that broke the modules. I didn't realise then that they needed re-compiling and that gave me the opportunity to work out how to get the modules to load automatically on booting

This is how I did it (after compiling the modules):

After examing a few other files in /etc/modprobe.d and some experimenting, I created a file /etc/modprobe.d/em8300 containing the following:
```

# commands installed by some package that don't work
# alias /dev/em8300* em8300
# alias char-major-121 em8300
# install em8300 /sbin/modprobe adv717x && /sbin/modprobe --ignore-install em8300

# commands installed by some package that don't work
# alias char-major-121 em8300
# pre-install em8300 modprobe adv717x
# post-install em8300 em8300setup

# alias char-major-121 em8300

install em8300 /sbin/modprobe --ignore-install adv717x $CMDLINE_OPTS \
	&& { /sbin/modprobe --ignore-install em8300 $CMDLINE_OPTS ; }

# default options installed by package
# options adv717x pixelport_16bit=1 pixelport_other_pal=0
# options em8300 dicom_fix=0 dicom_control=0 dicom_other_pal=0

# my options
options adv717x pixelport_16bit=1 pixelport_other_pal=0 \
	pixeldata_adjust_pal=3 pixeldata_adjust_ntsc=1
options em8300 major=0 use_bt865=0 dicom_other_pal=0 dicom_fix=0 \
	dicom_control=0 bt865_ucode_timeout=0 audio_driver=oss



```Note: the commented lines were mostly added when I tried to install the em8300 packages using Synaptic or with debs from the debian repository (which had a newer version). I haven't added a remove command (yet) because I'm not sure how necessary it is

This worked until the last 2 kernel updates (2.6.24-17 & 2.6.24-18). 2.6.24-17 obviously broke the modules again and was an opportunity for me to upgrade em8300 from 0.17-rc1 to the final version. Now comes the bit I didn't know about and had me stumped. I re-compiled the em8300 modules against 2.6.24-18. But they wouldn't load. FATAL: file not found etc. But I _could_ see them in nautilus. 'Search for files' didn't find them either. After some research I find out the 'locate' can find files in terminal. But that also found nothing. After another hour of research on depmod, I found a suggestion to do an 'updatedb'. And hey presto! the files were 'there'. The OS could finally see the modules as well. 'sudo modprobe em8300' worked and 'cat /proc/em8300' showed the expected results

By the way, is there a typo in your howto?
```
cd em8300-0.17.0/modules
./configure
make
make install
```
Shouldn't this be
```
cd em8300-0.17.0
./configure
cd modules
make
make install
```?

Quite a bit of text. I'll have to get into it all and rework the howto.
Thank you for the elaborate response.
I would have to rewrite parts to support both types of cards, but I'll have to need time for that.

For the last remark (.../modules) We only need the modules to compile, not the support software. I can't see the advantage of do a ./configure in a folder-level higher. To the best of my knowledge it is the same (is it?) result, but without configuring the rest of the source (Utils etc.)
But I'm definitely no expert. If you're sure your way is the best, please say so. I want to be as correct as possible.

Anyway Thanx again. Patience please, as I modify the howto.

Greetz, De Bubbel :-?

---

### Post by Bubbel on 2008-06-15
Hi Roial,

I revised the howto.
As you can see, I used your variant to get the configuration in there (thru /etc/modprobe.d/em8300). It sure is a more elegant solution.
The problem with 'module not found' is resolved by running depmod. It rebuilds the module cache or something, 'updatedb' didn't work for me.
For the folder to use make in, we need them both. I.e. the em8300-0.17.0 and the em8300-0.17.0/modules. The first one for the supporting software. It's not 100% needed, but as we are installing anyway. You were right in the location of the ./configure command though.

I think it's allright now, but if you find something, please don't hesitate to post again.

Greetz & Thanx, The Bubbel :-?

---

### Post by siddhartha_at on 2008-09-27
First thanks for the howto.

Today i upgraded to Intrepid. After that i had to recompile the modules for the new kernel (2.6.27-4-generic)

For the following list of files you have to correct to sources:
em8300_fifo.h, em8300_alsa.c

change the line ```
#include <asm/semaphore.h>
``` to ```
// #include <asm/semaphore.h>

```

thats all.

But for some reason my device files (/dev/em8300*) are not created. I also tried to create them manually but after a reboot the files are again missing.

---

