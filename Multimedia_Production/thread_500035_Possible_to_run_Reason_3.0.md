---
title: "Possible to run Reason 3.0?"
date: 2007-07-13
forum: Multimedia Production
---

### Post by b0ng0 on 2007-07-13
I was wondering if it is at all possible to get Reason 3.0 to run in Ubuntu Feisty. So far I have managed to install it through WINE and it can play back, but there is a deal of stuttering and also my midi keyboard will not work properly with it (although it is detected).

Would it work to emulate Windows (like a Virtual Windows, i'm not sure what those programs are called) and then run it from that or is this not possible?

Thanks for any help

---

### Post by fredj on 2007-07-13
It is unlikely that you will get any hardware intensive program such as Reason to run properly through 
Wine.
In Ubuntu to use your PC as a music station you need to install the real time kernel (see the first sticky) at
the top of this forum. Then you should install ubuntu studio including the jack audio server. Then investigate
the programs included in ubuntu studio and learn how to use them.

---

### Post by mcduck on 2007-07-15
Whatever you do to make it run, you won't get ASIO sound so latencies will be pretty high..

---

### Post by cino on 2007-07-16
this is the kinda info I have been searching for....

---

### Post by skipkent on 2007-07-16
Try it anyways, and let the rest of us know how you make out!  Latency on Linux/low latency kernel is pretty amazing.  I get awesome latency with the built-in motherboard nvidia sound card.  Synths in realtime, software monitoring with effects, the works.

That's with Linux apps, of course.  I haven't tried installing any of my old Windows stuff.  I'm very happy with Linux as my studio environment.  If I do install my old Tracktion 2 (awesome windows app) it'll be for curiosity more than anything else.

---

### Post by mcduck on 2007-07-17
> **skipkent said:**
> Try it anyways, and let the rest of us know how you make out!  Latency on Linux/low latency kernel is pretty amazing.  I get awesome latency with the built-in motherboard nvidia sound card.  Synths in realtime, software monitoring with effects, the works.

That's with Linux apps, of course.  I haven't tried installing any of my old Windows stuff.  I'm very happy with Linux as my studio environment.  If I do install my old Tracktion 2 (awesome windows app) it'll be for curiosity more than anything else.

Low latency kernel won't help, as Win/MAc audio apps won't use native linux audio. And the only way Win apps can get small latencies is by using ASIO (which pretty much gives the program direct control over your sound card)  and that won't work in Wine or any virtualisation software.

(Of course if you don't need to do anything in real time, like playing the notes in with MIDI keyboard or record anything, then Reason ay work quite ok with Wine)

---

### Post by skipkent on 2007-07-17
There are some tidbits in this thread that might be worth looking into (wine asio):
[http://ladspavst.linuxaudio.org/](http://ladspavst.linuxaudio.org/)

I didn't know that the low latency kernel wouldn't help wine apps.  Thanks for shedding some light.

I'd be interested to know if Reason work in Wine, even if only in the point-n-click sense as you mention, not realtime.

---

### Post by stmiller on 2007-09-04
Bumping this thread with some of my more recent findings:
-----------------------

I have had success in running Reason 3.0.4 under wine 0.9.43
Specs: 64bit Kubuntu Feisty Linux 2.6.22.1 low latency kernel
Soundcard: onboard VIA 8237 (set at 48000kHz)
AMD X2 3600 2x512MB

Ran installer, runs fine.

Then starting the program, it prompts for CD 2 and 3, but the window is behind the splash screen. Just right click on the 'Insert CD' from the task bar and choose 'move' to move the hidden window.

Inserting CD2 it would not read my CD. Do something like this:

```

sudo umount /dev/cdrom
sudo mount /dev/cdrom /media/cdrom0

```

and Reason should then detect the CD and start copying the contents. Or alternatively, adjust the settings in winecfg for your cdrom location.

When it prompts for the serial, that window too was hidden behind the splash screen. Right click on the 'Enter Serial' window from the task bar, and click 'move' to move it to a place where you can see it and enter your serial.


I then got this error when running Reason:

"Cannot open file the file "Reason" is not a type of file, that the application supports"

To fix this, change your icon link for Reason from
```

wine "C:\Program Files\Propellerheads\Reason\Reason.exe"

```
to
```

wine "C:\Program Files\Propellerheads\Reason\Reason.exe C:\Program Files\Propellerheads\Reason\Demo Songs\Orkester Demo.rps"

```
In the KDE menu you just right click on the item>edit, and then and edit the command line for that item.

Audio and MIDI in/out WORK. My wine only has options for ALSA and OSS. I uncommented the lines for the jack driver in ~/wine/config but I'm still having a problem getting jack to show up for an option in winecfg. I know with jack Reason will be even better.

Under winecfg > audio I set DirectSound Hardware Acceleration to Full.

OK, so now starting Reason, I manually added my midi controller (do not select auto-detect!) which is a USB Edirol PCR-M30. You can also use qjackctl to attach your usb midi controller to 'MIDI Through' which Reason also detects, if Reason fails to see you controller.

Then I adjusted some other prefs in Reason:

Reason Prefs>Audio>choose your soundcard

Reason Prefs>Audio>Buffer Size: 2048 (adjust as needed to find a good setting)

Reason Prefs> CPU limit> NONE

And now I have ZERO noticable latency from my midi keyboard.
Reason under wine seems to take up a LOT of cpu. Playing back the demo song took 85-95% of 200% for my AMD X2 3600. As soon as I can figure out getting the wine jack driver working, this will all be much improved I'm sure. 

I'd say you will need a recent rig to run Reason in wine at this point, at least a recent AMD or Intel cpu from the last couple of years.
I'm still going to fiddle with some settings and keep investigating wine+jack...

Ok hope this helps! Here's a screenshot:

[[img]http://xs319.xs.to/xs319/07363/reason.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs319&d=07363&f=reason.png)

EDIT: [As this person has stated here]("http://ubuntuforums.org/showpost.php?p=1283657&postcount=8"), the large amount of CPU used by Reason is not audio related, but rather related to the X11 rendering. I minimized Reason while playing the same default song and CPU usage went down to 35-40%.

---

