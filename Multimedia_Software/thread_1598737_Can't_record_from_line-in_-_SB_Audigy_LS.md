---
title: "Can't record from line-in - SB Audigy LS"
date: 2010-10-16
forum: Multimedia Software
---

### Post by Schrute Farms on 2010-10-16
I've looked up and down the web for the past hour, & I can't find anything.  Maybe someone here can help.

I am trying to record some vinyl using Audacity.  I'm using Lucid 10.04 with a Soundblaster Audigy LS card.  
Regular sound playback works.  Recording from the mic works.  I just can't get anything to record from the line in.  
Everything is hooked up correctly.  I can hear the music through the computer speakers.   I booted into Windows and was able to record with Audacity just fine there.  I can't get Audacity (or sound recorder) to show and record any input in Ubuntu.  I've messed with every setting I can find in Audacity.  I've also messed around with the settings in the GNOME ALSA mixer and sound properties.  The most I can get to record is some static in the left channel.

Anybody got any ideas before I give up & bite the bullet & use Windows?

---

### Post by Schrute Farms on 2010-10-17
Bump for the day crowd before it gets lost.

I'm beginning to think it's something goofy with Audacity.  I imported an MP3, and I couldn't hear any sound from the program.  I went into the preferences and changed the output from default to the CA0106 0,0 setting.  It started playing normally then.  It doesn't matter the setting on the input, nothing works.  I exited the program and started it a bit later.  It had no sound, and the CA0106 0,0 setting was not there, only the 0,3 and that didn't work.

Anyway, if anyone can help, I'd appreciate it.  If not, at least I can use Winblows.

Situations like this is exactly why I can't totally lose Windows.

---

### Post by Jonie on 2010-10-17
I've been using Ubuntu with this card for a couple of years and had no major issues. The only problems came up when Pulseaudio was introduced, like no output due to a process locking the pulseaudio server or crackling sound until a reboot. I think it's time for you to say goodbye to pulseaudio and get used to live with plain alsa (you aren't going to lose anything really). The procedure is described here:

[http://ptspts.blogspot.com/2009/09/how-to-get-rid-of-pulseaudio-on-debian.html]("http://ptspts.blogspot.com/2009/09/how-to-get-rid-of-pulseaudio-on-debian.html")

If you're not that brave-hearted it's also quite useful to have alsamixer installed, a command line utily that controls the alsa device directly.

To get rid of Windows... yes, you can ;)

---

### Post by Schrute Farms on 2010-10-17
Thanx for the reply.
I'm recording in Windows now, so when I'm through, I'll go back into Ubuntu and try what the link said.  I never use the volume control in the notification bar anyway, so maybe losing Pulse will work.

---

### Post by Schrute Farms on 2010-10-17
Well, thanks for the tip Jonie, but uninstalling pulseaudio did not work.  Alsamixer didn't help either.
:confused:
It's just frustrating, because I can hear the sound through the dang speakers, it just won't capture.

---

### Post by Jonie on 2010-10-18
Well, remember that this card has no analog mixer, i.e. it switches inputs rather than mixes them. That "mixer" thing is just saved states for the input lines. If you start alsamixer and press F4 to get into capture states you'll see three rightmost switches that correspond to the cryptic combinations in pulseaudio volume control applet (navigate with left and right arrows). You can switch them using up and down arrows. Be sure to select Analog Source = Line in, Digital Source = i2s in (i2s out is capture what you hear, just in case you're wondering) and Shared MIc = Line in (this card shares the blue jack for both mic and line in). Also check the Line in level here. Pressing F3 for playback control shows (again far to the right) the capture slider that enables you to hear what you capture.

Hope it was helpful. If you set up the card as described above and still have no capture it's time to consider the cabling.

---

### Post by Schrute Farms on 2010-10-18
Well, thanks for all of your help Jonie.  Unfortunately nothing worked.  I'm sure it's not my cabling, because I can hear the sound in Ubuntu, and I can record just fine in Windows.  I just can't record the music I hear playing through the line in through Ubuntu.

Googling around, I think I found the answer in a bug page on launchpad.net.  It says "CA0106
Details [PCI] Digital/Analog input does not work yet. Needs more development work."

So, it looks like a driver issue.

I'm going to mark this solved for now, but if you or anyone has recorded through the line in (NOT mic) on this card, I'd like to hear more.

Thanx again.

---

### Post by Jonie on 2010-10-18
Yes, I have captured audio thru Line in, Mic and Aux on CA0106, everything works fine.

The problem is that those switches which select recording source are not application conttrolled. The "mixer" is just virtual, you can mute or unmute a source but doing this does not select the capture source really. 

The only way to set up the capture source is to control the alsa driver directly - either by typing "alsamixer" in terminal or by installing that oldschool applet provided by Dave Lentz (dtl131). 

