---
title: "Pytube isn't converting anything!"
date: 2008-08-18
forum: Multimedia Software
---

### Post by Adaemon on 2008-08-18
I'm using Ubuntu Intrepid and I want to convert some youtube (FLV) files for my new phone (mp4).  Unfortunately when I set it to convert it says done before it does anything and then when I look for the new file, it doesn't exist.  If I try to convert FLV to mpg it does actually make a file, but the file contains no data.  Very odd...

I've tried using WinFF and that gives the same result.

What am I doing wrong?

---

### Post by billgoldberg on 2008-08-18
> **Adaemon said:**
> I'm using Ubuntu Intrepid and I want to convert some youtube (FLV) files for my new phone (mp4).  Unfortunately when I set it to convert it says done before it does anything and then when I look for the new file, it doesn't exist.  If I try to convert FLV to mpg it does actually make a file, but the file contains no data.  Very odd...

I've tried using WinFF and that gives the same result.

What am I doing wrong?

Uninstall pytube and winff.

```
sudo apt-get autoremove pytube winff --purge
```

Uninstall ffmpeg.

```
sudo apt-get autoremove ffmpeg --purge
```

Add the medibuntu repo 

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Install ffmeg

```
sudo apt-get install ffmpeg
```

Then install Winff.

Install from .deb file.

Now it should be fine.

--

I also have a problem when downloading a video and converting it to .mp3 using pytube. The first time I'm doing it it says done after 1 second, then I do the same thing again and it starts downloading.

---

