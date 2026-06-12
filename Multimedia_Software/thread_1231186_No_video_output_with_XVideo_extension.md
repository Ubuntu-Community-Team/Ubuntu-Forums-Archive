---
title: "No video output with XVideo extension"
date: 2009-08-04
forum: Multimedia Software
---

### Post by dmakreshanski on 2009-08-04
Hi,

Recently skype crashed for me and afterwards I couldn't get video from XV driver to work. (Which means no skype video for me now :( ). What i get is a transparent block in the place where the video should be. (or in the case of skype - just a white block)

  **Edit:** Skype wasn't the reason, it was cairo-dock with opengl

Anyways, after doing some testing I've realized that it doesn't work when the video is embedded.

For example in VLC 1.0.0 (with the output set to XVideo) the video works if the option 'Embed video in interface' is unchecked. Then the video is normally shown in a separate window. If this option is checked then the video doesn't work. Just a transparent block in vlc.

Same thing with mplayer and smplayer. Since in mplayer the video is not embedded everything is ok. While in smplayer again the transparent block.

From what I have tried only VLC outputs error:

```

X Error: BadMatch (invalid parameter attributes) 8
  Extension:    133 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0xb400006

```

And it outputs this repeatedly.

Sometimes it also crashes on opening a video and it outputs the following message:

```

QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 133.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  133 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  105
  Current serial number in output stream:  106

```

I googled a lot about this but I couldn't find anything specific about it.

**_EDIT:_** **Found a workaround for the problem.**

it seems cairo-dock with opengl affects all qt4 applications. There is a workaround in [http://www.glx-dock.org/ww_page.php?p=Recurrents%20problems&lang=en](http://www.glx-dock.org/ww_page.php?p=Recurrents%20problems&lang=en) however this requires that you launch the affected applications with this environment variable:
export XLIB_SKIP_ARGB_VISUALS=1

so what you can do is create a script for each app, for example for skype you could do:
```

sudo su
cd /usr/bin
mv skype skype.real
echo "export XLIB_SKIP_ARGB_VISUALS=1" > skype
echo "skype.real" >> skype
chmod ugo+x skype

```


or you could add the line to the ~/.bashrc file which means it will be a general environment variable.
This means that for all the application this variable will be set, which is not the perfect solution as it means that feature for transparency
will be disabled for all applications. I'm not really sure which applications make use of it, however I don't recommend it.
If you want to do this execute this command:

```

echo "export XLIB_SKIP_ARGB_VISUALS=1" >> ~/.bashrc

```

---

### Post by marcos10 on 2009-08-10
I am getting this strange behaviour too. it seems to be related to the nvidia drivers. The Xvideo extension works fine using the nv driver in xorg but no luck with the proprietry ones. I have tried the 96, 173, 180, 185 and 190 nvidia drivers with no luck.

Turning Compiz on or off has no effect on the behaviour.
Has it something to do with the xvideo libraries in Jaunty? I'm a relative noob so don't have the experience to troubleshoot the problem.

Marcos

---

### Post by dmakreshanski on 2009-08-11
> **marcos10 said:**
> I am getting this strange behaviour too. it seems to be related to the nvidia drivers. The Xvideo extension works fine using the nv driver in xorg but no luck with the proprietry ones. I have tried the 96, 173, 180, 185 and 190 nvidia drivers with no luck.

Turning Compiz on or off has no effect on the behaviour.
Has it something to do with the xvideo libraries in Jaunty? I'm a relative noob so don't have the experience to troubleshoot the problem.

Marcos

Yes, I have the same symptoms. XVideo works with the nv driver, but not with the proprietary ones. I have tried completely removing the XV extension and then installing it again but still no luck.

And when I try setting the xvideo attributes to default
```
xvattr -a XV_SET_DEFAULTS -v 0
```

I still get the same "BadMatch" error

I'm guessing that when Skype crashed for me (while the video was on) it left the driver in a broken state. And I still can't figure out how to reset or reconfigure it.

---

### Post by marcos10 on 2009-08-11
I managed to solve my problem but not sure if it will apply to your situation.

I was running the opengl version of cairo-dock from [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) and it was interfering with the xv and x11 output from vlc and skype. As soon as I ran the cairo version 'cairo-dock -c' the problem went away. 

Hope that helps.

---

### Post by dmakreshanski on 2009-08-14
I'm also running the opengl cairo-dock, and I've already tried with no  cairo-dock running and with the cairo version but I still can't get the video to work.

---

### Post by dmakreshanski on 2009-08-20
Solved! Cairo-dock was also causing the problems for me. It's just that for me just closing cairo didn't work, but removing cairo and restarting the computer solved the problem

---

### Post by kasulstyls on 2009-09-01
thanks for the update, your solution on removing cairo-dock solved my skype problem.

---

### Post by Anubis on 2009-11-01
:(This issue with Cairo was also responsible for borking Mythtv-frontend. Thanks to this thread, I now have a working frontend again. Thanks.

---

### Post by Incubus9 on 2009-11-03
I don't see how this issue is solved. I would like to use VLC embedded, AND cairo-dock with OpenGL. And I am having this problem in Karmic.

---

### Post by dmakreshanski on 2009-11-03
The solved tag is that after removing cairo-dock with opengl embedded xvideo works, however the problem with cairo-dock may still be present

---

### Post by daimaru on 2010-04-02
solved this by setting vlc's video output module to OpenGL

---

