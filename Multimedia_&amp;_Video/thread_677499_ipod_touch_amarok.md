---
title: "ipod touch amarok"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by myusername on 2008-01-24
ive got an ipod touch running 1.1.1 firmware ans it's jailbroken and i followed the guide about setting it up in amarok...but it deletes my album art...so is there any way to use amarok (or anything touch compatible) and an ipod touch that supports album art?

---

### Post by gtkourounis on 2008-01-24
i am not exactly sure if gtkpod works with ipod touch, but install it and see if it can recorgize it as a devise. If it does you can browse album art and/or find it through the program and save it in your touch...

just go to the terminal and type
```

sudo apt-get install gtkpod

```

---

### Post by myusername on 2008-01-24
ive tried gtkpod but it doesnt really work well

thanks anyway

---

### Post by raycosm on 2008-01-26
If you're getting all of your album art from Amarok, there isn't any album art being "deleted" from anywhere. If I understand correctly, when Amarok gathers album art for you, it doesn't write album art to the ID3 tags. The iPod won't display album art unless it's written in the tag, so you'll have to find a program that writes album art to ID3 tags. I used [EasyTAG]("http://easytag.sourceforge.net/") for the job, and it's faster than iTunes because you can tag multiple files with an album art at the same time (select the files you want to tag with a particular album art, add the art, and then click the little box to the right).

And if you're going to manually tag album art with EasyTAG, I'd like to recommend an Amarok script called "[CopyCover]("http://kde-apps.org/content/show.php/CopyCover+(amaroK+Script)?content=22517")". It uses the album art that Amarok finds and automatically makes a .png file in the folder that the song you are listening to, and changes the icon of the folder to album art. It works better if all your music is placed in folders by albums, and I think it only works in KDE (at least the changing of folder icon only works in KDE), but it makes tagging album art easier with EasyTAG because when you click to add album art to a song, the file browser starts in the directory of the song you're adding album art to, which makes adding album art to a whole album take only four clicks.

---

### Post by ntetreau on 2008-01-31
> **raycosm said:**
> If you're getting all of your album art from Amarok, there isn't any album art being "deleted" from anywhere. If I understand correctly, when Amarok gathers album art for you, it doesn't write album art to the ID3 tags. The iPod won't display album art unless it's written in the tag, so you'll have to find a program that writes album art to ID3 tags. I used [EasyTAG]("http://easytag.sourceforge.net/") for the job, and it's faster than iTunes because you can tag multiple files with an album art at the same time (select the files you want to tag with a particular album art, add the art, and then click the little box to the right).

And if you're going to manually tag album art with EasyTAG, I'd like to recommend an Amarok script called "[CopyCover]("http://kde-apps.org/content/show.php/CopyCover+(amaroK+Script)?content=22517")". It uses the album art that Amarok finds and automatically makes a .png file in the folder that the song you are listening to, and changes the icon of the folder to album art. It works better if all your music is placed in folders by albums, and I think it only works in KDE (at least the changing of folder icon only works in KDE), but it makes tagging album art easier with EasyTAG because when you click to add album art to a song, the file browser starts in the directory of the song you're adding album art to, which makes adding album art to a whole album take only four clicks.

Sorry to have to say this but amarok syncs my album art without problems.  You need to follow the wiki to the letter, including the parts on how to setup the model of your ipod in amarok:

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

Your album art will appear directly on your touch without having to do anything else.

---

