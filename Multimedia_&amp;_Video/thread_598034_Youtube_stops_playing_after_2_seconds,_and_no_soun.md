---
title: "Youtube stops playing after 2 seconds, and no sound"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by Eman64 on 2007-10-31
I've been scrounging through the depths of the forums trying to find a problem just like mine, but it seems that no one has found this problem on their computers.

Whenever I try to watch a video on YouTube it plays for two seconds and then pauses. If you move the cursor a little, it plays for two more seconds. This is frustrating as it is, especially seeing as games and sites such as Homestar Runner still play fine, but to make matters worse, nothing flash related has sound. I've tried every site I can think of, but I can't make it work. I've even tried rebooting and then running firefox before anything else.

I have no idea how I am going to fix this, but I'll list some things that may cause problems so that you all don't have to ask some little questions.

I am running compiz-fuzion.
Shockwave Flash:
        File name: libflashplayer.so
        Shockwave Flash 9.0 r48
I have already tried editing my firefoxrc and replacing none with aoss

---

### Post by aspie on 2007-12-31
Sorry this is not much help.  But I too have this issue on a Fedora system.  I will keep you posted if I find the answer.

---

### Post by soviet911 on 2007-12-31
hmm i had same problem but after instaling flash player 9 and rebooting it all started to work, try to do a reboot. might fix it did for me.

---

### Post by aspie on 2008-01-01
Thanks for the suggestion.  Sadly for me it still don't work.  However, I have noticed that other user accounts on the same machine work fine.

---

### Post by soviet911 on 2008-01-01
if i remeber corectly i uninstaled Gnash plug in for fire fox and never installed it again. at least its not listed in the plugins.

---

### Post by aspie on 2008-01-01
Well, it's probably unrelated.  But I installed KDE on mine to see if I could get the K browser to work for me.  

Then I logged back into Gnome, and Firefox/Youtube is now working fine!

---

### Post by Orkun Sensebat on 2008-03-23
Could it have something to do with Totem? Since I formated and installed hardy the problem occurs sometimes for me too - this time, I really remember, I booted, watched an episode of family guy with totem, read spiegel.de news and then - tried out a video on spiegel.de - which showed the same behaviour as you described.

same for youtube.

just a wild guess - do not want to trace back right now - but as i said - I suspect gstreamer/totem to have something to do with that.

---

### Post by mikeize on 2008-03-29
Clear the cache, it worked for me (after chatting with mozilla help).  Edit>Preferences>Privacy>Settings (check cache box)>Okay>Clear Now.  In the future, you can just hit Ctrl+Shift+Del, as a shortcut to clear private data.  Hope this works for everyone else having this problem.

-mike

---

### Post by Goggalor on 2008-04-30
I recently upgraded to Hardy 64 from Gutsy and came across this problem myself. After hours of searching for a cure, and trying many different things, I found that my problem was solved simply by going into the System Monitor, under the Processes tab, and ending the process pulseaudio. After that all my youtube videos, my on-computer videos, and DVDs worked perfectly fine.

---

### Post by oooh on 2008-05-01
I had exactly the same problem:
Flash based players such as youtube, or last.fm and so would not start playback, or stop playback after 2 seconds everytime.

The problem started after I set Amarok to use the ALSA mixer. When I returned it to AUTODETECT, everything started to work good again !

Conclusion: it may be some related gstreamer-alsa thingy...

---

### Post by Moustacha on 2008-05-06
Well, it's either pulseaudio or the clearing of the cache that does the trick. I'm thinking it's pulse that's evil.

---

### Post by Xzavier on 2008-05-07
One thing i discovered is that if i use firefox and a vid or site audio and i have audacious running a track.. it locks up the vid or track on the site.

now if i kill both apps.. restart firefox.. it works.. but then if i start audacious it doesnt play at all..

again kill all apps play an mp3 first.. then start firefox and a youtube vid.. fail.. mp3 plays video does..

---

### Post by powerofslack on 2008-05-08
Have had the same problem driving me nuts, in 32 bit and 64 bit swiftweasel as well as 64 bit firefox, on hardy amd64 desktop using flashplugin-nonfree without gnash installed; never had this problem at all with identical setup under gutsy.  There was a zombie pulseaudio process listed in the system monitor and killing it fixed the problem immediately!  I've gotten a million other suggestions that are clearly well intentioned but specific to more generic problems and not the new pulseaudio / flashplugin-nonfree conflict that is specific to hardy.  If anyone knows the bug report thread I need to send this to let me know or fwd it along and thanks a million as always for the help.

---

### Post by r!ots on 2008-05-08
Have you tried this:

Reinstall pulseaudio and libflashplugin support (which wasn't even installed before on my machine): 
```
sudo apt-get install --reinstall pulseaudio libflashsupport

```
and then change everything to pulseaudio in "system->preferences->audio settings".

This advice was posted [here]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/196470/comments/11"), which seems to be the right bug report thread for you as well (link to the whole   [thread]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/196470")).

Hope this helps you.

---

### Post by Xzavier on 2008-05-08
> **r!ots said:**
> Have you tried this:

