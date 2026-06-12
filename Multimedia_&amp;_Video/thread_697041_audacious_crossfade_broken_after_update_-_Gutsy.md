---
title: "audacious crossfade broken after update - Gutsy"
date: 2008-02-14
forum: Multimedia &amp; Video
---

### Post by Jose Catre-Vandis on 2008-02-14
Had Audacious working fine with the crossfade plugin since 7.10 was installed. Tonight's updates, 14/02/08. Removed all the settings for Audacious and simply does not show the crossfade plugin as an option under Output Plugins. Have reinstalled, uninstalled and reinstalled plugin to no avail. All the files are where they are supposed to be, but not showing up.

Can anyone advise on a fix for this

About to try a reinstall of Audacious :)
[EDIT] That didn't work either

---

### Post by bachi.bazofia on 2008-02-15
I have the same problem. When I update my system, I lost de Crossfade Plugin Output in Audacious. Before that, Crossfade works perfectly. Why? Is this a bug?

I make the same steps that **Jose Catre-Vandis** (uninstall, reinstall, purge, remove config files, etc. and more etc.!)...

I'm using at this moment XMMS. I missing my Audacious Crossfading!

If someone knows what is wrong, please help us...

Thanks

P.D.: Sorry, but my english is not very very good!

---

### Post by Jose Catre-Vandis on 2008-02-16
Tried installing a previous version of audacious to no avail (probably didn't do it properly), and tried installing a later version of the crossfade plugin but requires updated libc6 which conflicts with tzdata, so not got any further with this?

---

### Post by logos34 on 2008-02-16
Same here.  

And guess what else is wrong?  CD Audio NG plugin has disappeared frm the 'Add' button--you have to right-click>'Plugins services'>'Add CD'.  But it doesn't fetch the tracks from cddb no matter what I change in the preferences/configure.  Still fiddling with it...

---

### Post by logos34 on 2008-02-16
another thing I noticed:  they appear to have removed the ogg plugin option for enabling/disabling 'show average VBR bitrate', like the mpeg/mp3 plugin.  Nowit doesn't fluctuate, but rather just shows the nominal vbr rate.

Jose, 

if you find a solution please post back.  This is really maddening...just when it was working perfectly they had to go f**k it up.  I was relying on audacious for nogap playback (and I just today brought home a CD that is almost all continuous--wouldn't you know it!)

---

### Post by Jose Catre-Vandis on 2008-02-16
OK, found a work around, which means going back to the last version. I have gusty backports in my repositories, this is what is causing the problem for me. 

Before I did this I went into /var/cache/apt/archives and renamed the offending audacious deb file (not sure if this was necessary)

Open up synaptic and uninstall audacious, or from the cli ```
sudo apt-get remove audacious
``` Then open up your sources list:
```
sudo nano /etc/apt/sources.list
``` and put a hash (#) in front of the gutsy backports entry. Mine now looks like this:```
#deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
``` Back into synaptic and search for audacious, you should see the version number has changed back to 1.3.2-4. Click and mark for installation. Install it. next from the Package menu, with audacious highlighted, mark as Locked Version" (I did this for the crossfade plugin as well)

Try Audacious, you should see your crossfade plugin back! You may need to install a few more items and do some reconfiguring, but this seems to do the trick.

You could also try (instead, not as well as!) in Synaptic to select audacious, then from the package menu choose "Force Version". This lets you select the version you want. This didn't work for me, probably due to all the various attempts I made to fix things previously.

Also because the packages are now locked, it should be possible to reenable the backports repository in sources.list.

Let me know how it goes logos34 :)

---

### Post by logos34 on 2008-02-17
> **Jose Catre-Vandis said:**
> Let me know how it goes logos34 :)

Works great now!  Thanks!

Now that I have the previous version of the plugins back in, it looks like the ogg decoder never had an option for vbr display as I thought.  I would have sworn it did.  I like that feature in mp3.  Although the 'Add CD' has been changed and it refused to fetch the cddb info.

---

### Post by Shinoda on 2008-02-17
You may install [Crossfade's Hardy version]("http://packages.ubuntu.com/hardy/sound/audacious-crossfade") as a workaround.

---

### Post by peterx14 on 2008-02-17
Since the latest update (to 1.4.5) I've noticed that Ogg Vorbis files are stopping a few seconds from the end.

Example file here: [http://upload.wikimedia.org/wikipedia/en/d/d1/Debaser.ogg](http://upload.wikimedia.org/wikipedia/en/d/d1/Debaser.ogg)
This should fade out at the end, but it just stops dead a few seconds early. :(

---

### Post by Jose Catre-Vandis on 2008-02-17
> **Shinoda said:**
> You may install [Crossfade's Hardy version]("http://packages.ubuntu.com/hardy/sound/audacious-crossfade") as a workaround.

Yep, tried this, but the dependencies for it cause a vicious circle of dependency hell so i gave up!

---

### Post by Jose Catre-Vandis on 2008-02-17
> **logos34 said:**
> Works great now!  Thanks!

My pleasure :)

---

### Post by Shinoda on 2008-02-17
> **Jose Catre-Vandis said:**
> Yep, tried this, but the dependencies for it cause a vicious circle of dependency hell so i gave up!
Guess I saw that coming, even though I didn't run into that problem myself as all dependencies were already satisfied in my system due to similar issues in the past. But if you take the time to carefully look into it you'll probably be able to get the necessary packages manually.

---

### Post by bachi.bazofia on 2008-02-23
Excelent! It works perfectly. Now Crossfading is running!

Thanks, Thousands of them...

---

### Post by kallium on 2008-02-25
easier than uninstalling whole audacious, you can remove just the plugin and then compile it.
```
sudo apt-get remove audacious-crossfade
```
and then install audacious-dev package
```
sudo apt-get install audacious-dev
```
i'm supposing you have installed everything necessary for compiling source code, if you don't, also type
```
sudo apt-get install build-essential gcc
```
after doing all that, you have to get the plugin source code, [here]("http://www.eisenlohr.org/xmms-crossfade/") is the plugin developer page and for the lazy ones, [here is the source code]("http://www.eisenlohr.org/xmms-crossfade/xmms-crossfade-0.3.14.tar.gz").
after extract the code, go to a terminal, cd into the source code directory (/xmms-crossfade-0.3.14 normally in this case) and type
```
./configure --enable-player=audacious
```
in case you don't have xmms installed, if you have it, you can run the command with no options i guess.
cross your fingers until it ends with no errors, then run
```
make
```
and finally
```
sudo make install
```
close and reopen audacious if you have it open
et voilà :) the last audacious working with crossfade plugin.

hope this helps

---

### Post by Jose Catre-Vandis on 2008-02-26
Thanks Kalium for the update :)

---

### Post by Jean__ on 2008-04-30
Hello,

I am using a fresh hardy install.
I have tried the workarounds posted here but they were not succesfull.
In my sources.list the backports have already been commented out, and the version reported is 1.5.
Recompiling the plugin from source succeeded but upon choosing it in audacious output just stops and fiddling with it crashes audacious, just like the one you get from apt-get.

More people with this? I miss my gapless.

Greets.

---

### Post by Jose Catre-Vandis on 2008-04-30
My "virgin" Hardy is still awaiting customisation. I'll try to have a play tonight and see what gives.

---

### Post by Jean__ on 2008-04-30
Cool avatar, that's from the thunderbirds I believe, that father, Jeff. :)

Curious as to what you will find. Audacious after my upgrade just crashed untill I removed the crossfade plugin.

---

### Post by Jose Catre-Vandis on 2008-04-30
> **Jean__ said:**
> Cool avatar, that's from the thunderbirds I believe, that father, Jeff. :)

It is a Gerry Anderson puppet, but not Thunderbirds.

If you speak Spanish and French, you will understand :) (Look at my nick)

---

### Post by Jose Catre-Vandis on 2008-04-30
Well, a full install of just about everything "audacious" in synaptic (inlcuding the dev files) produced a fully working crossfader here, so can't offer any insight to your problem. Suggest you undo what you have done and try this from synaptic? or on the command line:

Enable medibuntu repositories and all other commented out repositories

```
deb http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy free non-free
```

Follow this guide: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

```
sudo apt-get update
```

```
sudo apt-get install audacious audacious-crossfade audacious-dev audacious-plugins audacious-plugins-dev audacious-plugins-extra libaudclient1 libaudid3tag1
```

HTH :)

---

### Post by Jean__ on 2008-05-01
Thanks,

I tried to compile everything from 1.4.6 from source and had to uninstall audacious because of that.
The compile worked but it didn't give me a working audacious.
So I removed that and installed the stuff with apt-get again.

Now it works and I'm happy again :)

Ps. used to be big fan of thunderbirds.

---

