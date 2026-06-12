---
title: "Installing iTunes?"
date: 2008-05-27
forum: Multimedia Software
---

### Post by Kidfork on 2008-05-27
Hello, Im running Ubuntu Hero Hardy 8.04. And im wondering if theres ANYWAY to run iTunes on THis. ANYWAY AT ALL. Rythumbox isn't good enough.

---

### Post by Jon11393 on 2008-05-27
I've been wondering about this aswell (can't live without my podcasts). If anyone has figured out how ould you please share it with us?

---

### Post by bettlebrox on 2008-05-27
You could try running it under [Wine]("http://appdb.winehq.org/appview.php?iAppId=1347"). [Packages]("http://packages.ubuntu.com/hardy/otherosfs/wine") are available for Ubuntu.

---

### Post by edd07 on 2008-05-27
Yeah, you could try wine, though I read somewhere it doesn't have iPod support.

Install it with synaptic (search for wine) or by typing
```
sudo apt-get install wine
```
in a terminal.

After it's installed, just find the iTunes installer and double click it.

---

### Post by abn91c on 2008-05-27
you can try amarok, it works fine with my 30gig video ipod, I have full access to all my songs you can play everythig even see the artwork and get updated track info from the internet

---

### Post by firefeather on 2008-05-27
Hey, see the [iTunes page on Wine AppDB]("http://appdb.winehq.org/appview.php?iAppId=1347") and see if it's going to do what you'd like it to do first. That'll save you an install of Wine if it's not ready yet (but development on Wine goes fast; check back every once in a while).

There's more than Rhythmbox. A non-definitive list of media players that may be similar to iTunes include Amarok (requires KDE dependencies), Banshee (they're coming out with a new version soon with a lot of nice stuff; an open beta of this new version is available), Exaile, Quod Libet, XMMS (that's more similar to Winamp I've heard but...). Anyway, you can try any of those and see if it's what you'd like!

---

### Post by Living2007 on 2008-05-27
> **Kidfork said:**
> Hello, Im running Ubuntu Hero Hardy 8.04. And im wondering if theres ANYWAY to run iTunes on THis. ANYWAY AT ALL. Rythumbox isn't good enough.
Most people would recommend using Wine if you want iTunes in ubuntu, but you will have to use the Windows installer of iTunes + the wine Program
```
sudo atp-get install wine
```

---

### Post by aysiu on 2008-05-27
Read this:
[http://www.psychocats.net/ubuntu/itunes](http://www.psychocats.net/ubuntu/itunes)

P.S. iTunes won't work fully in Wine.

---

### Post by GabrieisWings on 2008-06-13
I'm not entirely sure how I did it, but I've managed it.


That's right. I have iTunes on Ubuntu.

I'll explain what I've done, and you all can try to see, and tell me your results.

1. Pulled the iTunes setup file from the website, and installed through Wine. If you try to run it at this point it tells you that it needs Quicktime.

2.Pulled the Quicktime installer from a windows computer via flash drive, and installed it through Wine, also. It installs properly, and should also install the Quicktime player on your desktop.

3. Ran iTunes again, and it went thru the initial setup procedures.

4. Sat in awe and amazement as iTunes appeared on my screen and collected all my music.

Now, as it started, my screen flickered and it took a moment to recover completely, but it did. Text is off, and the search bar is a bit wonky, but it's iTunes. And I'm listening to Five Finger Death Punch right now.

I really don't know how i managed this. I just wanted to take a break from installing a new ATI driver for WoW.:-k

But I hope that it works for everyone who tries it.

---

### Post by aysiu on 2008-06-13
Can you sync your iPod with it?

---

### Post by GabrieisWings on 2008-06-13
Haven't tried yet. I've been too scared.

But I will right now.

I get a warning saying that I can't import cd's or burn cd's with iTunes unless I reinstall, and I'll try that after this.

...okay.

Here are the results:

iPod isn't picked up by iTunes, due to the iTunesHelper not working yet. I'm going to chalk that up to needing to reinstall iTunes. I restarted iTunes, just to be sure, and sure enough, a box came up saying, "The Software required for communicating with the iPod is not installed correctly. Please reinstall iTunes to install the iPod's software."

I'll do that, and keep you up to date.

---

### Post by GabrieisWings on 2008-06-13
nothing yet, but I'm not able to connect it to the net. (no wireless connection where I'm at) :o

---

