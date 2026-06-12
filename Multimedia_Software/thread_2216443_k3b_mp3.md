---
title: "k3b mp3"
date: 2014-04-12
forum: Multimedia Software
---

### Post by AbdRahim on 2014-04-12
k3b cannot burn mp3 files, to audio. k3b extracodecs are installed. Even reinstalled k3b and extra codecs. Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project. Ubuntu 12.04

---

### Post by SeijiSensei on 2014-04-12
Usually this problem is solved by installing **kubuntu-restricted-extras**.  Is that what you mean about codecs being installed?

---

### Post by Yellow Pasque on 2014-04-14
>  Is that what you mean about codecs being installed? 
Refers to libk3b6-extracodecs package, which is needed for mp3.

If that is installed, then I would try to manually install lame package. You could be hitting this bug: [https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/992844](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/992844)

---

### Post by AbdRahim on 2014-06-22
Refers to libk3b6-extracodecs package, which is needed for mp3.  Installed as well as lame.

---

### Post by ron998 on 2014-06-22
...

---

