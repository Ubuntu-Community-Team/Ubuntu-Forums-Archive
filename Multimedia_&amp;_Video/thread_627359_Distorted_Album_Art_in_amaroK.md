---
title: "Distorted Album Art in amaroK"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by CharonIDRONES on 2007-11-30
Okay, let us begin. I have my music collection hosted on my Windows XP box (as I am on a laptop that doesn't even have a hard drive as big as the collection) but I have it set up as a read only mount on Ubuntu. I set up a Collection to my mount point, it went through all that jazz, and then once it was finally done, everything loaded just fine, except the album art! I noticed also that there was a previous post on the forums, in the same category that was left unanswered, so here I am :D

The program I use to do the id3 tag editting in Windows is mp3tag ([http://www.mp3tag.de/en/](http://www.mp3tag.de/en/)), all the tags are id3v2 utf-8. The album art is in the mp3 themselves (I find it easier when backing up, a more permanent solution). So if someone could help me out with a solution to this issue, that would be fabulous! I do like the amaroK application quite a bit, though I do admit I am more addicted to Winamp, c'est la vie. Attached is a snapshot of the distortion, I used the Cover Manager inside of amaroK to show that it is not a problem with just one or two albums, but all of them. I must also note that the album art displays fine in the three applications I have tested it with in Windows (Winamp, Windows Media Player 11, and mp3tag)

Sincerely,
Brandon
[IMG]http://img522.imageshack.us/img522/3441/screenshotro8.png[/IMG]

---

### Post by AldoAxel on 2007-12-20
I have the exactly same problem.

I use mp3tag to embed album art as well. 

Have you find out something?

See you.
:guitar:

---

### Post by raycosm on 2008-01-31
Same problem, used EasyTAG to edit album art, saved in UTF-8 ID3v2. It seems completely random on what songs are affected, because a song from one album will have album art fine while another from the same album with the same art will have it corrupted like that. Amarok was working absolutely fine until about yesterday when this started happening to me.

---

### Post by marpstar on 2008-02-05
I can also confirm this for Easytag 2.1.2 when opening files in BMPx or in Kid3.  I'm currently seeking a resolution.

---

### Post by wink80 on 2008-02-06
Disable Window Effects And The Problem Goes Away .... I Noticed That This Also Affects The Save As Window Under Gimp

---

### Post by raycosm on 2008-02-09
Amarok seems to work fine if I use a .png image as the album art but absolutely botches .jpg images. Thing is, most of the covers from Amazon must be .jpgs or something cause whenever I fetch a cover from Amazon, Amarok almost always messes it up.

---

### Post by unai_goiko on 2008-02-16
Alright.. this is a common problem as I see...

I've been having this problem for the past 4-5 months and have found no solution yet to it. I have to say that  I think that it has nothing to do with easytag since the cover images are succesfully saved inside the id3 tags on the mp3 files.

I'm saying this because I've added the files succesfuly to a different program, iTunes on Leopard, and the covers are shown correctly, so this MUST BE a problem with Amarok.

wink80 mentioned something related with desktop effect.. I'm afraid i have them disabled and that the problem stil there. It obviously has nothing to do with compiz....

---

### Post by renyee on 2008-02-17
I used to have distorted album art with Amarok, but not anymore! I simply removed the images (added with EasyTag) and just put the album cover in the same folder (called it 'cover.png') and now Amarok locates it by itself. Pops up every time on the on-screen display now. Hope that helps.

---

### Post by adlisyahmi on 2008-06-02
hmm, I had the same problem too,
Amarok must correct this bug

---

