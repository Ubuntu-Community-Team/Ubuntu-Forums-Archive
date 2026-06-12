---
title: "Catching FLV videos from webpages"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by julzKB on 2008-03-31
Hello,

Does anyone know a way a download a flv/swf flash video from a webpage ? a flash video catcher in other words . There are several utilities on windows, so I`m suspecting there is a way in Linux .. command line would be even better ...

thanks !

-J

---

### Post by slimx3m on 2008-04-01
i would recommend you Download Helper extension from firefox. you could get it here [https://addons.mozilla.org/en-US/firefox/addon/3006]("https://addons.mozilla.org/en-US/firefox/addon/3006")

i use it even to download audio and picture files

hope it helps

---

### Post by shaggy999 on 2008-04-01
There's another slick way to do it. Wait until the flash file has completely loaded in your browser and then at the command line go to /tmp There will be a file called FlashwYhs2Kw7 or something similiar. The filename always starts with "Flash". Then just cp Flash* /home/username and you have a copy of it. The flash file is playable in VLC or totem or whatever. Or you can find a script (I know there's one out there) that converts the flv video to divx/xvid. It's very important that you wait to copy the file until after the complete video has downloaded, otherwise you just get a partial video. NOTE: once you leave the webpage that the flash file is on the file will disappear from /tmp

---

### Post by julzKB on 2008-04-01
interesting ways ..
I was actually looking for a more "command line approach", since I would like to do that from a server on which I usually don`t run the gui...

---

### Post by Prefix100 on 2008-04-01
It depends on what site your trying to download swfs from.

If its a site like newgrounds you can use 'view source' to find where the swf is located, then use wget in terminal to download it.

---

### Post by eye208 on 2008-04-01
> **Prefix100 said:**
> If its a site like newgrounds you can use 'view source' to find where the swf is located, then use wget in terminal to download it.
This way you will only get a copy of the player applet, not the movie itself.

Flash video is FLV, not SWF. Some websites based on Flash 9 also use MP4.

Retrieving the stream from the /tmp folder works only for video by the way. Audio streams are not stored on disc, but you can look up the URL from the cache info page in Firefox ("about:cache").

---

### Post by Prefix100 on 2008-04-01
I find that with some sites, such as newgrounds, the swf is the movie.

---

### Post by julzKB on 2008-04-01
Is this case , I`ve managed to extract the path to the .flv by actually parsing and RSS and then feeding it to wget ..

But that`s a workaround :)

---

### Post by eye208 on 2008-04-01
> **Prefix100 said:**
> I find that with some sites, such as newgrounds, the swf is the movie.
It's probably a short FLV clip embedded in a SWF applet. Some banner ads use this technique. Anyway, a SWF file is a program, not a video stream, i.e. you can't edit or transcode the clip until you extract the FLV from the applet.

---

