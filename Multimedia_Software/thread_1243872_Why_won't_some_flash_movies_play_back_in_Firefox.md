---
title: "Why won't some flash movies play back in Firefox?"
date: 2009-08-18
forum: Multimedia Software
---

### Post by stefcep on 2009-08-18
I tried to play video from newspaper site eg [http://media.theage.com.au/flintoff-faces-his-final-test-686402.html?from=videobox](http://media.theage.com.au/flintoff-faces-his-final-test-686402.html?from=videobox)

Any idea why they won't play back at all? Ubuntu 9.04, Firefox 3.13 and Shiretoko.

---

### Post by wojox on 2009-08-18
Well it was about Michael Jacksons mom...wait I don't want to ruin it.
Take a look at lovinglinux Firefox Optimization thread. 
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)
It helped me out.

---

### Post by HappyFeet on 2009-08-18
Works for me. What flash are you using? I use the adobe flash and have the mozilla-mplayer plugin.

---

### Post by anechoic on 2009-08-18
if you are using Gnash they report a change in Flash content as breaking the latest version...
for example YouTube works but Vimeo doesn't
file a bug at Launchpad

---

### Post by oboedad55 on 2009-08-18
> **anechoic said:**
> if you are using Gnash they report a change in Flash content as breaking the latest version...
for example YouTube works but Vimeo doesn't
file a bug at Launchpad

It says Flintoff faces his final Test.

---

### Post by stefcep on 2009-08-19
thank you.

I ended up doing this :

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

I also installed mozilla-mplayer plug-in from synaptic, mplayer itself and the w32codecs (not sure if needed, but I put it in anyway)

gnash was never installed in my system.

Previously when playing flash video eg from youtube i could right click and see the video downloading, select it and save it.  I've lost this now.  oh well can't have everything, i suppose.

---

### Post by bzhao on 2009-08-19
> **stefcep said:**
> thank you.

I ended up doing this :

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

I also installed mozilla-mplayer plug-in from synaptic, mplayer itself and the w32codecs (not sure if needed, but I put it in anyway)

gnash was never installed in my system.

Previously when playing flash video eg from youtube i could right click and see the video downloading, select it and save it.  I've lost this now.  oh well can't have everything, i suppose.


The above post has fix the same problem I have been having.
Thanks indeed!

---

### Post by anechoic on 2009-08-21
//sudo apt-get remove mozilla-plugin-gnash

it seems gnash was installed on your system

also, I tried your fix and wasn't able to play Vimeo content or anything from Comedy Central

:(

---

### Post by stefcep on 2009-08-26
> **anechoic said:**
> //sudo apt-get remove mozilla-plugin-gnash

it seems gnash was installed on your system

No it wasn't, I issued that command in case it was, and the package installer said  gnash wasn't installed.
> 
also, I tried your fix and wasn't able to play Vimeo content or anything from Comedy Central

:(
vimeo works for me. 

comedy central works, but I had to access the clips from the drop down menus  and with South PArk clips, the advertisements would play but not the actual South PArk clip unless I clicked o replay the clip, but all other clips including futurama played OK.

can also stream live tv from p2p4ue.

Works for me but your mileage may vary.

---

### Post by stefcep on 2009-08-26
> **bzhao said:**
> The above post has fix the same problem I have been having.
Thanks indeed!

CAn you check that vimeo and comedy central work for you?

---

