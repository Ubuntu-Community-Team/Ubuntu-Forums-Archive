---
title: "Media center for Unbuntu?"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by prince_alfie on 2007-05-02
Which application will allow me to get the feel of Front Row for Macs or Windows Media Center? I would like to store my videos and have an interface that makes it easy to play them back. :)

---

### Post by reclusivemonkey on 2007-05-03
Might be overkill if you're not recording tv, but MythTV is great;

[http://www.mythtv.org/](http://www.mythtv.org/)

---

### Post by prince_alfie on 2007-05-03
Looks cool but unfortunately the screenshots don't make me seem like you can access your media files. I don't plan to record TV, so myth TV seems to be more like TIVO to me.

I'm looking for an all-around media player more like Apple TV.

---

### Post by backwardselvis on 2007-05-03
I actually have a buddy who uses only the mythvideo portion of mythtv. He can play any video format he chooses and it works well.

---

### Post by emil10001 on 2007-05-03
I have been running myth for a little while now, and while the initial setup can be a pain the first time around (find a few good guides and follow them to the letter), it is well worth the effort. It is much more than just a tv recording app, although it does a very good job at that, it is really an all-round media center, complete with music player, video manager, web browser, etc. The only thing to watch out for is that Ubuntu, for whatever reason, whats to create its own mythtv user, and auto-login to that account, immediately starting up myth, you should try to disable/not allow that. 

Another suggestion, in conjunction with using myth, is to pick up a wiimote, and grab the cwiid drivers off of wiili.org . The wiimote makes an excellent remote/mouse for myth, and you can edit the button mappings (before you compile the driver) to be buttons that are normally mapped in myth (which is the least amount of work). What you get, is a very straight forward interface, with a remote that is 10x better than that little crappy apple remote (which i've tried at the apple store and don't like). If you are interested in doing this, post back and i'll post my buttons file.

If you go this route, you won't be dissapointed, and you will likely start wanting a tuner card =) .

Good luck.

-John

---

### Post by mjitkop on 2007-05-03
You may want to try [Freevo]("http://freevo.sourceforge.net/about.html"). If you have a video card with a tuner in your PC, it can be used as a TV recording device but it's ok if you don't have one. You can also use Freevo just to play your media files. It is not in the repos so you have to install it manually, unfortunately. 

I haven't personally installed it yet but I will do it this weekend. :)

I hope it works well. The screenshots are promising.

[http://freevo.sourceforge.net/about.html](http://freevo.sourceforge.net/about.html)

---

### Post by emil10001 on 2007-05-03
No need to do Freevo, myth is trivial to install via apt-get, just enable all of the repos. Setup is another story, as it is a bit more involved. But, since you are only doing music and videos, and not TV, you can skip a decent part of the setup. Again, follow the directions to the letter. mythtv.org is a good place to go for documentation. 

Let us know what you've decided to go with.

-John

---

### Post by mjitkop on 2007-05-03
Thanks, John. I will try MythTV first since it can be installed by apt-get automatically. :)

---

### Post by superm1 on 2007-05-03
There are a few Ubuntu specific things to watch out for when using the ubuntu packages.  Follow the docs at [http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV) and just skip over the parts about configuring tuners and such.  You will basically do a backend/frontend install on the same system.  You'll still have to run mythtv-setup the first time, just dont go to the tuner pages.

---

### Post by prince_alfie on 2007-05-03
Ah, I see... so basically to get the functionality of front row then I only need the backend/frontend of the myth tv setup?

---

### Post by superm1 on 2007-05-03
I have never used front row, so I couldnt tell you.  But minimally, you will need a backend and frontend with the mythvideo plugin installed.

---

### Post by emil10001 on 2007-05-03
Yes, the interface is similar to frontrow (without the smooth transitions), that said, if you get myth going and set up, I think that you'll agree that it is far superior to apple's frontrow. You can see some screenshots of baisc functionality on the mythtv site: [http://mythtv.org/modules.php?name=MythFeatures](http://mythtv.org/modules.php?name=MythFeatures)

---

