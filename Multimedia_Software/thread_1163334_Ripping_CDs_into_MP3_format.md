---
title: "Ripping CDs into MP3 format"
date: 2009-05-18
forum: Multimedia Software
---

### Post by ursus262 on 2009-05-18
I've got Jaunty and use K3B and the excellent Banshee Media Player.  I want to load my CDs onto MP3 format for use on my ipod.

However, when I come to rip, in K3B, the CD spins up, I get an error message, and it then halts.  The error message goes something like this:

[I]command failed: lame -h --tt[I]

Also, Banshee doesn't rip into MP either, with the option not being avaliable.

I tried doing this before and after trying the multimedia help sticky.

This is really exasperating.  Can anyone offer any suggestions?

Many thanks

---

### Post by growled on 2009-05-18
Install Sound Juicer. It works wonderfully.

---

### Post by ursus262 on 2009-05-18
Nope.  Don't work.  MP3 is not in the list of options in the drop-down box:eek:

---

### Post by Arup on 2009-05-18
You need to install codecs, install all the gstreamers from add remove, also check gstreamer-plugins-bad in synaptic.

---

### Post by ursus262 on 2009-05-19
Still doesn't work.  done all of that.

What is it with MP3 encoding and Linux?  Anyone would think it was a proprietary standard that someone is trying to protect ;)

Any more suggestions?

---

### Post by xc3RnbFO8P on 2009-05-19
Install **Ubuntu Restricted extras** in Synaptic Package Manager

---

### Post by Arup on 2009-05-19
Nothing wrong with mp3 in Ubuntu, it works, just need to install the right codecs.

---

### Post by ursus262 on 2009-05-20
Thanks guys.  I unstalled the restricted extras for Ubuntu and it now works.  I had the Kubuntu restricted extras installed already, as I use Kubuntu, but my media player needs the Ubuntu REs to work.

---

### Post by Niloc on 2009-05-21
Where do I get the 'Ubuntu restricted Extras' ?

---

### Post by andrew.46 on 2009-05-22
Hi Miloc,

> **Niloc said:**
> Where do I get the 'Ubuntu restricted Extras' ?

The details can be seen here:

RestrictedFormats
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

including details of how to download the relevant files.

Andrew

---

### Post by gordintoronto on 2009-06-21
That describes the situation exactly: it is a patented "standard" for which someone is trying to charge royalties.  See Wikipedia: MP3, licensing and patent issues.

> **ursus262 said:**
> What is it with MP3 encoding and Linux?  Anyone would think it was a proprietary standard that someone is trying to protect ;)


---

### Post by Naegling23 on 2009-07-01
im having problems on kubuntu with mp3's as well, I can play them, but when I encode them, all I get is a hissing sound.

You uninstalled ubuntu-restricted extras?

What files, when I try to remove the package, it only removes ubuntu-RE, not the individual files..

currently, I have both ubuntu, and kubuntu restricted installed, could this be my problem?

---

### Post by mameshiba on 2010-08-06
Hi there,

Stumbled upon this thread as I'm currently having the same problem. I've done everything suggested in this thread and am using Sound Juicer, but when I insert a disk and open Sound Juicer I'm getting an error message that says "The currently selected audio profile is not available on your installation." with the options "Quit" and "Change Profile", then takes me to a box headed up "Preferences" with "Output Format" at the bottom with a drop-down box and only CD quality MP3 available, but when I try to okay that and extract I get "Sound Juicer could not extract this CD. Reason - Failed to get output format".

Any thoughts?

(Thanks)

---

