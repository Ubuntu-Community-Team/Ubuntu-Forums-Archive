---
title: "Stream mp4 video to HTTP with VLC"
date: 2012-10-22
forum: Multimedia Software
---

### Post by OzuYatamutsu on 2012-10-22
Hi!

I'm trying to stream a video to http with vlc on my headless Ubuntu Server box. I've stumbled across the following command:

cvlc video.mp4 :sout=#std{access=http,mux=ts,dst=0.0.0.0:8080}

Which always gives me the following error, no matter what port I try:

[0x7fce68000df8] main stream output error: stream chain failed for `stddst=0.0.0.0:8080'
[0x7fce64000b28] main input error: cannot start stream output instance, aborting

---

### Post by BicyclerBoy on 2012-10-22
I think the dst=0.0.0.0.0 has to be the server IP address or resolvable hostname.

On the client you use the server hostname or IP..

---

### Post by mabittenc on 2012-10-23
I used to streaming my webcam as mjpeg at kubuntu 12.04 (64), but after the upgrade to 12.10 it stops to work. It always says: 

[FONT=Courier New]VLC media player 2.0.4 Twoflower (revision 2.0.3-289-g6e6100a)
[0xe6e108] main libvlc: Executando o VLC com a interface padrão. Use 'cvlc' para usar o VLC sem interface.
[mjpeg @ 0x7f2b7801a5a0] a vbv buffer size is needed, for encoding with a maximum bitrate
**[0x7f2b78000e08] avcodec encoder error: cannot open encoder**
[0x7f2b98008878] stream_out_transcode stream out error: cannot find video encoder (module:any fourcc:MJPG). Take a look few lines earlier to see possible reason.
[0x7f2b98008878] stream_out_transcode stream out error: cannot create video chain
[0x7f2b9800bc48] main decoder error: cannot create packetizer output (MJPG)
[/FONT]
As you can see, vlc cannot find or open the encoder.
I use the following command:

[FONT=Courier New]vlc v4l2:///dev/video0 --sout='#transcode{threads=2,acodec=none,vcodec=MJPG,vb=1500,width=640,height=480,fps=10}:standard{mux=mpjpeg,access=http{mime=multipart/x-mixed-replace; boundary=--7b3cc56e5f51db803f790dad720ed50a},dst=:8080/sala.mjpeg}'
[/FONT]
At 12.04 the vlc version is "VLC media player 2.0.3 Twoflower (revision 2.0.2-93-g77aa89e)"

At 12.10 the vlc version is "VLC media player 2.0.4 Twoflower (revision 2.0.3-289-g6e6100a)"

[FONT=Courier New]$ vlc -l | grep jpeg
VLC media player 2.0.4 Twoflower (revision 2.0.3-289-g6e6100a)
  mjpeg                  Descombinador de câmera M-JPEG
  mux_mpjpeg             Misturador de múltiplas partes de um JPEG
[/FONT]
Anyone has an idea how to fix?

---

### Post by OzuYatamutsu on 2012-10-24
$ cvlc video.mp4 :sout=#std{access=http,mux=ts,dst=[myip]:8080}
VLC media player 2.0.3 Twoflower (revision 2.0.2-93-g77aa89e)
[0x25d59b8] inhibit interface error: Failed to connect to the D-Bus session daemon: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
[0x25d59b8] main interface error: no suitable interface module
[0x25d59b8] main interface error: no suitable interface module
[0x23b1108] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x25d59b8] dummy interface: using the dummy interface module...
[0x7f0840000e08] main stream output error: stream chain failed for `stddst=[myip]:8080'
[0x7f083c000b28] main input error: cannot start stream output instance, aborting

Still nothing yet :\

---

