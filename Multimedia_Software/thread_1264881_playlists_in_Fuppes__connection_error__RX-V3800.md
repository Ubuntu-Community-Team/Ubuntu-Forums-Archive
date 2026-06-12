---
title: "playlists in Fuppes / connection error / RX-V3800"
date: 2009-09-12
forum: Multimedia Software
---

### Post by Gerwazy on 2009-09-12
Hello,
I've succeeded installing the last Fuppes on my Xubunto 9.04 64b. The only problem I have is the playlists aren't recognized in the right way and I get connection error on my Yamaha RX-V3800. I've tried with pls and m3u creating them with Rhythmbox. 
Does anybody know how should it look like? I mean the path to the song. (Rhythmbox has no problem with it, only fuppes has)
my test.pls
```
[playlist]
X-GNOME-Title=test
NumberOfEntries=1
File1=Green Day/21st Century Breakdown/14-Horseshoes And Handgrenades.wma

```
and the shared_objects section in my fuppes.cfg
```
  <shared_objects>
    <dir>/media/av/AV/Music/WMA</dir>
    <!--<itunes>/Users/.../iTunes.xml</itunes>-->
  </shared_objects>

```
There is "Green Day" folder in this folder but fuppes expects something different.
Thanks in advance

---

