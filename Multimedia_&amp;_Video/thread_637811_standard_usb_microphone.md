---
title: "standard usb microphone"
date: 2007-12-11
forum: Multimedia &amp; Video
---

### Post by beauman on 2007-12-11
Hi!

 I would like to report  hardware, that can not be properly installed.

On my Ubuntu 7.10 system the usb microphone "rode podcaster"
is not working properly.

The microphone comes without win driver and is just a standard usb hardware.

I can't record from it. 

The mic features also a headphone output. 
If I try to output the test signal from the audio configuration dialog in
"system/einstellungen/audio" (in englisch maybe system/properties/audio?)
the test signal will terminate after about a second or so and the conf
application will crash.
/var/log/messages says:
Dec 11 17:28:50 LosBastardos kernel: [  255.984000] 4:1:1: cannot get freq at ep 0x1
I tried the same under edgy eft, where the test output did not terminate.


Would you advice me to keep the mic and wait until somebody has
solved the bug or should I give it back?

Regards,

jens-christian


addition 05 jan 2008

I gave the rode podcaster to my dad, where it brings excellent
results under win. I bought the SE USB 1000A (which is even 40&#8364; cheaper)
and it works without any problems under ubuntu / gutsy gibbon.
The results are good. Maybe the sound level is a little low.
But I really like it. Hope somebody can fix the podcaster issue.

greetz,
jc

---

### Post by jwkungfu on 2008-01-28
Hello Beauman,
Please excuse the following angry rant...
I have just got back from my friends place after an aborted band practice session...
Aborted because I couldn't get my Podcaster to work either.....!!!!!!!!!??
Not happy.
Not happy at all....
My Lexmark X1170 printer/scanner doesn't work on Ubuntu either.
As I have only just converted to Linux/Ubuntu a few weeks ago, I am REALLY P#SSED OFF!!!
P#ssed off with all computer "developer" MORONS!!!!
They design packages with more functions than anybody will EVER use, and leave the public stranded because their hardware doesn't work....???
Hello??!!!? How about making packages that have LESS features and that are more bullet proof to run hardware with????? That is DEVELOPMENT!!!!
Sorry for the rant...
I live in Australia and I will phone RODE and try and find out if there is some sort of solution to our dilema...
If you come across an answer in the meantime could you send me the solution?
Many thanks,
All the best.
John W.
:guitar:
:lolflag:

---

### Post by beauman on 2008-02-24
Hi!  

As I mentioned above, I bought a USB mic from an other company.
That solved the problem for me.

It's still funny, that a "class compliant" USB device doesn't work.

>P#ssed off with all computer "developer" MORONS!!!!
>They design packages with more functions than anybody will EVER use, and leave the public >stranded because their hardware doesn't work....???
>Hello??!!!? How about making packages that have LESS features and that are more bullet proof to >run hardware with????? That is DEVELOPMENT!!!!
>Sorry for the rant...

Well, what should I say? The right solution would be to design all the functions
you need AND to make it bullet proof. Some people say, that sound is awesome under
linux, but this is not true. I, for example, I have to boot twice to make my onboard sound
and my sound card work. 
ALSA is quite ok, but sometime its also confused.
And than all the applications which just support oss like vmware ... 

Jack is nice, but too hard to operate. It would be nicer, if it could do everthing
by default and you could just change things if you like too. For example:
if I create a new audio track in ardour, why do I have to connect it to my PCM-outputs
by hand?

Sometimes sound even in nautilus crashes. If I then click on a sound file the icon would change
from the notes to blank. With "killall nautilus" the problem is fixed.

Well, all in all, there is sound under linux, but its nether bullet proof nor easy to operate.

Good luck with using it anyway!
greetz, beauman

---

### Post by jwkungfu on 2008-02-25
Hello Beauman,

I have one more trick to try with my Rode Podcaster USB microphone before I throw in the towel...
I am going to dual boot my Dell PC Laptop with Ubuntu and M$ Windoze.
When I need to use the microphone, I will boot up with M$ Windoze (I will partition my hard drive with just enough space to do this) and then I will record on to an external hard drive.
Then for everything else, I will boot up with Ubuntu....
Haven't done this yet, but I am assured by people who do know a fair bit about computers that it is possible...

Stay tuned...

john.

---

### Post by beauman on 2008-02-25
Hi John!

Yes, its of course possible to record under win and do the rest
under ubuntu. A little annoying maybe. To set up a dual boot system is
not a big problem. Just take care that you don't delete any existing
data. Back up everything!!! Windows will override the master boot sector.
After you have installed windows you will have to boot from your ubuntu
disk and "chroot" into your installed ubuntu to execute grub-install.
See for example [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
and look for "chroot"


What you also can try, is to run windows in a virtual machine.
This solution might only have the problem of latency.
But you could try at least.

I have played with both vmware and virtual box the last days
and found out that vmware runs a little bit better. The vmware
server is for privat users free of charge. You can set the virtual
machine to fullscrenn, so your computer appears to be a real 
win machine. You can also assign usb devices to the virtual 
machine, as long as they are not used in the host system.
For an usb stick you have to unmount it first in your file manager
before you can tell vmware  to assign it to windows.
For a mic you have to use the black list in some config file.
Too interchange data between the vmware virtual machine
and ubuntu install samba on the host and export some folders.
Under windows you create a private network.

Well, but this solution might have a problem with performance.
That means your recordings might be spoiled. 

If you really want to use ubuntu for recording, it's highly recommended
to use a real time kernel. Ubuntu studio comes for example
with such a kernel. I recorded some old records a couple of weeks
ago WITHOUT such a realtime kernel and I had two or three "cracks"
in the recordings.  There is a so called "meta-package" called 
ubuntu studio for the normal ubuntu edition. This installs a couple of
audio tools on your ubuntu desktop. Maybe it also ships with the realtime
kernel (I haven't tryed myself)

Get yourself a mic that works with ubuntu! Somebody 
is going to fix the issue with the podcaster quite soon, I'm sure about that,
but you don't know when this is.

The SE electronics mics work for example. They offer one that is even more 
expensive than yours and a midrange one for about 140€ (the se 1000a that i bought)

Yesterday I had to show my dad (who now owns my podcaster) how to
record and multi-channel edit under windows. The podcaster
is really a good mic. That is for sure. I showed him how  to cut music
and his recorded speech together, that was fun :)

Yesterday I saw how close Ardour is to existing software under windows. And Ardour is 
quite a good recording tool compared to the commercial digital audio workstation software.

For the "band-recording" case there is also a special linux audio project.
I can't remember the name of it, too bad. Maybe you find it.

Well, let me know, how you solve your recording problem!
greetz, beauman

---

