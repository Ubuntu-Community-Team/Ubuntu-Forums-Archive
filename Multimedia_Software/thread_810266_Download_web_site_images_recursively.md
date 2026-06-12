---
title: "Download web site images recursively"
date: 2008-05-28
forum: Multimedia Software
---

### Post by walmartshopper67 on 2008-05-28
There is a website that will most likely disappear from the internet in the next few weeks. I would like to download the pics from the site before it's gone. I can't figure out how to do it recursively

The site is structured like this - there is a main page (index) which links to sub-pages with categories, those sub-pages contain thumbnails which link to the full sized pictures. I've been looking at wget but I can't figure out how to download the images with them being a few links deep in the site. Is there a way to do this, with wget or any other application?

Thanks

---

### Post by kpkeerthi on 2008-05-28
You can use wget to download all image files recursively from a website
```
wget -r --accept gif,jpg,jpeg http://www.website.com
```

There is also a graphical version **gwget** available in the repository

---

