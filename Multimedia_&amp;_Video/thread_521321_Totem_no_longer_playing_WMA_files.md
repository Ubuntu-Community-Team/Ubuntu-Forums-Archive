---
title: "Totem no longer playing WMA files"
date: 2007-08-09
forum: Multimedia &amp; Video
---

### Post by cameran on 2007-08-09
hello,

yesterday i got totem to play wma files by installing the w32codecs from medibuntu and the gstreamer0.10-plugins-bad.  last night i read somewhere that i didn't need the w32codecs installed to play wma and only needed the gstreamer plugin so i uninstalled the w32codecs.  

now i can't play WMA files in totem, even after reinstalling the w32codecs.  does anyone know what to do?

thanks!

cameran

---

### Post by deadgobby on 2007-08-09
YOu may to reinstall the Bad, Good and Ugly again. You can test out VLC player, which rocks by the way. 
Gobby

---

### Post by cameran on 2007-08-09
i tried reinstalling them and it still doesn't work :(

i'd rather stick with totem if i can

any other suggestions?

thanks,

cameran

---

### Post by deadgobby on 2007-08-09
The reason why I ask if you have tried VLC player is to see if the wma file will play. If it does not play then not all the codecs did not install. Do you install the codecs using Automatix, Easy Ubuntu, or by one by one.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)
Gobby

---

### Post by cameran on 2007-08-09
i installed the codecs using the medibuntu repository through synaptic and it worked before i uninstalled the w32codecs and then when i reinstalled them it still didn't work.

i don't get how it could have gone from working to not working and then remained not working when i reinstalled the w32 codecs?

cameran

---

### Post by deadgobby on 2007-08-09
Yet, try VLC player and see if works. If not the codecs are not installed.

---

### Post by Chappy7777 on 2007-08-09
Hi,

I just looked for and found VLCPlayer in synaptic. In the documentation below the list of files when I had VLC highlighted, it said that it will work as a browser plugin if  mozilla-plugin-vlc is installed. 

My Noob question is: will it work from FFox if I just download this plugin and let synaptic install
 it?  Or do I need to download the whole list of files that appear when VLC player is typed into synaptic's search? My guess is that my 2nd "choice" is the correct one. 

If the answer is the second one, will synaptic do all the installing? Yes, methinks. Or do I need to do some typing in Terminal as well? 

I might as well ask all of my questions at once, right. Besides, it doesn't hurt to ask (and it moves this post back up the ladder) :)

---

### Post by Gremlinzzz on 2007-08-09
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
you could also try smplayer i use smplayer package (Qt3; without KDE support)
[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
i also use mplayer plugin for ff you have to uninstall totem plugin cause they bump heads:)

---

### Post by Gremlinzzz on 2007-08-09
> **Gremlinzzz said:**
> [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
you could also try smplayer i use smplayer package (Qt3; without KDE support)
[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
i also use mplayer plugin for ff you have to uninstall totem plugin cause they bump heads:)

oh yeah set your video to X11 and audio to alsa in all movieplayers and plugins

---

### Post by Gremlinzzz on 2007-08-09
if you want to watch divx movies with the mplayer plugin
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
:guitar:

---

### Post by cameran on 2007-08-09
ok i tried and still can't do anything.  i ran totem through command line and this was the output:

> ** Message: don't know how to handle audio/x-asf-unknown, codec_id=(int)355
** Message: Error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
gstplaybasebin.c(2182): prepare_output (): /play

** Message: Missing plugin: gstreamer.net|0.10|totem|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355 (audio/x-asf-unknown decoder)
no application found
** Message: No installation candidate for missing plugins found.
** Message: don't know how to handle audio/x-asf-unknown, codec_id=(int)355
** Message: Error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
gstplaybasebin.c(2182): prepare_output (): /play

** Message: Missing plugin: gstreamer.net|0.10|totem|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355 (ignoring)
** Message: All missing plugins are blacklisted, doing nothing


---

### Post by cameran on 2007-08-10
sorry to bump this but if anyone can help me figure this out i'll send you $10 via paypal, no joke!! 

 it seems like the only WMAs that don't play are my WMA lossless files now, even though they played just 2 days ago.

thanks for any help.

cameran

---

### Post by cameran on 2007-08-10
> **deadgobby said:**
> Yet, try VLC player and see if works. If not the codecs are not installed.

VLC player won't play the WMA lossless files that i have.  it plays, just that there is no sound.  totem gives the error message i pasted above.

i guess this means that the codecs aren't installed correctly, but they were apparently installed correctly until a day ago.  how can i reinstall them properly?  i've done everything i could - removing the codecs, purging them, reinstalling and still no luck.

cameran

---

### Post by Chappy7777 on 2007-08-10
> **Gremlinzzz said:**
> if you want to watch divx movies with the mplayer plugin
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
:guitar:
==================================
I can't tell who these replies are aimed at, myself or Cameron?

Please either quote the person you are helping or put in their name, ok?

Absolutely NO offense implied.  

Thanx, regardless;

---

### Post by Duranxl on 2008-07-17
i have this problem too.
Some wma files play though, but most don't.
I have W64codecs

edit: it seems it's wma lossless files

---

