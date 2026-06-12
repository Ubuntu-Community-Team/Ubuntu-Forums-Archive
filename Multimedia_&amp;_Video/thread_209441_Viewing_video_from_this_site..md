---
title: "Viewing video from this site."
date: 2006-07-05
forum: Multimedia &amp; Video
---

### Post by Alligator on 2006-07-05
I'm not able to view video (with mplayer)from this woodworking site.
[http://thewoodworking](http://thewoodworking) channel.com

Why?
:confused:

---

### Post by Alligator on 2006-07-05
[QUOTE=Alligator]I'm not able to view video (with mplayer)from this woodworking site.
[http://thewoodworking](http://thewoodworking) channel.com

Why?
:confused:[/QUOTE]
.

---

### Post by yopnono on 2006-07-05
If you are talking about this site: [http://thewoodworkingchannel.com/](http://thewoodworkingchannel.com/)
It works fine using dapper. mplayer. Do you have the mplayer firefox plugin installed.

---

### Post by Bloch on 2006-07-05
Works fine for me too on Dapper, using the DSL middle choice

---

### Post by Alligator on 2006-07-06
Well, I did an update. reinstalled mplayer and firefox plugin.  Tried mplayer on a couple of other woodworking sites - works.  Went to "thewoodworkingchannel.com"  and selecting the DSL option, mplayer started loading and stopped. I use to get a execv error. What am I missing?:cool: 

I left myself wide open there.

---

### Post by yopnono on 2006-07-06
Try different settings. Rightclick in the video window, select configure.
There you have video and audio settings, try change them. I use Video: X11, Audio: Alsa.

---

### Post by klytu on 2006-07-06
In addition to what was mentioned before, here's something else you can try. Do a search for all directories with plugins:

```
sudo updatedb
locate plugins
```

Note which plugin directories are sub-folders of anything named mozilla, mozilla-"anything", or firefox. Make sure that exactly one of those plugin directories  contains all of your plugins for mplayer and make sure there are no duplicates. In my case, I found duplicate plugins in the following directories:

/usr/lib/firefox/plugins
/usr/lib/mozilla/plugins
/usr/lib/mozilla-snapshot/plugins
/usr/lib/mozilla-firefox/plugins
/opt/firefox/plugins

You may not have all those directories on your system - I was surprised that I did! But the key for me was to make sure that all necessary plugins showed up exactly once and were all located in one place. I carefully examined all the directories and found duplicate mplayer plugins and links spread out among all of them. I consolidated all of them in the /opt/firefox/plugins directory leaving all the other plugins directories above empty. I restarted firefox and all firefox video playback problems had disappeared!

EDIT: Basically you want all the plugins to live in the plugin subdirectory of wherever your firefox executable resides. You can find this out by trying: "which firefox". For me, the result was "/usr/bin/firefox/firefox". I then did "ls -l /usr/bin/firefox/firefox" and discovered that was a link to /opt/firefox/firefox which is why I moved all plugins there.

I had once had embedded video playback working flawlessly, then one day a couple of months ago after doing some updates I began having problems. Mplayer would begin to load and then stop; realplayer would act up sometimes loading multiple instances of itself, sometimes not running at all; sometimes I could play an embedded video exactly once and then it would never play again. I tried many workarounds (the media player connectivity extension helped: [http://membres.lycos.fr/sethnakht/](http://membres.lycos.fr/sethnakht/)) and was able to get playback working in an artificial way but until last night I didn't find an answer for my situation. I apologize for the long post, but this situation was very frustrating and I am excited that everything works well for me now. I noticed MANY other people with similar symptoms where no one found an answer and I plan to check all the other threads I looked at over the last couple of months to see if anyone else has tried this. I think what was going on is that firefox was trying to load multiple instances of the mplayer plugin to play the same video at the same time and this would generate unusual errors. Hope this helps you!

---

### Post by Alligator on 2006-07-10
Well I setup to have the mplayer files only linked to /opt/firefox/plugins as per the "which firefox"  Same problem on this web site.  Also if I configure mplayer to have video = X11 and audio = ALSA , I don't have audio from another woodworking site @ woodcraft.com.  So these two are left blank.
Any more thoughts?  I appreciate your input.  Thanks

Ron](*,)

---

### Post by hayseeds77 on 2006-07-10
> **yopnono said:**
> If you are talking about this site: [http://thewoodworkingchannel.com/](http://thewoodworkingchannel.com/)
It works fine using dapper. mplayer. Do you have the mplayer firefox plugin installed.

Hi All and thanks for the brilliant information.  I'm a newbie - windows has run for the last time on my computers!!

However, after 2 weeks I'm missing Thewoodworkingchannel.com over broadband.  Everything else is working flawlessly.  However, when I click on the broadband option to stream the video at this website ... nothing happens.  I have downloaded and installed all manner of video viewers.  Should I reinstall Dapper a fresh and or can I easily hook up the mplayer firefox plugin as you suggest above??

Thanks in advance.

---

