---
title: "Wich is the best FREE ipod vido converter"
date: 2009-08-16
forum: Multimedia Software
---

### Post by hempa on 2009-08-16
Hi im looking for a simple free program that can convert lots of formats to mp4. so i can put them on my ipod nano.i  Know i can find a bunch of programs just by googling a bit but i dont know wich is the best one so maybe someone has used a good program and can reccomend it Thanks.

---

### Post by SuperSonic4 on 2009-08-16
Command line ffmpeg is the most flexible and it's both free as in speech and as in beer. It's well worth reading it's man page IMO, it should also be in the repo too

```
sudo apt-get install ffmpeg
```

For an iPod conversion it would be something like (assuming you're in the right directory, if not use **cd /path/to/dir** to get there)

```
ffmepg -i [COLOR="Red"]input.flv[/COLOR] -b 300k -s 320x240 -vcodec libx264 -acodec libfaac -ac 2 -ab 128k output.mp4
```

note: input does not have to be flv - pretty much all filetypes are supported

Avidemux should work too if you prefer a GUI

---

### Post by hempa on 2009-08-16
Thanks alot man i will try both of those programs and see wht works best for me.i usually prefer gui cause i dont use the terminal so often but its always good to learn so i think i willl try ffmpeg first.

---

### Post by kostkon on 2009-08-16
You could also try [*WinFF*]("http://winff.org") which is a GUI frontend for FFMpeg or [*Arista*]("http://programmer-art.org/projects/arista-transcoder"). They both offer a repository/PPA.

---

