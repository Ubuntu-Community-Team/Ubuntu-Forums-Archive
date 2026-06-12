---
title: "vsthost"
date: 2008-04-11
forum: Multimedia Production
---

### Post by DevilFish101 on 2008-04-11
I'm having problems with using VSTis with vsthost... I've looked elsewhere, but the only thing I could find advocated a serious downgrade of jack, so I thought it better to ask here before risking that... I have the newest version of jack, alsa, etc... Forgive my n00bery, but... What do I do? 
Here's what I get when I try running one...

nick@nick:~$ vsthost /home/vst/Crystal.dll
Returning file identifiers: gQaKKNhyhKGMnIHKCLCgjLyK
DSSI_PATH not set, defaulting to /home/nick/.dssi:/usr/local/lib/dssi:/usr/lib/dssi
RemoteVSTClient: executing /usr/local/lib/dssi/dssi-vst/dssi-vst-server -g /home/vst/Crystal.dll,gQaKKNhyhKGMnIHKCLCgjLyK
DSSI VST plugin server v0.986
Copyright (c) 2004-2006 Chris Cannam - Fervent Software
Loading "/home/vst/Crystal.dll"... 
VST_PATH not set, defaulting to /home/nick/vst:/usr/local/lib/vst:/usr/lib/vst
dssi-vst-server[1]: not found in /home/nick/vst//home/vst/Crystal.dll
dssi-vst-server[1]: not found in vst//home/vst/Crystal.dll
dssi-vst-server[1]: not found in /usr/local/lib/vst//home/vst/Crystal.dll
dssi-vst-server[1]: not found in /usr/local/lib/vst//home/vst/Crystal.dll
dssi-vst-server[1]: not found in /usr/lib/vst//home/vst/Crystal.dll
dssi-vst-server[1]: not found in /usr/lib/vst//home/vst/Crystal.dll
dssi-vst-server[1]: found in DLL path
done
Testing VST compatibility... 
dssi-vst-server[1]: VST 2.4 entrypoint "VSTPluginMain" not found in DLL "/home/vst/Crystal.dll", looking for "main"
dssi-vst-server[1]: VST entrypoint "main" found
dssi-vst-server[1]: plugin instantiated
dssi-vst-server[1]: plugin is a VST
dssi-vst-server[1]: plugin has a GUI
dssi-vst-server[1]: plugin supports processReplacing
dssi-vst-server[1]: opening plugin
dssi-vst-server[1]: plugin is VST 2.0 or newer
dssi-vst-server[1]: plugin is a synth
dssi-vst-server[1]: plugin name is "Crystal"
dssi-vst-server[1]: vendor string is "Green Oak Software"
Initialising Windows subsystem... 
dssi-vst-server[1]: registered Windows application class "dssi_vst"
dssi-vst-server[1]: created main window
dssi-vst-server[1]: sized window
dssi-vst-server[1]: showed window
done
dssi-vst-server[1]: created audio thread
Failed to set realtime priority for audio thread: Operation not permitted
vsthost: signal 17 received, exiting
ERROR: Remote VST plugin communication failure
Remote VST plugin audio thread: returning
nick@nick:~$ dssi-vst-server[1]: cleaning up
dssi-vst-server[1]: closed audio thread
dssi-vst-server[1]: freed dll
dssi-vst-server[1]: exiting

---

### Post by aeiah on 2008-04-11
well its saying the opperation is not permitted. the first things id do would be to check if you have a real time kernel, and also try running it with sudo vsthost /home/vst/Crystal.dll

---

### Post by DevilFish101 on 2008-04-11
I'm using the realtime kernel, and sudo made no difference... Any thoughts?

---

### Post by thorgal on 2008-04-12
check this file : /etc/security/limits.conf

this is what I have at the bottom of it :

@audio - rtprio 99
@audio - memlock unlimited
@audio - nice -19

