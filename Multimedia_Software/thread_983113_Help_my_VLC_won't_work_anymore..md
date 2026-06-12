---
title: "Help my VLC won't work anymore."
date: 2008-11-15
forum: Multimedia Software
---

### Post by noobuntoo on 2008-11-15
I absolutley love VLC and now i can't get it to work anymore. I had version 0.8.6 for a while and decided to upgrade to 0.9.3. I'm running Ubuntu 8.04

The newer version has a newer default skin when i open it. The problem, i can't play video or even open preferences in the player anymore. I press a button and nothing happens. Am i missing something?

I've tried uninstalling and reinstalling, uninstalling and reinstalling the old version (it gives me the same newer problematic skin).

At this point I just want any version of vlc that works.

Can anyone help me?

---

### Post by binbash on 2008-11-15
please paste the console output, it is probably a skin problem.Did you try to uninstall with --purge?

---

### Post by noobuntoo on 2008-11-15
how would i go about doing that?

I think it may be a skin problem. Even when i click and drag a video into the window it starts playing but i can't see anything

---

### Post by wolfen69 on 2008-11-15
in synaptic, completely remove vlc. then:
```
sudo apt-get clean
```then:
```
sudo apt-get autoremove
```then:
```
sudo apt-get install vlc
```

---

### Post by binbash on 2008-11-15
sudo apt-get purge vlc

---

### Post by noobuntoo on 2008-11-15
alright, i purged it, cleaned it, auto removed it, and installed it again.

I get the same thing. The latest vlc build which doesn't work.

If i press the button to open a file nothing happens. If i right click an avi file and choose to open it with vlc it plays audio but no video at all.

---

### Post by mc4man on 2008-11-15
If you want to go back to 0.8.6 then you must do a few additional things. After removing, purging, whatever, search vlc in synaptic and remove any remaining packages with vlc in the name. (libvlc0, vlc-nox, vlc-plugins, ect.

Then assuming your using the korn ppa as a software source disable it in system -> administration -> software sources -> third party.

If you don't you'll keep installing 0.9.3

---

### Post by noobuntoo on 2008-11-15
ok i get what you're saying. i removed any vlc files in synaptic. Made sure my software sources were correct and reloaded the package list. The version appearing in the package list is no longer 0.9.3. Now it is "0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2"

I installed vlc again and it was in fact installing this 0.8.6 version and...

I get the same thing. When i open vlc it still has that non working skin on it. Open file button, edit preferences button don't work. I get no video when i play a file.

Kaffiene works fine, Gnome MPlayer works fine. Vlc still wont work.

---

### Post by mc4man on 2008-11-15
Well there are 'skins' and there are 'interfaces'. The interfaces of 0.8.6 and 0.9.x aren't interchangeable so you must have vlc set to open with a 'skin' other than the default interface.

Try going into home folder and looking for 2 folders. (enable 'show hidden files'. Vlc 0.8.6 saves it's config in .vlc, if it's present delete it entirely.
0.9.x saves it's config in .config/vlc, if present delete the vlc folder.


If you wanted to do from terminal then (safe to copy and paste

```
rm -r ~/.vlc
```
and
```
rm -r ~/.config/vlc
```

---

### Post by noobuntoo on 2008-11-21
alright i did that. Deleted both folders, uninstalled, reinstalled. Same deal.

I noticed in the configuration for 0.8.6 it showed the folder the skin was in. /usr/local/share/vlc/skins2/defaul.vlt

Unistalled it again, deleted that vlt folder completely that i found, reinstalled it, and now when i start the program nothing happens. Doesn't even appear.

---

### Post by theluddite on 2008-12-01
I was having a lot of problems with the new VLC too, but had already upgraded to Intrepid, so simply removing the repo listed above wouldn't work.  I was finally able to downgrade back to VLC 0.8.6 using the method below on an amd64.  [COLOR="Red"]Disclaimer:  I am a relative n00b, so if you try this and it wrecks your VLC install don't blame me.  [/COLOR]On the other hand, if your intrepid VLC install was like mine, you have nothing to lose.  

Download the following three packages:

> [libvlc0_0.8.6.release.h-1ubuntu1_amd64.deb]("http://launchpadlibrarian.net/15988560/libvlc0_0.8.6.release.h-1ubuntu1_amd64.deb")
[vlc-nox_0.8.6.release.h-1ubuntu1_amd64.deb]("http://launchpadlibrarian.net/15988559/vlc-nox_0.8.6.release.h-1ubuntu1_amd64.deb")
[vlc_0.8.6.release.h-1ubuntu1_amd64.deb]("http://launchpadlibrarian.net/15988558/vlc_0.8.6.release.h-1ubuntu1_amd64.deb")

Then remove conflicting newer packages:
> sudo apt-get remove vlc vlc-nox vlc-data

Then install the older versions using GDebi Package installer (right click the files you just downloaded and select the first option) is this order:
> [LIST=1]
[*]libvlc0
[*]vlc-nox
[*]vlc_0.8.6
[/LIST]

And voila!  Back to normal.  No Qt, no hanging, no problem.

---

### Post by C. Wizard on 2008-12-01
> **wolfen69 said:**
> in synaptic, completely remove vlc. then:
....
```
sudo apt-get autoremove
```then:
[[/CODE]
Cute. Doing that un-installed Synaptic among other things.
However, I have the same problem as the OP.
I'm running 8.10 (mistake number one) and a few weeks ago after doing an "upgrede" VLC stopped running. 
When trying to run it in a console it simply reports back that, "path/vlc has crashed." Nothing more.
I've completely removed and re-installed it twice, about to try again here in a few minutes, but the results are all the same. VLC crashes.
Too bad as I really like it since 0.9.2 and have been using it as my default media player for both audio and video.

---

### Post by C. Wizard on 2008-12-06
> **theluddite said:**
> Download the following three packages:



Then remove conflicting newer packages:

Then install the older versions using GDebi Package installer (right click the files you just downloaded and select the first option) is this order:


And voila!  Back to normal.  No Qt, no hanging, no problem.
Is there another source for those packages. There are on the ppa, or is it, paa.launchpad server, which is completely, totally worthless for someone on dialup. 
Another source would be helpful.
Thank you.

---

### Post by theluddite on 2008-12-06
Here's the actual page from which I located the links to the above packages:

> [https://launchpad.net/ubuntu/intrepid/amd64/vlc/0.8.6.release.h-1ubuntu1]("https://launchpad.net/ubuntu/intrepid/amd64/vlc/0.8.6.release.h-1ubuntu1")

---

