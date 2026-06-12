---
title: "Media players mess"
date: 2008-12-02
forum: Multimedia Software
---

### Post by anil_robo on 2008-12-02
First of all, let me apologize for giving such a detailed explanation, but I think it'll make the matter clearer.

I recently returned to Ubuntu after a long time - I'd been primarily using a Mac for the last two years. Because I have a desktop and a laptop at home, I thought of moving all my music and videos to the Ubuntu desktop, and then mounting the music directory on my ubuntu laptop using ssh (sftp).

So far so good - I moved all my music to Ubuntu desktop server, the server is working fine, and I can mount the music directory using Nautilus. Now arises the big question:

"How do I play that music?"

I used "Media Player" to play the music, and it is able to play after some delay, which is acceptable because my music library is quite huge (40GB or so). But Media Player does not have a sound equalizer, so I don't like the sound quality at all, specially when I bought big speakers for it.

So I turn back to my faithful player, VLC. It is able to open single files on the mounted drive when I right click and "open with vlc", but ... when I try to open the entire music folder... It is adding items to the playlist slowly, probably would take two days to start playing music at this pace.

Now I am stuck, and a little bit angry because I was able to play that music on the mounted drive perfectly fine using both Mac (iTunes + Macfuse) and Windows (Winamp + Mapped network drive).

Can someone suggest a media player for Ubuntu that will be able to save the playlist files and play them again without waiting for the entire metadata to be re-read each time? Maybe I'm talking of a "media library"? And a sound equalizer is a must!

Thanks for reading my question in full, and I will be happy to provide more details, but I really do need a media player! ):P

---

### Post by cariboo on 2008-12-02
You   missed one on your poll, I use listen, it takes about 15 minutes to populate the play list the first time (I've got over 10,000 songs in my music collection). Listen doesn't have an equalizer, but it sounds the same as xmms. I would suggest if your music needs equalization, you are not ripping them at high enough quality, I use either vbr or a minimum bitrate of 256 for all my mp3's.

Jim

---

### Post by anil_robo on 2008-12-02
I've been ripping music for almost 10 years now, and it was hard to keep them together on a 3GB hard drive in 1993. So I ripped them at 56kbps to begin with. Most of the CDs I ripped refuse to play any more, and I can't re-rip them. Hence the need for equalization - it's something I can't live with. For now, I'm just using VLC - it finished adding all songs to list in about two hours, and I have saved the playlist as .m3u.

I seriously think Ubuntu should have equalizer built-into all music players by default. I was also trying to find a graphical equalizer for the system audio, but couldn't get something that was easy to use.

---

