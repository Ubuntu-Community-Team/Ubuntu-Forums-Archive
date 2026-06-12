---
title: "I think I missed a step: Windows Media 9"
date: 2006-03-05
forum: Multimedia &amp; Video
---

### Post by K.Mandla on 2006-03-05
I installed the w32codecs, and synaptic shows them as the latest versions, and yet I still can't seem to open Windows Media 9 files. 

Did I miss a step? or is there another codec I should be looking for? I thought the w32codecs handled WMV files. I might be confused, though.

Thanks in advance.

---

### Post by s6dalane on 2006-03-05
Try installing the codecs with [Automatix]("http://ubuntuforums.org/showthread.php?t=138405").

---

### Post by NoNo_231 on 2006-03-05
As far as I got with the theme if the file you are trying to play is encrypted (almost all I had were encrypted) they don't play. And searching I found that you cannot change it to mp3 if it is encrypted.

But as I remember they didn't play in an other windows machine too. You should have to register and take the licence over the internet - something like that.

---

### Post by K.Mandla on 2006-03-05
[QUOTE=s6dalane]Try installing the codecs with [Automatix]("http://ubuntuforums.org/showthread.php?t=138405").[/QUOTE]
I was deliberately trying to avoid Automatix, just so I could learn a little more about how these things work. I've looked for howto's on the codecs, but couldn't find anything instructive.

[quote=NoNo_231]As far as I got with the theme if the file you are trying to play is encrypted (almost all I had were encrypted) they don't play. And searching I found that you cannot change it to mp3 if it is encrypted.

But as I remember they didn't play in an other windows machine too. You should have to register and take the licence over the internet - something like that.[/quote]
I'm just trying to install the codecs so I can play Windows Media files. I don't think I'm working with encrypted files at all. These are Windows Media 9 files streamed through Firefox.

---

### Post by K.Mandla on 2006-03-06
Well, I think I got the codec issue figured out, but I need to work out the plugin issue for Firefox. I know, I know. It would be much easier to use Automatix. But I have to learn these things, you know. ... Thanks for the help.

---

### Post by yabbadabbadont on 2006-03-06
If you want to play them inside of Firefox, then you probably need to install something like mplayer-plugin or gxine (which includes a firefox plugin).

---

### Post by Maverick88 on 2006-03-06
I have the same problem on a virgin Ubuntu system.  I think you will find that the mplayer firefox plugin is not being used when plyaing back streaming Windows Media 9 content.  On my system, it is the totem plugin.  

I wish I could figure out a way to remove the totem plugin.  I tried removing totem but that did not do it.

I agree I wish the WIKI was better.  I would like to do things manually.

Rob

---

### Post by jrib on 2006-03-06
[QUOTE=Maverick88]I wish I could figure out a way to remove the totem plugin.  I tried removing totem but that did not do it.[/QUOTE]

```
sudo rm /usr/lib/mozilla-firefox/plugins/*totem*
```

should get rid of it, although you should try to figure out the package that provides them first with and then remove that instead.  The command to tell you what package a file belongs to is: ```
dpkg -S /usr/lib/mozilla-firefox/plugins/<insert the name of one of the totem files here>
```

To get the name of one of the totem files just do: ```
ls /usr/lib/mozilla-firefox/plugins/*totem*
```

---

### Post by jrib on 2006-03-06
[QUOTE=K.Mandla]Well, I think I got the codec issue figured out, but I need to work out the plugin issue for Firefox. I know, I know. It would be much easier to use Automatix. But I have to learn these things, you know. ... Thanks for the help.[/QUOTE]

mplayer and mplayer plug-in (mozilla-mplayer package) play everything for me. Just take a look at [https://wiki.ubuntu.com/MplayerInstallHowto](https://wiki.ubuntu.com/MplayerInstallHowto)

You didn't mention what player you were using originally but if it was totem, then you might want to try installing totem-xine since totem-gstreamer doesn't use the w32codecs

---

### Post by Maverick88 on 2006-03-06
Thanks Jason.  I also looked at the Automatrix scripts.  It renames the totem plugin entries (so if you ever want to restore the totem plugin you can).

After I did the following, the mplayer plugin took over and I was able to see streaming QT and WM content in Firefox:

sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.a  /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.a_backup

  sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt  /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt_backup

You might also have to rename the following if they exist (they weren't on my system):

sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.la  /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.la_backup  

sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so  /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so_backup 

I wish this info was added to the WIKI.  Or at minimum this post should be made sticky since I am sure others will have exactly the same problems and experience the same frustration (unless they give up and use automatix).

Rob

---

### Post by jrib on 2006-03-07
[QUOTE=Maverick88]
I wish this info was added to the WIKI.  
Rob[/QUOTE]

Sounds like a good idea.  It might go well in the MplayerInstallHowto wiki page.  Just edit the page and go for it :)

---

