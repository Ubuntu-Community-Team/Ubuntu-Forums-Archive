---
title: "PulseAudio Equalizer"
date: 2012-12-29
forum: Multimedia Software
---

### Post by mayagrafix on 2012-12-29
I'm looking for equalizer software to fine tune my music played through an external amplifier. I found this software: -PulseAudio Equalizer- but don't know if it works with U-12.10 and it is not supported anymore.

Does anyone know if it will work with 12.10 or is there a better solution?

Thanks for any and all information.:KS

---

### Post by Docaltmed on 2012-12-29
I couldn't get it to work as far back as 11.10.

---

### Post by mayagrafix on 2012-12-29
I was afraid of something like that would happen. So any other suggestions?

---

### Post by cwsnyder on 2012-12-29
In the Ubuntu Software center, there is the LV2 equalizer (package eq10q) which has no reviews.  There is also Tom's Audio Processing LADSPA plugins for Ardour or similar LADSPA compatible audio source which so far has 5 stars, but only one review.

---

### Post by mmstick on 2013-04-10
I got it working in Ubuntu 13.04. I imagine it works on every version prior as well.

```
sudo add-apt-repository -y ppa:nilarimogard/webupd8; sudo apt-get update -y; sudo apt-get install -y pulseaudio-equalizer; mkdir -p ~/.pulse/presets; pulseaudio-equalizer-gtk
```

 
It doesn't work unless you manually create that directory above, else the GUI will refuse to launch. Quite the programming error, but the Ubuntu community just doesn't see much use for a pulseaudio-equalizer, despite how critically useful this is in getting the most out of your sound equipment.

Just remember to adhere to Subtractive EQ, as it is never good to increase dB higher than 0.

---

### Post by Pablo Daniel on 2013-05-19
Hello! Seeking for problems in pulseaudio-equalizer i found a good solution for the problem. Pulseaudio-equalizer was not working in Ubuntu 13.04, that its installed in my machine.

The equalizer for pulseaudio not installed well in ubuntu 13.04 because it was designed to run until such time ubuntu 12.04.

The solution I found is:

go to the terminal, type and hit enter:

sudo add-apt-repository ppa: psyke83/ppa

(This command searches the repository, called PPA where this pulseaudio equalizer, but it will not find the file)

sudo apt-get update

Reboot the system after.

The solution is to search the site ppa: psyke83/ppa in google and get pulseaudio-equalizer first:

[http://ppa.launchpad.net/psyke83/ppa/ubuntu/pool/main/p/pulseaudio-equalizer/pulseaudio-equalizer_2.7_all.deb](http://ppa.launchpad.net/psyke83/ppa/ubuntu/pool/main/p/pulseaudio-equalizer/pulseaudio-equalizer_2.7_all.deb)

Once downloaded this file, you need to install two units:

ladspa-sdk
swh-plugins

From where to get:

Ubuntu Packages looking Raring:

[http://ubuntu.mirror.cambrium.nl/ubuntu//pool/universe/l/ladspa-sdk/ladspa-sdk_1.13-1ubuntu1_i386.deb](http://ubuntu.mirror.cambrium.nl/ubuntu//pool/universe/l/ladspa-sdk/ladspa-sdk_1.13-1ubuntu1_i386.deb)

[http://mirror.anl.gov/pub/ubuntu//pool/universe/s/swh-plugins/swh-plugins_0.4.15+1-7_i386.deb](http://mirror.anl.gov/pub/ubuntu//pool/universe/s/swh-plugins/swh-plugins_0.4.15+1-7_i386.deb)

When trying to install with Gdebi, you may ask the other files and do not install them. In  that case you need to open pulseaudio-equalize and allow the system to  download and install the files by pressing install the machine connected  to the network. When installing the program everything seems normal
but the run does not work. These are the causes and how the fix:

File-pulseaudio  pulseaudio-equalizer equalize installed and pulseaudio-equalizer-gtk in  usr / bin, with presets files in share / pulseaudio-equalizer,  containing the configuration of the sound system. The  system when trying to run, look at the user account to search the  hidden folder. / Pulse, to find the same configuration does not exist.
To  create it you should go to Nautilus, preferences, and choose to show  hidden files, close and reopen it to see the hidden files. Then you can create a new folder called. / Press. and left open nautilus

The system also seeks the. / Presets, which should be in / home / user account /. / Press / presets, which will be empty. To copy the files you requested, open pulseaudio-equalizer_2.7_all.deb with archive manager:

Then go open each folder to this location / usr / share / pulseaudio-equalizer. Here you will find the presets folder, which is precisely where the program asks. It can be extracted to the folder / home / user account, and from there copy it to the folder. / Pulse, and stay well:

/ Home / user account. / Press / presets

The  system installs a file called pulseaudio-equalizer.py in the / usr /  share / pulseaudio-equalizer, and this tells how to run the equalizer.
The script looks for a file called gnome-volume-control.svg in this folder, but the file is not found.
Inside  the terminal, it should execute the command: sudo nautilus, then type  your password and search for this file in the folder usr / share /  pulseaudio-equalizer and open with gedit for editing.
Once you open the file with gedit by double clicking within the pulseaudio-equalizer.py file to look for this line:

icon = self.window.set_icon_from_file ("/ usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg")

Changing to this location:

icon = self.window.set_icon_from_file ("/ usr/share/icons/Humanity/apps/16/gnome-volume-control.svg")

Close the file and all open windows and open the program from unity dash looking pulseaudio-equalizer. These steps solve the problem as the author of the program designed a version for Ubuntu 13.

---

### Post by Pablo Daniel on 2013-05-19
I forgot one thing: the home folder for the pulse folder is /home/user/./pulse/presets.

---

### Post by mmstick on 2013-05-19
For Ubuntu 13.04 and 13.10 you are better off with qpaeq.

[http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html](http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html)

Very easy to configure and an infinite number of bands.

---

