---
title: "Howto listen to internet radio"
date: 2012-01-08
forum: Multimedia Software
---

### Post by matza55 on 2012-01-08
Can someone tell me how to do, so I can listen to my favorite radioprogram. I live in Sweden, but that perhaps not make differens?

---

### Post by I_can_see_the_light on 2012-01-08
> **matza55 said:**
> Can someone tell me how to do, so I can listen to my favorite radioprogram. I live in Sweden, but that perhaps not make differens?

What station are you trying to listen to?

---

### Post by mörgæs on 2012-01-08
Are you looking for something like **dradio**?

---

### Post by ajgreeny on 2012-01-08
Have a look at radiotray which sits in the system tray (panel) and uses very low resources.

I'm not sure how well that works if you move on to unity desktop in future, as there is no panel in the same way on unity.  Perhaps it is all done differently in that DE.

---

### Post by matza55 on 2012-01-08
> **ajgreeny said:**
> Have a look at radiotray which sits in the system tray (panel) and uses very low resources.

I'm not sure how well that works if you move on to unity desktop in future, as there is no panel in the same way on unity.  Perhaps it is all done differently in that DE.
I'm on Unity, I don't see how to start it?

---

### Post by matza55 on 2012-01-08
> **mörgæs said:**
> Are you looking for something like **dradio**?

I don't now. But I can test if Y think it's good....

---

### Post by mörgæs on 2012-01-08
I do think it's good - if you can stand having the Danish 'DR' logo on your computer :-)

---

### Post by matza55 on 2012-01-08
Thats OK! I will test...

---

### Post by matza55 on 2012-01-08
> **mörgæs said:**
> I do think it's good - if you can stand having the Danish 'DR' logo on your computer :-)

But you never say - how?

---

### Post by mörgæs on 2012-01-08
Like all other applications: 

sudo apt-get install dradio

---

### Post by andrew.46 on 2012-01-09
There is a nice lua script that adds a convenient radio menu to vlc. A bit of fiddling is involved but the effort is worthwhile. I attach a screenshot of the script in action, the visualisation is not part of the script :).

---

### Post by matza55 on 2012-01-09
Thanks!

---

### Post by matza55 on 2012-01-09
Look nice!

---

### Post by matza55 on 2012-01-09
I will listen to P4 Sörmland, their news is good.

---

### Post by I_can_see_the_light on 2012-01-09
> **matza55 said:**
> I will listen to P4 Sörmland, their news is good.

Have you gotten it to work? If not, open Totem (Movie player) and paste one of the following liks: ```
http://sverigesradio.se/topsy/direkt/202.rtmp
```or
```
rtmp://rtmp-live.sr.se/webbradio/kanaler/p4sormland-aac-96
```

You might have to install [librtmp0]("apt://librtmp0") and [rtmpdump]("apt://rtmpdump")

---

### Post by matza55 on 2012-01-10
> **I_can_see_the_light said:**
> Have you gotten it to work? If not, open Totem (Movie player) and paste one of the following liks: ```
http://sverigesradio.se/topsy/direkt/202.rtmp
```or
```
rtmp://rtmp-live.sr.se/webbradio/kanaler/p4sormland-aac-96
```

You might have to install [librtmp0]("apt://librtmp0") and [rtmpdump]("apt://rtmpdump")

Thank's - it works fine!

---

### Post by coldraven on 2012-01-10
I just did this.
I went to this site: [http://www.listenlive.eu/sweden.html](http://www.listenlive.eu/sweden.html)
Then i right clicked on the first station (192kbps) and selected "Save Link Location".
Then I ran VLC (you can install it from the Software Centre)
Then select Media>Open Location from clipboard
It pasted this: [http://sverigesradio.se/topsy/direkt/132-hi-aac.pls](http://sverigesradio.se/topsy/direkt/132-hi-aac.pls)
Now I have Swedish radio which I cannot understand :)

In VLC look at View>Playlist for other options, like Internet>Jamendo Selections

---

### Post by matza55 on 2012-01-10
> **coldraven said:**
> I just did this.
I went to this site: [http://www.listenlive.eu/sweden.html](http://www.listenlive.eu/sweden.html)
Then i right clicked on the first station (192kbps) and selected "Save Link Location".
Then I ran VLC (you can install it from the Software Centre)
Then select Media>Open Location from clipboard
It pasted this: [http://sverigesradio.se/topsy/direkt/132-hi-aac.pls](http://sverigesradio.se/topsy/direkt/132-hi-aac.pls)
Now I have Swedish radio which I cannot understand :)

In VLC look at View>Playlist for other options, like Internet>Jamendo Selections

Fantastic!! You are great - thanks for the help! Sorry what Y can't understand, but often they play good music also... :D

---

