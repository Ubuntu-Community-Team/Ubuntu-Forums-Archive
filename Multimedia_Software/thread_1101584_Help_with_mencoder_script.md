---
title: "Help with mencoder script"
date: 2009-03-20
forum: Multimedia Software
---

### Post by deviant78 on 2009-03-20
Bit of a newbie so not 100% hoe to go about this.

I've seen this command for terminal to convert a wmv to an avi:

mencoder INPUT.wmv -ofps 23.976 -ovc lavc -oac copy -o outfile.avi

Is it possible to make some form of script or something so I can right click a wmv file and click convert?

---

### Post by lovinglinux on 2009-03-20
You can use a Nautilus script.

[This thread]("http://ubuntuforums.org/showthread.php?t=193754") might help you.

Also [this google search]("http://www.google.com.br/search?hl=pt-BR&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=V5P&q=nautilus+script+video+converter+site%3Aubuntuforums.org&btnG=Pesquisar&meta=lr%3Dlang_en|lang_pt")

---

### Post by deviant78 on 2009-03-22
Had some success using WinFF.

If anyone else is interested you can install it by:

echo "deb [http://winff.org/ubuntu](http://winff.org/ubuntu) intrepid universe" | sudo tee /etc/apt/sources.list.d/winff.list

wget --quiet --output-document=- "http://winff.org/ubuntu/AAFE086A.gpg" | sudo apt-key add - && sudo apt-get update

sudo apt-get install avidemux ffmpeg winff

---