It means that because I belong to the unix group audio, I am allowed to run processes with RT priv (i.e. not as root! don't do that by the way)

If you don't have this setting, I suggest you copy paste it, log out and log in again.

---

### Post by DevilFish101 on 2008-04-12
No luck there...
I tried it with @audio and @nick, and both ways nothing...

---

### Post by thorgal on 2008-04-12
can you start jackd with the realtime option enabled ?

also, type 'id' in a shell and check that you belong to the audio group.

---

### Post by DevilFish101 on 2008-04-12
I think I may have been being stupid; does vsthost depend on jackd?
Also, if I don't belong to @audio, what should I do?

---

### Post by DevilFish101 on 2008-04-12
Wait, I do belong to it...

---

### Post by thorgal on 2008-04-12
hehe, of course you need jackd to be running! :lol:
so, fire up qjackctl, set it up in the setup window and start it.
then run vsthost.

---

### Post by motin on 2008-04-14
That doesn't help either... jack is running with realtime enabled but still the same problem. 

Which version of vsthost have you got running, those who has it up and running?

I have identical problems as the OP, and have dssi-vst_0.4-1_i386.deb installed.

---

### Post by thorgal on 2008-04-14
I use dssi-vst version 0.6 that I compiled myself. I never tried it with older versions.

---

### Post by motin on 2008-04-15
> **thorgal said:**
> I use dssi-vst version 0.6 that I compiled myself. I never tried it with older versions.

Thanks - it works great with 0.6

Installation:

1. Download dssi-vst v 0.6, unpack and cd into the directory
2. Install:
```
sudo apt-get install dssi-dev wine-dev liblo0-dev
make
make install
```

To run a vsti, for instance Crystal.dll, run:
```
VST_PATH=/path/to/vst/plugins jack-dssi-host dssi-vst.so:Crystal.dll
```

I use the following wrapper, saved as /usr/local/bin/vst.sh: 
```
#!/bin/bash
VST_PATH=/path/to/vst/plugins jack-dssi-host dssi-vst.so:"$1"
exit 0
```

And then run for instance:

```
vst.sh Crystal.dll
```

I can't start plugins that have spaces in their filename... for now I rename them to contain underscores instead. I guess there is a better way but this works for me atm.

---

### Post by thorgal on 2008-04-15
hey! great :)
you're right about spaces in filenames. I also found out the 1st time I tried ...
know that there's already a "wrapper" compiled with dssi-vst.so, it's called vsthost :)

The drawback is that it appends the process id to the jack client name. The reasoning is that you could run more than one instance without name collision. BUT! if you save an ardour session with connections to one of these instances, the day you reopen the ardour session, you will have a problem because the VSTi process id has changed ...

Either you do it your way (which always provide the same jack client name) or you apply my patch to the code for the vsthost app :

```

 --- vsthost.cpp 2008-01-07 12:35:35.000000000 +0100
+++ vsthost.cpp.new     2008-04-01 19:25:02.295594022 +0200
@@ -350,12 +350,14 @@

     for (i = 0; i < 20 && pluginName[i]; ++i) {
        if (isalpha(pluginName[i])) {
-           tmpbuf[j] = tolower(pluginName[i]);
+           //      tmpbuf[j] = tolower(pluginName[i]);
+           tmpbuf[j] = pluginName[i];
            ++j;
        }
     }
     tmpbuf[j] = '\0';
-    snprintf(jackName, 26, "vst_%s_%u", tmpbuf, getpid());
+    //    snprintf(jackName, 26, "vst_%s_%u", tmpbuf, getpid());
+    snprintf(jackName, 26, "%s_VST", tmpbuf);

     if ((jackData.client = jack_client_new(jackName)) == 0) {
        fprintf(stderr, "ERROR: Failed to connect to JACK server -- jackd not running?\n");

```

and apply like this  in the dssi-vst src directory:

```

patch -p0 < mypatch

```

after you had saved the patch into 'mypatch' (pure text file).

---

### Post by thorgal on 2008-04-15
by the way, I did not know this VST, sounds cool! :D

---

### Post by ethanay on 2008-05-25
> The drawback is that it appends the process id to the jack client name. The reasoning is that you could run more than one instance without name collision. BUT! if you save an ardour session with connections to one of these instances, the day you reopen the ardour session, you will have a problem because the VSTi process id has changed

has this been fixed in dssi-vst 0.7?

from the README:
>  * The vsthost program uses jack_client_open instead of
   jack_client_new, for more predictable client names.

---

