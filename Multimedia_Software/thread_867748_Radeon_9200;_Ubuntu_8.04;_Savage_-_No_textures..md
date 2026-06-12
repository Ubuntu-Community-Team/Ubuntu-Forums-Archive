---
title: "Radeon 9200; Ubuntu 8.04; Savage - No textures."
date: 2008-07-23
forum: Multimedia Software
---

### Post by Husio on 2008-07-23
Hello,
I've made new installation of ubuntu (update to 8.04), and now, I don't have half of the textures in Savage game. Here's how it looks like:
[[img]http://xs329.xs.to/xs329/08303/savage_no_textures727.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs329&d=08303&f=savage_no_textures727.png)
```

$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)

$ uname -a
Linux tomek-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

$ glxinfo | grep direct 
direct rendering: Yes

```

What could be wrong?

---

