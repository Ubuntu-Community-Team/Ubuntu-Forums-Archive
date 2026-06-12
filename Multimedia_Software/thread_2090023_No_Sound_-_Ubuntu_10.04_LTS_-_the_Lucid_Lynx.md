---
title: "No Sound - Ubuntu 10.04 LTS - the Lucid Lynx"
date: 2012-12-01
forum: Multimedia Software
---

### Post by Jackels on 2012-12-01
Hi, pretty new to this forum and hope this is the right sub-forum to ask.

I have no sound on my t60 notebook and tried different solutions I found via google, but none helped.

In the end I tried to upgrade my sound driver desribed on this [page]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules"), but I only got this error ( after the ppa-part ):

sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-45-generic

Pretty much at a loss and don't know what to do.
Fun fact: If I use an usb-headset I get sound.

Hope you can help me and I am willing to provide nearly any output produced by command-lines you ask me to type into the console.

---

### Post by gnusci on 2012-12-01
run in a terminal

$ alsamixer

An check if something is not OK.

---

### Post by Enigmapond on 2012-12-01
Also you can delete the ~/.pulse folder. This will come back with default status automatically. Used to happen with me on occasion with Lucid. (In case you can't find it...it's a hidden file in your home folder,,,just delete the whole thing and see if that fixes when it come back.

---

### Post by ohnonot on 2012-12-01
> **gnusci said:**
> run in a terminal

$ alsamixer

An check if something is not OK.i once had a problem with installing a new sund driver - all channels were set to mute & volume 0 by default!

---

### Post by Jackels on 2012-12-01
> **gnusci said:**
> run in a terminal

$ alsamixer

An check if something is not OK.

How do I know if something is not OK?

> Also you can delete the ~/.pulse folder. This will come back with  default status automatically. Used to happen with me on occasion with  Lucid. (In case you can't find it...it's a hidden file in your home  folder,,,just delete the whole thing and see if that fixes when it come  back.Didn't help :/

> i once had a problem with installing a new sund driver - all channels were set to mute & volume 0 by default!     Seems like okay for me? Again don't know what to look for
[IMG]http://s1.directupload.net/images/121201/r37pqv4s.png[/IMG]

---

### Post by BicyclerBoy on 2012-12-01
Forget the audio-kernel dev ppa. Don't think that has been useful for a long time & it has a conflict with iQuik ppa.

The easiest audio update for lucid is:
apt-get install linux-backports-modules-alsa-lucid-generic
(may need to enable unsupported updates)

Then add the iQuik audio ppa
[https://launchpad.net/~team-iquik/+archive/alsa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=lucid](https://launchpad.net/~team-iquik/+archive/alsa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=lucid)
(better get in quick before it is all deleted)

apt-get update
apt-get upgrade


Your actual problem could be solved by adding this to file:
/etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=thinkpad

---

### Post by Jackels on 2012-12-01
Thanks for the answer.
Already had the last line in my config,

I added those repositories
add-apt-repository ppa:team-iquik/alsa
add-apt-repository ppa:ubuntu-audio-dev/ppa

And updated and upgraded, but still no sound :/
Or was I supposed to add a different repo, because I did not really know where to see those on the page you linked me.

---

### Post by BicyclerBoy on 2012-12-01
How does "Forget the ubuntu audio-dev ppa but install this:..."
```

apt-get install linux-backports-modules-alsa-lucid-generic

```"
turn into adding the audio-dev ppa & not installing the backports module ??

**Do not** use ppa:ubuntu-audio-dev/ppa
Remove any packages that have installed from there..
(Use synaptic package manager)

Using synaptic:
- remove the previous iQuik repository URL
- remove packages installed from audio-dev ppa (origin)
- add this by copying this into repositories..
```

deb http://ppa.launchpad.net/team-iquik/alsa/ubuntu lucid main

```
- reload
- update

---

### Post by ohnonot on 2012-12-03
...and about your screenshot:
usually you're interested in pcm and master and they're both up and not muted.
no problem there.

---

### Post by neilmaclennan on 2013-03-25
I realize that this thread is likely solved. I was having the same problem and tried a few of the ideas set out by other users. Anyway the long and short of it was that I managed to fix the problem on my own while messing about with various settings under sound. I fixed my problem by changing the following by left clicking on the audio icon: 

    **sound preferences**
        **output** (tab)
            **connector **(near the bottom)
                *Analog Outp*ut / No Amplifier

It was set to "Amplifier" on my system. Once this was changed the sound worked immediately, The reason I am adding this is that even if you check alsamixer etc... it will show that all is well with those things. And this may help others to fix the sound when all the other stuff (especially commandline stuff for beginners) is unnecessary and does not help identify the problem. Hope that this helps someone

---

