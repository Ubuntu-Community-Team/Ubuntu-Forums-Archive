---
title: "HDMI sound Msi-7349 AKA K9NGM3 -FIH"
date: 2011-08-25
forum: Multimedia Software
---

### Post by blackcatblack on 2011-08-25
Sorry to make this my first post but its driving me up a wall.
Last usage of this os was unix in 95

Ok so i have the board above [http://www.msi.com/product/mb/K9NGM3-FIH.html](http://www.msi.com/product/mb/K9NGM3-FIH.html)
Installed 11.04 and can get audio from analog but none from hdmi

Aplay -l shows 0/0 ALC888 [Analog]
                      0/1 ALC888 [Digital]
                      0/3 HDMI 0 [HDMI 0]
i have changed in alsa to allow hda-intel= All on list under alc888

All i get is pissed off for 2 weeks.
I know this board will function but all post found have no info if they fixed it or not last was posted in 08

i do have a recovery file from original distributor that is used to rebuild system but cant load it as its looking for a "special flash disk" any way to dig out the driver from the main recover tar? 

Recovery Guts [http://www.megaupload.com/?d=MQFFYT0R](http://www.megaupload.com/?d=MQFFYT0R)

Full original recover iso [http://alturl.com/wc4a6](http://alturl.com/wc4a6)

any help would be great. If posible just need to get the audio working on 11.04 and could care less to recover using old build as its blocked some how unless you all know some trix.

P.S. i did unmute in alsamixer

---

### Post by blackcatblack on 2011-08-27
Ok so i semi got it working

the nvidia driver that was installed via mythbuntu is pos 173 and did not support audio through hdmi updated to current 280 

i can get test audio to work out 0,7 hdmi and also wav/ogg through vlc but divix/mp3 any other audio wont put audio out just play with no sound

---

### Post by blackcatblack on 2011-08-29
Well after many times trying setting 1/3 as default in pulse and acsound.conf it would only play test freq and wav/ogg in vlc 

reinstalled 11.04 thinking all the messing with this and that for 2 weeks killled somthing but after updating i got the audio on wav and ogg only no mp3 or divx and changed default in pluse and then asound.config still nothing

Since 11.04 is still alpha/beta i installed 10.4. and installed the new nvidia driver 280 and can get wav /ogg but no mp3 
aplay -l shows nvidia hdmi now and not hdmi 0 like on 11.04 so i feel im close edit the asound.conf and pulse and shes up and running in vlc . 

Still would like to get 11.04 working some time and cant figure what broke in 11.04

GPU NVIDIA® GeForce® 7050 PV/NVIDIA nForce® 630a (MCP68PV) Chipset

**[FONT=Arial][COLOR=#000000][B][FONT=Arial, Helvetica, sans-serif]Audio[/FONT]**[/COLOR][/FONT][COLOR=#000000] [/COLOR][/B]             • Chipset integrated by Realtek® ALC888
- Flexible 7.1-channel audio with jack sensing
- Compliant with Azalia 1.0 Spec


Im sure il update this one day if i can figure the issue out or if others fell like chiming in il test out what they have to offer.

---

