---
title: "Getting mic to work on Sony Vaio VGN-CS215J"
date: 2009-01-18
forum: Multimedia Software
---

### Post by MockY on 2009-01-18
I just purchased a Sony Vaio VGN-CS215J for my wife. Almost everything works out of the box and I am overall very happy with it. However, I can't get the built-in microphone to work in Skype. 
I have followed this guide:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)
but nothing seems to work. Don't really know if I do it right but I tried to add the following lines in /etc/modprobe.d/alsa-base:
```

options snd-hda-intel model=vaio
options snd-hda-intel model=sony-assamd
options snd-hda-intel model=base

```
I have no none of them in this file, but as a result, the osund is now very low. How come, since it is back to when I started?

cat /proc/asound/card0/codec#* | grep Codec  gives me:
```

Codec: Realtek ALC262
Codec: Conexant ID 2c06

```

I have even replaced Pulseaudio with Esound.

I am now running out of ideas and would like to ask for help.
So if anyone has an idea, please let me know.

Thanks.

---

### Post by carlkhabbaz on 2009-03-18
me too! same hardware, same problem

---

### Post by MockY on 2009-04-27
Since this laptop runs on an Intel graphic card, upgrading to Jaunty is completely out of the question, so I can't test if this problem still exists. Have to wait for Karmic Koala.

---

### Post by MockY on 2009-07-07
Another update:

I just purchased a Vaio for myself (VGN-NW150J) and I am having the same problem.
The internal mic does not work, but the extrenal one does. The only work around I use right now is using an external mic plugged in to the laptop. The one I use currently is a Sony  ECM-DS30P that can be found [HERE]("http://www.sonystyle.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&langId=-1&productId=11035572")

---

### Post by Digitallysick on 2009-07-14
I have a Lenovo Y410 but it uses the ALC262 , same audio I believe because my mic doesn't work either. The sound drivers are a major pain for this regardless of OS

---

### Post by igorzwx on 2009-07-14
Ask on OSS4 forum, if they have such driver for OSS

---

### Post by MockY on 2009-07-17
> **Digitallysick said:**
> I have a Lenovo Y410 but it uses the ALC262 , same audio I believe because my mic doesn't work either.
Does the external mic work for you, as in, can you plug in a mic and use it like I do? I don't have a solution, I'm just curious if it's the same dealio for you.

---

### Post by kija on 2009-07-26
I have a Sony Vaio VGN-CS14G laptop and have this same problem, the internal mic is not working. I cant use skype because of this :(. Did anyone find a fix yet?
Please help...

---

### Post by MockY on 2009-07-27
Like I mentioned earlier, the only way you can use Skype (without mad Linux hacking) is by buying an external mic. The one I use, which is a pleasure to use and does not take up much room either, is [**THIS ONE**]("http://www.sonystyle.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&langId=-1&productId=11035572")

---

### Post by HarshReality on 2009-07-29
When I got my VGN-NS325J I was actually looking at the hardware figuring to get something that was actually within 100% lin compatibility.. so after all this turns out that everything worked out of the box EXCEPT the internal Mic.  While I know it sounds picky.. I guess I just cant get 100 % without BG >:(

Incidentally I have the same reponse for Codec as our first poster.. I did come across one post somewhere that mentioned typically parts were provided by BIOS settings however my particular model has no such settings in BIOS. So it might just be a matter of getting it what it needs to actually use the thing.

---

