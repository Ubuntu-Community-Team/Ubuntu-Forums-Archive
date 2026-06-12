---
title: "How to download &amp; convert Google/YouTube .flv files"
date: 2008-06-27
forum: Multimedia Software
---

### Post by Dino05 on 2008-06-27
Is there are program in Ubuntu that would allow me to download Google and YouTube videos and my second Q? is, is there a way to convert .flv to DVD on Ubuntu.

---

### Post by Het Irv on 2008-06-27
I think there are some Firefox add-ons that can help with the first problem, but I cannot remember the names.   Not sure about the second one, try searching for ".flv converter" in Add/Remove (you will have better results if you have the medibuntu Repo installed).

---

### Post by prshah on 2008-06-27
> **Dino05 said:**
> Is there are program in Ubuntu that would allow me to download Google and YouTube videos and my second Q? is, is there a way to convert .flv to DVD on Ubuntu.

Try the download helper addon to firefox for saving youtube video files. (and others)

---

### Post by Dino05 on 2008-06-27
Forgive me for asking a question - but how do I install the medibuntu repo

---

### Post by walkerk on 2008-06-27
> **Dino05 said:**
> Forgive me for asking a question - but how do I install the medibuntu repo

```
echo 'deb http://packages.medibuntu.org/ hardy free non-free' | sudo tee -a /etc/apt/sources.list
```
```
sudo apt-get update
```

---

### Post by SilverWolf240 on 2008-07-12
The Firefox add-on DownloadHelper will allow you to download Youtube videos. You can get it here: [https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

It can also help you convert them to other formats by installing ffmpeg.

```
sudo apt-get install ffmep
```

---

### Post by armageddon08 on 2008-07-13
There's no point loading your firefox with hundreds of add-ons. To download vids from youtube: wait till the vid streams completely; then(without closing the youtube page) go to:
File system-->tmp. There you should find a file starting with Flash....Just copy that file and paste it where you want to save your vid to.


Cheers!

---

