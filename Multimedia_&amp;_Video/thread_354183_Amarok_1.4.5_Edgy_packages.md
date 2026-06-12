---
title: "Amarok 1.4.5 Edgy packages?"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by darweth on 2007-02-05
Well, I just tried compiling 1.4.5 and was having some success but then I abandoned the effort because I did not want to manually install Ruby and all kinds of stuff.  When can we expect some neat .debs to come out for Edgy (third-party or official)?  If I can find a Feisty .deb, would it work?

---

### Post by btdown on 2007-02-05
yeah I came here looking for a 1.4.5 Amarok package as well. Perhaps some kind soul could help us out.

I thought about compiling it myself, but it never works right.

BT

---

### Post by ffxr on 2007-02-05
i compiled it from the tarball.. i just couldnt wait any longer..

dependedent packages you need include:

```
libaudio-dev libcupsys2-dev libglu1-mesa-dev liblcms1-dev libmng-dev libqt3-mt-dev qt3-dev-tools kdelibs enscript gettext-kde hspell kate kcontrol kdebase-bin kdebase-data kdebase-dev kdebase-kio-plugins kdelibs4-dev kdeprint kdesdk-scripts kdesktop kfind khelpcenter kicker  klipper kmenuedit konqueror konqueror-nsplugins konsole ksmserver ksplash ksysguard ksysguardd kwin libacl1-dev libarts1-dev libartsc0-dev libasound2-dev libaspell-dev libattr1-dev libavahi-compat-libdnssd1 libavahi-qt3-dev libdbus-qt-1-1c2 libidn11-dev
  libjasper-1.701-dev libkonq4 liblua50-dev liblualib50-dev libnss-mdns libogg-dev libopenexr-dev libsasl2-dev libtiff4-dev libtiffxx0c2 libvorbis-dev libxml2-utils libxslt1-dev lua50 poster psutils
```

at least, oh and you'll need to compile xine-lib as well.. 

, i wish had left it alone now.. ll probably just remove it... my curiosity satisfied and just wait for the edgy debs.. its not really that much different.. prettied up the collection browser with album art & a wee bit of alteration to how the playlist is displayed.. 

as i say id just hang on for the debs..

---

### Post by darweth on 2007-02-05
yeah... one of the main reasons i want it is actually quite minor.  the context browser is broken in 1.4.4 in that "favorite tracks" tab does not work under Ubuntu.  i was told 1.4.5 fixes that.  minor, but something i want! lol.  i also like the quick update collection button.

---

### Post by chavo on 2007-02-05
Wow it's been out like 5 minutes and you guys are screaming for packages :P
Just apt-get build-dep amarok to get all the libraries you need to build it.

---

### Post by btdown on 2007-02-05
It's not that I didnt try....I tried compiling it and making a deb for it, but it didnt work.  I've successfully done 1 or two easy packages before, but this one had a problem of some kind looking for x libraries when I ./configured and it puked. This looks like it may be difficult for a novice to pull off.

I wish making compiling and making packages was a lot easier, but i guess thats the price you pay....

---

### Post by darweth on 2007-02-05
I have a dumb question.

Let's say you install Amarok 1.x.x from a repos somewhere.  Later on you purchase an MTP or some other device.  You install lib-mtp.  Will it work in Amarok or does it need to be re-compiled to take advantage?  I suppose that depends on the deb as maybe a deb might come with all of that stuff packaged in and enabled from the outset.  Do they generally come with support for that stuff?

---

### Post by stokedfish on 2007-02-06
No worries - J. Riddell will offer packages on kubuntu.org...

Keep an eye on that site they should be up soon!  ;)

---

### Post by infopipe on 2007-02-06
> **stokedfish said:**
> No worries - J. Riddell will offer packages on kubuntu.org...


Are you sure about that? 
I saw this [http://dot.kde.org/1170628159/1170640766/1170668738/1170673828/1170688921/]("http://dot.kde.org/1170628159/1170640766/1170668738/1170673828/1170688921/") comment yesterday.

Nevertheless I'm hoping for an official kubuntu package. 
Or at least an official statement that no packages will be provided :-)

---

### Post by darweth on 2007-02-06
I couldn't wait any longer and just compiled it myself.  It was actually pretty easy.  I also built libgpod and libmtp from source for the hell of it.  I like BLOAT.  I am undecided about which and audio player to buy soon and figure I might as well just have support for everything. :P  It was a fun learning experience.  I encourage all of you to keep giving it a shot until you get it.  And remember to use checkinstall.

---

