---
title: "Bluetooth not working properly."
date: 2019-01-20
forum: MINT
---

### Post by dondymenelo on 2019-01-20
Hi, just wondering why my bluetooth suddenly not working properly, I've been using Linux Mint 18.1 for couple of months and it works great I installed it on my old laptop Asus s550c, then last month I upgraded it to 19.1 it works well but I found out recently that the bluetooth is not working properly but drivers are all present, blueman can show the list and it allows to paired, but whenever it's done the pairing my bluetooth speaker somehow doesn't detect that it was paired. I'm thinking there's some drivers I need to manually download and install but I just don't what it is.
```
pacmd list-cards
``` 
& 
```
pactl list short | grep blue
``` 
show results for the "audio speakers" & "audio-headphones" so I'm also thinking it might be also the bluetooth speaker is not been recognized / compatible is that possible? Before it was working well on 18.1.

Any response is appreciated.

Thanks.

---

### Post by nyeba on 2019-01-23
Hmm I haven't go into 19.1 still using 18.1, I encountered this pairing problem on my bluetooth speaker [jbl]("https://www.jbl.com/") and [aomais sport ii]("https://www.soundsmeister.com/aomais-sport-ii")  similar issue it doesn't detect even it was a successfully  paired. I think what you missed is the a2dp.py it was long thread and  still continuously listing a problem at  [https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1577197](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1577197),  to make it short you can easily install it with this:

```
wget [https://gist.github.com/pylover/d68be364adac5f946887b85e6ed6e7ae/archive/d698974910bbb7d016ec0ad08c1bf41b4b524364.zip](https://gist.github.com/pylover/d68be364adac5f946887b85e6ed6e7ae/archive/d698974910bbb7d016ec0ad08c1bf41b4b524364.zip)
unzip d698974910bbb7d016ec0ad08c1bf41b4b524364.zip
mv ~/d68be364adac5f946887b85e6ed6e7ae-d698974910bbb7d016ec0ad08c1bf41b4b524364/a2dp.py .a2dp.py
chmod +x a2dp.py
```
 
After pairing and reconnecting you need to run ```
./a2dp.py
```

Hope this helps.

---

