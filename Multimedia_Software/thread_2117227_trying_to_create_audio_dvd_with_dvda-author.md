---
title: "trying to create audio dvd with dvda-author"
date: 2013-02-17
forum: Multimedia Software
---

### Post by greenbag on 2013-02-17
I've been trying to create an audio dvd of a 2gb concert in wav format, using dvda-author. I keep getting a 1mb vob. :p

I found a guide with commands, but right at the start, some commands don't compute in ubuntu 12.04 lts.

This is from the example:

> [yaro][/tmp]$ cd /tmp/dvd-audio-test/
[yaro][/tmp/dvd-audio-test]$ ls
razem 436704
-rw-r--r-- 1 yaro yaro 49497064 2006-08-14 18:55 0.wav
-rw-r--r-- 1 yaro yaro 54464488 2006-08-14 18:55 1.wav
-rw-r--r-- 1 yaro yaro 43082728 2006-08-14 18:55 2.wav
-rw-r--r-- 1 yaro yaro 52847080 2006-08-14 18:54 3.wav
-rw-r--r-- 1 yaro yaro 38649832 2006-08-14 18:55 4.wav
-rw-r--r-- 1 yaro yaro 42456040 2006-08-14 18:55 5.wav
-rw-r--r-- 1 yaro yaro 63417832 2006-08-14 18:55 6.wav
-rw-r--r-- 1 yaro yaro 53773288 2006-08-14 18:55 7.wav
-rw-r--r-- 1 yaro yaro 48543208 2006-08-14 18:55 8.wav
[yaro][/tmp/dvd-audio-test]$ dvda-author -o DVD -g *.wav

I get an error **-rw-r--r--: command not found**

Am I missing some files?

---

