---
title: "Ubuntu 9.10 Firefox youtube problem"
date: 2009-12-21
forum: Multimedia Software
---

### Post by Bluemilk on 2009-12-21
Hi everyone,  There is a slight problem with playing flash videos in firefox. While the video itself can be played, I can't seem to pause, fast-forward or rewind the video.   Anyone else has similar problems?

---

### Post by joes7 on 2009-12-21
maybe it is due to your internet speed.

---

### Post by Puck7 on 2009-12-21
Which version of flash player did you install ? (:

---

### Post by Bluemilk on 2009-12-21
> **joes7 said:**
> maybe it is due to your internet speed.

 No it is not due to my internet speed.  This happens even when the video has fully loaded.

---

### Post by Grenage on 2009-12-21
> **Bluemilk said:**
> Hi everyone,  There is a slight problem with playing flash videos in firefox. While the video itself can be played, I can't seem to pause, fast-forward or rewind the video.   Anyone else has similar problems?

Let me guess, flash buttons just generally don't work in movies?

Your best bet is to manually replace your flash with the one from the Adobe site.

Go to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
Download the tar file (not the deb)
Extract it (should have libflashplayer.so)
Move it to /usr/lib/firefox/plugins (delete the existing one there)

---

### Post by Bluemilk on 2009-12-21
> **Puck7 said:**
> Which version of flash player did you install ? (:

 How do I find that out?

---

### Post by Puck7 on 2009-12-21
Grenage's post above can fix your problem probably, that way you will have the latest, although the flashplugin-free from the ubuntu official repository pulls the same one.

---

### Post by Bluemilk on 2009-12-21
> **Puck7 said:**
> Grenage's post above can fix your problem probably, that way you will have the latest, although the flashplugin-free from the ubuntu official repository pulls the same one.

 Just did that and restarted Firefox. Still the same problem. :(

---

### Post by Puck7 on 2009-12-21
Make sure you install it while firefox is not running.

---

### Post by perlluver on 2009-12-21
You may want to try the 64 bit plugin, [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html), go to that link, and download the 64 bit plugin on the bottom, and follow the instructions for the tar.gz above.

---

### Post by Bluemilk on 2009-12-21
> **perlluver said:**
> You may want to try the 64 bit plugin, [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html), go to that link, and download the 64 bit plugin on the bottom, and follow the instructions for the tar.gz above.

 Tried both plugins. No luck.  Edit:  Scratch that. It seems to work now. Will post back if I run into any more problems. Thanks!

---

### Post by devilscemo on 2009-12-29
hi I have the same problem as BlueMilk.. i tried to install the plugin in the directory grenage suggested (/usr/lib/firefox 3.5.6/plugins) but it didn't work... 
I installed also in the directory (/usr/lib64/firefox 3.5.6/plugins) but nothing happened... What should I do? I also have the firefox folder but I'm not sure i should put it in there... the folder is basically empty there is only 1 subfolder which says "plugins" and in there there is only "flashplugin-alternative.so"... :confused:

---

### Post by Norwal on 2009-12-29
I had the same problem. I tried the fixes mentioned above and nothing worked.  I decided the remove Flashplugin-installer completely with Synaptic. After removal I check with Firefox "Manage Content Plug-ins and noticed that "gnash" was still installed as the flash player.  I removed this with Synaptic and reinstalled Flashplugin-installer from the repository and the problem was fixed.  Adobe Flash Player in now there and Youtube works.

---

### Post by lovinglinux on 2009-12-29
Uninstall flash and follow the instructions [from here](http://ubuntuforums.org/showthread.php?t=1358591).

---

### Post by HappyFeet on 2009-12-29
> **devilscemo said:**
> hi I have the same problem as BlueMilk.. i tried to install the plugin in the directory grenage suggested (/usr/lib/firefox 3.5.6/plugins) but it didn't work... 
I installed also in the directory (/usr/lib64/firefox 3.5.6/plugins) but nothing happened... What should I do? I also have the firefox folder but I'm not sure i should put it in there... the folder is basically empty there is only 1 subfolder which says "plugins" and in there there is only "flashplugin-alternative.so"... :confused:

You need to put the libflashplayer.so file in /usr/lib64/**mozilla**/plugins

---

### Post by jibwell on 2009-12-29
[SIZE=4]Same problem can I use my mouse to install the Libflashplayer.so. into Firefox/plugin? I tried it will not let me. Help new. [/SIZE]

---

### Post by Moustaffa on 2009-12-29
> **jibwell said:**
> [SIZE=4]Same problem can I use my mouse to install the Libflashplayer.so. into Firefox/plugin? I tried it will not let me. Help new. [/SIZE]

Hello. I'm also a Ubuntu newbie, although I do have a litte bit of experience with the Terminal. It's not difficult to use it to move files actually, but before doing this make sure you uninstall all your flashplayers through System > Administration > Synaptic Package Manager > Search flash and mark every green flashplayer for complete removal (don't worry, it'll stay there).

1) Download the tar.gz package for the latest adobe flash player
2) Extract (using your mouse). For simplicity extract it to your Desktop (it should be libflashplayer.so)
3) Open a Terminal window and go delete the other libflashplayer.so plugin that's already in /firefox/plugins as follows:

cd /usr/lib/firefox/plugins [Hit Enter, you should notice your Terminal states you're in that directory now]

Then remove the file like this:
sudo rm libflashplayer.so

The sudo command gives you authority to delete this file; it will ask you for your password on Ubuntu. Enter it and hit enter.

Next go to your Desktop directory to find the libflashplayer.so file and to move it to /firefox/plugins:

cd ~/Desktop

You are now in the Desktop directory

sudo mv libflashplayer.so /usr/lib/firefox/plugins

That's it. Strangely enough it still doesn't work for my firefox, but for some reason my Chromium browser can play everything now.

If you want to check if the plugin is installed, open your webbrowser and enter the following in the address bar:
about : plugins (delete the spaces! type about : plugins connected, one word)

It should give you a list and on top of the list you should see Shockwave.  If you don't see it, it didn't install correctly. If you do see Shockwave, you can see below what version of flashplayer is installed. It should be something like this:

File name: libflashplayer.so
Shockwave Flash 10.0 r42

I hope this helps!

---

### Post by HappyFeet on 2009-12-29
> **Moustaffa said:**
> 
1) Download the tar.gz package for the latest adobe flash player
2) Extract (using your mouse). For simplicity extract it to your Desktop (it should be libflashplayer.so)
3) Open a Terminal window and go delete the other libflashplayer.so plugin that's already in /firefox/plugins as follows:

cd /usr/lib/firefox/plugins [Hit Enter, you should notice your Terminal states you're in that directory now]



That may work for chromium, but for firefox, libflashplayer.so needs to go to /usr/lib/mozilla/plugins

---

### Post by Moustaffa on 2009-12-29
Great! Now it also works in Firefox!

My bad, I saw firefox in de the lib directory and forgot about mozilla.

Strange thing however that I had to use the 64bit download (link posted in this thread earlier), but my laptop is over 2 years old, so I always thought I was running 32bit :s
Also not the first time, I encountered some errors a few times when installing software, saying: wrong architecture and something about i386.
Do you know how this is possible?

And perhaps how it is possible that Chrome and Chromium installed this plugin when I put the file in firefox/plugin? 

Thanks!

---

### Post by HappyFeet on 2009-12-29
> **Moustaffa said:**
> 
And perhaps how it is possible that Chrome and Chromium installed this plugin when I put the file in firefox/plugin? 

Thanks!

The developers decided that chromium should look to that directory for the flash plugin.

---

### Post by AmpersUK on 2010-02-25
> **perlluver said:**
> You may want to try the 64 bit plugin, [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html), go to that link, and download the 64 bit plugin on the bottom, and follow the instructions for the tar.gz above.

Surely, if you are using 64-bit and downloaded the plugin from the repository, it would send you the 64-bit version? If not why not?

I am having a another problem with YouTube videos. I can watch them OK on YouTube with my 9.10 but when I embed them into my blog I can't get them to operate.

Can someone look at [http://ampers.blogspot.com](http://ampers.blogspot.com) and see if they can operate the video please? But please post here immediately afterwards as I don't want every man and his dog logging on as it will play havoc with my Google Analytics which I like to keep accurate.

I need to know if it is just my system, or whether there is a temporary problem at Blogger.

Cheers,

Ampers

---

### Post by lovinglinux on 2010-02-25
> **AmpersUK said:**
> I am having a another problem with YouTube videos. I can watch them OK on YouTube with my 9.10 but when I embed them into my blog I can't get them to operate.

Can someone look at [http://ampers.blogspot.com](http://ampers.blogspot.com) and see if they can operate the video please? But please post here immediately afterwards as I don't want every man and his dog logging on as it will play havoc with my Google Analytics which I like to keep accurate.

I need to know if it is just my system, or whether there is a temporary problem at Blogger.

Works for me.

---

### Post by AmpersUK on 2010-02-25
> **lovinglinux said:**
> Works for me.

Oh dear, that makes life difficult!

*I have a Karmic installation on a 64-bit machine. I have an nVidia Geoforce 250 graphics card with a gig of on-board memory, 8GB of RAM.*

I can watch and listen to videos on YouTube easily **and with no problem**.

When I go into my blog they just won't work.

Others can go into my blog and watch and listen to the videos **which means I copied the embedded code correctly.**

If I can watch the videos on YouTube,** it means my Flash is working.**

See what I mean? [COLOR=Red]***Am I missing anything here? ***[/COLOR]

Any help will be appreciated, although if others can watch and listen, it is not the end of the world. I can't watch on other peoples websites either, but I can always click on the source and watch them on YouTube.

Ampers

---

### Post by VertexPusher on 2010-02-25
> **AmpersUK said:**
> Surely, if you are using 64-bit and downloaded the plugin from the repository, it would send you the 64-bit version?
No, it will send the 32-bit version along with nspluginwrapper.

> If not why not?
Because the 64-bit version has not been released yet.

---

### Post by AmpersUK on 2010-02-25
> **VertexPusher said:**
> Because the 64-bit version has not been released yet.

Ahhh!

---

### Post by dE_logics on 2010-02-25
This is most probably a general bug. Similar (not exact) problem is there with my Gentoo box.

Why not just download the video and watch?

---

### Post by AmpersUK on 2010-02-25
> **dE_logics said:**
> This is most probably a general bug. Similar (not exact) problem is there with my Gentoo box.

Why not just download the video and watch?

No need, If I go to YouTube's website, as I said earlier, I can watch there OK.

Ampers

---

### Post by lovinglinux on 2010-02-25
> **AmpersUK said:**
> Oh dear, that makes life difficult!

*I have a Karmic installation on a 64-bit machine. I have an nVidia Geoforce 250 graphics card with a gig of on-board memory, 8GB of RAM.*

I can watch and listen to videos on YouTube easily **and with no problem**.

When I go into my blog they just won't work.

Others can go into my blog and watch and listen to the videos **which means I copied the embedded code correctly.**

If I can watch the videos on YouTube,** it means my Flash is working.**

See what I mean? [COLOR=Red]***Am I missing anything here? ***[/COLOR]

Any help will be appreciated, although if others can watch and listen, it is not the end of the world. I can't watch on other peoples websites either, but I can always click on the source and watch them on YouTube.

Ampers

When you say you can't operate do you mean you can't interact with the video or it doesn't show at all?

You could try [this](http://ubuntuforums.org/showthread.php?t=1414595).

---

### Post by AmpersUK on 2010-02-25
> **lovinglinux said:**
> When you say you can't operate do you mean you can't interact with the video or it doesn't show at all?

You could try [this]("http://ubuntuforums.org/showthread.php?t=1414595").

When I press the start button on the video on my website, zilch, nothing happens at all, but on the YouTube website it plays immediately.

I looked at that but I was uncertain as I am not too technical and I have learned in my 70 years of life, a superb bit of advice. This is "When in doubt, don't!" :-)

Ampers
Politicians, like babies, should be changed often -
for the same reason...

---

### Post by lovinglinux on 2010-02-25
> **AmpersUK said:**
> When I press the start button on the video on my website, zilch, nothing happens at all, but on the YouTube website it plays immediately.

I looked at that but I was uncertain as I am not too technical and I have learned in my 70 years of life, a superb bit of advice. This is "When in doubt, don't!" :-)

Ampers
Politicians, like babies, should be changed often -
for the same reason...

Is just a script to remove conflicting plugins and install the correct version from Adobe, depending if you have 32bit or 64bit. I have tested it and it works just fine, as far as I can tell.

Usually when you can't interact with the video on a 64bit machine, then removing all traces of flash and installing the beta version solves the problem. Take a look at [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

---

### Post by AmpersUK on 2010-02-25
> **lovinglinux said:**
> Take a look at [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

Ah! This was within my level of competence :-)

[COLOR=Red]***Now all is working.***[/COLOR]

Thanks a lot for that link. It is really appreciated.

Ampers

---

### Post by AmpersUK on 2010-02-25
> **lovinglinux said:**
> Take a look at [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

Thanks for that. It was within my level of incompetence :-)

Followed the instructions, and then checked my blog, and I can watch and listen to the video there.

[COLOR=Red]***Thanks a lot for your excellent help.***[/COLOR]

Ampers.

---

### Post by lovinglinux on 2010-02-25
> **AmpersUK said:**
> Thanks for that. It was within my level of incompetence :-)

Followed the instructions, and then checked my blog, and I can watch and listen to the video there.

[COLOR=Red]***Thanks a lot for your excellent help.***[/COLOR]

Ampers.

You are welcome.

---

### Post by oingk on 2010-03-10
I read the link that is supposed to mention the solution to the "Youtube buttons don't work on Ubuntu 64bit" problem but I couldn't find what exactly is the solution.

The link with the solution is supposed to be this:
[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

Could someone point me to the solution for the problem ?

---

### Post by lovinglinux on 2010-03-10
> **oingk said:**
> I read the link that is supposed to mention the solution to the "Youtube buttons don't work on Ubuntu 64bit" problem but I couldn't find what exactly is the solution.

The link with the solution is supposed to be this:
[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

Could someone point me to the solution for the problem ?

Use the [automated installer created by carlee](http://ubuntuforums.org/showthread.php?t=1414595). This tool  will install the best flash version according to your CPU architecture and will also attempt to remove any left-overs from previous  installations, thus helping to avoid conflicts with manually installed plugins.

---

### Post by oingk on 2010-03-10
After reading what's on the first page of the thread you linked me to, would it be right then to install the thingy that is here: 
[http://www.mediafire.com/?mvkomveztyy](http://www.mediafire.com/?mvkomveztyy)

?

---

### Post by oingk on 2010-03-10
I can install that, but regarding the other things that this girl says, I hardly understand what I should do.

Actually, I always post in the beginner's forum area, so now I should give you notice that I am a beginner in Ubuntu

---

### Post by oingk on 2010-03-10
Downloaded the machinery from here :
[http://www.mediafire.com/?mvkomveztyy](http://www.mediafire.com/?mvkomveztyy)

double-clicked it, this small window opened, chose "Remove Flash", it said "Flash removed", then chose "Install 64bit Flash", and it said "Flash installed", but problem stil persists.

:(

I can't use the buttons of youtube videos.

---

### Post by lovinglinux on 2010-03-10
> **oingk said:**
> Downloaded the machinery from here :
[http://www.mediafire.com/?mvkomveztyy](http://www.mediafire.com/?mvkomveztyy)

double-clicked it, this small window opened, chose "Remove Flash", it said "Flash removed", then chose "Install 64bit Flash", and it said "Flash installed", but problem stil persists.

:(

I can't use the buttons of youtube videos.

Have you restarted Firefox?

---

### Post by oingk on 2010-03-10
yes, i have

---

### Post by oingk on 2010-03-10
maybe it doesn't work for my version of ubuntu?
Is there something else to try?

---

### Post by lovinglinux on 2010-03-10
> **oingk said:**
> yes, i have

Go to a YouTube video and test it. If it doesn't work, then clear the cache and reload the page. Sometimes this fixes the problem.

Do you have the same problem on any flash video site or just on YouTube?

---

### Post by oingk on 2010-03-10
nope, not working for youtube, I cleared all history/cookies and not working.

It does work for Vimeo videos

---

### Post by lovinglinux on 2010-03-10
> **oingk said:**
> nope, not working for youtube, I cleared all history/cookies and not working.

It does work for Vimeo videos

What version of firefox you are using?

---

### Post by oingk on 2010-03-10
firefox 3.5.8

Also, what I find strange that I just realised is that after clicking on "Remove flash" on the little program, and then I come to youtube, I can still watch a video. Shouldn;t that be impossible?

---

### Post by lovinglinux on 2010-03-10
> **oingk said:**
> firefox 3.5.8

Also, what I find strange that I just realised is that after clicking on "Remove flash" on the little program, and then I come to youtube, I can still watch a video. Shouldn;t that be impossible?

The plugin is loaded by Firefox when you start it, so it will still work until you restart Firefox.

Have you tried the 32Bit version of flash? I prefer to use the 64bit version and I have no problems with it, except for one time on YouTube, which was fixed be reloading the page. Nevertheless, I'm using Firefox 3.6.

Perhaps you could upgrade to 3.6 and see if it works. See [this](http://lovinglinux.megabyet.net/?page_id=220##3---Installation-from-PPA-repositories-3).

---

### Post by Nordite on 2010-03-10
Same problem here.  I have tried a bunch of different things including installing Chrome.  If I keep clicking about 15 time I can eventually get it to work.  Has there been any progress?

---

### Post by Nordite on 2010-03-10
This seems to be youTube specific because if I go to funnyOrDie.com I have no problems.
Nordite

---

### Post by Nordite on 2010-03-10
If you go to the link below and sign up for the HTML5 Beta it seems to cure the problem.  But there is no full screen option.  Is working for me so far.
Nordite

[http://www.youtube.com/html5](http://www.youtube.com/html5)

---

### Post by Nordite on 2010-03-21
I installed "Ubuntu restricted extras" package and it solved the problem of YouTube Play, Pause, and Full Screen not  working.
Nordite

---

