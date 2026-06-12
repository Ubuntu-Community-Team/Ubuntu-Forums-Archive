---
title: "Technisat CableStar2 &amp; remote"
date: 2006-07-13
forum: Multimedia &amp; Video
---

### Post by Matti on 2006-07-13
Hi everyone

I've got a Technisat CableStar2 DVB card working nicely with Ubuntu Dapper, but I can't get the remote control to work. If anyone has a remote like this, please give me some advice how to use it with linux. It works ok with WinXP. I think the SkyStar2 has a same kind of serial port IR remote (TTS35AI). I tried to follow different lirc howtos, but with no success.

Oh, if you're wondering how to get the card working, I used an older development snapshot from linuxtv.org. The current version seems to be useless for CableStar2.

You can get the version I used from here (just click *bz2*): [http://linuxtv.org/hg/v4l-dvb?cmd=changeset;node=c7e2369ad0cb]("http://linuxtv.org/hg/v4l-dvb?cmd=changeset;node=c7e2369ad0cb")

---

### Post by dinoj on 2006-07-19
Hi Matti,
I also have this card, and work very nice with hg-v4l-dvb-7b2efa772750. 
My card is using remote  model 100TS035 
First You must set serial mode:
setserial /dev/ttyS0 uart none
(or /dev/ttySX - where X is the port number)
and then load lirc_serial module
Then I start command mode2 and I see that I have communication.
I copy   100TS035 file ( [http://lirc.sourceforge.net/remotes/technisat/100TS035](http://lirc.sourceforge.net/remotes/technisat/100TS035))  as /etc/lirc/lircd.conf (or You can get technisat.conf file from Windows DVBViewer).
I have compile lirc from source, and I make script in /etc/init.d to setserial, and load lirc_serial. 
My favorite program is  xine, and I create .lircrc in my home directory with something like this:

..............
...............
begin
        remote =  100TS035
        button = RIGHT
        prog   = xine
        repeat = 0
        config = Volume+
end


begin
        remote =  100TS035
        button = LEFT
        prog   = xine
        repeat = 0
        config = Volume-
end

# audio muting toggle
begin
        remote =  100TS035
        button = MUTE
        prog   = xine
        repeat = 0
        config = Mute
end

begin
        remote = 100TS035
        button = UP
        prog   = xine
        repeat = 0
        config = NextMrl
end

begin
        remote =  100TS035
        button = DOWN
        prog   = xine
        repeat = 0
        config = PriorMrl
end

...........................
...........................
The remote and button values You can get from /etc/lirc/lircd.conf file. For More options check lirc and player documentations. 
Good luck!

---

