---
title: "RealPlayer 10 no sound video OK, other multimedia apps work OK"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by coleus on 2006-06-09
I just installed a fresh Drapper Ubuntu 6.06 on my IBM T30 laptop and after installing Realplayer 10 from [www.real.com](www.real.com) I noticed all .rm and .ram streams have no sound (video is OK). My sound card is an on-board Intel 82801CA/CAM AC97 audio controller as per my lspci and it works OK with other multimedia applications (ex. Totem and Xine with other media types - DVD, XVID/DIVX, Mpg, WMV work perfectly). However Real Player when I'm trying to play an mp3 it gives me "can't open audio device - another application might be using it" error and if i try a mpg videoclip it gives me "component missing - the player does not have the capabilities to play back this content". I tried configuring Realplayer 10 but the options are very slim, there doesn't seem to be a real "hardware configuration" it merely points to driver options...I even installed Real 10 as a root and every steps described on Real's website match, I have no clue what's going on...

Anyone had this problem and solved it, any help would be appreciated ?

Coleus

---

### Post by beko on 2006-06-12
The same problem here, I don't know why ,I was going to open  a new thread to ask for help:confused: :confused:

---

### Post by beko on 2006-06-12
I just found that you need to kill esd process in the background & everything will be fine

---

### Post by fordp on 2006-06-12
I have this problem.

How do you kill esd ?

Where is the thread with the info ??

Thanks

---

### Post by taurus on 2006-06-12
At the prompt, Applications -> Accessories -> Terminal, type
```

ps -A

```
Now, see what process ID or number (first column) esd.  Assuming for a second it's 1234, then from a terminal, type
```

sudo kill -9 1234

```

---

### Post by Bloch on 2006-06-14
This hack also worked for me. I open the system monitor and kill the esd process. Then realplayer will work with sound.

Is it a bug in realplayer? Is there a more permanant solution?

---

### Post by beko on 2006-06-14
I don't think it's in realplayer itself , I think it's related to Alsa & esd because sometimes this problem happend to Macromedia Flash Player also on sites like YOUTUBE  or Video Google

---

### Post by ariel on 2006-06-18
I have the same problem but I don't have ESD running. Any other suggestion?

In my case I have multiple sound cards and it looks like the default one is wrongly selected (in System > Preferences > Sound) and if I try to change it, my change doesn't stick.

---

### Post by rjl on 2006-06-21
It worked for me also, but everytime I turn the laptop off and on, the sound is lost again.  

Is there a fix that will "stay fixed"?

Bob

---

### Post by robtotheb on 2006-06-21
I hate REALPLAYER 10!!!!  I have sound thanks to this thread but now the video freezes every 5 seconds and the whole program becomes unresponsive!](*,)

---

### Post by flurdy on 2006-06-26
Same problem here.

Solved with killing esd.

However I dont want to do that every time.

Is installing alsa-oss a permanent solution?

Ps there apare to be new version available of realplayer and w32codecs from merilat, however didnt fix anything obvious.

---

### Post by igor4u on 2006-07-07
The same problem with sound. ](*,)

---

### Post by cs378 on 2006-07-17
I dont have est to kill too

If you have alsa sound driver installed
Try to use the command:
```
aoss realplay
```

It worked for me. The aoss command is a alsa OSS, which lets you have multiple sound output from different applications.

---

### Post by misha680 on 2006-07-19
Here is what I did.

```
sudo apt-get install alsa-oss
sudo gedit /usr/bin/realplay
```

Now, find the line that says

```
REALPLAYBIN=$HELIX_LIBS/realplay.bin
```

and replace it with

```
REALPLAYBIN="/usr/bin/aoss $HELIX_LIBS/realplay.bin"
```

Save the file, and realplayer should launch with no problems from now on.

Hope this helps. 

Misha

---

### Post by shoofy on 2006-07-23
Is there a way to apply this hack to the realplayer plugin for firefox?

---

### Post by pulver on 2006-08-19
> **misha680 said:**
> Here is what I did.

```
sudo apt-get install alsa-oss
sudo gedit /usr/bin/realplay
```

Now, find the line that says

```
REALPLAYBIN=$HELIX_LIBS/realplay.bin
```

and replace it with

```
REALPLAYBIN="/usr/bin/aoss $HELIX_LIBS/realplay.bin"
```

Save the file, and realplayer should launch with no problems from now on.

Hope this helps. 

Misha

You're the man, thanks.

---

### Post by Ambimom on 2006-08-19
> In my case I have multiple sound cards and it looks like the default one is wrongly selected (in System > Preferences > Sound) and if I try to change it, my change doesn't stick.


Did you ever find a solution to your sound card selection? I have exactly the same problem.  I've filed a bug report. >  [Bug 56482] Re: System Sound Card Selection at Bootup Incorrect It's driving me nuts! When it's usb sound card, I can't play flash or audacity....When it's Ich5, everything works as it should.  I just can't keep it on ich5.

---

### Post by madscientist on 2006-08-21
I had this same problem (Ubuntu 6.06.1 + realplayer 10 installed from the PLF repo): video was fine but no sound.

I installed alsa-oss and ran "aoss realplay" and it worked great... sort of.  Whenever RealPlayer starts a new clip, somehow my audio is magically muted!  If I click the audio applet on my toolbar and uncheck the mute option then I can hear the RealPlayer clip just fine... but as soon as another one starts I have to un-mute my audio again.

Does anyone have any idea (a) why this happens and/or (b) what I can do about it?

Cheers!

---

### Post by idn on 2006-08-23
Thanks misha680 this worked fine - it now works thanks!

---

### Post by mdurham on 2006-08-24
I have a similar problem. I use Realplayer in Firefox to listen to radio progs and I find after booting I have to log-out and log back in, then the sound works ok untill the next reboot.

---

### Post by beow on 2006-08-31
> **pulver said:**
> You're the man, thanks.

Agree... :D

---

### Post by vozdemirler on 2007-06-10
System->Sound preferences second tab "Sounds" has a check box for disabling ESD.  I unchecked it real player sound started immediately.
:popcorn:

> **rjl said:**
> It worked for me also, but everytime I turn the laptop off and on, the sound is lost again.  

Is there a fix that will "stay fixed"?

Bob

---

### Post by tribble43 on 2007-07-01
Well I'm more a Debian user than Ubuntu, but I was having the same problem and found an easier solution, so I thought I'd share.  

I use enlightenment instead of kde/gnome, and doing an "apt-get install oss-compat" seems to have fixed it.  I've got Real Player working now without even having alsa-oss installed, so everything seems to be getting along :)

---

### Post by acbo on 2007-08-26
Thanks Misha680 !  That worked perfectly for me  :) .

---

### Post by ZootNerper on 2007-10-08
Hi,

I have the same problem and found that killing "esd" was not enough. Looking at the list of processes again I noticed one call "xxxvlc" (sorry I can't recall the "xxx"). VLC was not running, but had been running (as had Movie Player). I guess this process was left over when I exited.

I haven't tried that script yet - it's late and I'm off to bed. A job for tomorrow.

Thanks for the posted help.

-- Zoot

---

