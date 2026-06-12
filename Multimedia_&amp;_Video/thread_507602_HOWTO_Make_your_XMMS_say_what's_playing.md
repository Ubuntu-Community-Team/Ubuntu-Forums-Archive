---
title: "HOWTO: Make your XMMS say what's playing"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by Basicalyptic on 2007-07-23
This howto explains how to get your computer say the name of the song in XMMS.

First, install XMMS if you don't have one:

```
sudo apt-get install xmms
```

Ubuntu should have the Festival speech synthetisator built in, but if you don't have it, run:

```
sudo apt-get install festival
```

Then configure the XMMS Song Change plugin:

    Press CTRL + P to bring out the Preferences.
    Select the General Plugins tab.
    Select the Song change plugin.
    Press Enable Plugin.
    Then press Configure.
    Paste this in the first text box without the brackets: (echo "Now playing: %n ." | festival --tts)

After the configure, press OK.

Play some media files and change the song. If done correctly, you should hear: Now playing, "name of the song".

Enjoy!:popcorn: :razz:

---

### Post by benx009 on 2007-07-23
haha! nice HOWTO it actually works!!!!

but the voice of the guy who talks is kinda lame, it there anyway to change it?

---

### Post by Basicalyptic on 2007-07-23
I don't know. See if you can find it from [The Festival homepage.]("http://www.cstr.ed.ac.uk/projects/festival/") P.S: You can configure what the computer says by pressing CTRL + P in XMMS and in the General Plugins tab selecting the Song change and clicking the Configure button. Edit the string in the text box. It is in format: ```
echo "string that the computer says and parameter from the bottom of the page" | festival --tts
``` P.P.S: Glad you liked it! I invented it when playing around with the Festival.

---

