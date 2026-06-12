---
title: "Upgrade to 9.04 Amarok music Player"
date: 2009-04-25
forum: Multimedia Software
---

### Post by dave r on 2009-04-25
Upgraded to 9.04 yesterday and got a new version of Amarok with no sound, same as a lot of other people. Can anybody tell me how to roll back to the previous version? I had the previous version working just as I wanted it to, even without the sound issue I can't see how to configure the new one like the old one as it looks like half the stuff is'nt there. The sound issue is not my computer I can play music in Rhythm box no problem, its the new Amarok.

---

### Post by Robster2 on 2009-04-25
Not sure if this will help your specific problem  but you will need medibuntu for other video play back and other things.  It will not hurt.

Open a termninal (Applications>Accessories>terminal) 

run the following code

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

---

### Post by smartbei on 2009-04-25
@Robster2: This has nothing to do with the problem.
I have also noticed that I am unable to access (at least through the gui) a lot of the options that used to be in the amarok preferences - such as playback engine, etc.

This is quite annoying.

---

### Post by aquascrotum on 2009-04-25
> **smartbei said:**
> @Robster2: This has nothing to do with the problem.
I have also noticed that I am unable to access (at least through the gui) a lot of the options that used to be in the amarok preferences - such as playback engine, etc.

This is quite annoying.

+1 - the new version of Amarok is a disaster for me. Buggy startup, temperamental audio, only finding parts of media libraries, podcast support apparently buggy, the list goes on (as well as a pretty poor user interface imo) .

What are the best alternative aplications in terms of music management and playback? Ideally with iPod support also.

---

### Post by dave r on 2009-04-25
:confused: Rhythm player is still working normally. I spent most of last night on this Forum searching and trying fixes for Amarok, but nothing has worked. Amarok was working well before the upgrade. I installed medibuntu when I first installed Ubuntu. This appears to be a problem specific to the new Amarok, the old one worked very well. It looks like the new version is a backward step, even when the sound is fixed I am not sure if I am going to get it to work as well as the old one.

---

### Post by quickk on 2009-04-25
The new amarok is in my opinion a piece of crap.  If you want to revert to the old amarok, just use this [PPA]("https://edge.launchpad.net/~bogdanb/+archive/ppa") (Personal Packages Archive).  

I just removed amarok 2 and installed 1.4 using this.  Follow the link to the repository, follow instructions on how to add it and import the key.  Then just paste this in a terminal window and you're set!

```
sudo apt-get remove amarok && sudo apt-get install amarok14
```

---

### Post by pdxken on 2009-04-25
I have the same problem with kubuntu 9.04.

I downloaded audacious to see if it worked and it did not.
Then clicked preferences > audio > current output plug-in and noticed it was set to pulse audio. After setting it to ALSA audacious now works OK (for audacious).

No idea how to change Amarok 2 to ALSA. I seem to recall Amarok 1.X having the option to change this .

ALSA rocks! pulse sucks? I don't know.

Ken.

My rig is an old dell 2 gig pentium with Sound Fusion CS46XX

---

### Post by Frostek on 2009-04-25
Thanks! What a relief - I have my old and working Amarok back! :P

---

### Post by Alex Deez on 2009-04-25
Yeah I have to agree the new Amarok is horrible.  I'll try that recommendation on how to install the old version, I might just revert to 8.10 since most of what I do on my computer is play music.

---

### Post by TR1X on 2009-04-25
I have amorak but ide like to know how I can add a smb:// into the library

---

### Post by dijeesh on 2009-04-26
hi try this to solve the sound problem in Amarok...

open terminal and run the below command....

$sudo apt-get install phonon-backend-xine
$sudo apt-get remove phonon-backend-gstreamer

Enjoy!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by marra on 2009-04-26
@dijeesh: it does work! thanks :)

---

### Post by tbiniaris on 2009-04-26
I had the same problem. The installation of *phonon-backend-xine *solved the problem without having to remove [I]phonon-backend-gstreamer. 
[/I]

---

### Post by shayguitarra on 2009-04-26
@Aquascrotum: The best music manager I've come across since switching to Ubuntu is gmusicbrowser [http://squentin.free.fr/gmusicbrowser/download.html]("http://squentin.free.fr/gmusicbrowser/download.html")
Powerful, great tagging and management facilities. I tried pretty much every music player there was and gmusicbrowser is the closest to Windows apps like Winamp, Foobar and Mediamonkey and I'm surprised more people haven't picked up on it.
And, very important. I have had absolutely no issues with it since upgrading to Jaunty. If anything it seems a little quicker.
Downside: Currently only supports flac, mp3 and ogg. No iPod support. But I run rockbox and there is an option to just copy files to your player. If conventional support is important to you, you could try out gtkpod, which is available in the repositories. But I recommend you download it, give it a try and then weight up what's most important. There is also a script here [http://squentin.free.fr/gmusicbrowser/devel.html]("http://squentin.free.fr/gmusicbrowser/devel.html") that lets you import play stats etc from Amarok.

---

