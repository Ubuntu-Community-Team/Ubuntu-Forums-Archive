---
title: "Proprietary Mp3 Tags"
date: 2013-04-07
forum: Multimedia Software
---

### Post by user777 on 2013-04-07
I have established, beyond reasonable doubt that most mp3 players search for proprietary tags in mp3 files.

=>

I copied my music collection to a new device - an Archos.

Some track listings for albums appeared in the correct order.

Others did not.

The ones that appeared in the correct orders were A) The ones I ripped from CD in Windows Media Player. and B) The One I downloaded from iTunes.

The tracks that did not appear in the correct order were the ones that I ripped in Linux.

Since the files for the Windows and iTunes albums contained proprietary tags, I am thinking that this is the cause of the disorder.

The windows tags begin "WM/..." and are followed by bytecode, and the iTunes tags begin "ITUN" and are also followed by bytecode.

I was wondering if there was a way to fool my new (and currently redundant) Mp3 player into thinking that all of my tunes contained the requisite, proprietary tags needed to ensure the correct sort-order.

---

### Post by tgalati4 on 2013-04-07
Depending on what tool you used to create your mp3 files, there are several versions of ID3 tags.  My guess is the Archos is programmed to interpret the latest version of ID3.  Try using *easytag* to compare the tags and clean up the linux ones so that they show up correctly.

I have an old Sandisk mp3 player that stopped playing podcasts because of embedded pictures.  It has a monochrome sceen and can't handle embedded pictures.  After deleting the pictures, the podcasts play normally.

---

