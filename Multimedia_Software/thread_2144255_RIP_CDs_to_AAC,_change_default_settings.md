---
title: "RIP CDs to AAC, change default settings"
date: 2013-05-11
forum: Multimedia Software
---

### Post by sdato on 2013-05-11
Hello,

I am running Ubuntu 13.04 x64 and I am trying to RIP audio CDs to AAC using Rhythmbox, I already installed gstreamer and faac and I can select to rip to MPEG4 under Rhythmbox preferences but I cannot change the default settings. By default it will RIP the CDs at 128000 bitrate, this is what I want to change to 256000. I already tried using gconf-editor to edit the preferences in the AAC profile but no luck. I am not new to Ubuntu and in the past I used to RIP my CDs to OGG but my wife got an stupid iPhone and it does not reads OGG and I do not like the gap between tracks usually found in MP3 files.

Any help will be much appreciated.

---

### Post by shantiq on 2013-05-12
hi sdato

i have no experience of Rhythmbox
but there is a handy way to get your 256 rips done in Ubuntu if a terminal solution is cool with you :KS

```
sudo apt-get install ripit
```
then go to the config

```
gedit .ripit/config
```

run find    "ctrl+f" enter quaffaac  and change to  quaffaac=**300**     [this will be around 256 kbps]     and save file   [only needs to be done once]

then place disc in drive and run

```
ripit -c 3  1-13  -o ~/Music --eject --save
```

and find your tracks in Music folder 
track numbers can be written as   3,4,5,6   or  3-6   detailed info [here]("http://en.digipedia.org/man/doc/view/ripit.1/")
-c 3 asks for faac encoder
1-13   are the tracks i wanted in this case

PS  use **mediainfo** to check kbps as right-click/properties will "lie"

---

### Post by Yellow Pasque on 2013-05-12
gconf system has moved to dconf, but I don't think the gnome media settings are even kept there anymore. They're probably in some unintuitive, hidden file (GNOME devs don't like to offer settings to their users).

This might still work:
```
sudo apt-get install gnome-media-profiles
gnome-audio-profiles-properties
```

---

### Post by speartip on 2013-05-13
This is the way I rip cds to aac.
Download the Nero aac codec from here to your desktop:
[http://www.softpedia.com/progDownload/Nero-Digital-Audio-Download-43050.html](http://www.softpedia.com/progDownload/Nero-Digital-Audio-Download-43050.html)
Extract the file, & enter the folder. Go into the Linux folder, where you will find neroaacdec, neroaacenc & neroaactag.
Open a terminal in that folder & issue the command:
```
[FONT=verdana][SIZE=2][COLOR=#000000]sudocp neroAacDec neroAacEnc neroAacTag /usr/bin[/COLOR][/SIZE][/FONT]
```
then:
```
[FONT=verdana][SIZE=2][COLOR=#000000]cd/usr/bin[/COLOR][/SIZE][/FONT]
```
and:
```
[FONT=verdana][SIZE=2][COLOR=#000000]sudochmod +x neroAacDec neroAacEnc neroAacTag[/COLOR][/SIZE][/FONT]
```
Then install the best Linux cd ripper (imo) Rubyripper from here:
[http://www.ubuntuupdates.org/package/getdeb_apps/raring/apps/getdeb/rubyripper](http://www.ubuntuupdates.org/package/getdeb_apps/raring/apps/getdeb/rubyripper)
Use either the apt install or the .deb install.
When installed open up Rubyrippers preferences, go to codecs, & make sure the "other" box is the only one ticked.
In the command line for "other" paste this command:
```
[FONT=verdana][SIZE=2][COLOR=#000000]neroAacEnc-q 0.75 -if %i -of %o.m4a && neroAacTag %o.m4a-meta:artist=%a -meta:album=%b -meta:genre=%g -meta:year=%y-meta:track=%n -meta:title=%t[/COLOR][/SIZE][/FONT]
```
You should now be able to rip your cds to aac with a quality of about 275kbps.
Hope this helps.

---

### Post by Patrick Ruymaekers on 2013-06-05
I am using abcde ripper at moment. [http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)   This link gives bit of info about modifying its config file

---

### Post by andrew.46 on 2013-06-06
> **Patrick Ruymaekers said:**
> I am using abcde ripper at moment. [http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)   This link gives bit of info about modifying its config file

Nice page :)

---

