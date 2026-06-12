---
title: "DVD playback difficulty with Totem"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by ticopelp on 2007-05-14
So here's my problem. I'm trying to play a DVD movie in Totem on Feisty, and I keep getting this error message:

> "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

The thing is, I have libdvdcss installed. I followed the instructions on the Ubuntu Guide to Feisty to enable DVD playback. I even tried a bunch of different means of getting the necessary libraries, including Synaptic and the Medibuntu repositories. The same thing always happens. 

If it's helpful, I ran totem from the terminal, and this is what comes out when the error message occurs: 

```
(totem:15419): Gtk-WARNING **: Attempting to add `dvd:/' to the list of recently used resources, but not MIME type was defined
libdvdnav: Using dvdnav version 1.1.4 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/hdc mounted on /media/cdrom1 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/dan/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000014e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00006133
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001eb52a
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
libdvdnav: Using dvdnav version 1.1.4 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/hdc mounted on /media/cdrom1 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/dan/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000014e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00006133
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001eb52a
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0

```

This happens at about halfway through the film each time. I'm really stuck as to what else to try. I even attempted using gxine instead of mplayer, but it craps out at about the same time. 

It's an older DVD and doesn't seem like it would be copy-protected, although I guess it's certainly possible.

Any ideas?

---

### Post by rax_m on 2007-05-23
Hi.. Did you ever get this sorted out?
I seem to be having similar issues.

---

### Post by ticopelp on 2007-05-24
> **rax_m said:**
> Hi.. Did you ever get this sorted out?
I seem to be having similar issues.

Not really. I started using VLC instead of Totem, which is mildly more stable, but still craps out on me every once in a while. I guess I just have to live with it for now.

---

### Post by whistlerspa on 2007-05-24
Try this link - it worked for me

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

I wonder why the 'oneclick 'easy install optionm didn't work for this though - it has for other codecs and plugins? Perhaps it is ther non-free thing.

---

### Post by Bablefish on 2007-05-24
I have nothing against the guy who posted the way to open the !@#$ thing so Totem and other players can play DVDs or let alone Medibuntu and it's creators. But I have been trying since May 12 and I still can get any of those commands to work. In fact I had just given up today, and hope sometime in the future someone decides to make this feature easy to download as any program in the Add Remove programs feature

---

