---
title: "HTML5. Flash. Chrome. 11.10. Issues."
date: 2011-10-16
forum: Multimedia Software
---

### Post by Roasted on 2011-10-16
I have been using HTML5 on YouTube for quite some time. It seemed to do the job well and HTML5 videos as well as flash videos co-existed nicely during my playlists.

I just upgraded to 11.10 via fresh install. It began as Beta 2 and I upgraded it via dist-upgrade, so I should be up to speed now. In doing so, I preserved my home directory.

I had no flash or HTML5. I downloaded restricted-extras, nothing. I installed flash from software center, nothing. I downloaded flash from Adobe's site via apt, nothing. The fix? I downloaded flash from the Adobe's site via tar.gz, extracted it, and dropped it in /home/me/mozilla/plugins. Bingo, I had flash back.

Two questions:

I use Chromium. Why did putting the flash file in the mozilla/plugins folder fix Chromium?

Secondly, HTML5 doesn't work in Chromium. It only works in Firefox. Being a Chromium user, I dislike this. How can I fix it? (the video just continually spins as if it's loading, but it never loads)

---

### Post by WiseOneBrad on 2011-10-17
I found a post on askubuntu for a similar issue. The following fixed the problem for me:

sudo apt-get install ubuntu-restricted-extras
sudo apt-get install flashplugin-downloader flashplugin-installer

---

### Post by Roasted on 2011-10-17
I got Flash fixed. However, HTML5 is being the brat now. It just sits and spins, meanwhile Flash works fine...

This is only in Chromium...

What gives?

---

