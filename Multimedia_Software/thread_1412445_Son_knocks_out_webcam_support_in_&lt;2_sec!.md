---
title: "Son knocks out webcam support in &lt;2 sec!"
date: 2010-02-21
forum: Multimedia Software
---

### Post by Prium on 2010-02-21
OSs don't need to be adult-proof. They need to be kid-proof ;) 

I don't know what keystrokes my son inadvertently performed in the space of 1-2 seconds while I was video-chatting on skype, but the camera no longer is recognised by the system. I have had over 12 months solid use on ubuntu now and for me to wipe out camera support would take orders of magnitude longer than this...ha!  

What on earth could he have pressed? I found these in system log messages, not 100% sure about the timestamps though:

```
Feb 21 13:26:46 matthew-laptop kernel: [12651.422731] dell-wmi: Unknown key ffd0 pressed
Feb 21 13:36:59 matthew-laptop kernel: [13264.686616] dell-wmi: Unknown key ffd1 pressed
Feb 21 13:37:47 matthew-laptop kernel: [13312.785593] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Feb 21 13:37:59 matthew-laptop kernel: [13324.528476] tun0: Disabled Privacy Extensions
```

And this in syslog:

```

Feb 21 13:26:46 matthew-laptop kernel: [12651.422731] dell-wmi: Unknown key ffd0 pressed
Feb 21 13:27:29 matthew-laptop wpa_supplicant[1555]: CTRL-EVENT-SCAN-RESULTS 
Feb 21 13:29:29 matthew-laptop wpa_supplicant[1555]: CTRL-EVENT-SCAN-RESULTS 
Feb 21 13:30:09 matthew-laptop wpa_supplicant[1555]: WPA: Group rekeying completed with 00:1c:28:16:f0:ea [GTK=TKIP]
Feb 21 13:30:09 matthew-laptop NetworkManager: <info>  (eth1): supplicant connection state:  completed -> group handshake
Feb 21 13:30:09 matthew-laptop NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Feb 21 13:31:29 matthew-laptop wpa_supplicant[1555]: CTRL-EVENT-SCAN-RESULTS 
Feb 21 13:33:29 matthew-laptop wpa_supplicant[1555]: CTRL-EVENT-SCAN-RESULTS 
Feb 21 13:35:29 matthew-laptop wpa_supplicant[1555]: CTRL-EVENT-SCAN-RESULTS 
Feb 21 13:36:59 matthew-laptop kernel: [13264.686616] dell-wmi: Unknown key ffd1 pressed
Feb 21 13:37:29 matthew-laptop wpa_supplicant[1555]: CTRL-EVENT-SCAN-RESULTS 
Feb 21 13:37:47 matthew-laptop kernel: [13312.785593] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Feb 21 13:41:29 matthew-laptop wpa_supplicant[1555]: CTRL-EVENT-SCAN-RESULTS 
Feb 21 13:43:29 matthew-laptop wpa_supplicant[1555]: CTRL-EVENT-SCAN-RESULTS 
Feb 21 13:45:29 matthew-laptop wpa_supplicant[1555]: CTRL-EVENT-SCAN-RESULTS 
Feb 21 13:47:29 matthew-laptop wpa_supplicant[1555]: CTRL-EVENT-SCAN-RESULTS 
Feb 21 13:47:38 matthew-laptop kernel: [13903.405317] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).
Feb 21 13:47:44 matthew-laptop kernel: [13909.402731] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).
Feb 21 13:48:10 matthew-laptop kernel: [13935.862863] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).
Feb 21 13:48:16 matthew-laptop kernel: [13941.862688] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).
Feb 21 13:49:29 matthew-laptop wpa_supplicant[1555]: CTRL-EVENT-SCAN-RESULTS 
Feb 21 13:49:41 matthew-laptop kernel: [14026.891944] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).
Feb 21 13:49:47 matthew-laptop kernel: [14032.894537] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).
```

---

### Post by impact on 2010-02-21
Does your computer have a "camera off" button? Most laptops and netbooks do have it. Just find it and press it to turn the camera back on.

---

### Post by Prium on 2010-02-21
Nope, no function key assigned to the camera on this notebook (Latitude E4300)

Camera still enabled in bios too, I checked

---

### Post by Prium on 2010-02-23
Well, for reasons unknown to me my webcam is working again. An odd, but welcomed idiosyncrasy I'd say....since I had no clue as to why it stopped working in the first place. Maybe it's just this Dell. Anyway, an OS that 'fixes' itself is fine with me ;)

---

