---
title: "TV tuner for a laptop"
date: 2011-02-01
forum: Multimedia Software
---

### Post by s1mp13m4n on 2011-02-01
Hello everyone.  I want to use my laptop for watching cable TV and as a DVR.  I need to buy a TV tuner card for the laptop.  What I want to know is what brands and cards work with Ubuntu 10.04?  Are they easy to install or so I need to be a CLI geek to make it work?

---

### Post by Chronon on 2011-02-03
There are a bunch of pages in the wiki here:
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia](https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia)

I'm not too certain of the purpose of those pages, though.  It doesn't seem like anybody has edited them since 2008 or so.

I use a WinTV HVR-950 from Hauppauge.  It didn't work out of the box when I first tried it with Hardy (had to manually install some firmware), but has been functional with drivers present in the kernel since Jaunty (IIRC).

I usually use SMPlayer or Kaffeine to watch TV.  Kaffeine has the advantage of a built-in tuning capability, while SMPlayer needs a channels.conf file to tell it what frequencies to tune to find available channels.  Both are GUI applications but you may need to run a utility from the command line to generate the channels.conf if you opt for SMPlayer.

--
Edit: I added my info to the Hauppauge page.  Hopefully people will take more interest in keeping the wiki updated.

---

### Post by jimmers on 2011-02-04
Hi,
I have been using an AverMedia Volar, Model No. A815 USB Tuner, Since Jaunty without any problems using Kaffeine, here in the UK it gives me 35 TV Channels and 25 Radio Channels, worked straight out of the box, except for the remote, but as I sit at my desk to watch, I don't need a remote.

Check it out, may be for you, may not.

Luck

---

