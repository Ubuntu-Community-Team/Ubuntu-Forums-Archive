---
title: "Avidemux questions"
date: 2009-05-28
forum: Multimedia Software
---

### Post by Straumoy on 2009-05-28
Hello,

I've got a few questions related to Avidemux. Googling around didn't really get me anywhere, so here I am. I've stumbled over this wonderful piece of software and combined with Mediatomb this looks like a match made in heaven as far as PSP and PS3 goes. Now on to the questions.

[LIST=1]
[*]How do you get subtitles from MKV files to show after you've converted said file to a format that the PS3/PSP can handle? The subtitles are not in a separate file, they're integrated into the video itself. 
[*]Is there a way to open a folder in Avidemux, or do I have to take one file at the time, set the convert settings and add it in a job list?
[/LIST]

---

### Post by lovinglinux on 2009-05-28
> **Straumoy said:**
> [LIST=1]
[*]How do you get subtitles from MKV files to show after you've converted said file to a format that the PS3/PSP can handle? The subtitles are not in a separate file, they're integrated into the video itself. 
[/LIST]

MKV subtitles are probably not integrated into the video. The mkv format is just a container that can have several individual video, audio and subtitle streams inside it. So you could extract the subtitle from it using mkvtoolnix and then embedding it into the video with Avidemux filters. Since Avidemux will embed the subtitles into the video, by converting the subtitles to images and then overlaying them with the video images, the format you use to output doesn't really matter. You should be able to see the subs on any player.

I'm afraid that Avidemux cannot read subtitles from mkv files, so you need to extract them first.

> **Straumoy said:**
> [LIST=1]
[*]Is there a way to open a folder in Avidemux, or do I have to take one file at the time, set the convert settings and add it in a job list?
[/LIST]

I'm afraid you need to add to the job list manually. You could use WinFF or command-line if you need to batch convert.

---

