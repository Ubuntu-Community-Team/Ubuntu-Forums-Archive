---
title: "Adobe Flash crash---Just started... Help"
date: 2009-06-05
forum: Multimedia Software
---

### Post by HunterThomson on 2009-06-05
Thank you for reading this :)

All was working well then up date and now adobe flash is broken. 
Where can I look to see what packages were updated in Ubuntu ? That way next time I will problay be able to fix stuff like this myself?

Anyway, Here is what happens.
All is playing fine then Wham! CPU at 100% and no sound but video keeps playing. It is vary random it mite happen in 2 sec's or it mite be 1hr into the video.

Here are the facts.
-In Firefox

-No compiz or any composite manager at all running.

-Tried both the Ubuntu outdated 32bit Adobe flash plug-in and the native 64bit Adobe flash plug-in (both the same problem)

-No other flash like gnash installed. (To bad gnash is outdated it use to work vary well)

-Doesn't matter what site I go to Youtube, Hulu, Revision3...

-Video driver Catalyst 9.5

-OpenBox WM >In Gnome

Boy it must have been something that was updated and that is conflicting with flash now because it is not Adobe Flash seeing as how I tried the 32bit flash form the repo's and the new 64bit native adobe flash form the adobe web site. It could be my dam ATI graphics card and ATI's POS driver. However, all was working fine until last night and nether Xserver nor the Catalyst were updated... But you know Ubuntu....

---

### Post by HunterThomson on 2009-06-05
O ok I found the log it is in /var/log/apt

