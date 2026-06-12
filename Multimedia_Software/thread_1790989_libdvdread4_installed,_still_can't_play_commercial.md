---
title: "libdvdread4 installed, still can't play commercial DVDs"
date: 2011-06-25
forum: Multimedia Software
---

### Post by Maximus559 on 2011-06-25
Like the title says... libdvdread4 is installed, and I'm still getting a "could not read from resource" error in Movie Player. The back story:

When I originally installed libdvdread4, I used it to to play DVDs using an external DVD drive. This worked perfectly. Today I installed an internal DVD-RW drive. This does not work. It does mount DVDs, and I can view the DVDs' contents using the desktop icon, but neither Totem nor VLC are able to play commercial DVDs. Totem gives the good old "could not read from resource" error, and VLC just doesn't do anything. Everything is behaving as if I never installed libdvdread4.

At first I thought the DVD-RW drive might not have a region setting yet, but regionset reports that it's set to region 1 (USA), as it should be. Any ideas? I'm using Ubuntu 10.04, by the way.

---

### Post by jramshu on 2011-06-25
Did you run this command?

```

sudo /usr/share/doc/libdvdread4/install-css.sh

```

---

### Post by Maximus559 on 2011-06-26
Works perfectly now - thank you. Strange that I never needed to run that command before...

---

