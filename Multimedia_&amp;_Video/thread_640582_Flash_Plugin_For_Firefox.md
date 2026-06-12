---
title: "Flash Plugin For Firefox?"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by CarlosinFL on 2007-12-14
I just installed 7.10 and when I open a site that requires a flash plugin, I get the install flash plugin prompt which I select Adobe and it installs fine. It asks for sudo passwd and runs through the install process and then the page loads again however flash plugin is not showing and I get the "missing plugin" pop up. I then select Adobe again however I get a window as shown below. 

This feature worked fine in 7.04 so I don't know why it does not work in 7.10.


Any advice?

---

### Post by lvleph on 2007-12-14
I just got the same error this morning. Not sure the issue.

---

### Post by CarlosinFL on 2007-12-14
Yeah - it happens both on my PC and on my Laptop however this was never an issue on 7.04. Seems to be an issue on 7.10 only.

I really need a flash plugin for my Firefox browser.

---

### Post by disturbedite on 2007-12-14
copy/move libflashplayer.so to /home/USER/.mozilla/plugins/.

---

### Post by CarlosinFL on 2007-12-14
You specified a destination but no source...

Thanks for the input!

---

### Post by erfahren on 2007-12-14
browse to /usr/lib and see if there is a directory "flashplugin-nonfree" (/usr/lib/flashplugin-nonfree/)

if there is do:
```

sudo ln -s /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/firefox/plugins

```

---

### Post by erfahren on 2007-12-14
Note: in the normal Flash install through Synaptic all it really does is create that directory I mentioned and creates symbolic link(s) to the file(s) in it in /usr/lib/firefox/plugins

(The older Flash 9 contained two files - libflashplayer.so and flashplayer.xpt , the newer version of Flash only has the libflashplayer.so - I'm not sure what version is being used for Gutsy right now.)

---

### Post by radioraheem on 2007-12-14
I'm experiencing the same problem and running the above command did not resolve it.

Between this and the nvidia 7000 series video bug I'm starting to get really tired of ubuntu...

Update:  Ok, this is weird, the /usr/lib/flashplugin-nonfree directory is empty on this box.  Nothing to link against.

Color me confused.  I tried installing via Synaptic and the directory is still empty.

---

### Post by CarlosinFL on 2007-12-14
Yes - same with me:

/usr/lib/flashplugin-nonfree/

That directory above is empty! 

I then looked at the following directory:

```
root@cwilliams:~# cd /usr/lib/firefox/plugins/lib
libtotem-basic-plugin.so         libtotem-gmp-plugin.xpt          libtotem-narrowspace-plugin.so   
libtotem-basic-plugin.xpt        libtotem-mully-plugin.so         libtotem-narrowspace-plugin.xpt  
libtotem-gmp-plugin.so           libtotem-mully-plugin.xpt        libunixprintplugin.so    
```

I don't know why installing a flash plugin for FF is so hard...

It worked on 7.04 fine. 

Anyone know what is wrong?

---

### Post by erfahren on 2007-12-14
it could have something to do with the bug they're talking about over on this thread (the post linked to in particular) [http://ubuntuforums.org/showpost.php?p=3916215&postcount=18](http://ubuntuforums.org/showpost.php?p=3916215&postcount=18)

it has something to do with the new flashplayer version and it being included in the Gutsy repos. 

I don't use Gutsy so I had no idea what they were talking about at first, but figured it would've been worked out by now.

Maybe if you go to Adobe and get it from there, but I tried the new version and it was buggy for me. I have the 9.0.31.0 saved if anyone wants it.

---

### Post by shinkaide on 2007-12-14
I have the same problem. I installed Flash via the popup in Firefox, but it has no effect. Everytime I visit a page with Flash content, I'm prompted to install it again, even though Firefox tells me it's already installed.

---

### Post by CarlosinFL on 2007-12-14
I reinstalled Debian Linux guys...everything works fine. My font is just not as pretty as in Ubuntu.

---

### Post by stanley82 on 2007-12-14
I have updated Fiesty to Gutsy to get the latest app updates etc for a special app that I need.  Now non of my plugins work on Firefox.  Mpalyer, flash and Real Helix.  Oh dear here I go again.

[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)
Kilzz from the above link worked well on Feisty.  His update instructions Fiesty to Gutsy did not pan out due to a checksum error on the flash dot.tar.gz file.  Any ideas?

---

### Post by AmericanYellow on 2007-12-14
I had the same problem. You can simply go to Adobe's website and download the Flash tar.gz, unzip and install manually. It takes only 15 seconds.

---

### Post by mdpalow on 2007-12-15
see links below (nevermind the title of link) in my signature. Click one and read first post.

---

### Post by radioraheem on 2007-12-15
I just grabbed the latest tar.gz file from adobe's site and installed it.  Works fine now.

And to think manual installs used to be (relatively speaking) a pain compared to using ubuntu's built in tools...

I'm just glad it's working now!

---

### Post by disturbedite on 2007-12-15
> **Carlwill said:**
> You specified a destination but no source...

Thanks for the input!

i assumed since you installed it you'd know where it was...

---

### Post by daradib on 2007-12-15
[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

