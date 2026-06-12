---
title: "Automate a slideshow"
date: 2010-07-08
forum: Multimedia Software
---

### Post by gobrien002 on 2010-07-08
:popcorn: Hello Everyone, Now this may seem somewhat strange, but I'm trying to find a way to use Ubuntu 10.04 to display a slideshow automatically, as in power on the laptop Ubuntu starts and the slideshow begins, very similar to a photo frame, but this would be on a plasma with no interaction other than turning the computer on.

My question is, would this be possible with 'F-Spot' or is there another app someone could recommend.

Cheers

---

### Post by fourpxdirectory on 2010-07-08
Nice and also Internet Slideshow is a tool that lets you build a list of  website addresses along with their names and browse them consiquently.

---

### Post by aeiah on 2010-07-08
the standard image viwer with ubuntu will probably do this, but if not you could use mirage, which is pretty lightweight

as a startup command, do:
```

mirage -sf /path/to/photo/directory/

```

slideshow settings can be set inside mirage. doesn't look like it can fade between images though. perhaps gthumb or whatever can.

(the -s option flag for mirage is slideshow, the -f is for fullscreen)

---

### Post by nothingspecial on 2010-07-08
You could do it with feh
```

sudo apt-get install feh
```
```

feh -rzF -D 5 /path/to/photos
```I bought a netbook with a broken keyboard and use it in this way as a digital photo frame.

The flags -

r = recursive ie use any image in the specified directory and all directories within it and so on.

z = random

F = full screen

D = delay, the number after it specifies the time in seconds each photo is displayed for, in the example 5 seconds

type man feh to see all the options, it is in my opinion one of the better written man pages.

When you have sorted out the exact options you want to use, add the command to System > preferences > startup applications. Then set ubuntu to log in automatically in System > Administration > Login Screen.

---

