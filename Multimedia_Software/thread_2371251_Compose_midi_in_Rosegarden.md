---
title: "Compose midi in Rosegarden"
date: 2017-09-12
forum: Multimedia Software
---

### Post by shantiq on 2017-09-12
This a basic howto to compose midi in Rosegarden
It is fairly simple if instructions are followed carefully
Only to get folks started




&#10122; ```
sudo apt install timidity awesfx fluid-soundfont-gm freepats
```

&#10123; run ```
timidity -iA
```

&#10124; if you want to run &#10123;  each time do or else

save into a text file
```

[Desktop Entry]
Type=Application
Exec=timidity -iA
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_GB]=timidity

```
to ~/.config/autostart/timidity.desktop

then you never have to think about this again

&#10125; Then go to Edit/Preferences/Midi and find your asfxload and your sf2 soundfont this way
[[IMG]https://s26.postimg.org/np4bs9n3p/asfxload.png[/IMG]]("http://postimg.org/image/np4bs9n3p/")

[[IMG]https://s26.postimg.org/6pvdd0bw5/soundfont.png[/IMG]]("http://postimg.org/image/6pvdd0bw5/")

&#10126; Then Read 2 earlier posts:

[https://ubuntuforums.org/showthread.php?t=1700943&p=10528034#post10528034](https://ubuntuforums.org/showthread.php?t=1700943&p=10528034#post10528034)
[https://ubuntuforums.org/showthread.php?t=1700943&p=10744915#post10744915](https://ubuntuforums.org/showthread.php?t=1700943&p=10744915#post10744915)

Make sure you pick the lowest port 0 and port 1 in the list to link to your playback devices ie the 2 at the bottom of the list if you use 2 playback devices or port 0 if you only use one   playback device
see pictures below or video below for clarifications
[https://ubuntuforums.org/attachment.php?attachmentid=185244&d=1299406056](https://ubuntuforums.org/attachment.php?attachmentid=185244&d=1299406056)
[https://ubuntuforums.org/attachment.php?attachmentid=190519&d=1304178466](https://ubuntuforums.org/attachment.php?attachmentid=190519&d=1304178466)



&#10127; Also view a handy video made in 2011 and still totally accurate in 2017
>> [https://www.youtube.com/watch?v=0-X6_q1iRzc](https://www.youtube.com/watch?v=0-X6_q1iRzc)

All this put together should make it that you can get started without too many hassles


PS &#10128; export your piece to a midi file then if you wish to make this into a wav [and later to any format you favour] use this:
```
timidity -A120 nameofyourfile.mid -Ow2 -o nameofyourfilename.wav
```

---

