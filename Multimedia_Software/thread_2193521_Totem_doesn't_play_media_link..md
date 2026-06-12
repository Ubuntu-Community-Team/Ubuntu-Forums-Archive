---
title: "Totem doesn't play media link."
date: 2013-12-13
forum: Multimedia Software
---

### Post by monkeybrain20122 on 2013-12-13
[http://www.ciut.fm/listen-now/](http://www.ciut.fm/listen-now/)

Check out the the media player link on the page.

[http://www.caribbean-radio.com/ciut/ciut.asx](http://www.caribbean-radio.com/ciut/ciut.asx)

mplayer (gecko-mediaplayer) plays it, vlc plays it but not totem. You can download the .asx file and play outside of the webbroser, Again anything based on mplayer plays it, vlc plays it but not totem.

But in other distros I have tried (Debian sid, Fedora, Manjaro) Totem plays the .asx file immediately. It is the same version of Totem (3.8.2) and the gstreamer backend has the same versions too apparently. It seems that Totem and gstreamer are broken in Ubuntu and in Ubuntu only (maybe Debian proper as well, I installed everything multimedia in Debian from deb-multimedia). I have installed all obvious Totem and gstreamer plugins and still it wouldn't play. In fact it has never been able to play it since 10.04 (it worked in 10.04, at least for the 6 months that I used it)

I tried to play the downlaoded .asx file with totem in the terminal but there is no error message.  I am wondering if there is a way to find out what's wrong. It just bugs me when things are broken. :)

---

### Post by mc4man on 2013-12-13
works fine here in totem, screen

---

### Post by monkeybrain20122 on 2013-12-13
Hmm.. Interesting. I have not modified Totem in anyway, just right from the repo. But it has never worked on any of my Ubuntu release. Is there any way that I can get some error message? Totem just says "stopped" on the status.

Thanks

Can someone else try it as well and see if that works?


Edited: It doesn't work in guest session either, so it is not my local configuration.

---

### Post by Yellow Pasque on 2013-12-13
Can you give output of gst-instpect command?:
```
sudo apt-get install gstreamer1.0-tools
gst-inspect1.0 | grep -i asf
```

---

### Post by monkeybrain20122 on 2013-12-13
Hi, here are the outputs

```
$ gst-inspect-1.0 | grep -i asf
asfmux:  asfparse: ASF parser
asfmux:  rtpasfpay: RTP ASF payloader
asfmux:  asfmux: ASF muxer
libav:  avmux_asf_stream: libav ASF format muxer (not recommended, use asfmux instead)
libav:  avmux_asf: libav ASF format muxer (not recommended, use asfmux instead)
asf:  rtpasfdepay: RTP ASF packet depayloader
asf:  rtspwms: WMS RTSP Extension
asf:  asfdemux: ASF Demuxer
typefindfunctions: video/x-ms-asf: asf, wm, wma, wmv
```

---

### Post by monkeybrain20122 on 2013-12-14
This is odd. In Fedora totem plays the asx 10 out of 10 times. But trying to play it with gstreamer command

```
gst-launch-1.0 playbin uri=file:///home/username/ciut.asx 

```
did not work
```

Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
ERROR: from element /GstPlayBin:playbin0/GstURIDecodeBin:uridecodebin0/GstDecodeBin:decodebin0/GstTypeFindElement:typefind: Could not determine type of stream.
Additional debug info:
gsttypefindelement.c(1044): gst_type_find_element_loop (): /GstPlayBin:playbin0/GstURIDecodeBin:uridecodebin0/GstDecodeBin:decodebin0/GstTypeFindElement:typefind
ERROR: pipeline doesn't want to preroll.
Setting pipeline to NULL ...
Freeing pipeline
```

Mybe this is not the correct command, or am I missing some options?

---

### Post by mc4man on 2013-12-14
does this work? (around now, sometimes it seems the connection to that stream is poor...
gst-launch-1.0 playbin uri=http://128.100.197.46:80/

---

### Post by monkeybrain20122 on 2013-12-14
> **mc4man said:**
> does this work? (around now, sometimes it seems the connection to that stream is poor...
gst-launch-1.0 playbin uri=http://128.100.197.46:80/

Yes! This works! I am wondering why gst-launch doesn't  work on the downloaded asx file (even in distros where totem does work).:roll: 

Totem still doesn't work in Ubuntu and I have tried both the firefox plugin and the downloaded asx.

---

### Post by kostkon on 2013-12-14
> **monkeybrain20122 said:**
> Yes! This works! I am wondering why gst-launch doesn't  work on the downloaded asx file (even in distros where totem does work).:roll: 

Totem still doesn't work in Ubuntu and I have tried both the firefox plugin and the downloaded asx.
You could try installing ubuntu-restricted-extras; It will pull all the gstreamer plugin packages.

---

### Post by monkeybrain20122 on 2013-12-14
Ubuntu-restricted-extras is installed, as are all the good bad ugly plugins.

---

### Post by mikelavekkia on 2013-12-14
use vlc and install Ubuntu-restricted-extras

---

### Post by monkeybrain20122 on 2013-12-14
> **mikelavekkia said:**
> use vlc and install Ubuntu-restricted-extras

No offence, but did you actually read my posts?

---

### Post by mc4man on 2013-12-14
The one thing I did notice is that when using totem on your link it takes considerably longer to start up (buffer) then any other way
(gst-launch...  2-3 sec, vlc 3 - 4 sec, mpv   2 sec,  totem  10 -12 sec
Maybe totem is timing out on you?, hard to say as totem doesn't provide much as far as debugging or verbosity (totem --help-all

---

### Post by monkeybrain20122 on 2013-12-14
I try to use totem --debug to play the .asx file but it shows nothing even though file doesn't play. The gui just says stopped. I was waiting for 10 minutes that should be long enough (actually it says "stopped" right after it launches, so doesn't seem like timing out)

---

### Post by monkeybrain20122 on 2013-12-14
Running totem --gst-debug-level=4 ~/ciut.asx gives these outputs..

```
totem --gst-debug-level=4 ~/ciut.asx
0:00:00.001321957  7487 0x7f31d7d40350 INFO                GST_INIT gstmessage.c:123:_priv_gst_message_initialize: init messages
0:00:00.005340622  7487 0x7f31d7d40350 INFO                GST_INIT gstcontext.c:77:_priv_gst_context_initialize: init contexts
0:00:00.006128920  7487 0x7f31d7d40350 INFO      GST_PLUGIN_LOADING gstplugin.c:317:_priv_gst_plugin_initialize: registering 0 static plugins
0:00:00.006603562  7487 0x7f31d7d40350 INFO      GST_PLUGIN_LOADING gstplugin.c:225:gst_plugin_register_static: registered static plugin "staticelements"
0:00:00.006786825  7487 0x7f31d7d40350 INFO      GST_PLUGIN_LOADING gstplugin.c:227:gst_plugin_register_static: added static plugin "staticelements", result: 1
0:00:00.006950603  7487 0x7f31d7d40350 INFO            GST_REGISTRY gstregistry.c:1680:ensure_current_registry: reading registry cache: /home/bee/.cache/gstreamer-1.0/registry.x86_64.bin
0:00:00.042215353  7487 0x7f31d7d40350 INFO            GST_REGISTRY gstregistrybinary.c:617:priv_gst_registry_binary_read_cache: loaded /home/bee/.cache/gstreamer-1.0/registry.x86_64.bin in 0.035102 seconds
0:00:00.042376197  7487 0x7f31d7d40350 INFO            GST_REGISTRY gstregistry.c:1539:scan_and_update_registry: Validating plugins from registry cache: /home/bee/.cache/gstreamer-1.0/registry.x86_64.bin
0:00:00.044412910  7487 0x7f31d7d40350 INFO            GST_REGISTRY gstregistry.c:1638:scan_and_update_registry: Registry cache has not changed
0:00:00.044477513  7487 0x7f31d7d40350 INFO            GST_REGISTRY gstregistry.c:1715:ensure_current_registry: registry reading and updating done, result = 1
0:00:00.044503704  7487 0x7f31d7d40350 INFO                GST_INIT gst.c:707:init_post: GLib runtime version: 2.38.1
0:00:00.044527799  7487 0x7f31d7d40350 INFO                GST_INIT gst.c:709:init_post: GLib headers version: 2.38.0
0:00:00.664313805  7487 0x7f31d7d40350 INFO      GST_PLUGIN_LOADING gstplugin.c:225:gst_plugin_register_static: registered static plugin "cluttersink"
0:00:00.664379945  7487 0x7f31d7d40350 INFO      GST_PLUGIN_LOADING gstplugin.c:227:gst_plugin_register_static: added static plugin "cluttersink", result: 1
0:00:00.667469304  7487 0x7f31d7d40350 INFO      GST_PLUGIN_LOADING gstplugin.c:830:gst_plugin_load_file: plugin "/usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstplayback.so" loaded
0:00:00.667560517  7487 0x7f31d7d40350 INFO     GST_ELEMENT_FACTORY gstelementfactory.c:363:gst_element_factory_create: creating element "playbin" named "play"
0:00:00.669223929  7487 0x7f31d7d40350 INFO      GST_PLUGIN_LOADING gstplugin.c:830:gst_plugin_load_file: plugin "/usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstaudioconvert.so" loaded
0:00:00.669323452  7487 0x7f31d7d40350 INFO     GST_ELEMENT_FACTORY gstelementfactory.c:363:gst_element_factory_create: creating element "audioconvert" named "audio-converter"
0:00:00.669598627  7487 0x7f31d7d40350 INFO        GST_ELEMENT_PADS gstelement.c:646:gst_element_add_pad:<GstBaseTransform@0x7f31d8652b60> adding pad 'sink'
0:00:00.669680062  7487 0x7f31d7d40350 INFO        GST_ELEMENT_PADS gstelement.c:646:gst_element_add_pad:<GstBaseTransform@0x7f31d8652b60> adding pad 'src'
0:00:00.671315185  7487 0x7f31d7d40350 INFO      GST_PLUGIN_LOADING gstplugin.c:830:gst_plugin_load_file: plugin "/usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstaudiofx.so" loaded
0:00:00.671384398  7487 0x7f31d7d40350 INFO     GST_ELEMENT_FACTORY gstelementfactory.c:363:gst_element_factory_create: creating element "scaletempo" named "scaletempo"
0:00:00.671541541  7487 0x7f31d7d40350 INFO        GST_ELEMENT_PADS gstelement.c:646:gst_element_add_pad:<GstBaseTransform@0x7f31d8658190> adding pad 'sink'
0:00:00.671591058  7487 0x7f31d7d40350 INFO        GST_ELEMENT_PADS gstelement.c:646:gst_element_add_pad:<GstBaseTransform@0x7f31d8658190> adding pad 'src'
0:00:00.671626747  7487 0x7f31d7d40350 INFO     GST_ELEMENT_FACTORY gstelementfactory.c:363:gst_element_factory_create: creating element "cluttersink" named "video-sink"
0:00:00.671905134  7487 0x7f31d7d40350 INFO        GST_ELEMENT_PADS gstelement.c:646:gst_element_add_pad:<GstBaseSink@0x7f31d865a8f0> adding pad 'sink'
0:00:00.671990620  7487 0x7f31d7d40350 INFO             cluttersink ./clutter-gst-video-sink.c:1269:clutter_gst_build_renderers_list: GL features: 0x00000007
0:00:00.672702442  7487 0x7f31d7d40350 INFO      GST_PLUGIN_LOADING gstplugin.c:830:gst_plugin_load_file: plugin "/usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstautodetect.so" loaded
0:00:00.672776194  7487 0x7f31d7d40350 INFO     GST_ELEMENT_FACTORY gstelementfactory.c:363:gst_element_factory_create: creating element "autoaudiosink" named "audio-sink"
0:00:00.672949051  7487 0x7f31d7d40350 INFO        GST_ELEMENT_PADS gstelement.c:646:gst_element_add_pad:<GstAutoAudioSink@0x7f31d86ce020> adding pad 'sink'
0:00:00.673991571  7487 0x7f31d7d40350 INFO      GST_PLUGIN_LOADING gstplugin.c:830:gst_plugin_load_file: plugin "/usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstcoreelements.so" loaded
0:00:00.674045628  7487 0x7f31d7d40350 INFO     GST_ELEMENT_FACTORY gstelementfactory.c:363:gst_element_factory_create: creating element "fakesink" named "tempsink"
0:00:00.674570905  7487 0x7f31d7d40350 INFO        GST_ELEMENT_PADS gstelement.c:646:gst_element_add_pad:<GstBaseSink@0x7f31d864da00> adding pad 'sink'
0:00:00.674668683  7487 0x7f31d7d40350 INFO        GST_ELEMENT_PADS gstelement.c:897:gst_element_get_static_pad: found pad tempsink:sink
0:00:00.674708981  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:2083:gst_pad_link_prepare: trying to link sink:proxypad0 and tempsink:sink
0:00:00.674741527  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:2285:gst_pad_link_full: linked sink:proxypad0 and tempsink:sink, successful
0:00:00.674771559  7487 0x7f31d7d40350 INFO               GST_EVENT gstevent.c:1313:gst_event_new_reconfigure: creating reconfigure event
0:00:00.690124283  7487 0x7f31d7d40350 INFO                 playbin gstplaybin2.c:2188:gst_play_bin_set_sink:<play> Setting video sink to <video-sink>
0:00:00.690346238  7487 0x7f31d7d40350 INFO     GST_ELEMENT_FACTORY gstelementfactory.c:363:gst_element_factory_create: creating element "capsfilter" named "audiofilter"
0:00:00.691501344  7487 0x7f31d7d40350 INFO        GST_ELEMENT_PADS gstelement.c:646:gst_element_add_pad:<GstBaseTransform@0x7f31d86fa150> adding pad 'sink'
0:00:00.694008507  7487 0x7f31d7d40350 INFO        GST_ELEMENT_PADS gstelement.c:646:gst_element_add_pad:<GstBaseTransform@0x7f31d86fa150> adding pad 'src'
0:00:00.694060818  7487 0x7f31d7d40350 INFO     GST_ELEMENT_FACTORY gstelementfactory.c:363:gst_element_factory_create: creating element "bin" named "audiosinkbin"
0:00:00.694155313  7487 0x7f31d7d40350 INFO        GST_ELEMENT_PADS gstutils.c:1543:gst_element_link_pads_full: trying to link element audiofilter:(any) to element scaletempo:(any)
0:00:00.694189256  7487 0x7f31d7d40350 INFO                GST_PADS gstutils.c:936:gst_pad_check_link: trying to link audiofilter:src and scaletempo:sink
0:00:00.694240799  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:3626:gst_pad_peer_query:<audiofilter:sink> pad has no peer
0:00:00.694282564  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:3626:gst_pad_peer_query:<scaletempo:src> pad has no peer
0:00:00.694340462  7487 0x7f31d7d40350 INFO                GST_PADS gstutils.c:1443:prepare_link_maybe_ghosting: audiofilter and scaletempo in same bin, no need for ghost pads
0:00:00.694383275  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:2083:gst_pad_link_prepare: trying to link audiofilter:src and scaletempo:sink
0:00:00.694412748  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:3626:gst_pad_peer_query:<audiofilter:sink> pad has no peer
0:00:00.694440195  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:3626:gst_pad_peer_query:<scaletempo:src> pad has no peer
0:00:00.694484475  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:2285:gst_pad_link_full: linked audiofilter:src and scaletempo:sink, successful
0:00:00.694511992  7487 0x7f31d7d40350 INFO               GST_EVENT gstevent.c:1313:gst_event_new_reconfigure: creating reconfigure event
0:00:00.694534551  7487 0x7f31d7d40350 INFO               GST_EVENT gstpad.c:5033:gst_pad_send_event_unchecked:<audiofilter:src> Received event on flushing pad. Discarding
0:00:00.694575408  7487 0x7f31d7d40350 INFO        GST_ELEMENT_PADS gstutils.c:1543:gst_element_link_pads_full: trying to link element scaletempo:(any) to element audio-converter:(any)
0:00:00.694607046  7487 0x7f31d7d40350 INFO                GST_PADS gstutils.c:936:gst_pad_check_link: trying to link scaletempo:src and audio-converter:sink
0:00:00.694641687  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:3626:gst_pad_peer_query:<audiofilter:sink> pad has no peer
0:00:00.694692741  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:3626:gst_pad_peer_query:<audio-converter:src> pad has no peer
0:00:00.694740652  7487 0x7f31d7d40350 INFO               structure gststructure.c:2853:gst_structure_get_valist: Expected field 'channel-mask' in structure: audio/x-raw, rate=(int)[ 1, 2147483647 ], channels=(int)[ 1, 2147483647 ], layout=(string)interleaved;
0:00:00.695068487  7487 0x7f31d7d40350 INFO                GST_PADS gstutils.c:1443:prepare_link_maybe_ghosting: scaletempo and audio-converter in same bin, no need for ghost pads
0:00:00.695151738  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:2083:gst_pad_link_prepare: trying to link scaletempo:src and audio-converter:sink
0:00:00.695206563  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:3626:gst_pad_peer_query:<audiofilter:sink> pad has no peer
0:00:00.695281991  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:3626:gst_pad_peer_query:<audio-converter:src> pad has no peer
0:00:00.695347921  7487 0x7f31d7d40350 INFO               structure gststructure.c:2853:gst_structure_get_valist: Expected field 'channel-mask' in structure: audio/x-raw, rate=(int)[ 1, 2147483647 ], channels=(int)[ 1, 2147483647 ], layout=(string)interleaved;
0:00:00.698040160  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:2285:gst_pad_link_full: linked scaletempo:src and audio-converter:sink, successful
0:00:00.698090795  7487 0x7f31d7d40350 INFO               GST_EVENT gstevent.c:1313:gst_event_new_reconfigure: creating reconfigure event
0:00:00.698117474  7487 0x7f31d7d40350 INFO               GST_EVENT gstpad.c:5033:gst_pad_send_event_unchecked:<scaletempo:src> Received event on flushing pad. Discarding
0:00:00.698157284  7487 0x7f31d7d40350 INFO        GST_ELEMENT_PADS gstutils.c:1543:gst_element_link_pads_full: trying to link element audio-converter:(any) to element audio-sink:(any)
0:00:00.698193322  7487 0x7f31d7d40350 INFO                GST_PADS gstutils.c:936:gst_pad_check_link: trying to link audio-converter:src and audio-sink:sink
0:00:00.698235436  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:3626:gst_pad_peer_query:<audiofilter:sink> pad has no peer
0:00:00.698309957  7487 0x7f31d7d40350 INFO               structure gststructure.c:2853:gst_structure_get_valist: Expected field 'channel-mask' in structure: audio/x-raw, rate=(int)[ 1, 2147483647 ], channels=(int)[ 1, 2147483647 ], layout=(string)interleaved;
0:00:00.698445449  7487 0x7f31d7d40350 INFO                GST_PADS gstutils.c:1443:prepare_link_maybe_ghosting: audio-converter and audio-sink in same bin, no need for ghost pads
0:00:00.698491125  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:2083:gst_pad_link_prepare: trying to link audio-converter:src and audio-sink:sink
0:00:00.698530865  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:3626:gst_pad_peer_query:<audiofilter:sink> pad has no peer
0:00:00.698600357  7487 0x7f31d7d40350 INFO               structure gststructure.c:2853:gst_structure_get_valist: Expected field 'channel-mask' in structure: audio/x-raw, rate=(int)[ 1, 2147483647 ], channels=(int)[ 1, 2147483647 ], layout=(string)interleaved;
0:00:00.698689894  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:2285:gst_pad_link_full: linked audio-converter:src and audio-sink:sink, successful
0:00:00.698717341  7487 0x7f31d7d40350 INFO               GST_EVENT gstevent.c:1313:gst_event_new_reconfigure: creating reconfigure event
0:00:00.698739621  7487 0x7f31d7d40350 INFO               GST_EVENT gstpad.c:5033:gst_pad_send_event_unchecked:<audio-converter:src> Received event on flushing pad. Discarding
0:00:00.698769583  7487 0x7f31d7d40350 INFO        GST_ELEMENT_PADS gstelement.c:897:gst_element_get_static_pad: found pad audiofilter:sink
0:00:00.698828948  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:2083:gst_pad_link_prepare: trying to link sink:proxypad1 and audiofilter:sink
0:00:00.698855138  7487 0x7f31d7d40350 INFO                GST_PADS gstpad.c:2285:gst_pad_link_full: linked sink:proxypad1 and audiofilter:sink, successful
0:00:00.698877487  7487 0x7f31d7d40350 INFO               GST_EVENT gstevent.c:1313:gst_event_new_reconfigure: creating reconfigure event
0:00:00.698905703  7487 0x7f31d7d40350 INFO        GST_ELEMENT_PADS gstelement.c:646:gst_element_add_pad:<audiosinkbin> adding pad 'sink'
0:00:00.698942300  7487 0x7f31d7d40350 INFO                 playbin gstplaybin2.c:2188:gst_play_bin_set_sink:<play> Setting audio sink to <audiosinkbin>
0:00:00.717428873  7487 0x7f31d7d40350 INFO                   totem bacon-video-widget-gst-missing-plugins.c:346:bacon_video_widget_gst_missing_plugins_setup: Set up support for automatic missing plugin installation
0:00:00.860983301  7487 0x7f31d7d40350 FIXME                    bin gstbin.c:4008:gst_bin_query: implement duration caching in GstBin again
0:00:00.861069136  7487 0x7f31d7d40350 FIXME                    bin gstbin.c:4008:gst_bin_query: implement duration caching in GstBin again
0:00:00.882555106  7487 0x7f31d7d40350 INFO              GST_STATES gstbin.c:1827:gst_bin_get_state_func:<play> getting state
0:00:00.883010961  7487 0x7f31d7d40350 FIXME                    bin gstbin.c:4008:gst_bin_query: implement duration caching in GstBin again
0:00:00.883054402  7487 0x7f31d7d40350 FIXME                    bin gstbin.c:4008:gst_bin_query: implement duration caching in GstBin again

```

---

### Post by mc4man on 2013-12-15
Don't think gst debug matters much here. 
In somewhat the  same vein,  if on 13.10 maybe upgrade to the libsoup I've got here, probably won't help but won't hurt.
[https://launchpad.net/~mc3man/+archive/rbaudiocd-fix](https://launchpad.net/~mc3man/+archive/rbaudiocd-fix)

---

### Post by monkeybrain20122 on 2013-12-15
Hi, 

Updated libsoup from your ppa and it works right the way! I have no idea where that comes from as totem basically doesn't give any debugging info.
Your fix should be incorporated into 14.04.

Thank you very much for the great work! 

P.S. I notice that your other ppa has something called totem-grilo, what is it about?

---

### Post by mc4man on 2013-12-25
> **monkeybrain20122 said:**
> 
P.S. I notice that your other ppa has something called totem-grilo, what is it about?
That is a grilo plugin enabled totem, something Ubuntu has been hemming & hawing about for some time now.

The grilo plugins in totem range from ok to broken with some in-between. (the youtube search & browse are an ex. of in-between, some vids play, some don't. The reason there is grilo doesn't fix changes in a timely manner, VeVo vids are an. ex. of what doesn't play, ect.
(if inclined to try after upgrade then grilo-plugins aren't auto installed so you need to do that yourself

There is also some issues with icon size in sidebar getting really big on occasion, usually a restart of totem fixes (works better in that regard in a gnome-shell session

Haven't decided whether to pursue on 14.04 if not enabled by Ubuntu - did just set up in my trusty -proposed, took adding 2 sources & adjusting libtotem-pl-parser to get some of the plugins to work...
(screen example of the "browse" view, > apple trailers

---