Similar behavior can be observed on Windows, activating "Digital Audio interface" in Vista/7 driver preferences puts line in into digital (SPDIF) mode and no analog capture is possible, even though Microphone, Aux or Line in is selected, it will not work.

My settings to capture from line in

```
jonie@jonie-desktop:~$ alsamixer

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.22 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: CA0106                                         F1:  Help               &#9474;
&#9474; Chip: CA0106                                         F2:  System information &#9474;
&#9474; View: F3: Playback  F4:[Capture] F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Shared Mic/Line in [Line in]                   Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;                                     &#9474;
&#9474;    &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;  &#9474;                                     &#9474;
&#9474;    &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;  &#9474;                                     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;       &#9492;&#9472;&#9472;&#9496;       &#9492;&#9472;&#9472;&#9496;       &#9492;&#9472;&#9472;&#9496;     Line in     i2s in    Line in   &#9474;
&#9474;   81<>81    100<>100     0<>0      80<>80                                    &#9474;
&#9474;  Line in      Mic       Phone       Aux     Analog Sou Digital So<Shared Mic>&#9474;
&#9474;                                                                              &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```

Right now when I'm typing these words music is playing thru line in jack. There is a catch however: when I start Sound Recorder it resets all capture levels to zero, so you got to have alsamixer open and move the Line in slider back all the way up. On the other hand: selecting the source in Sound Recorder does not really select the source, just as i wrote above.

---

### Post by Schrute Farms on 2010-10-18
Ok.  Here are my settings.  I notice they look a little different than yours.  What flavor of Ubuntu are you using?

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.22 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: CA0106                                         F1:  Help               &#9474;
&#9474; Chip: CA0106                                         F2:  System information &#9474;
&#9474; View: F3: Playback  F4:[Capture] F5: All             F6:  Select sound card  &#9474;
&#9474; Item: AC97 Line [dB gain: 12.00, 12.00]              Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;      &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                                &#9474;
&#9474;     L&#9492;&#9472;&#9472;&#9496;R       &#9492;&#9472;&#9472;&#9496;       L&#9492;&#9472;&#9472;&#9496;R       &#9492;&#9472;&#9472;&#9496;       Line in    IEC958 in     &#9474;
&#9474;    CAPTURE     -------     CAPTURE     -------                               &#9474;
&#9474;    100<>100    100<>100    100<>100       0                                  &#9474;
&#9474;     Capture    AC97 Aux  < AC97 Line > AC97 Mic   Analog Sour Digital Sou    &#9474;
&#9474;                                                                              &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```Right now with these settings I can hear the music that is coming through the line in.
If I deselect either capture setting, then the sound disappears.  I've checked the sound levels after starting Audacity & sound recorder.  They stay up on mine.  I've tried just about every setting I can think of on both alsamixer and in the Audacity preferences...no sound records.

:confused:

---

### Post by Jonie on 2010-10-19
There are some models of Audigy LS that sport AC97. If this is the case you have to switch Digital Source from "IEC958 in" to AC97. You may also try "i2s in" but it looks like in this aspect your card is different than mine. Nevertheless, IEC958 in is wrong, it puts "Line in" in SPDIF mode so that you could capture digital stream from ex. DAT deck. If the Digital Source is IEC958 in no analog recording is possible.

Available options for Digital Source (misnomer, should be Input Source):

i2s in - analog input (capture feedback does not affect recording)
AC97 - analog mixer on cards that have it, use instead of i2s in
i2s out - signal that gets into the speakers aka capture what your hear (capture feedback affects recording, you can play some music in the background and your Skype party will hear it)
IE958 in/out - like i2s in/out, but the card must be hooked digitally
SRC out - invalid for Audigy LS which has no hardware Sample Rate Converter

---

### Post by Schrute Farms on 2010-10-19
WHOOHOOO!!!!!   

Jonie, you're the best.

I never really looked at the digital source setting.  I figured since I was recording an analog source, the digital setting didn't matter.  I did try to set my settings like yours, obviously I didn't.

is2 in works.

What's really sad, is that you flat out told me in your second post to use is2 on the digital input.  Don't know how I missed that one.  Again, probably because I was fixated on the analog settings.  I'm usually better at following directions.

Thank you, thank you, thank you!  I was beginning to think my computer just hated me.

Now back to getting some old fashioned vinyl into the 21st century.   :guitar:

---

### Post by Jonie on 2010-10-19
I'm very glad too :)

What was a little bit misguiding is the subtle difference AC97 makes: without it you can't hear the signal on input unless you select proper input (digital) source, that's the way my card works.

For best results do the capturing at 48k, the quality of the default software SRC is rather poor, you can convert the audio later in a more precise way.

Nice capturing!

:guitar:

---

