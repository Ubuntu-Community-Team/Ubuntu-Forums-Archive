---
title: "My Zune MP3 player is working with Ubuntu!"
date: 2014-03-06
forum: Multimedia Software
---

### Post by pc10pc on 2014-03-06
I bought a 30GB zune player around 2009, or at least before I started using linux. I was never able to get it working with linux due to some kind of encrypted handshake MS used on it - until 2 days ago.
My searches for 'zune ubuntu' or 'zune linux' always led to this forum and other people stuck in a dead end. I searched 'linux mtpz' and found a site by [Sajid Anwar]("http://kbhomes.github.io/") who had been working on cracking the zune. I emailed him and he said yeah, I completed that about 2 years ago and told me how to hook things up.

*[FONT=arial]I hadn't touched the Zune MTPZ stuff in almost two years, I think, but I did finish most of the support if I remember correctly and got those changes implemented in the mainline libmtp. You should be able to install the latest version of libmtp with your package manager. Then, download and save this file to your home user directory as .mtpz-data: [/FONT][https://github.com/kbhomes/libmtp-zune/blob/master/src/.mtpz-data](https://github.com/kbhomes/libmtp-zune/blob/master/src/.mtpz-data)[FONT=arial] . Then you should be able to use your Zune with any software that uses libmtp (I'd give gMTP a shot first due to its simplicity)[/FONT]*

so I made the .mtpz-data file with the code from the link and fired up gMTP (which I already use for a Kindle Fire HD) and waited. And waited. Then finally my music files showed up, and I was able to transfer to and from the zune.

I realize people with zunes were few and far between, even less so now, but it's still a decent player and I'm really pleased to have it working on Ubuntu. Hopefully someone else will find this useful too.

---

### Post by AMPed126 on 2014-03-11
I found this thread by sheer luck, I actually wasn't even looking for  Zune compatibilty anymore.  I gave up about two years ago lol. But I  figured that I might as well give it a shot since I do still use my Zune  and awesome it worked to add music to my Zune! However music that was  on my Zune, I was able to download to my computer but I could not play  it....I tested out non DRM music and it just wouldn't do it. Does yours  allow you to download music from your Zune to computer and play no  problem?

Thanks for looking into this and posting your findings,  I'm sure we are few and farbetween but the Zune is really a great  device, regardless of it being owned by Microsoft.

---

### Post by pc10pc on 2014-03-12
i can upload and download from the device, and delete stuff off it. you can even make a playlist through gMTP. it's not pretty, but its working

---

### Post by Carl Alvey on 2014-07-11
> **pc10pc said:**
> i can upload and download from the device, and delete stuff off it. you can even make a playlist through gMTP. it's not pretty, but its working

I have followed the attached instructions and can connect and see my music on my zune.  As soon as I try to download the music from the zune to my computer I get an error for every song that it attempts to download.  The error is "Error getting file from MTP device.  Any additional suggestions.

---

