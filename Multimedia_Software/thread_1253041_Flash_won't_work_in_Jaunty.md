---
title: "Flash won't work in Jaunty"
date: 2009-08-29
forum: Multimedia Software
---

### Post by alexeix on 2009-08-29
Hi,

I've done a fresh installation of Jaunty (32bit) and am trying to get Flash working, but am having big problems.

Although Youtube worked initially, the following Nokia web page didn't: [http://maemo.nokia.com/n900/360/](http://maemo.nokia.com/n900/360/) - I get a prompt to install Flash.

Now, after trying various suggestions from the forum, not even Youtube works.

I've already tried all the suggestions here ([http://www.ubuntugeek.com/fix-for-flash-not-working-after-jaunty-upgrade-64bit.html#more-1318](http://www.ubuntugeek.com/fix-for-flash-not-working-after-jaunty-upgrade-64bit.html#more-1318)), but after several hours, am losing patience...
It just shouldn't be this difficult.

Any help would be much appreciated.
Thanks.

---

### Post by stefcep on 2009-08-29
Have you tried this:

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

I also installed mozilla-mplayer plug-in from synaptic, mplayer itself and the w32codecs (not sure if needed, but I put it in anyway)
 
The nokia site still wants you to install flash, but you-tube should work.

---

### Post by lovinglinux on 2009-08-29
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

