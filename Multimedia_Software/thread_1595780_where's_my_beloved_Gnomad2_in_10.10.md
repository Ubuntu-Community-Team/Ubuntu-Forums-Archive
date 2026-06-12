---
title: "where's my beloved Gnomad2 in 10.10?"
date: 2010-10-13
forum: Multimedia Software
---

### Post by awambawamb on 2010-10-13
Hi folks.
Yesterday I did the Great Leap and upgraded to Ubuntu 10.10 (from Jaunty). Everything ok, even the microphone worked and java apps are working fine. Some odd problems with the Executable bit but i worked around that (I'm not the usual MicroUser and I know what i do, *most of the time*).

The problem came when i searched the software centre (that froze over trying to install NetHack-x11, LOL) for Gnomad2 or something that could substitute, although i'd rather stick with it, in using my Zen Micro, a 6-years-old mp3 player, but with the new battery paid 11€ he returned magically to the rocking days when it was right out-of-the-box. :KS

Nothing found, so i downloaded the source of gnomad2 2.9.4, trying to compile it by myself. OPs, i can't find dependencies: **libnjb** (>=2.2.4) and **gtk+-2.0** (>=...?).

libnjb is available in synaptic, but executing ./configure still gives me the message that libnjb is missing.

searching for gtk+-2.0 throws me in a jungle of packages. too much for me :)

what's not working? i've read about a malfunctioning version of Gnomad2, but the bigger problem is that Gnomad2 isn't supported anymore - but it worked greatly.

thanks for answering!
Max

:guitar:

---

### Post by kostkon on 2010-10-13
You could try downloading and installing the Lucid version from [here]("http://packages.ubuntu.com/lucid/gnomad2"). Scroll down to *Download Gnomad2* and click on the i386 or amd64 and then select a server close to you, to download the deb file. I don't think you will have any dependency problems, but if you want, try installing the following packages beforehand, just to be sure:
[LIST]
[*]libnjb5
[*]libtagc0
[*]libid3tag0
[*]libmtp8
[/LIST]
use synaptic or in 1 command, just give:
```
sudo apt-get install libnjb5 libtagc0 libid3tag0 libmtp8
```

Hope that helps.

---

### Post by awambawamb on 2010-10-13
hi again!

I bring both good and bad news from here.
The bad news are that gnomad2, even when installed from the .deb package (thanks kostkon for showing me another part of the ubuntu database that i didn't know about) won't work. It starts up, but it closes. this for the last 2 version i found of it. 2.8 doesn't work, has a dependency problem with libmtp7 (i have libmtp8 installed, seems isn't compatible). I think it's a known bug, but in my nooby mind came this:

libMTP = library for Media Transfer Protocol?

seems that my ZEN supports smallsoft's MTP ( [http://en.wikipedia.org/wiki/Creative_Zen#ZEN_Micro](http://en.wikipedia.org/wiki/Creative_Zen#ZEN_Micro) ), let's see if maverick can do that...

here the good news: everything seems alright when i physically connect the player. Nautilus open up and i can see the main directory of my player. I found that i can copy-and-paste folders and single songs in the "my Music" folder of the device and it worked perfectly. So, no need for Gnomad2 anymore it seems. :P

thumps up for maverick...for now (never relax, community!). there was a little mess up when mounting/unmounting the ZEN and other HDs, owever, but I tried more times and didn't happened anymore, so I think it was just a WTF moment between pluggin/unplugging devices. :confused:

my only worries now go to the filesystem, gphoto2, of my ZEN. I wonder if copy-and-paste operations from nautilus could mess up something inside my little music box, and if i can do something to preserve it!

thanks again to everyone who will reply!
Max

---

### Post by eddier on 2010-10-17
I'm also crying onto my Creative Zen!

Awambawanmb(??) did you unmount your ZEN before opening Gnomad-if not,it wont work.

eddier

---

### Post by Bent Axle on 2010-10-18
Hi folks,

I found a way to get Gnomad2 working in Maverick.

Uninstall libmtp8 with synaptic. It will take a few dependencies with it but this is OK.

Re-install libmtp8 and Gnomad2 from Karmic sources. This worked for me in Lucid also.

Plug in Zen, unmount and then fire up Gnomad2. It works as it should.

I hope this helps other suffering Zen users.

BA

---

### Post by eddier on 2010-10-18
That will teach me to look before I post!

