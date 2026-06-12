---
title: "Can't install Dropbox in 11.04"
date: 2011-03-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by demonic_bunny on 2011-03-14
Hey. I just upgraded my system to Natty Alpha 3. I wanted to try Unity out and see how it compares to Gnome. I went to install Dropbox from dropbox.com, but instead of opening like normal, in 11.04 it defaults to opening in Ubuntu Software Center. I then get an error saying that the package is "of bad quality, and violates standards and isn't allowed." Wtf? Shouldn't I be the judge of that? Is there any way to override what the Software Center considers good and just install Dropbox. I'm a graphic designer and my entire portfolio and current projects are in the cloud. Dropbox is kinda essential xP

Thanks a lot

---

### Post by howefield on 2011-03-14
Moved to "*Natty Narwhal Testing and Discussion*"

---

### Post by Starks on 2011-03-14
"sudo dpkg -i" the deb.

---

### Post by r-senior on 2011-03-14
I consider Dropbox to be essential too, but remember Natty is still over a month away from release and the alpha is just for testing. Any work involving the word "essential" is best not risked on an alpha release.

(Personally I'm avoiding installing Dropbox because mine is in no way a test account and I don't want to mess up the contents of my Dropbox. I am trying Ubuntu One again, which would do the same job for me, but I've not found prior versions reliable and ended up with Dropbox).

There seem to be some redistribution issues which have resulted in removal of packages from Debian: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=610300#25]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=610300#25").

And from Ubuntu too: [https://launchpad.net/ubuntu/natty/+source/dropbox/1.0.10-1]("https://launchpad.net/ubuntu/natty/+source/dropbox/1.0.10-1")

There are also some bugs listed in launchpad regarding Dropbox and Unity incompatibility, e.g. [#704833]("https://bugs.launchpad.net/ubuntu/+source/indicator-application/+bug/704833").

Could this be the end for Ubuntu Dropbox?

---

### Post by Briga on 2011-03-14
I have successfully installed it in Natty and using it right now from this computer with no problems. 

Apparently some .deb are not "good enough" for the Ubuntu Software Centre to install so you have to do it (if you want) another way. 

For Dropbox there are at least two of them:
[B]
Via repository[/B]
Add the following sources to yours:
```

deb http://linux.dropbox.com/ubuntu maverick main

```
there are different ways of doing it. 
Once you are done:
```

sudo apt-get update
sudo apt-get install nautilus-dropbox

```

**Via package**
Download the file .deb from the dropbox website. At the end:
```

sudo dpkg -i nnn

```
where nnn is the full path to .deb file that you have just downloaded. The deb installer creates also the above repository so that dropbox will be updated/upgrade via apt-get or update-manager. 

Good luck.

---

### Post by awam66 on 2011-03-14
Yes I have it installed in Natty no prob;em. The only thing I find is that it does not show up on the top panel indicator. So you have to use the filer to access the folder instead of clicking on the icon in the panel. Can't get it to appear on the Unity Side Panel either.

---

### Post by r-senior on 2011-03-14
> **awam66 said:**
> Can't get it to appear on the Unity Side Panel either.
Did you try dragging the .desktop file from /usr/share/applications to the panel?

---

### Post by awam66 on 2011-03-14
> **r-senior said:**
> Did you try dragging the .desktop file from /usr/share/applications to the panel?

Ah I don't think so. Will try when I next boot Natty

---

### Post by andrek on 2011-03-14
There's a bug report on this, [https://bugs.launchpad.net/ubuntu/+source/indicator-application/+bug/704833](https://bugs.launchpad.net/ubuntu/+source/indicator-application/+bug/704833)

---

### Post by awam66 on 2011-03-14
> **awam66 said:**
> Ah I don't think so. Will try when I next boot Natty

Yes dragging to the side panel worked.

---

