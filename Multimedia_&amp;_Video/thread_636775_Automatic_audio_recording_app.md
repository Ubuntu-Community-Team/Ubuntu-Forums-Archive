---
title: "Automatic audio recording app?"
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by jnoreiko on 2007-12-10
I need a way of recording audio automatically.

I have an audio signal coming into my soundcard's line in, and I need to save this, ideally as one file for each hour, in mp3, but I can live with other formats.

It's for an archiving system at a radio station, so it needs to run continuously, without any input, so maybe a sound recording application that can take command line input and be run from cron?
Any suggestions for what to use?

I'd read about using streamripper to save the audio at the same time as we stream it to the internet, and I set this combination up on a test machine. But if the internet connection dies (our broadband is flaky), the mp3 filesize stops increasing -- I'm guessing the icecast source stops sending data, so streamripper has nothing to save any more.

---

### Post by edm1 on 2007-12-10
I was going to suggest streamripper. If the computers are on the same network could you not connect to the stream directly rather then going via the internet. Wouldnt matter if you're broadband went down then.

---

### Post by jnoreiko on 2007-12-10
The Icecast server is in a completely different physical location.

In my test setup I had streamripper connect to localhost:8000 so it picks up what MuSE (the icecast source) is sending out, on the same machine -- but it looks like if the internet connection to the icecast server is lost, then that goes too.

---

### Post by theorganloft on 2007-12-10
> **jnoreiko said:**
> I need a way of recording audio automatically.

I have an audio signal coming into my soundcard's line in, and I need to save this, ideally as one file for each hour, in mp3, but I can live with other formats.

It's for an archiving system at a radio station, so it needs to run continuously, without any input, so maybe a sound recording application that can take command line input and be run from cron?
Any suggestions for what to use?

I'd read about using streamripper to save the audio at the same time as we stream it to the internet, and I set this combination up on a test machine. But if the internet connection dies (our broadband is flaky), the mp3 filesize stops increasing -- I'm guessing the icecast source stops sending data, so streamripper has nothing to save any more.

The latest version of Audacity does scheduled recording.

---

### Post by jnoreiko on 2007-12-10
> **theorganloft said:**
> The latest version of Audacity does scheduled recording.

Hey that's pretty cool!
But it won't save the file too as far as I can tell?

This system needs to record audio 24/7 -- it's a legal requirement in the UK to keep an archive of all our FM radio output for 6 weeks so this thing needs to stay up all the time.

---

### Post by jnoreiko on 2007-12-18
For anyone finding this thread in a search...

I've found darkice does the job very nicely. More than that, it streams and saves an archive simultaneously (or can do just one of those).
More info here: [http://darkice.tyrell.hu/trac/wiki/Archiving](http://darkice.tyrell.hu/trac/wiki/Archiving)

---