### Post by Kaneda187 on 2009-04-26
Thank you! that new amarok is a joke its ugly horrible and useless!

---

### Post by johannessch on 2009-04-29
Hi all,

thanks for the tip and the PPA link for an easy uninstall of amarok2 and reinstall of amarok1.4.

There seem to be a lot of problems with amarok2 in the moment. After downgrading to 1.4, all the stuff i so got used to works flawless again.

For instance, amarok2 didn't have sound at all on my comp. But even if it would have had sound, streaming my m3u playlists with gnump3d from my server to my computer simply didn't work with amarok2 as player - a feature that works out of the box with amarok1.4.

I think the amarok developers did a great job in redesigning the player itself - but right now, the bugs overweigh the eye-candy way too much to upgrade - let's hope for amarok2.5 to be as feature-complete as amarok1.4, but nicer looking ;-)

Thanks again, guys.

---

### Post by mallegonian on 2009-04-29
I already had phonon-backend-xine and not -pulseaudio.
I fixed it by researching the initial lack of mp3 support in amarok 1*, and by running```
sudo apt-get install libxine1-ffmpeg
```

---

### Post by garethfnb on 2009-05-04
mallegonian, you rock, sorted out the issue with your suggestion

---

### Post by zoze on 2009-05-10
> **mallegonian said:**
> I already had phonon-backend-xine and not -pulseaudio.
I fixed it by researching the initial lack of mp3 support in amarok 1*, and by running```
sudo apt-get install libxine1-ffmpeg
```

it worked for me thanks a lot problems with 9.04 where to start(error at installation) and where to end(amarok) at least know all working perfectly .

---

### Post by hurricanesfan66 on 2009-06-01
Yeaaaa!  The new version was quite a shock, even though it saw my iRiver Clix.  Couldn't transfer playlists, which was huge for me.  I do like some of the graphics in where they are going, but that was definitely not ready for prime time.

Revert back, with the ppa sources, and I am good to go.

---

### Post by pointym5 on 2009-06-03
> **shayguitarra said:**
> @Aquascrotum: The best music manager I've come across since switching to Ubuntu is gmusicbrowser [http://squentin.free.fr/gmusicbrowser/download.html]("http://squentin.free.fr/gmusicbrowser/download.html")
Powerful, great tagging and management facilities. I tried pretty much every music player there was and gmusicbrowser is the closest to Windows apps like Winamp, Foobar and Mediamonkey and I'm surprised more people haven't picked up on it.
And, very important. I have had absolutely no issues with it since upgrading to Jaunty. If anything it seems a little quicker.
Downside: Currently only supports flac, mp3 and ogg. No iPod support. But I run rockbox and there is an option to just copy files to your player. If conventional support is important to you, you could try out gtkpod, which is available in the repositories. But I recommend you download it, give it a try and then weight up what's most important. There is also a script here [http://squentin.free.fr/gmusicbrowser/devel.html]("http://squentin.free.fr/gmusicbrowser/devel.html") that lets you import play stats etc from Amarok.

In my experience, gtkpod is absolutely abominable. The user interface is insane, and the program is almost comically inefficient in its use of resources (for example, just about anything you do results in it wanting to update a window with a complete list of all tracks in your collection, so if the collection is large that means anything you do takes approximately forever.)

Amarok - in its pre-2.0 incarnation - was somewhat better. The new Amarok, however, is terrible.  When re-scanning my collection, it burns 100% of a CPU - why?  That should be overwhelmingly an IO-bound process, so that tells me that there's simply some really dumb code in there.  It's sufficiently bad that it threatens to overheat my machine. Beyond that, the user interface is terrible about reporting status and process progress.  There's something you can do to get it into a state where it continually reports that there are "Multiple background processes" - what does that mean?  I don't know, but I do know that if you're not careful when syncing an ipod you can hose up the database intractably.

Another regression in Amarok 2 is that it cannot deal with ID3 tags that include non-Ascii characters.  Like Björk?  Well, too bad - Amarok doesn't.  (Several other music players, like Exaille, seem to agree with Amarok on that subject.)

It's free, so who can complain?  The only mystifying part of this for me is that I don't understand how a talented software developer with the motivation - presumably from love of music collecting and possession of a significant database of tracks - to suffer the pain of designing, developing, and maintaining a large piece of open-source software can end up happy with something that is so clearly and deeply flawed.

---

### Post by hurricanesfan66 on 2009-07-12
After rolling back Amarok, something I noticed with the new Jaunty version is it will automatically mount my iRiver Clix.  What I have to do then, I discovered, is unmount it, and then use Amarok to mount it.  Crazy little work around, but it does work.  Now I wonder if I would've done that with the new Amarok version, if it would've recognized my iRiver.  But I do like the entire GUI of the old version so much better than the new one anyway.

With my iRiver E100, neither works, so I unfortunately still use Windows for it.  )-:

---

### Post by Ekeluo on 2009-07-13
I think you all should give Amarok 2.2 a roll when it's released. Fingers crossed, you'll dump 1.4 finally...

---

