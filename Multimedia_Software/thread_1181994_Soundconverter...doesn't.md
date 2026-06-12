---
title: "Soundconverter...doesn't"
date: 2009-06-08
forum: Multimedia Software
---

### Post by fatherted on 2009-06-08
I have a fresh install of Server 9.04 AMD64. I installed soundconverter and the appropriate gstreamer plugins through apt-get. 

I queued up a large (10GB) batch of mp3's to re-encode to a more compact format for my mobile phone, and it completed in about three minutes, which seemed slightly suspect. 

Upon inspection, the newly created folders were empty - soundconverter very nicely removed all the spaces and replaced them with underscores for the folder names, and then failed to do any conversion on the actual FILES. I've tried re-running this a couple of times with different option settings and I don't feel like I'm getting anywhere. 

Given that the Lame encoder is installed, why would this not be working?

---

### Post by alex2399 on 2009-06-08
Did you install LAME through that link on the bottom of the SoundConverter Preferences? If not, click it! It should work then since it uses some gstreamer plugin for LAME...don't know the name anymore

---

### Post by fatherted on 2009-06-09
Indeed I did. I also manually installed most of the other codecs I could think of on the off chance the problem might be related. 

However, nothing fixed it, it continued to behave in a bizarre and unpredictable fashion, and I eventually gave up. 

In other news, gnormalize works perfectly. I strongly recommend using it instead of wasting your time messing with soundconverter.

---

### Post by dartmusic on 2009-06-09
Make sure that the folders that you are putting the converted files are not right in your home folder.  I believe that you can make a folder called /home/[user]/Music/trancoded  or something of that nature.  I've had this problem before and it drove me nuts until I found out about this bug.

Other than that Soundconverter is a great program.

Good luck.

---

### Post by fatherted on 2009-06-09
Eh, it worked out for the best in any case. Gnormalize is *far* more full-featured, and now in addition to re-encoding everything I'm doing a volume-leveling pass at the same time which should hopefully result in far fewer "oh god my ears are bleeding" moments when going from one track to the next.

---

