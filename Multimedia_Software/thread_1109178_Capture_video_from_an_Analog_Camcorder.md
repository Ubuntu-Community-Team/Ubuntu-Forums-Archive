---
title: "Capture video from an Analog Camcorder"
date: 2009-03-28
forum: Multimedia Software
---

### Post by bbharatsony on 2009-03-28
I have figured out how to connect an analog camcorder/analog video camera to a computer. The connection to the computer is a USB and an audio connector. I don't know what application to use to be able to capture the video. The analog camcorder is connected as a digital video camera. The only difference is that it is connected using a USB connecter and an audio connecter. Can someone please give a good application for capturing video from my analog video camera with these limits.

---

### Post by Silvernail on 2009-03-28
I can not really help you in the way you ask, but let me share my recent experince.

I needed to download for an analog Sony Hi8 that was made before USB came out.

If you will  continue to search, there are several 'Howto's in the Ubuntuforms.

Heres what I wound up doing.

Connected my camera to my video capture card via a S-Video cable.
Connected my audio to the video capture card.

From  the terminal, enter the command line. 'vlc2-ctl -i 1',
this command line puts VLC2 to recieve S-Video, use a capital I (eye) to see what other choices you have.

Then enter  the command:  cat /dev/video0 > very long descritive name of you movie.avi

Go make a cup of tea.

---

