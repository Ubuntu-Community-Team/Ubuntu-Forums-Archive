---
title: "Rocklight plugin for xmms works only as root"
date: 2007-06-16
forum: Multimedia &amp; Video
---

### Post by holihue on 2007-06-16
Why doesn't rocklight work without root acces?

And what must I do to have it on a normal user?


Form [http://www.xmms.org/plugins.php?details=248#:]("http://www.xmms.org/plugins.php?details=248#")
> **About: RockLight causes the Thinklight of an IBM Thinkpad to flash to the beat of your music. It consists of an XMMS visualisation plugin and a small stroboscope application that runs independently from XMMS. You need a ThinkPad and a Linux kernel with ibm_acpi enabled**.


Thanks

---

### Post by MRCeltic on 2007-12-25
was wondering if you ever got his working or not?  i recently downloaded this plugin and I am new to linux and not too sure even where to begin to install it.  was wondering if you knew anything that would help.  They are all in c files and not really sure what to do with them,  as far as getting it to work without root access should just be able to place them in one of your local folders.

---

### Post by holihue on 2007-12-27
> **MRCeltic said:**
> was wondering if you ever got his working or not?  i recently downloaded this plugin and I am new to linux and not too sure even where to begin to install it.  was wondering if you knew anything that would help.  They are all in c files and not really sure what to do with them,  as far as getting it to work without root access should just be able to place them in one of your local folders.


It works perfectly under root.

I think you downloaded the source, but it is in synaptic.

The easiest way to install softwares and other stuff is to use Synaptic.
If you open a terminal, you can type this in it to install the plugin for xmms:

```
sudo apt-get install rocklight
```

Or open System>Administration>Synaptic Package Mangager, and then search for rocklight, and install it.

---

### Post by Yellow Pasque on 2007-12-27
What happens when you run:
```
sudo chmod 777 /proc/acpi/ibm/light
```
Can normal users run it then?

---

### Post by holihue on 2008-02-03
After installing Gutsy the rocklight plugin didn't work at all, and a whole bounce of temeratures didn't show neither.

I think it is something that was excluded in the Gutsy, that was included in Feisty. Maybe a module or something.

---

### Post by disturbedite on 2008-02-03
i'd highly recommend moving away from xmms to audacious.  xmms has been dead for a long, long time.  audacious is its predecessor, so to speak.  it is still actively developed.
btw, it has a rocklight plugin too.  :)

---

### Post by GuttaMan on 2008-02-17
I'm using the current version of Audacious (1.4.6) and I'm having the same problem...Rocklight works perfectly in root, but not on my local username, I don't wanna start experimenting and mess everything up...Any solutions?  Thanks

---

### Post by holihue on 2008-02-26
I think the issue is that it is something wrong with the thinkpad-acpi module.

[http://ubuntuforums.org/showthread.php?t=676035](http://ubuntuforums.org/showthread.php?t=676035)

---

