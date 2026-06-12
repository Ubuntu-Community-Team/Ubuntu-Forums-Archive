---
title: "Audacity Wont Read &quot;Error while opening sound device.&quot;"
date: 2007-07-21
forum: Multimedia &amp; Video
---

### Post by Prosis on 2007-07-21
Hello

I can record on Audacity (I can see the nodules on the track line) but when I press Play I get this:

```
Error while opening sound device.  Please check the input device settings and the project sample rate.
```

And so I go see the sound device for Playback and all I got is:

ALSA: HDA Intel: Si3054 Modem (hw:0,6)
ALSA: modem
ALSA: phoneline

all three of which I doubt can read music.  

I've also tried chmoding /dev/dsp to 777 but still nothing

Help? :P

---

### Post by fredj on 2007-07-21
Start Audacity and go to Edit->Preferences->Audio I/O. Make sure that hw:0 under Alsa is select for both
record and playback. You won't have much luck trying to play audio through your modems sound device.

---

### Post by potpot on 2007-12-12
I can record while the music not playing but if I click playing background while i record it shows this error..... When I unclick it I can record again but the music doesn't play.... Please help.....

---

### Post by daXkat on 2007-12-12
The only way I managed it to work myself was selecting OSS for playback, and ALSA for recording, otherwise it crashes or gives that error.

-daX

---

### Post by kumoshk on 2008-04-24
I have a similar problem, only it gives me this error when I try to record (it won't let me record a whit).  Playback is fine.  I've tried using all the devices, with the same result.

Do I need to change the default sample rate?  Right now it's 44100 Hz with a 32-bit float default sample format.

Here's some other info from that screen:
Real-time: Fast Sinc Interpolation (Sample Rate Converter) | None (Dither)
High-quality: High-quality Sinc Interp... | Shaped

---

### Post by playmodrill on 2008-05-02
same problem here, plus Audacity doesn't let me choose an output driver (blank field)

---

### Post by olskar on 2008-05-06
I am suffering from he same problem..I guess it is related to pulseaudio?

---

### Post by Endolith on 2008-05-07
Bug: [https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/202791](https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/202791)

---

### Post by einfeldt on 2008-05-15
hi,

I was having this problem, and I solved, at least as to me.  I thought I would post it here, in case it helps someone else.  I describe the problem first, and then the solution:

I and a friend are both having problems using Audacity to edit music files.  In my case, I am trying to edit an .ogg vorbis file, and in his case, he is trying to edit a file that he recorded with Audacity.  He is a 69 year-old man, and I am trying to assist him over the phone, so it is kind of hard to get complete details from him, but, fortunately, I am having the same problem on my Gutsy install with Audacity 1.3.3-beta.  Here is the exact error message that we are getting:

Error while opening sound device.  Please check the output device settings and the project sample rate.

The solution:

On my system, the problem was solved simply by switching the sound device to ALSA default by doing this.  Open Audacity, the do Edit > Preferences > Audio I/O.  In the upper left hand corner of the window, you will see a section labelled, "Playback".  Click on the pull-down menu beside Devices and choose "ALSA default."  It's that simple, at least on my system, which is running Gutsy 32-bit with 4 GB of RAM on an AMD 3800 and a Realtek ALC883 or ALC889 sound device (can't be sure which, because my system is kinda new, so lshw might not be reporting it correctly, or so I am told).

---

### Post by outslider_pl on 2008-05-24
Hi! Im new here:)

I was having the same problem and on some forum (not this, but I don't remember, witch one) I found some help. Following this, I have installed 'aoss' package and now everything is fine:)

I hope it will help you, sorry for my english.

---

### Post by Tips on 2008-05-30
I fixed it by installing ***audiooss*** through Synaptic.

(Gutsy Gibbon)

---

### Post by barghest on 2008-05-31
> **Tips said:**
> I fixed it by installing ***audiooss*** through Synaptic. (Gutsy Gibbon)

Worked for me. Thank you.

---

### Post by Vasto on 2008-05-31
I installed both aoss and audiooss and audacity is still giving me only modem devices for playback (recording is fine).

---

### Post by MimeyNaomi on 2008-06-01
Same problem.  I have audiooss and aoss installed, and I get a nice long list of playback device options, including all those mentioned, none of which work.

---

### Post by Vasto on 2008-06-01
Some how mine was fixed with a reboot. Not the ideal solution though because now I don't know what was causing it to not work.

---

### Post by timsdeepsky on 2008-06-03
This is the only way i could get Audacity 1.3.4 beta to work in Ubuntu 8.04....
Keep in mind i am using my "oss" device,,and i did this in this order and it worked for me....

1= I right clicked my volume icon on my toolbar and chose open volume control,,
then i clicked "file",,and then chose my "oss mixer" device,,then i clicked "edit" and then clicked "preferences" and checked all boxes....

2= For a second time i right clicked my volume icon on my toolbar and chose "preferences",,then i selected my oss device,,and then highlighted "volume"....

3= I next went to "system",,then "preferences",,then clicked on "sound",,and on the "devices" tab i chose "oss-open sound system" on the first four choices,,and my oss mixer under the 
"default mixer tracks" header,,and then highlighted the "volume" line under that....

4= In terminal type "killall pulseaudio"....(this will have to be done everytime your computer is started because pulse audio was starting everytime in Ubuntu Studio)

5= Open Audacity and click the "edit" tab,,then "preferences",,and under "audio I/O" select your oss device....

Then open your mp3 and it should finally play and be editable....This is the only way i could edit or play mp3 files in Audacity in Ubuntu 8.04....

Hope this helps somebody....

[http://www.deepspaceimages.net/]("http://www.deepspaceimages.net/")

---

