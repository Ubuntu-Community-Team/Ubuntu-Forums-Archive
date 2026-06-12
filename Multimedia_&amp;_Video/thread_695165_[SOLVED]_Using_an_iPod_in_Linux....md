---
title: "[SOLVED] Using an iPod in Linux..."
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by chazdraves on 2008-02-12
Allrighty. So, I'm familiar with the fact that iPods work in Linux, but I'm a bit cautious as a Linux newb. I just recently sold off my Zune and intend to buy an iPod tomorrow. Before I do, however, I want to know what kind of issues I should expect... I see there's a guide recommending you use RhythmBox for playing/viewing files on your iPod, but supposedly RhythmBox can't handle transferring files to your iPod? Because of this, the guide recommends gtkpod (which I did manage to find in Synaptic). Basically, I want to know if it's possible for a Linux noob to get this working (without too much time invested) and what features I should expect to lose?

Also, I'm wondering about cover art and file formats. As I understand, the iPod doesn't accept FLAC lossless? I'm a bit of an audiophile, so lossless is important to me. How do I make that happen?

Thanks for your time and help guys, I realize I asked a number of questions there.

Regards,
- Chaz

---

### Post by Existentialist on 2008-02-12
Overall you should not experience many problems.  If you prefer to keep your music in FLAC I would look in to something like Rockbox to replace the firmware on your ipod with something that has the codecs for FLAC.  Here is their website:

[http://www.rockbox.org/](http://www.rockbox.org/)

---

### Post by chazdraves on 2008-02-12
Well, I don't want to bugger up the firmware on the iPod, I would just like some sort of lossless option... Is that possible?

_ Chaz

---

### Post by cozmicharlie on 2008-02-12
I use gtkpod and it works fine.  My set up for my Ipod is as follows:

gtkpod to manage the ipod (tranfer files etc)
Exfalso for tagging (because it supports m4a - needed to tag Apple Lossless)
PACPL for decoding/encloding (it will decode almost all formats including Apple Lossless).  SoundKonverter also works.

With Rockbox you can keep your ipod firmware intact (kind of like a dual boot) or you can uninstall the native Apple ipod firmware then if you want to go back you have to reinstall it.  But, if you don't want to do that then the only option is Apple Lossless.  Ipods do not support flac (and most likely never will).  See here for an explanation [http://en.wikipedia.org/wiki/Apple_Lossless](http://en.wikipedia.org/wiki/Apple_Lossless).  I use the packages above because they all support Apple Lossless.  

If you want flac then Rockbox is the only option.

---

### Post by chazdraves on 2008-02-12
So, that reminds me... Will soundkonverter convert to Apple Lossless? And on that note, can I delete the A Lossless files from my hard drive after they're converted?

Thanks, guys, I'm starting to understand.
- Chaz

---

### Post by cozmicharlie on 2008-02-12
Yes - Soundconverter will convert flac to Apple Lossless.  Yes you can delete the files on the HD (though you may want to back them up somewhere just in case the ipod crashes) after conversion.  Make sure you have all the proper codecs installed.  You need to add the Medibuntu repository and install the Ubuntu Restricted Extras.  This should install the codecs needed.  This will help [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

