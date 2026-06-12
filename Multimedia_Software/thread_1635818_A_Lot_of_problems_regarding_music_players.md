---
title: "A Lot of problems regarding music players"
date: 2010-12-02
forum: Multimedia Software
---

### Post by zhangyou on 2010-12-02
Hi, my first post here, meeting a lot of trouble when using music players lately

1. EXAILE and LISTEN both players won't play any music files, when started playing they just disappeared

I tried to run them in terminal, and it says "Segmentation fault" and nothing more. 

I googled for solutions, found one on the Linux Mint Debian Edition Forum, guys over there say the package of **python-gi** need to be removed. But when I try to remove it in my Ubuntu box, it also removes a lot of gnome applications and at the same time installs many KDE ones, that's not I am expecting otherwise I would rather go to Kubuntu instead.


2. Rhythmbox won't transfer aac files to my iPod Touch. When I drag AAC files over the iPod, Rhythmbox automatically transcodes them into Mp3s. This has been an issue for quite a while in my box however I find no solutions on the Internet. Many posts stated it was a very old bug and has been fixed in 2008. Strange. I clearly remember a few months back the issue didn't exist.

3. Rhythmbox again, actually not only Rhythmbox, but also Banshee and Sound-juicer. The problem is with the OGG conversion. They all crash when trying to convert my CD or some FLACs to OGGs. In the terminal it also says "segmentation fault" so I guess it might somehow relates to the first issue in this post.

4. How can I edit the .is_audio_player file in my Sandisk Sansa Mp3 to make it support AACs and MPCs? In the line output_formats I added [B]audio/mpeg,application/ogg
[/B]I tried audio/aac, audio/m4a and audio/mp4, didn't work, AACs were transcoded into MP3s. 
For MPCs I tried audio/mpc, audio/musepack, neither worked.

---

### Post by zhangyou on 2010-12-02
bump

---

### Post by tuppe666 on 2010-12-03
Hi, I am a little confused by your post, so in some part I am guessing to the real issue. The problem I suspect is AAC...and Apple, which although a good format is patent encumbered. What this means in practice is your Sandisk Salsa might not support the format...to play the files on Linux your have to enable restricted codecs, simply because of the cost involved in bundling this format. Be aware also that the files may contain information that identifies you.

Now that all being said as a fun suggestion other than enabling AAC on your ubuntu you may want to check out Rockbox, which may support in full or part your Salsa which would make me jealous, and does support AAC and everything else.

[http://en.wikipedia.org/wiki/Advanced_Audio_Coding](http://en.wikipedia.org/wiki/Advanced_Audio_Coding)
[http://www.rockbox.org/wiki/SoundCodecs#Current_status](http://www.rockbox.org/wiki/SoundCodecs#Current_status)
[http://www.rockbox.org/](http://www.rockbox.org/)

---

### Post by zhangyou on 2010-12-04
> **tuppe666 said:**
> Hi, I am a little confused by your post, so in some part I am guessing to the real issue. The problem I suspect is AAC...and Apple, which although a good format is patent encumbered. What this means in practice is your Sandisk Salsa might not support the format...to play the files on Linux your have to enable restricted codecs, simply because of the cost involved in bundling this format. Be aware also that the files may contain information that identifies you.

Now that all being said as a fun suggestion other than enabling AAC on your ubuntu you may want to check out Rockbox, which may support in full or part your Salsa which would make me jealous, and does support AAC and everything else.

[http://en.wikipedia.org/wiki/Advanced_Audio_Coding](http://en.wikipedia.org/wiki/Advanced_Audio_Coding)
[http://www.rockbox.org/wiki/SoundCodecs#Current_status](http://www.rockbox.org/wiki/SoundCodecs#Current_status)
[http://www.rockbox.org/](http://www.rockbox.org/)

Thank you very much for your reply. I already rockboxed my Sansa Clip+, actually I didnot even try out the original firmware since I bought it. :)

The transcoding issue is unsolvable to me in Ubuntu. Then I tried Debian, same results. Yesterday I spent some time installing an Archlinux, problem solved! Now I can convert FLACs to OGGs to my player, and when I copy AACs they will not be transcoded any more.

---

