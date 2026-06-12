---
title: "Windows Movie Maker alternative in Ubuntu?"
date: 2013-02-28
forum: Multimedia Software
---

### Post by ppdjoy on 2013-02-28
Hi

I'm kinda new in Ubuntu. I use it through Wubi (inside Windows7). I run Ubuntu 12.04 LTS. 

I was looking for an alternative to Windows Movie Maker for Ubuntu. I looked online & found that Cinelerra, kdenLive, Kino performs similarly. I wasn't sure which one would be light, fast. If it's portable then it's even better. 

Thanks.

---

### Post by uc50_ic4more on 2013-02-28
Cinelerra is advanced and feature-rich; not to mention horrendously ugly. Kdenlive is a KDE-based application, and I have heard it is a little crashy. I know nothing of Kino.

 I think your best bets at this point are Openshot and PiTiVi. Both seem to be actively developed and maintained, both seem quite capable in terms of features and stability and both are readily available inthe Software Centre

---

### Post by sudodus on 2013-02-28
> **uc50_ic4more said:**
> Cinelerra is advanced and feature-rich; not to mention horrendously ugly. Kdenlive is a KDE-based application, and I have heard it is a little crashy. I know nothing of Kino. I think your best bets at this point are Openshot and PiTiVi. Both seem to be actively developed and maintained, both seem quite capable in terms of features and stability and both are readily available inthe Software Centre+1 for Openshot

---

### Post by bro on 2013-02-28
I would stay clear of cinelerra, it is not very intuitive. I've had mixed results with all others but they all grew up quite a bit last years. Openshot, pitivi, kd kdenlive just install and try them. They are mostly straight forward.

---

### Post by slickymaster on 2013-02-28
Besides OpenShot, I would also mention Kino and LiVES.

---

### Post by Adam_GUI on 2013-02-28
I had really good luck with pitivi until 12.04.  Something to do with them switching to gstreamer.
I haven't gotten it to work well since as it started to either crash often or render time into infinity.

I have had good luck using Lives.  Works well, looks decent.

---

### Post by ppdjoy on 2013-03-01
Thanks everyone.

Does Openshot come in portable format? If so, can you give me the link for the portable version?

Thanks.

---

### Post by sleash78 on 2013-03-01
ffmpeg

---

### Post by sudodus on 2013-03-02
> **ppdjoy said:**
> Thanks everyone.

Does Openshot come in portable format? If so, can you give me the link for the portable version?

Thanks.
What do you mean by portable?

There are two alternatives for Ubuntu:

- Install a versionfrom the repositories that is tested by Canonical to work with Ubuntu. It works, but is not the newest version.

```
sudo apt-get install openshot
```

- Download an iso-file for a live DVD with the newest stable version from Openshot's web site. It is very likely to work and it has all the new features.

- Download a deb-file with the newest  stable version from Openshot's web site (or linked from it). It is very  likely to work and it has all the new features, but it may not be updated to the newest Ubuntu versions (above 9.10).

[[COLOR=#ff0000]http://www.openshot.org/download/[/COLOR]]("http://www.openshot.org/download/")

---

### Post by ppdjoy on 2013-03-02
I meant portable Openshot similar to apps in [portableapps]("http://portableapps.com/").

---

### Post by uc50_ic4more on 2013-03-02
> **ppdjoy said:**
> I meant portable Openshot similar to apps in [portableapps]("http://portableapps.com/").

I have never seen any Linux portable apps at all. There are two immediate issues I see with even trying that:

1) Applications like Openshot use so very many system libraries that bundling them all together may be a tumultuous affair. We're talking about packing a boatload of GTK libraries (I know, I know, this is common for GTK windows portable apps like Pidgin, GIMP, etc.) plus the codecs. I suppose anyone could check all of the dependencies and give it a shot. Me? I'd rather just install it. :^)

2) Anything on a USB drive will likely need to be made executable manually, wouldn't it?

When using a portable app, I suppose the main advantage is that you can use it on varying systems. This usually means that your portable apps ought to be Windows applications. If you are using it on known systems that have Linux installed, you may just have to install it.

Of course, you could install Openshot and then make a bootable USB drive out of your whole OS, and have a portable Ubuntu with Openshot installed already.

---

### Post by QIII on 2013-03-02
*Moved to **Multimedia & Video***

---

### Post by sudodus on 2013-03-02
> **ppdjoy said:**
> I meant portable Openshot similar to apps in [portableapps]("http://portableapps.com/").

I think the closest you can get is to download an iso-file for a live DVD with the newest stable version  from Openshot's web site. It is very likely to work and it has all the  new features. If you make a live USB 3 pendrive from that iso file, it will be pretty portable.

***Unetbootin*** is a good tool to make a live USB drive from an iso file.

---

### Post by ppdjoy on 2013-03-08
Thanks sudodus for the suggestion. I'll definitely try that.

Thanks everyone for the help!

---

