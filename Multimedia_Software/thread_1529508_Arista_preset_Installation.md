---
title: "Arista preset Installation"
date: 2010-07-12
forum: Multimedia Software
---

### Post by bharanik on 2010-07-12
Hi All,

I have installed Arista successfully using Synaptic.

However, It has installed arista-0.9.3 version.

My question is
1. How to upgrade to arista-0.9.5 version which contains my preset by default?
    (OR)
2. How to install a Preset Manually?

I am using Ubuntu 10.04.

Regards,
Bharani K

---

### Post by nlsthzn on 2010-09-26
> **bharanik said:**
> Hi All,

I have installed Arista successfully using Synaptic.

However, It has installed arista-0.9.3 version.

My question is
1. How to upgrade to arista-0.9.5 version which contains my preset by default?
    (OR)
2. How to install a Preset Manually?

I am using Ubuntu 10.04.

Regards,
Bharani K

Hello bharanik,

Firstly I would like to say it is sad that in how many months you have not even had a single reply to your question...

As for your second question about installing the latest version or your own preset I am a bit stumped and this has lead me to your thread seeking an answer.  I too have 0.9.3 from the Software Center and as per the website ([http://www.transcoder.org/presets/create/](http://www.transcoder.org/presets/create/)) it should be a simple affair of creating the preset then downloading and in the application selecting the preset to be installed... problem is it seems that 0.9.3 doesn't have the same option to install the preset you have created...

Which leaves installing the latest, which entails installing from source (which Ubuntu is not set up properly to begin with so I guess I need to do some more homework (if any body has a quick fix please feel free to jump in!)


Neil

---

### Post by nlsthzn on 2010-09-26
I feel rather silly currently... the files I downloaded from the Arista website is already compiled and not the source... ran the updated version of the app and I can add my own presets...

Now I do have one question, I have the older version installed (can access it from the menu etc. how do I "install" the newer version?  Do I just copy the files over?  But where do I copy it?

I am not sure what would be the best and need some guidance.


Regards
Neil

---

### Post by Baneblade on 2010-12-06
I'm looking for how to install Arista from the website download as well. If I discover how we are meant to do this, I'll post it here.

In the mean time, simply running the arista-gtk python script seems to be working well, if a little tedious to use.

---

### Post by Baneblade on 2010-12-13
If you upgrade to Maverick it will be [available from the repos]("http://askubuntu.com/questions/15675/how-to-install-arista-transcoder-from-source")

For those of us sticking with 10.04:

After changing to the directory it is located in

```
sudo python setup.py install --install-layout=deb
```

This will install it for you and place a shortcut in Sound & Video menu.

[Source]("http://askubuntu.com/questions/15675/how-to-install-arista-transcoder-from-source")

---

### Post by Superhuman on 2011-04-13
> **Baneblade said:**
> 
```
sudo python setup.py install --install-layout=deb
```


Thanks, this worked to upgrade to 0.9.6.

---

### Post by radu_radu on 2011-04-23
I've installed Arista as advised by Baneblade, but I'm getting the following error when I try to run it (console output):
```
Traceback (most recent call last):
  File "/usr/bin/arista-gtk", line 1689, in <module>
    main = MainWindow(options)
  File "/usr/bin/arista-gtk", line 397, in __init__
    self.setup_source()
  File "/usr/bin/arista-gtk", line 551, in setup_source
    size, 0))
glib.GError: Icon 'camera-video' not present in theme

```

So I did some digging & I found this [[COLOR="Blue"]italian website[/COLOR]]("https://lippolweblog.wordpress.com/2010/10/10/arista-transcoder-su-arch-con-kde-come-risolvere-problema-di-avvio/") that says I should look for "gnome-icon-theme-symbolic".
I'm running Kubuntu 10.04, that package appears not to be available for this version. I tried to compile gnome-icon-theme-symbolic-3.0.0. from source, but I still get the same error on arista-gtk. arista-transcode works just fine.
And I just checked,
```
 locate camera-video
/usr/share/icons/gnome/16x16/devices/camera-video.png
/usr/share/icons/gnome/22x22/devices/camera-video.png
/usr/share/icons/gnome/24x24/devices/camera-video.png
/usr/share/icons/gnome/32x32/devices/camera-video.png
/usr/share/icons/gnome/scalable/devices/camera-video.svg
```
I went in there and ran "gtk-update-icon-cache -f", and it told me: "gtk-update-icon-cache: Cache file created successfully."
So I guess I'm a little lost from here. Any advice on how to fix this silly icon problem? Or it's something else I'm missing?

---

### Post by hemna on 2011-10-06
dpkg -S /usr/share/icons/gnome/16x16/devices/camera-video.png 
gnome-icon-theme: /usr/share/icons/gnome/16x16/devices/camera-video.png


Try installing gnome-icon-theme ?

---

### Post by Sharpie1 on 2012-02-10
Hi
Arista wouldn't run on my daughters Dell Mini Inspiron, with a fresh install of 11.10, I downloaded gnome-icon-theme from
[http://ftp.gnome.org/pub/GNOME/sources/gnome-icon-theme/3.2/gnome-icon-theme-3.2.0.tar.bz2](http://ftp.gnome.org/pub/GNOME/sources/gnome-icon-theme/3.2/gnome-icon-theme-3.2.0.tar.bz2)
open terminal
cd to your gnome-icon-theme directory
configure
make
sudo make-install
then Arista works fine..  because its looking for a device icon for the webcam that isn't in the directory in usr/share/icons/gnome
[FONT=monospace]
[/FONT]hth

Arista is an excellent program for quick and easy conversion to for instance Iphone, PSP etc, and is very easy to use. Also, install the Ubuntu restricted extras !


Sharpie1[FONT=monospace]



PS to install a preset, save the archive of the preset from [Arista]("http://transcoder.org/presets/"). (normally tar.bz2) to your download folder, then in Arista click Install New Preset and navigate to your .bz2 file
[/FONT]

---

### Post by fi2 on 2012-02-11
```

```I have a persistent error message in Arista. When I try to convert an avi file with the DVD Player - Divx Home Theater preset, it starts searching for a "suitable plugin" then 

```
No packages with the requested plugins found
The requested plugins are:
GStreamer element xvidenc

```
I started it with 

```
arista-gtk -v
```

and the output says:

```
arista.presets [435]: INFO Attempting to install elements: xvidenc
arista.presets [444]: ERROR Unable to install required elements!

```

I am not into video formats at all, so it may be me doing some stupid thing. The starting problem is that my desktop video player does not play a file taken by a camera. The player can do divx, so I supposed this should be the preset to use.

It is a fresh install of Oneiric (32bit) and Synaptic shows, that xvidenc is installed. Running around in circles. Anybody could help please?

---

