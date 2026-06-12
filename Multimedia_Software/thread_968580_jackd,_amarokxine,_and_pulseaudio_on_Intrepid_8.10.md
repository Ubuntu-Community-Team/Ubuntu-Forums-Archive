---
title: "jackd, amarok/xine, and pulseaudio on Intrepid 8.10"
date: 2008-11-02
forum: Multimedia Software
---

### Post by neltnerb on 2008-11-02
This post is an update to the work I and others did on Hardy Heron.

First, I can verify that everything we did previously to make pulseaudio sink to jackd still works like a charm. Simply download and install the debian sid pulseaudio jackd output plugins:

[http://packages.debian.org/sid/i386/pulseaudio-module-jack/download]("http://packages.debian.org/sid/i386/pulseaudio-module-jack/download")

After installing this, you will be able to load the jack output modules. These work fine for me under Intrepid.

You can load them with the following script contributed by markbuntu

```

#load pulseaudio jack modules
#!/bin/sh

pactl load-module module-jack-sink
pactl load-module module-jack-source

```

I put this in a script /usr/local/bin/jackload. Just run this after you start up jackd and it will load the modules. You can unload them similarly.

As far as xine/jackd goes, I duplicated the work I did on the Hardy version and managed to get it to produce a working output plugin. It was sort of a pain, and I didn't carefully document my steps, but it works fine. Just take the attached file and install it with:

```

tar -xjf xineplug_ao_out_jack.so.tar.bz2
sudo cp xineplug_ao_out_jack.so /usr/lib/xine/plugins/1.24/

```

After that, xine should immediately recognize jack as an audio output device.

---