I have done persactly what you have done only to have problems with the mount/unmount part,the ZEN goes into play mode when unmounted. I suspect during attempts to get some usability going I have installed something that is causing this behaviour.

I dont think my keyboard can stand much more headbutting!](*,)


eddie

---

### Post by Archarzel on 2010-10-19
For those of you who are lazy:

Hit your Synaptic Package Manager, search Libmtp8 and remove it.
If your running a amd64 download these two and install with Ubuntu Software Center:
[http://mirrors.kernel.org/ubuntu/pool/main/libm/libmtp/libmtp8_0.3.7-3ubuntu2_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/libm/libmtp/libmtp8_0.3.7-3ubuntu2_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/universe/g/gnomad2/gnomad2_2.9.4-0ubuntu1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gnomad2/gnomad2_2.9.4-0ubuntu1_amd64.deb)

If 386:
[http://mirrors.kernel.org/ubuntu/pool/universe/g/gnomad2/gnomad2_2.9.4-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gnomad2/gnomad2_2.9.4-0ubuntu1_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/libm/libmtp/libmtp8_0.3.7-3ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libm/libmtp/libmtp8_0.3.7-3ubuntu2_i386.deb)

Plug it in, Unmount it, Fire up Gnomad2 and watch the magic!

---

### Post by spookyg on 2010-10-30
I was sad to see that Gnomad2 was gone, but then I noticed that for the first time my creative zen works with Rhythmbox.  Shocker!

---

### Post by Hugo Alvarado on 2010-11-03
Hello guys, I too was looking for gnomad2 in maverick, but I found a better solution..gtkam ! Its used to fetch pictures from cameras, but it works perfectly for my zen-v (and better than gnomad2 from what I remember). 

Just install gtkam, connect your device, go to 'camera->add camera' then click 'detect'. It worked for me.

The full details are here:

[http://lucky13linux.wordpress.com/2009/07/19/another-way-maybe-to-skin-the-mtp-cat/](http://lucky13linux.wordpress.com/2009/07/19/another-way-maybe-to-skin-the-mtp-cat/)

later.

---

### Post by eddier on 2010-11-07
GTkam seems to be fine for LOOKING at whats on the device,but there doesnt seem to be any means to upload to it!

I thought i had cracked it with QLIX,but once again transfer to the device (creative ZEN) doesnt seem to be possible! Damn.

eddie

---

### Post by iconoclast hero on 2011-08-10
I was hoping to find some way to put video (like The Daily Show) onto my Creative Zen Vision:M.  I was using rhythmbox to put mp3s onto it and took a look at banshee for the video but neither has worked for video.  I'm hoping that this gnome2 thing will help, but when i went to remove libmpt8, it brought up a bunch of things to remove that I'm not sure I want to remove...  Is this really saying that it will remove VLC and banshee?

```
sudo apt-get remove libmtp8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libva-x11-1 libmono2.0-cil libmono-data-tds2.0-cil libmono-system-data2.0-cil libxcb-keysyms1 libgdata1.7-cil libmono-zeroconf1.0-cil
  libgdata1.4-cil libgkeyfile1.0-cil libsqlite0 libcddb2 libdvbpsi6 libboo2.0.9-cil libgtk-sharp-beans-cil libmono-messaging2.0-cil libvlc5
  libmono-system-messaging2.0-cil libtaglib2.0-cil libupnp3 libmono-sqlite2.0-cil libxcb-randr0 libmono-system-web2.0-cil libiso9660-7
  libkarma0 libgudev1.0-cil libindicate0.1-cil vlc-data libtar libvlccore4 libvcdinfo0 libebml2 libmono-wcf3.0-cil libmatroska2 libgdiplus
  libnotify0.4-cil
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libboo2.0.9-cil libgdata1.7-cil libgtk-sharp-beans-cil
The following packages will be REMOVED:
  banshee banshee-extension-soundmenu banshee-extensions-common libmtp8 rhythmbox-plugins rhythmbox-ubuntuone-music-store vlc vlc-nox
  vlc-plugin-notify vlc-plugin-pulse
The following NEW packages will be installed:
  libboo2.0.9-cil libgdata1.7-cil libgtk-sharp-beans-cil
0 upgraded, 3 newly installed, 10 to remove and 0 not upgraded.
Need to get 921kB of archives.
After this operation, 24.7MB disk space will be freed.
Do you want to continue [Y/n]? 

```

---

### Post by iconoclast hero on 2011-08-11
So how do I stop libmtp8 from updating when I run sudo apt-get upgrade?

---

