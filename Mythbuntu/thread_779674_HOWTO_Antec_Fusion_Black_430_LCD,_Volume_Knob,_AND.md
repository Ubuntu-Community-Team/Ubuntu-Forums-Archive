---
title: "HOWTO: Antec Fusion Black 430 LCD, Volume Knob, AND Hauppauge Remote w/ 8.04"
date: 2008-05-02
forum: Mythbuntu
---

### Post by gazer22 on 2008-05-02
For those (millions) of you with an Antec Black 430 Case and a Hauppauge (non-MCE) remote, here's how I got mine all working together with Mythbuntu 8.04.  

For [COLOR=Red]8.10[/COLOR], please go to this thread: [http://ubuntuforums.org/showthread.php?t=1069267]("http://ubuntuforums.org/showthread.php?t=1069267")

(Note: typos updated as of 14feb09, 0200 UTC)
(Note: slightly modified LCDd.conf in the attached file as of 13feb09)


This hauppauge remote **[COLOR=Red]does not work[/COLOR]** with the IR receiver on the front of the Antec case.  These instructions are for  those hauppauge remotes that have their own receivers that plug into the PCI card.

If you're trying to use a MCE remote with Antec's IR module on this case, I can't help you, but feel free to reply with instructions!  (Hint: it's made by soundgraph, and likely ONLY works with an MCE remote)

Thanks to venky and the codeka folks for all of their work!

Before beginning, make sure you have some required development packages:
```
sudo apt-get install build-essential automake autoconf autotools-dev libtool cvs
```
Also, ensure that the /usr/local/src directory is there and is writable by all:
```

sudo mkdir /usr/local/src
sudo chmod ugo+rwx /usr/local/src
```

Now, let's get the [COLOR=Navy]LCD[/COLOR] working:
[LIST=1]
[*] First, download lcdproc and codeka's patch, compile it and install it:
```
cd /usr/local/src
wget http://internap.dl.sourceforge.net/sourceforge/lcdproc/lcdproc-0.5.2.tar.gz
tar -zxvf lcdproc-0.5.2.tar.gz
cd /usr/local/src/lcdproc-0.5.2
wget http://codeka.com/blogs/imon/lcdproc-0.5.2-imonlcd-0.3.patch
patch -p1 < lcdproc-0.5.2-imonlcd-0.3.patch
aclocal && autoconf && automake
./configure --enable-drivers=imonlcd
make
sudo make install
sudo cp scripts/init-LCDd.debian /etc/init.d/LCDd
sudo chmod +x /etc/init.d/LCDd
sudo update-rc.d LCDd defaults
```
[*] Next, copy the attached gz file to a convenient directory and untar it:
```
tar -zxvf antec_lirc_lcd.tar.gz
```This will create a subdirectory named "antec" from whatever directory the tar.gz file is in.
[*]Copy the file "LCDd.conf" from the antec subdirectory to /usr/local/etc:
```
sudo cp antec/LCDd.conf /usr/local/etc/.
```
[/LIST]

Now, lets get the volume knob and Hauppauge remote working via lirc.
[LIST=1]
[*] First, download the source code for lirc from cvs (login is anonymous, no password - just hit enter):
```

cd /usr/local/src
cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login
cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc
cd lirc
./autogen.sh
./configure --prefix=/usr --with-driver=all

```
[*]Manually edit this file: /usr/local/src/lirc/drivers/Makefile to remove any drivers from that list you aren't interested in.
The three parameters in that file you want to edit are: lirc_driver, DIST_SUBDIRS, and SUBDIRS - want imon_dev imon imon_i2c
**[COLOR=Red]OR:[/COLOR]** just copy my example over:
```
cp antec/lirc.drivers.Makefile /usr/local/src/lirc/drivers/Makefile
```
[*]Edit config.h so that the line: /* #undef LIRC_IMON_LCD */ becomes:  #define LIRC_IMON_LCD 1
**[COLOR=Red]OR:[/COLOR]** just copy my example over:
```
cp antec/lirc.config.h /usr/local/src/lirc/config.h
```
[*]Make lirc, but [COLOR=Red]DO NOT INSTALL IT!![/COLOR]:
```

cd /usr/local/src/lirc
make

```
[*]Backup the default drivers and add these new ones:
```

export rev_temp=`uname -r`
sudo mkdir /lib/modules/$rev_temp/misc
sudo cp -a /usr/local/src/lirc/drivers/lirc_i2c/lirc_i2c.ko /lib/modules/$rev_temp/misc/.
sudo cp -a /usr/local/src/lirc/drivers/lirc_dev/lirc_dev.ko /lib/modules/$rev_temp/misc/.
sudo cp -a /usr/local/src/lirc/drivers/lirc_imon/lirc_imon.ko /lib/modules/$rev_temp/misc/.

sudo mv /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_dev/lirc_dev.ko{,.OLD} 
sudo mv /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_imon/lirc_imon.ko{,.OLD} 
sudo mv /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_i2c/lirc_i2c.ko{,.OLD} 

sudo ln -s /lib/modules/$rev_temp/misc/lirc_imon.ko /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_imon/.
sudo ln -s /lib/modules/$rev_temp/misc/lirc_i2c.ko /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_i2c/.
sudo ln -s /lib/modules/$rev_temp/misc/lirc_dev.ko /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_dev/.

```

[*]Go ahead and load the new modules and start up the LCD:

```

sudo modprobe lirc_imon
sudo modprobe lirc_i2c
sudo /etc/init.d/LCDd start

```
[*]Add the following two lines to /etc/modules using sudo and your favorite editor:
```
lirc_imon
lirc_i2c
```
[*]Backup default configuration files:
```
sudo mv /etc/lirc/hardware.conf /etc/lirc/hardware.conf.orig
sudo mv /etc/lirc/lircd.conf /etc/lirc/lircd.conf.orig
mv ~/.lirc/mythtv ~/.lirc/mythtv.orig
```
[*]Copy files from the tar.gz files over:
```
sudo cp antec/hardware.conf /etc/lirc/.
sudo cp antec/lircd.conf /etc/lirc/.
sudo cp antec/lirc /etc/init.d/.
cp antec/mythtv ~/.lirc/mythtv
```
[*]Note that the file which now resides in ~/.lirc/mythtv is highly personal, and you should feel free to modify the mappings from the remote to MythTV commands.  It's configured for my specific hauppauge remote and the volume knob.
[*]Start lirc:
```
sudo update-rc.d lirc defaults
sudo /etc/init.d/lirc start
```
[/LIST]

TROUBLESHOOTING:

To troubleshoot the remote and/or volume knob:
[LIST=1]
[*]Make sure that no lircd processes are running:
```
sudo /etc/init.d/lirc stop
```
[*]Ensure that there are (at least) two lirc devices, lirc0 and lirc1:
```
ls -l /dev/lirc*
```
[*]Use mode2 for each of the devices - after running the command from the command line, press some buttons on the remote and/or rotate the volume knob.  You should get some codes appearing in the terminal window.  If not, the modules (lirc_imon and lirc_i2c) aren't configured quite right.  Hit CTRL-C to exit:
```
sudo mode2 -d /dev/lirc0
sudo mode2 -d /dev/lirc1
```
[*]If mode2 works for both lirc devices, go ahead and restart lirc:
```
sudo /etc/init.d/lirc start
```
[*]Run irw from the command line and then press some buttons on the remote and move the volume knob around.  You should get codes from each button press/volume knob turn.  They should identify the button/knob correctly.  If not, check your hardware.conf, lircd.conf, and /etc/init.d/lirc for errors.  Hit CTRL-C to exit:
```
irw
```
[*]If that works, but myth isn't responding to your commands, check your .lirc/mythtv file and your .lircrc file, which should include .lirc/mythtv.
[/LIST]

Good luck!

:guitar:

---

### Post by wombo on 2008-05-03
Hey this looks fantastic. nice work.

My comments
I think this is a spelling mistake in Section 3
sudo cp antec/LCDd.conf /[COLOR="Red"]etc[/COLOR]/local/etc/
sudo cp antec/LCDd.conf /usr/local/etc/

I fixed my first problem, for everyone else you need to have the following installed.
build-essentials
aclocal
libtool

Currently I have both the knob and IR working ok!! But I am still having some troubles with the LCD.

I get this result
```
htpc@htpc:/dev$ sudo echo -e "lirc_imon\nlirc_i2c" >> /etc/modules
-bash: /etc/modules: Permission denied
htpc@htpc:/dev$ 
```

---

### Post by tedder on 2008-05-03
I'm also having issues getting LCDd started:

Starting LCDproc display server daemon: Could not open driver module server/drivers/curses.so: server/drivers/curses.so: cannot open shared object file: No such file or directory

There's no "curses.so" on my machine. In the \[curses\] section, I could always set File=libcurses.so, but the path would be wrong. What's supposed to be done? Do you have a curses.so on your machine, and what installed it?

---

### Post by tedder on 2008-05-03
okay, so I needed to manually copy curses.so from the source tree over to my machine.

Still doesn't work, though. When I start LCDd, it displays in my ssh window (console). I assume I need to set "device=" to something. But what?

lsusb gives this:
```
Bus 001 Device 005: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
```

I don't have a /dev/lcd.

---

