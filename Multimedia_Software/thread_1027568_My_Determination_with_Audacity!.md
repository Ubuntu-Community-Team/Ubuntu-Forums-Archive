---
title: "My Determination with Audacity!"
date: 2009-01-01
forum: Multimedia Software
---

### Post by listerdl on 2009-01-01
Hi

I have spent hours and hours trying to configure audacity with no joy.

I cant seem to find a better alternative and I used to really like audacity when I was with Windows....so, now, I will endeavour to fix this issue.

I am running Ubunutu Hardy Heron and my problem is that when I try to record I get nothing. The timeline just moves as normal but with no evident recording of sound......

Edit>Preference>Audio 1/0 
I have two options for Recording ALSA: HDA Intel: STAC92xx Analog (hw:0,0) OR I can select OSS: /dev/dsp

Tried both and no joy.....

I played a little with the Project Rate bottom left of the screen and no joy either.

When I open the Volume settings I have 5 devices to choose from:

HDA Intel (Alsa Mixer)
SigmaTel STAC9200 (OSS Mixer)
Playback ALSA PCM Onfront:0 (Stac92xx Analog)
Capture: Monitor Source of ALSA PCM onfront:0 (Stac92xx)
Capture: ALSA PCM onfront:0 (Stac92xx)

**Any help with this will be VERY appreciated.**

Thanks!!!!!!!

---

### Post by namdung on 2009-01-01
Firstly, ensure that ur hardware microphone is functioning properly.

In *System-->Preferences-->Volume Control*, select **Capture** in *Edit-->Preferences*. Ensure the *Capture* is set to maximum in the *Recording* tab.

In *System-->Preferences-->Sound*, play around *Sound Capture*.

In *Audacity*, ensure the recorder volume slider is set to max.

---

### Post by listerdl on 2009-01-01
Hi Namdung thanks for your help...

Can you expand on what you mean by "In System-->Preferences-->Sound, play around Sound Capture" What did you mean by play around Sound Capture?

Thanks again!

---

### Post by namdung on 2009-01-01
> **listerdl said:**
> Hi Namdung thanks for your help...

Can you expand on what you mean by "In System-->Preferences-->Sound, play around Sound Capture" What did you mean by play around Sound Capture?

Thanks again!

In *System-->Preferences-->Sound--->Devices-->Audio-->Conferencing-->Sound Capture*, select the different options. I have OSS selected for this field even though other options selected for other settings are ALSA. This seems to work for me for to record in Audacity.

Have u tried the other options suggested earlier?

---

### Post by Stochastic on 2009-01-01
> **listerdl said:**
> Hi

I have spent hours and hours trying to configure audacity with no joy.

I cant seem to find a better alternative...

I like to record with Rezound, it's always been as stable as a rock for me while Audacity flakes out after every minor update.  It is only a single track wave editor, if you need multi-track stuff, you can then import the recorded files into Audacity, or use Ardour (though that's a big professional beast).  You might also want to give Jokosher (not the repo version, that's really old) a try.

---

### Post by listerdl on 2009-01-02
Thanks for your help...

I tried both those programs. Rasound closes when I try and create a file to record and jokosher is asking me to select an instrument! I am sure if I spend a lot more time on those two programs I will figure them out.

However, going back to audacity, does this help to explain my problem?

henry@DELL-laptop:~$ asoundconf
Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card PARAMETER
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio
asoundconf set-oss PARAMETER
asoundconf unset-oss


I would really love to solve this audacity drama!!

Thanks for all suggestions...

---

### Post by listerdl on 2009-01-02
Still no joy with everything you mentioned namdung....is there anything left to try or are the options really running out now?

---

### Post by namdung on 2009-01-03
Check if anything else has the sound device file open.
```
less /proc/asound/card0/pcm0p/info
```
and look at subdevices_avail (at the end of the file)
If avail is 0, then something already has your sound card open.

Which version of Audcity are u using? The latest release is 1.3.6, which may not be available in Ubuntu repository. Remove, download and install and try again.
[http://audacity.sourceforge.net/download/](http://audacity.sourceforge.net/download/)

Finally, try the Audacity forums.
[http://audacityteam.org/forum/](http://audacityteam.org/forum/)

---

### Post by listerdl on 2009-01-10
Thanks Namdung:

I did what you said and now have the following code replied:

card: 0
device: 0
subdevice: 0
stream: PLAYBACK
id: STAC92xx Analog
name: STAC92xx Analog
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 0

So yes that since subdevices_avail: 0 then, I guess then something has my sound card open....can this be fixed? Odd thing is that the sound works pefectly for everything else.....all audio plays 100%.

Ill try your suggestion for the fresh download...

So, do you reckon the sound card can be altered so whatever it is that is keeping it used is closed? Thanks!

---

### Post by namdung on 2009-01-10
Try this for multiple sound solution:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by gizmobay on 2009-01-10
Which version of audacity do you have? I had version 1.3.4 and I couldn't get it to work due to a bug. I have media ubuntu installed so I'm not sure which repo 1.3.4 came from. I ended up going to getdeb.net and installed 1.3.6 and everything worked.

---

### Post by listerdl on 2009-01-15
Hi thanks for reply. Yeah the audacity issue is a big shame. I love everything about Ubuntu and am trying to learn more, but I just cant seem to get audcaty to work, and, I hate to say this, but with Windows it seemed so much easier.

However. I shall continue with ubuntu for ever now.

My audatity version is 1.3.5 Beta Unicode....maybe that is the problem.

Thanks for your tip. Whem i have a chance i will try your version from the site you mention.

Thanks

---

### Post by ufugu on 2009-01-16
Every time I've had audio issues it seems to have had something to do with Pulse.

This is what worked for me to get a USB mic recording:

1) Add "killall pulseaudio" command to your Sessions to disable Pulse Audio. Log out and log back in, your new session will have Pulse disabled and revert to ALSA by default. (For me this clears up a lot of sound issues in general.)  

2) Open Synaptic, install the following:
audiooss
aoss

It is my understanding from the Audacity FAQ that Audacity uses OSS for sound, and these make ALSA emulate OSS in some way that makes Audacity happy.

3) In Audacity, go to "Edit > Preferences > Audio I/O" and select "ALSA : Default" for playback and your sound input for recording.

Presto, the cursor moves AND records audio.

I am really confused by audio on Linux and why the default (Pulse) causes so many new problems.  This was just what worked for me to get Audacity working and hope it helps your situation too, sounds similar.

---

