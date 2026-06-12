---
title: "I can't download mp3 plug-in!"
date: 2012-03-17
forum: Multimedia Software
---

### Post by Thebuntuway on 2012-03-17
HI there!..i just move from ubuntu 11.10 to kubuntu 11.10..these os was awesome. but there are trouble ahead when i tried to play a mp3 music and i was trying to download and install mp3-plugins. When i tried to open the muon software center, it said it was close unexpectedly and that was very annoying!. I know the main problem was the Muon Software center that i need to check the source code for third party software. How do i open the Muon Software center guys?..Help!!!

---

### Post by Yellow Pasque on 2012-03-17
Some workarounds are here:
[https://bugs.launchpad.net/ubuntu/+source/muon/+bug/915235](https://bugs.launchpad.net/ubuntu/+source/muon/+bug/915235)

---

### Post by SeijiSensei on 2012-03-18
Rather than using Muon, you can just install from the command line like this:

```
sudo apt-get install kubuntu-restricted-extras
```

Open a Terminal ("Konsole" in KDE) and type in the above command at the $ prompt.  You'll be asked for your password since sudo grants you administrative ("root") access to the machine.  kubuntu-restricted-extras includes the MP3 codec and many other things as well.  You'll be prompted to install the Microsoft TrueType fonts (like Verdana); when you're asked to accept the EULA, use the tab key to highlight the "OK" box, then hit Enter to confirm.

If you want a graphical package manager, I recommend Synaptic, even though it's a GNOME app.  Use "sudo apt-get install synaptic".  It will need to install a lot of "dependencies" but just say yes when prompted.

I like the Clementine player myself ("sudo apt-get install clementine").

---

### Post by Yellow Pasque on 2012-03-18
If going to install synaptic in KDE, minimize the dependencies with:
```
sudo apt-get install --no-install-recommends synaptic
```

---

