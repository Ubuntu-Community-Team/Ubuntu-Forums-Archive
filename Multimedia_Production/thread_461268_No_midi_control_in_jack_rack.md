---
title: "No midi control in jack rack"
date: 2007-06-01
forum: Multimedia Production
---

### Post by pekko on 2007-06-01
AFAIK jack rack should support controlling effect parameters with midi. However, I can't find jack rack in jack midi connections page, nor can I assign midi controls to parameters with right-click. I have installed jack rack as a part of ubuntustudio-audio meta package. Should I compile jack rack from source to get midi support working?

BR Pekko

---

### Post by pekko on 2007-06-04
I compiled jack-rack from source and it did the trick. Eventually I ended up using alsa modular synth as an effects box for more flexibility in routing and midi bindings.

---

### Post by coder_ on 2007-06-04
Sweet!  I knew that had to be possible!

---

