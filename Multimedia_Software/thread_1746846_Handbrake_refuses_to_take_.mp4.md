---
title: "Handbrake refuses to take .mp4"
date: 2011-05-02
forum: Multimedia Software
---

### Post by Ghost_Mazal on 2011-05-02
Lo all , I have a problem with Handbrake. I convert to mp4 and previously it always took the .mp4 file naming.

Now on a new install it refuses to take .mp4
It keep going to .m4v
I made all my settings the same as before , but it keeps doing that.

How can I get it to accept .mp4 on the filename ?

thanx

---

### Post by lovinglinux on 2011-05-02
As far as I know, you can't. However, it doesn't really matter because most players can handle m4v as well. It is similar to mp4.
> 
[http://en.wikipedia.org/wiki/M4v]("http://en.wikipedia.org/wiki/M4v")
M4V is a file container format used by Apple's iTunes application. The M4V file format is a video file format developed by Apple and is very close to MP4 format. The differences are the optional Apple's DRM copyright protection, and the treatment of AC3 (Dolby Digital) audio which is not standardized for MP4 container.

Additionally, the file extension doesn't really matter in Linux. You can save the file without the extension and it will still play.

BTW, I have been using handbreak with that format and is working well.

---

### Post by JohnAStebbins on 2011-05-02
> **lovinglinux said:**
> As far as I know, you can't. However, it doesn't really matter because most players can handle m4v as well. It is similar to mp4.


Additionally, the file extension doesn't really matter in Linux. You can save the file without the extension and it will still play.

BTW, I have been using handbreak with that format and is working well.

There is an option in HandBrake's preferences to select which extension it will use for mp4 files.

---

### Post by lovinglinux on 2011-05-02
> **JohnAStebbins said:**
> There is an option in HandBrake's preferences to select which extension it will use for mp4 files.

Indeed. In the general tab, untick the option to use ipod/itunes friendly extension for mp4.

Thanks.

---

### Post by Ghost_Mazal on 2011-05-03
> **lovinglinux said:**
> Indeed. In the general tab, untick the option to use ipod/itunes friendly extension for mp4.

Thanks.

It is unticked , but still refuses to take .mp4

---

### Post by JohnAStebbins on 2011-05-03
> **Ghost_Mazal said:**
> It is unticked , but still refuses to take .mp4

Ah, I forgot something.  The 0.9.5 release will still use the m4v extension if your output will contain ac3 audio, subtitles, or chapter markers.  The reason for this is that QuickTime will refuse to recognize these features if the extension isn't m4v.  But in the latest code, I have removed this auto-detection feature.  It causes too many problems such as yours.  The latest is available in the nightly builds PPA.
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by lovinglinux on 2011-05-03
> **JohnAStebbins said:**
> Ah, I forgot something.  The 0.9.5 release will still use the m4v extension if your output will contain ac3 audio, subtitles, or chapter markers.  The reason for this is that QuickTime will refuse to recognize these features if the extension isn't m4v.  But in the latest code, I have removed this auto-detection feature.  It causes too many problems such as yours.  The latest is available in the nightly builds PPA.
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

I didn't know you are one of the developers. Just wanted to say thanks for such a great software.

---

### Post by Ghost_Mazal on 2011-05-04
Indeed , great converter.

---

