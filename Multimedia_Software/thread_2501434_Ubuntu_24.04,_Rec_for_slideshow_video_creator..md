---
title: "Ubuntu 24.04, Rec for slideshow video creator."
date: 2024-10-07
forum: Multimedia Software
---

### Post by Advait on 2024-10-07
I'm using Ubuntu 24.04 with Gnome and Wayland. I got some images I want to turn into a slideshow video like an mp4 file. I would like an app where I specify the following:
* location of a directory of images,
* length of time for each image
* fade-out fade-in between images

Then I hit "GO" and it spits out an mp4 file (or some other widely compatible video format). Know any Linux compatible app that can do this?

I don't need to add any audio.

I was thinking of using a Play Store app but I don't like their privacy policies.

I searched Flathub and didn't find anything. Various image viewers but no slideshow video creators that I could see.

---

### Post by Holger_Gehrke on 2024-10-07
ffmpeg can do this. Search for "slideshow video ffmpeg" and you'll find tutorials and examples.

Holger

---

### Post by Advait on 2024-10-11
> **Holger_Gehrke said:**
> ffmpeg can do this. Search for "slideshow video ffmpeg" and you'll find tutorials and examples.

Holger

I'm a tech noob so using ffmpeg looks a little too much learning curve for me. I'll keep searching for a GUI app.

---

### Post by nicolasdentremont on 2024-10-11
A video editing program should be able to do that fairly easily.

---

### Post by bobunderwood99 on 2024-10-11
Check out [FFQueue]("https://ffqueue.bruchhaus.dk/Default.aspx")  

It's available in the App Center 

 or

```
snap install ffqueue
```

---

### Post by vmpx on 2024-11-23
You can try qslideshow incorporated in qdvdauthor (sf.net/p/qdvd) it uses the script dvd-slideshow.

---

### Post by Advait on 2024-11-24
> **bobunderwood99 said:**
> Check out [FFQueue]("https://ffqueue.bruchhaus.dk/Default.aspx")  

It's available in the App Center 

 or

```
snap install ffqueue
```

I'm now exploring this tool.

---

### Post by Advait on 2024-11-24
> **vmpx said:**
> You can try qslideshow incorporated in qdvdauthor (sf.net/p/qdvd) it uses the script dvd-slideshow.

Looks good. I'm now trying it out.

---

