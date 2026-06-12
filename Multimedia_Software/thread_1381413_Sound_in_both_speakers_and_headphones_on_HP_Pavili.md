---
title: "Sound in both speakers and headphones on HP Pavilion."
date: 2010-01-14
forum: Multimedia Software
---

### Post by bleakcabal on 2010-01-14
Hello.

I have an HP Pavilion Desktop computer with integrated speakers in the screen. 

When I do not have any headphones plugged in my headphone jack, sound is coming out of the speakers.

When I plug headphones in my headphone jack, sound is coming out of both the speakers and the headphones. 

I would like for sound to come only from the headphones when they are plugged in. 

Does anyone have had any success dealing with this issue?

---

### Post by HappyFeet on 2010-01-14
What version of ubuntu are you using?

---

### Post by bleakcabal on 2010-01-14
Oops, I should have mentioned that. 
Karmic Koala.

---

### Post by willix on 2010-01-19
Hy 
I'm having a similar problem. 
I installed Ubuntu 9.10 KK on my Pavilion dv7 2150ez. All fine but for sound. After browsing a little, I read somewhere something about updating my BIOS which I did and that solved my problem only to find that plugging my headphone does not turn off the speakers.

Any solution to that? I'm reading a lot of stuff about Karmic Koala having sound issues; having to manually upgrade to the next ALSA version or uninstalling PulseAudio. What's the final word on all this?

As a secondary issue, I have noticed that I dont have any sound whatsoever (speakers, headphone) when switching to a different user? Anybody experienced that too and solved it?

I have also noticed that my movies play at twice the speed they should when using movie player in that second account but are fine (other than sound) with VLC. Dont think there is a link but I'd rather mention it just in case...

---

### Post by willix on 2010-01-22
Ok I'm done, I finally have my sound working on my HP pavilion dv7 2150ez with Ubuntu 9.10 Karmic Koala; Both speakers are working and they switch off when I plug my headphones.

YEEEEEESSSSSSSSSS :popcorn:

So for the record here is what I did:

I updated my BIOS; that did not do the trick

I updated my alsa to version 1.0.21; that did not do the trick

I edited my alsa-base.conf and added the enable_msi=1 option: that did not do the trick

