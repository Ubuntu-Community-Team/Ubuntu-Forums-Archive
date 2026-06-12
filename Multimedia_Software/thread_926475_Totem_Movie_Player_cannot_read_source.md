---
title: "Totem Movie Player cannot read source"
date: 2008-09-22
forum: Multimedia Software
---

### Post by ineuw on 2008-09-22
I was trying to play a rented DVD film with the Totem Movie Player but, I got the message that it cannot read from source. I tested other DVD's and got the same results but, it did play a free mp4 film downloaded from the Internet Archive.

I found postings in Forums which guided me to Medibuntu. I read the restrictions, (which don't apply), and the instructions, and downloaded and installed the recommended libraries, but the DVD still won't play.

The recommended libraries are:libdvdcss2, libdvdread3 and libdvdnav4. I am using Ubuntu 8.0.4. What am I missing? Thanks in advance.

---

### Post by Bakon Jarser on 2008-09-22
Try using vlc and see if you get better results.  It's what most people choose for dvd viewing.

---

### Post by chongzivalve0809 on 2008-09-22
a professional [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm) China manufactuer and supplier,established in 1983The main product is:cast steel [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm),forged steel gate valve ,pressure seal gate valve,plate [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm).  BFV Valve also possess the test lab with various of examination equipment for material chemical composition analysis, physical property and non-destructive examinat-ions such as RT,UT,MT,PT .[gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm) manufacturer website:[www.valvesupplier.net/forged-steel-gate-valves.htm](http://www.valvesupplier.net/forged-steel-gate-valves.htm)

---

### Post by ineuw on 2008-09-22
Many thanks.  I installed vlc and the related extensions and this seems to be working fine.

---

### Post by Drakkor on 2008-09-22
I have vlc and totem, and they can play .avi and un-encrypted video,but not purchased dvd. I have ubuntu extras installed !! :confused:

---

### Post by ineuw on 2008-09-22
Hello Drakkor.  Most of the info I needed to get the DVD playing, I received through a duplicate posting of the same title [Totem Movie Player cannot read source] in the Installation & Upgrades Forum. (I posted it there first by mistake).  Here is the link to the topic. 

[http://ubuntuforums.org/showthread.php?t=926473](http://ubuntuforums.org/showthread.php?t=926473)

If this doesn't help, please get back to me and I'll log back into Ubuntu (I am in XP now), where I kept a record of the packages I installed, relating to this problem. I do remember that you need some codecs from Medibuntu.  I get email replies to both Ubuntu and XP, so feel free to contact me.  I hope this helps.

---

### Post by Drakkor on 2008-09-22
Yeah, I posted this on your other thread by mistake,but try this:

Got this from cj100570 on another thread,and it worked for me ! :)

Do a restart after issuing the following commands.

sudo aptitude install libdvdcss2
sudo /usr/share/doc/libdvdread3/./install-css.sh

---

### Post by ineuw on 2008-09-22
> **Drakkor said:**
> Yeah, I posted this on your other thread by mistake,but try this:

Got this from cj100570 on another thread,and it worked for me ! :)

Do a restart after issuing the following commands.

sudo aptitude install libdvdcss2
sudo /usr/share/doc/libdvdread3/./install-css.sh

No mistake and thanks.  Interestingly, now both vlc and totem play the film but totem is not controllable.  I cannot select the chapters or fast forward.  Oh well, I am happy with vlc.

---

### Post by dwiedenfeld on 2008-10-04
Sorry, but when I do "sudo aptitude install libdvdcss" I get:

```
No candidate version found for libdvdcss2
No packages will be installed, upgraded, or removed
```.

So is it in a repository that I don't have enabled? Or what?

---

### Post by ineuw on 2008-10-04
> **dwiedenfeld said:**
> Sorry, but when I do "sudo aptitude install libdvdcss" I get:

```
No candidate version found for libdvdcss2
No packages will be installed, upgraded, or removed
```.

So is it in a repository that I don't have enabled? Or what?

I will try to recall the steps for the proper installation.

The 1st 4 sources must be enabled in System>>Administration>>Software Sources.  They are Main, Universe, Restricted, and Multiverse.

Also, aim for the installation of vlc and not totem.  I also remember that Medibuntu downloads & installs are important.

I also noticed that you issued "sudo aptitude install libdvdcss".  It should be libdvdcss2.

I hope this helps.

---

### Post by dwiedenfeld on 2008-10-05
Oops--I actually did "sudo aptitude install libdvdcss2", it just appears that when I cut and pasted into the message I missed the "2" at the end. 

I made sure all of the four repositories--Main, Universe, Restricted, and Multiverse--are checked, and they were already checked. How can I allow Medibunutu?

---

### Post by minky311 on 2008-10-05
Go here [http://packages.medibuntu.org/hardy/libdvdcss2.html](http://packages.medibuntu.org/hardy/libdvdcss2.html) and scroll down to the bottom of the page. Download the package for your architecture which is most likely i386. Then just double click it to install it.

---

### Post by dwiedenfeld on 2008-10-05
Great--this worked. Now both VLC and Totem are working, both apparently just fine.

> **minky311 said:**
> Go here [http://packages.medibuntu.org/hardy/libdvdcss2.html](http://packages.medibuntu.org/hardy/libdvdcss2.html) and scroll down to the bottom of the page. Download the package for your architecture which is most likely i386. Then just double click it to install it.

By the way, this was on a Compaq Presario F500 laptop, running Ubuntu Hardy Heron. All seems fine now.

---

