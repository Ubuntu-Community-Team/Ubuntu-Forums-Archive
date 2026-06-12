---
title: "Digital Camera! Help my father completely switch to Linux!"
date: 2009-01-17
forum: Multimedia Software
---

### Post by bocmaxima on 2009-01-17
After refusing to fix my fathers windows box, he let me install Ubuntu on it after I touted how everything is awesome on it! He is 53 and its kind of a big deal, since Linux is so "different", but the printer is working, it displays a better resolution, wireless even is stronger (Wifi is getting better), however, we cant download the pictures from his digital camera. Its a little older Kodak DX7590, and when he tries to mount the camera it says

"Error Connecting to Camera

Received Error "Unspecified Error" while connecting to camera"

And he uses his camera enough for it to be a big issue. It connected to XP fine and works flawlessly on my Mac. I really need to rectify this issue before I have to put XP back on his machine.

He has a 6+ year old Toshiba Satellite

Any ideas? I gotta fix this!!!

---

### Post by srt4play on 2009-01-17
What version of Ubuntu did you install?  A quick google search shows that [gphoto2 is supposed to support the DX7590]("http://gphoto.org/proj/libgphoto2/support.php").  You might try installing gtkam and try to access the camera with that program.

---

### Post by bocmaxima on 2009-01-17
> **srt4play said:**
> what version of ubuntu did you install?  A quick google search shows that [gphoto2 is supposed to support the dx7590]("http://gphoto.org/proj/libgphoto2/support.php").  You might try installing gtkam and try to access the camera with that program.


8.10

---

### Post by bocmaxima on 2009-01-18
Im also getting "PTP I/O Error"

---

### Post by bocmaxima on 2009-01-18
No one has any other ideas? My idea is to  get him an SD card and a reader, lol, but thats like a total hack. Better than reinstalling windows though.

---

### Post by srt4play on 2009-01-18
> **bocmaxima said:**
> No one has any other ideas? My idea is to  get him an SD card and a reader, lol, but thats like a total hack. Better than reinstalling windows though.

How is that a hack? Sounds like a reasonable and cheap solution to me.  Did you try the program gtkam?

---

### Post by albinootje on 2009-01-18
> **bocmaxima said:**
> Im also getting "PTP I/O Error"

For some cameras you need to put the camera in PTP mode (or something) otherwise it won't work with gphoto based solutions.

Perhaps not relevant for your camera, see here :

