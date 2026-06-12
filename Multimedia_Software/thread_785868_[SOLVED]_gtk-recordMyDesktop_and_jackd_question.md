---
title: "[SOLVED] gtk-recordMyDesktop and jackd question"
date: 2008-05-07
forum: Multimedia Software
---

### Post by Rytron on 2008-05-07
Hi,
On gtk-recordMyDesktop, I go to Advanced > Sound Tab > Tick 'Use Jack for audio capture'

I have a microphone connected to the pc.

When I run gtk-recordMyDesktop I get this error message 'exited with status 256 error while parsing the arguments'.

Through trial and error I noticed that there are no errors when I untick 'Use Jack for audio capture' and then run gtk-recordMyDesktop.
In the available ports box, it says 'make sure jackd is running'. I have jackd installed in symantic. How do I make sure jackd is running? I went to terminal > jackd. It starts up but I don't know how to run it. 

Please help.
Thanks.

---

### Post by Rytron on 2008-05-10
I came across this:

start the Jack server. Either from terminal:

```
jackd -R -d alsa
```

or with the gui:

```
sudo apt-get install qjackctl
```

---

