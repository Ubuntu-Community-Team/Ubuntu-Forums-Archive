---
title: "Very weird ... every Internet app running slowly apart from Google Chrome (???)"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by wombatvvv on 2010-09-07
This has basically just occurred after a setup a new home wireless Internet connection.

It's bizarre and I have no idea what could be causing it. If any of you gurus can make some suggestions, I'd be greatly appreciative.

Basically, every Internet service runs slowly, or in "short bursts" apart from Google Chrome (which runs extremely quickly).

This includes Thunderbird, Filezilla, Firefox, Opera, etc. 

But I do have connectivity ... it's seems to just take a long time to start up and then happens in short bursts. First example, Filezilla might time out a few times trying to make a connection to upload a file, but when it finally does connect, the file will upload okay. But the problem will repeat for the next file/directory change/whatever. Thunderbird often times-out looking for mail-servers, but when it finally connects, they work fine in 30-second bursts. Firefox sits there loading for ages (20-30 seconds) before loading a web-page, but once it starts it seems to get it loaded fairly quickly.

The exception seems to be BitTorrents. They download at excellent speeds and don't go through highs and lows. 

Everything behaves like this except for Google Chrome, which runs extremely well and is almost instantaneous.

What's going on here, any ideas? None of those programs were acting like that before on my old network.

---

### Post by wesleybailey on 2010-09-07
To eliminate the problem, this is what I would do systematically, but you can cheat if you want to.

1. Plug laptop directly into internet connection(modem) and see if all connections are fast.
2. If all the connections are fast on a direct connection, then it must be the router.
3. Try adjusting the MTU of the new wireless router.

Let me know the model of the new router, and I can tell you where to look for that setting.

Latest Tutorial: [how to open uif in linux ]("http://wesleybailey.com/articles/uif-to-iso-converter")

---

### Post by wombatvvv on 2010-09-07
> **wesleybailey said:**
> To eliminate the problem, this is what I would do systematically, but you can cheat if you want to.

1. Plug laptop directly into internet connection(modem) and see if all connections are fast.
2. If all the connections are fast on a direct connection, then it must be the router.
3. Try adjusting the MTU of the new wireless router.

Let me know the model of the new router, and I can tell you where to look for that setting.

Latest Tutorial: [how to open uif in linux ]("http://wesleybailey.com/articles/uif-to-iso-converter")


Thanks very much!

It's a D-LINK modem/router and the model no. is DSL-2642B.

Cheers!

---

### Post by wojox on 2010-09-07
> **wombatvvv said:**
> Thanks very much!

It's a D-LINK modem/router and the model no. is DSL-2642B.

Cheers!

I use that router at my sister-in-laws house. I pretty much have to be standing right over it to deal with those burst issues. 

Have you also tried seeing if moving any closer helps for now?

---

### Post by wombatvvv on 2010-09-08
Nope, moving closer makes no difference, nor does plugging it in with a network cable instead of wireless.

The really strange thing is that Google Chrome is completely unaffected. In fact, it's lightning fast. Anything else is absolutely struggling, mail clients, FTP clients, whatever.

I asked my girlfriend to try Internet Explorer on her little Notebook, and it worked perfectly fine, so whatever the problem is, it's just my computer ... except for Google Chrome.

Is it possible Chrome is accessing the connection is some way that the other programs are not?

---

### Post by wombatvvv on 2010-09-08
P.S. I just fired up Windows 7 on VirtualBox, and Internet Explorer 8 runs perfectly. Just like Chrome in Ubuntu. So I guess it's obviously the operating system.

What a shame. I'd hate to have to be loading up Windows every time I need to do some work with FTP/whatever. I'd be ashamed! ;)

Any suggestions?

---

### Post by wombatvvv on 2010-09-08
anyone?

---