[http://libptp.sourceforge.net/README](http://libptp.sourceforge.net/README)

> 
Note that for some HP, Nikon, Canon and Sony cameras you have to switch
them to PTP mode as in most cases the camera is dual mode:
PTP and USB Mass Storage or PTP and native.


(In Arch Linux I had to run gtkam with sudo before it would work (I didn't spend enough time on finding out which groups and device permissions were needed), haven't tried recently in Ubuntu.)

---

### Post by bocmaxima on 2009-01-19
> **srt4play said:**
> How is that a hack? Sounds like a reasonable and cheap solution to me.  Did you try the program gtkam?

Yes

It shows up when I detect it, but gives the error.

---

### Post by BetterSense on 2009-01-19
I've never attempted to 'connect a camera' to any sort of computer. I have always used card readers.

---

### Post by b9k9kiwi on 2009-01-19
> **bocmaxima said:**
> 
...
"Error Connecting to Camera

Received Error "Unspecified Error" while connecting to camera"

...


Although Kodak cameras have a 'USB' connection the camera firmware does not comply with USB protocols.  Only Kodak software (and there is no Kodak Linux software) will talk with Kodak cameras.

I've 'been there, done that, got the teeshirt' and know from experience not to waste my life trying to communicate with a Kodak camera through USB with Linux.

---

### Post by bocmaxima on 2009-01-20
> **b9k9kiwi said:**
> Although Kodak cameras have a 'USB' connection the camera firmware does not comply with USB protocols.  Only Kodak software (and there is no Kodak Linux software) will talk with Kodak cameras.

I've 'been there, done that, got the teeshirt' and know from experience not to waste my life trying to communicate with a Kodak camera through USB with Linux.

So the card reader route is the way to go?

---

### Post by albinootje on 2009-01-20
> **bocmaxima said:**
> So the card reader route is the way to go?

Yes, sounds like it indeed.
Good luck!

---

### Post by wolfen69 on 2009-01-20
one last thing. i have a kodak camera and it works great with gthumb. i just do file>import photos. might be worth a try.

---

### Post by timcredible on 2009-01-20
maybe i missed it, but did you try changing the usb mode on the camera?  that almost always works.

---

### Post by cariboo on 2009-01-20
I have a Kodak camera, in earlier versions of Linux, I had to select PTP in whatever software I was using, digikam mostly, but since I started using Ubuntu, it is detected automagically and places an icon on the desktop and originally Fspot opened, but I changed that to manually download the pictures.

Jim

---

### Post by hyde0429 on 2010-02-12
... old thread... probably works with karmic

---

### Post by hyde0429 on 2010-02-12
Works in karmic.

---

### Post by Paul Crawford on 2010-02-16
No it is basically broken in Linux. It is not a problem of just the Kodak camera!

This is NOT a new problem, and it appears to be a basic issue with the USB system (similar problems with other photo programs). I found my Nikon D300s would not work, then it did, and now it wont again following kernel (or other?) updated.

See this bug post:

[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/191316](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/191316)

This has been a problem for a WHOLE YEAR and two revisions of Ubuntu :(

Will someone please take this problem seriously? Connecting a camera is one of the basic things that an average user expects to 'just work'.

---

### Post by RJARRRPCGP on 2010-02-16
> **bocmaxima said:**
> 

"Error Connecting to Camera

Received Error "Unspecified Error" while connecting to camera"


Reconnect the USB plug and try again. USB plugs are a pain, sometimes.

---

### Post by Paul Crawford on 2010-02-16
In my case, the machine will do this itself! Here is what happens in syslog now when I try to connect the camera to a Windows VM:

Feb 17 00:05:06 paul-ubuntu kernel: [  429.600115] usb 1-1: configuration #1 chosen from 1 choice
Feb 17 00:05:08 paul-ubuntu kernel: [  431.360521] usb 1-1: reset high speed USB device using ehci_hcd and address 41
Feb 17 00:05:08 paul-ubuntu kernel: [  431.440304] usb 1-1: USB disconnect, address 41
Feb 17 00:05:08 paul-ubuntu kernel: [  431.556091] usb 1-1: new high speed USB device using ehci_hcd and address 42
Feb 17 00:05:08 paul-ubuntu kernel: [  431.685970] usb 1-1: configuration #1 chosen from 1 choice
Feb 17 00:05:08 paul-ubuntu kernel: [  432.332037] usb 1-1: reset high speed USB device using ehci_hcd and address 42
Feb 17 00:05:09 paul-ubuntu kernel: [  432.405315] usb 1-1: USB disconnect, address 42
Feb 17 00:05:09 paul-ubuntu kernel: [  432.524053] usb 1-1: new high speed USB device using ehci_hcd and address 43
Feb 17 00:05:09 paul-ubuntu kernel: [  432.717020] usb 1-1: configuration #1 chosen from 1 choice
Feb 17 00:05:09 paul-ubuntu kernel: [  433.236040] usb 1-1: reset high speed USB device using ehci_hcd and address 43
Feb 17 00:05:09 paul-ubuntu kernel: [  433.306713] usb 1-1: USB disconnect, address 43

And so on, and on... It just flashes on-off and now I can't even use Windows XP on Ubuntu 9.10 to access this camera :(

I am not sure it is just the kernel, as booting to an earlier version did not fix it.

Anyone got any ideas?

---

### Post by Nick Brohman on 2010-02-17
G'day all,

I get the connection error when I'm running FSpot.

I just don't start FSpot before connecting the camera, but if I do have it running, I can use the Import button. Just close the error message.

I have 2 Canon Powershots and a Nikon Coolpix and last night I downloaded 770 photos from the Nikon using both methods as above.

I find the easiest and most painless method is to have FSpot closed.

There could also be a problem with your desktop theme - human, clear, etc. - there are some threads on this subject but I don't have the links to hand as this line is an afterthought as I was about to post.

I hope this helps.

---

### Post by woodmaster on 2010-02-17
>  No it is basically broken in Linux. It is not a problem of just the Kodak camera!

This is NOT a new problem, and it appears to be a basic issue with the USB system (similar problems with other photo programs). I found my Nikon D300s would not work, then it did, and now it wont again following kernel (or other?) updated.

See this bug post:

[[COLOR=#444444]https://bugs.launchpad.net/ubuntu/+s...ot/+bug/191316[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/191316")

This has been a problem for a WHOLE YEAR and two revisions of Ubuntu :sad:

Will someone please take this problem seriously? Connecting a camera is one of the basic things that an average user expects to 'just work'.

 
My wife's Canon DSLR and smaller Canon "just work"

---

### Post by no2498 on 2010-02-17
take the card out plug in the cam
put the card in did the computer see it

or try turning the cam on after its plugged in

i have a polaroid that comes up as a kodak
on 804 lts and 910 2 diff computers
i need to turn the cam on an set it to computer 
hope this helps

---

