---
title: "Audio conflicts with Firefox"
date: 2006-08-26
forum: Multimedia &amp; Video
---

### Post by aldegaz on 2006-08-26
My audio setup is ok, when I open an audio file it plays fine, but If I open Firefox no audio files will play if I had previously opened an audio file.

Then again, If I play an audio file on the web in Firefox I wont get any sound when I play and audio file.

Is this something well-known? I couldnt find something similar when I was looking for a solution.

I am familiar with the terminal and have been using Dapper in 2 computers without windows for several months now.

Thanks

---

### Post by PCalitrack on 2006-08-26
Bump.

I don't have any help to provide. However, I do have the same problem, so this must be some sort of common thing.

---

### Post by aldegaz on 2006-08-27
It is weird that I cant still find a way to fix this, maybe another type of plugin?

bump

---

### Post by mdurham on 2006-08-27
I have the same problem on Dapper, so I log out and log back in and the sound in Firefox (real-player) & VmPlayer works.
In my opinion, sound in Ubuntu is a mess, there are other problems too. Maybe it's a general Linux thing? I don't know about other distros.
Cheers

---

### Post by rjfioravanti on 2007-07-26
I am having this exact problem now

If I start firefox first, amarok wont open, rhythmbox opens but wont play songs

If i start amarok first, then firefox wont play sounds on websites that should make sound


I am using amd64 7.04

---

### Post by Gremlinzzz on 2007-07-26
Note: if sound doesn't work in Flash Player (for example on YouTube):

sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

Change:

FIREFOX_DSP=""

To:

FIREFOX_DSP="aoss"

    * Restart Mozilla Firefox. Now sound should work in Flash Player. 
from the guide
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)
This doesn't work for amd64, since there's no 64-bit firefox plugin. A 32-bit firefox is necessary. Ubuntuforums provides special scripts for configuring some 32-bit applications in amd64.

---

### Post by rjfioravanti on 2007-07-26
Thanks for your help... however it has nothing to do with flash I just accept that i can't use flash on this 64bit computer. I refuse to use the 32bit app hack, I am waiting for real support (doesn't adobe just have to compile it!!)

Its just sound in general, like my gmail makes noise when people message me, so if firefox is open first I hear gmail messages, but not music in external app. If I open external app first, then i dont hear gmail messages

---

### Post by Gremlinzzz on 2007-07-26
> **rjfioravanti said:**
> Thanks for your help... however it has nothing to do with flash I just accept that i can't use flash on this 64bit computer. I refuse to use the 32bit app hack, I am waiting for real support (doesn't adobe just have to compile it!!)

Its just sound in general, like my gmail makes noise when people message me, so if firefox is open first I hear gmail messages, but not music in external app. If I open external app first, then i dont hear gmail messages

[http://kb.adobe.com/selfservice/viewContent.do?externalId=6b3af6c9&sliceId=1](http://kb.adobe.com/selfservice/viewContent.do?externalId=6b3af6c9&sliceId=1)

---

