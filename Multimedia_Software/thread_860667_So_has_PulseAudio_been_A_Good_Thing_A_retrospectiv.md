---
title: "So has PulseAudio been A Good Thing? A retrospective...."
date: 2008-07-15
forum: Multimedia Software
---

### Post by danzvash on 2008-07-15
Back when I started using Linux on the desktop, all the soundcard drivers were in a project called OSS. You could have one sound app running at one time. So if you were playing an MP3 with Xmms, and you used Netscape 4.x to browse to a page that wanted to play sound, Netscape would lock up. I´d have to quit Xmms before I could continue browsing! Ah, happy days.

Then the KDE project came up with this cool thing called a Sound Server. They called it arts. (Gnome called theirs esd.) Basically, it worked on top of the OSS driver, so that it could mix multiple streams from different sound apps together, and stick the mixed stream into the soundcard. Now I could listen to Xmms and open Netscape on any page! Wow! Progress!

Then the dark side of sound servers reared its head. Each sound app had to now be able to talk to arts, rather than the OSS driver. So we had the xmms-arts-plugin. And soundAppx-arts-plugin. And foobarSound-arts-plugin. Each had to be installed separately - let alone developed and maintained separately. And for those apps, like Netscape, that didnt get their own plugins, there was this wrapper app called artsdsp that you would use to execute the app with - i.e. artsdsp netscape. Needless to say, this was very unstable and glitchy, at best.

Meanwhile, the ALSA project was simmering nicely in the background, and building up support across the soundcard range to rival the OSS project, but with a revamped and future-proof internal structure.

But even if you switched from OSS to ALSA for your soundcard driver, you still had to use arts (or esd) to have multiple sound streams simulaneously. The pain and suffering continued unabated.

And then, joy of joys, somebody came up with the ALSA **dmix** plugin.  Suddenly, I could forget arts and all the little sound arts plugins that my apps would use to talk to arts. ALSA did all the sound mixing on its own without any help! And there wasnt any dodgy sound server process that would just crap out unannounced. It all Just Worked! 
And after a short while, even those folks who make the RealAudio player, the Flash player, and (hey!) even the Audacity guys got with the program and made their apps talk to ALSA. Now everybody was at the same party and grooving together!

Sunlight broke through the cloud cover. Flowers popped up everywhere on my Linux desktop landscape, birds chirruped merrily, and the deer munched contentedly on the lush green grass that stretched away to the horizon.

It didnt matter which distro I used - Gentoo, Slack, Redhat/Fedora, Ubuntu ... everybody was in the same boat and singing the same beautiful song. Sound servers became a distant and ridiculous memory, something to raise as a topic at software engineer parties if the mood became sombre and we all needed a laugh. 

That is, until today, when I installed Ubuntu 8.04.1 on this no-name P4 desktop. The install goes swimmingly, as I have come to expect from Ubuntu installs. Everything auto-configures without me lifting a finger - lovely. And I want the desktop to be usable for general audio and video for the user who is going to be using the machine most of the time, so I install ubuntu-restricted-extras to cover all the common DivX/Xvid/mp3/etc type media out there. I load a XviD avi to test out the newly-equipped Totem player, and .... nothing. If I move the slider I can see individual frames, but it doesnt actually *play*.

Hmmmm. Okay, I say, maybe some backend problem. Lets install Mplayer and have a go! Same thing - no playing.
Smplayer? Same deal. Ok, this is getting serious. Can VLC help? I install it, and the video plays OK - but no sound.

After digging around and scratching my head, I realise that, horror of HORRORS - my beloved and highly mature Linux distro of choice, Ubuntu, has got a Sound Server running in it! The thing they call PulseAudio!

Aaaaarrrggghh! The nightmare is come again!

What has become of my lush and happy Linux landscape! What have the developers been smoking? ALSA dmix was so nice! It was so clean and simple! And nice! What the hell is going on? Has everybody gone mad?

So I read up. I read [[COLOR="Green"]this guys defence[/COLOR]]("http://mail.gnome.org/archives/desktop-devel-list/2007-October/msg00136.html") of PulseAudio.
I read ArsTechnicas [[COLOR="Green"]loving summary[/COLOR]]("http://arstechnica.com/journals/linux.ars/2007/10/17/pulseaudio-to-bring-earcandy-to-linux") of why PulseAudio is A Good Thing. 
And I also read, with eyes wide with alarm, the [[COLOR="Green"]HowTo[/COLOR]]("http://ubuntuforums.org/showthread.php?t=789578") for HowTo Get PulseAudio Actually Working On Your Machine. 
(That is ignoring the [[COLOR="Green"]Quick N Very Dirty FixMe Howto[/COLOR]]("http://sudan.ubuntuforums.com/showthread.php?t=852822") and the [[COLOR="Green"]Slightly Different HowTo[/COLOR]]("http://ubuntuforums.org/showthread.php?t=776739&highlight=pulseaudio") ...)

