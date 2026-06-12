---
title: "Audacity, JACK, and USB Latency Help Guidance Needed"
date: 2007-08-25
forum: Multimedia Production
---

### Post by Brendo613 on 2007-08-25
Taken from my original post at: 
[http://ubuntuforums.org/showthread.php?t=532157&highlight=Audacity+Jack](http://ubuntuforums.org/showthread.php?t=532157&highlight=Audacity+Jack)


[I]I'm using a Compaq N1015v, with an Alesis multi mix 16. There are random clicks all over the recordings I make, at different intervals. The mixer only allows for a stereo USB out (boo), but I'm glad I didn't opt for the 16 track firewire mixer straight up, seeing how much trouble I'm running into with the stereo mix ...

Today I tried some new tweaks. I do have DMA enabled, and am recording straight to the hard drive. I get fewer clicks recording mono, but they still exist and sound bad. I've done recordings with 8 mics plugged in at once during a jam and received clicks, but for testing purposes I'm plugging a guitar straight in to a channel with a built-in preamp. My sample rate is at 44.1khz, and I'm using 16 bit depth. I disabled auto-scroll while playing, and I disabled software playthrough. I even gave highest priority to Audacity through "sudo nice -n -20 audacity".[/I]

I'm now pretty sure I have to use JACK to configure my soundcard correctly in correlation with my OS (Ubuntu 7.04) ... 

I don't know how to use JACK, at all.  What do I do?

Thank you,

=Brendan

---

### Post by Amazona aestiva on 2007-08-25
Install JACK's configuration system:
```
sudo apt-get install qjackctl
```

After install there should be a shortcut in Apps.->Sound and Video->JACK Control

There You can configure JACK's in&output, sample rate and much more!

---

### Post by Brendo613 on 2007-08-25
Right, I have JACK, but I don't know which way to set it.  For example, I open up qjackctl, and I can tool around with what's there, but I don't know the differences between jackd, jackd-realtime, etc., what the Xrun thing is ... I really could use a general tutorial on what all of this means, so I can understand it more, you know?  I don't know how to set any of the things in Jack, or how to know it's working in conjunctino with Audacity.

=Brendan

---

### Post by variona on 2007-08-25
When you say the 'mixer' do you mean Alesis or software mixer? Are you using the Alesis firewire interface or are you using the analog in of your onboard soundcard? (or am I missing something about an usb interface here). What are the specs of your Computer?
Variona

---

### Post by Brendo613 on 2007-08-25
I'm using a USB 1.1 Stereo out from the Alesis multimix 16 into the USB 1.1 port on my computer.  I got a PCMCIA card with USB 2.0, but that's been too tough to configure ...

Anyway, the computer has an AMD Athlon XP, 1800mhz, 20 gig hard drive, 768 ram, and is running Ubuntu 7.04.

I just ran JACK a few times, crashed the computer twice, and on the third try I set it to 128 frames/period, 44100k, 4 periods/buffer, on ALSA with a timout of 200ms and 128 port maximum.  I barely know what any of this means :shock::grin:.  The latency is  11.6 ms.

This is what popped up in the little window that comes along when jack is "running" :

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|128|4|44100|2|2|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 128 frames, buffer = 4 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 4 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 4 periods for playback
**** alsa_pcm: xrun of at least 15.404 msecs
**** alsa_pcm: xrun of at least 3.254 msecs
10:42:09.304 Server configuration saved to "/home/brendan/.jackdrc".
10:42:09.309 Statistics reset.
10:42:09.321 Client activated.
10:42:09.327 Audio connection change.
10:42:09.352 Audio connection graph change.
**** alsa_pcm: xrun of at least 0.256 msecs
**** alsa_pcm: xrun of at least 50.015 msecs
10:42:09.439 XRUN callback (1).
10:42:11.238 Transport start.
**** alsa_pcm: xrun of at least 35.553 msecs
10:42:11.301 XRUN callback (3).
**** alsa_pcm: xrun of at least 7.123 msecs
**** alsa_pcm: xrun of at least 8.114 msecs
10:42:11.370 XRUN callback (4 skipped).
**** alsa_pcm: xrun of at least 8.186 msecs
**** alsa_pcm: xrun of at least 25.140 msecs
**** alsa_pcm: xrun of at least 5.617 msecs
**** alsa_pcm: xrun of at least 6.174 msecs
**** alsa_pcm: xrun of at least 1.062 msecs
**** alsa_pcm: xrun of at least 5.793 msecs
**** alsa_pcm: xrun of at least 3.216 msecs
**** alsa_pcm: xrun of at least 5.104 msecs
10:42:13.386 XRUN callback (7 skipped).
10:42:13.422 XRUN callback (14).
**** alsa_pcm: xrun of at least 0.709 msecs
**** alsa_pcm: xrun of at least 7.760 msecs
**** alsa_pcm: xrun of at least 8.157 msecs
**** alsa_pcm: xrun of at least 14.952 msecs
**** alsa_pcm: xrun of at least 6.648 msecs
**** alsa_pcm: xrun of at least 7.698 msecs
**** alsa_pcm: xrun of at least 3.566 msecs
**** alsa_pcm: xrun of at least 9.871 msecs
10:42:15.432 XRUN callback (7 skipped).
10:42:15.473 XRUN callback (22).
**** alsa_pcm: xrun of at least 25.154 msecs
**** alsa_pcm: xrun of at least 41.938 msecs
**** alsa_pcm: xrun of at least 9.875 msecs
**** alsa_pcm: xrun of at least 0.969 msecs
10:42:17.458 XRUN callback (3 skipped).
10:42:17.486 XRUN callback (26).
**** alsa_pcm: xrun of at least 17.765 msecs
**** alsa_pcm: xrun of at least 12.816 msecs
**** alsa_pcm: xrun of at least 0.582 msecs
**** alsa_pcm: xrun of at least 0.900 msecs
**** alsa_pcm: xrun of at least 0.975 msecs
10:42:19.481 XRUN callback (4 skipped).
**** alsa_pcm: xrun of at least 25.314 msecs
10:42:19.530 XRUN callback (31).
**** alsa_pcm: xrun of at least 2.164 msecs
**** alsa_pcm: xrun of at least 8.160 msecs
**** alsa_pcm: xrun of at least 8.161 msecs
**** alsa_pcm: xrun of at least 12.922 msecs
**** alsa_pcm: xrun of at least 11.348 msecs
**** alsa_pcm: xrun of at least 5.484 msecs
**** alsa_pcm: xrun of at least 4.297 msecs
**** alsa_pcm: xrun of at least 2.159 msecs
10:42:21.507 XRUN callback (8 skipped).
10:42:21.535 XRUN callback (40).
**** alsa_pcm: xrun of at least 14.340 msecs
**** alsa_pcm: xrun of at least 0.367 msecs
**** alsa_pcm: xrun of at least 2.100 msecs
**** alsa_pcm: xrun of at least 0.967 msecs
10:42:23.531 XRUN callback (3 skipped).
**** alsa_pcm: xrun of at least 29.581 msecs
10:42:23.577 XRUN callback (44).
**** alsa_pcm: xrun of at least 22.162 msecs
**** alsa_pcm: xrun of at least 3.121 msecs
**** alsa_pcm: xrun of at least 25.893 msecs
**** alsa_pcm: xrun of at least 10.872 msecs
**** alsa_pcm: xrun of at least 0.192 msecs
10:42:25.554 XRUN callback (5 skipped).
10:42:25.587 XRUN callback (50).
**** alsa_pcm: xrun of at least 2.838 msecs
**** alsa_pcm: xrun of at least 8.211 msecs
**** alsa_pcm: xrun of at least 16.150 msecs
**** alsa_pcm: xrun of at least 18.124 msecs
**** alsa_pcm: xrun of at least 9.493 msecs
**** alsa_pcm: xrun of at least 0.288 msecs
**** alsa_pcm: xrun of at least 6.676 msecs
10:42:27.578 XRUN callback (6 skipped).
**** alsa_pcm: xrun of at least 29.476 msecs
**** alsa_pcm: xrun of at least 4.284 msecs
10:42:27.644 XRUN callback (57).
**** alsa_pcm: xrun of at least 2.165 msecs
**** alsa_pcm: xrun of at least 15.189 msecs
**** alsa_pcm: xrun of at least 14.032 msecs
**** alsa_pcm: xrun of at least 9.532 msecs
**** alsa_pcm: xrun of at least 0.816 msecs
**** alsa_pcm: xrun of at least 21.871 msecs
**** alsa_pcm: xrun of at least 1.814 msecs
**** alsa_pcm: xrun of at least 8.197 msecs
**** alsa_pcm: xrun of at least 8.167 msecs
**** alsa_pcm: xrun of at least 9.149 msecs
**** alsa_pcm: xrun of at least 8.131 msecs
**** alsa_pcm: xrun of at least 30.871 msecs
**** alsa_pcm: xrun of at least 16.878 msecs
10:42:29.689 XRUN callback (14 skipped).
**** alsa_pcm: xrun of at least 32.549 msecs
10:42:29.746 XRUN callback (72).
**** alsa_pcm: xrun of at least 0.518 msecs
**** alsa_pcm: xrun of at least 8.197 msecs
**** alsa_pcm: xrun of at least 22.720 msecs
**** alsa_pcm: xrun of at least 15.173 msecs
**** alsa_pcm: xrun of at least 11.153 msecs
**** alsa_pcm: xrun of at least 28.152 msecs
10:42:31.728 XRUN callback (6 skipped).
10:42:31.756 XRUN callback (79).
**** alsa_pcm: xrun of at least 0.340 msecs
**** alsa_pcm: xrun of at least 8.201 msecs
**** alsa_pcm: xrun of at least 8.150 msecs
**** alsa_pcm: xrun of at least 18.156 msecs
**** alsa_pcm: xrun of at least 0.883 msecs
**** alsa_pcm: xrun of at least 2.428 msecs
**** alsa_pcm: xrun of at least 5.504 msecs
10:42:33.754 XRUN callback (6 skipped).
10:42:33.782 XRUN callback (86).
**** alsa_pcm: xrun of at least 4.368 msecs
**** alsa_pcm: xrun of at least 6.304 msecs
**** alsa_pcm: xrun of at least 6.142 msecs
**** alsa_pcm: xrun of at least 0.188 msecs
10:42:35.776 XRUN callback (3 skipped).
10:42:35.818 XRUN callback (90).
**** alsa_pcm: xrun of at least 25.971 msecs
**** alsa_pcm: xrun of at least 23.626 msecs
**** alsa_pcm: xrun of at least 10.373 msecs
**** alsa_pcm: xrun of at least 28.553 msecs
10:42:36.518 Client deactivated.
10:42:36.528 JACK is stopping...
**** alsa_pcm: xrun of at least 0.275 msecs
jack main caught signal 15
**** alsa_pcm: xrun of at least 2.787 msecs
**** alsa_pcm: xrun of at least 2.449 msecs
**** alsa_pcm: xrun of at least 2.508 msecs
**** alsa_pcm: xrun of at least 2.508 msecs
**** alsa_pcm: xrun of at least 2.504 msecs
**** alsa_pcm: xrun of at least 2.363 msecs
**** alsa_pcm: xrun of at least 4.163 msecs
no message buffer overruns
10:42:38.597 JACK was stopped successfully.


These xruns were popping up like crazy, the whole time ... is that normal?  Can that explain why I'm getting all these random clicks and misses in my recordings?

=Brendan

---

### Post by Amazona aestiva on 2007-08-25
I'm not master of JACK, sorry... 
However this should help:[http://www.linuxjournal.com/article/8354]("http://www.linuxjournal.com/article/8354")

---

### Post by nalmeth on 2007-08-25
So this is a firewire device, correct? In the setup window in qjackctl, change the driver from ALSA to freebob. You may see a dramatic improvement with the xruns.
Enable realtime, and try bumping up the frames/period to 256/512

Tweak your settings until you reach a level where you are only experiencing xruns when opening/closing applications, while keeping latency to a minimum.

The problem is that Ubuntu comes with a kernel that isn't good for audio production. You can install a realtime kernel which should greatly improve your performance, but I would suggest you first get to know JACK and how it operates a bit better. 

Install Ardour, and run it when you have jack running. You will see Ardour in the JACK Connections window.
When you add a track in Ardour, you should see the automatic connections made by JACK to your audio device.

-- EDIT: From a google search, I thought your device was firewire. If it is USB, don't use the FREEBOB driver. It is meant for firewire --

---

### Post by variona on 2007-08-25
> **Brendo613 said:**
> 
These xruns were popping up like crazy, the whole time ... is that normal?  Can that explain why I'm getting all these random clicks and misses in my recordings?

=Brendan

Yes. Rule of thumb xrun=click . If possible use the firewire interface. Another issue is, of course, that standard ubuntu kernels are not designed to be optimized for audio - I'm not sure yours is a parameter issue. Xruns are are buffer over or underruns (means soundcard can't deliver enough data or PC can't manage all the data), therefore you could try to go for higher latency and increase the buffersize. But to use sound seriously you should look out for ubuntu studio.
variona

---

### Post by Brendo613 on 2007-08-25
All right!  Looks like the trick was upping the buffersize, but  Ubuntu froze when I started laying down a second track while playing the first ... any suggestions on that, or should I just commence general noodling until I hit the right combo of parameters?

Also, I can never get it to work with Realtime :-\ not sure why ...

=Brendan

---

### Post by variona on 2007-08-27
> **Brendo613 said:**
> All right!  Looks like the trick was upping the buffersize, but  Ubuntu froze when I started laying down a second track while playing the first ... any suggestions on that, or should I just commence general noodling until I hit the right combo of parameters?

Also, I can never get it to work with Realtime :-\ not sure why ...

=Brendan
Probably the wrong kernel, standard kernels are not optimized for audio with realtime priority (which is OK - as this is not their aim).  Try the 
linux-lowlatency meta-package which works fine with me.
variona

---

### Post by nalmeth on 2007-08-27
Brendan,

Perhaps there are permission problems stopping you from using realtime.

If you are using firewire (recommended), hit ALT-F2, and use this command to edit the following file:
```
gksudo gedit /etc/udev/rules.d/40-permissions.rules
```
In this section,
```
# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
KERNEL=="raw1394",            GROUP="disk", MODE="0666"
KERNEL=="dv1394*",            GROUP="video"
KERNEL=="video1394*",            GROUP="video"
```Make the changes to your file to make it look like this ```
KERNEL=="raw1394",            GROUP="disk", MODE="0666"
```Close the file, then hit ALT-F2 again, and edit another file:
```
 gksudo /etc/security/limits.conf
```
Add the following lines to the end of the file:
```
@audio - rtprio 99
@audio - memlock 512000
@audio - nice -19
```You should be able to enable realtime after this, you may have to reboot.

---

### Post by Brendo613 on 2007-08-28
I downloaded and installed the low-latency linux kernel, and am really excited to try the codes that were just posted, but I don't have the firewire model, mine is USB 1.1 based and gives a stereo USB signal to the computer.  What should I do differently to configure the port?  

I feel so close to the right solution!

=Brendan

---

### Post by Brendo613 on 2007-08-28
Also, "gksudo /etc/security/limits.conf" doesn't work, and neither does " gksudo /etc/security/limits.conf.".  I can open  gksudo /etc/security/limits.conf. and see what I need to add, but I can't save it without being logged in as root.  Help!

---

### Post by nalmeth on 2007-08-28
Sorry Brendan, my mistake:
```
gksudo **gedit** /etc/security/limits.conf
```
gksudo is the command that gives you root permission to edit the file, **gedit** is the text editor.

---

### Post by Brendo613 on 2007-08-29
Well, I can enable realtime mode now, but it gives me the error of cannot connect to JACK server as client.  I don't know what that means, but I can still press the play button  anyway ... what does that button do, by the way?  There's start, and then play, and I don't know what it's for.  Should I turn it off for audio playback?

=Brendan

---

### Post by nalmeth on 2007-08-29
Those buttons control the Jack transport.

Basically, you can have the playback of all JACK applications (like Ardour, hydrogen) controlled from one place.

When you push play, and Ardour + Hydrogen are using JACK transport, both apps start 'playing'

You can control this behavior in the individual apps

About JACK not starting.. There must be something in your settings, you will have to play around until you get it to start. I can't help in too much detail right now, but if you post your setup I can look again later tonight.

One thing though, is there any way to use firewire with this device? Or do you just not have a cable?

---

### Post by Brendo613 on 2007-08-29
Nah, this is a USB model only.  I can mess around with settings and get the error messages to go away, but I still wind up with clicks in the recording.  The only way I've gotten almost perfect recording is with a mono signal being recorded at 16 bit.  Even if this model did firewire, I'd have to get a PCMCIA firewire card and config all those drivers .., I have a USB 2.0 card, but haven't figurd out yet how to get that going ... ndiswrapper worked for me with my wireless card pretty easily, though; maybe the USB 2.0 card would help some of these ridiculous problems?

=Brendan

---

### Post by fredj on 2007-08-30
To get low latency sound you really need to run jack in Realtime. To do that 
you need to install the realtime kernel (There is a sticky at the top of this
forum calling for real time kernel testing. It also tells you where to get the 
realtime kernel). When you have installed it you also need to make a few
tweaks to the limits.conf file.

However the first thing is to install the realtime kernel. You may find after you
install the realtime kernel that ndiswrapper stops working. To get it working
again you may need to recompile it after installing the realtime kernel headers.
Of course if you select the previous kernel at boot rather than the realtime
one you should find that ndiswrapper still works.

---

### Post by tgalati4 on 2007-08-30
Download and burn a disk of Dynebolic 2.4.2.  It's a Live CD designed for recording audio (and other stuff).  It pretty much runs out of the box.  Give it a spin.

---

### Post by Brendo613 on 2007-08-30
I am having an absolutely AWFUL time here.

The Realtime Kernel wouldn't install correctly ... even with sudo in the command, it threw a permission error trying to open a folder ... 

Dynebolic wouldn't load on the laptop, so I tried it on my desktop just for the hell of it ... (am actually using it right now).  It doesn't recognize my sound card at all.  

All I want is to have NO CLICKS on my recordings!  AHHH!  Maybe Audacity is the culprit?  I tried downloading Ardour, but I haven't been able to compile anything before ... I've just installed packages :( Would that be any better?

---

### Post by nalmeth on 2007-08-30
It can be a frustrating experience treading around new territory. I still have minor (although private) outbursts when I'm having problems I can't solve.
Sometimes it takes an unconventional approach, sometimes a lot of extra time and effort, and sometimes things just work when you don't expect them to (or the other way around).

Just stay patient, the ultimate satisfaction will come when you achieve what you're working towards.

Lets start with the realtime kernel problem, what specifically went wrong? Which folder are you trying to open?
All you should need to do is open your sources.list:
```
gksu gedit /etc/apt/sources.list
```Add the following lines to the bottom (if you are using feisty):
```
deb http://www.texware.it/ubuntu feisty/
deb-src http://www.texware.it/ubuntu feisty/
```Save and close the file, then add the key: 
```
wget -q http://www.texware.it/ubuntu/feisty/BBA3222D.gpg -O- | sudo apt-key add -
```Update APT:
```
sudo apt-get update
```Install the kernel:
```
sudo apt-get install linux-realtime
```Then reboot!

If you have problems loading the X Server, just reboot and choose your old kernel, and you will be back to normal
[U]
Did anything go wrong in those steps?[/U]

EDIT: You don't need to compile Ardour! If you installed some packages that will probably be fine, if you want the latest version there is a .deb available, but what you have should work fine. Audacity doesn't work with JACK, whereas Ardour requires it.

---

### Post by variona on 2007-08-30
> **Brendo613 said:**
>   AHHH!  Maybe Audacity is the culprit? 
Not guilty!
Sorry to hear that dyne:bolic didn't work for you. If your soundcard was recognised in ubuntu maybe you should give ubuntustudio a shot? Is there any specific reason you need to use Jack? I'm asking because I begin to wonder if your hardware records clickless with ALSA or OSS. Does your USB Interface mixer register as usb audio device? are there other devices hanging on the same bus? Are there shared interrupts on the pci bus?
These are rethorical questions - I hope they give you ideas about possible suspects.
As for  Audacity: Out of interest I once made a small production (a play 45mins long with 12 tracks) using a Knoppix Live CD on a via epia board 600MHz CPU, 512 MB RAM, on board soundcard, no local harddisk but 100Mbit onboard nic using nfs on local LAN for storage, there was not a single problem! The customer was impressed.  Therefore I'm sure Audacity is not guilty.

HTH
variona

---

### Post by fredj on 2007-09-01
I think you are getting lots of conflicting advice here and it just isn't
working for you. You perhaps need to think about what you want to 
achieve and how to achieve it. If you just keep following all these
different bits of conflicting advice you will get nowhere.

---

### Post by Brendo613 on 2007-09-01
I tried the realtime kernel, but it takes a long time to start up, and nothing's really any different.  A friend of mine has a better-equipped laptop, currently running XP and Ubuntu.  I think I should try my mixer on his computer, and see just where the problem lies ... it's possible it's actually the mixer and nothing else, I guess.  Weird thing is that different microphones make more clicks occur ... Go figure!  Te mixer's also the only thing plugged into the bus at the moment.  Good suggestion, though


As far as conflicting advice, I thought of it more as different approaches to fixing this issue in different ways.  After fooling around with JACK, I've found combinations of frame settings, period/buffer settings, and port maximum settings which allow JACK to be recognized in Audacity, thus letting me work through the JACK server.  What I want to achieve is a click-free recording, and how I do i t ... well, that's what this whole thread is for, but now I think it's time to test the other components in this lineup.

Anyway, how is Ubuntu Studio different?  I looked into it, but it just seems to have a few pre-installed packages and a different startup screen.  I already have a low-latency kernel, so I don't really see why it'd be any better to use Studio, but I might be overlooking something.

=Brendan

---

### Post by variona on 2007-09-02
If you are using a lowlatency kernel - it probably won't make the difference. It was just a guess you are using the generic kernel. BTW does your onboard soundcard work? Are you able to record clickless in Audacity without the usb mixer?
variona

---

### Post by krissovo on 2007-09-03
Hi 

I feel for you but I have just had a similar issue with my Alesis  USB mixer.  You will be happy to know that mine is working perfectly now but it took a little pain to get going.

Firstly I was running feisty and had the clicks, its due to Xruns and in Feisty it was still clicking with the latency set at 49mls. I then found and downloaded studio once installed I followed this process to set up jack.

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

Once i did that I had to play around with the settings for Frames/Period to get it running with virtually no Xruns (mine is at 128 now 5 milli seconds or so)

Once done I can play with near zero latency and record into ardour no bother.

A tip is to use the ALSAgui to set your input volumes as mine was set very high and clipped everything.  Also if you want to use sooper looper and creox I would advise using pacthage (in the app menu) to set jacks connections as I have much better results than using the connections in jack.

A couple of issues I still have is that I have to boot my laptop up with the mixer connected and that I cannot get firefox to play through the mixer.

I could post some screen shots if you are still having trouble!

Good luck

---

