---
title: "Multimedia (Flash) Chrome Beta."
date: 2009-08-09
forum: Multimedia Software
---

### Post by Wiebelhaus on 2009-08-09
*Did not find a how to on the board , So I'll offer one*

Easy flash enabling for Chrome Beta:

Create plugins folder:
```
sudo mkdir /opt/google/chrome/plugins/
```

cd to plugins dir:
```
cd /opt/google/chrome/plugins/
```

Create link from installed flash player to plugins folder:
```
sudo ln -s /usr/lib/flashplugin-installer/libflashplayer.so
```

Add this line to your command section of your shortcut:
```
/opt/google/chrome/google-chrome --enable-plugins %U
```

---

