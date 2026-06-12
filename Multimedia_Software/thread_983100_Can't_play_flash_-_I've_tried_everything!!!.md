---
title: "Can't play flash - I've tried everything!!!"
date: 2008-11-15
forum: Multimedia Software
---

### Post by TheIronFistedMonk on 2008-11-15
I'm Baffled.

I've been checking these forums, I've followed instructions from many threads and nothing has helped so far. not even psyke's post about pulseaudio.

I can't play any flash files. I used to be able to play youtube (though very jumpy) but not anymore. All I now get from youtube is "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player". Java is on by the way. And it was flash v10 i installed. Other sites just say click here to install the flash player.

I've had various flash players installed in various ways and nothing has worked....

I did a check thingy that someone instructed in a forum and I currently have installed

/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so

oh and when I look in tools-addons-plugins in firefox, there's only 'default plugin' visible. I suspect the problem lies here somewhere but have no idea how to rectify.

If anyone can help I will be thoroughly pleased, as this is the only part of ubuntu (8.04 by the way) that I can't get working.

The Monk

---

### Post by gandaran on 2008-11-15
type in firefox url bar and post the output here
```
about:plugins
```

---

### Post by TheIronFistedMonk on 2008-11-15
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

---

### Post by TheIronFistedMonk on 2008-11-15
And there's a little table, says enabled - no

---

### Post by gandaran on 2008-11-15
> **TheIronFistedMonk said:**
> Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

this has nothing to do with flash, you should post the full output

---

### Post by TheIronFistedMonk on 2008-11-15
thats under the title 'default plugin', after it is nothing but blank page

---

### Post by Yownanymous on 2008-11-15
EDIT: Should have read post properly.

---

### Post by Meshach on 2008-11-15
If you don't have the plugin go here to download it:

