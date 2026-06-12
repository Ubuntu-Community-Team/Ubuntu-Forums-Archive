---
title: "Play me a song, Ubuntu."
date: 2020-01-01
forum: Multimedia Software
---

### Post by MartyBuntu on 2020-01-01
My machine is a Ryzen 7, 16GB of RAM with an NVIDIA 750ti running Ubuntu MATE 18.04.
What I'd like to do is have this system play a song, one specific song, once every day at a specific time of the day. It's an 8 MB .mp3 file.I typically listen to audio files with VLC or Audacious.

How can I automate the playing of one song as a schedule? Thank you.

---

### Post by Yellow Pasque on 2020-01-02
The first few sections here should get you up to speed on cron: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

As for the command, mpg123 is a simple program that should do what you want:
```
sudo apt-get install mpg123
mpg123 <path to file>
```

---

