---
title: "[SOLVED] Hardy Video Playback"
date: 2008-06-02
forum: Multimedia Software
---

### Post by emid on 2008-06-02
I just upgraded to Hardy 64bit from Gutsy 64bit (through the update-manager).  I can't seem to play video files anymore.  I think I have all the proper packages downloaded, but clearly something is wrong.  AVI's, WMV's, and MPG's all don't work.  When I try to play them Totem prompts me to search for the proper codec, but the search always comes back empty.

Does anyone know of a solution for this?

---

### Post by emid on 2008-06-02
Just wanted to add that on avi's I seem to hear the audio, even though there is no video.

---

### Post by emid on 2008-06-03
C'mon, clearly someone more clever than I knows the answer! :)

---

### Post by Kaneda187 on 2008-06-03
I dont know the answer, sorry!:( 

I suggest a fresh install though, as I have heard of countless problems regarding upgrading! just tryin to help:)

Good luck buddy!

---

### Post by emid on 2008-06-03
> **Kaneda187 said:**
> I dont know the answer, sorry!:( 

I suggest a fresh install though, as I have heard of countless problems regarding upgrading! just tryin to help:)

Good luck buddy!

NEVER!:)

Seriously, I dread the thought of a fresh install.  I've had this install going since Feisty, and I'm way too lazy to set everything up again from scratch.

---

### Post by lswest on 2008-06-03
try doing:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

then do:
```
sudo apt-get install --reinstall ubuntu-restricted extras
```

and finally:
```
sudo apt-get install libdvdcss2
``` see if that helps.

---

### Post by emid on 2008-06-03
> **lswest said:**
> try doing:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

then do:
```
sudo apt-get install --reinstall ubuntu-restricted extras
```

and finally:
```
sudo apt-get install libdvdcss2
``` see if that helps.

I'd already had the medibuntu repo set up from my earlier attempt to fix this problem.  I tried the reinstall that you suggested but it didn't work.

I'm assuming that this:

```
ubuntu-restricted extras
```

was meant to be this:

```
ubuntu-restricted-extras
```

Is there some way to erase all codecs and go back to the default state? (Not a fresh install though:))  Maybe then I could go about installing codecs normally.  I still don't understand why when it prompts me to search for a codec it finds nothing.

Thanks for the suggestion though.

---

### Post by lswest on 2008-06-04
yeah, sorry for the typo, i was really tired when i wrote that :P  You can just remove the codecs manually using synaptic package manager or aptitude/apt-get.  Might be a lot of work, but it may work

Oh, also: make sure your universe and multiverse repositories are enabled.  Check under system-->administration-->software sources

---

### Post by emid on 2008-06-04
I found the answer on this thread:

[http://ubuntuforums.org/showthread.php?t=775943]("http://ubuntuforums.org/showthread.php?t=775943")

Not sure why I didn't find it until just now.  :)

Basically you just uninstall all the "libx264" related packages in synaptic, then reinstall the newest version.  I guess when I upgraded it didn't uninstall the old version while installing the newer version.

---

