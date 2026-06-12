---
title: "can no longer stream movies at divx.com"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by daverich on 2007-07-04
this is weird.

I can no longer stream movies from divx.com but i can download them and then watch them fine in totem.

i've uploaded a screenshot of what happens.

The only thing i've done recently is uninstalled compiz-fusion, but I can't imagine that caused this? - either way, anyone got any ideas?

it'd be nice to preview Bottom episodes before downloading.

Kind regards

Dave Rich

---

### Post by shavenlunatic on 2007-07-04
last time i had an issue with it.. deleting the contents of the .xine folder  (usually just catalog.cache) fixed it

i have no idea why this worked as it makes no sense.. but it did :)

---

### Post by nebhead on 2007-07-05
wow.... i'm not alone, exactly the same thing is happening to me, its rather annoying, and i have to download the movie to play it back. i use totem in firefox also. anyone know whats wrong?

---

### Post by tuxcantfly on 2007-07-05
Same problem here too... the solution by shavenlunatic didn't work for me, and I have this problem with both totem-gstreamer and totem-xine, though mozilla-mplayer works for me... Also, like daverich, I tried out compiz-fusion recently (and it still worked then), though I removed it and reverted back to metacity, and it doesn't work (though I don't think that's the cause of the problem, since I don't know exactly when the problem emerged)... However if you need a quick fix, this will do the job: [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

---

### Post by tuxcantfly on 2007-07-05
here's the output on the terminal, if anybody needs it... seems like something with dbus to me...

```
** Message: NP_Initialize
** Message: NP_Initialize succeeded
** Message: totemPlugin ctor [0x93d1db8]
** Message: Init mimetype 'video/divx' mode 1
** Message: Base URI is 'http://stage6.divx.com/'
** Message: Real mimetype for 'video/divx' is 'video/x-msvideo'
argv[0] id divx-plugin1354830
argv[1] type video/divx
argv[2] pluginspage http://go.divx.com/plugin/download/
argv[3] showpostplaybackad false
argv[4] statuscallback dv.status_callback
argv[5] custommode Stage6
argv[6] disabledimmer true
argv[7] movietitle Apples & Oranges Trailer
argv[8] height 384
argv[9] width 645
** Message: mSrc: 
** Message: mCache: 0
** Message: mControllerHidden: 0
** Message: mShowStatusbar: 0
** Message: mHidden: 0
** Message: mAudioOnly: 0
** Message: mAutostart: 1, mRepeat: 0
** Message: Launching: /usr/lib/totem/totem-plugin-viewer --plugin-type mully --user-agent Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty) --mimetype video/x-msvideo 
** Message: Viewer spawned, PID 6240
** Message: GetValue variable 14 (e)
** Message: Initial window set, XID 260163d size 645x384
** Message: No viewer proxy yet, deferring SetWindow
** Message: GetValue variable 15 (f)
** Message: Unhandled variable NPPVpluginScriptableNPObject
** Message: GetValue variable 11 (b)
** Message: GetValue variable 268435466 (1000000a)
** Message: GetScriptable [0x93d1db8]
** Message: totemMullYPlugin ctor [0xa64d9b8]
** Message: GetValue variable 15 (f)
** Message: Unhandled variable NPPVpluginScriptableNPObject
** Message: GetValue variable 11 (b)
** Message: GetValue variable 268435466 (1000000a)
** Message: GetScriptable [0x93d1db8]
** Message: Viewer DBus interface name is 'org.gnome.totem.PluginViewer_6240'
** Message: NameOwnerChanged old-owner '' new-owner ':1.27'
** Message: Viewer now connected to the bus
** Message: ViewerSetup
** Message: Calling SetWindow
** Message: NameOwnerChanged old-owner '' new-owner ':1.27'
** Message: Already have owner, why are we notified again?
Viewer: SetWindow XID 39851581 size 645:384
** Message: Viewer state: STOPPED
** Message: SetWindow reply
** Message: ViewerReady
```

---

### Post by skaboss on 2007-07-06
Hello,
I have the same problem. Divx streams used to work perfectly until 2 or 3 days ago...

---

### Post by tuxcantfly on 2007-07-13
for some reason, it's now suddenly working as usual in totem... might've been the latest slew of feisty updates...

---