Didn't really see anything that stands out as the problem.... here is the log
```

(Reading database ... 136681 files and directories currently installed.)

Preparing to replace foomatic-db-engine 4.0.0-0ubuntu6 (using .../foomatic-db-engine_4.0.0-0ubuntu6.1_amd64.deb) ...

Unpacking replacement foomatic-db-engine ...

Preparing to replace libsqlite3-0 3.6.10-1 (using .../libsqlite3-0_3.6.10-1ubuntu0.2_amd64.deb) ...

Unpacking replacement libsqlite3-0 ...

Preparing to replace libcups2 1.3.9-17ubuntu3 (using .../libcups2_1.3.9-17ubuntu3.1_amd64.deb) ...

Unpacking replacement libcups2 ...

Preparing to replace libcupsimage2 1.3.9-17ubuntu3 (using .../libcupsimage2_1.3.9-17ubuntu3.1_amd64.deb) ...

Unpacking replacement libcupsimage2 ...

Preparing to replace cups-common 1.3.9-17ubuntu3 (using .../cups-common_1.3.9-17ubuntu3.1_all.deb) ...

Unpacking replacement cups-common ...

Preparing to replace cups 1.3.9-17ubuntu3 (using .../cups_1.3.9-17ubuntu3.1_amd64.deb) ...

 * Stopping Common Unix Printing System: cupsd

   ...done.

Unpacking replacement cups ...

Preparing to replace cups-bsd 1.3.9-17ubuntu3 (using .../cups-bsd_1.3.9-17ubuntu3.1_amd64.deb) ...

Unpacking replacement cups-bsd ...

Preparing to replace cups-client 1.3.9-17ubuntu3 (using .../cups-client_1.3.9-17ubuntu3.1_amd64.deb) ...

Unpacking replacement cups-client ...

Preparing to replace libedataserver1.2-11 2.26.1-0ubuntu1 (using .../libedataserver1.2-11_2.26.1-0ubuntu2_amd64.deb) ...

Unpacking replacement libedataserver1.2-11 ...

Preparing to replace libcamel1.2-14 2.26.1-0ubuntu1 (using .../libcamel1.2-14_2.26.1-0ubuntu2_amd64.deb) ...

Unpacking replacement libcamel1.2-14 ...

Preparing to replace libebackend1.2-0 2.26.1-0ubuntu1 (using .../libebackend1.2-0_2.26.1-0ubuntu2_amd64.deb) ...

Unpacking replacement libebackend1.2-0 ...

Preparing to replace libebook1.2-9 2.26.1-0ubuntu1 (using .../libebook1.2-9_2.26.1-0ubuntu2_amd64.deb) ...

Unpacking replacement libebook1.2-9 ...

Preparing to replace libecal1.2-7 2.26.1-0ubuntu1 (using .../libecal1.2-7_2.26.1-0ubuntu2_amd64.deb) ...

Unpacking replacement libecal1.2-7 ...

Preparing to replace libedata-book1.2-2 2.26.1-0ubuntu1 (using .../libedata-book1.2-2_2.26.1-0ubuntu2_amd64.deb) ...

Unpacking replacement libedata-book1.2-2 ...

Preparing to replace libedata-cal1.2-6 2.26.1-0ubuntu1 (using .../libedata-cal1.2-6_2.26.1-0ubuntu2_amd64.deb) ...

Unpacking replacement libedata-cal1.2-6 ...

Preparing to replace libegroupwise1.2-13 2.26.1-0ubuntu1 (using .../libegroupwise1.2-13_2.26.1-0ubuntu2_amd64.deb) ...

Unpacking replacement libegroupwise1.2-13 ...

Preparing to replace libgdata1.2-1 2.26.1-0ubuntu1 (using .../libgdata1.2-1_2.26.1-0ubuntu2_amd64.deb) ...

Unpacking replacement libgdata1.2-1 ...

Preparing to replace libgdata-google1.2-1 2.26.1-0ubuntu1 (using .../libgdata-google1.2-1_2.26.1-0ubuntu2_amd64.deb) ...

Unpacking replacement libgdata-google1.2-1 ...

Preparing to replace evolution-data-server 2.26.1-0ubuntu1 (using .../evolution-data-server_2.26.1-0ubuntu2_amd64.deb) ...

Unpacking replacement evolution-data-server ...

Preparing to replace evolution-data-server-common 2.26.1-0ubuntu1 (using .../evolution-data-server-common_2.26.1-0ubuntu2_all.deb) ...

Unpacking replacement evolution-data-server-common ...

Preparing to replace libedataserverui1.2-8 2.26.1-0ubuntu1 (using .../libedataserverui1.2-8_2.26.1-0ubuntu2_amd64.deb) ...

Unpacking replacement libedataserverui1.2-8 ...

Preparing to replace libexchange-storage1.2-3 2.26.1-0ubuntu1 (using .../libexchange-storage1.2-3_2.26.1-0ubuntu2_amd64.deb) ...

Unpacking replacement libexchange-storage1.2-3 ...

Preparing to replace evolution 2.26.1-0ubuntu1 (using .../evolution_2.26.1-0ubuntu2_amd64.deb) ...

Unpacking replacement evolution ...

Preparing to replace evolution-common 2.26.1-0ubuntu1 (using .../evolution-common_2.26.1-0ubuntu2_all.deb) ...

Unpacking replacement evolution-common ...

Preparing to replace evolution-plugins 2.26.1-0ubuntu1 (using .../evolution-plugins_2.26.1-0ubuntu2_amd64.deb) ...

Unpacking replacement evolution-plugins ...

Preparing to replace metacity-common 1:2.25.144-0ubuntu2 (using .../metacity-common_1%3a2.25.144-0ubuntu2.1_all.deb) ...

Unpacking replacement metacity-common ...

Preparing to replace libmetacity0 1:2.25.144-0ubuntu2 (using .../libmetacity0_1%3a2.25.144-0ubuntu2.1_amd64.deb) ...

Unpacking replacement libmetacity0 ...

Preparing to replace mysql-common 5.1.30really5.0.75-0ubuntu10 (using .../mysql-common_5.1.30really5.0.75-0ubuntu10.2_all.deb) ...

Unpacking replacement mysql-common ...

Preparing to replace libmysqlclient15off 5.1.30really5.0.75-0ubuntu10 (using .../libmysqlclient15off_5.1.30really5.0.75-0ubuntu10.2_amd64.deb) ...

Unpacking replacement libmysqlclient15off ...

Preparing to replace libpurple-bin 1:2.5.5-1ubuntu8 (using .../libpurple-bin_1%3a2.5.5-1ubuntu8.1_all.deb) ...

Unpacking replacement libpurple-bin ...

Preparing to replace pidgin-data 1:2.5.5-1ubuntu8 (using .../pidgin-data_1%3a2.5.5-1ubuntu8.1_all.deb) ...

Unpacking replacement pidgin-data ...

Preparing to replace libpurple0 1:2.5.5-1ubuntu8 (using .../libpurple0_1%3a2.5.5-1ubuntu8.1_amd64.deb) ...

Unpacking replacement libpurple0 ...

Preparing to replace metacity 1:2.25.144-0ubuntu2 (using .../metacity_1%3a2.25.144-0ubuntu2.1_amd64.deb) ...

Unpacking replacement metacity ...

Preparing to replace pidgin 1:2.5.5-1ubuntu8 (using .../pidgin_1%3a2.5.5-1ubuntu8.1_amd64.deb) ...

Unpacking replacement pidgin ...

Preparing to replace evolution-documentation-en 2.26.1-0ubuntu1 (using .../evolution-documentation-en_2.26.1-0ubuntu2_all.deb) ...

Unpacking replacement evolution-documentation-en ...

Preparing to replace gnome-settings-daemon 2.26.1-0ubuntu1 (using .../gnome-settings-daemon_2.26.1-0ubuntu2_amd64.deb) ...

Unpacking replacement gnome-settings-daemon ...

Processing triggers for man-db ...

Processing triggers for doc-base ...

Processing 1 changed doc-base file(s)...

Registering documents with scrollkeeper...

Processing triggers for ufw ...

Processing triggers for menu ...
Setting up foomatic-db-engine (4.0.0-0ubuntu6.1) ...



Setting up libsqlite3-0 (3.6.10-1ubuntu0.2) ...



Setting up libcups2 (1.3.9-17ubuntu3.1) ...



Setting up libcupsimage2 (1.3.9-17ubuntu3.1) ...



Setting up cups-common (1.3.9-17ubuntu3.1) ...

Setting up cups (1.3.9-17ubuntu3.1) ...

 * Reloading AppArmor profiles ...

   ...done.

 * Starting Common Unix Printing System: cupsd

   ...done.



Setting up cups-client (1.3.9-17ubuntu3.1) ...



Setting up cups-bsd (1.3.9-17ubuntu3.1) ...



Setting up libedataserver1.2-11 (2.26.1-0ubuntu2) ...



Setting up libcamel1.2-14 (2.26.1-0ubuntu2) ...



Setting up libebackend1.2-0 (2.26.1-0ubuntu2) ...



Setting up libebook1.2-9 (2.26.1-0ubuntu2) ...



Setting up libecal1.2-7 (2.26.1-0ubuntu2) ...



Setting up libedata-book1.2-2 (2.26.1-0ubuntu2) ...



Setting up libedata-cal1.2-6 (2.26.1-0ubuntu2) ...



Setting up libegroupwise1.2-13 (2.26.1-0ubuntu2) ...



Setting up libgdata1.2-1 (2.26.1-0ubuntu2) ...



Setting up libgdata-google1.2-1 (2.26.1-0ubuntu2) ...



Setting up evolution-data-server-common (2.26.1-0ubuntu2) ...

Setting up evolution-data-server (2.26.1-0ubuntu2) ...

Setting up libedataserverui1.2-8 (2.26.1-0ubuntu2) ...



Setting up libexchange-storage1.2-3 (2.26.1-0ubuntu2) ...



Setting up evolution-common (2.26.1-0ubuntu2) ...



Setting up evolution (2.26.1-0ubuntu2) ...



Setting up evolution-plugins (2.26.1-0ubuntu2) ...

Setting up metacity-common (1:2.25.144-0ubuntu2.1) ...



Setting up libmetacity0 (1:2.25.144-0ubuntu2.1) ...



Setting up mysql-common (5.1.30really5.0.75-0ubuntu10.2) ...

Setting up libmysqlclient15off (5.1.30really5.0.75-0ubuntu10.2) ...



Setting up libpurple-bin (1:2.5.5-1ubuntu8.1) ...

Setting up pidgin-data (1:2.5.5-1ubuntu8.1) ...



Setting up libpurple0 (1:2.5.5-1ubuntu8.1) ...



Setting up metacity (1:2.25.144-0ubuntu2.1) ...



Setting up pidgin (1:2.5.5-1ubuntu8.1) ...



Setting up evolution-documentation-en (2.26.1-0ubuntu2) ...



Setting up gnome-settings-daemon (2.26.1-0ubuntu2) ...
```

