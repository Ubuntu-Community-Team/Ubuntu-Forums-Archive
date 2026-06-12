---
title: "Will VocProc work with ubuntu 10.04?"
date: 2011-10-18
forum: Multimedia Software
---

### Post by carrie.kandira on 2011-10-18
I was wondering if the vocproc with autotune will work in Ubuntu 10.04? And if so what program will it work with? 




Thank you for your help in advance! :)

---

### Post by gbd on 2011-11-04
Should do. I use Ardour, available from Synaptic.

---

### Post by carrie.kandira on 2011-11-05
Hmm, what's that exactly?

---

### Post by gbd on 2011-11-05
Just trying to recall 10.04, um... in System->Administration->Synaptic Package Manager.

You need to install Ardour, ubuntustudio-audio-plugins (which should include VocProc) and any other audio plugins you want. Ardour is a Digital Audio Workstation, where you can record and edit multi-track sound. Synaptic should ask to install anything else needed to make Ardour work. If you're unsure there should be an install guide somewhere, Google is your friend. Here's one I found in a few seconds you may be able to adapt...

[http://www.audiorecording.me/free-daw-digital-audio-workstation-software-install-ardour-in-linux.html](http://www.audiorecording.me/free-daw-digital-audio-workstation-software-install-ardour-in-linux.html)

Before you start Ardour you need to run Qjackctl (should be installed by Synaptic as part of Ardour) and you may need to tweak the settings to make it work on your system. (Google again...) Qjackctl is the front-end for the engine that runs audio processing for tasks like recording.

After that you add VocProc as a plugin to the vocal track you want to autotune and tweak accordingly.

I'll keep checking in.

---

### Post by gbd on 2011-11-05
Here's a link showing how to add plugins to Ardour tracks once you're up and running...

[http://www.audiorecording.me/how-to-add-use-and-install-ardour-plugins-in-linux-ubuntu.html](http://www.audiorecording.me/how-to-add-use-and-install-ardour-plugins-in-linux-ubuntu.html)

---

