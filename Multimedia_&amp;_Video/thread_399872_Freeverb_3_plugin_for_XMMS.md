---
title: "Freeverb 3 plugin for XMMS"
date: 2007-04-02
forum: Multimedia &amp; Video
---

### Post by learning curve on 2007-04-02
Has anyone ever tried to install the Freeverb 3-1.6.4.tar.gz plugin for XMMS?  If so please help.  I have no clue how to do it.  thanks in advance for your time.
Learning Curve

---

### Post by aurelix on 2007-04-23
```

# unpack
tar xzf freeverb3-1.4.6.tar.gz
cd freeverb3-1.3.6
# get build dependencies
sudo apt-get install fftw3-dev xmms-dev libsamplerate0-dev libsndfile1-dev checkinstall
# compile
./configure --enable-xmms --enable-sse --enable-3dnow
make
#install
sudo checkinstall
# answer "n" to the docs question
# enter any description
# let it install
#

```

annotation: for me checkinstall complained about replacing /usr/bin/ld, I do not know why. if it doesn't work, use
```

sudo make install

```
instead, which works anyway. drawback is that you cannot remove it with 'dpkg -r freeverb3' in this case.

hth,
aurelix

// edit: if you never compiled anything before, you probably need to install the package build-essential beforehands:
sudo apt-get install build-essential

---

