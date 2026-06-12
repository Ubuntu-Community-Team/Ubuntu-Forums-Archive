---
title: "h.264 decoder"
date: 2008-09-03
forum: Multimedia Software
---

### Post by cnymike on 2008-09-03
I visited a website with quicktime content and that content did not play. INstead I was informed that I did not have the following...

MPEG-4 AAC decoder
H.264 decoder

I've not had any luck finding the h.264 decoder for xubuntu. Any solution?

---

### Post by aeiah on 2008-09-04
the x264 decoder is an opensource version of it that will work, providing there is no drm. of course, the site may be looking specifically for h.264 but you should be able to somehow grab the video and still play it with x264.

---

### Post by hugmenot on 2008-09-04
Install gstreamer0.10-plugins-bad-multiverse and gstreamer0.10-plugins-bad

---

### Post by cnymike on 2008-09-04
hugmenot, that was the solution I was looking for and it works like a champ. Thanks!

---

### Post by ktat on 2009-06-17
> **hugmenot said:**
> Install gstreamer0.10-plugins-bad-multiverse and gstreamer0.10-plugins-bad

Works great for me too!
For others interested - I'm unsing Ubuntu - Jaunty Jackal.

To install follow path:
System --> Administration --> Synaptic Package Manager enter the name into the search field and then mark for installation and apply.

---

### Post by sebastian.gasparetti on 2009-08-19
> **hugmenot said:**
> Install gstreamer0.10-plugins-bad-multiverse and gstreamer0.10-plugins-bad

Awesome!, works perfectly, many thanks.

---

