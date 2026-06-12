---
title: "[SOLVED] RAW conversion in gThumb"
date: 2007-08-03
forum: Multimedia Production
---

### Post by gobbles414 on 2007-08-03
Hi all,

After trying several photo managers in Ubuntu, I have decided that I like gThumb the best for basic photo editing. I shoot pictures in RAW mode with my Olympus E-510 SLR. Olympus' raw format has the ORF extension.

I've come to realize that I will need to convert my RAW images into either PNGs, TGAs or TIFFs before I can edit them in gThumb. **I need advice from people who know more than I do about these formats. Which of them will preserve the most data from the original RAW image?** This is not as big of an issue for me, but can gThumb use the sRGB colorspace? If so, how can I tell it to do so?

---

### Post by MetalMusicAddict on 2007-08-05
> **gobbles414 said:**
> Hi all,

After trying several photo managers in Ubuntu, I have decided that I like gThumb the best for basic photo editing. I shoot pictures in RAW mode with my Olympus E-510 SLR. Olympus' raw format has the ORF extension.

I've come to realize that I will need to convert my RAW images into either PNGs, TGAs or TIFFs before I can edit them in gThumb. **I need advice from people who know more than I do about these formats. Which of them will preserve the most data from the original RAW image?** This is not as big of an issue for me, but can gThumb use the sRGB colorspace? If so, how can I tell it to do so?

Give [Rawstudio]("http://rawstudio.org") a look. It's in the repos.

There's also **gimp-ufraw** and **gimp-dcraw** as plugins to The GIMP. **gimp-ufraw** has been mentioned as a favorite.

---

### Post by gobbles414 on 2007-08-06
Hi MMA,

Thanks for the advice, but I was hoping to do all of my photo editing in a basic photo editor. Plus...

Rawstudio looks like a great conversion program, but not so good of a photo editor (imho). Gimp is too complex for my needs. I want an iPhoto clone like gThumb. Also, the version of dcraw in the repos -- which is used by ufraw as I understand -- is several releases out of date and does not support my camera's RAW files. I had to install a newer version of dcraw manually from source.

So, back to my original question: **which kind of conversion will give me the best results in _gThumb_ (Tiff, TGA, PNG)?**

Thanks again!

---

### Post by gobbles414 on 2007-08-08
bump :-(

---

### Post by gobbles414 on 2007-08-12
Hi all,

Well still no new responses. All three formats showed the same resolution and bit-depth in GIMP. So I have chosen PNG as my export format. If any of you disagree with that choice, please post a reply with some advice on the best format. Thanks.

---

### Post by salsafyren on 2007-08-29
Hi,

I think the best option is to use dcraw to convert the ORF file to TIFF. That's what's recommended by Olympus (they said that in the demo DVD).

Also, PNG does not support CMYK (see wikipedia), so TIFF is a better choice.

---

### Post by gobbles414 on 2007-09-18
salsafyren,

Thanks for your post... I respect your opinion. My camera and printer both use RGB-based color spaces. Additionally, converting to PNG in gThumb is an "idiot proof" situation, whereas there are many options available when converting to TIFF. I think that I'll keep using PNG for now.

---

