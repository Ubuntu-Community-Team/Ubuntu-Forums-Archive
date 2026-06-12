---
title: "Getting sound in Flash"
date: 2007-01-13
forum: Multimedia &amp; Video
---

### Post by malfist on 2007-01-13
I once opon a time had sound for flash, that was when I let ubuntu do the work and installed the default plug-in for flash. But then I came across a problem, most flash things where telling me I needed to update to a newer version or weren't working quite right. So I check the help files in the documentation online and installed the firefox-flash plugin (I'm using firefox) but now none are telling me to update but some are still not working right (like some flash chatrooms) and there is absolutly no sound. Because I prefer sound and what little was working I uninstalled the firefox-flash plugin and reinstalled the other one. And nothing seemed to change. Does anyone know how to activate sound on flash apps? I can't watch youtube anymore.

---

### Post by gilgongo on 2007-01-13
THis may not be your problem, but I had no sound with Flash on Breezy until I discovered alsamixer.

Go to the console and type "alsamixer" - you will see the ugliest utility known to man, but it may be that for some reason something is muted (it'll have "MM" at the bottom, or the lever will be very low. Use the cursor keys to navigate and use the "m" key to toggle muting.

Hit escape to save the changes and quit. Does that change anything?

---

### Post by malfist on 2007-01-13
I have sound otherwise but only not in flash. The alsamixer had a few things muted and I unmuted them and turned them up (minus the line-in, I don't use it) but it didn't fix anything.

---

### Post by obsidion on 2007-01-13
Try this

Howto fix Firefox Flash Video Sound on Ubuntu Linux Dapper

If after a system update you’ve discovered that streaming Flash is without sound - fear not. Dapper will at times drop the sound from Firefox & Flash, as always you need to search the forums before freaking out as someone has more than likely already experienced the problem and discovered a solution. Trial and error has lead me to the following fix on my system.

sudo aptitude install alsa-oss
sudo gedit /etc/firefox/firefoxrc

FIREFOX_DSP=”aoss”

[http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/](http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/)

---

### Post by malfist on 2007-01-13
I'm not using dapper, I'm in Edgy

---

### Post by obsidion on 2007-01-13
> **malfist said:**
> I'm not using dapper, I'm in Edgy

  So put it in your profile so others will know that too

---

### Post by obsidion on 2007-01-13
> **malfist said:**
> I'm not using dapper, I'm in Edgy


  Did you try it or did you just go,,,I'm not using dapper so it won't work ?

---

### Post by malfist on 2007-01-16
No I haven't tried it because unfortanatly I was taken away from that computer and wont be back on it for another day or so and had no chance to test it. I will do so as soon as possiable.

---

### Post by philh99 on 2007-01-16
You need to use Adobe Flash Player 9 Beta.
Download it from here - [http://labs.adobe.com/downloads/flashplayer9.html]("http://labs.adobe.com/downloads/flashplayer9.html")
Then, extract the file to your home folder/.mozilla/plugins.

If the file directory doesn't exist, then you will need to create.
If the file exists, back it up and replace with this one.

It will now work fine.

---

### Post by gray-squirrel on 2007-01-16
> **philh99 said:**
> You need to use Adobe Flash Player 9 Beta.
Download it from here - [http://labs.adobe.com/downloads/flashplayer9.html]("http://labs.adobe.com/downloads/flashplayer9.html")
Then, extract the file to your home folder/.mozilla/plugins.

If the file directory doesn't exist, then you will need to create.
If the file exists, back it up and replace with this one.

It will now work fine.

I've tried this without success.  I even had to reboot the computer to try to make Flash work, but that had no effect.  Yesterday, I also noticed a Flash 9 in the Dapper repos, which did not correct the lack of sound problem.

The [FONT="Courier New"]firefoxrc[/FONT] file I have has always had the [FONT="Courier New"]FIREFOX_DSP=”aoss”[/FONT] line in it, and [FONT="Courier New"]alsa-oss[/FONT] is installed as well.

I suspect the problem for some is deeper than what's been discussed so far.  If anyone has any suggestions on how I can investigate further, please let me know.  I went through Google and [Clusty]("http://www.clusty.com") and have only been able to find as solutions what has been discussed here so far.

---

### Post by nbayiha on 2007-01-16
You're not the only one to have this problem.
i follow a lot of thread , and did all what is written up, but i still didn't manage to make the sound run. And watching smth without  sound ??? :( :( :( 
if i could read in the lips :-k :-k :-k

I'm using edgy in hp dv6040us

---

### Post by obsidion on 2007-01-16
> **gray-squirrel said:**
> I've tried this without success.  I even had to reboot the computer to try to make Flash work, but that had no effect.  Yesterday, I also noticed a Flash 9 in the Dapper repos, which did not correct the lack of sound problem.

The [FONT="Courier New"]firefoxrc[/FONT] file I have has always had the [FONT="Courier New"]FIREFOX_DSP=”aoss”[/FONT] line in it, and [FONT="Courier New"]alsa-oss[/FONT] is installed as well.

I suspect the problem for some is deeper than what's been discussed so far.  If anyone has any suggestions on how I can investigate further, please let me know.  I went through Google and [Clusty]("http://www.clusty.com") and have only been able to find as solutions what has been discussed here so far.

  Try taking it out instead then, computers can be contrary things and fixes like this are only a guide. It can be any combination of things, from the software installed to the sound daemon you are using to the soundcard. Basically they all have to talk together and like families everywhere sometimes forget and need a kick to make them do it :)

---

### Post by malfist on 2007-01-17
I followed those instructions. After I edited the file to say aoss instead of none I get the 'no flash player' error when I try to play flash. I then installed the plash plugin from adobe and same thing.

Now I'm stuck with no flash

---

### Post by nbayiha on 2007-01-17
which version of alsa are you using??

---

### Post by gray-squirrel on 2007-01-18
> **nbayiha said:**
> which version of alsa are you using??


Version 1.0.10 under Dapper.  I'm using the [FONT="Courier New"]alsa-base[/FONT] package which was installed by default.

---

### Post by nbayiha on 2007-01-19
First of all be sure that you already have lib32asound installed ,

if you do so , check if the sound work , if not ; follow this thread 

[http://www.ubuntuforums.org/showthread.php?t=277077](http://www.ubuntuforums.org/showthread.php?t=277077)

but before following this thread make sure you have this repository already installed

[http://www.ubuntuforums.org/showthread.php?t=196093&highlight=amd64+repository](http://www.ubuntuforums.org/showthread.php?t=196093&highlight=amd64+repository)

installed the one which suit for your ubuntu version. and don't forget to update and upgrade :rolleyes:  after installing the repository.

i guess after that you should have everything working.

and smth else :-k :-k  try to run firefox throw  the terminal and go to  youtube  watch a movies and tell us what's written in the terminal. 

i hope this will help you :D :D and help us helping you ;-)

---

### Post by gray-squirrel on 2007-01-19
Thanks.  I'll check on the status of [FONT="Courier New"]lib32asound[/FONT] later this evening when I'm at my computer.  The strange thing is that sound works otherwise, except when a Flash page shows up, in which case the Web browser hijacks the sound card, and I get no sound until I close the browser.  This happens regardless of whether I use Firefox, Konqueror, or Mozilla.

I have run Firefox via the terminal previously, and don't get anything displayed on the terminal when attempting to play YouTube videos.  I'll see if I can force it to crash later, and see if I can get sound library-related error messages which I can post later.

I'm not running 64-bit Kubuntu, so I would not need additional repositories.

---

### Post by gray-squirrel on 2007-01-20
I don't have [FONT="Courier New"]lib32asound[/FONT], but that is probably because I am not running the 64-bit version of Kubuntu.

Here's what happened before a recent Firefox crash which was the eventual result of my playing a Flash video within it:

```
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open files
ALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open files
ALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
./run-mozilla.sh: line 131: 26805 Segmentation fault      "$prog" ${1+"$@"}
```

I apologize for not being able to get all of the messages, the first six lines before the seg fault error repeated dozens of times and anything which may have happened before had been pushed out of the terminal's buffer.  I was not able to keep up with the messages.

I have also attached terminal output while running a YouTube video under Konqueror.  I never have been able to get Konqueror to crash, however.  The ALSA error messages run ad infinitum, so I had to close the Web session before I lost any information which may have revealed the cause of them.  And, I had to cut most of those lines (there are three which run repetitively) so that it could be uploaded here.

---

### Post by bartek on 2007-03-27
i hate to bring old threads back to life, but I'm having the same issue on a brand new Edgy install - no sound in Firefox, Konqueror or Opera playing YouTube videos. I have sound with everything else - any fixes since this was posted?

---

### Post by gray-squirrel on 2007-07-08
> **bartek said:**
> i hate to bring old threads back to life, but I'm having the same issue on a brand new Edgy install - no sound in Firefox, Konqueror or Opera playing YouTube videos. I have sound with everything else - any fixes since this was posted?

Not a problem.  I stumbled onto something recently which may help if all else fails.

For those with sound cards without hardware mixing capability, you may have a config file (either [FONT="Courier New"].asoundrc[/FONT] or [FONT="Courier New"]/etc/asound.conf[/FONT]) which sets up the [FONT="Courier New"]dmix[/FONT] plugin so you can have software mixing capability.  I found out - and I can't remember where I read this unfortunately - that versions 1.0.9 and later of ALSA have [FONT="Courier New"]dmix[/FONT] enabled by default, so there's no need to have the [FONT="Courier New"]dmix[/FONT] setup in your ALSA config file.  That was the only thing I had in mine, so I removed [FONT="Courier New"].asoundrc[/FONT] from my computer, and, surprisingly enough, Flash videos were once again audible - plus, I still have my system sounds (and I can use Amarok simultaneously if I so choose).  If you have Edgy or Feisty (or possibly Dapper, but I haven't upgraded to Flash 9 on another partition containing Dapper yet), give this a shot and see what happens.

I was expecting to lose other sounds while Flash videos were playing, just like back in the days when I was trying desperately shut down aRts and OSS while trying to keep ALSA running during my switch from Gnome to KDE.  Fortunately, that didn't happen this time.  8)  So far, I have had success with Flash using Konqueror and Seamonkey.  I'll cross my fingers and try this with Firefox. . . Swiftfox tomorrow.

I wish I found out about the nice development in ALSA earlier, though. . . I don't always have time to stop just to dual-boot into Windows for trouble-free Web browsing - especially when most of my other productive work (e-mail, Web design, writing) is done in Kubuntu.

---

### Post by RealG187 on 2007-07-09
> **obsidion said:**
> So put it in your profile so others will know that too

not always fool proof, peps could forget to update or have muitiple machines, or in my case have Kubuntu (see my sig).

anyways come to think of it today i ran an swf in konqueror and got no sound!

---

