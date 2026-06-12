---
title: "Using vlc plugin for mozilla"
date: 2008-02-21
forum: Multimedia &amp; Video
---

### Post by Ramptu on 2008-02-21
How can I make mozilla use the vlc plugin for viewing divx movies on joox? I d/l the plug-in using synaptic. I went to mozilla prefrences >file types and vlc is not an option in "use this plug-in" only mplayer is. Totem is annoying because you click on volume and it doenst go away until you click it again same with right clicking on the video its playing. 

I also got the media player add-on for mozilla. Didn't change my defaults to vlc. Why isn't it listed in the list of add-ons? I only found it through a thread here. I don't remeber managing plug-ins this difficult in windows. Can anyone suggest anything?

---

### Post by ubuntu-freak on 2008-02-21
If you want to use the VLC plugin you have to remove totem-mozilla, mozilla-mplayer, xine-plugin etc and then delete the pluginreg.dat file;
 
**rm $HOME/.mozilla/firefox/pluginreg.dat**
 
You have to delete it everytime you change plugins.
 
I recommend you try the MPlayer plugin if you want the best results though. Take a look at my [how-to](http://ubuntuforums.org/showthread.php?t=661833).
 
Nathan

---

