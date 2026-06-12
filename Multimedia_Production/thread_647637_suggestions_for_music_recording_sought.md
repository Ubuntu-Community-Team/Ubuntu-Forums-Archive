---
title: "suggestions for music recording sought"
date: 2007-12-22
forum: Multimedia Production
---

### Post by scholzilla on 2007-12-22
I'm looking to do some recording, first of just electric geetar and vocals and then probably more tracks for low-fi recordings in our practice space. I don't know a thing about using a computer to record music and was hoping I could get gear/software suggestions here. I've heard good things about audacity and line6.....

About my box:

OS: gutsy
processor: dual AMD Turion 64bit TL-52
sound capture: ALSA
mixer: hda ati sb
plenty o' disk space

I'd be interested in your opinions, at least the ones relevant to this post

cheers

---

### Post by Lagos on 2007-12-22
install Ardour Gtk2 from the package manager. its a nice multi track recording app.

---

### Post by scholzilla on 2007-12-22
Thanks for the response. Any other votes?

---

### Post by Stochastic on 2007-12-23
ardour is definitely the best for recording, though it make take a bit of learning.
audacity has some good points for beginners, as does jokosher.
rezound is also good and stable.
and I'd HIGHLY recommend using JACK for your audio capture rather than alsa.
As for hardware, it all depends on your budget.  I'd check the hardware listings at the ALSA website and the FFADO website to make sure anything you buy is compatible before spending the dough.

---

### Post by scholzilla on 2007-12-23
Thanks for that. If you don't mind, what's the advantage of JACK over ALSA?

---

### Post by kayosiii on 2007-12-25
Jack is designed with professional audio use in mind and many sound apps will not work or will work with reduced functionality without running jack - easiest way is to install and run qjackctl.... It will sit quite happily ontop of your alsa drivers.

The other bonus with jack is you can route the audio outputs of any jack enabled app into the inputs of any other jack enabled app. Best interface for routing would have to be patchage - so install that too.

As for gear - check ffado or alsa web sites.... I have an external firewire soundcard that works with linux (presonus firebox) and am very happy with it.

---

### Post by FakeOutdoorsman on 2007-12-26
I'll give you some guitar specific recommendations:

[creox]("http://zyzstar.kosoru.com/?creox") - Creox is a real-time sound processor. You can plug your electric guitar or any other musical instrument directly to the PC's sound card and start experimenting with various sound effects. Creox has a nice user-friendly GUI, a preset support, a low-latency DSP engine and each effect parameter can be altered "on the fly". [from the creox site]

[gtkguitune]("http://www.geocities.com/harpin_floh/kguitune_page.html") - guitar and other instrument tuner.

[SimulAnalog]("http://www.simulanalog.org/guitarsuite.htm") - simulates guitar amps.  (Also see this thread:  [Software Monitoring in ArdourVST]("http://ubuntuforums.org/showthread.php?t=501163")).

...and also [Hydrogen]("http://www.hydrogen-music.org/") drum machine.  It's easy to use and sounds good too.

You may be interested in Ubuntu Studio.  It come preinstalled with many popular linux audio programs to play with.  Here is the [list of Ubuntu Studio programs]("https://wiki.ubuntu.com/UbuntuStudio/PackageList").

And finally, read through these threads for opinions and recommendations on other programs:
[Music production - where to start?]("http://ubuntuforums.org/showthread.php?t=442307")
[Ubuntu Musicians(?)]("http://ubuntuforums.org/showthread.php?t=11857")

---

