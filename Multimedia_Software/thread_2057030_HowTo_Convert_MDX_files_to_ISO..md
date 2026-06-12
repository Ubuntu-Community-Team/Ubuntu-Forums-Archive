---
title: "HowTo: Convert MDX files to ISO."
date: 2012-09-12
forum: Multimedia Software
---

### Post by e-San on 2012-09-12
Hi!

I've been looking for this solution a while and not for the first time.
Most accurate and only working solution was found on some RUS page and, since many people can not read and understand it, i would like to make this small note for You:

Original site: [http://liberatum.ru/forum/kak-smontirovat-obraz-mdx-v-linux](http://liberatum.ru/forum/kak-smontirovat-obraz-mdx-v-linux)
NOTE: It is not straight translation!

As far as i know MDX format is composed (in straight words) of disk image and CUE file (let's do not go into technical). It is far more complex than iso, so it can be easily to converted.

Since we can not mount it by simple mount command, we have to convert it with some tool. In our example we use  iat (Iso9660 Analyzer Tool). Luckily it is in repos:

```
sudo apt-get install iat
```

To convert image:

```
iat image.mdx image.iso
```

And now we can mount it with 'mount -oloop'.

Hope someone will find it useful. 

Regards!

---

### Post by v3ga on 2012-12-03
It did convert to ISO file which could be mounted too. But after mounting they show up empty in the file manager(even though they aren't)

---

