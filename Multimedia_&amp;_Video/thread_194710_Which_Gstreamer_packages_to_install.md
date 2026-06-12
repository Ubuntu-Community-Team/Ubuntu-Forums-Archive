---
title: "Which Gstreamer packages to install"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by testing1234 on 2006-06-11
I made, I believe, a big mistake in un-installing all of my gstreamer packages (was trying to get my sound card to function properly and at the time was unaware that gstreamer extended past audio capabilities). Anyone have an idea of which Gstreamer packages I need to install for Ubuntu-Dapper (I have a soundcard that uses the alsa driver) to function properly? Does synaptic store some kind of history of what was installed before a removal? If it does, that would be a solution. Either way, I am in trouble here, as booting up is not happening now, although I do have an internet connection and am able to access all of my files from recovery mode.

Any suggestions?

---

### Post by glotz on 2006-06-11
Synaptic > File > History

---

### Post by Patsoe on 2006-06-11
Removing all gstreamer packages will mean that you have also removed the virtual "superpackage" ubuntu-desktop.

So reinstalling ubuntu-desktop, which depends on all the basic gstreamer packages, will be sufficient.

---

### Post by glotz on 2006-06-11
And by using that solution you'll get all the other crap back you might have uninstalled off ubuntu-desktop...

---

### Post by testing1234 on 2006-06-11
Thank you Glotz and Patzo. When you say re-install the ubuntu desktop, can this be done by installing packages with apt-get? Or do you mean for me to re-install ubuntu desktop using the original install cd?. Please excuse my newbeeness.

---

### Post by glotz on 2006-06-11
He means you to install the (meta) package ubuntu-desktop. You can do it using apt-get, aptitude, synaptic or whatever you like... :)

Try Synaptic, that'll be the easiest to understand probably.

---

### Post by Patsoe on 2006-06-11
There's a package called ubuntu-desktop. It depends on all packages that come in a standard install. Like Glotz says, this way you get back everything you removed from that set, not only the gstreamer packages.

You can just type "sudo apt-get install ubuntu-desktop" at the command prompt, if you want to pursue this option.

Alternatively, you can check out this guys page who has listed all packages that are in ubuntu-desktop: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde) - you can see in that list which gstreamer packages are included by default... but it's a long read :p

---

