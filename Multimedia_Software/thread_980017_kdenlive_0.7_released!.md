---
title: "kdenlive 0.7 released!"
date: 2008-11-12
forum: Multimedia Software
---

### Post by daverich on 2008-11-12
does anyone know how to make a .deb or know where one exists?


[http://www.kdenlive.org/](http://www.kdenlive.org/)



Kind regards

Dave Rich

---

### Post by cowanh00 on 2008-11-12
Hopefully [Getdeb]("http://getdeb.net") are on to this! How do you request a package to get built on Getdeb?

---

### Post by grigio on 2008-11-13
I don't think Kdenlive 0.7 will be on Getdet, it has a lot of deps. Maybe a volounteer could open a PPA for it :P

---

### Post by billstei on 2008-11-14
I was able to install Kdenlive 0.7 into Ubuntu Intrepid by doing this:

1) Get and install the libsox0a package (aka version 14.1.0 ) from the Ubuntu Jaunty archive here: [http://packages.ubuntu.com/jaunty/libsox0a](http://packages.ubuntu.com/jaunty/libsox0a)
2) Add the debian-multimedia unstable (sid) and testing repositories (and gpg key, aka the Christian Marillat key) to Software Sources.  Install kdenlive (and a whole bunch of dependencies).

I had to uninstall at least one package first due to some conflict (and then it came back in with kdenlive), but I don't remember now which one it was ( maybe libavcodec51, or libsox0, or both ?).  You may have to pull in (a lot of) KDE 4.1 stuff too, which I already had.  Also the launch icon did not show up, but it is simply "kdenlive" to start.  Is there a post-install Gnome menu update utility that should have run that I can now run to get a KDE menu item?  Easy enough to create one, but am just wondering.

Obviously the debian-multimedia "unstable" repository is just that, so use at your own risk, and there is no guarantee this will not/never conflict with Ubuntu Intrepid repo's and packaging.  If you don't want to use the unstable repo then Kdenlive 0.7 will supposedly move from the "unstable" to the "testing" repo in about <10 days.

Bill

---

### Post by skiwithpete on 2008-11-18
> **billstei said:**
> I was able to install Kdenlive 0.7 into Ubuntu Intrepid by doing this:

1) Get and install the libsox0a package (aka version 14.1.0 ) from the Ubuntu Jaunty archive here: [http://packages.ubuntu.com/jaunty/libsox0a](http://packages.ubuntu.com/jaunty/libsox0a)
2) Add the debian-multimedia unstable (sid) and testing repositories (and gpg key, aka the Christian Marillat key) to Software Sources.  Install kdenlive (and a whole bunch of dependencies).


I'm too much of a newb to understand the two steps you've written down.  Will there be a deb?  Will this join the repository?  Just want to edit some AVCHD and I can't seem to find anything besides this... and I can't even figure out how to install it!

P

---

### Post by billstei on 2008-11-18
I probably can't emphasize enough that this is Risky Business.

*1) Get and install the libsox0a package (aka version 14.1.0 ) from the Ubuntu Jaunty archive here: [http://packages.ubuntu.com/jaunty/libsox0a](http://packages.ubuntu.com/jaunty/libsox0a)*

The link above will take you to a "Details of package libsox0a in Jaunty" page.  At the bottom of the page are the available architectures, i386, and amd64.  Assuming you are using a 32 bit Ubuntu you want i386 and that is a link that takes you to a page of all the mirrors that have the libsox0a package.  The first one is fine for a download this small, aka the mirrors.kernel.org/ubuntu link, which is a direct link to the file libsox0a_14.1.0-1_i386.deb, a deb of the libsox0a package.  Install it by using the GDebi program, or you could do it from the command line like this:

sudo dpkg -i libsox0a_14.1.0-1_i386.deb

[I]2) Add the debian-multimedia unstable (sid) and testing repositories (and gpg key, aka the Christian Marillat key) to Software Sources. Install kdenlive (and a whole bunch of dependencies).
[/I]
The gpg key file for debian-multimedia is here:

[http://debian-multimedia.org/gpgkey.pub](http://debian-multimedia.org/gpgkey.pub)

Once you have it, go to System->Administration->Software Sources, under the Authentication tab, click the Import Key File button at bottom left, and browse to where you put the key file.  Once imported you should see "Christian Marillat" listed in the "Trusted software providers" box.

Now go to the Third-Party Software tab (still in Software Sources) and click the Add button and put this line in for "APT line":

deb [ftp://ftp.debian-multimedia.org](ftp://ftp.debian-multimedia.org) testing main

Now Add another source:

deb [ftp://ftp.debian-multimedia.org](ftp://ftp.debian-multimedia.org) unstable main

Both of these new sources should be checked.  When you click Close on Software Sources it will say that you need to Reload.  Click the Reload button and APT will update it's database.

Now use Synaptic to pick kdenlive, which should be listed as version 0.7, and install it.  Note that kdenlive-data is not needed and is listed as the 0.5 version, so you may want to uninstall that.

If at some point in the future you decide you do not want to be pulling in packages from these sources, use Software Sources to either uncheck or remove them, however, any new(er) versions of installed packages will remain installed, so again the risk of a Big Mess (tm) is something to consider carefully.  Nevertheless, the latest multimedia packages are a fast moving target, and I know no other (better) way to stay current than debian-multimedia, aside from doing your own compiling.

Bill

---

### Post by skiwithpete on 2008-11-18
> **billstei said:**
> I probably can't emphasize enough that this is Risky Business.

Bill

wouldn't it be easier if someone just made a .deb?

Thanks for your help tho, will try it.

// doesn't work, kdenlive no longer appears in Synaptic package manager

/// I was trying it on a live USB install of Kubuntu.  Maybe that's the reason it didn't work.  I have regular Ubuntu installed on my HDD, but can Kdenlive 0.7 work in Gnome?  Should I even bother trying this method in Ubuntu?

---

### Post by billstei on 2008-11-18
As to how/why kdenlive would not listed is very strange, because the regular Ubuntu repo's have it (as 0.5), the debian-multimedia testing has it (as 0.5), and the debian-multimedia unstable has it as 0.7 .  I suspect you are correct in guessing the live USB is the problem.

I am using Ubuntu, and this means that a lot of KDE 4 libraries get installed, but it is not necessary to be running the KDE desktop, aka Kubuntu.  There are lots of KDE apps that I use in Gnome regularly.

Bill

---

### Post by skiwithpete on 2008-11-19
Thanks Bill, I think I'll try it on my Ubuntu install tonight...

Will let you know the results

P

---

### Post by misterb101 on 2008-11-19
> **billstei said:**
> I probably can't emphasize enough that this is Risky Business.


Bill, You are officially my hero of the day! I have been trying to install 0.7 for a couple of days now and this did the trick!

Later,
Rob

---

### Post by skiwithpete on 2008-11-19
> **skiwithpete said:**
> Thanks Bill, I think I'll try it on my Ubuntu install tonight...

Will let you know the results

P

I've successfully installed it, but have terrible frame drops, skips and inconsistent sound...

I have a modern HP Pavillion Laptop with Dual Core Centrino 5250 at 2ghz, 3 gig ram, and Intel vid card.

---

### Post by billstei on 2008-11-19
Hard to say, but video and audio drivers can be selected/changed under menu Settings->Configure Kdenlive->Playback.  No playback problems here, but you should talk to the gurus either on the kdenlive forum or via the kdenlive mailing list.

My knee-jerk reaction is to guess PulseAudio, which I have no love for thus far.  Complete removal of PulseAudio is slightly tricky or you might get locked out of Gnome, so don't try it (yet).  But I did, and have no regrets (or playback problems).  I'm all so ALSA.

Bill

---

### Post by stelekpl on 2008-11-30
Hi all,
I did what is described here and the latest Kdenlive is now installed. Unfortunately it crashes on startup. The problem is like that:

```
kdenlive(8913) MainWindow::parseProfiles: RESULTINGÂ*MLT PATH:  "/usr/share/mlt/profiles/"
KCrash: Application 'kdenlive' crashing...
sock_file=/home/myuser/.kde/socket-myhost/kdeinit4__0
Warning: connect() failed: : No such file or directory
KCrash cannot reach kdeinit, launching directly.

```

I've been searching around the web and I found that my problem might be with the MLT not working. So following the advices I tried to start "inigo" but on my system it simply ends with "Segmentation fault". Do you have any hints for me? Is there something I can do to get Kdenlive working?

---

### Post by billstei on 2008-11-30
The latest mlt package (0.3.2-0.2) from debian multimedia causes a unresolvable dependency on libsox1 14.2.0.  This is exactly the kind of problem that I referred to in an earlier post as "Risky Business", so here we go...

Unfortunately, there is no libsox1 14.2.0 in the Jaunty repo's (yet).  You can get one here:

[http://packages.debian.org/sid/libsox1](http://packages.debian.org/sid/libsox1)

but there are two problems in using it, 1) libsox1 conflicts with libsox0a that I used earlier, and 2) it depends on libltdl3 which is no longer in the Ubuntu repos for >Hardy.

Uninstalling libsox0a means kdenlive (0.7) and the mlt stuff gets uninstalled too.

Then I used the old Hardy libltdl3 from here:

[http://packages.ubuntu.com/hardy/libltdl3](http://packages.ubuntu.com/hardy/libltdl3)

Using GDebi, I manually installed libltdl3, then the new libsox1 (14.2.0).  Now kdenlive can be installed normally via Synaptic which pulls in the new mlt 0.3.2-0.2 ( mlt, libmlt1, libmlt++1 ) from debian multimedia, and there are no un-upgradeable packages bugging the Update Manager.

Seems to be working for me.

Bill

---

### Post by stelekpl on 2008-12-01
My problem is that I already have everything installed. It just does not work. All the mentioned libs I already have. The problem is that Kdenlive crashes at startup :(

---

### Post by wadelewis4 on 2008-12-06
It may be of little help, but I remember playing around with kdenlive months back in ubuntu, and it crashed all the time as well. I could see it attempting to start but then it would just crash. I disabled compiz effects and it worked, just a thought.

---

### Post by wadelewis4 on 2008-12-07
Hey again,

Ok, I just successfully installed Kdenlive 0.7 by use of the debian multimedia sources. I had to hunt for all of the dependencies and install them one by one, then install kdenlive from the deb there. I took all the collected dependencies and the kdenlive deb and archived them.

I uploaded it to one of my sites.
I'll include a link so you guys can try it too: [Download it Here.]("http://sites.google.com/site/virtubuntu/Home/Kdenlive0.7.tar.gz?attredirects=0")

Note: I had to install one by one as I kept up with each file and it's dependencies, but you should only have to install by "sudo dpkg -i *.deb" from the dependencies folder. 

Hope it helps. Worked for me. Have fun.

UPDATE: I started a new thread with a link to the files and instructions for installing: [http://ubuntuforums.org/showthread.php?t=1004600]("http://ubuntuforums.org/showthread.php?t=1004600").

---

### Post by Gide on 2008-12-07
Thank you very much, your packages seem to work fine !
Regards,

gide

---

### Post by wadelewis4 on 2008-12-07
> **Gide said:**
> Thank you very much, your packages seem to work fine !
Regards,

gide


You're welcome! I'm glad I could help.

---

### Post by djclue917 on 2008-12-14
Kdenlive 0.7 packages (and related packages) for Intrepid (64-bit) are available here:

[http://www.kde-apps.org/content/show.php?content=95039](http://www.kde-apps.org/content/show.php?content=95039)

Basically, I've backported the MLT packages from the Jaunty sources while the Kdenlive package was based on the sources from debian-multimedia unstable. I've adjusted the dependencies to minimize dependence on unofficial packages.

---

### Post by cowanh00 on 2008-12-14
> **djclue917 said:**
> Kdenlive 0.7 packages (and related packages) for Intrepid (64-bit) are available here:

[http://www.kde-apps.org/content/show.php?content=95039](http://www.kde-apps.org/content/show.php?content=95039)

Basically, I've backported the MLT packages from the Jaunty sources while the Kdenlive package was based on the sources from debian-multimedia unstable. I've adjusted the dependencies to minimize dependence on unofficial packages.

Thanks so much for these packages. They work perfectly for me. Just a couple of things, in the menu there is no icon for Kdenlive and what is the path I should set for the Mlt profiles?

EDIT: I managed to figure these points out. The path for Mlt was: /usr/share/mlt/profiles and I found an icon in one of the icon folders.

---

### Post by Erlander on 2008-12-14
Today I installed kdenlive 0.7 using this guide:
[https://help.ubuntu.com/community/KdenliveSVN]("https://help.ubuntu.com/community/KdenliveSVN")

I've also just re-installed using _djclue91_'s packages. _Edit: djclue91 just inserted as package owner. (sorry my error Cowanh00)_

In both cases I could not get it to load AVCHD files from my HD camera.

According to the documentation on the kdenlive web site it should handle these clips and in fact kdenlive 0.5 from the repositories does load and edit them.  The catch is that it crashes so regularly it is un-usable for me.

What am I missing to get 0.7 to see the AVCHD clips?  Am I missing codecs?

Rob

---

### Post by cowanh00 on 2008-12-14
> **Erlander said:**
> 
I've also just re-installed using Cowanh00's packages.


Not my packages! :p

---

### Post by cignale on 2008-12-14
I've made some packages for Intrepid.

you can grab them at [http://blog.linux-fueled.com/2008/12/14/deb-kdenlive-07-per-ubuntu-810-i386-impacchettato-per-voi/](http://blog.linux-fueled.com/2008/12/14/deb-kdenlive-07-per-ubuntu-810-i386-impacchettato-per-voi/)

---

### Post by billstei on 2008-12-14
For those still using the debian-multimedia scheme, today's update to frei0r breaks/conflicts with the libgavl dependency.  To resolve this I uninstalled libgavl0 (1.0.1-0.2) which in turn uninstalled (the old) frei0r.  Then I downloaded libgavl (note there is a difference between libgavl0 and libgavl ) directly from here:

[http://packages.debian.org/sid/libgavl-1.0-0](http://packages.debian.org/sid/libgavl-1.0-0)

and installed that manually with GDebi, then I was able to (re)install the new frei0r 1.1.22-0.1

Bill

---

### Post by billstei on 2008-12-31
More breakages using the Debian Multimedia repos with the kdenlive 0.7.1, and mlt1 / mlt++1 0.3.4 updates.  I resolved my Big Mess (tm) by using Jaunty packages libjack0 (0.116.1) jackd (0.116.1) libasound2 and libasound2-plugins (1.0.18 ).  I had to remove jackd (and consequently qjackctl, jack-rack) and also libasound2-plugins before I could install the others.  Along the way I took out some -dev packages too (like libjack0.100.0-dev for example) but these should be easy to update with additional Jaunty packages as needed.  Also I am not using PulseAudio (completely removed long ago) so YMMV.  ALSA sound seems to be working fine, although Ubuntu popped up a message saying to update asoundconf, which was like this in a terminal:

asoundconf set-default-card [Name-of-your-sound-card-here]

Tricky at best, and I have no idea yet if I will regret all this (at least between now and a full Jaunty system) but there it is so far, and kdenlive 0.7.1 even runs ;)

Bill

---

