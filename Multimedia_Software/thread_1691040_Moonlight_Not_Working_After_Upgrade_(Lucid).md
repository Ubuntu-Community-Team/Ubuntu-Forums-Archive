---
title: "Moonlight Not Working After Upgrade (Lucid)"
date: 2011-02-19
forum: Multimedia Software
---

### Post by woofti on 2011-02-19
I use Novell Moonlight to stream a television station.

Since my last updates, it refuses to stream the station.

[http://www.revelationtv.com/watch_now](http://www.revelationtv.com/watch_now)

I hope someone can help me fix this.

Ubuntu 10.04
Firefox 3.6.13
Novell Moonlight 3.99.0.1

Many thanks
woof

---

### Post by woofti on 2011-02-19
On another machine with the same OS and Firefox, the stream is fine. It just doesn't play on this machine. I suppose that's a bit crazy...

---

### Post by grizzler on 2011-02-19
When I tried the link, Moonlight showed an icon and after clicking that, a configuration panel. Turns out it needed an extra codec. Maybe that's the same problem?

Also Ubuntu 10.04, Firefox 3.6.13 and Moonlight 3.99.0.1.

---

### Post by woofti on 2011-02-20
I don't think that's the problem - as I said it was working fine right up until one of the more recent updates, now when you click the arrow to start playing, nothing much happens. On a Netbook that I've just renewed with a fresh install of Lucid, with all the most recent updates, and running the same Firefox, it works fine!

---

### Post by woofti on 2011-02-20
Output of terminal:

Moonlight: 3.99.0.1
Moonlight: Attempting to load libmoonloaderxpi 
debug_get_option: GALLIUM_DRIVER = softpipe
couldn't open libtxc_dxtn.so, software DXTn compression/decompression unavailable
Moonlight: no audio capture service available
Moonlight: Installing signal handlers for crash reporting.
Moonlight: Enabling MONO_DEBUG=keep-delegates,reverse-pinvoke-exceptions and MOONLIGHT_ENABLE_CONSOLE=1
Moonlight: Loaded mscodecs from: /home/richard/.mozilla/plugins/moonlight/silverlight-media-pack-linux-x86-21-1.so.
Using the ff3 bridge
Moonlight: Plugin AppDomain Creation: OK
Moonlight: URL = [http://www.revelationtv.com/watch_now](http://www.revelationtv.com/watch_now)
Moonlight: OpenGL vendor string: Tungsten Graphics, Inc
Moonlight: OpenGL renderer string: Mesa DRI Intel(R) IGDNG_M GEM 20091221 2009Q4 x86/MMX/SSE2
Moonlight: OpenGL version string: 2.1 Mesa 7.7.1
Moonlight: ErrorEventArgs created with message: 'AG_E_NETWORK_ERROR'
Moonlight: MediaError 4001 AG_E_NETWORK_ERROR (null)
Moonlight: ErrorEventArgs created with message: 'AG_E_NETWORK_ERROR'
EMIT OF EVENT Error(1) ON OBJECT Surface CALLED WITH NO LISTENERS AND NON-NULL CALLDATA

---

### Post by woofti on 2011-02-20
Strangely I can stream from [www.watchindia.tv](www.watchindia.tv)

But not from revelationtv.com/watch_now

???

---

### Post by grizzler on 2011-02-20
Probably far fetched, but you're not letting the Firefox add-on NoScript block revelationtv.com, are you?

---

### Post by woofti on 2011-02-21
No NoScript. It was working fine, then I upgraded (on 16th I believe), then on 17th I noticed I couldn't stream. I found out how to de-upgrade file after file to find the culprit but that's for another day.

---

