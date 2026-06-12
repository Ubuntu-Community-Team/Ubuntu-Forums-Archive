---
title: "Xbox 360 and Ubuntu."
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by mikemcpherson on 2007-10-25
Hello everyone.

My name is Mike and I have been playing around with Linux on and off for a soild year. I have been a Windows user since I was little. I have alot of experiance with it, so I guess I always stuck with it (Even though I knew Linux was much more stable.) Latley my Windows has been acting very very, how should I say this.... crappy. I'm really tried of it. Basically to get down to the point I have a couple of questions. My main thing to do was play PC games, now that I have a Xbox 360, I play it instead. With 360, you can stream music to it, via Windows Media Player 11, and listen to music on your home stereo via your 360 and PC connected to it. If there is the possibility of doing this with some application or method for Ubuntu, I will switch over to Ubuntu in a heart beat. my music is on my 2nd harddrive and both are of course NTFS. I hope you guys can really help me, I would really love to transition over to linux.

Thanks Alot

Mike

---

### Post by Qwerty_ on 2007-10-25
NTFS is easily solved.

```
sudo apt-get install ntfs-config
```

then run

```
sudo ntfs-config
```

And select your preferences as required.

---

### Post by mikemcpherson on 2007-10-25
Thanks alot for the info Qwerty, but now as far as the ability for the Xbox to find my music folder, what should I do. For those who don't know what I mean, basically in Windows Media Player 11, you can have the option to let the Xbox 360 look at what folders you have set up with music and video in them, and search thru them on your 360 and play what you want.  How should I go about doing this? 


I was alo thinking, is it possible to some way install Windows Media Player 11 via Wine or some fashion and have it find my music folder then, but if not, is there a suggestion to what application should allow me to do this.



Thanks,

Mike

---

### Post by dk5151 on 2007-10-27
I've been using uShare. I found this link on another post in this forum a while ago, but I don't remember who posted the link to give credit to.

[http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/]("http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/")

You can find the packages at the link above, and then you need to run this command in the terminal:

ushare -p 49153 -D -x -c /media/sda1/MyVideos/converted/

Change the path to wherever you have your media. I have not tried this with videos, only music, but it works fine. It isn't perfect but it gets the music to your 360. Let me know if you have any trouble.

---

### Post by dk5151 on 2007-10-27
Oh and if you want it to run at startup, put the command into the startup programs under System > Preferences > Sessions

---

### Post by notwen on 2007-10-31
Hello, I am following the link you provided a couple of posts up.  I am unable to install the ushare .deb file due to a libc6 dependency issue.  I've checked in Synaptic and I have all of the libc6 packages available installed.  Any ideas how to correct this?

---

