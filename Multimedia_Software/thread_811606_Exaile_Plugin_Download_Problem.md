---
title: "Exaile Plugin Download Problem"
date: 2008-05-29
forum: Multimedia Software
---

### Post by monkeydragon707 on 2008-05-29
Hey guys, 
I've searched everywhere throughout this forum and elsewhere and couldn't find any other cases of my same problem. I'm using Hardy and in Exaile 0.2.13 (most recent I believe) I have a peculiar and annoying problem: Whenever I open the Plugin Manager and try to look at the Available Plugins, it simply says "Fetching available plugin list..." but never comes up with anything, even if i leave it open for like an hour. The other network functions work fine, e.g. I can look up lyrics and wikipedia info., except for album cover fetching, which might be related. Exaile has no album art at all on my files although other music programs can display them. I hope its not because of my proxy settings; I have to connect using a proxy server and I've configured everything (Exaile and Ubuntu) to work with it and I haven't had any problems until now. 
As a workaround for the plugin problem I tried searching for another way to download the python scripts and such, and only found a few plugins on the exaile website hidden in their archives. These were very helpful, but there were only like 10 or 15 of them, and I wanted to try the other ones. Any ideas for where I else I can download them externally?

Any help/comments would be appreciated. Thanks.

---

### Post by superzorro on 2008-05-29
I had the same proble and the only way I could fix it was:

Uninstalled the current Exaile and then added the repository that is stated on the Exaile download page: [www.exaile.org/downloads]("http://www.exaile.org/downloads")

```
deb http://ppa.launchpad.net/exaile-devel/ubuntu hardy main
```
then
```
sudo apt-get update<p>sudo apt-get install exaile
```


After that Exaile was running normally and I could install all the plugins

---

### Post by monkeydragon707 on 2008-05-30
Hey,thanks for the suggestion. I tried it, but after deleting and reinstalling Exaile, I'm still getting the same problem. Maybe in the next update/release it'll work. Any other suggestions?

---

### Post by monkeydragon707 on 2008-05-30
Whoa, that was strange. My problem got fixed, but I have no clue why. 
Previously I had been using launchers set to launch the command "exaile", but when I ran the exact same command from the terminal, all my problems disappeared. Even when I go back and try another launcher say from the panel or desktop, they always result in the same problem, but from the terminal it always goes smoothly. 
Why?

---

### Post by superzorro on 2008-06-03
Thats very strange, I don't know what could make that.

Have you tried deleting the .exaile folder on your home directory and starting again Exaile?

---

