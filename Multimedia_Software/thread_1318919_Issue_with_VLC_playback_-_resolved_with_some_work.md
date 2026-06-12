---
title: "Issue with VLC playback - resolved with some work"
date: 2009-11-08
forum: Multimedia Software
---

### Post by psylo on 2009-11-08
Hi all,

I'm posting this here because it took me a good couple of hours to find a solution to this problem and went down a lot of wrong tracks so I wouldn't be surprised if the issues are similar for others and they are hunting down the wrong solution.

Environment: 

I upgraded to Ubuntu 9.10 from a 9.04 install. I don't know if this affects clean builds. I'm running an acer TravelMate laptop.

I have two DVD drives - one internal on laptop (PAL REGION 2) and a plugin external SONY DVD RW (Multi-region).

Both of these worked flawlessly with Jaunty and Intrepid.

Symptoms:

After upgrading VLC stopped working correctly.

Specifically depending on the type of disk put in there would be a variety of errors. EG:

Cannot read encrypted data related errors

Skipping through all of the different region areas of the DVD.

Some DVDs would start playing then suddenly stop.

Audio would play but no video.

Additionally Media Player and Totem stopped working correctly as well with the following types of errors:

Outright crashing.

Hanging seeming to "load" for ever.

Initially I was hunting after the encryption issue thinking libdvdcss was at fault post-upgrade but this was a symptom not a cause. Likewise there was a lot of talk about hardware problems but my DVD drives would both read and write non-movie DVDs without problems.

I didn't check but some people had also cited issues around playback on media that was copied direct from DVD and not converted to alternative encodings.

Solution:

So whilst my specific symptoms were very different from some of those reported (mostly there was an issue with hardware detection) it appears that the underlying fix is the same.

Thanks to moviemaniac for their posts around this subject which ended up fixing mine too.

1. Remove libbrasero-media0 

sudo apt-get remove libbrasero-media0

This will break certain packages and uninstall others - let it do so. The biggest casualties will be rhythmbox and brasero but leave that for now.

2. Once this has been removed try and play a selection of DVDs with VLC / MPlayer / Totem and you should find it works.

3. Now fix your brasero and rhythmbox install.

Download these to a folder: 

[http://launchpadlibrarian.net/31473036/libbrasero-media0_2.27.92-0ubuntu1_i386.deb](http://launchpadlibrarian.net/31473036/libbrasero-media0_2.27.92-0ubuntu1_i386.deb)

[http://launchpadlibrarian.net/31524185/libbrasero-media0_2.27.92-0ubuntu2_i386.deb](http://launchpadlibrarian.net/31524185/libbrasero-media0_2.27.92-0ubuntu2_i386.deb)

In terminal go to this folder and then install it using sudo dpkg -i *.deb and it will go through the install process.

These libraries are a stable copy that seems to work appropriately which moviemaniac found in his cache and rolled back to. There might be some since then but these definitely work.

4. Reinstall rhythm box to get your music player back if you use it:

sudo apt-get install rhythmbox

5. If you want to lock these files so they don't get updated by the package manager do the following:

Open Synaptic.

Do a search for: libbrasero

You'll see the package libbrasero-media0 installed. 

Select it then go to the menu Packages -> Lock Version 

It will go away and think about it then proceed to lock the package.

Now hopefully it shouldn't update and your VLC will remain working.

I hope that helps anyone with a VLC DVD playback issue with a range of symptoms. Big thanks to a casual posting by moviemaniac for the fix as well. I would have posted a solved to that thread ([http://ubuntuforums.org/showthread.php?t=1283142](http://ubuntuforums.org/showthread.php?t=1283142)) but for the fact it was in Alpha so was closed.

Cheers
AndrewF

---

