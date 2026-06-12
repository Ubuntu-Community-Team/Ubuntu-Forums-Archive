---
title: "Problems Playing Streaming videos in Firefox with ubuntu x86_x64"
date: 2009-01-22
forum: Multimedia Software
---

### Post by nmarcell on 2009-01-22
No matter what I do I can't play Windows Media and some other video streams in my Firefox Web Browser although I have GStreamer, mplayer plugin, vlc plugin, w64codecs, etc. installed. Here's what the terminal says:

** Message: NP_Initialize
** Message: NP_Initialize succeeded
** Message: totemPlugin [0x366e810]
** Message: Init mimetype 'application/x-mplayer2' mode 1
** Message: GetScriptableNPObject [0x366e810]
** Message: totemGMPPlayer [0x366ea40]
** Message: Base URI is 'http://www.missglad.com/webtv/webtv-true.php?categ_id=212&video=9d550f2d8f'
** Message: Real mimetype for 'application/x-mplayer2' is 'video/x-msvideo'
argv[0] type application/x-mplayer2
argv[1] name MediaPlayer
argv[2] pluginspage [http://www.microsoft.com/windows/windowsmedia/download/](http://www.microsoft.com/windows/windowsmedia/download/)
argv[3] src [http://www.missglad.com/webtv/jumptv.php?channel=Hard01&TICKET=fce2cc5d7b6e8768d404ae0faa89c390%7C1232654596%7C10%7C81.183.48.160%7Canonymoususer%7C15%7C0%7C0](http://www.missglad.com/webtv/jumptv.php?channel=Hard01&TICKET=fce2cc5d7b6e8768d404ae0faa89c390%7C1232654596%7C10%7C81.183.48.160%7Canonymoususer%7C15%7C0%7C0)
argv[4] autostart true
argv[5] autosize true
argv[6] showcontrols 1
argv[7] showdisplay 0
argv[8] volume 100
argv[9] enablecontextmenu 0
argv[10] stretchtofit 1
argv[11] showstatusbar 0
argv[12] height 360
argv[13] width 480
** Message: Stream requested (force viewer: 0)
** Message: mSrcURI: [http://www.missglad.com/webtv/jumptv.php?channel=Hard01&TICKET=fce2cc5d7b6e8768d404ae0faa89c390%7C1232654596%7C10%7C81.183.48.160%7Canonymoususer%7C15%7C0%7C0](http://www.missglad.com/webtv/jumptv.php?channel=Hard01&TICKET=fce2cc5d7b6e8768d404ae0faa89c390%7C1232654596%7C10%7C81.183.48.160%7Canonymoususer%7C15%7C0%7C0)
** Message: mCache: 0
** Message: mControllerHidden: 0
** Message: mShowStatusbar: 0
** Message: mHidden: 0
** Message: mAudioOnly: 0
** Message: mAutoPlay: 1, mRepeat: 0
** Message: Launching: /usr/lib/totem/gstreamer/totem-plugin-viewer --plugin-type gmp --user-agent Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.5) Gecko/2008121623 Ubuntu/8.10 (intrepid) Firefox/3.0.5 --mimetype video/x-msvideo 
** Message: Viewer spawned, PID 10891
** Message: Initial window set, XID 3c03280 size 480x360
** Message: No viewer proxy yet, deferring SetWindow
** Message: GetScriptableNPObject [0x366e810]
** Message: Viewer DBus interface name is 'org.gnome.totem.PluginViewer_10891'
** Message: NameOwnerChanged old-owner '' new-owner ':1.9'
** Message: Viewer now connected to the bus
** Message: ViewerSetup
** Message: Calling SetWindow
Viewer: SetWindow XID 62927488 size 480:360
** Message: NewStream mimetype 'video/x-ms-asf' URL 'http://www.missglad.com/webtv/jumptv.php?channel=Hard01&TICKET=fce2cc5d7b6e8768d404ae0faa89c390%7C1232654596%7C10%7C81.183.48.160%7Canonymoususer%7C15%7C0%7C0'
** Message: Not expecting a new stream; aborting stream
TotemEmbedded-Message: Viewer state: STOPPED
** Message: SetWindow reply
** Message: ViewerReady
** Message: Stream requested (force viewer: 0)
** Message: IsSchemeSupported scheme 'http': yes
TotemEmbedded-Message: totem_embedded_open_stream called: uri [http://www.missglad.com/webtv/jumptv.php?channel=Hard01&TICKET=fce2cc5d7b6e8768d404ae0faa89c390%7C1232654596%7C10%7C81.183.48.160%7Canonymoususer%7C15%7C0%7C0](http://www.missglad.com/webtv/jumptv.php?channel=Hard01&TICKET=fce2cc5d7b6e8768d404ae0faa89c390%7C1232654596%7C10%7C81.183.48.160%7Canonymoususer%7C15%7C0%7C0), base_uri: [http://www.missglad.com/webtv/webtv-true.php?categ_id=212&video=9d550f2d8f](http://www.missglad.com/webtv/webtv-true.php?categ_id=212&video=9d550f2d8f)
totem_embedded_set_uri uri (null) base (null) => resolved (null)
totem_embedded_set_uri uri [http://www.missglad.com/webtv/jumptv.php?channel=Hard01&TICKET=fce2cc5d7b6e8768d404ae0faa89c390%7C1232654596%7C10%7C81.183.48.160%7Canonymoususer%7C15%7C0%7C0](http://www.missglad.com/webtv/jumptv.php?channel=Hard01&TICKET=fce2cc5d7b6e8768d404ae0faa89c390%7C1232654596%7C10%7C81.183.48.160%7Canonymoususer%7C15%7C0%7C0) base [http://www.missglad.com/webtv/webtv-true.php?categ_id=212&video=9d550f2d8f](http://www.missglad.com/webtv/webtv-true.php?categ_id=212&video=9d550f2d8f) => resolved [http://www.missglad.com/webtv/jumptv.php?channel=Hard01&TICKET=fce2cc5d7b6e8768d404ae0faa89c390%7C1232654596%7C10%7C81.183.48.160%7Canonymoususer%7C15%7C0%7C0](http://www.missglad.com/webtv/jumptv.php?channel=Hard01&TICKET=fce2cc5d7b6e8768d404ae0faa89c390%7C1232654596%7C10%7C81.183.48.160%7Canonymoususer%7C15%7C0%7C0)
TotemEmbedded-Message: totem_embedded_open_internal 'fd://0' is-browser-stream 1 start-play 1
TotemEmbedded-Message: BEFORE _open

(totem-plugin-viewer:10891): GLib-CRITICAL **: g_strrstr: assertion `haystack != NULL' failed

** (totem-plugin-viewer:10891): WARNING **: cannot set NULL uri
TotemEmbedded-Message: AFTER _open (ret: 1)

** (totem-plugin-viewer:10891): CRITICAL **: bacon_video_widget_play: assertion `bvw->com->mrl != NULL' failed
** Message: NameOwnerChanged old-owner ':1.9' new-owner ''
** Message: Viewer lost connection!
** Message: OpenStream reply

** (firefox:10791): WARNING **: OpenStream failed: Message did not receive a reply (timeout by message bus)


I'd be very glad if someone could help me with my problem, it's very annoying.

---

