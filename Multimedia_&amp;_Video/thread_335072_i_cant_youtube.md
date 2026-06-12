---
title: "i cant youtube"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by inuz on 2007-01-09
i want to watch some videos on youtube but i get this:

  ""[COLOR="Blue"]Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest flash player. [/COLOR]

what should i do:

thnaks

inuz

---

### Post by pay on 2007-01-09
You need to install flash player.

---

### Post by inuz on 2007-01-09
how?? i am new to ubuntu

I tried from terminal

[B]-sudo apt-get install Macromedia  
or -sudo apt-get install flashplayer
[/B]
 but nothing happens....

plz suggest

---

### Post by anachreon_ on 2007-01-09
I'm on Kubuntu, so am not familiar with Gnome's graphical package manager, but in Adept I simply installed flashplugin-nonfree and video now works fine on YouTube using FireFox 2.  Note that this particular package is non-free (it downloads from Adobe).

---

### Post by pay on 2007-01-09
You can install Macromedia Flash with ```
sudo aptitude install flashplugin-nonfree
```or the free flash player (gnash?)```
sudo aptitude install libflash-mozplugin
```Then to test that they work open firefox and type about:plugins into the address bar.

---

### Post by inuz on 2007-01-10
as suggested above i get this;;;


The following packages have been kept back:
  gnome-cups-manager python-netcdf
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done


what is the problem guys??


thanks a lot

---

### Post by pay on 2007-01-10
You need the universe and multiverse repositories.

---

### Post by Josh1 on 2007-01-10
I just used automatix and then installed swiftfox + the plugins for swiftfox and that worked fine for me :).

---

### Post by inuz on 2007-01-10
how can i use:
universe and multiverse repositories.
plz suggest??

---

### Post by inuz on 2007-01-10
i clicke on synaptic package manager and setting---repositories--add--


thats what u mean....

thanks

---

### Post by inuz on 2007-01-10
now it says:


The following packages have been kept back:
  gnome-cups-manager python-netcdf

---

### Post by inuz on 2007-01-10
also:

Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by &lt;EggMan&gt; on 2007-01-10
Have you tried automatix2 yet?

---

### Post by hakan69 on 2007-01-10
Hello!
I also recommend Automatix or Easyubuntu. However if your processor is an AMD, I don't think Flash will work with Firefox. It does with Swiftfox (only 32-bit) Also, uninstall totem-mozilla (with Synaptic) - I had no sucess until I uninstalled that plugun.

Regards/Hakan

---

### Post by inuz on 2007-01-10
how can i get
Automatix 
 youtube used to work on this comp with XP....also with Fedora5...

is there any way i can see video on youtube...plz suggest again

---

### Post by inuz on 2007-01-10
when i try to 
sudo apt-get update
 i get this
[HTML]0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.[/HTML]
why???

---

### Post by alinuxfan on 2007-01-10
go to
[getautomatix.com]("http://www.getautomatix.com/wiki/index.php?title=Installation")
and follow instructions. Once it is installed one of the many things that it will in turn install for you will be flash player

Adam

---

### Post by pay on 2007-01-10
> **hakan69 said:**
> Hello!
I also recommend Automatix or Easyubuntu. However if your processor is an AMD, I don't think Flash will work with Firefox. It does with Swiftfox (only 32-bit) Also, uninstall totem-mozilla (with Synaptic) - I had no sucess until I uninstalled that plugun.

Regards/HakanIt doesn't matter if your processor is amd or not. It only matters if you are using 32bit of 64bit... even then it doesn't really matter because you can run a 32bit browser or use nspluginwrapper or even gnash to get flash running.

I don't understand why everyone always relies on Automatix... Anyway open upi y our terminal```
wget http://www.adobe.com/go/fp9_update_b2_installer_linuxplugin
tar zxvf FP9_plugin_beta_112006.tar.gz
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/mozilla-firefox/plugins
```And to know if you are on 64bit or not run ```
uname -r
```

---

### Post by inuz on 2007-01-11
i did as suggested above OP but nothing so far...

---

### Post by inuz on 2007-01-11
finally, i clicked on Application-internet and clicked on Java  web start... and now i can watch youtube  thanks a lot for all your info....

---

