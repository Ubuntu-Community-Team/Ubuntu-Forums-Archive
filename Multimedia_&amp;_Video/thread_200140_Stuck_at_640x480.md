---
title: "Stuck at 640x480"
date: 2006-06-19
forum: Multimedia &amp; Video
---

### Post by black mariah on 2006-06-19
I used Linux for three years, went back to Windows for simplicity's sake, and want to give Ubuntu a shot since there are some aspects of Linux I prefer. The problem is that I can't change the resolution to anything but 640x480. Installing the nvidia drivers (I have an FX5500) through Synaptic did nothing. Installing them from the package on nvidia's site did nothing. On other distros (various Fedora, Slackware, and Debian) I have had no issues after installing the drivers, but for some reason Ubuntu refuses to cooperate.

The only notable thing here is that my monitor requires the "IgnoreEDID" option to be set in the monitor category in my xorg.conf. 

Really makes me wonder why I bother with this stuff in the first place...](*,)

---

### Post by tseliot on 2006-06-20
Try point 5 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")

If that doesn't work try point 10

And BTW if you had used the Search function of the forum you would have found a few threads about the same topic (and with the same solution)

---

### Post by black mariah on 2006-06-24
And why the assumption that I didn't use the search function? Believe it or not, the same problem doesn't always have the same resolution.

Point 5 didn't work. I'd already done that and ended up with nothing to show for it. Point 10 is something I was well aware of from the first run-through trying to install the Nvidia drivers and, if you would learn to read, is something I mentioned IN MY ORIGINAL POST. "IgnoreEDID" and "UseEDID" "False" do the same thing, only the former is deprecated (although, contrary to what Nvidia's documents say, it still works. At least on my box it does). 

For no reason whatsoever, the only thing that made it work was manually editing the xorg.conf file and removing all references to any resolution but 1280x1024. Save it, restart X, and suddenly I have my choice of resolutions.

WTF? ](*,) Eh, whatever. It's working. I've come to expect braindamaged pseudo-solutions that make no sense from every other distro I've used. I don't know why I expected Ubuntu to be different.

---

### Post by tseliot on 2006-06-25
[QUOTE=black mariah]Point 5 didn't work. I'd already done that and ended up with nothing to show for it. Point 10 is something I was well aware of from the first run-through trying to install the Nvidia drivers and, if you would learn to read, is something I mentioned IN MY ORIGINAL POST. "IgnoreEDID" and "UseEDID" "False" do the same thing, only the former is deprecated (although, contrary to what Nvidia's documents say, it still works. At least on my box it does).[/QUOTE]
My statement was polite and so should have been yours. I remind you that we are here to help people (for free).

[QUOTE=black mariah]For no reason whatsoever, the only thing that made it work was manually editing the xorg.conf file and removing all references to any resolution but 1280x1024. Save it, restart X, and suddenly I have my choice of resolutions.[/QUOTE]
Weird...

---

