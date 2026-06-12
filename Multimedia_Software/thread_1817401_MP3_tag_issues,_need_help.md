---
title: "MP3 tag issues, need help?"
date: 2011-08-03
forum: Multimedia Software
---

### Post by christopher.suttles on 2011-08-03
I have a very clean and nice music library on my laptop, running Ubuntu 11.04. Everything shows up correctly under banshee. All the artist, song info, and album art. It also shows up by right clicking the files under nautilus and going to the song info tab under its properties.

However, I have a phone with an 8 GB micro SD card that supports mp3. When I used to use Windows i had no issues with tags showing up. I would just copy paste the music to the my_music folder of my phone, and in windows I used WMP as my music player. My phone is a Samsung R355C that I use with StaightTalk. 

I used EasyTag to tag my audio. I strip all ID3v1 tags, and only use ID3v2.3.

Everything shows up correctly on my phone, except some songs have "Unknown" artist and a few show random jumbled letters. Example of one artist is "cn ol" without the quotes.

My question is am I doing something wrong or could it be my phone? I have triple checked my work, and even re-forced the saving of the tags of every song on the SD card, and even re-formatted it but every time I have the same problem.

I tried to attach a song for someone to check if they pleased, but even putting a song in a .zip wont upload, as they forums have pretty crazy restrictions on file sizes, less than 1MB for .zips.

Any help would be greatly appreciated!

Using EasyTag version 2.1.5 (Latest I believe)
Already ran sudo apt-get update && sudo apt-get upgrade to check for latest updates even though I doubt that is the problem.

---

### Post by aeiah on 2011-08-03
perhaps your phone isnt fully compatible with ID3v2.3?

have you tried changing the tags on a few problem examples to a prior version of ID3?

---

### Post by christopher.suttles on 2011-08-03
[]("http://ubuntuforums.org/member.php?u=71962")Aeiah you are a lifesaver! That did the trick. Stripped the 2.3 tags on one album and switched to the older tag format (EasyTag only shows it was 1. tags, assuming 1.0), and it works.

The funny thing is all my music worked fine originally when working with windows, and the music worked fine with 2.3. But that was a few weeks ago before I finally made the full leap from Windows to Linux.

---