So I finally installed the alsa-driver-snapshot.tar.gz as described here 
[https://help.ubuntu.com/community/SoundTroubleshooting#Having%20sound%20issues%20with%20HP%20dvx%20laptop](https://help.ubuntu.com/community/SoundTroubleshooting#Having%20sound%20issues%20with%20HP%20dvx%20laptop)

and edited the alsa-base.conf file and added
options snd_hda_intel model=hp-dv5

(and not options=hp_dv5 as I read in a few threads)

and that did it. 

The bottom line is; when everything else fails, read the doc!

It was right there under my eyes but read the section about dv7 ignoring the one about dvxx. When I tried the section about dvxx (dv7 is, afterall, a dvxx), everything fitted.

Next step: getting HDMI working...

---

### Post by defaria on 2010-02-02
While this works (I've tried both the alsa-driver snapshot and the alsa-driver-1.0.22.1) what you lose is your microphone! With this fix the input is dead. If you right click on the speaker icon and select Sound Preferences then over to the Input tab you'll see your input is all grayed out. :icon_frown:

Also, adding enable_msi=1 doesn't seem to do anything for me. setting model=hp-dv5 appears to be key. I wonder what hp-dv7 will do... Well that doesn't work... Back to hp-dv5.

Argh! I can't seem to get my mic working again. Perhaps it stopped working when I went from the default alsa with 9.10 -> 1.0.22.1. The default alsa driver worked like crap in that the sound was horrible - it seems like all the audio was coming from the sub woofer. With 1.0.22.1 the sound was much improved but still only stereo (where's the 5.1?). But I think the mic input broke with that new driver.

Either 1.0.22.1 or the snapshot driver works IFF you set model=hp-dv5 (other values such as hp-dv7 don't work). 

Given the state of things I think I'll stick with 1.0.22.1 and hp-dv5. Still I'd like to get all the functions of the sound card, which I did pay for BTW, working. Is that asking for too much? Argh!

Update: Another problem is that my Bluetooth headset doesn't work!!!

---

### Post by sleepee on 2010-02-04
hmmmm...  i have the same problem on my hp dv7 3080us
but i already have alsa 1.0.21 and have added
"options snd_hda_intel model=hp-dv5"
to alsa-base.conf and still have the same issue..

in fact, here's my alsa-base file
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv5
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
```

i wonder why it works for willix's dv7 but not on mine
:confused:

---

### Post by defaria on 2010-02-04
My guess? Those multiple option lines are messing you up. I have only one options line that has a model on it. You have multiple.

Question: (Assuming your using pulseaudio) if you run pavucontrol and go to the Output Devices tab I see "Internal Audio Analog Stereo" with only a left and right control. I thought this was a 5.1 card. Where is Front Center, etc? Sleepee, what do you see here?

Click on Input Devices tab - I see no "input devices available". Also right clicking on the speaker icon and selecting Sound Preferences then Input tab shows Input Volume grayed out. This means your mic doesn't work and you cannot use things like Skype. Not good! Sleepee what do you see here?

Also, I have a Bluetooth headset (Sony Ericson HBH-D980). I cannot connect the bluetooth headset for audio or phone operation. Sleepee, do you have any Bluetooth stereo headsets? I find them invaluable - especially on my bus commute to work. Right now I am booting to Windows 7 to watch videos or recorded TV on the bus because at least Windows 7 can hook up with my Bluetooth headset.

---

### Post by sleepee on 2010-02-05
> **defaria said:**
> My guess? Those multiple option lines are messing you up. I have only one options line that has a model on it. You have multiple.

Question: (Assuming your using pulseaudio) if you run pavucontrol and go to the Output Devices tab I see "Internal Audio Analog Stereo" with only a left and right control. I thought this was a 5.1 card. Where is Front Center, etc? Sleepee, what do you see here?

Click on Input Devices tab - I see no "input devices available". Also right clicking on the speaker icon and selecting Sound Preferences then Input tab shows Input Volume grayed out. This means your mic doesn't work and you cannot use things like Skype. Not good! Sleepee what do you see here?

Also, I have a Bluetooth headset (Sony Ericson HBH-D980). I cannot connect the bluetooth headset for audio or phone operation. Sleepee, do you have any Bluetooth stereo headsets? I find them invaluable - especially on my bus commute to work. Right now I am booting to Windows 7 to watch videos or recorded TV on the bus because at least Windows 7 can hook up with my Bluetooth headset.

the thing is, i put all those options in because i had another sound problem with my dv7 before..
i had no sound at all from my speakers... i only had sound from my subwoofer, but upgrading alsa and putting those options fixed it..  well, except for this jack sensing problem..

anyway, i put some pics of my pulseaudio volume control and sound preferences so you can see them...
they seem to be working fine for me.. but i don't think i have 5.1 sound though...
i do wish i had bluetooth headphones... that sounds pretty cool

---

### Post by defaria on 2010-02-05
Did you try reverting back to the standard config and just modifying it by adding model=dv5? Sorry my config file is not handy at the moment. Let me know if you want to see it.

From what I can see your mic should work because it's controls are not greyed out. Mine's broken.

Finally, I would have thought that this card with a subwoofer and a "multimedia/entertainment laptop" would be at least 5.1! On my desktop I know I have a 5.1 sound card because the Pulse Audio Volume Control let's me control all 5 channels.

The bluetooth headset that I have it great. I use it all the time as I'm usually listening to podcasts. They sit like a necklace of sorts and you can plug in the two comfortable earbuds and listen to music or podcasts. They sound quite good and I can wear them all day without fatigue. They also handle incoming calls just fine. Finally they are a great place to hang your card access card for work! They do go for about $100 and last 4-6 months before getting ratty. 

What I want to use them for is as audio for my laptop so I can watch a video or listen to a podcast on my laptop as I ride the bus instead of having to lug and wear large, bulky, wired head phones. I know this works - it works in Windows 7 for me - just not in Ubuntu - yet.

---

### Post by sleepee on 2010-02-05
> **defaria said:**
> Did you try reverting back to the standard config and just modifying it by adding model=dv5? Sorry my config file is not handy at the moment. Let me know if you want to see it.

From what I can see your mic should work because it's controls are not greyed out. Mine's broken.

Finally, I would have thought that this card with a subwoofer and a "multimedia/entertainment laptop" would be at least 5.1! On my desktop I know I have a 5.1 sound card because the Pulse Audio Volume Control let's me control all 5 channels.

The bluetooth headset that I have it great. I use it all the time as I'm usually listening to podcasts. They sit like a necklace of sorts and you can plug in the two comfortable earbuds and listen to music or podcasts. They sound quite good and I can wear them all day without fatigue. They also handle incoming calls just fine. Finally they are a great place to hang your card access card for work! They do go for about $100 and last 4-6 months before getting ratty. 

What I want to use them for is as audio for my laptop so I can watch a video or listen to a podcast on my laptop as I ride the bus instead of having to lug and wear large, bulky, wired head phones. I know this works - it works in Windows 7 for me - just not in Ubuntu - yet.

wow, those bluetooth headsets sound like a pretty good idea!  just out of curiosity, what brand are you using??  i might have to look into getting one of those.  especially if you can switch between cell phone and laptop audio.

btw, i just upgraded alsa to 1.0.22.1 and it fixed my jack sensing problem!
my mic was working already though.. i think in the pics i put up i was talking or something to show you that the mic was picking up sound..  the only problem i had was the jack sensing..  but not anymore!!!  wooohoooo!!!!!!  no more sound issues!!!
:D

i actually don't even know if i have 5.1 sound, but i don't really need it, so i really don't know much about that.  i wouldn't use my laptop for anything that needs surround sound, but if i did have it, i guess i'd want to know it works.
i mean, i have an "hp pavilion entertainment pc" so i guess it should have 5.1???
maybe i should be looking into that too..

---

### Post by defaria on 2010-02-06
> **sleepee said:**
> wow, those bluetooth headsets sound like a pretty good idea!  just out of curiosity, what brand are you using??  i might have to look into getting one of those.  especially if you can switch between cell phone and laptop audio.

They are [Sony Ericson HBH-DS980's]("http://www.sonystyle.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&productId=8198552921665254721&langId=-1"). I love 'em. They switch from laptop to cell phone - will from laptop running Windows 7 to cell phone. With this 1.0.22.1 ALSA drivers I've lost the ability to hook up to the DS980's via Bluetooth! :sad:


> btw, i just upgraded alsa to 1.0.22.1 and it fixed my jack sensing problem! my mic was working already though.. i think in the pics i put up i was talking or something to show you that the mic was picking up sound..  the only problem i had was the jack sensing..  but not anymore!!!  wooohoooo!!!!!!  no more sound issues!!!
:D

Yes but does your mic still work! I mean when I went to 1.0.22.1 the mic broke. Perhaps you went to 1.0.22.1, say the jack sense works and got excited but neglected to see that your mic broke.

If your mic still works then I'd be pissed because mine broke and I really wanted to use Skype! If so could you verify what hardware you have? I believe you said you had an HP dv7 like me, right?

> i actually don't even know if i have 5.1 sound, but i don't really need it, so i really don't know much about that.  i wouldn't use my laptop for anything that needs surround sound, but if i did have it, i guess i'd want to know it works.
i mean, i have an "hp pavilion entertainment pc" so i guess it should have 5.1???
maybe i should be looking into that too..

Right. I really don't think that the 5.1 will really be noticeable on the laptops speakers. But I plan on hooking this up to a home theater system via HDMI. If the sound card can do 5.1 I want it doing 5.1 out the HDMI to my Bose.

---

### Post by sleepee on 2010-02-06
> **defaria said:**
> They are [Sony Ericson HBH-DS980's]("http://www.sonystyle.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&productId=8198552921665254721&langId=-1"). I love 'em. They switch from laptop to cell phone - will from laptop running Windows 7 to cell phone. With this 1.0.22.1 ALSA drivers I've lost the ability to hook up to the DS980's via Bluetooth! :sad:

Yes but does your mic still work! I mean when I went to 1.0.22.1 the mic broke. Perhaps you went to 1.0.22.1, say the jack sense works and got excited but neglected to see that your mic broke.

If your mic still works then I'd be pissed because mine broke and I really wanted to use Skype! If so could you verify what hardware you have? I believe you said you had an HP dv7 like me, right?

Right. I really don't think that the 5.1 will really be noticeable on the laptops speakers. But I plan on hooking this up to a home theater system via HDMI. If the sound card can do 5.1 I want it doing 5.1 out the HDMI to my Bose.

$150!?!?  :shock:  they look pretty cool, but not THAT cool...
i'll think i'll pass for now.  lol

anyway, i checked my mic, and apparently it seems to be working fine when i used it with Cheese and Sound Recorder.  the sound did come out a little bit scratchy, but it works..  i didn't try it in skype, but i assume it works there too...
i don't think i have a way of testing that 5.1 since i don't have those kinds of speakers, so i guess i can't help you there..
but i assume there must be a way to get 5.1 sound working... i mean, 5.1 is pretty common, so there must be support for it in ubuntu..

BUT, i did speak a little too soon about everything working fine with Alsa 1.0.22.1.
because i realized afterwards i had the weirdest problem..
i can't play sound from an app, like movie player, vlc, songbird, etc., and sound from a flash movie in firefox at the same time.
if i put a flash movie to play first, the other apps won't play sound.  but if i close the flash movie, THEN i can play sound in vlc, songbird, etc...
but if i do that, then the flash movie won't play sound!
](*,)

i don't even know if i'm explaining it right, but it's a mess..
of course, i had also upgraded to flash 10 alpha for 64 bit...  but i'm not sure if that's the problem.  i have a feeling it was alsa's fault..

anyway, exactly which dv7 model do you have??  because i know some of them have slightly different features..
maybe yours has something mine doesn't.

---

### Post by warp99 on 2010-02-06
/usr/share/doc/alsa-base/driver/HD-Audio.txt.gz

```
Speaker and Headphone Output
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
One of the most frequent (and obvious) bugs with HD-audio is the
silent output from either or both of a built-in speaker and a
headphone jack.  In general, you should try a headphone output at
first.  A speaker output often requires more additional controls like
the external amplifier bits.  Thus a headphone output has a slightly
better chance.

Before making a bug report, double-check whether the mixer is set up
correctly.  The recent version of snd-hda-intel driver provides mostly
"Master" volume control as well as "Front" volume (where Front
indicates the front-channels).  In addition, there can be individual
"Headphone" and "Speaker" controls.

Ditto for the speaker output.  There can be "External Amplifier"
switch on some codecs.  Turn on this if present.

[b]Another related problem is the automatic mute of speaker output by
headphone plugging.  This feature is implemented in most cases, but
not on every preset model or codec-support code.

In anyway, try a different model option if you have such a problem.
Some other models may match better and give you more matching
functionality.  If none of the available models works, send a bug
report.  See the bug report section for details.[/b]
```
/usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
```
  Model name	Description
  ----------    -----------
ALC880
======
  3stack	3-jack in back and a headphone out
  3stack-digout	3-jack in back, a HP out and a SPDIF out
  5stack	5-jack in back, 2-jack in front
  5stack-digout	5-jack in back, 2-jack in front, a SPDIF out
  6stack	6-jack in back, 2-jack in front
  6stack-digout	6-jack with a SPDIF out
  w810		3-jack
  z71v		3-jack (HP shared SPDIF)
  asus		3-jack (ASUS Mobo)
  asus-w1v	ASUS W1V
  asus-dig	ASUS with SPDIF out
  asus-dig2	ASUS with SPDIF out (using GPIO2)
  uniwill	3-jack
  fujitsu	Fujitsu Laptops (Pi1536)
  F1734		2-jack
  lg		LG laptop (m1 express dual)
  lg-lw		LG LW20/LW25 laptop
  tcl		TCL S700
  clevo		Clevo laptops (m520G, m665n)
  medion	Medion Rim 2150
  test		for testing/debugging purpose, almost all controls can be
		adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y
  auto		auto-config reading BIOS (default)

ALC260
======
  hp		HP machines
  hp-3013	HP machines (3013-variant)
  hp-dc7600	HP DC7600
  fujitsu	Fujitsu S7020
  acer		Acer TravelMate
  will		Will laptops (PB V7900)
  replacer	Replacer 672V
  basic		fixed pin assignment (old default model)
  test		for testing/debugging purpose, almost all controls can
		adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y
  auto		auto-config reading BIOS (default)

ALC262
======
  fujitsu	Fujitsu Laptop
  hp-bpc	HP xw4400/6400/8400/9400 laptops
  hp-bpc-d7000	HP BPC D7000
  hp-tc-t5735	HP Thin Client T5735
  hp-rp5700	HP RP5700
  benq		Benq ED8
  benq-t31	Benq T31
  hippo		Hippo (ATI) with jack detection, Sony UX-90s
  hippo_1	Hippo (Benq) with jack detection
  sony-assamd	Sony ASSAMD
  toshiba-s06	Toshiba S06
  toshiba-rx1	Toshiba RX1
  tyan		Tyan Thunder n6650W (S2915-E)
  ultra		Samsung Q1 Ultra Vista model
  lenovo-3000	Lenovo 3000 y410
  nec		NEC Versa S9100
  basic		fixed pin assignment w/o SPDIF
  auto		auto-config reading BIOS (default)

ALC267/268
==========
  quanta-il1	Quanta IL1 mini-notebook
  3stack	3-stack model
  toshiba	Toshiba A205
  acer		Acer laptops
  acer-dmic	Acer laptops with digital-mic
  acer-aspire	Acer Aspire One
  dell		Dell OEM laptops (Vostro 1200)
  zepto		Zepto laptops
  test		for testing/debugging purpose, almost all controls can
		adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y
  auto		auto-config reading BIOS (default)

ALC269
======
  basic		Basic preset
  quanta	Quanta FL1
  eeepc-p703	ASUS Eeepc P703 P900A
  eeepc-p901	ASUS Eeepc P901 S101
  fujitsu	FSC Amilo
  auto		auto-config reading BIOS (default)

ALC662/663
==========
  3stack-dig	3-stack (2-channel) with SPDIF
  3stack-6ch	 3-stack (6-channel)
  3stack-6ch-dig 3-stack (6-channel) with SPDIF
  6stack-dig	 6-stack with SPDIF
  lenovo-101e	 Lenovo laptop
  eeepc-p701	ASUS Eeepc P701
  eeepc-ep20	ASUS Eeepc EP20
  ecs		ECS/Foxconn mobo
  m51va		ASUS M51VA
  g71v		ASUS G71V
  h13		ASUS H13
  g50v		ASUS G50V
  asus-mode1	ASUS
  asus-mode2	ASUS
  asus-mode3	ASUS
  asus-mode4	ASUS
  asus-mode5	ASUS
  asus-mode6	ASUS
  auto		auto-config reading BIOS (default)

ALC882/885
==========
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  arima		Arima W820Di1
  targa		Targa T8, MSI-1049 T8
  asus-a7j	ASUS A7J
  asus-a7m	ASUS A7M
  macpro	MacPro support
  mbp3		Macbook Pro rev3
  imac24	iMac 24'' with jack detection
  w2jc		ASUS W2JC
  auto		auto-config reading BIOS (default)

ALC883/888
==========
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire	Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  medion	Medion Laptops
  medion-md2	Medion MD2
  targa-dig	Targa/MSI
  targa-2ch-dig	Targs/MSI with 2-channel
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e	Lenovo 101E
  lenovo-nb0763	Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky	Lenovo Sky
  haier-w66	Haier W66
  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell	Dell machines with 6stack (Inspiron 530)
  mitac		Mitac 8252D
  clevo-m720	Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  auto		auto-config reading BIOS (default)

ALC861/660
==========
  3stack	3-jack
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack with SPDIF I/O
  3stack-660	3-jack (for ALC660)
  uniwill-m31	Uniwill M31 laptop
  toshiba	Toshiba laptop support
  asus		Asus laptop support
  asus-laptop	ASUS F2/F3 laptops
  auto		auto-config reading BIOS (default)

ALC861VD/660VD
==============
  3stack	3-jack
  3stack-dig	3-jack with SPDIF OUT
  6stack-dig	6-jack with SPDIF OUT
  3stack-660	3-jack (for ALC660VD)
  3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
  lenovo	Lenovo 3000 C200
  dallas	Dallas laptops
  hp		HP TX1000
  asus-v1s	ASUS V1Sn
  auto		auto-config reading BIOS (default)

CMI9880
=======
  minimal	3-jack in back
  min_fp	3-jack in back, 2-jack in front
  full		6-jack in back, 2-jack in front
  full_dig	6-jack in back, 2-jack in front, SPDIF I/O
  allout	5-jack in back, 2-jack in front, SPDIF out
  auto		auto-config reading BIOS (default)

AD1882 / AD1882A
================
  3stack	3-stack mode (default)
  6stack	6-stack mode

AD1884A / AD1883 / AD1984A / AD1984B
====================================
  desktop	3-stack desktop (default)
  laptop	laptop with HP jack sensing
  mobile	mobile devices with HP jack sensing
  thinkpad	Lenovo Thinkpad X300

AD1884
======
  N/A

AD1981
======
  basic		3-jack (default)
  hp		HP nx6320
  thinkpad	Lenovo Thinkpad T60/X60/Z60
  toshiba	Toshiba U205

AD1983
======
  N/A

AD1984
======
  basic		default configuration
  thinkpad	Lenovo Thinkpad T61/X61
  dell		Dell T3400

AD1986A
=======
  6stack	6-jack, separate surrounds (default)
  3stack	3-stack, shared surrounds
  laptop	2-channel only (FSC V2060, Samsung M50)
  laptop-eapd	2-channel with EAPD (ASUS A6J)
  laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
  ultra		2-channel with EAPD (Samsung Ultra tablet PC)
  samsung	2-channel with EAPD (Samsung R65)

AD1988/AD1988B/AD1989A/AD1989B
==============================
  6stack	6-jack
  6stack-dig	ditto with SPDIF
  3stack	3-jack
  3stack-dig	ditto with SPDIF
  laptop	3-jack with hp-jack automute
  laptop-dig	ditto with SPDIF
  auto		auto-config reading BIOS (default)

Conexant 5045
=============
  laptop-hpsense    Laptop with HP sense (old model laptop)
  laptop-micsense   Laptop with Mic sense (old model fujitsu)
  laptop-hpmicsense Laptop with HP and Mic senses
  benq		Benq R55E
  test		for testing/debugging purpose, almost all controls
		can be adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y

Conexant 5047
=============
  laptop	Basic Laptop config 
  laptop-hp	Laptop config for some HP models (subdevice 30A5)
  laptop-eapd	Laptop config with EAPD support
  test		for testing/debugging purpose, almost all controls
		can be adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y

Conexant 5051
=============
  laptop	Basic Laptop config (default)
  hp		HP Spartan laptop
  hp-dv6736	HP dv6736
  lenovo-x200	Lenovo X200 laptop

STAC9200
========
  ref		Reference board
  dell-d21	Dell (unknown)
  dell-d22	Dell (unknown)
  dell-d23	Dell (unknown)
  dell-m21	Dell Inspiron 630m, Dell Inspiron 640m
  dell-m22	Dell Latitude D620, Dell Latitude D820
  dell-m23	Dell XPS M1710, Dell Precision M90
  dell-m24	Dell Latitude 120L
  dell-m25	Dell Inspiron E1505n
  dell-m26	Dell Inspiron 1501
  dell-m27	Dell Inspiron E1705/9400
  gateway-m4	Gateway laptops with EAPD control
  gateway-m4-2	Gateway laptops with EAPD control
  panasonic	Panasonic CF-74
  auto		BIOS setup (default)

STAC9205/9254
=============
  ref		Reference board
  dell-m42	Dell (unknown)
  dell-m43	Dell Precision
  dell-m44	Dell Inspiron
  eapd		Keep EAPD on (e.g. Gateway T1616)
  auto		BIOS setup (default)

STAC9220/9221
=============
  ref		Reference board
  3stack	D945 3stack
  5stack	D945 5stack + SPDIF
  intel-mac-v1	Intel Mac Type 1
  intel-mac-v2	Intel Mac Type 2
  intel-mac-v3	Intel Mac Type 3
  intel-mac-v4	Intel Mac Type 4
  intel-mac-v5	Intel Mac Type 5
  intel-mac-auto Intel Mac (detect type according to subsystem id)
  macmini	Intel Mac Mini (equivalent with type 3)
  macbook	Intel Mac Book (eq. type 5)
  macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
  macbook-pro	Intel Mac Book Pro 2nd generation (eq. type 3)
  imac-intel	Intel iMac (eq. type 2)
  imac-intel-20	Intel iMac (newer version) (eq. type 3)
  ecs202	ECS/PC chips
  dell-d81	Dell (unknown)
  dell-d82	Dell (unknown)
  dell-m81	Dell (unknown)
  dell-m82	Dell XPS M1210
  auto		BIOS setup (default)

STAC9202/9250/9251
==================
  ref		Reference board, base config
  m1		Some Gateway MX series laptops (NX560XL)
  m1-2		Some Gateway MX series laptops (MX6453)
  m2		Some Gateway MX series laptops (M255)
  m2-2		Some Gateway MX series laptops
  m3		Some Gateway MX series laptops
  m5		Some Gateway MX series laptops (MP6954)
  m6		Some Gateway NX series laptops
  auto		BIOS setup (default)

STAC9227/9228/9229/927x
=======================
  ref		Reference board
  ref-no-jd	Reference board without HP/Mic jack detection
  3stack	D965 3stack
  5stack	D965 5stack + SPDIF
  dell-3stack	Dell Dimension E520
  dell-bios	Fixes with Dell BIOS setup
  auto		BIOS setup (default)

STAC92HD71B*
============
  ref		Reference board
  dell-m4-1	Dell desktops
  dell-m4-2	Dell desktops
  dell-m4-3	Dell desktops
  hp-m4		HP mini 1000
  hp-dv5	HP dv series
  hp-hdx	HP HDX series
  auto		BIOS setup (default)

STAC92HD73*
===========
  ref		Reference board
  no-jd		BIOS setup but without jack-detection
  dell-m6-amic	Dell desktops/laptops with analog mics
  dell-m6-dmic	Dell desktops/laptops with digital mics
  dell-m6	Dell desktops/laptops with both type of mics
  dell-eq	Dell desktops/laptops
  auto		BIOS setup (default)

STAC92HD83*
===========
  ref		Reference board
  mic-ref	Reference board with power managment for ports
  dell-s14	Dell laptop
  auto		BIOS setup (default)

STAC9872
========
  vaio		VAIO laptop without SPDIF
  auto		BIOS setup (default)
```

Check to see which chipset that you have with this command:
```
cat /proc/asound/card0/codec#* | grep Codec
```

More information on Intel HDA sound configuration can be found here:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by defaria on 2010-02-07
> **sleepee said:**
> $150!?!?  :shock:  they look pretty cool, but not THAT cool...
i'll think i'll pass for now.  lol

I just picked up a new set @Frys for $99. Yes they are expensive. But $150 is what you may pay at the Sony Store itself.

> anyway, i checked my mic, and apparently it seems to be working fine when i used it with Cheese and Sound Recorder.  the sound did come out a little bit scratchy, but it works..  i didn't try it in skype, but i assume it works there too...

Yes I'm jealous!

> i don't think i have a way of testing that 5.1 since i don't have those kinds of speakers, so i guess i can't help you there..

You don't need speakers - just controls. As my screen shot from my desktop showed there should be separate controls and changing them should affect the sound.

> but i assume there must be a way to get 5.1 sound working... i mean, 5.1 is pretty common, so there must be support for it in ubuntu..

There is on my desktop with another sound card. It's just this driver that's not doing this. Additionally if you plug the HDMI cable into your home theater the sound it not transfered. This is what I bought this laptop for - to run my home theater system and to be able to directly connect it via an HDMI cable and have 5.1 sound coming out (as well as being able to do 1080p HD video). This does not work in Ubuntu with this sound driver. No sound comes out the home theater system - just the laptop speakers. I know that this is workable because I can dual boot to Windows 7 and in Windows 7 the HDMI cable does transmit the sound just fine.

> BUT, i did speak a little too soon about everything working fine with Alsa 1.0.22.1.
because i realized afterwards i had the weirdest problem..
i can't play sound from an app, like movie player, vlc, songbird, etc., and sound from a flash movie in firefox at the same time.
if i put a flash movie to play first, the other apps won't play sound.  but if i close the flash movie, THEN i can play sound in vlc, songbird, etc...
but if i do that, then the flash movie won't play sound!
](*,)

Hmm are you using pulseaudio? I can play flash videos (.flv) and say youtube at the same time.

> i don't even know if i'm explaining it right, but it's a mess..
of course, i had also upgraded to flash 10 alpha for 64 bit...  but i'm not sure if that's the problem.  i have a feeling it was alsa's fault..

anyway, exactly which dv7 model do you have??  because i know some of them have slightly different features..
maybe yours has something mine doesn't.

Might be. How do I tell exactly? [Here's a page from HP]("http://www.shopping.hp.com/webapp/shopping/store_access.do?template_type=series_detail&category=notebooks&series_name=dv7tqe_series&aoid=35252") about my laptop. Of course the specs don't even say what the sound card is!

---

### Post by defaria on 2010-02-08
warp99, I'm sure you're trying to be helpful but I'm not sure you are being helpful. My laptop (an HP dv7-3000) is not listed in your list and your links point off to tons-o-information about all kinds of sound things and really nothing specific about my problem. I'm not trying to become a Linux Sound Engineer here - I'm just trying to get my hardware to work in a reasonable fashion. Is that asking for too much?

I realize that there are bugs in the drivers or that the sound card is new and not fully working, etc. However I'm not here to hear problems or excuses - I'm here to get solutions. Got any of those?

---

### Post by donfromconn on 2010-02-08
Hello,
The external speakers, and now headphones (but not earbuds) on my Dell Vostro have recently stopped working. I always assumed this was a hardware problem with the jack or port (because the same would happen with Sony Walkman, and can temporarily be fixed by applying sideways pressure to the jack). Someone just showed me how the jack port works, and how the little metal tabs can get bent back, so you fix them just by bending them back. So my first question is, do people think this is really the problem, and is it easy to open the laptop? I just unscrew all the screws on the bottom?
 
The strange thing is the speakers don't work on other laptops or CD players. The power light is on for the speakers, so that suggests the jack itself, or the connection inside the speakers. But then why do the headphones....? You see the twilight zone aspects of the situation.
 
Thanks for any reactions
 
DonfromConn

---

### Post by warp99 on 2010-02-08
> **defaria said:**
> warp99, I'm sure you're trying to be helpful but I'm not sure you are being helpful. My laptop (an HP dv7-3000) is not listed in your list and your links point off to tons-o-information about all kinds of sound things and really nothing specific about my problem. I'm not trying to become a Linux Sound Engineer here - I'm just trying to get my hardware to work in a reasonable fashion. Is that asking for too much?

I realize that there are bugs in the drivers or that the sound card is new and not fully working, etc. However I'm not here to hear problems or excuses - I'm here to get solutions. Got any of those?

I already posted the solution based on the documentation, but unfornately you didn't see this. If goes like this:

First check which souncard you have:
```
cat /proc/asound/card0/codec#* | grep Codec
```

With this information go through the list and try different models to see if this option gives you the functionally that you need. Example:

Your chipset is STAC92HD71B* so going through the list you see that there are several model options:

```
STAC92HD71B*
============
  ref		Reference board
  dell-m4-1	Dell desktops
  dell-m4-2	Dell desktops
  dell-m4-3	Dell desktops
  hp-m4		HP mini 1000
  hp-dv5	HP dv series
  hp-hdx	HP HDX series
  auto		BIOS setup (default)

```

Per the documentation the solution is to **"try a different model option if you have such a problem."** I'm sorry but if you're not even willing to read the documentation and only looking for someone to just solve your problem maybe you should get a paid support solution.

Edit: Anyway my previous post was to help the original owner of the thread, which is the exact problem that the documentation stated will happen sometimes.

---

### Post by defaria on 2010-02-10
> **warp99 said:**
> I already posted the solution based on the documentation, but unfornately you didn't see this.

No I saw it. It's just that it's **NOT** a solution. Do you know what a solution is son? It's something that **solves** the problem. You're posted "solution" doesn't solve anything for me.

> If goes like this:

First check which souncard you have:
```
cat /proc/asound/card0/codec#* | grep Codec
```

With this information go through the list and try different models to see if this option gives you the functionally that you need. Example:

Your chipset is STAC92HD71B* so going through the list you see that there are several model options:

Nice try but your wrong. Where do you get the "Your chipset is STAC92HD71B*" crap? When I do that command I get:

Codec: IDT 92HD75B3X5

Not STAC92HD71B*. You can tell that those strings don't compare right?

> ```
STAC92HD71B*
============
  ref		Reference board
  dell-m4-1	Dell desktops
  dell-m4-2	Dell desktops
  dell-m4-3	Dell desktops
  hp-m4		HP mini 1000
  hp-dv5	HP dv series
  hp-hdx	HP HDX series
  auto		BIOS setup (default)

```

Per the documentation the solution is to **"try a different model option if you have such a problem."**

Huh? Where do you get that a **solution** is to **try** a different option? Aside from the fact that my sound card does not at all match the string and assumption you made (close but not really a match), the word "try" does not impart certainty of a solution. So stop being full of yourself asserting you have posted the solution until and unless your posted solution actually solves the problem, OK?

> I'm sorry but if you're not even willing to read the documentation

I read the documentation you presented. It didn't match my particular situation so I had no particular reason to go off trying those options. Got it?

> and only looking for someone to just solve your problem maybe you should get a paid support solution.

Well of course I want somebody to solve the problem. Here's a clue for the clueless such as yourself... the stupid problems of sound not working is not a problem that an end user should be solving!!! Having functioning sound is something that has been working for quite literally decades on other OSes. Can't Linux do the same? What's so frigging hard getting a mic to work? Why does the sound come out only through the sub-woofer in my original case? This is really not rocket science as evidenced by other OSes getting it right out of the box rather than belittling their customers to do the work for them... But I digress...

And since you were not following along I'll fill you in - it's not just the problem with the speakers still working when the headphones plugged in but also that the mic doesn't work, the sound doesn't come out the HDMI connection and the Bluetooth profile is all messed up.

I'm willing to put up with a certain amount work, debugging and building of stuff myself. But putting up with snot nosed kids who can't even string match is asking too much from me!

---

### Post by KeLa on 2010-02-10
Hi,
I have exact same sound chip that you defaria.
Codec: IDT 92HD75B3X5
What i did yesterday evening to fix this speaker headphone problem was that i
compiled and installed latest alsa drivers (1.0.22.1), lib (1.0.22) and utils (1.0.22)
and rebooted.
That was what fixed my system. Now speakers mutes when headphones are connected and comes back up after removing headphones.
Also mic in headset works fine.

---

### Post by defaria on 2010-02-10
Oh my headphones work with the model set to dv5 as I stated. The mic, unfortunately, doesn't work. By that I mean the mic input is greyed out in gnome-volume-control. I'm speaking about the internal mic on the laptop with the webcam. It used to work, until I updated the sound driver. I've only tried wired headsets that are headphones only. I don't have a wired headset with a mic - I do have a Bluetooth headset with a mic. That's not work but that's probably a Bluetooth problem.

Question: Does your pavucontrol: Configuration (tab): Profile have any 5.1 stuff? I would think that this sound card does 5.1 - maybe not on the laptop speakers but at least out the HDMI? Also does your HDMI connection produce sound? I wish to hook up this entertainment PC to my entertainment center via HDMI. Usually sound is forwarded down the HDMI connection and will then go out my home theater system. On this PC it doesn't. Finally, if you have nay Bluetooth headset - does your Bluetooth work? I'd rather use my comfortable and small Bluetooth headset on the bus than to have to lug around a large set of wired headphones.

---

### Post by KeLa on 2010-02-10
Internal (analog) soundcard doesn't have 5.1 sound.
I have not tested the HDMI connector in anyway yet.
Bluetooth i have tested and it worked great without any problems (headphones and mic both)
Bluetooth headset i tested was Nokia BH-905 with active noise reduction system.

I have bought a SteelSeries Siperia V2 headset and it have usb virtual 7.1 soundcard included but have not yet get it work with 7.1 sound (only 5.1 worked out of the box)
and that is my backup number 1 for sound in this laptop.
Second backup is Terratec Aureon Dual USB and it has optical and analog output and mic input and
it's same size as usb memory stick.

---

### Post by warp99 on 2010-02-10
> **defaria said:**
> But putting up with snot nosed kids who can't even string match is asking too much from me!

My original post was for the owner of the thread, not you. Don't think so highly of yourself because nobody really cares. The only snot nosed kid appears to be you since you hijacked this thread instead of helping the OP.

---

### Post by defaria on 2010-02-11
That's why I said in my initial response to you, that I know you are trying to be helpful but it doesn't help me - let me repeat that since you obviously missed it the first time - it doesn't help ME, that's right I SAID ME!!! at all. It is implied that perhaps you might have helped others but you didn't help me. 

Let me quote it for you as further evidence here with emphasis:

> warp99, I'm sure you're trying to be helpful but I'm not sure you are being helpful. **My laptop** (an HP dv7-3000) is not listed in your list and your links point off to tons-o-information about all kinds of sound things and really nothing specific about **my problem**. I'm not trying to become a Linux Sound Engineer here - **I'm just trying to get my hardware** to work in a reasonable fashion. Is that asking for too much?

I realize that there are bugs in the drivers or that the sound card is new and not fully working, etc. However I'm not here to hear problems or excuses - I'm here to get solutions. Got any of those?

Clearly I was talking about my problems which had been being discussed.

IOW idiot, that's exactly what I first said, politely, before you started getting all rude. Now if you had half brain and any humility you'd admit that it was you who screwed up there son. So wipe your nose and suck it up! Methinks you won't admit it because you'd rather argue and be full of yourself!

---

### Post by defaria on 2010-02-11
Back to sound issues...

With the latest driver and model=hp-dv5

. Plugging in the headphones does nothing - no sound and it doesn't cut off the internal laptop speakers. Funny this used to work.

. Mic input (for the internal mic?) is simply greyed out and doesn't record anything. Initially this used to work before I updated the sound driver.

. Bluetooth is now working but oddly. Getting it to connect is extremely hit and miss. Most times I have to go into pavucontrol and over to configuration because it connects but is configured off. Other times it says it's connected in the Bluetooth devices but no sound comes out. When it's really misbehaving I have to remove and re-add the device.

. HDMI output does not work - no sound goes out the HDMI cable. (Additional problem: When plugging in the HDMI cable, the output doesn't immediately appear on the screen. I have it hit Fn and like F4 to get it to "project". Further, the laptop "screen" is larger than my 42" HDTV! By that I mean if I move the mouse to the right edge of the screen the viewport on the HDTV shifts).

---

### Post by Eraser on 2010-02-13
I would like to report that I was having the issue of sound coming from both speakers and headphones in ah HP Pavilion dv6-1375dx.

Following the procedure described by willix solved the problem.

Thanks willix for the simple, easy to follow instructions.


> **willix said:**
> Ok I'm done, I finally have my sound working on my HP pavilion dv7 2150ez with Ubuntu 9.10 Karmic Koala; Both speakers are working and they switch off when I plug my headphones.

YEEEEEESSSSSSSSSS :popcorn:

So for the record here is what I did:

I updated my BIOS; that did not do the trick

I updated my alsa to version 1.0.21; that did not do the trick

I edited my alsa-base.conf and added the enable_msi=1 option: that did not do the trick

So I finally installed the alsa-driver-snapshot.tar.gz as described here 
[https://help.ubuntu.com/community/SoundTroubleshooting#Having%20sound%20issues%20with%20HP%20dvx%20laptop](https://help.ubuntu.com/community/SoundTroubleshooting#Having%20sound%20issues%20with%20HP%20dvx%20laptop)

and edited the alsa-base.conf file and added
options snd_hda_intel model=hp-dv5

(and not options=hp_dv5 as I read in a few threads)

and that did it. 

The bottom line is; when everything else fails, read the doc!

It was right there under my eyes but read the section about dv7 ignoring the one about dvxx. When I tried the section about dvxx (dv7 is, afterall, a dvxx), everything fitted.

Next step: getting HDMI working...

---

### Post by defaria on 2010-02-13
I'm unhappy to report that my headphones no longer work. I did not change my configuration. It used to work. Now I get no sound in the headphones and plugging them in does not silence the laptop's speakers.

---

### Post by mattaphore on 2010-02-20
Warp & Willix, thanks for your posts, it definitely fixed my audio problem. Now my laptop speakers mute when I plug in my headphones on my HP Tx2110us.

I was having a heck of a time finding a thread this morning. [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") was also helpful (basically the same thing)

For the hp tx2110us the model to put in alsa-base.config is simply "hp"
I tried the model=3stack and 3stack-dig but those didn't work.

I just checked sound recorder and my mic input also works.:popcorn:

---

### Post by defaria on 2010-02-20
Figured it out! If you recall (and was reading this thread) Willix and I had downloaded and installed a newer version of alsa. At that point things worked for me. But then a kernel update or two happened (Actually from 2.6.31-17 -> 2.6.31-19) and that's what broke it! Luckilyh I saved the source under /usr/src (alsa-driver-1.0.22.1, alsa-lib-1.0.22 and alsa-utils-1.0.22). So I went under those directories and performed configure, make and make install for all 3 and rebooted. Of course I need to have model=hp-dv5 in /etc/modprobe/alsa-base.conf (I had been playing with that lately) and all is well again. Well not all, HDMI sound still doesn't work and Bluetooth is funky still (When I connect my Bluetooth it's set to Off and I need to toggle it on every time) but the speakers work well and headphones work as expected.

---

### Post by opethfan89 on 2010-03-25
I am SO glad I came across this thread, and holy CRAP was I surprised when this worked!
I am using an HP Pavillion dv7-3060US laptop, running 9.10 64-Bit.

My headphone jack works perfectly now (I actually have 2 jacks, both work perfect) _**AND**_ my mic still works!!

Oh man I am so happy right now, this just makes my Ubuntu install ALMOST perfect :P

Ok, enough about how happy I am....for those of you who read this, and are using an HP Pavillion DV7 laptop, I followed [this link]("https://help.ubuntu.com/community/SoundTroubleshooting#Having%20sound%20issues%20with%20HP%20dvx%20laptop") and it worked for me. I added both lines to my alsa-base.conf file, that is, the 'options snd_hda_intel model=hp-dv5' line, AND 'options snd-hda-intel enable_msi=1' line. I should also mention that I followed the steps listed [here]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats") from the official Ubuntu wiki to update to the latest version of the pulse-audio driver.

Again, my speakers are working, my mic is working, and the sound behaves appropriately when headphones are plugged into either one of my jacks.

The only minor issue is that the sound is much lower than it is when I'm in windows, but its not a big enough issue to make me want to sign onto windows just to listen to music.

Thanks again for whoever posted that 1st link, helped me tremendously!

*EDIT* I updated my driver FIRST, then followed the steps SECOND. This is on a FRESH 9.10 install, and it works flawlessly. Also, at least preliminary results show that this has fixed the rather annoying shut down BEEP noise that I had been experiencing.

---

### Post by azurepalm on 2011-04-03
I had the same issue for my old laptop (HP nw8000) on Ubuntu 10.10, I fixed it by:

1. Open Terminal
2. Type in: **alsamixer**
3. Use right/left arrow key and select **<headphon>** (aka Headphone Jack Sense)
4. Press **m** on your keyboard to modify (from default OFF to ON)
5. Press **Esc** (escape key) to quit the alsamixer app

and woalaa... it magically and immediately senses my plugged-in headphone and routes the sound appropriately.

Note: for my case, other posted solutions (like updating ALSA drivers, editing the 'alsa-base' file, etc) killed my audio driver completely, and i had to do a reinstall of Ubuntu 10.10 to get them back.

Reference: [http://ubuntuforums.org/showthread.php?t=900898](http://ubuntuforums.org/showthread.php?t=900898)

---

