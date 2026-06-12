---
title: "3 small problems"
date: 2008-04-26
forum: Multimedia Software
---

### Post by Snyper64 on 2008-04-26
In Totem I cannot get Dolby Digital or DTS playback to work. I have gotten it to work in Mplayer but I do not like Mplayer for playing DVDs. Also I have the sound coming out of my laptop speakers and not my external sound card since removing GStreamer backend(It was giving me problems with DVD Menus not working but the sound was coming out of my external sound card but with no DD/DTS). Is there any way to make my external sound card the default sound card in Totem(I have the hardware number and subset for the optical out on it).

Any help would be greatly appreciated.
Thanks
Snyper64

---

### Post by Snyper64 on 2008-04-26
bump

---

### Post by Snyper64 on 2008-04-27
bump

---

### Post by Snyper64 on 2008-04-28
bump

---

### Post by Snyper64 on 2008-05-02
bump

---

### Post by coolen on 2008-05-02
Are you using Hardy? If so, it should be possible with PulseAudio. I don't know how exactly, but their FAQs would undoubtedly be of use.

---

### Post by Snyper64 on 2008-05-02
Yes, I am using 8.04 Hardy. How would PulseAudio help me get this working correctly? Do you have a link to the FAQs page?

---

### Post by coolen on 2008-05-02
[Here]("http://www.pulseaudio.org/wiki/FAQ") is a link to the FAQ page.

PulseAudio lets you do things like change an application's volume (and I read somewhere about muting music and video when you get a call on Skype), so I'm sure you could set it to route an application to another sound card.

---

### Post by Snyper64 on 2008-05-02
I'll give it a try when I get home from work and let you know what happened.

---

### Post by Snyper64 on 2008-05-04
Well I gave it a try and it didn't help, in fact it screwed up the audio in Mplayer and I had to remove it completely just to get Mplayer to work right again. Does anybody know if Totem has a configuration file I can edit to set up the default sound card?

---

### Post by coolen on 2008-05-04
I think MPlayer has had problems with PA in the past. The solution was merged upstream a while back, but I'm not sure if it's made it to the repos. The previous solution was to build MPlayer from source.

---

### Post by Snyper64 on 2008-05-04
I never had a problem with Mplayer since Gutsy came out(I had alot of problems with previous releases) and since you get more options with it on how you want it set up. If Totem had more options in audio and video especially which audio device to use as a lot of people have more than one sound card on their pc I wouldn't be having this problem now. Personally I don't think Totem has a valid excuse not to have these options implemented already.

---

### Post by Snyper64 on 2008-05-08
bump

---

### Post by Snyper64 on 2008-05-30
bump

---

