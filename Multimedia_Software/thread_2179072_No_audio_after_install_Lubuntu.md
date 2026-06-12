---
title: "No audio after install Lubuntu"
date: 2013-10-06
forum: Multimedia Software
---

### Post by cahaya2 on 2013-10-06
Hi, I need help in resolving the following issue.  As I only started using Linux only about 3 weeks ago, I am still trying to figure my way around.  Please bare with me.

I was using Ubuntu 12.04.3 LTS at first, on my old but faithful laptop.  The audio was fine and I was able to watch video and listen to sound from Youtube.  I then read that Lubuntu is the lighter version of Ubuntu and hence, I gave Lubuntu 13.04 a try.  While Lubuntu was very responsive and quick, I later found out it didn't have any audio at all.

So, now I switched back to Ubuntu 12.04.3 LTS.  I was able to get sound from the analog output (built-in audio) but nothing coming from digital output (S/PDIF) (Built-in audio).  I didn't mind then for I thought analog audio is fine.   However, when I try to watch Youtube, there was no sound.  I could not figure out what else I didn't do.  Before I switch back to Ubuntu, I installed pavucontrol, pulseaudio, pulseaudio-utils and libgtk-3-0 on Lubuntu, but that didn't help.

I am using the HP Pavilion DV5121tx.  I don't know what sound card it is using but checking at the HP web site, it is using the Conexant high definition audio driver (hope this infor would help).

---

### Post by Yellow Pasque on 2013-10-06
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by cahaya2 on 2013-10-06
Your ALSA information is located at [http://www.alsa-project.org/db/?f=486ac7576d51949eea66806bb3ba82304d7df9cf](http://www.alsa-project.org/db/?f=486ac7576d51949eea66806bb3ba82304d7df9cf)

EDIT: I clicked the link but the page was blank. ??
EDIT2: I tried to run the command again and this time I received this:
[COLOR=#ff0000][I]HTTP request sent, awaiting response... 504 Gateway Time-out
2013-10-07 09:42:51 ERROR 504: Gateway Time-out.
[/I][/COLOR][COLOR=#ff0000]
[/COLOR]

---

### Post by cahaya2 on 2013-10-06
re-installation fixed it.  Bad resolving techinique but it helped me this time.

---

### Post by Bob_Bean on 2013-10-07
Open a terminal. (The quickest way is the Ctrl-Alt-T shortcut.)
Enter &#8220;alsamixer&#8221; and press the Enter key.
You will now see a user interface. In this user interface, you can do the following:
1- Select your correct sound card using F6 and select F5 to see recording controls as well
2- Move around with left and right arrow keys.
3- Increase and decrease volume with up and down arrow keys.
4- Mute/Unmute with the &#8220;M&#8221; key. An &#8220;MM&#8221; means muted, and &#8220;OO&#8221; means unmuted.
5- Exit from alsamixer with the Esc key.
A caveat here: When you mute or unmute something, pulseaudio might pick it up and mute and unmute other controls, as well as PulseAudio&#8217;s main mute.
- See more at: [http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/#sthash.209ZRfPs.dpuf](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/#sthash.209ZRfPs.dpuf)

---

