---
title: "How to record music streams coming from Flash"
date: 2011-04-25
forum: Multimedia Software
---

### Post by Montfinal on 2011-04-25
Hi,

I would like to record music streams on my computer, coming from the Firefox FLASH plugin,  with audacity or something else.

In ancient times I had a soundcard that allowed to enable loopback by sw, but my current soundcard (realtec ALC888) doesn't support it. 

I am looking for a sw based solution to record the sound (not a hw loopback cable). I need  a GUI. 

I tried JACK, but this is horribly complicated, Audacity seems to support it, but does the FLASH player? Anyhow, I never got any sound stream rerouted to audacity through JACK.

Isn't there a simple solution that allows to tap the digital audio stream at the output of the Flash player and write it to a file ??

Thanks in advance for any ideas you might be able to share ...

Cheers 

Alex

---

### Post by dniMretsaM on 2011-04-25
Maybe I'm not understanding you correctly but can't you just use Audacity to record whatever is being played through the sound card? I do that all the time to record radio.

---

### Post by collisionystm on 2011-04-25
> **Montfinal said:**
> Hi,

I would like to record music streams on my computer, coming from the Firefox FLASH plugin,  with audacity or something else.

In ancient times I had a soundcard that allowed to enable loopback by sw, but my current soundcard (realtec ALC888) doesn't support it. 

I am looking for a sw based solution to record the sound (not a hw loopback cable). I need  a GUI. 

I tried JACK, but this is horribly complicated, Audacity seems to support it, but does the FLASH player? Anyhow, I never got any sound stream rerouted to audacity through JACK.

Isn't there a simple solution that allows to tap the digital audio stream at the output of the Flash player and write it to a file ??

Thanks in advance for any ideas you might be able to share ...

Cheers 

Alex

If your trying to do what I think you are, just use youtube to mp3

Free websites all over google.

---

### Post by Montfinal on 2011-04-26
@collisionystm
 
Thanks, but it is not youtube I'm interested in. There are other sites with crypted FLV files, no way to download. You can just listen to the misuc - nothing more. Here I would need to "rip" the audio stream.
 
@dniMretsaM
 
It doesn't seem to be that simple. In audacity I can select as input only the mic and line in of my soundcard. I would need a hw loopback cable. This is what I am seeking to avoid.
But maybe you are simply smarter with your ALSA, PULSE, etc configuration. Could you let me know what input you have selected in audacity when recording ?
 
Thanks
 
Alex

---

### Post by dniMretsaM on 2011-04-26
I select Mix:0 (see screen shot). Make sure you have the correct device settings. View->Toolbars->check Device Toolbar. Change the settings around till you get the mix option.

---

### Post by beew on 2011-04-26
> **Montfinal said:**
> @collisionystm
 
Thanks, but it is not youtube I'm interested in. There are other sites with crypted FLV files, no way to download. You can just listen to the misuc - nothing more. Here I would need to "rip" the audio stream.
 

 
Alex

You can use outrec to record the sound as it plays.
[http://outrec.sourceforge.net/](http://outrec.sourceforge.net/)

But there is a thread that says it has stopped working [http://ubuntuforums.org/showthread.php?t=1724688](http://ubuntuforums.org/showthread.php?t=1724688)

I used it less than 2 weeks ago and it worked, when I go home I will try again and see if anything has gone wrong.

---

### Post by Montfinal on 2011-04-26
Ha ! 

there's my problem. I don't have all these options and in particular I don't have the one that says "mix". 
I have tried to install zillions of mixers, plugins, sound servers, but  don't get it working. Starts frustrating me !

[IMG]http://img814.imageshack.us/i/screenshotfsz.png/[/IMG]
[]("http://img801.imageshack.us/i/audacityc.png/")[IMG]http://img801.imageshack.us/img801/9582/audacityc.png[/IMG]


Cheers

Alex

PS: BTW once I start Jack, all sound playback stops.

---

### Post by dniMretsaM on 2011-04-26
Select something other than ALSA: Default. There is no mixer option when that is selected on my computer and some don't have mix either. Just FYI, I'm having a horrible time getting stuff to record right now. It skips so much in the recording even when it doesn't when it's streaming and it sometimes just won't record right. So you may be better off finding a different program to record with (which I have been trying to do for like the past hour, so if you find one let me know).

---

### Post by Montfinal on 2011-04-26
Yeah what a mess ! 

I just tried outrec, as proposed by beew (thank you), and at a first glance it works. It is not very handy to use (doesn't ask for filename when saving for instance), but basically it does exactly what I was looking for.

I will check more in detaill whether it works really flawlessly ...

Cheers
Alex

PS: I tried all combinations in audacity, but I never get "mix" ...

---

### Post by lidex on 2011-04-27
Or this:
[http://ubuntuforums.org/showthread.php?t=1005196](http://ubuntuforums.org/showthread.php?t=1005196)

---

