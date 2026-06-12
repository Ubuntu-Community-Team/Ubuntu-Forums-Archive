---
title: "Installing swf-player will UNINSTALL everything in my machine."
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by deformation on 2007-12-31
hello forums


recently i wanted to install a swf player to play games in my firefox. i opened synaptic and searched for swf player, i found it "swf-player" in synaptic (i think its from the multiverse repo)

when i choose to install it, synaptic will show me a dialog box that tells me in order to install the swf player i have to Uninstall the following programs, and lists for me almost everything i have on my hard disk, from kde apps to gnome apps and all the libraries.

attached are screenshots to show whats happening 

[IMG]http://img.photobucket.com/albums/v225/DeforMatiOn/Screenshot-5.png[/IMG]

[IMG]http://img.photobucket.com/albums/v225/DeforMatiOn/Screenshot-4.png[/IMG]


if this is happening only to me, then help is requested, if its happening to all of the ubuntu machines, then i think some attention or explanation is required.

please all, search your synaptic for " swf-player " and mark it for install (dont install it, just mark it for install and check what it affects) and post here if the same happens for you

---

### Post by comandrei on 2007-12-31
I think you shold install a flash player. Try looking for gnash or flashplugin-nonfree.
If you can't install flashplugin-nonfree from the repositories (some md5 checksum failure) you can always download it from [adobe's site]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BONRN")
and then you just 
```

tar xvzf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux
./flashplayer-installer

```
And answer the questions. Good luck :)

---

### Post by deformation on 2007-12-31
Thanks for the reply

my problem is not installing a flash player or flash plugin, actually there is no problem, but only i have a question which is why when marking swf-player for install it asks to remove all the installed apps and libs on my machine?

can someone help with this?

---

### Post by gogglecat on 2007-12-31
Using gutsy...tried doing what you said...gives me same list of libs/progs to be uninstalled...strange...
:confused:

---

### Post by sdowney717 on 2007-12-31
it will even want to uninstall synaptic
weird but true

---

### Post by deformation on 2007-12-31
Can someone find out who's responsible for this? i find it more dangerous than malware or bad commands, because any ubuntu beginner will not notice what it will do at the time.

Moderators help please? :)

---

### Post by mahesan on 2008-01-03
This is a serious question... I also want to search for answer to it.
I am using Ubuntu-7,10 Both 64-bit (pentium D)  and 32-bit (Pentium M).

Why does  "Installing swf-player" try to uninstall many installed ones?
 
Please developers kindly look into it.

Thanks a lot.

-Ubuntu Blacky

---

### Post by deformation on 2008-01-03
bump

we need more confirmation cases.

---

### Post by RawMustard on 2008-01-03
Perhaps you should report it on launchpad as a bug and see what response you get there?

Not many devs read all the threads on these forums.

---

### Post by lleonard on 2008-01-03
swf-player is in universe: [http://packages.ubuntu.com/gutsy/utils/swf-player](http://packages.ubuntu.com/gutsy/utils/swf-player)

RawMustard is correct, this should be reported directly on Launchpad at [https://launchpad.net/distros/ubuntu/+source/swfdec0.3/+bugs](https://launchpad.net/distros/ubuntu/+source/swfdec0.3/+bugs).

---

### Post by deformation on 2008-01-03
The program is not registered in launchpad, it have nothing to do with swfdec.

---

### Post by lleonard on 2008-01-05
Humm, I wonder why the packages.ubuntu.com page links to it.

---

### Post by gsub on 2008-01-19
I'm having the same problem. Asked for help on [http://ubuntuforums.org/showthread.php?t=669774](http://ubuntuforums.org/showthread.php?t=669774)

but didnt get anything useful.

Anyone?

---

### Post by mdpalow on 2008-01-19
I'm using Ubuntu 7.10 / 32-bit and ran this test and I too got quite a few things Synaptic wanted to un-install first - to include itself...

---

### Post by gsub on 2008-01-26
<shameless bump>

---

### Post by otrojake on 2008-02-04
Alright.  I just figured out what swf-player is up to.  The package depends on libgtk 2.10.3 or greater.  The default in Gutsy from what I can tell is 2.0-0.  And I don't know of any official repository that contains an appropriate upgrade.  Anyway, what swf-player is trying to do is resolve its dependency issue and upgrade libgtk, and since it's not finding an available upgrade it's saying the way to resolve this is by removing libgtk (the GTK+ graphical user interface library--it's kind of a big deal apparently) and everything that depends on libgtk--in other words, pretty much every dang thing on your system.

I hope that makes sense and helps.

EDIT:  After checking Synaptic, I'm not sure if the version of libgtk is 2.0-0 or 2.12.0.  Anybody with more knowledge about Synaptic know what the actual version is?  I am pretty sure that swf-player doesn't like whatever version libgtk is and that's what's causing the issues.

---

### Post by gsmanners on 2008-02-04
$ apt-cache policy libgtk2.0-0
libgtk2.0-0:
  Installed: 2.12.0-1ubuntu3
  Candidate: 2.12.0-1ubuntu3
  Version table:
 *** 2.12.0-1ubuntu3 0
        500 cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071017) gutsy/main Packages
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
        100 /var/lib/dpkg/status

---

