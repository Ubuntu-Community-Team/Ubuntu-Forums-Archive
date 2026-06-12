---
title: "Hanndbrake -&gt; Start Greyed out"
date: 2010-04-24
forum: Multimedia Software
---

### Post by jv2112 on 2010-04-24
I just did a fresh install of Lucid , activated medibutnu repositories, installed libdvdcss2,w64codecs and it won't let me rip my DVD's.

Any thoughts ?

---

### Post by howefield on 2010-04-24
Start handbrake from a terminal, you might get a clue as to what the problem is.

Applications > Accessories > Terminal, and type

```
ghb
```

---

### Post by jv2112 on 2010-04-24
Thanks for the suggestions. I did & I got this -->

** (ghb:6777): WARNING **: returning null (AudioTrack)

when I exit I get ->

(ghb:6777): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed



Not sure what this refers to.

---

### Post by finnlloyd on 2010-04-24
I have the exact same problem in 10.04 release candidate.  Everything loads and previews but I the start button is greyed out so I can't get this thing rolling.  Any help would be appreciated.

---

### Post by howefield on 2010-04-24
You could try a later snapshot than the 0.9.4 version.

Load up Synaptic Package Manager and select Settings > Repositories. Then Other Software tab, press the Add button and paste in the following

```
deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu lucid main
```

Then close and press press the reload button.

You should now have an update for your Handbrake installation available via the Update Manager. No guarantees but it worked perfectly for me.

---

### Post by jv2112 on 2010-04-24
Perfect  !!! 

Thanks for the help :)

---

### Post by howefield on 2010-04-24
> **jv2112 said:**
> Perfect  !!! 

Thanks for the help :)

Any time, glad it worked for you.

---

### Post by JohnAStebbins on 2010-04-24
Or you could use HandBrake's official nightly snapshots.
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by howefield on 2010-04-24
Edited my post above to include the official PPA.

I'd rather that than any other, but couldn't find the link. Thanks for that.

---

### Post by nukeqler on 2010-05-02
> **howefield said:**
> Edited my post above to include the official PPA.

I'd rather that than any other, but couldn't find the link. Thanks for that.

Synaptic is complaining that it needs libwebkit and libnotify, but they aren't available.  Any idea what PPA I'd need to add to get them?

Edit: Hmm, it looks like those libs are available on my system, just under different names (libwebkit-1.0-2 and libnotify1).  Any idea why, or what I might do to convince apt that everything is ok?

---

### Post by pcfixitguy on 2010-05-02
> **nukeqler said:**
> Synaptic is complaining that it needs libwebkit and libnotify, but they aren't available.  Any idea what PPA I'd need to add to get them?

Edit: Hmm, it looks like those libs are available on my system, just under different names (libwebkit-1.0-2 and libnotify1).  Any idea why, or what I might do to convince apt that everything is ok?

I'm having the same problem.  When I try to install the nightly build (PPA) of handbrake, I get the following error:

The following packages have unmet dependencies:
  handbrake-gtk: Depends: libwebkit but it is not installable
                 Depends: libnotify but it is not installable

Anyone know how to fix this?

---

### Post by shungun on 2010-05-02
Search for the following packages in synaptic and install them, then try handbrake again :D
libwebkit-dev (gui)
libnotify-dev (gui)

---

### Post by nukeqler on 2010-05-03
> **shungun said:**
> Search for the following packages in synaptic and install them, then try handbrake again :D
libwebkit-dev (gui)
libnotify-dev (gui)

Tried that, didn't seem to make a difference.

---

### Post by shungun on 2010-05-03
Yes, i just tried too didn't make a difference :-( sorry to trouble you.
Anyone out there to help us on this?

---

### Post by Chilly_Willy on 2010-05-03
I get the same error, but the older version did work!

[http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/pool/main/h/handbrake/handbrake-gtk_svn3271ppa1~lucid1_i386.deb](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/pool/main/h/handbrake/handbrake-gtk_svn3271ppa1~lucid1_i386.deb)

---

### Post by adlin5000 on 2010-05-03
Unfortunately thats for 32bit and I'm running 64bit. I tried looking in the directory for a 64bit one and they only have it for the latest build.

BTW I'm getting the same errors as everyone else.

---

### Post by BHSPitMonkey on 2010-05-04
If you are trying to install the PPA build on 10.04 but are getting unresolved dependency errors, use this workaround:

[http://ubuntuforums.org/showpost.php?p=9232137&postcount=11](http://ubuntuforums.org/showpost.php?p=9232137&postcount=11)

---

### Post by adlin5000 on 2010-05-04
I gave up and compiled it from source. If you follow the instructions here:

[HTML]http://trac.handbrake.fr/wiki/CompileOnLinux[/HTML]

It's real simple. The first part is just the basics for those who are beginners at this kind of thing, then it goes into all the options and settings after that.

Just a quick note, I had to install a few dependences by hand. One due to a slightly different name, and one that just wasn't in the wiki. If you are a complete beginner then I'd just try the workaround BHSPitMonkey suggested.

---

### Post by JohnAStebbins on 2010-05-07
Apologies for the bad packages deps.  The latest on the nightly snapshot PPA are now working again.

---

### Post by nukeqler on 2010-05-07
> **JohnAStebbins said:**
> Apologies for the bad packages deps.  The latest on the nightly snapshot PPA are now working again.

Huzzah!  So it does!  Thanks!

---

### Post by barkej on 2010-05-12
The ppa worked great for me.

---

### Post by delimiter on 2013-03-08
I have this problem today also, after installing handbrake-gtk from the PPA @ [https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases)
I am running Ubuntu 12.04 Precise 32-bit.

HandBrake would open /dev/sr0 or/dev/dvd and appear to read the titles on it but came back with a disabled start button.
Nothing shown on the console when started it using ghb

After poking around I found [http://ubuntuforums.org/archive/index.php/t-2071073.html](http://ubuntuforums.org/archive/index.php/t-2071073.html) and followed the instructions there.
Now it works!

If this doesn't solve it for YOU I suggest looking in the View-Activity Window as that has the logs for the application and helpful clues to what is happening under the hood.

---

