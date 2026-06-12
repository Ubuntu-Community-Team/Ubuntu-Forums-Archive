---
title: "Turtlebeach USB micro amigo sound card"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by v604mustangjoe on 2007-07-26
so i have a dell 350 mhz 512mb ram 10 gig old brick with ubuntu fiesty on it. I am very novice at using ubuntu and have managed to get to know my way a little bit.

I have one of those USB memory stick sized TBS amigo usb micro sound cards with the fiberoptic output on it going into my 5.1 home theatre. 
[U][B]
Well here is the problem: [/B][/U] I can get sound on GAIM (im noises and such), i can get sound in the ubuntu african tradition example video, i CANNOT get sound in the sound preference tool where you play the .wav files, i cannot get sound on start up or at log off, i cannot get sound in mp3 files when i play them with various players.

Can someone please help, thanks :-)

---

### Post by LDRoamer on 2007-07-26
I used the fix found in this post to get my turtle beach mirco card working:

[http://ubuntuforums.org/showthread.php?t=490986&highlight=Logitech+USB+headset](http://ubuntuforums.org/showthread.php?t=490986&highlight=Logitech+USB+headset)

Basically what you have to do is run this command from a termnal.

```
asoundconf list
```

That should tell you the name of the sound card that was installed. In my case it said my sound card was called "default". This confused me it at first but the term "default" is the actual name of the card just as "sound blaster" might the name of the card.

IN order to get my card working I then ran

```
asoundconf set-default-card default 
```

You need to substitute the name of your card for "default".  If your card is, for example, called Audio then you would run

```
asoundconf set-default-card Audio 
```

Since yours is a turtle beach card like mine it might also be called "default" This worked for me. I hope it works for you.

---

### Post by LDRoamer on 2007-07-26
One more thing I forgot to mention. You also have to go into your sound preferences and set them all manually to USB Audio. Once you do this you will have some sound but things ike system sounds won't be working until you set the card to be the default card as I described in my earlier post.

---

### Post by v604mustangjoe on 2007-07-27
wow that was easy once  you know what to do! thanks a lot, where can i get a list of all the differnt terminal commands, i am really starting to like this terminal part about linux, way better than digging through folders finding stuff. 

All things are good now, now i just gotta figure out how to get a realtek wifi driver for my desktop and a HP broadcomm laptop driver running for my wifi on that.

---

