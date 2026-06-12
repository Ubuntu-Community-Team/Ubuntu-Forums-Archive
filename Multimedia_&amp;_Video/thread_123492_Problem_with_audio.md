---
title: "Problem with audio"
date: 2006-01-30
forum: Multimedia &amp; Video
---

### Post by MJoshi on 2006-01-30
Hi,

I have just installed the latest version of Ubuntu but when I tried to play an audio C.D by double clicking the Audio Disk icon on the desktop, I receive the following error message:

Sound Juicer

The currently selected profile is not available on your installation

(The same error message appears when the colume control icon is clicked)?


If I try using CD Player, the following error message appears:

Registry is not present or is corrupted.  Please update it by running gst-register


The sound card is an on-board VIA chipset.

---

### Post by FarEast on 2006-01-30
Hi,
Just in case, make sure if your sound card has been configured
properly.
Execute below in a console window:
```
$ cat /proc/asound/cards
```

---

### Post by MJoshi on 2006-02-06
O.K - The hard-drive I installed Ubuntu on originally died - Apparently there was a faulty controller chip from Cirrus Logic on the Fujitsu MPG series hard-drives which Fujitsu announced in a press release.  They have settled a class action suit, and it has been accepted by the court:

[http://hddclassactionsettlement.com/](http://hddclassactionsettlement.com/)

Here is a forum thread detailing other users problems with these drives - all seem to be related to the same problem:

[http://217.115.198.3/content/topic/2190/?o=0](http://217.115.198.3/content/topic/2190/?o=0)

I spoke to Fujitsu customer services - firstly, they denied there ever being a problem!  I therefore, forwarded a link to them on the Fujitsu website giving a press release of the problem.

However, they were not very helpful and said they could not do anything.  All I can say is if you have one of these series hard-drives, backup your data immediately and throw it away - you never know when the problem may occur.  Sometimes the problem is progressive and some people have noticed a slow down in access - this is probably due to the overheating issue with the chip.

I would strongly recommend anyone never to purchase Fujitsu hard-drives as their customer service is terrible.


Anyway, rant over, back to the original problem:

I have installed Ubuntu on another hard-drive but I still get the same error message.

I entered the command -  cat /proc/asound/cards and it does give information about the internal VIA sound card?

---

### Post by FarEast on 2006-02-07
> I would strongly recommend anyone never to purchase Fujitsu
> hard-drives as their customer service is terrible.

I should say "I am sorry." to you, for the head office of the company
is in *my* country(I have nothing to do with it, though;) ).  
"Fuji" is the name of a mountain that is highest in Japan.

> Registry is not present or is corrupted. Please update it by running
> gst-register

I am not sure what causes the problem.  Anyway how about doing
what the error massage says?

---

### Post by MJoshi on 2006-02-09
I have installed KDE and now a different error message appears when I try to play a C.D:

Totem:
Failed to create a GStreamer play Object.
Please check your GStreamer Installation?

---

### Post by FarEast on 2006-02-09
Open 'Control Center' and choose the item 'sound'.
Can you hear any system sound?

I think it important to know, at first, if your sound chip is properly configured.

---

### Post by MJoshi on 2006-02-21
The 'test sound' option works in the Sound Settings and I can hear system sounds however, I just cannot play C.D's?

The same error message appears about Totem player?

---

### Post by MJoshi on 2006-02-22
One of the error messages says to run '*gst-register*' however, when I try to run the command in a terminal window, it says that the command cannot be found?

---

### Post by Heretushi on 2006-02-22
I have the same exact problem.

The reason you can't use this command is because it's not the good command! ;)

In the console, try to type "gst" then hitting the Tab key 2-3 times. It should list all the available commands that start with "gst". There you will see that the only gst-register command is (probably) gst-register-0.8.

**Even if I run this command, it does not help me. I tried to register 2-3 times, reboot, etc. Not working.**

Found the solution. You know what? Trying to execute system command in normal user won't cut it...

Just :

sudo gst-register-0.8

And it will register fine and dandy. Then Totem and eveything else will work! ;)

---

### Post by MJoshi on 2006-03-08
I ran that command and now I am able to view the volume/mixer settings however, I still cannot playback any audio from a C.D or from a WAV file?

I also tried different audio applications within KDE but none of them will play audio?

---

### Post by krazykat on 2006-03-09
I'm having the same issue - I get system sounds but can't use audio apps. I can run sudo gst-register-0.8 in the terminal and it seems to work, but changes nothing. Tried executing the command and rebooting, still no change.

---

### Post by MJoshi on 2006-03-11
krazykat,

Are you using on-board sound with a VIA chipset motherboard by any chance?

---

### Post by MJoshi on 2006-03-16
O.K, I have given up on being able to get the on-board VIA sound to work (At least on this version of Ubuntu anyway)!

I have just acquired and installed a Sound Blaster Live! 24Bit card but i'm not sure how to install it.

I assumed that it would be automatically recognised like Windows does?

---

### Post by FarEast on 2006-03-27
Hi MJoshi,

According to the web of ALSA, your card is driven by 'snd-ca0106'.
[http://www.alsa-project.org/alsa-doc/index.php?vendor=.%23vendor-Creative_Labs.1.1.1.1#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=.%23vendor-Creative_Labs.1.1.1.1#matrix)

I do not think that it needs any setting made by hand.  But I remember that someone was having trouble with 'Sound Blaster Live! 24Bit'...

BTW
I have been absent from the forums because of removal;).  I hope you can enjoy audio on Linux!

---

