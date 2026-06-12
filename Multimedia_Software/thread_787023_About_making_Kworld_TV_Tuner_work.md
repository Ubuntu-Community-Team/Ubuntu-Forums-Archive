---
title: "About making Kworld TV Tuner work"
date: 2008-05-08
forum: Multimedia Software
---

### Post by sofasurfer on 2008-05-08
I have a Kworld TV card with a saa7131 ver.c chip. In trying to get it working I came across this web site...
[http://linuxtv.org/v4lwiki/index.php/KWorld_Studio_TV_Terminator](http://linuxtv.org/v4lwiki/index.php/KWorld_Studio_TV_Terminator)

Right off the bat I find that the important file that I need to change...
/etc/modprobe.conf  OR  /etc/modprobe.d/saa7134  ...does not exist on my system.

Can you tell me how to handle this situation? Or if you have better information that can get me started in setting this thing up, I'm all ears and will appreciate any help.

---

### Post by sofasurfer on 2008-05-09
I got my tv tuner card working.
I found a thread which had similar information as the site mentioned at the start of this thread, but the thread that I used was clearer to me.
Basically, to get a card with a saa7131 chip working here is what you do:

$ locate saa7131
$ cd /<to the directory with the ssa7131 file>
$ rmmod saa7134_alsa
$ rmmod saa7134
$ modprobe saa3134 card=81

The problem is that everytime you restart the computer you have to follow this proceedure to get the TV Tuner card working again.

So, I am in need of a way to get the above commands to stay in effect after the computer is restarted.

If no one has a solution, please, at least point me to a place where I can get an answer.

Thanks.

---

### Post by Mze on 2008-05-09
Check this [thread]("http://ubuntuforums.org/showthread.php?t=725431") out

---

### Post by sofasurfer on 2008-05-10
I tried again to use the method that I described above and it did not work this time. I get errors. And when I ran "$ locate saa7134" I now have saa7134 files all over the place. So I tried your method at the link you posted above, I get a "no signal" message from TVTime.

O,o! I think I screwed everything up. Can you guide me some more? I promise to listen.

Thanks.

---

### Post by sofasurfer on 2008-05-10
So I quess the place I want to start is in getting my system back to the way it was before, so I can make another attempt either with the method that worked for me only the 1 time, or the method you suggested.

How would I get things back to the way they were?

---

### Post by Mze on 2008-05-11
1. Remove the saa7134 file you created from the thread I posted.

sudo rm /etc/modprobe.d/saa7134

2. If you added saa7134 to /etc/modules you will need to delete that too.

sudo nano /etc/modules

and delete saa7134
----------------------------------------
If these are the only changes you made to your system then, you should be back to where you were before these changes were made.

Restart your system

---

### Post by sofasurfer on 2008-05-11
When I first started messing around, using the method I mentioned at the top of this thread, the result of "locate saa7134" would turn up these results...
/lib/modules/2.6.24-16-generic/kernel/drivers/media/video/saa7134/saa7134.ko
/lib/modules/2.6.24-16-generic/ubuntu/media/saa7134

Now after my failed attempts "locate saa7134" turns up this...
/home/daryl/.kde/share/apps/RecentDocuments/saa7134.ko.desktop
/home/daryl/.kde/share/apps/RecentDocuments/saa7134.ko[2].desktop
/home/daryl/.kde/share/apps/RecentDocuments/saa7134.ko[3].desktop
/lib/modules/2.6.24-16-generic/kernel/drivers/media/video/saa7134
/lib/modules/2.6.24-16-generic/kernel/drivers/media/video/saa7134/saa6752hs.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/media/video/saa7134/saa7134-dvb.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/media/video/saa7134/saa7134-empress.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/media/video/saa7134/saa7134.ko
/lib/modules/2.6.24-16-generic/ubuntu/media/saa7134
/lib/modules/2.6.24-16-generic/ubuntu/media/saa7134/saa6752hs.ko
/lib/modules/2.6.24-16-generic/ubuntu/media/saa7134/saa7134-alsa.ko
/lib/modules/2.6.24-16-generic/ubuntu/media/saa7134/saa7134-dvb.ko
/lib/modules/2.6.24-16-generic/ubuntu/media/saa7134/saa7134-empress.ko
/lib/modules/2.6.24-16-generic/ubuntu/media/saa7134/saa7134-oss.ko
/lib/modules/2.6.24-16-generic/ubuntu/media/saa7134/saa7134.ko
/usr/src/linux-headers-2.6.24-16/drivers/media/video/saa7134
/usr/src/linux-headers-2.6.24-16/drivers/media/video/saa7134/Kconfig
/usr/src/linux-headers-2.6.24-16/drivers/media/video/saa7134/Makefile
/usr/src/linux-headers-2.6.24-16-generic/include/config/video/saa7134
/usr/src/linux-headers-2.6.24-16-generic/include/config/video/saa7134.h
/usr/src/linux-headers-2.6.24-16-generic/include/config/video/saa7134/dvb.h

I think as a matter of good housekeeping I should get rid of all of this. But how? Do I simply delete each file or do I reverse a specific process to eliminate them?

As you suggested, I ran "sudo rm /etc/modprobe.d/saa7134" and also "sudo nano /etc/modules" but I don't think they did anything.

I want to remind you that I have 7131 chip, not 7134. Although I think from what I have read, that the series 713* is whats important.

I just tried (again) the method that is used in the thread that you pointed me to and again I get a "no signal" message.

---

### Post by Mze on 2008-05-11
The instructions are geared toward the 713x chipset series. Mine is identified as 7130 in lspci but I created a saa7134 and modified my tuner number as per a Google/Ubuntu forums search and things are fine on my end.

When you add the saa7134 to modprobe.d, what you are trying to do is force the kernel to recognise your card with parameters set in the file.

For e.g. in /etc/modprobe.d/saa7134 
my saa 7134 file contains these instructions:
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=40 tuner=37

Below is the result of my "locate saa7134"

/etc/modprobe.d/saa7134
/lib/modules/2.6.24-17-generic/kernel/drivers/media/video/saa7134
/lib/modules/2.6.24-17-generic/kernel/drivers/media/video/saa7134/saa6752hs.ko
/lib/modules/2.6.24-17-generic/kernel/drivers/media/video/saa7134/saa7134-dvb.ko
/lib/modules/2.6.24-17-generic/kernel/drivers/media/video/saa7134/saa7134-empress.ko
/lib/modules/2.6.24-17-generic/kernel/drivers/media/video/saa7134/saa7134.ko
/lib/modules/2.6.24-17-generic/ubuntu/media/saa7134
/lib/modules/2.6.24-17-generic/ubuntu/media/saa7134/saa7134-alsa.ko
/usr/src/linux-headers-2.6.24-17/drivers/media/video/saa7134
/usr/src/linux-headers-2.6.24-17/drivers/media/video/saa7134/Kconfig
/usr/src/linux-headers-2.6.24-17/drivers/media/video/saa7134/Makefile
/usr/src/linux-headers-2.6.24-17-generic/include/config/video/saa7134
/usr/src/linux-headers-2.6.24-17-generic/include/config/video/saa7134.h
/usr/src/linux-headers-2.6.24-17-generic/include/config/video/saa7134/dvb.h
-----------------------
Now with your card your might also want to take a look at this [page]("http://www.linuxtv.org/v4lwiki/index.php/Saa713x_devices#KWorld")

---------
You might also want to run:

sudo nano /etc/modeprobe.d/options

and if there are any references to saa7134 on any line, only DELETE the line with parameters for SAA7134, exit and save changes.

------
I don't think it's a good idea to delete the files you found using  "locate saa7134", you might bork your system.

---

### Post by Mze on 2008-05-11
Initially you wrote that you'd created a saa7131 file and added it to modprobe and it worked.

So once again, create your saa7131 file:

sudo nano /etc/modules/
add saa7131 to the file

if there's a reference to "saa7134" in the file opened, delete it. Save file.

Back to terminal:

sudo nano /etc/modprobe.d/saa7131

then add this option to your file>>

options saa7131 card=81 

Run:

sudo modprobe saa7131

to load module.

if it doesn't work, reboot your machine a try your TV tuner.

Here's a [link]("http://www.filledvoid.com/2007/12/15/techcom-tv-tuner-configuration-in-ubuntu/") for an explanation of using modprobe.d, rmmod commands while setting up a TV card

---

### Post by sofasurfer on 2008-05-12
I followed your link to: [http://www.linuxtv.org/v4lwiki/index.php/Saa713x_devices#KWorld](http://www.linuxtv.org/v4lwiki/index.php/Saa713x_devices#KWorld) and used the "Studio TV Terminator" link. 
When I got to the part that said
 
"Then, reload the module, as well as the tuner:
rmmod saa7134 tuner
modprobe saa7134 card=65 tuner=54"

I got this result:

daryl@ubuntu:~$ rmmod saa7134 tuner
ERROR: Module saa7134 is in use by saa7134_alsa
ERROR: Removing 'tuner': Operation not permitted
daryl@ubuntu:~$ modprobe saa7134 card=65 tuner=54
WARNING: Failed to open config file /etc/modprobe.d/blacklist.save: Permission denied

I then did the "blacklist" and "permissions" recommendation and still got the above errors.

I think I'm screwed until I get a better tuner card.

---

### Post by Mze on 2008-05-12
1. Did you also try the method of returning your system to it's previous state, prior to making all the changes as I had suggested in my last 2 posts?

2. Could you post the results of this command?

lspci | grep -i saa713

---

### Post by sofasurfer on 2008-05-12
I have been using kate in place of nano. I can't figure nano out and I can't find a manual for it. So kate is ok with me.

Ok, on with my lessons.

You asked for the results of lspci | grep -i saa713. I think you meant lspci | grep -i saa7134 or maybe you want all variations of saa713***, but I will give you both.


daryl@ubuntu:~$ lspci | grep -i saa713
01:06.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

daryl@ubuntu:~$ lspci | grep -i saa7134

lspci | grep -i saa7134 shows nothing.

Let me know what else you want, and thank you for your patience with me.

---

### Post by Mze on 2008-05-12
Post output of:

dmesg | grep saa713

This should at least show your card number and then we'll take it from there.

---

### Post by sofasurfer on 2008-05-13
daryl@ubuntu:~$ dmesg | grep saa713
[   37.711690] saa7130/34: v4l2 driver version 0.2.14 loaded
[   37.712092] saa7133[0]: found at 0000:01:06.0, rev: 209, irq: 16, latency: 32, mmio: 0xfb000000
[   37.712097] saa7133[0]: subsystem: 1131:0000, board: V-Stream Studio TV Terminator [card=65,insmod option]
[   37.712105] saa7133[0]: board init: gpio is 40
[   37.712159] input: saa7134 IR (V-Stream Studio TV  as /devices/pci0000:00/0000:00:04.0/0000:01:06.0/input/input6
[   37.876447] saa7133[0]: Huh, no eeprom present (err=-5)?
[   38.127577] tuner 2-004b: chip found @ 0x96 (saa7133[0])
[   38.461661] saa7133[0]: registered device video0 [v4l2]
[   38.461677] saa7133[0]: registered device vbi0
[   38.461693] saa7133[0]: registered device radio0
[   38.468395] saa7134 ALSA driver for DMA sound loaded
[   38.468426] saa7133[0]/alsa: saa7133[0] at 0xfb000000 irq 16 registered as card -2

---

### Post by Mze on 2008-05-13
Once again, back to square 1. :(

Run:

sudo rmmod saa7134_alsa

sudo rmmod saa7134

sudo modprobe saa7134 card=65 tuner=54

(Using card=65 because your dmesg output shows:
[ 37.712097] saa7133[0]: subsystem: 1131:0000, board: V-Stream Studio TV Terminator [**card=65**,insmod option]

I'm also using the [KWorld Global TV Terminator]("http://www.mythtv.org/wiki/index.php/KWorld_Global_TV_Terminator#HOWTO_with_KnoppMyth") webpage you provided as reference.

Run:
tvtime 

[Do you get video and sound after changing your video source to Television?]

If you get video and sound then, to make your options load each time you boot, you'd have to create create a file named saa7134 in /etc/modprobe.d/

Command: 
sudo nano /etc/modeprobe.d/saa7134

Add this line to file:

options saa7134 card=65 tuner=54

Save changes.

***
I've read also on another website, where /etc/modeprobe.d/options was modified and this line added:
options saa7134 card=65 tuner=54

If your card works with the modification to saa7134 then I don't think you need this addition.

*******
Your card doesn't show any eeprom info from dmesg, so lets go with tuner=54 as per MythTV webpage. If that doesn't work, then try tuner=5 [Philips PAL_BG (FI1216 and compatibles)] by editing saa7134 file. Unload modules using rmmod commands as before and reload with modprobe

**********
According to info on the MythTV website, there might be some issues with sound.
If you have any problems with sound run this command in terminal:

arecord -l

and post output.

---

### Post by sofasurfer on 2008-05-13
Your a genius! Thank you. I now have tv video, but I still don't have sound.
I have sound on [www.youtube](www.youtube) and [www.cbs](www.cbs) and [www.nbc](www.nbc). But sound on TV Tuner still evades me.

---

### Post by shane2peru on 2008-05-13
> **Mze said:**
> Once again, back to square 1. :(

Run:

sudo rmmod saa7134_alsa

sudo rmmod saa7134

sudo modprobe saa7134 card=65 tuner=54

(Using card=65 because your dmesg output shows:
[ 37.712097] saa7133[0]: subsystem: 1131:0000, board: V-Stream Studio TV Terminator [**card=65**,insmod option]

I'm also using the [KWorld Global TV Terminator]("http://www.mythtv.org/wiki/index.php/KWorld_Global_TV_Terminator#HOWTO_with_KnoppMyth") webpage you provided as reference.

Run:
tvtime 

[Do you get video and sound after changing your video source to Television?]

If you get video and sound then, to make your options load each time you boot, you'd have to create create a file named saa7134 in /etc/modprobe.d/

Command: 
sudo nano /etc/modeprobe.d/saa7134

Add this line to file:

options saa7134 card=65 tuner=54

Save changes.

***
I've read also on another website, where /etc/modeprobe.d/options was modified and this line added:
options saa7134 card=65 tuner=54

If your card works with the modification to saa7134 then I don't think you need this addition.

*******
Your card doesn't show any eeprom info from dmesg, so lets go with tuner=54 as per MythTV webpage. If that doesn't work, then try tuner=5 [Philips PAL_BG (FI1216 and compatibles)] by editing saa7134 file. Unload modules using rmmod commands as before and reload with modprobe

**********
According to info on the MythTV website, there might be some issues with sound.
If you have any problems with sound run this command in terminal:

arecord -l

and post output.

Ok Mze, you are the TV Card Guru!  I have followed this thread, and I happen to be using the Kworld 7134 card, so I shouldn't have any problems, however here is my output of the dmesg:
```

[   31.747466] saa7130/34: v4l2 driver version 0.2.14 loaded
[   31.875346] saa7134[0]: found at 0000:04:00.0, rev: 1, irq: 21, latency: 32, mmio: 0x70001000
[   31.875354] saa7134[0]: subsystem: 17de:7128, board: V-Stream Studio TV Terminator [card=65,insmod option]
[   31.875365] saa7134[0]: board init: gpio is c0407f
[   31.875441] input: saa7134 IR (V-Stream Studio TV  as /devices/pci0000:00/0000:00:1e.0/0000:04:00.0/input/input6
[   32.235997] saa7134[0]: i2c eeprom 00: de 17 28 71 10 28 ff ff ff ff ff ff ff ff ff ff
[   32.236008] saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.236017] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.236025] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.236034] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.236042] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.236051] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.236059] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.362185] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[   32.374109] tuner 0-0061: chip found @ 0xc2 (saa7134[0])
[   32.751408] saa7134[0]: registered device video1 [v4l2]
[   32.751434] saa7134[0]: registered device vbi0
[   32.751455] saa7134[0]: registered device radio0
[  841.767468] saa7130/34: v4l2 driver version 0.2.14 loaded
[  841.767537] saa7134[0]: found at 0000:04:00.0, rev: 1, irq: 21, latency: 32, mmio: 0x70001000
[  841.767547] saa7134[0]: subsystem: 17de:7128, board: V-Stream Studio TV Terminator [card=65,insmod option]
[  841.767560] saa7134[0]: board init: gpio is c0407f
[  841.767644] input: saa7134 IR (V-Stream Studio TV  as /devices/pci0000:00/0000:00:1e.0/0000:04:00.0/input/input7
[  841.926514] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[  841.934517] tuner 0-0061: chip found @ 0xc2 (saa7134[0])
[  842.321704] saa7134[0]: i2c eeprom 00: de 17 28 71 10 28 ff ff ff ff ff ff ff ff ff ff
[  842.321722] saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  842.321734] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  842.321747] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  842.321757] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  842.321770] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  842.321782] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  842.321795] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  844.857991] saa7134[0]: registered device video1 [v4l2]
[  844.858035] saa7134[0]: registered device vbi0
[  844.858067] saa7134[0]: registered device radio0
[  989.934506] saa7130/34: v4l2 driver version 0.2.14 loaded
[  989.934568] saa7134[0]: found at 0000:04:00.0, rev: 1, irq: 21, latency: 32, mmio: 0x70001000
[  989.934577] saa7134[0]: subsystem: 17de:7128, board: V-Stream Studio TV Terminator [card=65,insmod option]
[  989.934589] saa7134[0]: board init: gpio is e0407f
[  989.934674] input: saa7134 IR (V-Stream Studio TV  as /devices/pci0000:00/0000:00:1e.0/0000:04:00.0/input/input8
[  990.113030] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[  990.120996] tuner 0-0061: chip found @ 0xc2 (saa7134[0])
[  990.152931] saa7134[0]: i2c eeprom 00: de 17 28 71 10 28 ff ff ff ff ff ff ff ff ff ff
[  990.152944] saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  990.152955] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  990.152966] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  990.152976] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  990.152986] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  990.152997] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  990.153007] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  990.196171] saa7134[0]: registered device video1 [v4l2]
[  990.196208] saa7134[0]: registered device vbi0
[  990.196230] saa7134[0]: registered device radio0

```
 
I afterward read the change the tuner to 5, so I tried that unloaded the modules, and reloaded them (I think that is why there is a double error report).  However it seems that eeprom and i2c are giving me some problems.  Any ideas???  I have followed all the instructions, put the saa7134 file into /etc/modprobe.d/saa7134  and the other file.  Any ideas would be greatly appreciated.  Ohh, I too had to blacklist the saa7134_alsa module as that was an error I ran into too.  Please help!  :)

Shane

---

### Post by cariboo on 2008-05-13
I have to thank you for this thread. I've got an MSI TV@nywhere and I've never been able to get the card setting to load on a reboot. This has been going on for about 3 years now, every time I want to use the TV card I would remove and then load saa7134 with card=17. With the modprobe script it works every time. Thanks :guitar:

Jim

---

### Post by shane2peru on 2008-05-13
Ok, seems as though I have video but no sound.  Any ideas on that.  Turns out my webcam was interfering with my video camera and TVTime was only picking up the web cam.  I had to do some hacking to get webcam to work, followed this thread:  [http://ubuntuforums.org/showthread.php?t=634393&highlight=skype](http://ubuntuforums.org/showthread.php?t=634393&highlight=skype)  Sooo, that seems to be why my TV Card was not working even though I followed all those steps.  I unloaded that module, and then reloaded my TV Card (saa7134) module, and presto worked!  Now I just have to figure out how to get the sound working!  lol

Shane

---

### Post by Mze on 2008-05-13
I'm also learning here:

Post the output of command:

arecord -l

---

### Post by sofasurfer on 2008-05-14
I hope this is a first-come-first-served request for our arecord -l output.  Heres mine:


daryl@ubuntu:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 2: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SAA7134 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by shane2peru on 2008-05-14
> **Mze said:**
> I'm also learning here:

Post the output of command:

arecord -l

Sorry Sofasurfer, didn't mean to steal your thread!  :)  Mze  Here is the output of arecord -l:
```

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SAA7134 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Seems as though I have a very similar setup to Sofasurfer, if you post the answer to his, I can probably figure mine out.  Thanks!

Shane

---

### Post by Mze on 2008-05-14
I'm using info from the [V4lwiki website]("http://www.linuxtv.org/v4lwiki/index.php/Saa7134-alsa") for saa7134 cards

The info on the KWorld Global TV Terminator wiki page, indicates that saa7134-alsa might be problematic however give each option a try and see what works for you.

Run sudo nano /etc/modprobe.d/saa7134 once again

A: add these 2 lines to file to use OSS:

install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-oss
options saa7134-oss dsp_nr=1,2,3,4 mixer_nr=1,2,3,4

Save and exit.

Using the terminal, unload modules and reload with the same old commands below (one command at a time)

sudo rmmod saa7134_alsa
sudo rmmod saa7134
sudo modprobe saa7134 card=65 tuner=54

Run your TV program.

Do you have sound now?

If no sound, you might want to add this code:

echo saa7134 >> /usr/share/linux-sound-base/OSS-module-list

This adds saa7134 to your OSS-module-list.

unload and reload modules again, run TV program.

**note the part to the OSS-module-list, you can use your text editor to remove the added saa7134 from the command above if you still fail to receive sound.

Still no sound?

then try option B (below): edit your /etc/modprobe.d/saa7134 file again. delete the 2 lines you added above or simply overwrite them with the lines for ALSA below.

B: add these 2 lines to file to use ALSA:

install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa
options saa7134-alsa index=1,2,3,4

Save file and exit.

Unload and reload modules.

Run your TV program. 

No sound?

**************************
If after trying these 2 options you still get no sound then I guess you'd have to go over the saa7134 wiki on V4L or check the MythTV for saa7134again to see if there are any other options for Debian systems.

---

### Post by shane2peru on 2008-05-14
> **Mze said:**
> I'm using info from the [V4lwiki website]("http://www.linuxtv.org/v4lwiki/index.php/Saa7134-alsa") for saa7134 cards

The info on the KWorld Global TV Terminator wiki page, indicates that saa7134-alsa might be problematic however give each option a try and see what works for you.

Run sudo nano /etc/modprobe.d/saa7134 once again

A: add these 2 lines to file to use OSS:

install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-oss
options saa7134-oss dsp_nr=1,2,3,4 mixer_nr=1,2,3,4

Save and exit.

Using the terminal, unload modules and reload with the same old commands below (one command at a time)

sudo rmmod saa7134_alsa
sudo rmmod saa7134
sudo modprobe saa7134 card=65 tuner=54

Run your TV program.

Do you have sound now?

If no sound, you might want to add this code:

echo saa7134 >> /usr/share/linux-sound-base/OSS-module-list

This adds saa7134 to your OSS-module-list.

unload and reload modules again, run TV program.

**note the part to the OSS-module-list, you can use your text editor to remove the added saa7134 from the command above if you still fail to receive sound.

Still no sound?

then try option B (below): edit your /etc/modprobe.d/saa7134 file again. delete the 2 lines you added above or simply overwrite them with the lines for ALSA below.

B: add these 2 lines to file to use ALSA:

install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa
options saa7134-alsa index=1,2,3,4

Save file and exit.

Unload and reload modules.

Run your TV program. 

No sound?

**************************
If after trying these 2 options you still get no sound then I guess you'd have to go over the saa7134 wiki on V4L or check the MythTV for saa7134again to see if there are any other options for Debian systems.

None of these options worked for me.  I just can't get sound working.  When my speakers are plugged into the video card's sound out then I get nothing but static  buzzzz the whole time.  I tried the oss, and nothing but the same, however with the oss setting arecord -l doesn't report the card as active.  So I switched back to alsa, and still nothing.  I have spent way more time on this than I should have.  This just isn't working for me.  Video without sound is just not an option for me.  I guess I will have to hope and pray that a dev comes along and can fix this for the next release of Ubuntu.  Ohhh, well for now!

Shane
**EDIT:**  Ps I have been over that web site several times, no matter what settings I try I still get the eeprom fff  fff fff ff stuff in my dmesg.  I'm missing some setting somewhere, and haven't a clue.

---

### Post by Mze on 2008-05-14
What happens when you hold down the Right Arrow key on the keyboard?


With the info KnoppMyth wiki (being Debian) I was hoping it would work with UBuntu too.

Ah well, I guess we tried.

---

### Post by shane2peru on 2008-05-14
> **Mze said:**
> What happens when you hold down the Right Arrow key on the keyboard?


With the info KnoppMyth wiki (being Debian) I was hoping it would work with UBuntu too.

Ah well, I guess we tried.

Mze,  I appreciate your time and help with this!  THANKS!!!

Shane

---

### Post by sofasurfer on 2008-05-15
Mze.
I followed your instructions in post #23 above.
I added the 2 lines and then unloaded and reloaded the modules.
I still had no sound. So I continued and added the code to add saa7134 to OSS module list.
And lastly, I unloaded and reloaded the modules again. However, this time I got errors. Here they are...

daryl@ubuntu:~$ sudo rmmod saa7134_alsa
[sudo] password for daryl: 
ERROR: Module saa7134_alsa does not exist in /proc/modules

daryl@ubuntu:~$ sudo rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_oss

daryl@ubuntu:~$ sudo modprobe saa7134 card=65 tuner=54
WARNING: /etc/modprobe.d/saa7134 line 8: ignoring bad line starting with 'echo'

This was method 'A'. Tomorrow night I will try your method 'B'.
Then if that doesn't work and if you have any more suggestions great. 

Thanks again for you patience.

---

### Post by Mze on 2008-05-15
It looks like we've got to the end of the road with this card's sound problems. :( 

I searched the web (like everyone else) and read that those using Fedora 6 have got it working.

I have a [saa713x]("http://linuxtv.org/v4lwiki/index.php/Generic_SAA7134_Card_Installation") series card that I got working as per my previous posts. 

**A**
***
With ALSA being a problem for your card, the only other thing I found is to make your /etc/modprobe.d/saa7134 file look like this.

alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=65 tuner=54 oss=1

********
If that modification doesn't work, then you might want to check the Ubuntu irc channels where the developers might be able to be of help.

****

**B.**

You are getting this error because you most probably pasted this string: 

echo saa7134 >> /usr/share/linux-sound-base/OSS-module-list

into your /etc/modprobe.d/saa7134 file.

daryl@ubuntu:~$ sudo modprobe saa7134 card=65 tuner=54
WARNING: /etc/modprobe.d/saa7134 line 8: ignoring bad line starting with 'echo'

Check your /etc/modprobe.d/saa7134 and delete that line.
The string should be run as a command in terminal. I didn't seem to make that clear earlier.

All the best

---

### Post by sofasurfer on 2008-05-15
Ok, I'll take your advice. Got to go to work now. 
Later.

---

