---
title: "Mplayer in Edgy?"
date: 2006-11-01
forum: Multimedia &amp; Video
---

### Post by adds2one on 2006-11-01
I did a full install of Edgy on my laptop a couple days ago. I used 
Automatix2 to get all the codecs and plugins for Firefox as I have previously done with Dapper.

I notice now that when I view video online that the interface is different than mplayer on my Dapper machine. The controls are missing and there is no Mplayer logo as the video buffers. Also sometimes the video won't play till fully buffered and I get strange audio glitches as the video is buffering.

Could this be an issue with the new Firefox? If there is no Mplayer logo am I really using mplayer?

Anyone else using a fresh Edgy install and mplayer?

---

### Post by jpeddicord on 2006-11-01
You may be using the default Totem plugin for firefox. Check to see if totem-firefox is installed.

---

### Post by adds2one on 2006-11-02
totem-mozilla is installed, as is mplayer. 

Do i need to uninstall totem-mozilla for mplayer to work or is there something else I have to do to get mplayer to be the default player in my browser?

I didn't have to do this with Automatix on Dapper, so would appreciate any help. :)

---

### Post by lognok on 2006-11-04
Uninstalling totem-mozilla did the trick for me. Now I see a Mplayer logo whenever I open a file format it handles.

---

### Post by hamil on 2006-11-05
Well, you do not need to remove the totem-mozilla pack.

If you do type about:plugins in Firefox's adressline, you will be presented for all the plugins active in your webbrowser. If totem is showing up there, you should remember the filename of that plugin, and simply remove it from the /usr/lib/mozilla-firefox/plugins/ directory. That should do the trick also..

---

### Post by donfilipo on 2006-11-05
Well i am glad i found some help Hamil ...and of course a man who knows something about it....my story: i upgraded first from 6.06 to 6.10 and everything went fine, except for the watching streams from the web. You know news and even TV and of course the mistress of silicon valley Pamela Anderson. There was misery. After installing all possible codecs and plugins nothing worked. I noticed that totem and totem plugin can not be removed from 6.10 at least that says the synaptic. Well ok but then the totem should play streams fine and not just sit there with a white-browny window and do nothing. And after installing kaffeine...mplayer...vlc...gxine and donowhat nothign helped. Somehow this totem prevailed and now i can not watch streaming video. (Anything on my HDD will play well...i mean no codecs **** i think even txt file will show movies:) And of course i went to #ubuntu and asked...but nothing ...i reinstalled the 6.10 from scratch but the same **** happened....i just need to know how to convince the firefox wich plugin shoud it use (firefox 2). Please Help???!!!!](*,)

---

### Post by hamil on 2006-11-05
donfilipo:
I do not know how to get Totem to play the media streams correct in Firefox 2, but I do know how to get mPlayer to play them fine.. :)

First, you need to make sure that you do not use the totem plugins in Firefox. If you type the text ```
about:plugins
``` in Firefox's adressline, you will see what kinds of plugins that will play the different kinds of files. If totem is listed there, to play media files, write down the filename of those files, e.g libtotemxxx.so

To remove these, you need to be root. In a terminal, you remove these files like this:
cd /usr/lib/mozilla-firefox/plugins/
sudo rm the_filenames_that_contains_totem

If you now go back to Firefox, and type the about command, you will see that there no longer is any totem plugins there. 

If you now have the mPlayer plugin installed,  I am sure that it will work just fine now, and play all the streaming media you wants. If you do not have the mPlayer plugin installed, I do recommend that you install it.

If you in the future do an upgrade of totem and the totem-mozilla pack, you need to remove files from the plugin folder again.

---

### Post by donfilipo on 2006-11-06
Thank you hamil..you have been very nice trying to help...but i will wait and bother the dr.Frankensteins behind the bug and mess about watching silicon waleys;) See... if i type the code suggested i see a display in which mplayer should play most of important files just like it should do. Anyway all known files are covered so...i have a dream, one day someone of the development team of debian and ubuntu will figure it out what bug causes the pluggins to sit still and will put them in operating condition. According to totem info *.ram files should be handled by mplayer but that is not the case...Hopefully i will live to that update. Ubuntu is supposed to be user friendly so watching streams is a must for such kind of linux. I hope.

---

