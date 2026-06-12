---
title: "Amarok, System Sounds are not working after installing restricted codecs."
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by keka on 2007-05-19
Hi, I have tried to play a movie file in VLC but it only had sound no picture. Then I have tried it in Movie Player and Ubunutu 7.04 told me to download restricted codecs (3) of them. So I did and now I can watch the movie in Movie Player fine but everywhere else audio is muted. I can hear GAIM soun activity and I can listen to mp3's in Movieplayer but VLC, Amarok and System Sounds are muted. Please help me remove restricted codecs or suggest a solution. I have tried reinstalling  xine-codecs in Synaptic P. M. nothing seems to be working. Thanks

---

### Post by joslinar on 2007-05-19
I had the same problem until yesterday. I solved it removing for the hidden file .asoundrc in my home folder. On a terminal windows type "rm ~/.asoudrc".
If it works you'll have to thanks dbott67 who suggested that solution for me.

---

### Post by keka on 2007-05-19
> **joslinar said:**
> I had the same problem until yesterday. I solved it removing for the hidden file .asoundrc in my home folder. On a terminal windows type "rm ~/.asoudrc".
If it works you'll have to thanks dbott67 who suggested that solution for me.

Thanks for your post, but it returns to me that there is no such file
$ rm ~/.asoundrc
rm: cannot remove `/home/000/.asoundrc': No such file or directory

Still looking for solutions thanks

---

### Post by joslinar on 2007-05-20
Is your username 000?

---

### Post by keka on 2007-05-20
No, I used 000 to hide my real user name, but anyway, for some reason today everything is working fine. I hate this about Linux! thanks for your suggestion, I appreciate it very much!

---

### Post by keka on 2007-05-22
What I noticed is when I uninstall Gstreamer plugins and Restart the computer, everything seems to working fine...exept nothing playing mp3 format. Maybe someone knows a way around this issue....thanks

---