---

### Post by lovinglinux on 2009-06-05
That update actually increased Firefox performance on my system, which is probably due to libsqlite3, since SQLite databases are also running more efficiently now.

BTW, I'm having the same problem with Firefox since the release of Jaunty.

---

### Post by HunterThomson on 2009-06-05
If there is a different web-browser that you think could work or some way to make gnash work let me know.

---

### Post by HunterThomson on 2009-06-05
> **lovinglinux said:**
> That update actually increased Firefox performance on my system, which is probably due to libsqlite3, since SQLite databases are also running more efficiently now.

Try to create a new profile for Firefox and check if it exhibit the same symptoms.

BTW, I'm having the same problem with Firefox since the release of Jaunty.

Hum how do I make a new profile? Sorry I have never done that.
Never mind I am on it.

---

### Post by lovinglinux on 2009-06-05
> **HunterThomson said:**
> If there is a different web-browser that you think could work or some way to make gnash work let me know.

Tested Flash on several browsers and it sucks on all of them.

> **HunterThomson said:**
> Hum how do I make a new profile? Sorry I have never done that.

Sorry, I removed that suggestion from my previous post, because I think it won't help. I guess I should get some sleep before posting. Anyways, to create a new profile, start Firefox from terminal with this command:

```
firefox -P
```

