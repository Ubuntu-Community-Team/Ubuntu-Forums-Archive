---
title: "How to play MP3 audio stream in terminal"
date: 2023-01-19
forum: Multimedia Software
---

### Post by Grimly Fiendish on 2023-01-19
Hello!

I would like to play an audio MP3 stream (specifically this one: [https://dir.rcast.net/radio/66127](https://dir.rcast.net/radio/66127)) in a terminal on Ubuntu Server 22.04.1

I'm looking at possible solutions like MPG123, nvlc (ncurses VLC) and pyradio but I'm all at sea at the moment and not having any luck, so any pointers would be hugely appreciated!

Thanks in advance :)

---

### Post by yancek on 2023-01-20
Several suggestions on software to use at the link below.

[https://askubuntu.com/questions/920539/how-do-you-play-a-sound-from-the-terminal](https://askubuntu.com/questions/920539/how-do-you-play-a-sound-from-the-terminal)

---

### Post by Holger_Gehrke on 2023-01-20
Using that address won't work since it's the web page for that radio in the rcast directory. The actual stream is at 'https://stream.rcast.net/66127'. Found it using the 'network analysis' function (ctrl-shift-e) of the web-developers functions in Firefox. Using that address with mpv or ffplay works just fine.

Holger

---

### Post by mIk3_08 on 2023-01-21
> **Grimly Fiendish said:**
> Hello!

I would like to play an audio MP3 stream (specifically this one: [https://dir.rcast.net/radio/66127](https://dir.rcast.net/radio/66127)) in a terminal on Ubuntu Server 22.04.1

I'm looking at possible solutions like MPG123, nvlc (ncurses VLC) and pyradio but I'm all at sea at the moment and not having any luck, so any pointers would be hugely appreciated!

Thanks in advance :)
I haven't experience this kind of trick yet. But I have already played mp3 file using terminal with sox. Regards and cheers.

---

### Post by ajgreeny on 2023-01-21
I have little experience of this but try ***paplay <url>***

---

