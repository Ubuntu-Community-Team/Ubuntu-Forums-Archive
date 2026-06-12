---
title: "Creative Sound Blaster Live 24-bit getting confused for Creative Labs SB Audigy LS"
date: 2006-01-02
forum: Multimedia &amp; Video
---

### Post by thefrug on 2006-01-02
I just got a creative sound blaster live 24-bit. It is not working correctly, and the only way I can hear anything is through the digital out port.

When I do lspci, my card is listed like this: 
0000:00:0c.0 Multimedia audio controller: Creative Labs SB Audigy LS

Sorry, I realized that they have the same module. This is a useless post.

---

### Post by rossjman1 on 2006-01-14
How did you get the card to work? I've been trying to get sound for months now...

---

### Post by Teroedni on 2006-01-14
rossjman:I would guess newer drivers;) What ubuntu version are you using

The frug:Open terminal
write
```
alsamixer
```

a little program opens
This is Alsamixer.

It is here you are configuring sound volume etc;)
Browse in that program and when you find digital out press m .
This will turn digital off resulting in that analog channel on the souncard get open...and tadaa you got Sound:)

---

