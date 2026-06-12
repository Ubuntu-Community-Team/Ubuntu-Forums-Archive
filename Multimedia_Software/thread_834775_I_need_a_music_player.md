---
title: "I need a music player"
date: 2008-06-19
forum: Multimedia Software
---

### Post by Detox06 on 2008-06-19
So, I need a new music player. Banshee was doin me pretty well, but I have well over 10,000 songs in my music library now, and it just isn't capable of handling it. I remember with Winamp, I was able to sort by artist or album, and no matter how many songs I had (I had well over 20,000 at one point before a major crash) I never had a problem with winamp crashing. 

What I need: 

1. Read ALL my music. (Songbird has some great features, but won't read certain albums by certain artists, even though every song I have is mp3.)

2. Don't freeze while browsing my library. Both Banshee and Songbird fail miserably at this. 

3. Read mp3 tags. (Again, Songbird does great, except for certain songs where it won't read the mp3 tag. I've recently updated all of them to idv3, so that shouldn't be an issue but apparently is.)

4. Browse by artist or album (Songbird does this really well, but fails at a couple of the more important ones)

Anyone have suggestions? I've tried Amarok in the past, and its been the best to me, but if I can get one to work without installing all of the kde libs, I'm great.

---

### Post by ibutho on 2008-06-19
Try Exaile. Its a bit similar to Amarok, but its built using Python and GTK. I don't know if it will suite your needs, but its worth a try.

---

### Post by kk0sse54 on 2008-06-19
> **Detox06 said:**
> So, I need a new music player. Banshee was doin me pretty well, but I have well over 10,000 songs in my music library now, and it just isn't capable of handling it. I remember with Winamp, I was able to sort by artist or album, and no matter how many songs I had (I had well over 20,000 at one point before a major crash) I never had a problem with winamp crashing. 

What I need: 

1. Read ALL my music. (Songbird has some great features, but won't read certain albums by certain artists, even though every song I have is mp3.)

2. Don't freeze while browsing my library. Both Banshee and Songbird fail miserably at this. 

3. Read mp3 tags. (Again, Songbird does great, except for certain songs where it won't read the mp3 tag. I've recently updated all of them to idv3, so that shouldn't be an issue but apparently is.)

4. Browse by artist or album (Songbird does this really well, but fails at a couple of the more important ones)

Anyone have suggestions? I've tried Amarok in the past, and its been the best to me, but if I can get one to work without installing all of the kde libs, I'm great.
You might have gotten the nightly build of Songbird which is the latest unstable version of it. I use songbird right now and I have around 10,000
all in mp3 and whatever other format that itunes gives you when you buy music from them and it doesn't freeze at all with me and it recognizes and plays them all. Nor does it lag like winamp, itunes, and Rythmebox. I used to use Exaile it all right pretty much just Amarok for Gnome you might want to check it out.

---

### Post by cozmicharlie on 2008-06-19
Quod Libet is another that may work for you.

---

### Post by jrusso2 on 2008-06-19
Amarok is best if you have a large database of songs then use mysql instead of sqlite with amarok.

---

### Post by Detox06 on 2008-06-19
@C!oud: I have version 0.6 stable. Maybe I need to reinstall. 

I tried exaile, but it doesn't show the songs in the main window. I have to use the sidebar. 

> For now, I think I'm going to use Winamp on Wine, but I am still trying all the suggestions you guys are giving, so please continue. If I can find one native as good as winamp, I'll be sold. Songbird is VERY close to being that one.

Edit: Winamp/WINE is more of a problem than its worth. =(

---

### Post by kk0sse54 on 2008-06-19
> **Detox06 said:**
> @C!oud: I have version 0.6 stable. Maybe I need to reinstall. 

I tried exaile, but it doesn't show the songs in the main window. I have to use the sidebar. 



Edit: Winamp/WINE is more of a problem than its worth. =(

When I first started using Linux I faced the same problem being a big Winamp fan in windows so I tried to install it in wine and I definitely agree with you it's way more problems than it's worth

---

### Post by Detox06 on 2008-06-20
@C!oud, with Songbird 0.6, its almost perfect. It hasn't frozen on me so far, but I have over 9,000 songs, and it won't read the metadata for them. It will show, for example, '01 - Song Name' in the title field of ALL of the tracks, and I have to listen to the first 5-10 seconds of the track to get it to register all the metadata. Do you have this same problem? Do you have a fix for it?

---

### Post by kk0sse54 on 2008-06-20
> **Detox06 said:**
> @C!oud, with Songbird 0.6, its almost perfect. It hasn't frozen on me so far, but I have over 9,000 songs, and it won't read the metadata for them. It will show, for example, '01 - Song Name' in the title field of ALL of the tracks, and I have to listen to the first 5-10 seconds of the track to get it to register all the metadata. Do you have this same problem? Do you have a fix for it?

I have never experienced this. I'm around the 8,900 range in number of songs and it already has all the metadata shown. What made it work for me though was that I downloaded an Add-On which imports your itunes library from windows or MAC, if you used itunes. It essentially reads a config file for itunes which tells itunes where each song was located and the information about that song and playlists. You just have to change the file destinations within that config file so that they point to locations in the way linux would name them. For example if you had your music stored in C drive under windows then you change it to say /media/disk-1 or whatever its called under your linux OS.

---

### Post by madmed on 2008-06-20
if you like winamp then try xmms or audacious or bmp they also support winamp skins!

---

### Post by Detox06 on 2008-06-22
xmms doesn't have a good enough library mode. And I don't like the look of Audacious. However, I redownloaded Songbird from Getdeb, and it works perfectly. So, I'm happy now. Hehe.

---

### Post by Moonshiner on 2008-06-29
Exaile looks very promising! And it works way faster than Banshee on my ancient PIII system ;)

---

### Post by hanniph on 2008-06-29
> **Detox06 said:**
> @C!oud, with Songbird 0.6, its almost perfect. It hasn't frozen on me so far, but I have over 9,000 songs, and it won't read the metadata for them. It will show, for example, '01 - Song Name' in the title field of ALL of the tracks, and I have to listen to the first 5-10 seconds of the track to get it to register all the metadata. Do you have this same problem? Do you have a fix for it?

I had this problem when I installed Songbird manually from tarball. I guess it was something wrong with installation because after I reinstalled Songbird from deb package, the Songbird was able to read metadata instantly.

---

