---
title: "[SOLVED] Error using Mono in 8.04 (possible problem with repositories?)"
date: 2008-04-18
forum: Mythbuntu
---

### Post by amphibem on 2008-04-18
I have just upgraded to 8.04 Beta (as a re-install was required anyway) and am now having no luck running xmlTVNZ with Mono. xmlTVNZ does exactly the same as xmlTV, just for New Zealand TV.

So I try run xmlTVNZ (see instructions here [http://www.reven.co.nz/xmlTVNZ/Guides/LinuxGuide.aspx](http://www.reven.co.nz/xmlTVNZ/Guides/LinuxGuide.aspx)) and get the following error:

"mono: error while loading sharwd libraries: libgthread-2.0.so.0: cannot open shared object file: No such file or directory"

Also, when installing mono it completes but at the end gives me a long list of packages that it failed to install. I have tried searching for a few of them (including the specific error above) in Synaptic with no luck.

I have tried changing repositries and fiddling with other such settings and still have both these problems. Off both the 'Main Server' and NZ server I get errors saying it cannot locate all repositries or the like. This cuased me issues right at the start when i couldn't install mythtv-backend-master until I changed to the main server.


I guess many people don't use Mono/xmlTVNZ here, but does anyone know what the issue is with not being able to find repositries in 8.04?

---

### Post by KillerKiwi on 2008-04-20
Just tried it with all updates from today installed using 

 mono xmlTVNZ.exe tvguide.xml -days 5 default_tv1

Works fine note thats version 3... version 2 of xmlTVNZ is broken

```
mono xmlTVNZ.exe tvguide.xml -days 5 default_tv1
Using Debug File: Logging/xmlTVNZ 2008-04-21 09.44.30.log
xmlTVNZ v3.0.0.11
No xmlTVNZ Update Available
Getting info for channel: TV1 on TVNZ at 21 April 2008 00:00
Getting info for channel: TV1 on TVNZ at 22 April 2008 00:00
Getting info for channel: TV1 on TVNZ at 23 April 2008 00:00
Getting info for channel: TV1 on TVNZ at 24 April 2008 00:00
Getting info for channel: TV1 on TVNZ at 25 April 2008 00:00
Channel 'TV1' found 125 shows from 'TVNZ'

Time taken: 0:00:16.0300

```

---

### Post by amphibem on 2008-04-20
I did try this this with v3.0 RC and still got errors, now re-installing with 8.04 RC as I mucked around with Mono and mythfilldatabase so much I probably made a mess somewhere.

Will get back once I have tried it out on fresh install.

---

### Post by amphibem on 2008-04-20
Wow this is getting ridiculously fustrating. I now cant seem to run the Mono installer:

```
sudo chmod +x mono-1.9_5-installer.bin
[Type password]
./mono-1.9_5-installer.bin
```

And nothing happens. Is there something I am missing here? Is there another way to get mono?

---

### Post by Lindsay.Mathieson on 2008-04-20
Did you run the mono installer using sudo?

Also [BadgerPorts]("http://directhex.mfgames.com/hardy.html") is a ubuntu repository with the latest mono debs (1.9+dfsg-2~dhx2). You could add it to your /etc/apt/sources.lst Easier/safer than installing an non-packaged mon.

---

### Post by amphibem on 2008-04-20
Thank you! xmlTVNZ has successfully downloaded data.

One last step, mythfilldatabase gives me this:

```
2008-04-21 11:51:35.692 Unknown xmltv channel identifier: c4 - Skipping channel.
2008-04-21 11:51:35.693 Unknown xmltv channel identifier: prime - Skipping channel.
2008-04-21 11:51:35.694 Unknown xmltv channel identifier: tv1 - Skipping channel.
2008-04-21 11:51:35.695 Unknown xmltv channel identifier: tv2 - Skipping channel.
2008-04-21 11:51:35.696 Unknown xmltv channel identifier: tv3 - Skipping channel.

```

I have done a manual setup and numbered TV1 as 1, Tv2 as 2 and so on (as in the Channel ID's) and this keeps happening. I did have this working on my old install but I can't figure out where I am going wrong. How did you set things up in the mythfilldatabase --manual run?


OK all fixed, see here:

[HTML]http://ubuntuforums.org/showthread.php?p=4755675#post4755675[/HTML]

Wrong options in mythfilldatabase :P

---

### Post by Lindsay.Mathieson on 2008-04-21
> **amphibem said:**
> Thank you! xmlTVNZ has successfully downloaded data.


OK all fixed, see here:



Excellent.

Hows the state of Digital TV in NZ these days? been a while since I was back but I have hopes :)

Much free content?

---

### Post by amphibem on 2008-04-21
Well the Over The Air Digital servive, called Freeview HD has just launched, and as soon as my Nova T 500 arrives I will have 720p for TV1 & and TV2, and 1080i TV3. Now as the TV in my flat only does 800x600 I won't be seeing HD, but as soon as I can get my own TV... :)

Not much in extra content over analog, some extra TVNZ channels that don't look very interesting. Still, it is cool that we are getting HD Free-To-Air straight up.

---

