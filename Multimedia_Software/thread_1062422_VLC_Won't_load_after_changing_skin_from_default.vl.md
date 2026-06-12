---
title: "VLC Won't load after changing skin from default.vlt"
date: 2009-02-06
forum: Multimedia Software
---

### Post by Modie101 on 2009-02-06
I just upgraded to Kubuntu Intrepid Ibex. I upgraded from 8.04.
I successfully installed VLC using "sudo apt-get install vlc".

I then tried to add skins from [http://www.videolan.org/vlc/skins.php](http://www.videolan.org/vlc/skins.php)

I unzipped the skins package at first under ~/.vlc/skins2/

When I tried to switch skins through the skins chooser they were not present so then I copied all the new skins to:
/usr/share/vlc/skins2

Now the skins were choosable under the VLC skin chooser but when I tried to change the skin nothing would happen it would stay at the default.vlt. I played around with permissions chmod 777 * to see if that would work but nothing would allow me to change from the default. so I went ahead and removed the default.vlt suddenly VLC would no longer load it would ask me to choose a skin even though I copied the defult.vlt skin back into the directory it still refuses to load. I even uninstalled it by: "sudo apt-get autoremove vlc" and tried to reinstall it. It still does not load.

I uninstalled and resinstalled several times to no avail.

What the heck did I do wrong?

---

### Post by kostkon on 2009-02-06
First of all, try to remove any old configuration files that may still be present by deleting the *.vlc* folder.

If that does not work, then you can go to Synaptic and do a complete removal of VLC or in the terminal, like this:
```
sudo apt-get remove vlc --purge
```
and then install it again.

---

### Post by Modie101 on 2009-02-06
One more thing It actually generates and error and automatically launcehs the skin chooser but when i select any skin including default.vlt it just closes VLC completely.

it closes too fast to see the errors that are generated.

Modie101

---

### Post by kostkon on 2009-02-06
Whoops, you have Kubuntu, so you have Adept instead of Synaptic.

---

### Post by Modie101 on 2009-02-06
so will --purge work?

---

### Post by kostkon on 2009-02-06
> **Modie101 said:**
> One more thing It actually generates and error and automatically launcehs the skin chooser but when i select any skin including default.vlt it just closes VLC completely.

it closes too fast to see the errors that are generated.

Modie101
You can run it from the terminal. That way you'll be able to see the error messages.

Open a terminal and give
```
vlc
```
to run it.

---

### Post by kostkon on 2009-02-06
> **Modie101 said:**
> so will --purge work?
Yes, I believe so.

---

### Post by Modie101 on 2009-02-06
ok I removed the config files as you said and I even had to "sudo apt-get autoremove vlc" because the directories were still there.
so should I try to "sudo apt-get install vlc" or is there another way to install it again?

---

### Post by kostkon on 2009-02-06
> **Modie101 said:**
> ok I removed the config files as you said and I even had to "sudo apt-get autoremove vlc" because the directories were still there.
so should I try to "sudo apt-get install vlc" or is there another way to install it again?
No, just install it again the normal way. Now VLC should start afresh.

---

### Post by Modie101 on 2009-02-06
00000001] main libvlc debug: translation test: code is "C"
[00000396] telnet interface: using the VLM interface plugin...
[00000396] telnet interface: telnet interface started on interface  4212
[00000420] access_directory access error: /usr/share/vlc/skins2/chaos.vlt: No such file or directory
[00000420] access_file access error: cannot open file /usr/share/vlc/skins2/chaos.vlt (No such file or directory)
[00000411] main interface error: no suitable access module for `/usr/share/vlc/skins2/chaos.vlt'
[00000411] skins2 interface error: failed to open /usr/share/vlc/skins2/chaos.vlt for reading
[00000411] skins2 interface error: failed to parse /usr/share/vlc/skins2/chaos.vlt
[00000425] xml xml error: XML parser error (line 1) : failed to load external entity "skin.dtd"

[00000425] xml xml error: XML parser error (line 2) : Validation failed: no DTD found !
[00000411] skins2 interface error: failed to parse /tmp/vltjKshdL/default/theme.xml
[00000411] skins2 interface error: error while parsing /tmp/vltjKshdL/default/theme.xml
[00000428] xml xml error: XML parser error (line 1) : Document is empty

[00000411] skins2 interface error: failed to parse /usr/share/vlc/skins2/default.vlt

---

### Post by Modie101 on 2009-02-06
Sorry I forgot to add text.

That's what I get after reinstalling" it doesn't seem to like the fact that a skin called chaos is not present in the directory.
Oh one caveat is that I switched to a skin called chaos.vlt that was in the skins pack, then I tried to switch back to default then thats when this mess began!

Modie101

---

### Post by kostkon on 2009-02-06
> **Modie101 said:**
> Sorry I forgot to add text.

That's what I get after reinstalling" it doesn't seem to like the fact that a skin called chaos is not present in the directory.
Oh one caveat is that I switched to a skin called chaos.vlt that was in the skins pack, then I tried to switch back to default then thats when this mess began!

Modie101
Sorry to ask again, but did you actually try to do a complete removal, i.e. in a terminal give
```
sudo apt-get remove vlc --purge
```
or in Adept?

---

### Post by Modie101 on 2009-02-06
Here's some news! I copied chaos.vlt back into /usr/share/vls/skins2 and it loaded it again FINALLY!!
gonna try to see if loading the rest of the skins "one by one" allows me to change them.

---

### Post by Modie101 on 2009-02-06
> **kostkon said:**
> Sorry to ask again, but did you actually try to do a complete removal, i.e. in a terminal give
```
sudo apt-get remove vlc --purge
```
or in Adept?

Yes I did. and kept giving me that error until i specifcally copied chaos.vlt back into the /usr/share/vlc/skins2 directory.

---

### Post by kostkon on 2009-02-06
> **Modie101 said:**
> Yes I did. and kept giving me that error until i specifcally copied chaos.vlt back into the /usr/share/vlc/skins2 directory.
Ah, now I understand where the errors came from! Sorry, I got confused.

---

### Post by Modie101 on 2009-02-06
Guess what! now I choose a skin called Presume.vlt its from the skins pack and now vlc won't load at all!

---

### Post by mc4man on 2009-02-06
vlc 0.9.x is very touchy about skins, many will not work. You'll be lucky to find a handful that do.

if you can't get vlc back than this will restore
In konsole

```
vlc --reset-config
```

---

### Post by redroad55 on 2009-02-06
Is this how you are adding skin:>   Adding a new skin

To add a new skin go to the Skin page, choose a skin and click the "Download" link. Alternatively you can obtain the 'Skin Pack' which contains all available skins.

Important: It is recommended to download the 'Skin Pack'! This is, because the download package of some 'specific' skins (e.g. ASkin and WMP11), don't include it's '.vlt' file, that is needed to use it. These '.vlt' files are only found in the 'Skin Pack', which, on the other hand, doesn't include other files needed by other skins.

In addition to the skins listed on the 'Skins Page', VLC supports all Winamp2 and XMMS skins (.wsz files).

To install, move the skins' ".vlt" file to the 'VLC\skins' (Linux users ~/.vlc/skins2/) directory. For the the 'Skin Pack' goes: unzip it to 'VLC\skins'. Each skin will have it's own sub-folder created containing it's files.

Finally, to set the skin, right-click in the title bar or control bar, go to 'Select skin' and select the desired skin.

post back..Best to you

---

### Post by Modie101 on 2009-02-06
Dude that did the trick.but I want to be able to change skins. Where can I get a skins pack that will not mess up my installation? 

or can I use the same skins pack and unzip in a different location perhaps?

Modie101!

---

### Post by Modie101 on 2009-02-06
Ok I say your post but the strang thing is the skins pack had only .vlt files no subdirectories. so I'm not sure anout using it. But anyway you saved me. maybe I'll justchoose a few skins for now and try loading those from the webpage.

I really appreciate your help.

---

### Post by mc4man on 2009-02-06
Here are some. now that vlc 0.9 has been out a while there should be more, just try to use ones designed for 0.9.x 
Most 0.8.x skins won't work though some may. (process of elimination, when vlc chokes on one just reset and discard that skin


[http://www.videolan.org/vlc/skins.php](http://www.videolan.org/vlc/skins.php)

---

### Post by Uthen Phutneam on 2009-05-27
Run this commandline in terminal.

vlc  --reset-config

---

