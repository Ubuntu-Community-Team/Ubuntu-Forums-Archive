---
title: "Another octoshape flash plugin ?"
date: 2010-01-21
forum: Multimedia Software
---

### Post by lekzz on 2010-01-21
I'm trying to play ESL TV ([http://tv.esl.eu/de/esltv_stream/stream/55-flv-free](http://tv.esl.eu/de/esltv_stream/stream/55-flv-free)) on Karmic using Firefox. It used to work but some time ago it stopped working, returning the error: An error occurred: notsupported, pluginbasic, install.

However octoshape is still working fine, i can watch the octoshape showcase and other octoshape streams just fine.

In windows the stream also doesn't play with the old plugin installed (Octoshape Streaming Services). But it installs another plugin: Octoshape add-in for Adobe Flash Player. In fact even after removing the streaming services plugin the stream still works. So it seems there is another octoshape plugin.

Does anyone know more about this and how to get this working in ubuntu?
I tried searching but all i could find was a few posts with the error, but no responses. Also can't find anything about it on the octoshape page, they just say they support linux and link to the usual installer.


Also i know i can just play the free stream using -url, but i recently bought the premium stream and when trying to use that with -url it can't authenticate and returns: You do not have permission to view this stream.

---

### Post by josemanden on 2010-02-10
I had the same problem, I sortta solved it (at least allowing me to play the ESL stream) by using the following command inside the octoshape library.

Download octoshape plugin here: 
[http://www.octoshape.com/index.php?page=get_octo/get_octo](http://www.octoshape.com/index.php?page=get_octo/get_octo)

Once installed (chmod +x the file and run it), go to installed directory and type:
./OctoshapeClient -url:ESL.oph350

This will play the stream in mplayer (which should be installed out of the box on most distros)

(The following is relevant only if the link seems not to work)

I do not know if this link always works, I randomly tried it after finding this link:
[http://www.reddit.com/r/gaming/comments/athsq/european_quake_live_finals_live_from_germany/](http://www.reddit.com/r/gaming/comments/athsq/european_quake_live_finals_live_from_germany/)
Regardless, it seems that ESL supports this so it's not impossible to use their stream at least.

Regards

---