---

### Post by HunterThomson on 2009-06-05
> **lovinglinux said:**
> Tested Flash on several browsers and it sucks on all of them.



Sorry, I removed that suggestion from my previous post, because I think it won't help. I guess I should get some sleep before posting. Anyways, to create a new profile, start Firefox from terminal with this command:

```
firefox -P
```

Ok cool, well you did remind me that I should try removing firefox and deleting ~/.mozilla/firefox and reinstalling. So, well see if that works. Thanks for bringing that vary oveous thing to my mind that I forgot about.

Thats why two minds are better then one :P

Hope it works but we'll see....

---

### Post by HunterThomson on 2009-06-05
Nope same problem that started after toughs updates...

This really ******* sucks. I don't have a TV. I live on Flash.... I have alredy downloaed every torrented movie I can find that is worth watching. AND NO Hak5 or Diggnation !

---

### Post by lovinglinux on 2009-06-05
> **HunterThomson said:**
> Nope same problem that started after toughs updates...

This really ******* sucks. I don't have a TV. I live on Flash.... I have alredy downloaed every torrented movie I can find that is worth watching. AND NO Hak5 or Diggnation !

You might want to check my threads about flash problems and Jaunty performance, maybe they will help you:

[http://ubuntuforums.org/showthread.php?t=1152095](http://ubuntuforums.org/showthread.php?t=1152095)
[http://ubuntuforums.org/showthread.php?t=1146943](http://ubuntuforums.org/showthread.php?t=1146943)

---

### Post by HunterThomson on 2009-06-05
Hum, ya it looks like there are quite a few things to try, reading them now.

What gits me though is that I never had a problem until that update... the problem must be in there.

I have made a bootable USB that I can use to watch videos now. It is a super pain in the *** but at lest I can watch Hak5, diggnation, and stuff on hulu.

Still up for any suggestions.

---

### Post by HunterThomson on 2009-06-06
Well, ThankYou lovinglinux. 

Boy, I really hope I didn't jump the gun on that.....

But, it seems I have fixed the problem. I just watched a whole 1 1/2 hr movie on Hulu and didn't have a problem.

This is what I did.

First I...

```
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
```

After this, in hulu it would be the same problem kind of. Like, it would not play the video but play the sound then after the sound was finished it would play the video realy fast. This would happen before. 

The thing that changed was the when it would freak out and do that the CUP "Did Not" go to 100%.... So, I thought "Well half way there..."

Then I was thinking, "hell I'll try getting rid of Pulse Audio. That is sound and sound seems to be the only problem now..."

So, I did this...

```
sudo apt-get remove pulseaudio
sudo apt-get install esound
```

and this...

```
sudo cp /etc/X11/Xsession.d/70pulseaudio /etc/X11/Xsession.d/70pulseaudio.back
sudo rm /etc/X11/Xsession.d/70pulseaudio
```

Now I just watched a full 1.5hr long movie on hulu.com and even paused it and watched in full screen (but I kept it small for most of it to watch the CPU in conky.

It did get jumpy a vary little bit form time to time but no big deal. Other then that, it is working fine now.

So, If I have the problem pop up again I'll post here.

---

### Post by lovinglinux on 2009-06-06
You shouldn't remove pulsaudio, because it also removes ubuntu-desktop which, according to Synaptic description:

> 
It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.

Installing esound also removes ubuntu-desktop.

---

### Post by lovinglinux on 2009-06-06
Just an update about ubuntu-desktop. There is a good explanation of what it does at [http://ubuntuforums.org/showthread.php?t=378140](http://ubuntuforums.org/showthread.php?t=378140)

It seems that it only affects upgrades and you can install it again just before upgrading.

I think I'm gonna try removing pulseaudio too :)

---

### Post by HunterThomson on 2009-06-06
Ya your right it did remove ubuntu-desktop. Well I'll just install it again just before upgrading. While I was looking around there is a pulsaudio gstreamer plug-in installed for firefox. Maybe all you realy need to do is get rid of that....

**_Ranting starts now... Read at your own risk!_**

You seee this is why I think Ubuntu is a pile of ****. It works fine "If it works fine" and if it dosn't your ****ed. Ubuntu is so dependent apon itself. Case and point, You ever try removing GDM? If you do alsamixer in the terminal will not work "WTF!!!" What the hell dose GDM have to do with alsamxier ???? It dosn't end there... If you install OpenBox all hell brakes loose. I got OpenBox working but I dare not mess with it to much. So, much stuff is like that in Ubuntu. It is so setup to only work with what "They" think you should use. If you try and change anything a whole bunch of **** that has nothing to do with what your changing gets all messed up.


A lot of the things I hate about Windows is the same problem in Ubuntu. Extreme bloat, Monolithic (Linux is not at all Monolithic but Ubuntu is), Everything is hiden from you, (Ubuntu now ****ing hides the stdout from you WTF!!) it is GUI based so it's a pain in the *** to tell anyone how to do the stupidest little things. ON and on & on....


I only use it because I messed up and thought ATI had good Linux support. I was way wrong it has the most POS driver there is and ATI will never change that.

Arch Linux is the perfect mix of stability, up-to-date, customisability and good package manager.

Arch Linux dose what you tell it to do... Nothing more, Nothing less. Just like Linux should be.

---

### Post by HunterThomson on 2009-06-06
Owe, OK I just read that link... Thank you for giving it to me.

It seems it dosn't matter at all. It is only a problem upgrading to whole new vertion of ubuntu like when 9.10 comes out. I do a clean install anyway.

Also, it only blocks new installs of the packages in that bloat ubuntu-desktop package anyway. And I hate all the packages that are part of that bloat ubuntu-desktop anyway...

So, it is really no problem.

---

### Post by lovinglinux on 2009-06-06
> **HunterThomson said:**
> Owe, OK I just read that link... Thank you for giving it to me.

It seems it dosn't matter at all. It is only a problem upgrading to whole new vertion of ubuntu like when 9.10 comes out. I do a clean install anyway.

Also, it only blocks new installs of the packages in that bloat ubuntu-desktop package anyway. And I hate all the packages that are part of that bloat ubuntu-desktop anyway...

So, it is really no problem.

I also removed pulsaudio and installed esound. It's much better now. I can even watch videos on crappy web flash players and YouTube HD on fullscreen.

Thanks for the tip.

BTW, I also do fresh installs ;)

---

### Post by HunterThomson on 2009-06-06
Hum the problem returned....

I now removed everything pulseaudio I'll let you know....

---

### Post by lovinglinux on 2009-06-06
> **HunterThomson said:**
> Hum the problem returned....

No, no, no. Don't tell me that :)

I can even watch Youtube HD now while running rkhunter, which is CPU hungry. I will try to transcode a video and watch YouTube at the same time.

---

### Post by HunterThomson on 2009-06-06
nope no good... messed up agin. Everything stops and firefox crashes... :(

I hate Ubuntu.... This crap never ever happens in Archlinux

This is all do to some bloat package of crap programs that I never use. Or some broken driver that Ubuntu installs and Ubuntu will never let you get rid of...

To be fair... The problem with Archlinux is there is no real support at all form the community. And it is far to dependent on the AUR. So with Archlinux, once you get it working it stays working forever. But, the trick is getting it working in the first place i.e. my ATI problems....

---

### Post by lovinglinux on 2009-06-06
> **HunterThomson said:**
> nope no good... messed up agin. Everything stops and firefox crashes... :(

Everything is fine here. 

Try changing the sound settings. Put everything on "Autodetec", except "Sound Playback". Set ALSA for this one. This is my configuration. Also open gstreamer-properties and set ALSA for both.

---

### Post by HunterThomson on 2009-06-06
Just to be clear.

I never install pulseaudio in Archlinux. It is a outdated audio server. ALSA is way way way better. Ubuntu just install any crap the devs can find weather they work or not.

---

### Post by HunterThomson on 2009-06-06
Hum, ya I guess the first movie was just a fluke. I needed to set the output to ALSA instead of leaving it as autodect.


So far so good. Thanks :)

++++++++++++++++++++++++++++++++++

Nope still no good.... as soon as I typed that in it crashed....

---

### Post by HunterThomson on 2009-06-07
YES ! 

I got my ATI card to work with Archlinux :guitar:

I really really really doubt I will have any problem with flash in Arhclinux.

So, so long Ubuntu ):P

I'll post here if I do but all is well so far.

---

