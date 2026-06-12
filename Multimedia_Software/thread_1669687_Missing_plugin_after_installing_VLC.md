---
title: "Missing plugin after installing VLC"
date: 2011-01-18
forum: Multimedia Software
---

### Post by Ramot on 2011-01-18
Good morning to all,

Two days ago I installed VLC on my Ubuntu 10.04 and now I can't listen to live radio stations on the web (using Chrome).
I tried a few of them and they all complain about a missing plugin.

Does anybody know which plugin is missing and how to fix it?

---

### Post by Ramot on 2011-01-25
Is there really no one who can answer this question?

---

### Post by poodoopealeoaph on 2011-01-25
For some reason with VLC in Ubuntu, you don't get as many plugins as you would normally get in other OS's. So, basically, you need to go to synaptic and install "ubuntu-restricted-extras". This may help your issue. If not, try to type in vlc in your synaptic manager and see if there are any libs that say anything about lib-vlc-streamer.

Another solution is to keep movie player in your system. After installing the restricted extras you should be able to stream most audio and video off the internet with movie player. If you try to watch or play anything off the internet after this and it doesn't work, just try to right click on the thing you want to listen to and see if it gives the option of just opening it in movie player or vlc. This way it will just skip the idea of going through chrome then to vlc or media player.

---

### Post by Ramot on 2011-01-25
Movie-player and the restricted extras including the different lib-vlc are already installed.

I don't get the option to stream with Movie-player or any other streamer when I right click on the small window that opens after clicking on the "listen now" button.

So... I'm still stuck with this problem. I might try removing vlc and see if I get it back to normal...

Thnx anyhow.

---

### Post by Yellow Pasque on 2011-01-25
Did you also install the mozilla plugin for VLC? If so, it may be interfering with whatever you had installed previously. Look at your list of plugins in Firefox or Chrome.

---

### Post by mc4man on 2011-01-25
To add to Temüjin's post - 
there are several browser plugins available, the 3 most commonly used are 
totem-mozilla : gecko-mediaplayer : mozilla-plugin-vlc

All have their plus's and minus's, you should try them all to see what suits your usage best. (I use totem-mozila, though sometimes temporarily switch to gecko-mediaplayer on some sites

You should only have 1 installed at a time for best performance

---

### Post by Ramot on 2011-01-29
Thanks guys for your ideas, but, unfortunately this very much needed plugin is still MIA...
I actually removed vlc but it didn't do much good.
Now I even consider reinstalling Chrome with hope to reset it back to normal.

---

