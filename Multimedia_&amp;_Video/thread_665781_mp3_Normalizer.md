---
title: "mp3 Normalizer"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by Andrew07 on 2008-01-12
I've been looking for a mp3 normalizer that works with Ubuntu forever, but I still haven't managed to find one. I'm hoping someone here has wind of one that I've just missed. An example of a windows based one would be mp3gain if that helps any.

---

### Post by wolfen69 on 2008-01-12
for me, mp3gain is in synaptic. if it's not there for you, try adding the medibuntu repositories. [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by polmir on 2008-01-12
```
sudo apt-get install normalize-audio
```

---

### Post by sub2007 on 2008-01-12
> **wolfen69 said:**
> for me, mp3gain is in synaptic. if it's not there for you, try adding the medibuntu repositories. [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Yup MP3Gain is in repositories. In Linux it is CLI only, it has no GUI. 

Install it, then open a terminal and enter **mp3gain -?**. That'll give you a list of all the parameters that you can use. I personally used -r (apply track gain automatically) but am really not an expert in any way on using MP3gain in Linux.

Then cd to the required directory and enter:

mp3gain -(whatever options you chose) *.mp3

Then you should see the progress of the normalization.

If you like the GUI, as far as I know the Windows version of MP3Gain works fine under Wine so if you would rather use a GUI and don't mind using Wine then you might want to use that.

Didn't know about normalize-audio, I just looked at it. It's CLI only again but has far fewer options (although the options are more varied and well explained in the --help) and supports OGG as well - looks good and I might use it in the future.

---

