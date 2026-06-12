---
title: "ATI Radeon X1300 'fglrxinfo' Help"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by corevette on 2007-01-15
When I do a "fglrxinfo" command into the terminal, this is my output: 
```
corevette@corevette-desktop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

I followed the steps here: 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Automatic and Manual and same results.  I tried "fgl_glxgears" into the terminal and got this:
```
corevette@corevette-desktop:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  30
  Current serial number in output stream:  30
```
any help at all?

---

### Post by corevette on 2007-01-15
here is my xorg.conf file: [http://paste.ubuntu-nl.org/1763/](http://paste.ubuntu-nl.org/1763/)

and my output to lspci | grep -i display
02:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)

---

### Post by arrenlex on 2007-01-15
[http://paste.ubuntu-nl.org/1766/plain/](http://paste.ubuntu-nl.org/1766/plain/)

Try using that as your /etc/X11/xorg.conf. Remember to back up your old one. I don't think it will work, but it won't do any harm. If it doesn't work, please paste a new /var/log/Xorg.0.log

---

