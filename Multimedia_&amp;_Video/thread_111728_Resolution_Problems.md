---
title: "Resolution Problems"
date: 2006-01-02
forum: Multimedia &amp; Video
---

### Post by Dath on 2006-01-02
I just installed Ubuntu, and can't seem to get my resolution higher than 1024*768. During the installation, I couldn't figure out how to select the higher ones, and now I think I'm stuck. Does anyone know how to increase it afterwards?

---

### Post by markuman on 2006-01-03
just edit your xorg.conf

```
sudo nano /etc/X11/xorg.conf
```

instead of nano use a editor you like.

add your resolution under << Section "Screen" >>

```

...
SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
...

```

now restart your mashine or jsut The xserver.

---

### Post by mesocool on 2006-01-03
[QUOTE=markuman]just edit your xorg.conf

```
sudo nano /etc/X11/xorg.conf
```

instead of nano use a editor you like.

add your resolution under << Section "Screen" >>

```

...
SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
...

```


now restart your mashine or jsut The xserver.[/QUOTE]

I do have these setups, but i still cannot get any one above 1024 X 768 from "Screen Resolution"..

---

