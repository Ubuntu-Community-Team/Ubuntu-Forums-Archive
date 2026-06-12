---
title: "Bluetooth A2DP headphones with Banshee"
date: 2008-11-13
forum: Multimedia Software
---

### Post by hill33love on 2008-11-13
Hello,everyone
Recently I use Bluetooth A2DP headphones to listen to music
The Player is banshee.
I can use a button to switch Bluetooth headset to built-in computer speakers by activating a script.



#!/bin/bash

state=`gconftool --get /system/gstreamer/0.10/default/musicaudiosink | cut -d\  -f1`

if [ $state == "autoaudiosink" ]; then
  gconftool --type string --set /system/gstreamer/0.10/default/musicaudiosink "alsasink device=bluetooth"
  zenity --info --title="GStreamer" --text="Switched to Bluetooth headphones."
else
  gconftool --type string --set /system/gstreamer/0.10/default/musicaudiosink "autoaudiosink"
  zenity --info --title="GStreamer" --text="Switched to speaker output."
fi

echo musicaudiosink set to `gconftool --get /system/gstreamer/0.10/default/musicaudiosink`


However, this function can not switch in time.
It switches to another output either by broadcasting to the next song or by pressing the button of PLAY.
The structure of audio is as follows.


&#9632;Audio

 ----------------------------------------------------------
&#9474;Application                                             &#9474;
&#9474;                       Banshee    Amarok                &#9474;
&#9474;                          &#8595;                             &#9474;
 ----------------------------------------------------------
&#9474;Desktop Environment                                     &#9474;
&#9474;                     &#8595;             &#8595;            &#8595;    &#9474;           
&#9474;                   GNOME            KDE          XFCE   &#9474;    
&#9474;                                                        &#9474;
--------------------------DBus----------------------------
&#9474;                                                        &#9474;
---------------------------------------------------------- GStreamer framework
&#9474;Sound Server                                            &#9474;
&#9474;                     &#8595;             &#8595;                    &#9474;
&#9474;                     &#8595;             &#8595;                    &#9474;
&#9474;                    ESD            aRTs       PulseAudio&#9474;
----------------------------------------------------------
&#9474;Kernel                                                  &#9474;
&#9474;                           &#8595;                            &#9474;
&#9474;                        ALSA driver                     &#9474;
----------------------------------------------------------
&#9474;Hardware                                                &#9474;
&#9474;                           &#8595;                            &#9474;
&#9474;                        Soundcard                       &#9474; &#9474;                                                        &#9474;
----------------------------------------------------------


I'm not sure if I just control Gstreamer decoder.
If I want to make it real-time, should I control the kernel to achieve real-time voice switching functions?
	
Thanks
OS: [Xubuntu] 8.04.1 kernel 2.6.24-19-generic

---