Now, I realise that plenty of people at Ubuntu from Shuttleworth down must have considered this, just like the guys at Fedora and SuSe who are also using this thing, and I can see that PulseAudio has got Way Cool Things going for it (like hotplugging audio-device support, redirecting audio over a network etc) - but if I cant play a silly little movie using this new WhizzBang Sound Server without following a rather frightening multi-page HowTo, then who the hell really wants to use it? Or use Ubuntu, for that matter?
Please bear in mind here that I am an experienced Unix System Administrator, infrastructure support engineer and developer - I dont mind messing with the terminal and getting my hands dirty (in fact I love it) - but I represent about 0.001% of the global computer-using population, and for good reason: most people like to use their cars and computers and stuff to Do Things, not Find Out How They Work For The Fun Of It.

And yes, I know that many, if not most, Ubuntu-ers have had no problems with PulseAudio - but Im using pretty generic kit and a totally default install, so what the hell happened to me and my install?
More to the point, how is the inevitable additional complexity of having a userspace sound system (again!) going to be handled in general? More plugins, more fiddling, more projects to maintain - where does it all end?  libao-pulse? libsdl1.2debian-pulseaudio? I never used to need this extra rubbish....

From a slightly concerned Ubuntu lover.


p.s. 
lspci shows:
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)

p.p.s.
I see also that the Preferences->Sound->Sounds Tab gives me the option to untick Enable software sound mixing (ESD), log-out and in again, and then to have my media fun. Yeah, sorry - not good enough guys! It should Just Work!

p.p.p.s.
Yes, I know that ESD has actually been in Ubuntu for ages. When I have actually used vanilla Ubuntu in the past, ESD has always been disabled, if not in fact deleted from the filesystem, to the general betterment of the system and all human life in general. (ESD was always a sad creature.) My points and questions above still hold.

---

### Post by smokiemac on 2008-07-15
i am having the same problem where cant run sound applications and still get sound from firefox. didnt have same problem with fedora so i am going to be patient and wait to see if it gets fixed in any updates not that big a deal to me to close rhythmbox to watch utube... but would be nice if it wasnt using pulseaudio.

---

### Post by tomjennings on 2008-07-15
No, it's bad. Features? More like creeping featuritis.

Too many damn layers to configure. I honestly have a hard time grokking what  the many layers of sound control do and how they interact, never mind how to configure them.

And sound apps like audacity bloat as well. (For some reason my audacity insists on launching jackd, even when no 'jack' feature or item is selected in it's config. And I rm -r .audacity-data to be sure. I have to start audacity, kill jackd, then use audacity. THAT was not fun to discover.)

I realise this stuff grew organically, but sheesh, it did get good (better) before pulseaudio came on the scene.

And I STILL have old-fashioned problems like having to killall firefox before I can use various sound programs. Even when the window that was using sound is closed. Something's leaving a handle open. Whatever.

It's not bad that these tools exist -- it's bad that all the bells and whistles are turned on by default. 

On my DJ machine OK, I use jack, adjusted for low latency etc, but even there, RELIABILITY is worth more than 1000 feetches. On my laptop, and my work machine, I play audio, web browse, etc, like millions of other n00bs. It's pretty bad.

---

### Post by sdennie on 2008-07-15
I would agree that the inclusion of Pulse Audio was not a good idea.  I understand this is an LTS release and so some things were crammed in so that the release would still be viable years after launch.  However, unlike FF3 (shaky at launch but certainly the right thing to include), Pulse Audio doesn't solve any widespread complaints about the Ubuntu audio system and in fact brings problems to huge numbers of users (I bet that I've personally answered at least 25-50 posts related to Pulse Audio breaking previous audio behavior).  The only thing that it offers that the average user would likely to find very beneficial is the ability to have a system wide/application equalizer yet, that functionality isn't even installed by default and must be hand configured by the user.

Luckily, there is an easy workaround (and in fact, is the first thing I do whenever I install Hardy on a new machine).  Go to System->Preferences->Sound and change everything to ALSA.  You sometimes have to tell individual apps to use ALSA instead of Pulse Audio as well but, this is far easier than dealing with Pulse Audio in my opinion.

---

### Post by markbuntu on 2008-07-15
The big problem with pulseaudio is that it is still basically a beta. It has lots of bugs and is missing some critical pieces OOTB. Why would they not include plugins for xmms or oss? or the Pulse Audio Manager? I am baffled about this.

It took me weeks to get my sound working properly and basically now I have Pulse Audio using ALSA and ALSA apps and all the ALSA plugins and wrappers going through Pulse so that all the buggy PA apps like audacious and flash don't hog the sound card. Someday, I will try to get jack to work with this but I have low expectations since pulse provides another mostly unecessary layer of management that puts a big hit on latency.

I can understand, in a sort of non-sympathetic way why they would choose to include this nightmare in a LTS release, the same reason they gave us that bugfarm of a firefox. it leaves an easier path for the devs.

