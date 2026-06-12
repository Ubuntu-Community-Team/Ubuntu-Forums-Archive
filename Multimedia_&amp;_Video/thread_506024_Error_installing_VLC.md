---
title: "Error installing VLC"
date: 2007-07-21
forum: Multimedia &amp; Video
---

### Post by Irihapeti on 2007-07-21
I installed VLC and got an error message which I didn’t record, sorry.

However, VLC is now listed in the menu with other media players, and it seems to work for the most part. I tested it on a couple of DVDs, an audio CD and an mp3 file. It crashed when I tried to use the “scope” visualisation.

   I’m now getting the following error message from the update manager

   Could not initialize the package information 

   A unresolvable problem occurred while initializing the package information. 

   Please report this bug against the 'update-manager' package and include the following error message: 

   'E:The package vlc needs to be reinstalled, but I can't find an archive for it.'

If I try to open Synaptic package manager, I get this message:

   An error occured 

   The following details are provided:

   E: The package vlc needs to be reinstalled, but I can't find an archive for it. 
  E: Internal error opening cache (1). Please report. 

When I click on the close box, the package manager quits altogether. It won’t let me remove VLC and start again. Or any other program, for that matter!

What should I do now? 

By the way, I can’t access the internet from Ubuntu, because I have an internal modem that doesn’t want to play. So any sort of online checking is out of the question, but I can download via Windows (which is what I’m using at the moment).

Thanks
Irihapeti

---

### Post by Cappy on 2007-07-21
Two suggestions:
Try ```
sudo apt-get -f install
``` and see if that fixes it.

Try downloading this:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fv%2Fvlc%2Fvlc_0.8.6.release-0ubuntu4_i386.deb&md5sum=f10ad4197a89c79069a7a9eab73a5f0d&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fv%2Fvlc%2Fvlc_0.8.6.release-0ubuntu4_i386.deb&md5sum=f10ad4197a89c79069a7a9eab73a5f0d&arch=i386&type=main)
and copying it to /var/cache/apt/cache with sudo

---

### Post by Irihapeti on 2007-07-21
Thanks for your reply.

I tried both of those; still getting the same error message.

There is now a file named “cache” in /var/cache/apt/ of exactly the same size as the VLC package. Is this what was supposed to happen? (I’m rather rusty on this command line stuff, and very new (3 days) to Linux.) I also tried my other interpretation of what it could mean, i.e. make a new dir "cache" and copy the package to it, but still the same message. A bit frustrating, this, but an interesting learning curve.

Is there any way of removing the installed package so I can start again? Or are there more options before we get to that stage?

Thanks
Irihapeti

---

### Post by Cappy on 2007-07-21
o_O I thought I copied and pasted that directory from my system. I GUESS NOT. That should have been
```
sudo cp vlcfilename.deb /var/cache/apt/archives/
```

Anyway, I found this which should fix it:
```
sudo dpkg --remove --force-remove-reinstreq vlc
```

Don't worry about the cache thing. It's not even a directory/file =(

---

### Post by Irihapeti on 2007-07-21
Thanks, Cappy

I'll have a play with that and get back to you.

Irihapeti

---

### Post by Irihapeti on 2007-07-21
Cappy:

MANY THANKS! That did the trick.

While removing, I got the following message:

dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 89032 files and directories currently installed.)
Removing vlc ...

I installed it again, using another copy I'd downloaded from a different mirror site just to make sure.

Now it's working, and I can stop wondering if I have to reinstall Ubuntu.

Thanks again
Irihapeti
:)

---

