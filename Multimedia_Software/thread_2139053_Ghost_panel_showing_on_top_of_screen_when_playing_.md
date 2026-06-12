---
title: "Ghost panel showing on top of screen when playing full screen video."
date: 2013-04-25
forum: Multimedia Software
---

### Post by cdysthe on 2013-04-25
Hi,

I am running Ubuntu 13.04 on a laptop with Intel graphics and everything works fine except for one problem I didn't have on previous versions: There's a ghost panel showing on top of the screen when I am playing movies in full screen. It happens regardless of whether I use VLC or Movie Player (Totem). It looks like this:

[http://bit.ly/17YVWBo]("http://bit.ly/17YVWBo")

What could be causing this and how can I get rid of it?

Update: I have found out that if I use SMplayer I do not have this problem in full screen. With Totem and VLC I do. Go figure.

---

### Post by Mkaveli on 2013-04-27
I am having the exact same problem so if someone can help i would apreciate it. Thank you

---

### Post by felipeautran on 2013-05-06
Same problem here. To (kind of) solve this I need to maximize the VLC (or any other video player) window and then put it in full screen, then the ghost panel won't appear. Unfortunately, I still have no idea on how to solve it for YouTube videos on Firefox.

I'm not sure but I think that's a bug with Unity. I couldn't reproduce the error in my notebook with GNOME installed. Searching on the web I found quite some people with the same problem, but apparently, no definitive solution. :(

Update: Ubuntu 13.04 with Intel graphics too.

---

### Post by Luiz Eduardo on 2013-05-06
I am having the exact same problem too :(
And I already updated my kernel to 3.9 version to try to solve the problem, but it didn't work.


PS: Sorry about my english.

---

### Post by Nausser on 2013-05-08
Same issue here as well. Running a Dell laptop with Intel graphics on Ubuntu 13.04. Not sure where to begin... Mplayer and VLC both has the same issue. Making youtube videos full screen starts the screen white, sometimes for quite a few seconds so you end up hearing the video but not seeing it. Not sure if these two are related. Using Chrome as a browser...

---

### Post by shantanu18 on 2013-07-14
It's known bug reported [here]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1170958"). This bug is already fixed but didn't come as update. It will come soon.
Panel shadow is causing the problem. You can fix it by disable the top panel shadow. 

```
sudo dpkg-divert --local --rename --divert /usr/share/unity/6/panel-shadow.png_disabled --add /usr/share/unity/6/panel-shadow.png
```

Now logout or restart unity (Alt+F2 and type unity)

To revert this change 
```
sudo dpkg-divert --local --rename --remove /usr/share/unity/6/panel-shadow.png
```

original post is [here]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&ved=0CDoQFjAB&url=http%3A%2F%2Fwww.webupd8.org%2F2013%2F05%2Ffix-shadow-displayed-on-top-of-full.html&ei=Y6LiUZWJFciNrQfJ0oCoDw&usg=AFQjCNGKlXkMGzxyCvF-HzlhYnN2UKq9zA&sig2=4rYSlWPAHziADXfCV8mkPA")

---

