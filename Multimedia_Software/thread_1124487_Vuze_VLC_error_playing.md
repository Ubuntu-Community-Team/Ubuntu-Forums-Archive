---
title: "Vuze VLC error playing"
date: 2009-04-13
forum: Multimedia Software
---

### Post by retrodans on 2009-04-13
I have been trying to get vuze to automatically load VLC rather than totem, and almost got there with:

```
sudo gedit /etc/gnome/defaults.list
```

Then proceeded to put in vlc.desktop where required.  This has resulted in the play button permanently being grey, but I can click the 'launch' button, this then opens up vlc.  Sadly it doesn't start playing the media, so I click play within vlc, it then gives me the below errors:

```

File reading failed:
VLC could not open the file "file:/home/retrobadger/Azureus Downloads/17_Again_-_Trailer_1_(HD)[WARB00000122].mkv".
Your input can't be opened:
VLC is unable to open the MRL 'file:/home/retrobadger/Azureus Downloads/17_Again_-_Trailer_1_(HD)[WARB00000122].mkv'. Check the log for details.
```

Now, if I load the media direct from Nautilus it loads fine, so I am unsure what is the problem exactly.

Any suggestions?
Dan

---

### Post by mc4man on 2009-04-13
Part of the problem may be the address in the .asx file

Ex. - doesn't open (default
<REF HREF="file:/home/doug/Azureus_Downloads/X-Men_Origins__Wolverine_-_Trailer_2_(HD)[FOX00000020].mkv"/>

Does open (added  //
<REF HREF="file:///home/doug/Azureus_Downloads/X-Men_Origins__Wolverine_-_Trailer_2_(HD)[FOX00000020].mkv"/>

The problem is vuze keeps changing it back to first ex.

What I did is edit the line and then in the properties of the .asx took away write permissions (read only, shows lock icon


what line did you change in defaults.list? (to set vlc, am assuming audio/x-ms-asx ( was thinking of maybe setting up a userapp.desktop instead, would allow files to be queued. (but not in defaults.list, re-editing the same line in there is trouble

---

### Post by retrodans on 2009-04-13
I changed pretty much all instances of totem to vlc as I wanted vlc as the default for many media types, but the line you mentioned now looks like:

```
audio/x-ms-asx=vlc.desktop
```

I changed the line in the .asx file, then set permissions to read only and this solved the problem.  I don't really want to be doing this for every file though, else I may as well just open directly from Nautilus.  Is there a way for it to do this automatically?

---

### Post by mc4man on 2009-04-13
> Is there a way for it to do this automatically?

Not sure, just tried vuze for this thread, will look thru the config options, file(?) later

Other possibilities are maybe a built .deb version would be patched for this (in repo or ppa ?

search page for ubuntu ppa's
[https://edge.launchpad.net/ubuntu/+ppas](https://edge.launchpad.net/ubuntu/+ppas)

---

