---
title: "missing codecs"
date: 2008-08-11
forum: Multimedia Software
---

### Post by medimais on 2008-08-11
I am a new member using xubuntu 8.04 on a dell 4500s as my only OS at the moment having formated and got rid of Windows XP. The only thing I miss is not being able to listen to streamed German radio. I tried to use Banshee but every time I get the message "no codecs". Have tried to download various ones but although many stations work which I don't want the German station HR2 is still not working. I've tried going onto the HR2 site and starting it with media player ( I click on the web page ) . It is then down loaded and I am asked which programme I want to use (Mplayer Default) And after that it asks me to choose what I want to open it with . Frustration!!

Have searched various forums but am no nearer a solution. Can anybody help?

Thanks.

---

### Post by unoodles on 2008-08-11
Welcome to the forums!

What you need is to install the gstreamer codecs from synaptic.
What format are the files?
Go into synaptic and search "gstreamer". You will see a whole bunch of packages called gstreamer-plugings-*.
Just install the one that has the codec you need. (If you install them all, you're sure to get it :D)

---

### Post by medimais on 2008-08-11
The files are .m3u. Now have all the gstreamer plugins and still no luck.
When I click on the default Mplayer it goes straight to the downloaded files and asks again what I want to open with.

Thanks unoodles!

---

### Post by diwas on 2008-08-11
Install ubuntu restricted extras:
```

sudo apt-get install ubuntu-restricted-extras

```

This might solve all the media problems including other u mite face in the future.

Cheers!

---

