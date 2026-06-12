---
title: "[SOLVED] Internet Radio etc."
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by Dave Otter on 2007-05-01
Is there an equivalent to Winamp?
 If so where can I get it?

---

### Post by agurk on 2007-05-01
Look for a program called "xmms" in Synaptic (System -> Administration -> Synaptic Package Manager), or simply type:
```
sudo apt-get install xmms
```
in the terminal.

---

### Post by Dave Otter on 2007-05-01
Thanks found XMMS

---

### Post by Dave Otter on 2007-05-01
How do I now get to Radio channels

---

### Post by agurk on 2007-05-01
There are probably many ways to go about it, but I have associated .pls and .m3u files with xmms, which makes it easy for me to try out different radio stations on the web.
Example:

1. Go to [http://www.radioparadise.com](http://www.radioparadise.com), right-click the "128k MP3" link, choose "Save link as..." and put it on your desktop.
2. Right-click on the "rp_128-9.m3u" file on your desktop, choose "Open with" -> "Open with Other Application" and select xmms from the list of applications.
3. You should now be able to listen to the radio station. To automate things so that you just have to click the link next time, right-click the file again and select "Properties". In the tab "Open with", select xmms.

---

### Post by Dave Otter on 2007-05-02
Have now got one channel-should I be able to get more?
  If so   How?

---

### Post by agurk on 2007-05-02
Sure, just shop around for anything you might fancy. A favorite of mine is [http://slayradio.org](http://slayradio.org) since I have a soft spot for retro gaming. [http://www.radio-locator.com](http://www.radio-locator.com) comes up with a lot of suggestions, looks like it's worth a try.
There are a couple of linux related podcasts around as well that I listen too, in particular [LAS](http://www.linuxactionshow.com) and [LUG Radio](http://lugradio.org). Podcasts are prerecorded shows you can download and listen to.

---

### Post by bionnaki on 2007-05-02
the easy way would be to just

sudo apt-get install streamtuner

---

### Post by Dave Otter on 2007-05-02
sudo apt-get install streamtuner..... this is where I go wrong   where do I type this


                               Thanks

---

### Post by agurk on 2007-05-02
You type it into a terminal, you'll find it in Applications -> Accessories -> Terminal
It will ask you for your password, just type it in and press <Enter>.

Alternatively, you can find and install the streamtuner package using Synaptic, just like you did with XMMS.

Synaptic is actually just a graphical interface to the "apt" program, which is Ubuntu's package management system.

---

### Post by Dave Otter on 2007-05-02
Agurk

           Thank you for that-much appreciated

---

### Post by agurk on 2007-05-02
No problem!

---

### Post by Dave Otter on 2007-05-02
Thanks to all who helped,  agurk and  bionnaki-now got radio up and running

---

### Post by Dave Otter on 2007-05-12
I have just had to reinstall Ubuntu 6.06
   I have lost all the sts
ations I could get thru' streamtuner-I cannot find it in Synaptic Package Manager. 

    Also lost DVD player.....Help!

---

### Post by agurk on 2007-05-13
Oops. Make sure you have the Universe and Multiverse repositories enabled in Synaptic: [http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

---

### Post by ThomasNovin on 2007-05-13
You really shouldn't use XMMS. Most other distributions has dropped the xmms-packages  . The GUI looks like sh*t.

Try the Beep Media Player instead (just install package beep-media-player). BMP supports Winamp Classic skins so you can make it look just like Winamp :)

[http://ubuntuforums.org/showpost.php?p=2640467&postcount=2](http://ubuntuforums.org/showpost.php?p=2640467&postcount=2)

---

### Post by Dave Otter on 2007-05-13
All seems well now   not sure that I did anything-just reappeared.

    Think I am too impatient to wait long enough for all updates.
    
       Anyhow-thanks to all who rep;ied with suggestions

---

