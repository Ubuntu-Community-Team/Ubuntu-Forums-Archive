---
title: "Firefox closes when I click on video at WDIV news"
date: 2008-12-21
forum: Multimedia Software
---

### Post by sofasurfer on 2008-12-21
I go to [http://www.clickondetroit.com/video/18329481/index.html](http://www.clickondetroit.com/video/18329481/index.html) and click on a video and Firefox instantly closes.

I then tried the same thing with Konqueror. I see a message that says I need to install the latest version of Flash Player (Flash 10).

I click on the link to download it and save it to desktop. Then I extract it to desktop. Then it asks me to enter path to browser such as /usr/lib/mozilla. I enered /usr/lib/mozilla and I also tried /usr/lib/firefox. I am then told that it is not a legitimate path.

What am I doing wrong?

---

### Post by wolfen69 on 2008-12-21
remove any version of flash that you have. then
```
sudo apt-get clean
``` then ```
sudo apt-get autoremove
``` then go [here]("http://get.adobe.com/flashplayer/") and download the .deb flash file for ubuntu. put it in your home folder. then ```
sudo dpkg -i install_flash_player_10_linux.deb
``` restart firefox if open.

---

### Post by sofasurfer on 2008-12-21
The version you said to download is for Ubuntu 8.04. But I tried anyway. I got an error message stating that a later version is already installed.

Synaptic shows that 10.0.15.3 is installed.

---

### Post by mc4man on 2008-12-21
The version from that link (which I use to install on both 8.04 and 8.10) are both the same version, the linked ver. just has hardy in the name.
I have no problems with your site or any other.

Try following the above suggestion exactly, search flash in synaptic, do a complete removal, run the commands and then re install. (from the link or repo
Note the link does say 8.04[COLOR="Red"]+[/COLOR]

---

### Post by sofasurfer on 2008-12-21
I did a complete removal of 2 flash packages which show in synaptic. I then went to the link mentioned above and clicked on the .deb file. I opened it with GDebi package installer. I restarted firefox.

Firefox still closes when I click on the files I mentioned.

Maybe there is some confusion. I can watch some of the videos on the site... [http://www.clickondetroit.com/index.html](http://www.clickondetroit.com/index.html) ...but not others. Possibly the links are broken. 

Do this... go to [http://www.clickondetroit.com/index.html](http://www.clickondetroit.com/index.html). On the right side of the page there is a place called "video and live events". You see "fast cast", "Ron Gattlefinger" and "weather".
I can click on "Ron Gettlefinger" and a video comes up and plays. Below this video are links to other videos. If I click on any of these links, Firefox closes. I think this is a link problem. Is it just on my end or do these link close your browser also?

EDIT::
This does not happen on my winblows computer.

---

### Post by sofasurfer on 2008-12-28
I have another system with a fresh clean I
Ubuntu 8.10 installation and it does the same thing. As soon as I click on a link under "Fast Cast", Firefox closes.

---

