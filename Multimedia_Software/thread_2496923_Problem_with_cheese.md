---
title: "Problem with cheese"
date: 2024-04-17
forum: Multimedia Software
---

### Post by amiarg on 2024-04-17
Hi, Ubuntu 22.04 and cheese Cheese 44.1, camera Logitech c2770 HD
 installed, I can take a picture but when i try to record a video comes a blck screen  "there was an error playing video from webcam" after that i can only close cheese.
cheese
Gtk-Message: 12:43:58.928: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.

(cheese:30899): Gtk-WARNING **: 12:43:58.995: GTK+ module /snap/cheese/40/gnome-platform/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so cannot be loaded.
GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported.
Gtk-Message: 12:43:58.995: Failed to load module "canberra-gtk-module"

(cheese:30899): Gtk-WARNING **: 12:43:58.997: GTK+ module /snap/cheese/40/gnome-platform/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so cannot be loaded.
GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported.
Gtk-Message: 12:43:58.997: Failed to load module "canberra-gtk-module"

(cheese:30899): cheese-WARNING **: 12:44:00.035: Can't find vp8enc preset: "Profile Realtime", using alternate preset: "Cheese Realtime". If you see this, make a bug report!

(cheese:30899): GStreamer-WARNING **: 12:44:00.036: gst_value_deserialize_g_value_array: unimplemented

(cheese:30899): GStreamer-WARNING **: 12:44:00.036: gst_value_deserialize_g_value_array: unimplemented

(cheese:30899): GStreamer-WARNING **: 12:44:00.036: gst_value_deserialize_g_value_array: unimplemented

(cheese:30899): GStreamer-WARNING **: 12:44:00.042: gst_value_deserialize_g_value_array: unimplemented

(cheese:30899): GStreamer-WARNING **: 12:44:00.042: gst_value_deserialize_g_value_array: unimplemented

(cheese:30899): GStreamer-WARNING **: 12:44:00.042: gst_value_deserialize_g_value_array: unimplemented

(cheese:30899): cheese-WARNING **: 12:44:04.292: Failed to connect stream: Access denied: ../ext/pulse/pulsesrc.c(1622): gst_pulsesrc_prepare (): /GstCameraBin:camerabin/GstAutoAudioSrc:audiosrc/GstPulseSrc:audiosrc-actual-src-puls


(cheese:30899): cheese-WARNING **: 12:44:04.294: Internal data stream error.: ../libs/gst/base/gstbasesrc.c(3127): gst_base_src_loop (): /GstCameraBin:camerabin/GstAutoAudioSrc:audiosrc/GstPulseSrc:audiosrc-actual-src-puls:
streaming stopped, reason not-negotiated (-4)

---

### Post by amiarg on 2024-04-21
Guess I will wait for the new LTS, instead.

---

