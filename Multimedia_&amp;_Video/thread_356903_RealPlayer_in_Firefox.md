---
title: "RealPlayer in Firefox"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by Red Knuckles on 2007-02-08
When trying, for example, to play 'Hourly Newscast' at 'http://www.npr.org/' RealPlayer opens then gives the error 'Cannot open the audio device. Another application may be using it.' What can I do to correct this???:confused:

After installing 'mozilla-mplayer' Firefox then tries to play the same streaming audio [NPR Hourly News] with MPlayer instead of RealPlayer but the sound is choppy and unintelligeable. What to do next?
:(

Firefox does play embedded video with audio for what that means in regards to problem playing streaming audio.

---

### Post by ingo on 2007-02-10
I had the same problem using Suse (some time ago...). I had to close Amarok and any other audio programmes before RealPlayer would get access to the device. Try that...

---

### Post by peterx2 on 2007-02-13
symlinks used to promote totem have made the job difficult to run realplaye when using Firefox..
An easy solution has been to mount Opera.. everything works easily. all you have to know is the command line to fetch realplay.

---

### Post by Red Knuckles on 2007-02-18
I got video and sound from [http://www.rte.ie/](http://www.rte.ie/) and [http://www.bbc.com](http://www.bbc.com) now. The mplayer plugin is playing video with sound. For the radio pages I uninstalled RealPlayer and installed gxine, gxine-plugin, kaffeine-plugin. For these 2 websites gxine works for me. For [http://www.npr.org](http://www.npr.org) kaffeine works.:guitar: :lolflag:

---

### Post by Red Knuckles on 2007-02-18
I've just figured out how to get sound from RealPlayer in Firefox and Swiftfox:

sudo aptitude install alsa-oss
sudo kwrite /usr/lib/realplay-10.0.8/realplay 

edit this line [It's line 73]

$REALPLAYBIN "$@"

to read:

aoss $REALPLAYBIN "$@"

reboot and you should have sound in RealPlayer on the mentioned web sites.
:guitar: :lolflag:

---

