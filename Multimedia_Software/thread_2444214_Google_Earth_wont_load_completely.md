---
title: "Google Earth wont load completely"
date: 2020-05-26
forum: Multimedia Software
---

### Post by adambond on 2020-05-26
Im running 
18.04.4 LTS
Intel® G33
GNOME 3.28.2
64bit

When I open google earth, the dashboard loads just fine, but the planet never materializes, and this is all I get. 

I think its something to do with WebGL? But know nothing about that.

---

### Post by monkeybrain20122 on 2020-05-26
You can use GE in the browser.

---

### Post by adambond on 2020-05-26
I know. But I need some of the utilities. Such as measuring in miles, ft, etc.   Thank you tho.

---

### Post by monkeybrain20122 on 2020-05-26
So try this just for a diagnosis

```
sudo apt install mesa-utils
```

After mesa-utils is installed, run this and post the outputs.

```
glxinfo | grep OpenGL
```

---

### Post by adambond on 2020-05-26
```
glxinfo | grep OpenGL
```

```
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) G33 
OpenGL version string: 1.4 Mesa 19.2.8
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 2.0 Mesa 19.2.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
OpenGL ES profile extensions:
```

---

### Post by monkeybrain20122 on 2020-05-27
Your card is too old, I think you need at least OpenGL2.1

---

### Post by Yellow Pasque on 2020-05-28
You can possibly hack around it: [https://ubuntuforums.org/showthread.php?t=2374952&p=13701831#post13701831](https://ubuntuforums.org/showthread.php?t=2374952&p=13701831#post13701831)
Even if you get OpenGL 2.x advertised, don't be surprised if Google Earth (or other 3D apps) are buggy. Also, don't be surprised if GE is painfully slow.

---

### Post by monkeybrain20122 on 2020-05-28
> **Yellow Pasque said:**
> You can possibly hack around it: [https://ubuntuforums.org/showthread.php?t=2374952&p=13701831#post13701831](https://ubuntuforums.org/showthread.php?t=2374952&p=13701831#post13701831)
Even if you get OpenGL 2.x advertised, don't be surprised if Google Earth (or other 3D apps) are buggy. Also, don't be surprised if GE is painfully slow.

OP can try to upgrade mesa driver but doubt that it will work, it is a hardware limitation. [https://www.intel.com/content/www/us/en/support/articles/000005524/graphics-drivers.html](https://www.intel.com/content/www/us/en/support/articles/000005524/graphics-drivers.html)

---

### Post by Yellow Pasque on 2020-05-28
> **monkeybrain20122 said:**
> OP can try to upgrade mesa driver but doubt that it will work, it is a hardware limitation.

It's not upgrading or changing the driver. It's faking the OpenGL version by using CPU/software rendering for a few hardware features that these GPU's lack that make them compatible with OpenGL 2.x
If you read the article, you'll see that Intel devs previously used this as the default configuration on Linux, but decided against it because of bugs and poor performance. [https://www.phoronix.com/scan.php?page=news_item&px=Mesa-i915-OpenGL-2-Drop](https://www.phoronix.com/scan.php?page=news_item&px=Mesa-i915-OpenGL-2-Drop)

So, yes, it should "work" in the sense that OpenGL 2.x is advertised, but as I told OP, don't be surprised if a program doesn't work and don't expect miracles in performance.

---

### Post by adambond on 2020-05-29
Thanks, for a bunch of great information. I will attempt these fixes. 
I dont actually have a 'graphics card'. But i would gladly buy one if that would resolve the problem. Sounds like it wont. ?

---

