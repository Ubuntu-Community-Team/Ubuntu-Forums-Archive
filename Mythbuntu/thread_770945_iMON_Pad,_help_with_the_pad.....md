---
title: "iMON Pad, help with the pad...."
date: 2008-04-27
forum: Mythbuntu
---

### Post by slyhne on 2008-04-27
Hi

I have just upgraded my MythTV computer with mythbuntu 8.04, and this left me with a non working SoundGraph Imon Pad remote.

Well it works sort of, but the pad doesn't send up/down/left/right as I had it doing in 7.04.
I have tried compiling lirc with the pad-patch, but compiling lirc on 8.04 must have changed because it fails.

Can anybody give me a quick walk-through on how to do this?

I also wonder why this still haven't been fixed in 8.04. In my old setup I could use the Mouse/Keyboard button to switch behavior of the pad (as it should do).

Thanks

Søren

---

### Post by slyhne on 2008-04-29
Apparently lirc now comes as a DKMS package, and according to Mythbuntu's release announcement this should be fairly easy to patch:

> DKMS support. If you have modules that get upgraded after 8.04 comes out, you can patch them via lirc-modules-source manually, or grab a lirc-modules-source from a future Ubuntu/Mythbuntu testing release and simply install it without any manual patching necessary.

Unfortunately I haven't found any howto that explains the necessary steps for patching.

Help....!:confused:

Forgot to mention that this is a new installation, not an upgrade - I did reformat the harddisk...

Søren

---