### Post by kernelsandirs on 2007-02-06
I compiled 1.4.5 last night it fixed the collection issue others and I were having!!! I can now add all of my tracks to my collection, and only get a warning if some tracks were not going to be added(instead of just dropping the entire sync with an error)  :-)
some also had issues over smb but it worked fine also.

I also did not have to compile xine-lib, I guess the one I had from apt met the dependency ok

:guitar:

---

### Post by stokedfish on 2007-02-06
Yes, I am sure.

I talked to the kubuntu backport lead the day before yesterday in #amarok on freenoide I asked him about DEBs for 1.4.5 - he passed my question on to J. Riddell and he said yes, there will be packages!

Well that's all I know, maybe it's just delayed a bit...

And I think there's already packages in the zcessi repository if you can't wait:

[http://forum.ubuntuusers.de/goto?post=565526](http://forum.ubuntuusers.de/goto?post=565526)  ;)

---

### Post by infopipe on 2007-02-06
> **stokedfish said:**
> Yes, I am sure.

I talked to the kubuntu backport lead the day before yesterday in #amarok on freenoide I asked him about DEBs for 1.4.5 - he passed my question on to J. Riddell and he said yes, there will be packages!



OK. thanks for the info. I'll wait for the kubuntu packages.

---

### Post by stokedfish on 2007-02-06
Just for your info - the above linked edgy packages work great!  ;)

--->   [http://forum.ubuntuusers.de/goto?post=565526](http://forum.ubuntuusers.de/goto?post=565526)

But yeah, packages on kubuntu.org should follow as well, dunno why they are not up yet...

---

### Post by btdown on 2007-02-06
Just a quick followup...I finally succeeded in compiling 1.4.5 on Edgy with the help of FFxr's dependent package list above. I used checkinstall (cause that's all I know) and it installed and plays fine. The only thing funky is that the "update" icon always shows up now and wants me to downgrade to 1.4.4. Any idea how to fix?

Thanks for the help.

BT

---

### Post by F-3582 on 2007-02-07
> **btdown said:**
> Just a quick followup...I finally succeeded in compiling 1.4.5 on Edgy with the help of FFxr's dependent package list above. I used checkinstall (cause that's all I know) and it installed and plays fine. The only thing funky is that the "update" icon always shows up now and wants me to downgrade to 1.4.4. Any idea how to fix?

Thanks for the help.

BT
Ubuntu often uses some awkward prefixes before the real version numbers (does anyone know why?). Before trying to build own packages with checkinstall, you need to look those prefixes up in Synaptic. In this case you have to set the version number to "2:1.4.5" in order to avoid such conflicts.

---

### Post by stokedfish on 2007-02-07
[http://kubuntu.org/announcements/amarok-1.4.5.php](http://kubuntu.org/announcements/amarok-1.4.5.php)  ;)

---

### Post by lamalex on 2007-02-07
> **darweth said:**
> I have a dumb question.

Let's say you install Amarok 1.x.x from a repos somewhere.  Later on you purchase an MTP or some other device.  You install lib-mtp.  Will it work in Amarok or does it need to be re-compiled to take advantage?  I suppose that depends on the deb as maybe a deb might come with all of that stuff packaged in and enabled from the outset.  Do they generally come with support for that stuff?

you most likely have to recompile amarok with your modules installed

---

### Post by tgmaster on 2007-02-07
It works automatically, if you add

> deb [http://kubuntu.org/packages/amarok-145](http://kubuntu.org/packages/amarok-145) edgy main

in Synaptic Paket Manager
> Seetings > Repositories > Third Party

eventually you have to enable Proposed and/or Backported update.

Then you have to start the update manager and you'll get Amarok 1.4.5

---

### Post by testube_babies on 2007-02-07
I'm not sure if this is the right place to post this, but when I was upgrading to 1.4.5 I saw some startling and exciting news about 2.0:

"Amarok 2.0 development, based on Qt4/KDE4, has already started. Exciting times for the Amarok project - the 2.0 release (perhaps as soon as this summer) will run natively on Linux, OS X and Windows!"

---

### Post by btdown on 2007-02-07
> **F-3582 said:**
> Ubuntu often uses some awkward prefixes before the real version numbers (does anyone know why?). Before trying to build own packages with checkinstall, you need to look those prefixes up in Synaptic. In this case you have to set the version number to "2:1.4.5" in order to avoid such conflicts.

Thanks for the info on this...I wound up uninstalling my deb and adding the repo thats posted in this thread, and everythings fine now. It was a good learning experience if nothing else.

BT

---

