---
title: "Problem with FireFox and RealPlayer Videos"
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by abyssius on 2008-01-26
When I first tried to view a RealPlay encoded video using FireFox, it prompted me to install a plugin. Assuming that it would direct me to the RealPlayer plugin, I clicked on the icon. Instead FireFox installed the Xine plugin, which simply doesn;t work. I subsequently downloaded the RealPlayer for Linux .bin file and installed it. After this, I was able to watch the video fine. However, after turning my computer off and then on again, FireFox went back to the Xine plugin. I assumed, I'd be able to direct FireFox to use the RealPlayer plugin as default. Strangely, FireFox, doesn't include .rm in its FileTypes list, so I couldn't change it there. I tried about:plugins - and RealPlayer isn't even listed (although I installed it, and it did work with FireFox, until I rebooted). 

I thought I'd try to get Xine to work. I found this on the MPlayer website:

[INDENT][COLOR="Blue"] The situation with real files and streams is pretty similar to the situation with Quicktime Streams (see above). The newer real audio and video formats are only supported by using binary-only codecs which are not included in xine.

Possibly the most convenient way to get the Real codecs is to download them from the MPlayer website [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html) . The package is called "essential". Unpack it and move everything you find inside to /usr/lib/codecs and set the decoder.external.real_codecs_path in your xine config file to /usr/lib/codecs (actually you can place them anywhere you want, e.g. someplace in your home directory, but then you'll have to set decoder.external.real_codecs_path accordingly). Restart xine then and you should be able to watch Real files/streams. [/COLOR][/INDENT]

My problem is I don't know how to comply with their recommendation. I downloaded the codec files. However:

(a) There is no /usr/bin/codecs directory that I can find. Do I create this directory? Or, maybe this isn't mandatory, since, according to them, I can put the codecs anywhere. 

(b) They don't specify how to find the xine config file (e.g. what is the file name? and where is it located?)

Alternatively, how can I simply instruct FireFox to use the RealPlayer plugin instead of Xine? Do I have to reinstall RealPlayer plugin again?

I'm not sure which is the best way to proceed?

---

### Post by Gannin on 2008-01-26
Yes, go ahead and create the directory.  But keep in mind, it's /usr/lib/codecs, not /usr/bin/codecs as you wrote.  Also, your Xine configuration file is in ~/.xine/config.

---

### Post by abyssius on 2008-01-26
Thanks Gannin.

Please bear with the newbie ex-windows user - just two days into Linux and Ubuntu. I wasn't able to create a directory under* /usr/lib* because of write permissions. I did create the directory "codecs" under my* /home* directory. I extracted the codec files to that directory. However, I did not find */.xine/config*. I only found */.xine* which contained a file named *catalog.cache*. Is this the config file I'm supposed to modify? If so, how do I find where to modify the path to the new codecs?

---

### Post by benerivo on 2008-01-26
I think you're unlucky that firefox is not using your installed realplayer. First, are you sure the streams you are trying to play using the realplayer plugin are .rm links? They may appear in the firefox filetype list as .ram or .rv. Assuming they don't, you could look at the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories that include the realplayer codecs. If you follow the instructions and then install the 'w32codecs' package. If you know you already have the codecs, then it would be best to put them in /usr/lib/codecs as suggested. To do this, open a terminal and type ```
gksudo nautilus
```and you will have no permissions problems.

---

### Post by abyssius on 2008-01-26
The real player files I'm trying to play are indeed .rm files, that are called by rpm files. I know this because I posted them myself a few years ago. I'm trying hard to comprehend the Linux file structure, having been extremely indoctrinated in the DOS/Windows file structure.

Even if I deposit the codec files in the /usr/lib/codecs directory, I can't find the xine config file that is supposed to declare the path to these files. The one file I found (catalog.cache) doesn't seem to use syntax like: *decoder.external.real_codecs_path in your xine config file to /usr/lib/codecs * as the instructions require.

Maybe, I should try to re-install the realplayer plugin?

---

### Post by benerivo on 2008-01-26
If you reinstall the realplayer plugin, i would use a .deb installer rather than the .bin file you can download from the Real website. Get it [here]("http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.1_i386.deb"). The config file is probably the one located at```
/home/YOURUSERNAME/.xine/config
``` The .xine part of the address is a hidden folder, so you will have to make sure that hidden folders are made visible in nautilus or whatever file manager you are using.

---

### Post by benerivo on 2008-01-26
abyssius, i see that you have actually found the correct folder but do not have a config file. I do have a config file, but i don't know what program created it. Sorry.

---

### Post by abyssius on 2008-01-26
I really appreciate the help I'm getting here. I don't really want to use Real Player because of its proprietary nature. I would love to view these files using open source software, just to see the differences (if any). When these videos were originally posted, Real Player was the only game in town (other than Windows media). 

I did find the folder /home/YOURUSERNAME/.xine. But, I didn't see /config. I don't think it's there. I'm sure I have [show hidden files] enabled. I will use the ,deb file to re-install RealPlayer. However, I'll feel defeated when I do this. I'm so determined to figure this out.

---

### Post by benerivo on 2008-01-26
Here is a config file from the internet. You could copy it and put it in your own folder. It is just named 'config' with no filetype extension.

---

### Post by abyssius on 2008-01-26
Thanks Benerivo

I looked through the config file you posted, and I don't see anything remotely like the line specified in the instructions I found at the MPlayer site.

I'll place the config file in the .xine directory and try guessing at the syntax:

decoder.external.real_codecs_path: /usr/lib/codecs

Maybe????

I'll let you know how it works

---

### Post by abyssius on 2008-01-26
I placed the file *config* in the *.xine* directory with the line specified in my previous post. All the downloaded files are in the */usr/lib/codecs* directory.. Unfortunately, nothing happened. I still get the XINE logo, the buffering message, which reaches 100% - claims success, but plays nothing. 

I don't want to try uninstalling Xine - since it seems to be intimately tied to all my multimedia resources. I'm wondering if there is any way to work on this from the FireFox standpoint. Why does FireFox insist on calling the Xine plugin? Is there a config file for FireFox that I might direct to the RealPlayer plugin instead. This is so different from FireFox behavior in Windows, where this would be completely simple to fix.

---

### Post by benerivo on 2008-01-27
> **abyssius said:**
> Thanks Benerivo

I looked through the config file you posted, and I don't see anything remotely like the line specified in the instructions I found at the MPlayer site.

I'll place the config file in the .xine directory and try guessing at the syntax:

decoder.external.real_codecs_path: /usr/lib/codecs

Maybe????

I'll let you know how it works

Try removing the space between path: and /usr.

Firefox uses xine because of the mplayer Firefox plugin that you have installed (i'd guess), unless you manually set it to use mplayer when first trying to view a real video file. When you installed realplayer it would have created a plugin file (look in /usr/lib/mozilla or /usr/lib/firefox), but i don't know how to set firefox so that it will use the realplayer one, rather than the mplayer one.

---

### Post by abyssius on 2008-01-27
benerivo thanks for your patience and attention. I was able to get firefox to recognize the realplayer plugin in the following manner:

In */usr/lib/mozilla/plugins* I saw: *xineplugin.so* - which I assumed was the xine plugin. I also saw *nphelix.so* which I assumed was the real player plugin. When I accessed  */usr/lib/mozilla-firefox/plugins* I saw *gxineplugin.so* and *xineplugin.so *plugins. But no other plugins. I copied these two files* /usr/lib/mozilla/plugins:- * *nphelix.so*, *nphelix.xpt* and pasted them into the */usr/lib/mozilla-firefox/plugins* directory. I restarted firefox, and now I can watch my videos using the realplayer plugin.

I still wish I could have gotten the xine plugin to work, though. Their instructions in my earlier post simply didn't do anything.

---