Reinstall pulseaudio and libflashplugin support (which wasn't even installed before on my machine): 
```
sudo apt-get install --reinstall pulseaudio libflashsupport

```
and then change everything to pulseaudio in "system->preferences->audio settings".

This advice was posted [here]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/196470/comments/11"), which seems to be the right bug report thread for you as well (link to the whole   [thread]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/196470")).

Hope this helps you.


I tried it..
```
xzavier@Dragon:~$ sudo apt-get install --reinstall pulseaudio libflashsupport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  eggdrop-data libboost-thread1.34.1 libboost-date-time1.34.1 gnash-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/296kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 139718 files and directories currently installed.)
Preparing to replace pulseaudio 0.9.10-1ubuntu1 (using .../pulseaudio_0.9.10-1ubuntu1_i386.deb) ...
Unpacking replacement pulseaudio ...
Preparing to replace libflashsupport 1.9-0ubuntu1 (using .../libflashsupport_1.9-0ubuntu1_i386.deb) ...
Unpacking replacement libflashsupport ...
Setting up pulseaudio (0.9.10-1ubuntu1) ...

Setting up libflashsupport (1.9-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
xzavier@Dragon:~$ 

```

No luck.. launch an MP3 with audacious then firefox with a youtube video (tried both firefox 3b5 and firefox 2.0.0.14)

i do see this in the system logs.. (user.log)

```
May  8 00:01:14 Dragon pulseaudio[27294]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
May  8 00:24:09 Dragon pulseaudio[27294]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
May  8 00:29:22 Dragon pulseaudio[27294]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
May  8 00:29:24 Dragon pulseaudio[27294]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
May  8 18:00:34 Dragon pulseaudio[27294]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
May  8 18:02:03 Dragon pulseaudio[27294]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
May  8 18:02:26 Dragon pulseaudio[27294]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
```

---

### Post by Xzavier on 2008-05-09
Well i did kill pulseaudio from the processes set all the audio settings to ALSA and now videos on youtube/javagames and mp3s now play harmoniously. So it appears to be a pulseaudio situation..  

my suggestions would be to take your questions/concerns to [[COLOR="Blue"]http://pulseaudio.org/[/COLOR]]("http://pulseaudio.org/")

---

### Post by dopeking on 2008-06-06
Hy folks

i found a solution to this problem. 
I use firefox 3 on ubuntu 8.04.

I simply deactivated and reactivated the flash-plugin in the EXTRA->ADD-ON's Menu. It worked perfectly for me. 

I guess the flash-plugin crashed somehow... 

greez dopeking :lolflag:

---

### Post by ElvisGump on 2008-06-18
It's not just happening in Ubuntu/Firefox.

It's happening to me when I boot back over into Windows and try FF 2.0014 or the new FF3 final. I restart any version of FF in either OS and YouTube videos might play normally a couple of times, or sometimes they won't play at all with the brief 1-2 second play, hang and buffering continues. If you move the slider the video will play for a second or two then hang again.

---

### Post by beenudel1986 on 2008-06-23
I am facing the same problem with ubuntu 8.04 wid firefox 3 beta installed , to rectify i tried to reinstall the firefox , then i tried with flash and i even tired to kill the process mentioned in the above thread but nothing worked for me :confused:

---

### Post by CH1C0 on 2008-06-23
its definitely something to do with firefox, and IE from my experience. i've seen this happen on a few computers and in windows 95, windows 2000, windows XP, vista, puppy linux, and ubuntu. i usually just reinstall flash.

---

### Post by floyin on 2008-06-23
Its not with flash, its pulseaudio. 2 seconds into youtube videos (other flash videos and things aswell) it stops. Opening up system monitor, and killing pulseaudio, and restarting Firefox(close and open again) allows flash to work correctly. 

Maybe we should uninstall pulesaudio? I don't know if it is really needed for stuff.

---

### Post by junglist313 on 2008-07-01
I think this is a Flash & Firefox issue. Several Windows users are experiencing similar problems. This was all I could find on the official Adobe site. 

[http://www.adobe.com/cfusion/webforums/forum/messageview.cfm?forumid=44&catid=184&threadid=1330412&enterthread=y](http://www.adobe.com/cfusion/webforums/forum/messageview.cfm?forumid=44&catid=184&threadid=1330412&enterthread=y)

I really can't believe this has been happening to people since January and there is still no word from Adobe even recognizing the bug. 

Anyway I got it the other day. not using pulse, still on ALSA. Although I did try pulse for a few hours, a day or so ago, so I guess that could have something to do with it. But I switched everything back to ALSA, I'm confused.:confused:

---

### Post by loganp82 on 2008-07-01
i had this problem as well. then i noticed both flash 10 and flash 9 were in my firefox under tools>addons>plugins and i disabled flash 9 and restarted and everything works now.

---

### Post by junglist313 on 2008-07-01
> **loganp82 said:**
> i had this problem as well. then i noticed both flash 10 and flash 9 were in my firefox under tools>addons>plugins and i disabled flash 9 and restarted and everything works now.

Just checked mine, only ver. 9 is installed.

---

