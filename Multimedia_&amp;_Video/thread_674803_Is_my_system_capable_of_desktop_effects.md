---
title: "Is my system capable of desktop effects?"
date: 2008-01-22
forum: Multimedia &amp; Video
---

### Post by Zdravko on 2008-01-22
After installing Gutsy, the desktop effects weren't enabled. Does this mean I shouldn't ever try them?
How do I know whether OpenGl support (Direct rendering) is enabled?
My laptop is an Acer Aspire 5715z with an Intel Mobile Graphics Accelerator X3100.

---

### Post by Thanoulis on 2008-01-22
Usually, when the 3D effects aren't enabled by default, means that you'll need some kind of video card driver...(i do not have any clue about your card...sorry....i have NVidia...)
To learn if your Direct Rendering is enabled, try this to a terminal
```
glxinfo | grep rendering
```

---

### Post by Zdravko on 2008-01-22
direct rendering: yes
I think the current loaded driver is 'intel'.

---

### Post by Thanoulis on 2008-01-22
Ok then...go ahead and try to enable them...:)
(Its the Visual Effects tab in the System-->Preferences-->Appearance)

---

### Post by Zdravko on 2008-01-25
I tried. And got an error box - desktop effects could not be enabled.
Why is that?

---

### Post by Yellow Pasque on 2008-01-25
**QUICK GUIDE FOR COMPIZ**
Begin by opening /usr/bin/compiz for editing:
```
gksudo gedit /usr/bin/compiz
```
Make sure the first block after the initial comments has /usr/ paths and not /usr/local paths. Areas you may need to change are bolded.
> COMPIZ_BIN_PATH="**/usr/bin**/" # For window decorators and compiz
PLUGIN_PATH="**/usr/lib/compiz**/" 
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="**compiz.real**" # Final name for compiz (compiz.real)

If your video card is blacklisted (intel 965, x3000, ati x600) scroll down a bit and change the following line. Note that compiz may not run correctly and there's nothing you can do short of waiting for the driver to be fixed.
> BLACKLIST_PCIIDS="$T"
--->
> BLACKLIST_PCIIDS=""
If you have an Intel GMA X3k chip (G3x or G965 chipset), hardware-accelerated video playback will not work correctly, which is why the chip is blacklisted. You can disable compiz before viewing video or disable hardware-accelerated video (I hope you have a fast Core 2 CPU in that case)

Also, if you're using the ATI proprietary Catalyst/fglrx driver, find the line that says WHITELIST="ati nvidia intel..." and add fglrx to the list.

Now, save the file and in the terminal, type: compiz 
It should start. If not, post your output. 

For advanced compiz settings.
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Zdravko on 2008-01-25
I followed another solution:
sudo gedit /etc/xdg/compiz/compiz-manager
SKIP_CHECKS=yes

And it works! At least normal :)

---

### Post by bixejo on 2008-02-29
Hi, Temüjin.

Besides the changes you mention, I had to make one more:

My former /etc/xdg/compiz/compiz-manager file looked like:

> #Updated whitelist and source Ubuntu settings

. /etc/xdg/compiz/compiz-manager.ubuntu

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810 fglrx"

I had to comment the line referred to compiz-manager.ubuntu to make compiz work:

> #Updated whitelist and source Ubuntu settings

# . /etc/xdg/compiz/compiz-manager.ubuntu

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810 fglrx"

 Any time I tried to start compiz, it complained about missing /etc/xdg/compiz/compiz-manager.ubuntu file (which indeed does not exist in my system).

--Bixejo

---

### Post by Virgilius on 2008-02-29
Hello, I'm also having problems with my Compiz as well since it wasn't running. I did the modifications of Temüjin and Zdravko and it came up with this when running Compiz through the Terminal:

```
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

(gtk-window-decorator:5824): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(gtk-window-decorator:5824): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,

```

It doesn't seem to be working for me because of the warnings and what have you.

---

### Post by Virgilius on 2008-02-29
Sorry for spamming this topic, but my graphics card is an ATI Radeon X800XT. Just letting you all know.

---

### Post by darkstr2o4 on 2008-03-01
I have followed the posts in this thread and this is what gets spit out by the terminal 
```
aslan@narnia:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1920x1200) to maximum 3D texture size (8192): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

aslan@narnia:~$ 


```

---

### Post by Yellow Pasque on 2008-03-21
darkstor, if you haven't already figured it out, you need to add your driver (fglrx?) to the WHITELIST="ati nvidia intel..." line in /usr/bin/compiz

---

### Post by Thelasko on 2008-04-07
[Vote]("http://brainstorm.ubuntu.com/idea/1266/") to get the Intel driver fixed.  Sorry to spam but...

---

