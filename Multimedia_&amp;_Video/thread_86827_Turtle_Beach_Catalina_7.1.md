---
title: "Turtle Beach Catalina 7.1"
date: 2005-11-06
forum: Multimedia &amp; Video
---

### Post by souled on 2005-11-06
Does anyone have experience with this card? I've been looking at it for awhile and it's on sale for $40. Right now I have onboard sound, and I was wondering if anyone knows if this card will work with Ubuntu. I don't want to buy it if it won't work. The sale ends today so please help! Thanks

---

### Post by souled on 2005-11-06
Ok... I couldn't wait and I bought it. I can play sound through analog, but my SPDIF does not work. What do I do to make it work?

In System --> Perferences --> Sound, the sound card is detected as Chaintech AV-710. I'm guessing this isn't right...

---

### Post by posterberg on 2007-02-05
> **souled said:**
> Ok... I couldn't wait and I bought it. I can play sound through analog, but my SPDIF does not work. What do I do to make it work?

In System --> Perferences --> Sound, the sound card is detected as Chaintech AV-710. I'm guessing this isn't right...

I have the same card, had it working with SPDIF in Gentoo but have switched to Ubuntu now and I can't seem to find the correct setting for it to produce SPIF output.

Did you solve this problem?

Thank you!

---

### Post by ethridgt on 2007-02-21
I'm also trying to get this working.  Anybody know how to enable spdif output with this card?

---

### Post by posterberg on 2007-03-12
I actually got some sound from it today. I am far from satisfied but it did at least produce a sound digitally.

System->Preferences->Sound->(Sound events, Music/Movies, Conference)
(Translated to english from swedish, sorry if the aren't 100%)
Set those to IEC1724 IEC958 and make sure the IEC958 isn't muted in the alsamixer.

Press the "Test" button and you will a get a tone and your amp will say that it is recieving it digitally.

So far so good, now I want it working in real applications.

Does anyone know how the "Test" button generates it's sounds so I can tell mplayer to do the same trick?

have tried all kinds of things in mplayer with -ao alsa:device=hw=0,x and nothing works....

Will keep you posted if I get any further

---

### Post by posterberg on 2007-03-12
I'll be damned... Rythmbox is actually playing an ABBA .flac file now and doing it digitally (using the just mentioned settings)... =)

But still, I want this with command line version of mplayer...

---

### Post by posterberg on 2007-03-12
mplayer -ao alsa:device=plughw=0.1

works like a charm!

Hope this helps you as well!

---

### Post by posterberg on 2007-05-02
Found another thing today. If you create a asoundrc file like the one below you will get any program to work that output it sound to ALSA:default.

Quite nice since you won't have to reconfigure every single program that uses sound... =)

Goes in /etc/asound.conf
pcm.!default {
  type plug
  slave.pcm {
  type hw
  card 0
  device 1
}
}

---

### Post by DealerMan on 2007-05-03
Thank God, you might actually have a solution to my sound problems as well.  Please, please post your asound.rc (asoundrc?) file and exact location.  Do you also have an asound.state file somewhere?  All I want is for my headphones to work with the videos & music I listen to, I don't care about system sounds.

Also, for what it's worth, I'm running the Chaintech AV-710 card, which shares the VIA envy24 chipset with your TB Catalina, that's why it's being recognized as such.

Thanks very much for you help.

Edit:  One more thing, what are your Alsamixer settings?  I've tried so many.  I do change them running alsamixer from terminal.

---

### Post by posterberg on 2007-05-06
Glad to be able to help.

Just read all of my previous posts. I have implemented all the settings in them and am not sure what mightbe needed or not. At least everything works fine now.

asoundrc is called asound.conf when you have it in /etc/
It's called .asoundrc if you have it in your home direcroty. I wanted my changes to be system wide for all users that is why i put it in /etc/

The three important settings in alsamixer are:
IEC958 = PCM Out
IEC958 0 = Not muted!!
IEC958 1 = PCM Out

Nothing more should need any changes here.
Note that all analog audio will disapear when you unmute IEC958 0. So it is either digital out or analog out. I think that sucks but I haven't found any way to change that.

lspci in my computer says "02:0b.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)"

Hope you get the things rocking!

---

### Post by rggavubt on 2007-07-24
> **posterberg said:**
> Glad to be able to help.

Just read all of my previous posts. I have implemented all the settings in them and am not sure what mightbe needed or not. At least everything works fine now.

asoundrc is called asound.conf when you have it in /etc/
It's called .asoundrc if you have it in your home direcroty. I wanted my changes to be system wide for all users that is why i put it in /etc/

The three important settings in alsamixer are:
IEC958 = PCM Out
IEC958 0 = Not muted!!
IEC958 1 = PCM Out

Nothing more should need any changes here.
Note that all analog audio will disapear when you unmute IEC958 0. So it is either digital out or analog out. I think that sucks but I haven't found any way to change that.

lspci in my computer says "02:0b.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)"

Hope you get the things rocking!

I entered alsamixer in the terminal and got the gui and was able to arrow over to the IEC958 settings.  How do I tell if IEC958 0 is not muted.  Mine shows two zeros in a box?  I tried arrowing up and down but nothing changed.  I also entered and nothing happened.

---

### Post by posterberg on 2007-07-31
> **rggavubt said:**
> I entered alsamixer in the terminal and got the gui and was able to arrow over to the IEC958 settings.  How do I tell if IEC958 0 is not muted.  Mine shows two zeros in a box?  I tried arrowing up and down but nothing changed.  I also entered and nothing happened.

You should press the 'M' key to mute/unmute channels in alsamixer.

Hope that helps.

---

### Post by gubemton on 2007-10-08
I've managed to get it working! First I thought it was going to be trivial just pluging the
cable then after reading some forums I thought it was going to be impossible.

This was helpful:

[http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound_with_AC3_and_SPDIF]("http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound_with_AC3_and_SPDIF")

but also using the alsamixer ( console application, open it from a terminal). Use the keyboard left arrow to reach IEC958 Playback Source [AC-Link] Yo will see it as IEC958 P
it works when I select AC-Link, aother option is  A/D conv but it doesnt work. Then
I tested it with

mplayer -ao alsa:device=spdif audiofile

I have not been able to make it work in gnome applications yet.  My card is ASUS K8V onboard.

---

### Post by pak_a_bowl on 2008-03-30
Hey everybody, 1st post just registered but these forums have helped me out many times for opensuse and now kubuntu so i really hope this helps someone else. I have this card and to enable optical i just went to kmix and set IEC958 to H/W in 0 (1 worked too) for me IEC958 was already lit up but the red light above mix wasn't, turned it on and presto! the ones i have lit up are 3d control -switch, IEC935 output, Mix, External Amplifier, and multi track rate reset. (i messed with alsa mixer a little too) This is all i did and it works great playing from amarok. I have the 8.04 beta but i'd bet its all the same. again I really hope this helps ppl and i look forward to being part of the Ubuntu community.

---

### Post by pak_a_bowl on 2008-04-05
I noticed that its not decoding surround, only pcm 2 channel

---

