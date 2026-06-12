---
title: "Need to record tv from internet."
date: 2009-10-28
forum: Multimedia Software
---

### Post by Dundurs on 2009-10-28
Hi everybody, I am newbie here and this is my 1st post. I need a little help. I have an internet TV. And I can watch it using VLC, but i need to record some tv channels at certain time.  For example there is one tv channel, they broadcast my favourite TV show at 12 at clock and i need to start recording it at 12, but if I am not at home? I need to set up that recording at morning. But i dont see some kind of that option in VLC. Maybe there is some other programm, which can do that?

---

### Post by mikewhatever on 2009-10-28
I think you are talking about MythTV like functionality. Look at Mythbuntu, I suppose.

---

### Post by Marco_A on 2009-11-09
> **Dundurs said:**
> Hi everybody, I am newbie here and this is my 1st post. I need a little help. I have an internet TV. And I can watch it using VLC, but i need to record some tv channels at certain time. For example there is one tv channel, they broadcast my favourite TV show at 12 at clock and i need to start recording it at 12, but if I am not at home? I need to set up that recording at morning. But i dont see some kind of that option in VLC. Maybe there is some other programm, which can do that?

For cable (analog) TV I used xdtv (installing it from debian-multimedia, as ubuntu does not give it any more). It give some scheduling features using cron.

I think you could use [Gnome-schedule]("http://gnome-schedule.sourceforge.net/") (to be installed from Synaptic) to run VLC using the command line, but you have to know the sintax used by VLC to watch and record the channel. I don't know VLC very well, but I think that you can copy/paste the correct options from the dialog window where you set up your recording options (something like:
```
vlc http://www.youtube.com/get_video?video_id=KaG0_x6Cnf8&t=vjVQa1PpcFMlYqwkEum8Htcx0Z8Pq_YHKfqY74z35lk= :sout=#transcode{vcodec=mp4v,vb=800,scale=1,acodec=mp4a,ab=128,channels=2}:duplicate{dst=display,dst=std{access=file,mux=mp4,dst=video.avi}}
```

---

