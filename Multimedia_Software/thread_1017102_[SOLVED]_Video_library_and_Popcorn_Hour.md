---
title: "[SOLVED] Video library and Popcorn Hour"
date: 2008-12-20
forum: Multimedia Software
---

### Post by Kissell on 2008-12-20
Okay, so I have a Ubuntu server that has video files on it, and it's connected to a plasma tv/monitor and I just play the videos on the server using mplayer.

My roommate bought a Popcorn Hour media extender for the TV in the living room...  it's pretty cool ([http://www.popcornhour.com/]("http://www.popcornhour.com/")) it has a great interface to play and search through the movies I have on the server.  

Popcorn Hour is running on linux, so my question is, does anyone know where I can get the software?  I'd like to run it from my Ubuntu server without having to have the extra popcorn box.  I don't see why I should need to buy and add another physical box to my room when I already have a linux box connected to the tv.  I just want the nicer interface and searching abilities that popcorn offers, and to be able to share the laboriously constructed database pulled from IMDB with the popcorn box in the living room.

---

### Post by cariboo on 2008-12-20
If you go [here]("http:///www.networkedmediatank.com/download/myihome_download_note.html"), you can download the linux version of myihome server, I'm currently downloading it (the server is slow). I report back once I have installed it.

Edit: I Downloaded myiHome server version 5.0.2, I couldn't get it to work, but version 4.9.1 seems to work the way it is supposed to, I don't have a Popcorn Hour so I could go any further.

Once you have downloaded the file, extract to your home directory. In a terminal navigate to the directory:

```
cd myihomeLinux-v4.9.1
```

then type:

```
./startserver.sh
```

to start the server. This will create a directory called Library in your home directory. Navigate to ~/Library/myiHome and edit the preference.xml as per the Readme file, add the paths to your media. save the file and restart the server. You should be good to go.

Jim

---

### Post by Kissell on 2008-12-20
I saw that, but it went nowhere fast when i tried it, maybe I just don't know what to do...

I installed java runtime (apt-get install sun-java6-jre)

Ran the ./startserver.sh

edited the ~/Library/myiHome/preference.xml file to add my movies folder

re-ran startserver.sh

then what?  did you get farther than me?  I don't know what to do after that point...  it looks like this program is meant to be used with an external box attached to your tv, but I don't want to have another box, I just want to be able to use my Ubuntu box, nothing else.

---

### Post by Kissell on 2008-12-20
yeah, that's what i did...  but how you said you can go no further because you don't have a popcorn hour, that's what i want to know...

How can I go further without having a popcorn hour box?

The popcorn hour box is just another linux computer, so why i would I need another linux computer when I already have ubuntu hooked up to my tv, and popcorn hour would be playing from my ubuntu server anyway...  i'd like to run the popcorn hour program on ubuntu.

---

### Post by joef5052881 on 2008-12-20
[size=2][I note that the TV people love the mixed event and to VIPs, as if they know a lot more from the central closer. Bai Yansong also failed to cashing in on the trend, everywhere in the photos and text disclosed in the pro-Yen days of excitement and complacency, what "I am the first to applaud," I am sorry, I have to say this is Zhou Mei, it seems such Gongwei secret, of course, welcome you Kehe, I do not care!](http://www.chineefriendfinder.com/) From what the past, j[[color=#282827]A move that is not very Prior to the agreement, or to move to your mother [/color]high, but we all like to use, that is, the Cold War. After the quarrel, not-to-Phone, deliberately "forgotten" Jiaqu Zhu Yiqizhixiado not cgiving me freedom!" Ridicule is ynical. used when the husband and  "You do not take me out to play, I would also like to thank you for commonlywife quarrel bad trick, uses only](http://www.3gmm.net.cn/) [infuriated the other side. But this](http://www.1ke.net.cn/)ust [like what the quality of the weight, gravity is, the Zhanbian Zhanbian not think that he is a part. Bai Yansong boast in those aspects, I do not understand is "sitting in the front row," this sentence. We are all into the theatre. The front row and stand behind what is the difference between, viewers are not? ? But you see more, hear more bashing drums and gongs, Beijing dialect is "the purpose of eating." What need to perform the first row behind the audience to stand up to the audience to explain the story ? You can see what the background of insider things ? How how polite euphemism, no](http://www.3gmm.net.cn)other word - Zizuoduoqing. [Write this on the text, I also saw one of the Bai Yansong, "Dongfangzhizai", an interview with Yu Hua, this is his being Branch, I would like to here more about his true colors, so carefully observed this trick of the negative impact is significant and will bring enormous harm to both sides, is likely to](http://www.3gmm.net.cn)[/size]

---

### Post by abbot on 2008-12-30
it may have something to do with the fact that the popcorn hour box uses a separate chip for video & audio decoding rather than just straight software like a computer would.  that's the reason that the popcorn hour box plays 1080p mkv video butter smooth but takes 10 seconds to load a jpg or webpage.

you may want to look into a program called boxee.

---

### Post by Kissell on 2008-12-30
Boxee looks cool, but they won't let me download or use it, because it's in alpha and it appears to be in an invite only testing phase.  :(

---

### Post by Kissell on 2008-12-30
An alpha tester was kind enough to send me the boxee repositories for Ubuntu...  And it looks like they'll post .DEBs of the alpha on their website starting January 8th.

I am very impressed with Boxee!

I have been looking for a media center for a long time, and have tried XMBC, MythTV, SageTV, and Windows Media Center, among other less known solutions, and none of them were what I was looking for.

Boxee has the BEST interface by far!  Very cool graphical interface, similar to a black version of the Nintendo Wii channels, and it works very well with both keyboard and mouse, so you can use your Wii-remote on it!  :)

---

