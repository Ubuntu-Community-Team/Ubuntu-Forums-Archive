---
title: "Multi-Monitor: USB 2.0 External VGA Video"
date: 2008-06-20
forum: Multimedia Software
---

### Post by taylorluker on 2008-06-20
I am trying to get three monitors to work on Ubuntu using, one monitor plugged in via VGA and another two plugged in with: 

[USB 2.0 External VGA Video Card]("http://www.iogear.com/product/GUC2015V/")

Currently, there is no Linux driver for the adapter.  **Is there anyway around this? I want desperately to get 3 monitors to work. Please, I am begging you....**

Thank you so much in advance for you help!

P.S.> I would especially appreciate a response from: santoshssu OR 
daller

---

### Post by aeiah on 2008-06-20
its doubtful.

---

### Post by Nados on 2008-07-10
Hi!
I'm looking for the same thing, I have  a USB2VGA adaptor, I use it with windows, but I cannot find any driver with linux... 

I'm still searching...

thank's for the help!

Hola, tengo el adaptador USB2VGA y estoy buscando un piloto para que funcione con Ubuntu, si alguien puede ayudar. gracias!

Salut!
j'ai l'adaptateur USB2VGA et j'aimerais qu'il puisse fonctionner sous Ubuntu, si quelqu'un a le pilote, ce serait grandement apprécié!

merci!

Steve :)

---

### Post by Niko Johnson on 2010-01-09
Im listing on this thread too. please help

---

### Post by jrsprice on 2010-09-12
Yeah me too! I have a no name that I purchased off ebay. I did read that the displaylink brand has their own proprietary drivers that should work with linux. My no name usb adapter came with a mini disc that contained usb drivers for libdlo ... Didn't work since I have crappy ati drivers since crappy ati is so far behind...

I found this link:

[http://lists.freedesktop.org/archives/libdlo/2010-March/000609.html](http://lists.freedesktop.org/archives/libdlo/2010-March/000609.html)

---

### Post by imcrazy on 2010-09-29
I there are different DisplayLink chipsets and I don't think they are all supported by linux DisplayLink drivers.  It's not easy to tell which chipset is in a given DisplayLink USB External Video Adapter.  

While I've had success with a Kensignton model, I didn't have success with a similar IOGear model.  See [http://ubuntuforums.org/showthread.php?t=1566718](http://ubuntuforums.org/showthread.php?t=1566718).

---

### Post by AcidHawk on 2010-11-30
While I realise that this a a little old now... and while I am still searching ... has any-body got this working in ubuntu yet...?

---

### Post by Nados on 2010-11-30
Hello!

YES!

but for the moment I don't have it configured to work, but it was really easy to make it work with Ubutnu 10.04 and should be the same with Ubutnu 10.10.

It's automaticaly reconize by Ubuntu now, you just have to put the information in the xorg.conf file.

I took the example in this page:

[http://ubuntuforums.org/archive/index.php/t-260863.html](http://ubuntuforums.org/archive/index.php/t-260863.html)

but I had to keep only the part I needed to use the USB2VGA adapter.

I make the configuration in my office, then I think you can make it yours too...

good luck!
Steve

---

### Post by AcidHawk on 2010-12-10
Hmm ... Thanks for your input.  However, the link you posted and all the subsequent links didn't help at all.  

I have to resign myself to the fact that this device I have is just not supported in Linux.

Now when I am building a Pro/Con list of whether or not to go back to Windows, at least there will be 1 pro for windows. :)

---

### Post by asharpham on 2010-12-10
I've just purchased the DisplayLink USB Display Adapter, and when I installed it from the supplied disk onto my Windows machine, i discovered a Linux option.

Of course, setup won't run under linux as it's only triggered by "setup.exe"!

So I went searching and found others had been trying to do the same thing. I found information at [http://libdlo.freedesktop.org/wiki/](http://libdlo.freedesktop.org/wiki/) and followed some of the links but I found the instructions way too complicated for a novice like me (including the instructions above by Nados' link).

I love Ubuntu but some things I just can't do because there is no linux "setup" file.

Alan.

---

### Post by kendoori on 2011-01-21
Any updates on this?

---

### Post by tibalt-99 on 2011-02-16
Does it help: [http://mulchman.org/blog/?tag=usb-video-card](http://mulchman.org/blog/?tag=usb-video-card)

---

### Post by wkulecz on 2011-02-16
> **asharpham said:**
> I've just purchased the DisplayLink USB Display Adapter, and when I installed it from the supplied disk onto my Windows machine, i discovered a Linux option.

Of course, setup won't run under linux as it's only triggered by "setup.exe"!

So I went searching and found others had been trying to do the same thing. I found information at [http://libdlo.freedesktop.org/wiki/](http://libdlo.freedesktop.org/wiki/) and followed some of the links but I found the instructions way too complicated for a novice like me (including the instructions above by Nados' link).

I love Ubuntu but some things I just can't do because there is no linux "setup" file.

Alan.

This is one place Unbuntu really falls down.  Its the only UNIX/Linux system I've ever used that didn't come ready to compile software out of the box.  This greatly complicates things that fundamentally should be as simple as:

download source code
unpack
cd source_tree_root_dir
./configure
make
sudo make install.

Then do local configuration for your needs as you must even for windows.

The above is essentially the default Linux "setup.exe" but unfortunately out of the box the ./configure step fails for missing tools, header files, and libraries.

Until someone makes a deb and puts it in the repos, "normal" users are in a rough spot :(

I use an EVGA UV Plus+12 on Windows 2000 and it works fantastic, even allowing video media playback on its monitor!  Would love to find such a thing for Ubuntu.

I'll try to find one of the "supported" Displaylink brands. 

This is a chronic problem with Linux hardware, the support is mapped to the chips used in the device but the mapping of what brands you can buy that uses the chip set is poor, or worse the brand name remains the same but the chips inside change,  Wireless networking devices are the poster children for this issue :(

---