[https://addons.mozilla.org/en-US/firefox/browse/type:7]("https://addons.mozilla.org/en-US/firefox/browse/type:7")


Hope this works,
Meshach

---

### Post by TheIronFistedMonk on 2008-11-15
I already have installed 
/usr/lib/flashplugin-nonfree/libflashplayer.so

though doesn't show up as a plugin in firefox

---

### Post by gandaran on 2008-11-15
> **Meshach said:**
> If you don't have the plugin go here to download it:

[https://addons.mozilla.org/en-US/firefox/browse/type:7]("https://addons.mozilla.org/en-US/firefox/browse/type:7")




Hope this works,
Meshach

going here leads to the adobe site [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
installing from the adobe site or synaptic repositories is the same, the flash is exactly the same one, if one package doesn't work installing another one will not work too, you have to find out what the problem is

---

### Post by TheIronFistedMonk on 2008-11-15
I know I've tried both. I'm no computer genious unfortunately just tryng to make things work! Any ideas or should I just try updating to ubuntu 8.10?? I'd rather not but thats what other people seem to have done when facing unresolvable problems

Whether you help me fix it or not, thanks for your efforts
Monk

---

### Post by binbash on 2008-11-15
go here . [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

and select .deb and download.install it via sudo dpkg -i asdasdasdasdasd.deb

before installation close firefox.Then go to your browser  and write about:plugins , if you see flash there you will be fine

---

### Post by TheIronFistedMonk on 2008-11-15
EDIT: oops posted twice

---

### Post by TheIronFistedMonk on 2008-11-15
binbash - 
Thanks downloading now, I'll post the results!!

---

### Post by gandaran on 2008-11-15
okay, I asked for the output of about:plugins because I wanted to make sure you haven't any other flash package installed like **mozilla-gnash-plugin** or **swfdec-mozilla**
open synaptic package manager and look for those two packages if any installed mark them for complete removal.
if you don't find any of the two installed mark the flashplugin-nonfree for complete removal and click the apply button, next run these commands 
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update
now reinstall the flashplugin-nonfree and reboot

---

### Post by TheIronFistedMonk on 2008-11-15
no gnash or swfdec, starting removal of nonfree. i have ubuntu-restricted-extras. anything i need to do with that?

---

### Post by gandaran on 2008-11-15
> **TheIronFistedMonk said:**
> no gnash or swfdec, starting removal of nonfree. i have ubuntu-restricted-extras. anything i need to do with that?
no, just ignore it

---

### Post by TheIronFistedMonk on 2008-11-15
Right my computer's ballsing up now. Seems I have no connection though I'm managing to use this forum. Baffled again.
Gonna switch off anyway as I have stuff to do, maybe the old girl will be feeling a bit friendlier towards me when I switch back on.
Many thanks peepletons.

TheIronFistedMonk

---

### Post by Meshach on 2008-11-15
Maybe you should upgrade to ubuntu 8.10?


Meshach

---

### Post by TheIronFistedMonk on 2008-11-15
I'm considering it. Just gonna give gandaran's advice another shot now my comp seems to like me again

---

### Post by rebel789 on 2008-11-15
Get cool free gaming stuff and ipods at
[http://www.prizerebel.com/index.php?r=487360](http://www.prizerebel.com/index.php?r=487360)

---

### Post by TheIronFistedMonk on 2008-11-15
Nope. the whole thing's gone nuts. getting error messages when I try to reinstall flash plugin nonfree. Says it's not authenticated as well. I'll give the new heron a whirl.
Many thanks to all you wise and friendly ubuntists

The heavy handed monk

---

### Post by Meshach on 2008-11-15
IronFistedMonk, 

So are you going to upgrade to 8.10?

If so here is an article I would recommend to get you started:

[http://www.howtoforge.com/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server]("http://www.howtoforge.com/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server")

It explains things in plain English with screenshots.


Have fun!
Meshach

---

### Post by psyke83 on 2008-11-16
You'll need to add my repository to your sources.list (see my [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide.

When you've added the repository and updated your packages, please follow the steps in [this]("http://ubuntuforums.org/showpost.php?p=6141615&postcount=4") post (ignore the mention of Intrepid). I suspect you've got an issue with missing library symlinks (caused by broken third-party packages).

---

### Post by macghsot on 2008-11-16
did you try installing it this way?
sudo apt-get -y install flashplugin-nonfree swfdec-gnome swfdec-mozilla

---

### Post by TheIronFistedMonk on 2008-11-16
> **macghsot said:**
> did you try installing it this way?
sudo apt-get -y install flashplugin-nonfree swfdec-gnome swfdec-mozilla

Just tried that and it said this:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

 So I ran that and it said this:
dpkg: requested operation requires superuser privilege

---

### Post by TheIronFistedMonk on 2008-11-16
> **psyke83 said:**
> You'll need to add my repository to your sources.list (see my [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide.

When you've added the repository and updated your packages, please follow the steps in [this]("http://ubuntuforums.org/showpost.php?p=6141615&postcount=4") post (ignore the mention of Intrepid). I suspect you've got an issue with missing library symlinks (caused by broken third-party packages).


Thanks but I've been through your pulseaudio fixes guide a few days ago and it didn't fix the problem. Just tried your post on fixing flash and after the first input it just tells me:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Seems to come up a lot. Whats this mean?

---

### Post by psyke83 on 2008-11-16
> **TheIronFistedMonk said:**
> Thanks but I've been through your pulseaudio fixes guide a few days ago and it didn't fix the problem. Just tried your post on fixing flash and after the first input it just tells me:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Seems to come up a lot. Whats this mean?

It means your system is an inconsistent state. Run the commend as a superuser:
```
$ sudo dpkg --configure -a
```

After invoking that command, please follow the instructions in [this]("http://ubuntuforums.org/showpost.php?p=6141615&postcount=4") post again so I can help you (you're probably going to need to reinstall/downgrade packages, but I won't tell you how until I get the requested output, or else you'll break your system).

---

### Post by Meshach on 2008-11-18
To get into root before you do that you would type:

```

sudo -i

```

Then type your password, you will now see root@yourmachine.


Meshach

---

### Post by funky_D on 2008-11-18
hello guys, i'm having a problem too with flash firefox i guess..
i installed epiphany web browser just to do a comparison, and when i go to this site [http://www.thewebsiteisdown.com/](http://www.thewebsiteisdown.com/) i can watch the movie with epiphany, but not with firefox! i can see youtube videos in firefox.. i just don't have a clue about this! do you guys have any idea?

thanks for your time
Dino

ubuntu intrepid; firefox 3.0.4

---

