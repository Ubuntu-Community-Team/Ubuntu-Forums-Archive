---
title: "Flash"
date: 2007-08-09
forum: Multimedia &amp; Video
---

### Post by EatSomeZebraCakes on 2007-08-09
I have no idea at all how to use linux.
I have to navigate with the terminal to run the install for the flash player.
Could some one give me that command line?
I need flash on mozilla badly

Thanks
:)

---

### Post by Gremlinzzz on 2007-08-09
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
click the link and get Option 1: .tar.gz save to desktop
now paste these commands in the terminal one line at a time and hit enter
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/

---

### Post by EatSomeZebraCakes on 2007-08-09
Great I entered them all in.
It seemed to work but it still wont let me view things on youtube =/

---

### Post by aysiu on 2007-08-09
> **EatSomeZebraCakes said:**
> I have to navigate with the terminal to run the install for the flash player. No you don't.

There are a couple of point-and-click methods for installing Flash.

Read more here:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by Gremlinzzz on 2007-08-09
> **EatSomeZebraCakes said:**
> Great I entered them all in.
It seemed to work but it still wont let me view things on youtube =/

what's your computers processor is it 64amd?

---

### Post by EatSomeZebraCakes on 2007-08-09
It's core 2 duo

---

### Post by Gremlinzzz on 2007-08-09
> **Gremlinzzz said:**
> what's your computers processor is it 64amd?

did you restart your browser before going to utube?

---

### Post by EatSomeZebraCakes on 2007-08-09
I restarted my browser but its doing the same thing.

I tried the point and click but it said it was an unknown plugin.

I'm going to restart my computer and see if it works.

---

### Post by Gremlinzzz on 2007-08-09
If your computers processor is 64bit you should check here and post here
[http://ubuntuforums.org/forumdisplay.php?f=134](http://ubuntuforums.org/forumdisplay.php?f=134)

---

