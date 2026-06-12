---
title: "New problem with Rhapsody player engine - Firefox plugin"
date: 2007-03-26
forum: Multimedia &amp; Video
---

### Post by habtish on 2007-03-26
Hey all,

For the Rhapsody users on Linux, we all have been accessing this service through rhapsody.com and been using a Firefox plugin to play tracks. granted it is limited in many aspects as compared to its stand-alone counterpart in windows, i have never had any problems accessing my account and playing tracks.

About a month ago, rhapsody did an upgrade to their firefox plugin, which meant that I could no longer play tracks. I could sign in and out using the plug-in fine.. but every time I try to play a track, I keep getting an error message about not being signed in.

I spent over 45 min.s on the phone last week with Real customer support to get to "level 2" support, only to be told they couldn't help me at the time and haven't had any complaints from other Linux users.

Please let me know if you have been using rhapsody.com on Ubuntu and can still access your stuff without any issues.


My "Specs" are:
Ubuntu 6.10
Firefox 2.0.0.1 > downloaded through apt-get and upgraded in update manager.

Thanks

---

### Post by broon22 on 2007-05-18
This has already been posted somewhere else but.... Try this:

1. Close firefox completely
2. open a Root terminal (or sudo)
3. type killall esd 
4. To restart esd, if you need it for anything type ALT+F2 and type esd (should here some beeps)... Probably don't need it though
5. Now try your Rhapsody.... 


The only other problem I have is that pcm goes to 100% which distorts the sound. I can't figure out how to default the sound to something more reasonable for my system...

Hope this helps...

---

### Post by Mitush on 2007-10-14
I cannot make rhapsody plug-in to work with my Ubuntu 7.04 and Firefox 2.0.0.6. (I and trying the free streaming audio rhapsody). I created a (free) account with rhapsody.com. When I try to sign up, the plugin window comes up, than I sign up, than my account info appears in the firefox rhapsody (main) window, but the plugin window disappears at this moment. If I try to play a stream after that, the plugin window come back up, but it gets stuck on "Authenticating" step, and nothing happens (plugin window does not display my login name).

I tried deleting .mozilla/plugins/nprhapengine.so and .rhapsody and reinstalling, this did not help.

I tried to use yottamusic.com interface and this did not work either (after logging into rhapsody plugin window, it also dissapears and not comes back).

I also tried "killall esd" advice above and it did not work either.

Its very frustrating because I could not find anything about this problem in the net and many people have it working fine apparently.

Any insight would be great.

---

### Post by jshbbe on 2007-10-15
I'm also getting the same problems.  I installed the plugin, which made Firefox crash.  Then I tried to play a song, and it will play for a while then stop.  Then if I try to play a song again it will get stuck on authenticating.

---

### Post by Mitush on 2007-10-15
I actually signed up for "unlimited" access with rhapsody. Some things on Rhapsody work for me (individual songs, playlists), but some still do not (streaming radio) with the same "authenticating" error. It also looks like this plugin's gui code gets in the way of music playing, by that i mean that if the plugin window is being redrawn/changed/etc, playback gets briefly interrupted. And I have recent quad-core Dell XPS720, so its not that my computer is underpowered.

And it crashes firefox occasionally too.

---

### Post by jshbbe on 2007-10-15
I have an unlimited account too since I would always use it on Windows.  Now that I am using Ubuntu again, I want to listen to music on Rhapsody.  The songs will play for me, but then they will stop playing after about a minute, and if I try playing them again they will be stuck authenticating.

I found something at LinuxQuestions.org that I'm going to try when I get back to my computer.  I hope this works.  [http://www.linuxquestions.org/questions/linux-software-2/rhapsody-firefox-1.5-488056/]("http://www.linuxquestions.org/questions/linux-software-2/rhapsody-firefox-1.5-488056/")

---

### Post by balak on 2008-03-19
Did you guys get this working. Any insights will be useful for me.

For me, firefox is unable to even install the addon.. it says insufficient diskspace!! error code -235

---

### Post by devapea on 2008-03-20
Yeah same problem here.  It worked fine before the upgrade to Gutsy.  I ended up cancelling my Rhapsody account because of it not working.  I told the customer service dept located in India from the sound of it the reason why I quit.  It works so so on my roomates computer.  It sometimes just plays one song and thats it.  Good luck guys.

---

### Post by konlevin on 2008-03-26
Got the answer from here.

[http://www.linuxquestions.org/questions/linux-software-2/rhapsody-firefox-1.5-488056/](http://www.linuxquestions.org/questions/linux-software-2/rhapsody-firefox-1.5-488056/)

All I needed to do was download the useragent firefox plugin and configure it to trick Rhapsody into thinking I am running Firefox 1.0.1.

---

### Post by steve101101 on 2008-06-09
> **konlevin said:**
> Got the answer from here.

[http://www.linuxquestions.org/questions/linux-software-2/rhapsody-firefox-1.5-488056/](http://www.linuxquestions.org/questions/linux-software-2/rhapsody-firefox-1.5-488056/)

All I needed to do was download the useragent firefox plugin and configure it to trick Rhapsody into thinking I am running Firefox 1.0.1.

How did you do this. I followed the directions, but it didn't work. If anyone has a solution please send me a private message.

---