### Post by slyhne on 2008-04-30
Bump :(

---

### Post by zugol on 2008-05-03
This makes my pad work like arrows. (but have trouble with Mouse_E) 

In /usr/share/lirc/remote/lircd.conf.imon-pad

          Mouse_N                  0x6902F9B7
          Mouse_S                  0x6882C1B7
          Mouse_W                  0x6AFA81B7
          Mouse_E                  0x68A281B7

---

### Post by slyhne on 2008-05-06
Hi

This bug report solves the problem:

[https://bugs.launchpad.net/ubuntu/+s...rc/+bug/153184](https://bugs.launchpad.net/ubuntu/+s...rc/+bug/153184)

I have tried the patch and it's working.

Hi

This is what you have to do in order to get the pad working in Hardy:

Install lirc sources and dkms

```
sudo apt-get install dkms lirc-modules-source
```

Copy the patch file (lirc-0.8.3~pre1-0ubuntu7-pad2keys.patch) to /usr/src

```
cp (path)/lirc-0.8.3~pre1-0ubuntu7-pad2keys.patch /usr/src/.
```

Patch the source

```
cd /usr/src/lirc-0.8.3~pre1
sudo patch -p1 < ../lirc-0.8.3~pre1-0ubuntu7-pad2keys.patch
```

Build and install lirc using dkms

```
sudo dkms remove -m lirc -v 0.8.3~pre1 --all
sudo dkms add -m lirc -v 0.8.3~pre1
sudo dkms build -m lirc -v 0.8.3~pre1
sudo dkms install -m lirc -v 0.8.3~pre1
```

Activate patch

```
sudo pico /etc/modprobe.d/options
```

Add the following line to the end of this file

> options lirc_imon pad2keys_active=1

Then a reboot, and you ready to navigate MythTV usin the pad.

Have fun

slyhne

---

### Post by rajwani on 2008-05-09
I can confirm that slyhne's instructions work, and left me with a working pad, yeaaaay!

However after rebooting, my IMON VFD stopped working and I also started to see log messages like:

/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_imon/lirc_imon.c: lcd_write: invalid payload size: 32 (expecting 8)

To fix this, I changed the last line in file /etc/modprobe.d/options

from:
options lirc_imon pad2keys_active=1

to:
options lirc_imon pad2keys_active=1 islcd=0

All is good now, working imon pad and vfd and no error messages.

Arif Rajwani

---

### Post by kryptonite2k on 2008-08-08
I have the IMON pad remote and all the buttons work, I verified using irw, except for the arrow key pad. I have tried using the procedure with the pad2keys patch. I didn't get any errors but the arrow key pad still doesn't work.
What else can I do get the pad to work?

---

### Post by kryptonite2k on 2008-08-08
All the keys, except for the pad of course, are recognized by irw. But when I am using mythtv, the only key that is recognized is the enter key. I am not sure what the patch did but the only difference I can find are these entries added to lircd.conf.imon-pad

# Corrin added
          Space                    0x2B9B15F7
          Up                       0xEB53F9B7
          Left                     0x6ABAFFBF
          Down                     0x6F9ECBB7
          Right                    0x69A281B7

Do these appear correct?

Also the hardware.conf lists

#Chosen Remote Control
REMOTE="Soundgraph iMON PAD IR/VFD"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="imon/lircd.conf.imon-pad"
REMOTE_LIRCD_ARGS=""

Should there be a driver listed in the REMOTE_DRIVER entry?

---

### Post by kryptonite2k on 2008-08-08
Does any one know if the 0.8.3 final version of lirc has support for the pad?

---

### Post by kryptonite2k on 2008-08-10
I have the Imon pad with the Imon inside reciever. The remote control daemon failed to start. There was nothing listed as the REMOTE_DRIVER in the hardware.conf. So I guessed a driver name. When I tried to start the lirc daemon using 

```

sudo /etc/init.d/lirc start

```

I got this message.

```

 
 * Loading LIRC modules                                              [OK] 
 
* Starting remote control daemon(s) :                                  LIRC Driver `lirc_imon-pad' not supported.
Supported drivers:
	accent
	alsa_usb
	asusdh
	atilibusb
	audio_alsa
	bte
	bw6130
	creative
	creative_infracd
	default
	devinput
	dsp
	dvico
	ea65
	i2cuser
	irman
	livedrive_midi
	livedrive_seq
	logitech
	macmini
	mp3anywhere
	mouseremote
	mouseremote_ps2
	null
	pcmak
	pinsys
	pixelview
	sb0540
	silitek
	tira
	udp
	uirt2
	uirt2_raw
	usb_uirt_raw
	usbx
                                                                    [fail]

```

I don't see any driver with imon or soundgraph in the name. Which driver should I choose?

---

### Post by kryptonite2k on 2008-08-10
Could someone who has a working imon pad remote post the contents of there 
/etc/lirc/hardware.conf file? I would like to see if I even have the correct driver on my system.

---

### Post by Aisknab on 2008-08-10
I am also having issues with my IMON Pad, I have just posted in this thread here
[http://ubuntuforums.org/showthread.php?t=865356&highlight=imon](http://ubuntuforums.org/showthread.php?t=865356&highlight=imon)

Are you have the same issues?

---

### Post by kryptonite2k on 2008-08-16
I'm having different problems with lirc and my remote. I don't get any response at all from the remote. I have tried the instructions on all of these threads

[http://xbmc.org/forum/showthread.php?p=190949]("http://xbmc.org/forum/showthread.php?p=190949")

[http://www.gexperts.com/blog/archives/2008/06/entry_347.html]("http://www.gexperts.com/blog/archives/2008/06/entry_347.html")

[http://ubuntuforums.org/showthread.php?t=849568]("http://ubuntuforums.org/showthread.php?t=849568")

[http://ubuntuforums.org/showthread.php?t=814294]("http://ubuntuforums.org/showthread.php?t=814294")

[http://ubuntuforums.org/showthread.php?t=818660]("http://ubuntuforums.org/showthread.php?t=818660")

and the instructions towards the beginning of this thread

And nothing seems to work. I think I have installed lirc 0.8.3 and when I
run:

```

/etc/lirc$ sudo /etc/init.d/lirc start

```

I get this 

```

 * Loading LIRC modules                                         [ OK ] 
 * Starting remote control daemon(s) : LIRC                            Driver `devinput' not supported.
Supported drivers:
	default
                                                                [fail]

```

When I change the driver in hardware.conf to default and try to start the
lirc daemon, I get this

```

 * Loading LIRC modules                                         [ OK ] 
 * Starting remote control daemon(s) : LIRC                            lircd: WARNING: config file contains no valid remote control definition
                                                                [ OK ]

```

I don't know where to go from here. Does anyone know how to get this Imon pad to work?

---

### Post by kryptonite2k on 2008-08-20
Is there, or can someone provide, steps to properly remove the currently installed lirc driver and properly install the latest lirc driver(I believe the latest version is 0.8.3) with setup geared toward the Imon pad remote?

---

### Post by drlabel on 2008-08-22
i need help to i have a nox media with Imon Pad nad i can't get lirc to work pls make a step by step guide because i can't get the remote to work.

---

### Post by Markus72 on 2008-08-22
Hi,

I got a silverstone LC18 case with imon pad and vfd.

After a fresh installation of Mythbuntu 8.04 I used the Mythbuntu control centre and selected 'Infrared devices'.

I activated the remote 'Soundgraph iMON PAD IR/VFD'.

After applying, the control centre automatically downloaded all packages and installed them.

I rebooted (or maybe I didn't - can't remember) and both the remote and the vfd worked.

I created a dynamic button mapping (control centre) and added some mappings to the .lirc/mythtv config file after making a backup (how to do this, you'll know after you read this posting).

That was it.

You can check if your buttons are detected just by calling 'irw' from within a shell and poking around on your remote.

As far as I remember, all buttons were producing some output in irw (only the .lirc/mythtv mapping was very rudimentary - if you like to enhance it, just make a backup, edit the original and add some mappings).

But there was one exception: the pad.

For the pad I applied the patch described earlier in this thread (see the good description from slyhne on page 1).

But I was not completely satisfied with the patch, though: it seemed that it only produced the mouse-events if you exactly hit the perfect direction.
Will say: there seemed to be no tolerance which makes it pretty unuseful to me (I was able to produce a Mouse_E event only once !!).

(am I the only one experiencing this?)

Nearly two years ago I walked through this imon hell the first time and that time I used the perfectly working patch from here:

[http://brakemeier.de/electronics/vdr/lirc-imon.html]("http://brakemeier.de/electronics/vdr/lirc-imon.html")

So after not being satisfied with the patch I found in this thread, I cleaned all sources with 

```
sudo apt-get remove lirc-modules-source
```

After that I followed slyhne's description how to patch but used the brakemeier-patch instead of the posted one.

Since there had been no change in the patch from the pre1-version to the 0.8.3 final version, I tried the final patch.

It looks like it all worked :-)

Give it a try.

Markus

PS: dont forget these!

1. If you have a VFD display, you habe to change the modprobe options (brakemeier patch)
```
sudo nano /etc/modprobe.d/options
```
and added the following line:
```
options lirc_imon islcd=0
```

If you installed the other patch before, remove the pad2keys option!

2. you have to edit lircd-conf
```
sudo nano /usr/share/lirc/remotes/imon/lircd.conf.imon-pad
```
scroll down to the line looking like
```
begin codes
```
and add the following lines below it
```

Mouse_N 0x6902F9B7
Mouse_S 0x6882C1B7
Mouse_W 0x6AFA81B7
Mouse_E 0x68A281B7

```

3. if you want to restart the lirc demon to test your changes, you need to reboot (in case of the changes to the modprobe options) or to restart the lirc demon using
```
sudo /etc/init.d/lirc restart
```

4. in case you like some mythtv mappings for the pad, edit the mythtv lirc mapping file:
```
nano ./.lirc/mythtv
```
and add the following mappings:
```

begin
	remote = iMON-PAD
        prog = mythtv
        button = Mouse_N
        repeat = 5
        delay = 5
        config = Up
end

begin
	remote = iMON-PAD
        prog = mythtv
        button = Mouse_S
        repeat = 5
        delay = 5
        config = Down
end
begin
	remote = iMON-PAD
        prog = mythtv
        button = Mouse_W
        repeat = 5
        delay = 5
        config = Left
end
begin
	remote = iMON-PAD
        prog = mythtv
        button = Mouse_E
        repeat = 5
        delay = 5
        config = Right
end

```

---

### Post by Markus72 on 2008-08-22
Hmmm... 

I just took a look into the patch provided by slyhne and it also seems to be something Mr. Brakemeier has been involved in...

But the source is less bytes...

@slyhne: what's the difference?

It's strange - even though it works, the Mouse_E event is still somehow stubborn...

Is it my remote or do you experience a similar behavior?

Markus

---