### Post by gazer22 on 2008-05-03
> **wombo said:**
> Hey this looks fantastic. nice work.

Thanks!

> **wombo said:**
> sudo cp antec/LCDd.conf /[COLOR="Red"]usr[/COLOR]/local/etc/
Yup, thanks.  Unless you change the configuration in lcdproc, it will install the configuration files in  /usr/local/etc


> **wombo said:**
> I fixed my first problem, for everyone else you need to have the following installed.
build-essentials
aclocal
libtool

Yes, additional things need to be installed from the base Mythbuntu install.  I have a hard time tracking which packages I've added... :)

> **wombo said:**
> I get this result
```
htpc@htpc:/dev$ sudo echo -e "lirc_imon\nlirc_i2c" >> /etc/modules
-bash: /etc/modules: Permission denied
htpc@htpc:/dev$ 
```
It's probably trying to ask for your password, but is thwarted by the redirection.  Go ahead and manually add the two lines:
```

lirc_imon
lirc_i2c
```
to /etc/modules using sudo and your favorite editor.

---

### Post by gazer22 on 2008-05-03
> **tedder said:**
> Starting LCDproc display server daemon: Could not open driver module server/drivers/curses.so: server/drivers/curses.so: cannot open shared object file: No such file or directory

This is likely related to the typo wombo found in my original instructions (now fixed!).

Make sure you copy antec/LCDd.conf to /[COLOR="Red"]usr[/COLOR]/local/etc/.

Double check that the Driver= line reads Driver=imonlcd and any other Driver= lines are commented out (around line 45 in LCDd.conf).

---

### Post by wombo on 2008-05-03
IT WORKED!!!

YOUR A CHAMPION!!!

Thank you so much its been sitting there dead for ages and now its working.:)

---

### Post by Juzz on 2008-05-03
The package is:
build-essential

I can't find aclocal in the repository - do you have other repositories added?
EDIT:
According to this:
[http://ubuntuforums.org/archive/index.php/t-6149.html](http://ubuntuforums.org/archive/index.php/t-6149.html)

aclocal is in the automake package.

You also need the cvs package!

---

### Post by Juzz on 2008-05-03
What distro are you running?

On a Mythbuntu install I am having trouble getting this to get past the lirc make.

Either some packages are missing or you are running another distro with mythbuntu added through repository.

---

### Post by gazer22 on 2008-05-03
> **Juzz said:**
> What distro are you running?

I started with the regular Mythbuntu 8.04 distro, asked it to install Ubuntu desktop (for other reasons), and added quite a few packages on top of that (mostly for other stuff).

Thanks, I fixed the apt-get install line for build-essential, added cvs, and switched aclocal to automake.

Might also be missing autoconf and autotools-dev, so they're on the apt-get line now too.

---

### Post by wombo on 2008-05-03
> **Juzz said:**
> On a Mythbuntu install I am having trouble getting this to get past the lirc make.

I think I had to add libtool to get that to work

---

### Post by Juzz on 2008-05-05
By the way:
There's a shorthand for your backup copying:

```
sudo mv /lib/modules/2.6.24-16-generic/ubuntu/media/lirc/lirc_dev/lirc_dev.ko{,.OLD}
sudo mv /lib/modules/2.6.24-16-generic/ubuntu/media/lirc/lirc_imon/lirc_imon.ko{,.OLD}
sudo mv /lib/modules/2.6.24-16-generic/ubuntu/media/lirc/lirc_i2c/lirc_i2c.ko{,.OLD}

```
;)

---

### Post by gazer22 on 2008-05-06
> **Juzz said:**
> By the way:
There's a shorthand for your backup copying:

```
sudo mv /lib/modules/2.6.24-16-generic/ubuntu/media/lirc/lirc_dev/lirc_dev.ko{,.OLD}
sudo mv /lib/modules/2.6.24-16-generic/ubuntu/media/lirc/lirc_imon/lirc_imon.ko{,.OLD}
sudo mv /lib/modules/2.6.24-16-generic/ubuntu/media/lirc/lirc_i2c/lirc_i2c.ko{,.OLD}

```
;)


Nice one.  Thanks.

---

### Post by bwooster0 on 2008-05-10
Before I could do "sudo /etc/init.d/LCDd start" I had to do:

"sudo chmod +x /etc/init.d/LCDd"

---

### Post by bwooster0 on 2008-05-10
I think that step 9 needs a line to be changed to:

"sudo cp antec/lirc /etc/init.d/"

---

### Post by gazer22 on 2008-05-10
Correct on both - thanks.

OP updated.

---

### Post by justinux on 2008-05-11
Thank you for this information, it's very helpful.

I have got my remote and volume knob working but still no luck with the display.

when starting LCDd, and MythTV nothing comes up on the display.  Any suggestions?

---

### Post by wombo on 2008-05-12
What would I have to modify your configuration to support a Windows MCE remote?

Thanks

---

### Post by axelsvag on 2008-05-12
You could try this [HTML]http://ubuntuforums.org/showthread.php?t=723003[/HTML]

---

### Post by gazer22 on 2008-05-12
> **justinux said:**
> ...still no luck with the display.  When starting LCDd, and MythTV nothing comes up on the display.  Any suggestions?

