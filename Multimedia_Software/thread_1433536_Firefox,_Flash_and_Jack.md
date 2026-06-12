---
title: "Firefox, Flash and Jack"
date: 2010-03-19
forum: Multimedia Software
---

### Post by kazakore on 2010-03-19
Anybody able to help me get my system working on all audio fronts?

Mainly used for music production and have now set it to kill PA (pulseaudio -k) and start the Jack server (qjackctl with auto-start on) at Start-up and can get my media players (VLC or MPlayer) working as well as my main host (Renoise) although not tried many other audio programs.

I installed GNOME-MPlayer and followed [these instructions]("http://sites.google.com/site/kdekorte2/gnomemplayer") hoping it would also use Jack but even if I drag a mp3 into Firefox it still plays no audio and it would never of worked with Flash for sites like Youtube from what I understand anyway. Seemed this was the more recomended way of doing it rather than install MPlayer Plugin For Firefox (which states it isn't maintained anymore and couldn't see the Gecko Media Player it mentions in the repository.)

Other searches brought up something called libjackasyn0 which sounded like it might work but couldn't find it in Synaptic.

Any suggestions what to try? I think I might of slightly screwed up PA stuff (remember following some instructions to get PA to output to Jack but never worked) but as it is killed at startup now hopefully that wont matter...

---

### Post by ajgreeny on 2010-03-19
Gecko-mediaplayer is certainly in the repos.  Check your search terms, and use gecko in the search box and it should appear; it certainly does in synaptic, which is what I always use to install packages.

I can't help with other jack problems, I'm afraid.  Pulse seems to work great for me with my hardware, so that is what I use.

---

### Post by Bucky Ball on 2010-03-19
I would personally get rid of the kill Pulseaudio at boot line and use Pulse and plug-ins. Turn on Jack manually when you want to do music production.

But that's me. Exactly what I do. I run Ubuntu Studio rt kernel and only use Jack when I need to for a particular software(s).

---

### Post by kazakore on 2010-03-19
> **Bucky Ball said:**
> I would personally get rid of the kill Pulseaudio at boot line and use Pulse and plug-ins. Turn on Jack manually when you want to do music production.

But that's me. Exactly what I do. I run Ubuntu Studio rt kernel and only use Jack when I need to for a particular software(s).

That's what I tried initially but found that on boot Firefox would work but then no matter what I did I could not get Jack to load without restarting the computer so thought I would try another way around it. Found having Jack locked out too annoying!

> **ajgreeny said:**
> Gecko-mediaplayer is certainly in the repos. Check your search terms, and use gecko in the search box and it should appear; it certainly does in synaptic, which is what I always use to install packages.


Gecko does appear in Synaptic, cheers, but it doesn't show in the Add/Remove Application, which is where I initially looked.

---

### Post by kazakore on 2010-03-19
Been finding myself too often wanting to watch quick bits on the 'net so have removed the "pulseaudio -k" and "qjackctl" from startup.

Any idea why I can't restart PA after having used Jack? If I try and run pulse-session it fails to start. Is there any kind of diagnostics I can run on this?

---

### Post by markbuntu on 2010-03-19
If you use pasuspender instead of pulseaudio-k then pulseaudio will suspend itself while jack is running and restore itself when jack is killed. 

This is the default setup in UbuntuStudio since 8.04 so unless you have been tinkering under the hood it should work that way.

There is another way around that which involves the pulse-jack modules which you have to get/build yourself. There is some threads around here about that.

---

### Post by Bucky Ball on 2010-03-19
> **kazakore said:**
> ... no matter what I did I could not get Jack to load without restarting the computer so thought I would try another way around it. 

On my machine, Apps->Multimedia->Jack Control and just start Jack. That easy. If you don't have Jack Control, install it. I am presuming you are booting Jack from a terminal. That GUI gives you all kinds of options.

---

