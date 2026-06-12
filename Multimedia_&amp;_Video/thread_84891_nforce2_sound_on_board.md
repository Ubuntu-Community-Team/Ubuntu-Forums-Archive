---
title: "nforce2 sound on board"
date: 2005-11-01
forum: Multimedia &amp; Video
---

### Post by Kirzzy_Boy on 2005-11-01
This was intended as an howto but it doesn't work properly (yet).

First I'd like to all concerned to know that this is simply what I found on the Hoary HOWTO page and all credit goes to RastaMahata. The original post is here: [http://www.ubuntuforums.org/showthread.php?t=30076](http://www.ubuntuforums.org/showthread.php?t=30076)

This has solved all my Quake4, Americas Army and Doom3 sound issues.

1. ```
killall esd
```
2. System > preferences > sound > enable sound server startup: uncheck
3. ```
gedit ~/.asoundrc
``` or alternatively ```
/etc/asound.conf
```
4. insert the following ```
pcm.nforce-hw {
    type hw
    card 0
}

pcm.!default {
    type plug
    slave.pcm "nforce"
}

pcm.nforce {
    type dmix
    ipc_key 1234
    slave {
        pcm "hw:0,0"
        period_time 0
        period_size 1024
        buffer_size 4096
        rate 44100
    }
}

ctl.nforce-hw {
    type hw
    card 0
}
```

Save and close
5. ```
sudo gedit /etc/libao.conf
```
and where it says esd, type alsa as shown here:
```
default_driver=alsa
```
6. System > Preferences > Multimedia Systems Selector:
Default Sink: Select ALSA
Default Source: Select OSS below.
This way you can record with your mic
7. System > Administration > Synaptic Package Manager: Search for libesd-alsa0 and check that it's installed along with all dependancies.
8. Finally test by playing a movie _and_ a song (totem + rhythmbox)...

Final note from original post: anyway, gaim sounds seem choppy / bad quality, but totem movies play excellent (no audio delay). I've learnt how to live with it, though.  (Maybe changing the sounds could work...)
I don't use Gaim so I cannot confirm this!

Hope this helps ;)

---

### Post by Dracontopes on 2005-11-01
I have an Asus A7N8X deluxe rev2, with nvidia Soundstorm (nforce2 sound).
I have followed the guide exactly and rebooted the system.

Sounds are very choppy in Rhythmbox and every other app using sound. The sound is very hackling, stuttering, etc, unbearable. Any clue on how to solve this?

---

### Post by wylfing on 2005-11-01
[QUOTE=Dracontopes]I have an Asus A7N8X[/QUOTE]

I have the same board. Don't bother with any of this, because it won't work.

I'm not entirely sure about the genesis of this anyway. Granted, I don't have Quake or America's Army, but all the games I *do* have play sound just fine with Ubuntu's out-of-the-box sound setup, using ESD. That includes a lot of stuff running under Cedega. I can definitely play music and movies simultaneously without trouble. (I just tried it to make sure I wasn't hallucinating -- ABBA's *Dancing Queen* and Dave Chappelle's R. Kelly parody at the same time, wheee!)

The short story is that if it's not broke don't fix it. I think this HOWTO should be amended to say "If you have such-and-such a motherboard and sound chip, and you have problems with Ubuntu's out-of-the-box sound, try this."

---

### Post by Dracontopes on 2005-11-01
[quote=wylfing]text[/quote]

Did you configure anything on your system to have simultanious sounds? Because it didn't work on my PC :(

---

### Post by Kirzzy_Boy on 2005-11-01
The problem I had was when I ran Quake4 or Doom the sound was extremely distorted.... I landed up having to use: ```
quake +set s_driver oss
``` to get the sound to work but this resulted in crashing after about 5 - 10 minutes game time. The log showed sound overflows. After doing the above changes my system runs really well. 
IMHO I think it might have something to do with the actuall sound chip used by the MB manufacturer. Then again I could be very wrong. I'd be more than happy to hear any input on this. :confused:

---

### Post by Kirzzy_Boy on 2005-11-01
[QUOTE=wylfing]I have the same board. Don't bother with any of this, because it won't work.

I'm not entirely sure about the genesis of this anyway. Granted, I don't have Quake or America's Army, but all the games I *do* have play sound just fine with Ubuntu's out-of-the-box sound setup, using ESD. That includes a lot of stuff running under Cedega. I can definitely play music and movies simultaneously without trouble. (I just tried it to make sure I wasn't hallucinating -- ABBA's *Dancing Queen* and Dave Chappelle's R. Kelly parody at the same time, wheee!)

The short story is that if it's not broke don't fix it. I think this HOWTO should be amended to say "If you have such-and-such a motherboard and sound chip, and you have problems with Ubuntu's out-of-the-box sound, try this."[/QUOTE]


I think your right!! I'll change the title:(

---

### Post by wylfing on 2005-11-01
[QUOTE=Kirzzy_Boy]IMHO I think it might have something to do with the actuall sound chip used by the MB manufacturer.[/QUOTE]

You are correct, it has everything to do with the specific sound chip. The nVidia sound system is just specs -- it's up to the motherboard manufacturers to contract with a chipmaker to create a chip that meets the spec. That means you'll end up with chips that implement things differently, and to different degrees of success.

[QUOTE=Dracontopes]Did you configure anything on your system to have simultanious sounds? Because it didn't work on my PC[/QUOTE]

I don't recall doing anything to "fix" it. However, my comments were a little off-base, because I'm not running that motherboard anymore [1]. Let me revise what I said by directing you back to the sound chip itself. Find out what driver it's using. Then search on that information to find out what kinds of settings are working for people. The asoundrc data above is not correct for all nforce2 sound, and for some people will produce garbly noise.

[1] I still have an nforce2 board, but it's a Gigabyte one. It's true with this board too, though -- if I plug that asoundrc data in, I will get noise.

---

### Post by Dracontopes on 2005-11-01
Thanks for your input wylfing. I set all options to the default ones (that is, how they were before doing this how-to) and now simultanious sounds work... Listening to a .mp3 in Totem and radion in Rhythmbox now works. :confused:

Oh well :eek::eek::cool:

---

### Post by wylfing on 2005-11-01
Great! Glad everything's working now :)

Anyway, I didn't mean to turn this thread into a smash-fest against the HOWTO. I only wanted to point out that this does not work for all nforce2 on-board sound setups.

---

### Post by poptones on 2005-11-02
*You are correct, it has everything to do with the specific sound chip. The nVidia sound system is just specs*

This is not correct. I have a motherboard with NForce sound on board. I bought this motherboard *explicitly* because it has on board NForce sound (and, in the case of this motherboard, dual VGA output). This is sound hardware *built into the chipset* on motherboards with the MCP-T Northbridge, and that core sound functionality does not rely on the codecs used to interface the hardware functionality of that chipset to the analog world. 

Getting this stuff to work on linux (and especially ubuntu), however, seems to be a  mystery.

---

### Post by Kirzzy_Boy on 2005-11-02
[QUOTE=wylfing]Great! Glad everything's working now :)

Anyway, I didn't mean to turn this thread into a smash-fest against the HOWTO. I only wanted to point out that this does not work for all nforce2 on-board sound setups.[/QUOTE]

You didn't :smile: 
These forums are for interactive help as far as I know, so all input is a help! :p

---

