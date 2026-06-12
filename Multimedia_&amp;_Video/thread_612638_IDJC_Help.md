---
title: "IDJC Help"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by Kristopher on 2007-11-14
I am using Ubuntu 7,10 and started to look at IDJC. When i add mp3's or Oggs to my playlist and press play and listen....the audio is very stuttery at my end is this correct? I have still to add it to a shoutcast server to see if its the same there, but i thought i would check to see if this is correct or an issue.

Thanks

---

### Post by StephenF on 2007-11-15
You'll probably want to configure for real-time scheduling which is a lot easier than you might think.

With root privileges edit the file /etc/security/limits.conf and add the following lines.

```
@audio          -       rtprio          20
@audio          -       nice            -15
@audio          -       memlock         400000

```

Now log out of your user account and log back in again.

Type ulimit -r in a console. It should read 20 if it worked.

Now open up a text editor and create/modify ~/.jackdrc

Make it read something like this...

```
/usr/bin/jackd -t 25 -R -dalsa -dhw:0 -r44100 -p1024 -n2
```

Be sure to specify the correct sound card if you have more than one.

If you want lower audio latency you need only reduce the value of -p but note this risks increased audio "stuttering". All p values must be powers of 2 starting at something sensible like 32. 

Now run idjc.

For perhaps a further improvement you can run the rt kernel but that's a bit more involved.

---

