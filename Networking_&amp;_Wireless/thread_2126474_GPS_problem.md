---
title: "GPS problem"
date: 2013-03-17
forum: Networking &amp; Wireless
---

### Post by malodobry on 2013-03-17
Hello everyone,

Sience this is my first post i would like to take my time to say "hello" :) 

i got myself a shiny-new gsm.gps modem Dell 5550 aka 2XGNJ, installed it on my dell D630 and on windows it works without issues.
But not on Ubuntu 12.04 :(

Driver installed correctly, and automatically which is great.
I tried to turn on the GPS functionality, to do so i installed screen, than send AT commands to start gps feed on port
```

xxx@Lapek:~$ screen /dev/ttyACM2

*EMRDY: 1
AT+CFUN=1
OK
AT*E2GPSCTL=1,2,1
OK
AT*E2GPSNPD
OK


```

At this point i got something that looked like gps coordiantes feeding to console, so i happily killed it, started gpsd on /dev/ttyACM2, than attempted to run FoxtrotGPS to chack how it behaves, and got no input from gpsd.
So i killed it.
Now i checked if gps still writes on port by

```
cat /dev/ttyACM2
```
but there was only *EMRDY:1 there
tried using wvdial to do the job, but to no avail.
than i tried using echo to send commands directly to the serial port, they appear on cat, but coordiantes feed doesent start.

and now i just dont know what more could i do to make it work.
I will appriciate any sugestions.

Cheers :)

---

### Post by Herman on 2013-04-13
Hello malodobry and welcome,

I must be lucky with my hardware since all I needed to do was install gpsd and gpsd-clients and my USB GPS just works for me.

Another user called KBN80  outlined what looks to me like a nice logical procedure for getting almost any GPS device working in Ubuntu.
 It's a little hard to find because it's inside another thread,  here's a link: [USB DeLorme GPS on Ubuntu with gpsd]("http://ubuntuforums.org/showthread.php?t=1430516&p=11247253#post11247253")

Maybe you'll get some useful clues out of that, I hope it helps.

Regards, Herman

---

### Post by morgwai on 2013-07-12
Hey,
I was experiencing similar problems while playing with my Ericsson H5321 gw. It's a different card but maybe the reason of the problem is similar. It turned that my card enters stand-by mode when /dev/ttyACM2 is no longer opened (for power saving reasons) so you need to send initialization AT commands to it (AT*E2GPSCTL=x,y,z AT*E2GPSNPD) each time you want to read your position again. Unfortunately gpsd can not handle this automatically.
It also turned that my card is very strict about CRLF line endings so when I played manually with it and did just `echo "ATxxxx" >/dev/ttyACM2"` it didn't work. doing `echo -e "ATxxxx\r"` did the trick.

Hope this helps.

---

