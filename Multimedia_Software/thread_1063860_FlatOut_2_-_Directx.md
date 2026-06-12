---
title: "FlatOut 2 - Directx"
date: 2009-02-08
forum: Multimedia Software
---

### Post by Deldo on 2009-02-08
Hi

I would like to play FlatOut 2 on Ubuntu (Gnome).
But every time I start the game, I get this message:

"FlatOut requires DirectX 9.0c or newer. Please install the latest DirectX version and restart the game"

I can choose to Ignore this og press Exit.
I look around the internet and found out that DirectX can not be installed with Wine, but instead I need OpenGL. It seems to be installed on my computer, but it still doesn't work.

Can anyone help me?

Rune

---

### Post by Deldo on 2009-02-10
Is it correct that FlatOut 2 can't be played in Wine?

---

### Post by ad_267 on 2009-02-10
The Wine AppDB is the place to look to see if an application will work with Wine. See [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9406](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9406). It says there, "need a crack (Euro Version with StarForce), and a native d3dx9_30 dll".

---

### Post by Deldo on 2009-02-10
Thank you.

Well, I'm not familiar with these informations, so shall I download a crack and the dll-file?

---

### Post by ad_267 on 2009-02-11
I'm not sure what the crack is for. It's probably not something that's legal but there's a link there to find it in google.

If you have a Windows installation you can look for the dll file in C:/windows/system32 and copy it into your wine directory in ~/.wine/drive_c/windows/system32

If you can't find it or don't have a windows installation you may be able to search for that file and find it on the internet

---

### Post by Deldo on 2009-02-11
The patch seems easy to "install" and i have the dll-file, so I will copy it into ~/.wine/drive_c/windows/system32, unzip FlatOut 2, patch it and try to play.

---

### Post by avaxdownload on 2009-02-11
> **Deldo said:**
> The patch seems easy to "install" and i have the dll-file, so I will copy it into ~/.wine/drive_c/windows/system32, unzip FlatOut 2, patch it and try to play.

This helps!

---

### Post by Deldo on 2009-02-14
It does not work. I can run the game but with a black screen. The sound and menu options works like it should, but I can't see anything.

---

