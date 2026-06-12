---
title: "Playing f4v files"
date: 2011-11-13
forum: Multimedia Software
---

### Post by Open4D on 2011-11-13
There doesn't seem to be a great deal of information here (or elsewhere on the Web) about playing [f4v files]("http://pcsupport.about.com/od/fileextensions/f/f4vfile.htm") in Ubuntu.

[SIZE=1](The most promising search engine result I found was [http://www.linuxtalkforums.com/showthread.php/18349-Is-there-a-good-solution-for-playing-f4v-files-on-ubuntu?p=18679&viewfull=1](http://www.linuxtalkforums.com/showthread.php/18349-Is-there-a-good-solution-for-playing-f4v-files-on-ubuntu?p=18679&viewfull=1), but that no longer works and I couldn't find any mirrors.)[/SIZE]

So I thought I start a new thread on this topic, and get things rolling with my own experience ...


I am using 10.04 (Lucid Lynx), with *ubuntu-restricted-extras*, fully up-to-date.  (10.04 is a Long Term Support release.)

N.B.  I can play FLV files fine, which [are different]("http://superuser.com/questions/214214/are-f4v-files-the-same-as-flv-files").



In the file browser, f4v files show up as being of type 'unknown'.  If I double click on one, I get a "Could not display ... The file is of an unknown type" popup error.  This popup gives me a "Select Application" button, through which I can select "Movie Player".  [SIZE=1](Specifically, "Totem Movie Player 2.30.2" - "Movie Player using GStreamer 0.10.28")[/SIZE]

When I open f4v files in Movie Player, sometimes they work fine, but sometimes the *only* thing that works is the text at the bottom that tells you how long the video is.  The latter is the case even for f4v files that I have saved to my computer after *successfully* viewing them on a website.  Given this, I wondered why I couldn't just view the f4v files in Firefox.

Now, [this]("http://www.flvsoft.com/play-flv-with-firefox/") seems to suggest that to play even just FLV files (let alone f4v files) in Firefox, I might have to use "[Moyea Flash Video MX Pro]("http://www.moyea.com/video-to-flash/")" - but that only works on Microsoft Windows.

Instead I came across a Firefox extension called "[Ant Video Downloader and Player]("https://addons.mozilla.org/en-US/firefox/addon/video-downloader-player/?src=api")", which can play both FLV files and all the f4v ones that I have tried - including the ones that didn't work in "Movie Player".  For the time being I have been making this work by copying the f4v files into my "~/Downloads/Ant Videos" directory and *then* launching the Ant Player.


If I wanted to continue my investigations, the next thing I would try is this forum's [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683").

---

### Post by FakeOutdoorsman on 2011-11-13
Moyea is a violator of the FFmpeg license. This is one of many, if not hundreds, of similar Chinese based products that abuse the licenses of several free tools including FFmpeg and various encoders.

Can you provide a sample of a FV4 video that does not play correctly in Movie Player?

---

