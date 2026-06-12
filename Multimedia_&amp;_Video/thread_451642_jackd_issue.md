---
title: "jackd issue"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by Matthijs on 2007-05-22
hi there, 

With Ubuntu 6.04 i manually installed jackd to work with ardour2. But now in *feisty fawn*, jackd is installed via apt-get, and i think things went well. I can start jackd successfully with this command 'jackd -d alsa' 

But even when jackd is running i can **not** start ardour2..... It says jackd is not operating.  When i start ardour2 via the commandline, i notices this error... 
**'jackstart: md5 checksum for /usr/bin/jackd does not match'**
so... jackd is apparently not installed correctly..  Here is my dpkg -l output:
```

dpkg -l | grep jack
ii  jackd                                      0.102.20-1                                 JACK Audio Connection Kit (server and exampl
ii  liballegro4.2-plugin-jack                  4.2.0-5                                    JACK audio plugin for the Allegro library
ii  libjack0.100.0-0                           0.102.20-1                                 JACK Audio Connection Kit (libraries)

```

Any thoughts about doing the next step? Or does someone know a soulution for my problem? I'd be very happy if jackd is running, helps me forget those windows frustrations...

note: ardour2 would not compile as well, it could not find jack, so i installed ardour2 via the ubuntustudio repo. This was the error trying to compile jackd: 
[B]Checking for jack... no 
jack >= 0.101.1 not found.[/B]
Could it be a version problem?

thanks in advance!

Matthijs

---

### Post by Matthijs on 2007-05-25
Okay, i installed qjackctl. And with those setting i got ardour2 to work. topic should be closed

---