But, to me this goes completely against the Ubuntu philosophy that everything should "just work". Spending 3 weeks getting my sound in order "just doesn't work". If I was younger and less patient and did not have so much free time, Ubuntu would have been kicked to the curb a long time ago over this issue.

---

### Post by Prinny_SoFaRo on 2008-07-15
Hmm...

I'm removing all the PulseAudio packages now...but it says it's going to remove all my media players and such, too...

So...basically, "Ubuntu Studio" is a contradiction in terms, then? Because not one of the sound recorders has worked, and that's generally the sort of activity one would associate with a studio, right?

Meh. Hopefully getting this crap out of the system will fix them...though, since all the packages I actually use seem to be being removed, I doubt it will...

Anyone have a workaround, should I need to choose between having sound and being free of this PA rubbish?

Besides setting everything to ALSA, I mean--that doesn't even work quite right, I'm afraid...

---

### Post by YaroMan86 on 2008-07-15
Before Hardy Heron, PulseAudio caused way more problems than it solved. To the point where even removing it complete with configuration purge still left half my sound crippled with only a re-install to fix it. (I was still relatively new to Ubuntu and Linux altogether, so I wasn't sure what configuration files where were changed. I'm still not sure but I bet I'd be able to fix the problem now rather than then.)

It seems to have worked really well for me in Hardy, though.

---

### Post by jocheem67 on 2008-07-16
I agree with the above, I'm not too fond of pulse...doesn't work on my production-rig.
alsa is there without any probs, but the whole pulse daemon won't even start, let alone recognize my soundcard which is a well known m-audio delta 1010lt.
I'm pretty confident compiling stuff: so I decided to start pulse from scratch...pfffff...got myself into a big messy dependency-hell which I haven't encountered for a long time using ubuntu.
My opinion: when the advantages of pulse aren't that obvious, they are kind of "thin" , why bother using such a still beta framework? Alsa is okay, is well developed into a nice stable environment...

On the other hand, Now I've got some work to do which is okay for me and you guys above, but not for the newbies...they'll be driven into using MS once more. Pity.

---

### Post by Mark Phelps on 2008-07-16
Sorry, but I have to agree -- PulseAudio is way too difficult to get working.  I spent hours going through the How-to, step by step, and what was the result?  The only sound app that worked was XMMS -- and that's probably because it did NOT use Pulse.

So, I followed the How-to instructions on removing Pulse and then what? I got no sound.  Great.

Fortunately, I made a complete backup using PartImage before messing around with Pulse, so I was able to restore my machine.

And yeah, I know that getting new stuff to work in Linux is SUPPOSED to be challenging -- but pages and pages of How-to just to get audio working, that's obviously a Work In Progress, not a finished product.

So, I'm back to using ALSA and/or OSS (under 8.04), and it works fine.

---

### Post by galileon on 2008-07-16
i went thru quite a few how-tos and very nearly downgraded to gutsy to get sound working properly. however, these two links helped me, so in the hope its useful to someone else:

[http://www.lockergnome.com/eksodos/2008/06/24/getting-flash-to-play-nice-with-pulseaudio-in-ubuntu-without-crashing/](http://www.lockergnome.com/eksodos/2008/06/24/getting-flash-to-play-nice-with-pulseaudio-in-ubuntu-without-crashing/)

[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

---

### Post by wkulecz on 2008-07-16
For me, Pulse Audio is all pain and zero gain. Stuff that used to work doesn't, whatever fancy stuff it is supposed to do I just don't need.  The sound subsystem in 6.06 met all my needs, the "upgrade" has been a serious regression, if sound were mission critical I'd have rolled back to 6.06 immediately.

It should have crept in as an addon or alternative for those who need what "advantages" it offers -- sound over a network? I get all the sound I need over a network by playing mp3 files from a network share!

--wally.

---

### Post by atari130xe on 2008-08-03
I Totally agree with the person who has opened this thread. Till Ubuntu 7.10 sounds on my pc worked very well. I had many expectations about PulseAudio but it was a pain for me. Playing videos on youtube + chatting on emesene = one of the apps hanged, "sound server is busy" yuk. I love Ubuntu I have changed from XP to Ubuntu 2 years ago and didnt go back. I think ubuntu developers should review about the inclusion of PulseAudio waiting for a little bit more stable version. The "solution" came to me thanks to Markbuntu, I have uninstalled and replaced pulseaudio for Esound, now my pc plays startup and shutdown sounds, and ALL sounds from MANY different sources without any problem.

---

### Post by MillDaKill on 2008-08-04
I have to say that pulseaudio has caused me nothing but trouble.  Basically I just have to live with having audio available for about 20 minutes at a time, and then my pulse instance dies and I have to restart PA and all the apps that crashed with pulse.  I would sure hope that the cost we are all paying right now pays off with a kick-*** pulseaudio server in a year or so that has a per application EQ that works like the per application volume control.  It actually amazes me that the EQ wasnt developed before the per application volume.

---

