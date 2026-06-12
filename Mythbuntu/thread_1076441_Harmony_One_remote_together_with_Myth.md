---
title: "Harmony One remote together with Myth?"
date: 2009-02-21
forum: Mythbuntu
---

### Post by Freddan101 on 2009-02-21
Hello guys!

I've struggled long and hard to get the Imon device in my Silverstone LC16 to work with MythTV in Ubuntu. Apparently Silverstone changed the IR device just before I bought the case and lirc hasn't supported this device (15c2:0036) until recently.

So I'm been trying to teach my Pronto Neo all the tricks from the Imon pad remote to manage all parts of Myth but it's a slow and painful process as I have to learn the raw codes from scratch and the Imon is quiet special with that. Therefore I've started to look towards the Harmony One to let it replace the Pronto and get the codes from Logitech's download service (which I hope they have in their device database).

But as I'm searching the forums I've found that many seem to have problems with the combo Imon, Harmony and Myth so I'm afraid I would be back at square one. Though, I haven't found anyone using exactly the same case (or Imon device) together with the Harmony One so I'm hoping to find someone with feedback by posting this.

Any experiences welcome!

---

### Post by keimol on 2009-02-21
Hi,

I also have a SilverStone LC16B-M case, Mythbuntu and a Harmony One remote. Works fine. IIRC, I just selected Silverstone from the Harmony website and remapped some keys (the directions don't seem to work that well, so I remapped them to other keys). If you want my LIRC conf files, just let me know. I can also take a screenshot of the button mappings on the Harmony website.

---

### Post by Freddan101 on 2009-02-22
> **keimol said:**
> Hi,

I also have a SilverStone LC16B-M case, Mythbuntu and a Harmony One remote. Works fine. IIRC, I just selected Silverstone from the Harmony website and remapped some keys (the directions don't seem to work that well, so I remapped them to other keys). If you want my LIRC conf files, just let me know. I can also take a screenshot of the button mappings on the Harmony website.
Thank you for your feedback, Keimol! What kind of problems are you experiencing with the directional buttons? Will all keys be repeated ok in Myth when you're holding down a button on the Harmony? 

If you have the possibility to post (or PM) your lirc conf and screenshots of the button mapping from the Harmony website I would appreciate it a lot!

---

### Post by keimol on 2009-02-22
Actually button repeat is not working for me (pretty much haven't seen the need for it). My lirc config file is standard, using the distro provided /usr/share/lirc/remotes/imon/lircd.conf.imon-pad file. Here's the config files I have in ~/.lirc/ (included in ~/.lircrc):

[mythtv]("http://pastebin.com/f2f67ea6e")
[mplayer]("http://pastebin.com/f56dfdd29")

And here's a badly composed screenshot of my Watch TV activity buttons:

[Screenshot](http://i41.tinypic.com/256h2ip.png)

---

### Post by Freddan101 on 2009-02-22
> **keimol said:**
> Actually button repeat is not working for me (pretty much haven't seen the need for it). My lirc config file is standard, using the distro provided /usr/share/lirc/remotes/imon/lircd.conf.imon-pad file. Here's the config files I have in ~/.lirc/ (included in ~/.lircrc):

[mythtv]("http://pastebin.com/f2f67ea6e")
[mplayer]("http://pastebin.com/f56dfdd29")

And here's a badly composed screenshot of my Watch TV activity buttons:

[Screenshot](http://i41.tinypic.com/256h2ip.png)
Excellent, thank you!!

When you say that the directonal buttons don't work that well, in what way don't they work? How have you remapped them?

I could see use of the repeat function while for example browsing through a media library, i.e. lots of mp3 files etc.

---

### Post by keimol on 2009-02-23
Repeat would be nice, but Mythmusic sucks so much that I haven't really used it :)

If I remember correctly, Left/Right/Up/Down map to ShiftTab, Tab, etc on lirc and there are "DirectionUp", "DirectionLeft", etc separately which correspond to iMON Pad's "joystick".

---

### Post by Freddan101 on 2009-02-23
> **keimol said:**
> Repeat would be nice, but Mythmusic sucks so much that I haven't really used it :)

If I remember correctly, Left/Right/Up/Down map to ShiftTab, Tab, etc on lirc and there are "DirectionUp", "DirectionLeft", etc separately which correspond to iMON Pad's "joystick".
I hear you! :) But in XBMC for example, repeat could be nice to have.

---

