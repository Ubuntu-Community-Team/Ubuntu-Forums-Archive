---
title: "Teamspeak 3 and WINE"
date: 2010-01-06
forum: Multimedia Software
---

### Post by Objekt on 2010-01-06
Has anyone tried the Teamspeak 3 beta?  They released clients and servers for Windows, Linux, and Mac, but there is a huge problem with the Linux client.  Because of a deficiency in a supporting library for Pulseaudio, the Linux uses near 100% of your CPU most of the time, making it impossible to do anything else, such as play a game.

Since Pulseaudio is now the default sound implementation for Ubuntu, this creates a large problem for us Ubuntu users who want to use TS3 while playing a game (e.g. Urban Terror).  We can't.  I haven't yet figured out an effective way to NOT use Pulseaudio, since it's so tightly integrated with Gnome.

I tried installing the Windows TS3 client via WINE, but it doesn't run.  The installer offers no complaints, but when I try to run the WINE install of TS3, nothing happens.  Has anyone gotten it to work?

The Windows Teamspeak 2 client works just great through WINE, so I was hoping that would work with TS3 too.

---

### Post by spimby on 2010-02-09
I've been having problems with Teamspeak 2.0 on 9.10.  It works ok, but it has these huge fonts which I've never had before on previous versions of Ubuntu.  They're so big I can't even see the interface.

For using TS3 with Wine, when I run it in the terminal, it looks like it needs a bunch of .dll's.  Irfanview does the same thing (Installs fine but doesn't do anything when you try to run it).  If you add the missing mfc42.dll to the .wine c/Windows directory, it works fine.  So...Looks like for TS3, you need to get the following files and move them into the ~.wine/drive_c/windows folder.  Then you will move past the initial *blank stare* to either a working TS3 or a new problem ;)

MSVCP90.dll
QtCore4.dll
Microsoft.VC90.CRT
QtGui4.dll
QtNetwork4.dll

---

### Post by Neiklot on 2010-03-22
Hey you guys, whats the latest on TS3 ?? 

I recently tried installing the .run that i downloaded off of their main site. I didnt get anywhere though! Could you guys give me a hand with it? thanks!

---

### Post by xhalarin on 2010-03-22
I am successfully using the Linux client.  It doesn't consume a ton of CPU either.  Keep in mind that it is still in Beta and they have been releasing frequent updates.

To install it, you need to ensure the .run file has execute permissions.  Then run it from the command line (ie ```
$ ./TeamSpeak3-Client-linux_x86-3.0.0-beta17.run
```)

You may want to play around with the sound driver settings on the Capture options tab.  You can specify ESD, Alsa, or OSS.  It may behave differently depending on what one is chosen.  ESD is the highest level wrapper so you might want to start there, then Alsa and OSS (not recommended) last.

---

### Post by Objekt on 2010-03-23
No dice.  Choosing the ESD options mean my mic doesn't work.  Using ALSA makes TS3 work and not use 100% CPU, but...and this is a HUGE but...I get no sound in Urban Terror.

I do get sound in other apps, like Rhythmbox.  That makes no sense.

As soon as I switch TS3 back to PulseAudio (what it really means when you pick "Automatically use best mode" for capture & playback in TS3), I get sound in Urban Terror once again, but CPU use goes through the roof.

I can't win either way.

---

### Post by Objekt on 2010-04-20
I don't know if it was the latest beta (10073) or my move to a realtime Linux kernel (2.6.31-9-rt), but TS3 no longer consumes 100% of CPU cycles.  I can even play games at the same time without framerate drops.  I'm marking this one solved.

---

### Post by aphixnet on 2012-04-06
This does not work for me :(

I tried some things and it turns out, that I can either hear Wine or TS/Ubuntu. What kind of Ubuntu app doesn't matter. Even with the rt kernel it does not work together. What works is two different outputs seperated. So, my usb headset can play game sound and the sound card plays TS - or vice versa.

Any ideas?

---