If LCDd is working, you should get a rather generic text on the LCD (LCDproc... Cli... some #'s).  If you get that, then you just need to ensure that you've turned on MythTV's lcd output in the frontend.  (Utilities/Setup->Setup->Appearance)

If you have no text at all on the LCD, you should double check LCDd.conf to ensure that Driver=imonlcd and the device (/dev/lcd0) and contrast (200-ish) settings are reasonable in the [imonlcd] settings.

---

### Post by gazer22 on 2008-05-12
> **wombo said:**
> What would I have to modify your configuration to support a Windows MCE remote?


Completely guessing, but...

[LIST]
[*]You might not have TWO lirc devices, assuming that the volume knob and MCE remote are treated as one device by the soundgraph module.  This means that you don't need the modified hardware.conf and /etc/init.d/lirc
[*]You need a different lircd.conf file.  Can be generated via irremote, or find one to match the MCE remote.  May need to add the portion for the volume knob.
[*]Need a different .lirc/mythtv file to map the remote's buttons to mythtv.
[/LIST]

If the volume knob is working, you should be able to get codes using "mode2" as described in the Troubleshooting section.  If you get codes from mode2, then the next step is to ensure the lircd.conf file is configured correctly, then you should be able to get good output from "irw."  After that, the .lirc/mythtv configuration is the last step to getting the buttons working with MythTV.

---

### Post by justinux on 2008-05-12
> **gazer22 said:**
> If you have no text at all on the LCD, you should double check LCDd.conf to ensure that Driver=imonlcd ...

"imonlcd" ???

LCDd.conf from this post's attachment uses ```
Driver=imon
``` and has settings under ```
[imon]
```.  Is there a difference if we use imonlcd or just imon?

---

### Post by gazer22 on 2008-05-12
> **justinux said:**
> "imonlcd" ???

LCDd.conf from this post's attachment uses ```
Driver=imon
``` and has settings under ```
[imon]
```.  Is there a difference if we use imonlcd or just imon?

In the LCDd.conf in the original post's antec_lirc_lcd.tar.gz, it uses Driver=imonlcd (Driver=curses and Driver=imon are commented out).

Absolutely a difference between imon and imonlcd.  That's what the codeka patch in the first step does.  For more details on the codeka patch, go [here]("http://codeka.com/blogs/index.php?cat=30").

---

### Post by justinux on 2008-05-12
Thank you for your help.  I'm so close I can smell it.

I have double-checked that I am using the LCDd.conf attached with this post, and it does specify imonlcd as the driver.

I get the following when I set reporting to stderr and run LCDd directly (or through /etc/init.d/LCDd):
imonlcd: cannot read Backlight: off, using default -1209052337
imonlcd: sending command: 40

But still nothing shows up on the display.  I know the hardware works because I can get it running in Windows just fine.  I may end up trying again from a fresh install, but I hope not to.

---

### Post by gazer22 on 2008-05-13
> **justinux said:**
> I get the following when I set reporting to stderr and run LCDd directly (or through /etc/init.d/LCDd):
imonlcd: cannot read Backlight: off, using default -1209052337
imonlcd: sending command: 40

This comes from me accidentally leaving Backlight=off in LCDd.conf.  It doesn't work, does generate that error, but shouldn't do anything else.  Go ahead and comment it out to get rid of that error.

I don't have too much experience debugging the LCD, as "it just worked" with the patch from codeka.

That said, double check that the screen is getting power (the backlight should always be on), and that the usb header is plugged in correctly to your motherboard (lsusb should list a SoundGraph iMon PAD Remote Controller), and try running lcdproc in foreground mode (this runs instead of mythlcdserver) - first make sure to kill any running mythlcdserver processes, then:
```
sudo /etc/init.d/LCDd stop; sudo LCDd -f -r 5
```
Then, in a different window:
```
 lcdproc -f
```

If you're still stuck, check out the codeka forums [here]("http://codeka.com/forums/").

---

### Post by justinux on 2008-05-14
Well,
I ended up re-installing a fresh new build and everything works.  I installed some updates, which broke it (/dev/lcd0 wouldn't come up) so I just followed the instructions through again, and everything was back up and working.

Thanks

---

### Post by gazer22 on 2008-05-14
Awesome!  Glad it works.

> **justinux said:**
> /dev/lcd0 wouldn't come up

Yeah, if you don't have /dev/lcd0, that indicates something goofy with the /etc/init.d/LCDd script or the /usr/local/sbin/LCDd binary.

---

### Post by Shorty36 on 2008-05-26
Gazer22, you ROCK!!  :guitar:

I just picked up one of these cases, and your instructions were spot on.  Everything works!

Thanks so much for your work on this.

---

### Post by khanw on 2008-05-26
Hi,

When trying to run through the steps you described I get an error while trying to build lirc:

configure: error: *** you need to have the Linux kernel source installed for this driver

I don't have the kernel source installed and remember from earlier attempts that I had trouble installing a source that matched my installed kernel. Could someone give me a pointer as to how I do that?

I'm running Mythbuntu 8.04 with kernel 2.6.24-17-generic

Thanks!

---

### Post by gazer22 on 2008-05-26
> **khanw said:**
> 
When trying to run through the steps you described I get an error while trying to build lirc:

configure: error: *** you need to have the Linux kernel source installed for this driver


Hmmm, I don't have linux-source* installed either (at least not to my knowledge!).

I just got the upgrade to 2.6.24-17, so I refreshed my lirc directory, and re-tried the configuration.

After running autogen.sh, configure gave me this line (among many others):
```
checking for Linux kernel sources... /lib/modules/2.6.24-17-generic/build/
```

No idea how it got there, though...

Configure worked fine for me.  

Might want to check here:  [http://www.lirc.org/]("http://www.lirc.org/")

---

### Post by boffyflow on 2008-05-28
> **gazer22 said:**
> If LCDd is working, you should get a rather generic text on the LCD (LCDproc... Cli... some #'s).  If you get that, then you just need to ensure that you've turned on MythTV's lcd output in the frontend.  (Utilities/Setup->Setup->Appearance)

If you have no text at all on the LCD, you should double check LCDd.conf to ensure that Driver=imonlcd and the device (/dev/lcd0) and contrast (200-ish) settings are reasonable in the [imonlcd] settings.

I had everything working really nicely 2 days ago. But yesterday the LCD starting displaying a simple clock (that strangely was 9 minutes different than the CPU clock). I tried restarting the daemon and also restarting the machine but to no avail. The clock is now constantly displayed - even after shutting down the frontend. I have not updated the system since I followed these instructions. Does anybody have an idea what is going on?

Thanks.

---

### Post by gazer22 on 2008-05-28
> **boffyflow said:**
> I had everything working really nicely 2 days ago. But yesterday the LCD starting displaying a simple clock... Does anybody have an idea what is going on?

Are you sure you didn't update the system?  Try:
```
uname -r
```

If you get 2.6.24-17 or similar (the 17 is important), then your kernel was updated over the past couple of days (as was mine).

If that's the case, I think the kernel is looking for the driver files where they are not yet located.

The simple thing might be to set up symbolic links from the expected location to your old location:
```

export rev_temp=`uname -r`
sudo ln -s /lib/modules/2.6.24-16-generic/misc/lirc_imon.ko /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_imon/.
sudo ln -s /lib/modules/2.6.24-16-generic/misc/lirc_i2c.ko /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_i2c/.
sudo ln -s /lib/modules/2.6.24-16-generic/misc/lirc_dev.ko /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_dev/.

```
But, this might cause trouble if you get rid of the 2.6.24-16 kernel.

Another way would be to go back to your /usr/local/src/lirc directory and just re-copy the drivers to a new /lib/modules/2.6.24-17-generic/misc directory:
```

cd /usr/local/src/lirc
export rev_temp=`uname -r`
sudo mkdir /lib/modules/$rev_temp/misc
sudo cp -a /usr/local/src/lirc/drivers/lirc_i2c/lirc_i2c.ko /lib/modules/$rev_temp/misc/.
sudo cp -a /usr/local/src/lirc/drivers/lirc_dev/lirc_dev.ko /lib/modules/$rev_temp/misc/.
sudo cp -a /usr/local/src/lirc/drivers/lirc_imon/lirc_imon.ko /lib/modules/$rev_temp/misc/.

sudo mv /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_dev/lirc_dev.ko{,.OLD} 
sudo mv /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_imon/lirc_imon.ko{,.OLD} 
sudo mv /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_i2c/lirc_i2c.ko{,.OLD} 

sudo ln -s /lib/modules/$rev_temp/misc/lirc_imon.ko /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_imon/.
sudo ln -s /lib/modules/$rev_temp/misc/lirc_i2c.ko /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_i2c/.
sudo ln -s /lib/modules/$rev_temp/misc/lirc_dev.ko /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_dev/.

```

Hope that's it!

Does anyone know if this has to be done with every kernel update?

---

### Post by boffyflow on 2008-05-28
> **gazer22 said:**
> Are you sure you didn't update the system?  Try:
```
uname -r
```

If you get 2.6.24-17 or similar (the 17 is important), then your kernel was updated over the past couple of days (as was mine).

If that's the case, I think the kernel is looking for the driver files where they are not yet located.

The simple thing might be to set up symbolic links from the expected location to your old location:
```

export rev_temp=`uname -r`
sudo ln -s /lib/modules/2.6.24-16-generic/misc/lirc_imon.ko /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_imon/.
sudo ln -s /lib/modules/2.6.24-16-generic/misc/lirc_i2c.ko /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_i2c/.
sudo ln -s /lib/modules/2.6.24-16-generic/misc/lirc_dev.ko /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_dev/.

```
But, this might cause trouble if you get rid of the 2.6.24-16 kernel.

Another way would be to go back to your /usr/local/src/lirc directory and just re-copy the drivers to a new /lib/modules/2.6.24-17-generic/misc directory:
```

cd /usr/local/src/lirc
export rev_temp=`uname -r`
sudo mkdir /lib/modules/$rev_temp/misc
sudo cp -a /usr/local/src/lirc/drivers/lirc_i2c/lirc_i2c.ko /lib/modules/$rev_temp/misc/.
sudo cp -a /usr/local/src/lirc/drivers/lirc_dev/lirc_dev.ko /lib/modules/$rev_temp/misc/.
sudo cp -a /usr/local/src/lirc/drivers/lirc_imon/lirc_imon.ko /lib/modules/$rev_temp/misc/.

sudo mv /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_dev/lirc_dev.ko{,.OLD} 
sudo mv /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_imon/lirc_imon.ko{,.OLD} 
sudo mv /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_i2c/lirc_i2c.ko{,.OLD} 

sudo ln -s /lib/modules/$rev_temp/misc/lirc_imon.ko /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_imon/.
sudo ln -s /lib/modules/$rev_temp/misc/lirc_i2c.ko /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_i2c/.
sudo ln -s /lib/modules/$rev_temp/misc/lirc_dev.ko /lib/modules/$rev_temp/ubuntu/media/lirc/lirc_dev/.

```

Hope that's it!

Does anyone know if this has to be done with every kernel update?


I don't have access the the mythbox right now, but wouldn't I have problems with the remote and the volume knob if I had upgraded the kernel? I will report back later tonight.

Thanks.

---

### Post by gazer22 on 2008-05-28
> **boffyflow said:**
> ...but wouldn't I have problems with the remote and the volume knob if I had upgraded the kernel?

What?!? That sounds rational!  ;)

No idea - my remote was still working, but the LCD was as described - the ugly clock.

---

### Post by boffyflow on 2008-05-29
> **gazer22 said:**
> What?!? That sounds rational!  ;)

No idea - my remote was still working, but the LCD was as described - the ugly clock.

Still no luck. I had not updated the kernel to 17. But just to be on the same page I now did update Ubuntu to the latest and greatest (incl. kernel 17) and followed your instructions. Remote and volume still working, but I still have the ugly clock. I went back to your original instructions and double checked everything and I think I may have found the culprit. It seems as if the LCDd daemon cannot start. There is no error message, but it just shows:
[INDENT]Starting LCDproc display server daemon:[/INDENT]

I also noticed that I do not have a /dev/lcd device only a /dev/lcd0 device, so I tried changing the device in the /usr/local/etc/LCDd.conf file, but that didn't help either...

---

### Post by wonko69 on 2008-05-29
I have been tinkering with the volume button and LCD display for a few hours now. The volume button worked like a charm (only the box doesnt respond to the changes in volume, must be the wrong mixer) and after I installed imonlcd like it the howto the LCD worked. Now the thing is that during the boot process the time is displayed in am/pm format, that doesnt bother me. But for some reason after Mythtv starts the display changes to:
LCDproc server
cli: 1 src: 7

Any one got any ideas on howto get it working with mythtv?

I have setup mythtv to have a LCD display.

Best regards


PS Thanks for a super Howto guide.

---

### Post by gazer22 on 2008-05-29
> **boffyflow said:**
> It seems as if the LCDd daemon cannot start. There is no error message, but it just shows:
[INDENT]Starting LCDproc display server daemon:[/INDENT]

If you get this by running:
```
sudo /etc/init.d/LCDd restart
```
Then something is likely goofy with /etc/init.d/LCDd  a good response is:
```
user@mediapc:~$ sudo /etc/init.d/LCDd restart
[sudo] password for user: 
Stopping LCDproc display server daemon: LCDd.Starting LCDproc display server daemon: imonlcd: sending command: 40

```

> **boffyflow said:**
> 
I also noticed that I do not have a /dev/lcd device only a /dev/lcd0 device...
You're supposed to have /dev/lcd0, not anything else.

---

### Post by gazer22 on 2008-05-29
> **wonko69 said:**
> ...for some reason after Mythtv starts the display changes to:
LCDproc server
cli: 1 src: 7


If you have the LCDproc server screen, then the LCD is working okay.  

mythlcdserver (make sure it's running via "ps -e | grep myth*") has been acting a little weird recently for me.  After rebooting, and starting mythtv, the LCD would give me the above-mentioned LCDproc server screen until I started moving around in the mythtv screens and playing a recorded video.  After that, it started acting normally, and stayed up.

Try moving around in the mythtv menus and playing some videos - does that bring up the normal myth lcd screens?

---

### Post by wonko69 on 2008-05-30
> **gazer22 said:**
> 
Try moving around in the mythtv menus and playing some videos - does that bring up the normal myth lcd screens?

If I go through the appreance setup, the screen comes up normal. But that might be from just restarting the Mythtv front app.
Would be interesting to know what causes the display change.

---

### Post by boffyflow on 2008-05-30
> **gazer22 said:**
> If you get this by running:
```
sudo /etc/init.d/LCDd restart
```
Then something is likely goofy with /etc/init.d/LCDd  a good response is:
```
user@mediapc:~$ sudo /etc/init.d/LCDd restart
[sudo] password for user: 
Stopping LCDproc display server daemon: LCDd.Starting LCDproc display server daemon: imonlcd: sending command: 40

```


You're supposed to have /dev/lcd0, not anything else.

Yeh! Got it working again. I went back through your initial instructions and rebuilt everything against .17 kernel. I rebooted a couple of times and it seems as if the LCD and the remote/volume are stable now. I did notice that the LCD displays sometimes just the system setting and you have the move around the menus in myth before the display catches the menus. It seems a little flaky, but overall I am a pretty happy now. Thanks for you help gazer22.

---

### Post by eriklindered on 2008-06-15
Hi 

Im gettig this when im starting LCDd

Starting LCDproc display server daemon: imonlcd: sending command: 5000000000000040

and nothin happend on the screen

What do i do ?

---

### Post by gazer22 on 2008-06-16
> **eriklindered said:**
> I'm getting this when starting LCDd:

Starting LCDproc display server daemon: imonlcd: sending command: 5000000000000040

and nothing on the screen

What do i do ?

If you have no text at all on the LCD, you should double check LCDd.conf to ensure that Driver=imonlcd and the device (/dev/lcd0) and contrast (200-ish) settings are reasonable in the [imonlcd] settings.

If that's good, double check that the screen is getting power (the backlight should always be on), and that the usb header is plugged in correctly to your motherboard (lsusb should list a SoundGraph iMon PAD Remote Controller), and try running lcdproc in foreground mode (this runs instead of mythlcdserver) - first make sure to kill any running mythlcdserver processes, then:
```
sudo /etc/init.d/LCDd stop; sudo LCDd -f 
```
Then, in a different window:
```
 lcdproc -f
```

If you're still stuck, check out the codeka forums [here]("http://codeka.com/forums/").

---

### Post by spencer0749 on 2008-07-06
Ok. I followed the instructions given but I'm having problems.

When ever I start the LCDd program I get a bunch of random characters  scrolling rapidly across the screen.  If I kill LCDd I can use echo to print strings.

---

### Post by gazer22 on 2008-07-08
> **spencer0749 said:**
> 
When ever I start the LCDd program I get a bunch of random characters  scrolling rapidly across the screen.  If I kill LCDd I can use echo to print strings.

Hmmm.  Tough one.  Haven't seen that before.

what's your output from lsusb?
Should include this:
```
Bus 003 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
```

If LCDd is stopped, you shouldn't be able to get anything on the screen, so that's weird.

The output of "ps -e | grep -si lcd" should be something like (if you're running mythtv):
```
user@htpc:~$ ps -e | grep -si lcd
 5607 ?        00:00:20 LCDd
 7205 ?        00:00:11 mythlcdserver
```

The output of "lsmod | grep -si imon" should look something like this:
```
user@htpc:~$ lsmod | grep -si imon
lirc_imon              18308  2 
lirc_dev               15556  2 lirc_i2c,lirc_imon
usbcore               146028  5 lirc_imon,ohci_hcd,ehci_hcd
 
```

The output of "ls /dev/lcd*" should be:
```
user@htpc:~$ ls /dev/lcd*
/dev/lcd0
```

If all that looks good (and it probably will if you're able to get some text to the LCD), check out this post for getting debugging output from LCDd: [post #25 from this thread]("http://ubuntuforums.org/showpost.php?p=4952743&postcount=25")

The people over at [codeka.com]("http://codeka.com/forums/viewforum.php?f=3&sid=39f4bf6e0eb2a88a70c550a05feecb69") are the actual brains behind the lcd patch, and they have an active forum which might be able to provide more technical troubleshooting help: [Codeka.com forum]("http://codeka.com/forums/viewforum.php?f=3&sid=39f4bf6e0eb2a88a70c550a05feecb69")

---

### Post by semafour on 2008-07-23
Hi everyone.

This is probably the most detailed set of steps to get everything working on the Antec Fusion Black 430.

I'm right up with you, up until Step 4, when I have to make. I'm getting errors.

If this thread is still alive, and someone can help me, that would be great. I'm running the newest version of Ubuntu Server (8.04.1).

Thanks guys. This is incredibly frustrating, as the only reason I bought this case was because I saw threads like this where everyone was able to get the LCD working. I lack an IR remote, so I'm only interested in getting the LCD screen working and the right-hand-side knob.

If you need any (or all) output of my steps, let me know. I'm not posting at the moment because I'm not at the computer that I'm trying to install it on.

EDIT:
This works like a charm with mythbuntu. There must be some important differences or requirements that Ubuntu Server does not contain. Is there a chance anyone knows what those are?

Thanks so much!

---

### Post by gazer22 on 2008-07-25
> **semafour said:**
> I'm right up with you, up until Step 4, when I have to make. I'm getting errors...
I'm running the newest version of Ubuntu Server (8.04.1).

...I'm only interested in getting the LCD screen working and the right-hand-side knob.


Okay, starting with the last point first.  To get the LCD and volume knob, you still need to do the modifications to LCDd and lirc.  You won't need all of the modifications to hardware.conf and lircd.conf, but you'll need some of them.  That shouldn't be a huge deal though, and isn't holding you up now.

Exactly what command is giving you trouble?  You are correct that you're likely just missing a package that comes by default with the mythbuntu distribution, but not the ubuntu server distribution.

As noted at the top of the HOWTO, the following packages are required on top of the standard mythbuntu distro, so make sure those are installed on your system too!:
```
sudo apt-get install build-essential automake autoconf autotools-dev libtool cvs
```

---

### Post by semafour on 2008-07-27
Thanks for the quick reply. The following is giving me trouble:

4. Make lirc, but DO NOT INSTALL IT!!:
Code:
```
cd /usr/local/src/lirc
make
```

Specifically, make. When running make, as root, here's my issue:

```
root@box:/usr/local/src/lirc# make
Makefile:187: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop.

```

Makefile around line 187 is the following:
```
kernelcc =
  ERROR: Kernel configuration is invalid.
         include/linux/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.

```
where "include/linux/autoconf.h ..." is line 187.

I have installed all the packages suggested by you in your opening post. Thanks for the help.

---

### Post by gazer22 on 2008-07-27
> **semafour said:**
> The following is giving me trouble:
```
cd /usr/local/src/lirc
make
```
... When running make, as root, here's my issue...

Hmmm - a couple of things:
[LIST=1]
[*]**Do you have the linux-headers-generic package installed?**  (Check this before moving on.  I'm guessing that it's required...)
```
user@htpc:/usr/local/src/lirc/drivers$ dpkg-query -l *headers*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                    Version                 Description
+++-=======================-=======================-==============================================================
un  libqt3-compat-headers   <none>                  (no description available)
ii  libqt3-headers          3:3.3.8-b-0ubuntu3      Qt3 header files
un  libqt3-plugins-headers  <none>                  (no description available)
ii  libxmu-headers          2:1.0.4-1               X11 miscellaneous utility library headers
un  linux-headers           <none>                  (no description available)
un  linux-headers-2.6       <none>                  (no description available)
ii  linux-headers-2.6.24-16 2.6.24-16.30            Header files related to Linux kernel version 2.6.24
ii  linux-headers-2.6.24-16 2.6.24-16.30            Linux kernel headers for version 2.6.24 on x86/x86_64
ii  linux-headers-2.6.24-17 2.6.24-17.31            Header files related to Linux kernel version 2.6.24
ii  linux-headers-2.6.24-17 2.6.24-17.31            Linux kernel headers for version 2.6.24 on x86/x86_64
ii  linux-headers-2.6.24-18 2.6.24-18.32            Header files related to Linux kernel version 2.6.24
ii  linux-headers-2.6.24-18 2.6.24-18.32            Linux kernel headers for version 2.6.24 on x86/x86_64
ii  linux-headers-2.6.24-19 2.6.24-19.36            Header files related to Linux kernel version 2.6.24
ii  linux-headers-2.6.24-19 2.6.24-19.36            Linux kernel headers for version 2.6.24 on x86/x86_64
ii  linux-headers-generic   2.6.24.19.21            Generic Linux kernel headers
un  linux-kernel-headers    <none>                  (no description available)

```
[*]What happens if you run the instructions NOT as root, but as a regular user?  (You may need to sudo chmod go+rw /usr/local/src).
[*]What are the outputs of the previous ./autogen.sh and ./configure lines?  Should look like:
```
user@htpc:/usr/local/src/lirc$ ./autogen.sh 
configure.ac:16: installing `./compile'
configure.ac:9: installing `./install-sh'
configure.ac:9: installing `./missing'
daemons/Makefile.am: installing `./depcomp'
Creating setup-driver.sh ...

user@htpc:/usr/local/src/lirc$ ./configure --prefix=/usr --with-driver=all
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
...
-bunch of checking for stuff-
...
config.status: creating doc/man/Makefile
config.status: creating config.h
config.status: executing depfiles commands

All kernel modules will be built.

Now enter 'make' and 'make install' to compile and install the package.

```
[*]To check the above, it might be worthwhile to ```
rm -fR /usr/local/src/lirc
``` and go back to step 1 to re-download the lirc code into a fresh directory.
[/LIST]

One other thing to check is the contents of /usr/local/src/lirc after the autogen.sh and configure commands.  Should be something like this:
```
user@htpc:/usr/local/src/lirc$ ls
acinclude.m4     config.h        CVS/            ltmain.sh    setup-driver.sh
aclocal.m4       config.h.in     daemons/        Makefile     setup.sh*
ANNOUNCE         config.log      data2setup.sh*  Makefile.am  stamp-h1
AUTHORS          config.status*  depcomp*        Makefile.in  TODO
autogen.sh*      config.sub*     doc/            missing*     tools/
autom4te.cache/  configure*      drivers/        NEWS
ChangeLog        configure.ac    INSTALL         README
compile*         contrib/        install-sh*     remotes/
config.guess*    COPYING         libtool*        setup.data

```

---

### Post by semafour on 2008-08-09
Thanks very much for all the help, gazer22.

What I've ended up doing was installing Ubuntu Desktop. For what I'm doing, I may eventually need X, so I figured why not. Something is seriously lacking for LCD output using lirc on the vanilla server version, and I can't spend the time to find out what.

Now what I need to figure out is how to get the LCD to output arbitrary text (my idea is to have it show the output of the CLI fortune program).

If anyone has any ideas, let me know?

---

### Post by gazer22 on 2008-08-11
> **semafour said:**
> Now what I need to figure out is how to get the LCD to output arbitrary text (my idea is to have it show the output of the CLI fortune program)...

I'd check out this guy's [blog]("http://mythtvblog.blogspot.com/2008/04/mythtv-imon-server-alpha-release-1.html") - Ron's done a lot of work to get all of the whiz-bang features of the screen working.

He has a thread running over at codeka's forums [here]("http://codeka.com/forums/viewtopic.php?f=3&t=46").

I haven't tried it yet, but remain severely tempted...

---

### Post by neoneddy on 2008-08-20
I was able to get the LCD working fine, however if I do, the Microsoft MCe remote (1039) does not work.  Any pointers?  there is another post about this, but I'm still having problem.  Thanks!

---

### Post by gazer22 on 2008-08-24
> **neoneddy said:**
> I was able to get the LCD working fine, however if I do, the Microsoft MCe remote (1039) does not work...

You mean this post: [post 21 of this thread]("http://ubuntuforums.org/showpost.php?p=4942457&postcount=21")?

Might also check the hardware.conf file.

I'm in the middle of a move right now, so the HTPC is packed up in a moving truck!

---

### Post by ljp on 2008-08-25
I have followed these instructions to the letter and now (after much previous struggling, before switching to mythbuntu) have a working LCD. However, the hauppauge remote no longer works correctly (only a few buttons work - up, down left, right & 123456789) and mythtv doesn't respond to the volume control.

I had previously got the remote working correctly via the standard mythbuntu setup (without the LCD) after finding that it outputs to /dev/input/event6 NOT /dev/lirc0. Is there some way I can configure lirc to read both /dev/lirc0 (for the volume control) & /dev/input/event6 (for the remote)? Or should I be able to redirect the hauppauge output to /dev/lirc0 somehow?

I found that the Volume control was responding on /dev/lirc0 using the "mode2 -d /dev/lirc0". However, it doesn't seem to have any effect in mythtv. The button names appear to be locked to [ & ] correctly in .lirc/mythtv.

---

### Post by gazer22 on 2008-09-13
> **ljp said:**
> ...However, the hauppauge remote no longer works correctly (only a few buttons work - up, down left, right & 123456789) and mythtv doesn't respond to the volume control.

...finding that it outputs to /dev/input/event6 NOT /dev/lirc0...


Hmmm, what Hauppauge card are you using, and what is the model of the remote  (Look at the inside of the battery cover - mine reads A415 OH/S 1-4)?

In general, I'd follow the troubleshooting section in my first post.

---

### Post by wobri on 2008-09-22
i am stuck on step 2

where do i find this antec package ?

tar -zxvf antec_lirc_lcd.tar.gz

(woops missed the attachment 

MY BET b:P:lolflag:

---

### Post by NoahsMyBro on 2008-11-11
I'll hopefully have a chance to attempt this sometime this week. Frankly, I'm excited to try it, but first I have to actually get Mythbuntu installed on my Fusion that I bought (last Thanksgiving!), and haven't had time to put into use yet.

I have a quick question though - I've just set up a backend running 8.10, and plan to install 8.10 Frontend on the Fusion. Will this How-To work for 8.10 as well as 8.04? I'm assuming yes, and will try it and post my results if I don't see any reply first, but thought I'd ask here in case there are any known problems.

(Luckily for me, I have nearly the exact components described. I have a silver Antec Fusion with the LCD panel, and I also have the silver Hauppauge PVR-150 Remote, not the MCE edition.)

Thanks.

---

### Post by gazer22 on 2008-11-11
> **NoahsMyBro said:**
> ...Will this How-To work for 8.10 as well as 8.04? 

No idea!  I'm sticking with 8.04 for now.  Let us know how it goes!

---

### Post by NoahsMyBro on 2008-11-14
I won't be trying this out soon after all. I didn't read closely or think clearly before - my backend contains the Hauppauge PVR cards (with the IR sensor), but my Antec Fusion with the volume knob is the frontend. I haven't got a remote and sensor for the front end yet.

If anything changes and I do manage to give it a go, I'll post my results on 8.10.
-------------------------------------------------------------------------------------

I've been sucked in. Soon after writing the above I realized that I could try to get the LCD & volume knob working even if I don't have a remote to configure.

I'm too tired and clueless to understand some of thsi stuff, but I can follow directions. I tried to follow the steps in Post #1 as closely as I could. Some steps seemed to need me to add 'sudo' in front of, though. The fact that I did that could account for the problem I'm seeing, I suppose.

I'm seeing the same result as was mentioned in post #43 ([http://ubuntuforums.org/showpost.php?p=5346449&postcount=43](http://ubuntuforums.org/showpost.php?p=5346449&postcount=43)). If I start LCDd, I get a sequence of random characters scrolling across the LCD, too quickly to read. The scrolling display continues until I stop LCDd.

My output from lsusb DOES include:
"Bus 003 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller"

I don't know how to use echo to send strings to the display, so I can't say whether or not that would happen on my system.

My output of "lsmod | grep -si imon" :
```

lirc_imon              18308  2 
lirc_dev               15556  2 lirc_i2c,lirc_imon
usbcore               146028  5 lirc_imon,ehci_hcd,uhci_hcd

```

ls /dev/lcd* returns /dev/lcd0 .

Whenever I stop the LCDd daemon (service? process?), the display ALWAYS continues to scroll until reaching the end of its sequence, with the final display remaining static showing "_ _ _ _ _ _ _ Q". Interestingly to me, when I shutdown the system, the PC shuts off, the illuminated ring around the power button shuts off, but the LCD display remains lit.

In case it's relevant, my system is running Mythbuntu 8.10.


I'm too tired to even begin trying to understand the Codeka forums right now, but I figured a bit more info about this issue wouldn't hurt.

-- Steve

---

### Post by gazer22 on 2008-11-15
Easy things first: 
> **NoahsMyBro said:**
> Interestingly to me, when I shutdown the system, the PC shuts off, the illuminated ring around the power button shuts off, but the LCD display remains lit.
-That's a "feature" of the Antec case.  The LCD screen is hard-wired to the power supply.

> **NoahsMyBro said:**
> I tried to follow the steps in Post #1 as closely as I could. Some steps seemed to need me to add 'sudo' in front of, though. The fact that I did that could account for the problem I'm seeing, I suppose.

I've assumed that the directory /usr/local/src is readable and writable by everyone on your system.  Check that first.  Otherwise, every command given that requires sudo should have it in the instructions.  The exceptions are the cases when you're asked to edit a file.  Those may require 'sudo gedit /etc/modules' for example.

> **NoahsMyBro said:**
> 
I'm seeing the same result as was mentioned in post #43 ([http://ubuntuforums.org/showpost.php?p=5346449&postcount=43](http://ubuntuforums.org/showpost.php?p=5346449&postcount=43)). If I start LCDd, I get a sequence of random characters scrolling across the LCD, too quickly to read. The scrolling display continues until I stop LCDd.

You can follow post #25 ([http://ubuntuforums.org/showpost.php?p=4952743&postcount=25](http://ubuntuforums.org/showpost.php?p=4952743&postcount=25)) for some help on debugging LCDd with lcdproc.

It may also be that mythtv is sending out gibberish - make sure that it's configured to give output to the lcd.

---

### Post by NoahsMyBro on 2008-11-15
I moved my PVR-150 and remote control to the frontend machine, and while trying to get the remote to work, using the info in this thread: [http://ubuntuforums.org/showpost.php?p=4850005&postcount=1](http://ubuntuforums.org/showpost.php?p=4850005&postcount=1), the LCD display on the Fusion suddenly stopped scrolling the thought-to-be-endless characters, and began showing the date and time. After a reboot the display reverted to the scrolling characters, but if it again goes to the calendar display I'll update this post with the exact display shown.

I don't have any other addl info to add to the thread yet, but thought what I saw was interesting and might help somebody here out.

---

### Post by fatmonk on 2008-11-18
Great How To!

Now have a fully working LCD on my Fusion Black - looking good.

There were a couple of directory changes to make as I am running 8.10.

In Step 5 the lirc directory is now found at:
```
/lib/modules/$rev_temp/kernel/ubuntu/lirc/
```

changing this got me right through to the end and a working LCD.


Not so much luck with the remote though.

My unit came with an iMon PAD remote (which is nice).

After following this through I now have four lirc* entries in /dev/

```
/dev/lircd
/dev/lircd1
/dev/lirc0
/dev/lirc1
```

/dev/lirc1 seems to be where my remote commands are turning up as irw sees pad movements (mouse up/down/left/right I assume), mouse clicks (the remote has a left click and right click button) and number presses BUT nothing else. No other keys generate any output.

The two lircd entries seems a little odd to me.

This is an improvement on previous installs as previously if I hit any button other than those mentioned above the remote would stop working altogether until a reboot of the machine.

Also, the knob on the front isn't generating any output - I'm not too worried about that as I'm not using internal volume control, but I thought I shoudl mention it in case it gives any clues.

Am wondering what to try next - it's close, but not quite there yet.

-FM

---

### Post by ElGeraldo on 2008-12-08
> **gazer22 said:**
> For those (millions) of you with an Antec Black 430 Case and a Hauppauge (non-MCE) remote, here's how I got mine all working together with Mythbuntu 8.04.
I followed your instructions to the letter, and couldn't believe it when the LCD started displaying MythTV status messages. Many thanks!

My elation was short-lived however, because no sooner had I rebooted the PC the LCD was blank again. This was a couple of weeks ago and I had forgotten about getting the LCD working because there were other, more important things broken (ATI display drivers to be exact). I've more-or-less fixed that now, so I can go back to the LCD.

I think I've let Mythbuntu update itself a couple of times since then, so I reckon this may have overwritten something to do with lirc and stopped it working.

I'm still a relative Linux newbie, so please could anyone tell me what files I need to verify are in the correct places for the iMon LCD to work with MythTV? I don't really want to go through this whole procedure again, blindly copying files without actually knowing what they do. If I could just understand what file calls what, etc. I might be able to fix it.

I have an lirc process running on the machine, but I think it may be the wrong one. Irw still takes and displays input from the volume knob. When I tell the system to reboot and it's going through its scripts, a brief message flashes up about there already being an LIRC running, but it's not there long enough to read it.

/var/syslog keeps repeating these messages:

lircd-0.8.3pre1[4060]: failure connecting to localhost
lircd-0.8.3pre1[4060]: Connection refused

I don't care about the remote - I don't have one yet. My system:

 Case : Antec Veris Fusion Black 430 (with the LCD, not VFD)
 Mobo : ASUS M3A78-EM (ATI Radeon HD3200 / 780G chipset)
 CPUs : AMD Athlon X2 4850e 2.5GHz
 RAM : GSKILL 2GB (2*1GB of DDR2 1066)
 HDD : WD6400AACS 640GB, SATA
 DVD : ASUS DRW-2014L1T, SATA
 Tuner: HDHomerun ATSC (both inputs from a DB2 antenna)
 TV : Samsung LN-S4095D 40" 1080p LCD HDTV (on VGA cable)
 LAN: DLink WDA-1320 (running on Atheros restricted driver)
 OS : Mythbuntu 8.04.1

---

### Post by fatmonk on 2008-12-09
Not sure about your dmesg enytries from lircd, but if you allow the automatic updates to upgrade your kernel version the changes you made to get the LCD working will be lost.

Part of the process you followed includes copying various files into the active kernel directory (the $rev_temp variable contains the current running kernel version when running the cp and move commands in step 5).

This means that whenever the kernel version is upgraded the system is no longer using the files in the directory you copied them to, its using the files in the new kernel directories.

I tried bodging my system just by re-copying the files in step 5, but it didn.t work.

So I ended up just going through the process again. You can get pretty quick at it after a couple of gos!

Someone with a bit more knowledge of what the procedure is doing elsewhere may be able to provide a shortcut to getting things working again, but until then I'll just be running through the instuctions in the OP after any kernel upgrades.

-FM

---

### Post by gazer22 on 2008-12-09
> **ElGeraldo said:**
> ... no sooner had I rebooted the PC the LCD was blank again. 
...I think I've let Mythbuntu update itself a couple of times since then, so I reckon this may have overwritten something to do with lirc and stopped it working.
...


FatMonk is right - kernel upgrades will overwrite some files (and move things to other directories), requiring you to re-do the changes.

At a minimum, you have to re-do Step 5: "Backup the default drivers and add these new ones" from the original post.

If that doesn't work, I'd just re-do the whole thing, as FatMonk recommends.

ElGeraldo - can you let me know if just repeating step 5 works for you?  If so, I'll add it to the original post.

Unfortunately, my HTPC is mostly off these days, as I've switched to digital cable, and am waiting until the support for the HD-PVR gets more stable so that the machine will be useful again.  But, that's a story for another thread on another day...  :(

---

### Post by gazer22 on 2008-12-09
> **fatmonk said:**
> 
There were a couple of directory changes to make as I am running 8.10.

In Step 5 the lirc directory is now found at:
```
/lib/modules/$rev_temp/kernel/ubuntu/lirc/
```

changing this got me right through to the end and a working LCD.

Thanks - I've added the info to the original post (now at step 6).  Can you check to ensure that I got it right?  (I'm still in 8.04 land).



> **fatmonk said:**
> 
Not so much luck with the remote though.

My unit came with an iMon PAD remote (which is nice).

After following this through I now have four lirc* entries in /dev/

```
/dev/lircd
/dev/lircd1
/dev/lirc0
/dev/lirc1
```

/dev/lirc1 seems to be where my remote commands are turning up as irw sees pad movements (mouse up/down/left/right I assume), mouse clicks (the remote has a left click and right click button) and number presses BUT nothing else. No other keys generate any output.

The two lircd entries seems a little odd to me.


Hmmm, no experience with the PAD remote, but I have a few guesses.

First, the two lirc entries make sense.  If I remember correctly, the two lircd entries also make sense.

Second, the fact that you're getting some output from irw is good.

It looks like you need to update your ~/.lirc/mythtv file to ensure that it has the correct mappings from your PAD remote to mythtv (or whatever).  If you followed the instructions in the original post to the letter, you would have over-written whatever was in ~/.lirc/mythtv with something that doesn't work with your remote.  The original should be in ~/.lirc/mythtv.orig

Check out [http://lirc.sourceforge.net/remotes/imon/]("http://lirc.sourceforge.net/remotes/imon/") for some hopefully helpful files.  The codes should match what you're getting by running mode2.

Hope that helps, and apologies for the late response!

---

### Post by ElGeraldo on 2008-12-10
> **gazer22 said:**
> FatMonk is right - kernel upgrades will overwrite some files (and move things to other directories), requiring you to re-do the changes.

At a minimum, you have to re-do Step 5: "Backup the default drivers and add these new ones" from the original post.

If that doesn't work, I'd just re-do the whole thing, as FatMonk recommends.

ElGeraldo - can you let me know if just repeating step 5 works for you?  If so, I'll add it to the original post.
Running from Step 5 doesn't work. When I ran the modprobe lines, it whinged that the modules were incompatible. I then assumed that I needed to rebuild the LIRC source to make it compatible with the newer kernel, so started again from step 1 (of the LIRC instructions; I assumed the LCDd stuff was still OK on my HTPC). I deleted the LIRC source code and retrieved it again from CVS, just to be on the safe side. I powered off the HTPC completely (including the ATX PSU switch on the back), just to make sure the LCD module got reset. Now the LCD works on every reboot.

Q: Is there any way to get more interesting stuff to appear on the LCD? MythTV only seems to display the name of the channel and a horizontal bar that grows from left to right - goodness knows what that's supposed to mean. Is it possible to get it to show CPU load and temperature? That would really be useful.

> Unfortunately, my HTPC is mostly off these days, as I've switched to digital cable...
Funny, I'm going the other way. I already have digital cable with about a dozen HD channels and I'm getting rid of it. I'm sick of paying $70 a month for channels that are full of commercials. I thought the whole point of having to endure commercials was that it makes the content free? I never watch half the stuff I record on the cable company's DVR box, so I figured I might as well revert to broadcast TV and spend the money on the HTPC.

Thanks again for your useful HowTo. :KS

---

### Post by gazer22 on 2008-12-10
> **ElGeraldo said:**
> ... Now the LCD works on every reboot.
Cool.  Wish that we didn't have to do the whole process every time too.  Guess the real answer to that is to get these things incorporated into the lirc release.  I haven't looked into that at all.  Leaving that up to the venky/codeka guys.


> **ElGeraldo said:**
> 
Q: Is there any way to get more interesting stuff to appear on the LCD? MythTV only seems to display the name of the channel and a horizontal bar that grows from left to right - goodness knows what that's supposed to mean. Is it possible to get it to show CPU load and temperature? That would really be useful.


Yes, but not that easily.

LCDproc will give system stats, but AFAIK doesn't do anything with Myth. 

Check out this: [Ron Frazier - Developing iMon client for MythTV]("http://mythtvblog.blogspot.com/2008/04/developng-imon-client-for-mythtv.html") and his posts on Codeka's forums: [MythTV iMON Server - custom app for driving the LCD]("http://codeka.com/forums/viewtopic.php?f=3&t=46")

The horizontal bar should reflect how much of the program you've watched.  (AKA, the "progress bar")

> **ElGeraldo said:**
> 
...I never watch half the stuff I record on the cable company's DVR box, so I figured I might as well revert to broadcast TV and spend the money on the HTPC.

Yeah, the cable-company DVR drives me bonkers. Hard to use it once one is used to MythTV!

---

### Post by boffyflow on 2008-12-30
Thanks for the update information for 8,10. I have the LCD and the remote working, but *not* the volume knob which is kind of strange. I have an Antec Fusion Black 430 with a PVR 150 and standard remote (not the MCE).

Everything was working fine with 8.04 (following this HOWTO) and the upgrade (going through all of the steps again) went flawless except for the volume knob. 

Here are my lirc devices (0 = volume know, 1 = remote)
> crw-rw---- 1 root root 61, 0 2008-12-30 02:32 /dev/lirc0
crw-rw---- 1 root root 61, 1 2008-12-30 02:32 /dev/lirc1
srw-rw-rw- 1 root root     0 2008-12-30 03:12 /dev/lircd
srw-rw-rw- 1 root root     0 2008-12-30 03:12 /dev/lircd1
prw-r--r-- 1 root root     0 2008-12-30 02:32 /dev/lircm

Does anybody know what the /dev/lircm device is?

Using mode2 on the lirc0 and lirc1 I get:

> robert@mythbox:/etc/lirc$ sudo mode2 -d /dev/lirc1
code: 0x1790
code: 0x1f91
code: 0x1791
code: 0x1791
code: 0x1f81
code: 0x1782
code: 0x1782
code: 0x1f83
^C
robert@mythbox:/etc/lirc$ sudo mode2 -d /dev/lirc0
code: 0x0001000000009fee
code: 0x0001000000009fee
code: 0x0001000000009fee
code: 0x0001000000009fee
code: 0x0100000000009fee
code: 0x0100000000009fee
code: 0x0100000000009fee
code: 0x0100000000009fee
code: 0x0100000000009fee
^C

But as soon as I start the lirc daemon irw only sees the remote (lirc1) not the volume knob (lirc0). I have tried replacing the code from 0x01000000 to 0x0100000000009fee for VolDn to no avail. I have been staring at hardware.conf and lircd.conf and searching old posts but I cannot find anything wrong. The only things I see different are the somewhat odd codes I get from mode2 and the fifth device which I cannot recall when using 8.04.

Any pointers or help very much appreciated...

Thanks.
Robert

---

### Post by gazer22 on 2009-01-01
Well, according to the lirc documentation, lircm provides mouse functionality from your remote to the system.  Shouldn't be required for the remotes we're talking about here.

I just poked around in the newest lirc cvs release.  It appears that v0.8.5-CVS has added "support for Antec-branded iMon LCD and VFD devices."  This may mean that my section on getting and compiling lirc needs some updating.

My system is down for a while (dang digital cable), and I won't be testing this out, but here's what I would try (be careful - not tested at all!!!):
```
cd /usr/local/src
cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login
cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc
cd lirc
./autogen.sh
./configure --prefix=/usr --with-driver=imon_lcd
make

```

You may be able to run sudo make install and have it work, but I'm not sure.  If not, you'd have to copy the .ko files to the appropriate places.

Following the lirc documentation, you may no longer need the lirc_i2c device.  This would mean that you'd add lirc_dev and lirc_imon to /etc/modules.

Check out the lirc website for deeper info:  [http://www.lirc.org]("http://www.lirc.org")

Good luck, and happy new year!

---

### Post by Spr0k3t on 2009-01-03
> **gazer22 said:**
> Now, let's get the [COLOR=Navy]LCD[/COLOR] working:
[LIST=1]
[*] First, download lcdproc and codeka's patch, compile it and install it:
```
cd /usr/local/src
wget http://internap.dl.sourceforge.net/sourceforge/lcdproc/lcdproc-0.5.2.tar.gz
tar -zxvf lcdproc-0.5.2.tar.gz
cd /usr/local/src/lcdproc-0.5.2
wget http://codeka.com/blogs/imon/lcdproc-0.5.2-imonlcd-0.3.patch
patch -p1 < lcdproc-0.5.2-imonlcd-0.3.patch
aclocal && autoconf && automake


This is where I'm stuck at.  When I do an automake, this is the output.

[code]server/drivers/Makefile.am:80: compiling `IOWarrior.c' with per-target flags requires `AM_PROG_CC_C_O' in `configure.in'
```

My only concern is to get the LCD portion working.

---

### Post by Spr0k3t on 2009-01-03
Okay, I was able to get it working by using lirc from the repos.  The display is working great with the mythbox and the knob is also correctly working as well.  I just have to finish the inclusion of the remote in the lirc.conf file.  Though, I'm not in a huge hurry to get that working since I have a nice bluetooth keyboard with built in mouse.

---

### Post by mlord on 2009-01-15
If anyone is interested in a simplier alternative to lcdproc/imond etc.. for the VFD (not LCD, yet) of the original Antec Fusion case, then there's my own tiny project here:

[http://rtr.ca/vfd_updater/](http://rtr.ca/vfd_updater/)

A buddy of mine has just acquired the cursed LCD version of the case, and I may see if it's feasible to get my vfd_updater going on it as well.

Cheers

---

### Post by nicoloks on 2009-02-05
> **mlord said:**
> If anyone is interested in a simplier alternative to lcdproc/imond etc.. for the VFD (not LCD, yet) of the original Antec Fusion case, then there's my own tiny project here:

[http://rtr.ca/vfd_updater/](http://rtr.ca/vfd_updater/)

A buddy of mine has just acquired the cursed LCD version of the case, and I may see if it's feasible to get my vfd_updater going on it as well.

Cheers

I'd love to see your app expanded to include the LCD version of this great Antec case, and also if possible newer versions. There seems to be a lot of instructions out there to get this case working properly (volume knob and all), however with changes to the hardware versions and the rapid development of patches and required software it is an absolute minefield for the novice Linux user. A one stop shop such as your app would be of great benefit!

---

### Post by gazer22 on 2009-02-05
> **nicoloks said:**
> ...There seems to be a lot of instructions out there to get this case working properly (volume knob and all)...

It's getting closer to being fully incorporated into Ubuntu.  I think the LCD is or is close to being fully supported without any fiddling.  That leaves the coordination of multiple remotes (counting the volume knob as one), which will probably remain a bit of a hassle for a while, though you should only have to do that configuration once.

---

### Post by fatmonk on 2009-02-09
Another kernel update and back to needing to set my LCD up again - BUT then I spot that these fixes have been incorporated in lirc 0.8.4a.

However, even though I am running the standard updates through synaptic, my lirc is still at 0.8.3.

How can I force my system to update to 0.8.4a?

Is there an easy failsafe way to do this or do I need to remove lirc and reinstall from somewhere?

Cheers,

FM

---

### Post by gazer22 on 2009-02-09
> **fatmonk said:**
> ... then I spot that these fixes have been incorporated in lirc 0.8.4a.

However, even though I am running the standard updates through synaptic, my lirc is still at 0.8.3.
...


Found 'em!  They're in intrepid-backports.

Info on what the heck backports are and how to access them can be found here:
[https://help.ubuntu.com/community/UbuntuBackports]("https://help.ubuntu.com/community/UbuntuBackports")


Cool.

---

### Post by fatmonk on 2009-02-10
Cheers Gazer11,

Will take a look at the backports stuff.

Is there anything else I'd need to do after upgrading to 0.8.4a to get the LCD working?

Last night I actually managed to get a version of 0.8.4a onto my machine (from a link on the ComandIR site - I don't have CommandIR, but tried it anyway).

After a reboot I still didn't have the LCD working so I guess theer may still be some config work required (or the CommandIR version is different in the way it treats the LCD somehow).

I reverted back to 0.8.3 via the force version option in Synaptic, so I am ready to give a legit upgrade a go. Would be useful to have some idea of what I'll need to do after upgrading lirc though.

Cheers,

FM

---

### Post by gazer22 on 2009-02-10
> **fatmonk said:**
> ...Is there anything else I'd need to do after upgrading to 0.8.4a to get the LCD working?


Oh sure, ask the tough questions.

Also, let it be known that I'm completely shooting from the hip, as I'm still running 8.04, and not even using the box as an htpc these days.  (Digital cable incompatibility being the main reason - please let native MythTV/Mythbuntu support for the HD-PVR come soon!!).  

That being said, I think you still need lcdproc in order to get /etc/init.d/LCDd.  There have been no updates to lcdproc, as it's still v0.5.2, so it still needs patching as in my original post  (The three steps under "Now, let's get the LCD working:").

End result will be the existence of /etc/init.d/LCDd and /usr/local/etc/LCDd.conf, the latter being the one which should hold the configuration for our LCD.

The lirc updates should eliminate the need to do the rest of the stuff, including re-doing stuff with every new kernel. 

If you want "two" remotes working (and the volume knob counts as one), you may have to do the modifications to hardware.conf and /etc/init.d/lirc as described in the OP, but again, you shouldn't have to do this more than once (unless apt overwrites it...)

Let me know if that works!  :KS

---

### Post by fatmonk on 2009-02-11
Well.... it wouldn't be any fun if all the questions were easy, would it?

Hopefully I'll get a chance to give this lot a go in the next couple of days. I'll report back when I have.

Cheers for your help so far.

-FM

---

### Post by fatmonk on 2009-02-12
OK, am well and truly stuck here now...

After the kernel upgrade the instructions in the OP didn't work - I can't remember where it failed, but I'm 90% sure that it was the same place as I am about to describe.

Then I noticed that lirc 0.8.4a apparently supports the iMon stuff.

I've now upgraded to 0.8.4a and run a dependency check.

I then tried the instructions again - first of all starting at section 3 about getting the LCD working as advised. When that didn't work I tried again from the start, and the same error again.

The error I am getting is as follows:

```
/usr/local/src/lcdproc-0.5.2# aclocal && autoconf && automake
server/drivers/Makefile.am:80: compiling `IOWarrior.c' with per-target flags requires `AM_PROG_CC_C_O' in `configure.in'

```

I have no idea what AM_PROG_CC_C_0 is, but it doesn't appear in the configure.in file. Everything else in configure.in appears to have parameters with it, so just adding this line obviously isn't going to work.

As it is now, I have no working LCD and no working remote. I am an unhappy monk :-(

Any help?

Cheers,

FM



[some more info after some more playing]

After a bit of googling I found posts elsewhere on these forums ([http://ubuntuforums.org/showthread.php?t=907256&page=2]("http://ubuntuforums.org/showthread.php?t=907256&page=2")) that that error is not a problem (really?), so tried the next command... the last message from the ./configure command is:

```
configure: checking for which drivers to compile...
configure: error: Unknown driver imonlcd
```

now, that does seem quite important.

Bear in mind aswell that this box should already have the correctly patched LCDd on it as it was working perfectly (in terms of the LCD) before the last kernel update.

If I try to run LCDd from the command line with -f -r 4 flags I just get the copyright/info message - no errors or info about which .conf file its using.

ps-ef | grep -is lcd just turns up the mythtv lcd process, not LCDd - so it looks quite fundamental.

-FM

---

### Post by gazer22 on 2009-02-12
> **fatmonk said:**
> OK, am well and truly stuck here now... 
... I am an unhappy monk :-(

Well, thank the lord you're not getting any thinner!  ;)

> **fatmonk said:**
> 
...
The error I am getting is as follows:

```
/usr/local/src/lcdproc-0.5.2# automake
server/drivers/Makefile.am:80: compiling `IOWarrior.c' with per-target flags requires `AM_PROG_CC_C_O' in `configure.in'

```

Okay, I'm getting the same thing here (in 8.04).  Weird.  After a _quick_ look into the code - it looks like IOWarrior is just another module, that we're not compiling, so it should be okay to ignore the warning.

> **fatmonk said:**
> 
After a bit of googling I found posts elsewhere on these forums ([http://ubuntuforums.org/showthread.php?t=907256&page=2]("http://ubuntuforums.org/showthread.php?t=907256&page=2")) that that error is not a problem (really?), so tried the next command... the last message from the ./configure command is:

```
configure: checking for which drivers to compile...
configure: error: Unknown driver imonlcd
```

now, that does seem quite important.


That would seem quite important, and I don't get it in my 8.04 trial.  I am able to get through the configure step and make successfully.

It sounds as if the patch didn't apply correctly.

I'd suggest removing the /usr/local/src/lcdproc-0.5.2 directory and starting over with the step "First, download lcdproc and codeka's patch, compile it and install it:"

After running the patch command (patch -p1 < lcdproc-0.5.2-imonlcd-0.3.patch) but before running aclocal and the rest, please try this:
```

find . -type f -print0 | xargs -0 grep -il imonlcd

```
This should give:
```

./server/drivers/imonlcd.c
./server/drivers/Makefile.am
./server/drivers/imonlcd.h
./lcdproc-0.5.2-imonlcd-0.3.patch
./acinclude.m4

```

If not, something is goofy with the patch, and we need to figure it out...

---

### Post by fatmonk on 2009-02-13
After removing the lcdproc directory under /usr/local/src and starting again the patch worked properly and the configure worked properly.

However, when I ran the make I received loads of warnings that there were values that were too big for the long variable type.

Anyway, I bashed on, and everything seemed to go ok.

After I'd completed step 3 in the 'get the LCD working' bit I tried runnig LCDd via /etc/init.d/LCDd start.... nothing, the only thing of note is that there is no OK or FAIL message, it seems to bail out early and my command prompt runs straight on from the starting message as follows:

```
root@unicorn:/home/mythbox# /etc/init.d/LCDd start
Starting LCDproc display server daemon: root@unicorn:/home/mythbox# 
```

So I thought that maybe there was something wrong with the init.d script.

But, again when I try to run it directly as follows, again it doesn't start but neither do I get any errors:

```
root@unicorn:/home/mythbox# /usr/local/sbin/LCDd -f -r 4
LCDd 0.5.2, LCDproc Protocol 0.3
Part of the LCDproc suite
Copyright (C) 1998-2007 William Ferrell, Scott Scriven
                        and many other contributors

This program is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License
as published by the Free Software Foundation; either version 2
of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software Foundation,
Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.

root@unicorn:/home/mythbox# ps -ef | grep -is lcd
mythbox   8595     1  0 15:27 ?        00:00:00 /usr/bin/mythlcdserver -v none
root      9459  9086  0 16:20 pts/0    00:00:00 grep -is lcd
root@unicorn:/home/mythbox# 
```

So, still no LCD, and still no clue as to why :-(

-FM

---

### Post by gazer22 on 2009-02-13
> **fatmonk said:**
> ...
So, still no LCD, and still no clue as to why :-(

Time for a new thread!!!

8.10 info started on a new thread:
[http://ubuntuforums.org/showthread.php?t=1069267]("http://ubuntuforums.org/showthread.php?t=1069267")

Follow me over there.  Hopefully those instructions should fix your system!

---

### Post by h2o_chris on 2009-02-22
Thank you very much for your hard work.
I'm in the process of resetting my mythbox and I'm following your instructions (again). I've noticed in step 5 (backing up) there are many references to .ko files. My files end in .c
Can I simply changed the instuctions in that section to reflect the difference in file extensions?

chis@Fusion:/usr/local/src/lirc/drivers/lirc_i2c$ ls -la
total 84
drwxr-xr-x  4 chis chis  4096 2009-02-22 13:39 .
drwxr-xr-x 29 chis chis  4096 2009-02-22 13:39 ..
drwxr-xr-x  2 chis chis  4096 2009-02-22 13:37 CVS
-rw-r--r--  1 chis chis   170 2009-01-05 14:28 .cvsignore
drwxr-xr-x  2 chis chis  4096 2009-02-22 13:39 .deps
[COLOR="Red"]-rw-r--r--  1 chis chis 16883 2009-02-14 14:35 lirc_i2c.c[/COLOR]
-rw-r--r--  1 chis chis 16860 2009-02-22 13:39 Makefile
-rw-r--r--  1 chis chis   436 2004-04-25 12:29 Makefile.am
-rw-r--r--  1 chis chis 16799 2009-02-22 13:38 Makefile.in
chis@Fusion:/usr/local/src/lirc/drivers/lirc_i2c$

---

### Post by gazer22 on 2009-02-22
> **h2o_chris said:**
> ...I've noticed in step 5 (backing up) there are many references to .ko files. My files end in .c...


No!!

The lack of .ko files indicates that your compilation didn't work.  Make sure the permissions are good on the directory.  

You probably had errors from autogen, configure, or make.

---

